# Modelo C4 – Nível 2: Diagrama de Containers

## Helix LMS – Visão de Containers

O Diagrama de Containers mostra os principais processos executáveis, armazenamentos de dados e como eles se comunicam internamente.

---

## Representação Textual (C4 Containers)

```
+=========================================================================+
|                            HELIX LMS                                    |
|                                                                         |
|  +-----------------+      HTTPS/REST      +-------------------------+  |
|  |                 | -------------------> |                         |  |
|  |  Web App        |                      |  API Server             |  |
|  |  (React SPA)    | <------------------- |  (Node.js + Express)    |  |
|  |                 |      JSON            |                         |  |
|  |  Navegador Web  |                      |  - Autenticação JWT     |  |
|  |  do usuário     |                      |  - RBAC Middleware      |  |
|  +-----------------+                      |  - Regras de Negócio    |  |
|                                           |  - Validação de Prazos  |  |
|                                           |  - Gestão de Uploads    |  |
|                                           +----------+--------------+  |
|                                                      |                 |
|                         +----------------------------+----------+      |
|                         |                            |          |      |
|                         v                            v          v      |
|              +------------------+   +---------------+  +--------+     |
|              |                  |   |               |  |        |     |
|              |  Banco de Dados  |   | Object Storage|  | Fila   |     |
|              |  (PostgreSQL)    |   | (S3 / MinIO)  |  | Email  |     |
|              |                  |   |               |  | (Redis)|     |
|              |  - Usuários      |   |  - Arquivos   |  |        |     |
|              |  - Turmas        |   |    atividades |  +---+----+     |
|              |  - Matrículas    |   |  - Entregas   |      |         |
|              |  - Atividades    |   |    (50MB max) |      v         |
|              |  - Entregas      |   +---------------+  +--------+    |
|              |  - Avaliações    |                      | Worker |    |
|              +------------------+                      | Email  |    |
|                                                        | (Node) |    |
|                                                        +---+----+    |
+=========================================================================+
                                                             |
                                                             v
                                                +---------------------+
                                                | Serviço de E-mail   |
                                                | (SMTP / SendGrid)   |
                                                | [SISTEMA EXTERNO]   |
                                                +---------------------+
```

---

## Descrição dos Containers

### 1. Web App (React SPA)
- **Tecnologia:** React.js rodando no navegador do usuário.
- **Responsabilidade:** Interface gráfica para todos os perfis (Estudante, Professor, Coordenador, Administrador).
- **Comunicação:** Envia requisições HTTP/HTTPS para a API Server. Recebe respostas JSON.
- **Principais decisões:**
  - Validação client-side de tamanho de arquivos (RN04) antes do upload.
  - Exibição visual diferenciada para entregas atrasadas (RN02).
  - Renderização condicional de funcionalidades por perfil de usuário (RBAC).

### 2. API Server (Node.js + Express)
- **Tecnologia:** Node.js com framework Express.
- **Responsabilidade:** Toda a lógica de negócio, autenticação, autorização e orquestração dos dados.
- **Comunicação:**
  - Recebe requisições REST do Web App.
  - Lê e escreve no PostgreSQL.
  - Faz upload/download de arquivos no Object Storage.
  - Publica eventos de notificação na fila Redis.
- **Principais módulos internos:**
  - `auth/`: geração e validação de JWT.
  - `middleware/rbac.js`: verificação de perfis antes das rotas.
  - `services/prazo.js`: validação de prazos com timestamps UTC.
  - `services/upload.js`: integração com S3/MinIO, validação de 50MB.
  - `controllers/`: handlers das rotas REST por domínio (turmas, atividades, entregas, avaliações).

### 3. Banco de Dados (PostgreSQL)
- **Tecnologia:** PostgreSQL 15+.
- **Responsabilidade:** Persistência de todos os dados estruturados do sistema.
- **Principais tabelas:** `usuarios`, `turmas`, `matriculas`, `atividades`, `entregas`, `avaliacoes`.
- **Restrições de integridade:** `NOT NULL` em `turmas.professor_id`, `DECIMAL(4,2)` para notas, `FOREIGN KEY` em todas as relações.

### 4. Object Storage (S3 / MinIO)
- **Tecnologia:** AWS S3 (produção) ou MinIO (desenvolvimento).
- **Responsabilidade:** Armazenamento de arquivos binários (materiais de aulas e entregas dos estudantes).
- **Limite:** 50MB por arquivo (RN04), validado no API Server antes do upload.
- **Acesso:** URLs assinadas com expiração para downloads seguros.

### 5. Fila de E-mails (Redis)
- **Tecnologia:** Redis + Bull (biblioteca de filas para Node.js).
- **Responsabilidade:** Desacoplar o disparo de notificações das operações principais da API.
- **Eventos que disparam e-mails:** nova atividade publicada, entrega avaliada, atividade reaberta, matrícula confirmada.

### 6. Worker de E-mail (Node.js)
- **Tecnologia:** Processo Node.js separado consumindo a fila Redis.
- **Responsabilidade:** Processar jobs da fila e enviar e-mails via SMTP externo.
- **Benefício:** Falhas no envio não afetam a resposta da API ao usuário.

---

## Fluxo de Exemplo: Submissão de Entrega (US05)

1. **Estudante** seleciona arquivo no Web App.
2. **Web App** valida tamanho < 50MB no cliente (RN04).
3. **Web App** envia `POST /entregas` com arquivo para a **API Server**.
4. **API Server** verifica JWT e permissão RBAC (estudante matriculado na turma).
5. **API Server** valida novamente o tamanho (server-side).
6. **API Server** compara timestamp atual com `atividade.prazo` → define `entregue_atraso` (RN02).
7. **API Server** faz upload do arquivo para o **Object Storage**.
8. **API Server** persiste registro de entrega no **PostgreSQL**.
9. **API Server** publica job de notificação na **Fila Redis**.
10. **API Server** retorna resposta de sucesso ao **Web App**.
11. **Worker de E-mail** processa job e envia e-mail de confirmação ao estudante.

---

## Referências

- Diagrama de Contexto (Nível 1): `c4/contexto.md`
- Decisões Arquiteturais: `docs/arquitetura.md`
- Regras de Negócio: `docs/regras-negocio.md`
