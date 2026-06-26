# Arquitetura de Software – Helix LMS

## 1. Visão Geral

O Helix LMS é um Sistema de Gestão de Sala de Aula Online projetado para centralizar a gestão de turmas, atividades, entregas e avaliações entre professores e estudantes. Esta documentação registra as principais decisões arquiteturais tomadas durante o projeto, suas justificativas e impactos técnicos.

---

## 2. Estilo Arquitetural

### Decisão: Arquitetura em Camadas (Layered Architecture) com separação Cliente-Servidor

**Contexto:** O sistema precisa suportar múltiplos perfis de usuário (Estudante, Professor, Coordenador, Administrador) com permissões distintas, além de operações de CRUD sobre turmas, atividades e entregas.

**Decisão:** Adotar uma arquitetura em camadas clássica com separação entre frontend (cliente web) e backend (API REST):

```
┌──────────────────────────────────────────────────────┐
│                   Camada de Apresentação              │
│              (Frontend Web – SPA/React)               │
├──────────────────────────────────────────────────────┤
│                  Camada de Aplicação                  │
│            (API REST – Node.js / Express)             │
├──────────────────────────────────────────────────────┤
│                   Camada de Domínio                   │
│       (Regras de Negócio, Serviços, Validações)       │
├──────────────────────────────────────────────────────┤
│               Camada de Infraestrutura                │
│   (Banco de Dados Relacional, Object Storage, NTP)    │
└──────────────────────────────────────────────────────┘
```

**Justificativa:**
- Separação de responsabilidades facilita manutenção e evolução independente do frontend e backend.
- API REST permite integração futura com aplicativo mobile nativo (previsto para versões futuras).
- Camada de domínio isolada facilita aplicação e teste das regras de negócio (RN01 a RN08).

**Consequências:**
- Necessidade de gerenciar autenticação via token (JWT) para comunicação stateless entre cliente e servidor.
- Maior latência em operações simples comparado a uma arquitetura monolítica, mas ganhos significativos em escalabilidade e manutenibilidade.

---

## 3. Decisões Arquiteturais

### DA01 – Controle de Acesso Baseado em Papéis (RBAC)

**Contexto:** O sistema possui quatro perfis com permissões muito distintas: Administrador, Coordenador, Professor e Estudante. RN01 e RN03 exigem controle granular de acesso.

**Decisão:** Implementar RBAC (Role-Based Access Control) com verificação de perfil via middleware nas rotas da API.

**Justificativa:**
- RN01 exige que somente professores criem/editem/excluam atividades.
- RN03 exige que estudantes acessem apenas turmas em que estão matriculados.
- RN07 exige que coordenadores visualizem todas as turmas sem restrição de professor.
- RBAC é o padrão mais adequado para sistemas com perfis bem definidos e permissões estáticas.

**Implementação:**
- Cada usuário possui um campo `role` (admin | coordenador | professor | estudante).
- Middleware de autorização `checkRole(['professor'])` é aplicado nas rotas protegidas.
- Permissões especiais para coordenador: `read:all_turmas`.

**Alternativas Consideradas:**
- ABAC (Attribute-Based Access Control): descartado por ser excessivamente complexo para o escopo do MVP.
- ACL (Access Control Lists): descartado por dificuldade de manutenção em cenários com muitos usuários.

---

### DA02 – Autenticação via JWT (JSON Web Token)

**Contexto:** A comunicação entre frontend e backend precisa ser autenticada de forma segura e stateless.

**Decisão:** Utilizar JWT para autenticação. O token é emitido no login e enviado em todas as requisições via header `Authorization: Bearer <token>`.

**Justificativa:**
- Stateless: o servidor não precisa manter sessão em memória, favorecendo escalabilidade.
- Portável: facilita futura integração com aplicativo mobile.
- Amplamente suportado nas tecnologias escolhidas (Node.js, React).

**Consequências:**
- Tokens expirados exigem fluxo de refresh token para boa experiência de usuário.
- Dados sensíveis não devem ser armazenados no payload do JWT.

---

### DA03 – Banco de Dados Relacional (PostgreSQL)

**Contexto:** O sistema possui entidades fortemente relacionadas: Usuário, Turma, Matrícula, Atividade, Entrega, Avaliação.

**Decisão:** Utilizar banco de dados relacional PostgreSQL.

**Justificativa:**
- Relacionamentos complexos (ex.: muitos-para-muitos entre Estudante e Turma via tabela `matricula`) são naturalmente expressos em SQL.
- RN06 exige precisão decimal em notas (`DECIMAL(4,2)`), nativamente suportado.
- RN08 exige integridade referencial (turma com professor obrigatório), garantida via `NOT NULL` e `FOREIGN KEY`.
- PostgreSQL oferece suporte nativo a transações ACID, essencial para garantir consistência em operações como submissão de entregas.

**Alternativas Consideradas:**
- MongoDB (NoSQL): descartado pela natureza fortemente relacional dos dados e necessidade de integridade referencial.
- MySQL: considerado, mas PostgreSQL foi preferido por recursos avançados (tipos de dados, extensibilidade).

**Modelo de Dados Principal:**
```
Usuario    (id, nome, email, senha_hash, role, criado_em)
Turma      (id, nome, codigo_acesso, professor_id FK, criado_em)
Matricula  (id, estudante_id FK, turma_id FK, criado_em)
Atividade  (id, turma_id FK, titulo, descricao, prazo, pontuacao_max, status, criado_em)
Entrega    (id, atividade_id FK, estudante_id FK, arquivo_url, entregue_em, entregue_atraso, criado_em)
Avaliacao  (id, entrega_id FK, nota DECIMAL(4,2), comentario, avaliado_em)
```

---

### DA04 – Object Storage para Arquivos (S3-compatible)

**Contexto:** O sistema precisa armazenar arquivos de atividades e entregas (até 50MB por arquivo, conforme RN04).

**Decisão:** Utilizar serviço de object storage compatível com S3 (ex.: AWS S3 em produção ou MinIO em desenvolvimento/testes).

**Justificativa:**
- Desacopla o armazenamento de arquivos do servidor de aplicação, facilitando escalabilidade.
- Limites de tamanho configuráveis tanto no cliente quanto no servidor (RN04).
- Baixo custo operacional para volumes moderados de arquivos.
- Acesso direto por URL assinada permite download seguro sem tráfego desnecessário pelo servidor.

**Consequências:**
- Arquivos enviados são validados antes do upload (client-side e server-side).
- URLs de arquivos são armazenadas no banco, não os binários.

---

### DA05 – Validação de Prazos com Sincronização NTP

**Contexto:** RN02 exige que entregas após prazo sejam sinalizadas automaticamente. A comparação de timestamps precisa ser confiável.

**Decisão:** Utilizar servidor NTP para sincronização de horário e armazenar todos os timestamps em UTC no banco de dados.

**Justificativa:**
- Evita inconsistências de fuso horário entre servidores e clientes.
- Garante precisão na detecção de entregas atrasadas.
- Campo `entregue_atraso` (boolean) calculado no momento da submissão comparando `entregue_em > atividade.prazo`.

---

### DA06 – Notificações por E-mail (Assíncrono)

**Contexto:** Diversas ações no sistema requerem notificação ao usuário (nova atividade, avaliação publicada, reabertura de atividade).

**Decisão:** Implementar sistema de notificações assíncrono via e-mail, utilizando fila de mensagens (ex.: Redis + Bull).

**Justificativa:**
- Notificações não devem bloquear a resposta da API ao usuário.
- Processamento assíncrono garante que falhas no envio de e-mail não afetem a operação principal.
- Escopo do MVP: notificações básicas por e-mail; versões futuras podem adicionar notificações push.

---

## 4. Requisitos Não Funcionais

| RNF | Descrição | Decisão Relacionada |
|-----|-----------|---------------------|
| Segurança | Controle de acesso baseado em perfis | DA01 – RBAC |
| Segurança | Autenticação stateless | DA02 – JWT |
| Integridade | Notas entre 0 e 10 com 2 casas decimais | DA03 – DECIMAL(4,2) |
| Integridade | Turma com professor obrigatório | DA03 – NOT NULL FK |
| Confiabilidade | Precisão na sinalização de prazos | DA05 – NTP + UTC |
| Performance | Cache de relações estudante-turma | DA01 – RBAC middleware |
| Usabilidade | Feedback imediato sobre erros de upload | DA04 – Validação dupla |
| Escalabilidade | Separação de responsabilidades | Arquitetura em Camadas |
| Rastreabilidade | Histórico de reabertura de atividades | DA03 – Modelo de dados |
| Auditoria | Registro de criação/edição por perfil | DA01 + DA02 |

---

## 5. Tecnologias Adotadas

| Camada | Tecnologia | Justificativa |
|--------|-----------|---------------|
| Frontend | React.js (SPA) | Componentização, ecossistema maduro, adequado para interfaces dinâmicas |
| Backend | Node.js + Express | Alta produtividade, JavaScript full-stack, amplo suporte a APIs REST |
| Banco de Dados | PostgreSQL | Relacional, ACID, suporte a DECIMAL e integridade referencial |
| Autenticação | JWT | Stateless, portável, padrão de mercado |
| Armazenamento | AWS S3 / MinIO | Object storage escalável, desacoplado da aplicação |
| Notificações | Nodemailer + Fila | Assíncrono, não-bloqueante |
| Controle de Versão | Git + GitHub | Colaboração, histórico de mudanças |
| Gestão de Projeto | Jira (Kanban) | Rastreabilidade de tarefas e épicos |

---

## 6. Referências

- Visão do Produto: `docs/visao-produto.md`
- Regras de Negócio: `docs/regras-negocio.md`
- User Stories: `docs/user-stories.md`
- MVP: `docs/mvp.md`
- Modelo C4 – Nível 1 (Contexto): `c4/contexto.md`
- Modelo C4 – Nível 2 (Containers): `c4/containers.md`
