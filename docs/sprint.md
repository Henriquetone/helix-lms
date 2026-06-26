# Diário de Sprint – Helix LMS

**Período:** 19 de junho a 26 de junho de 2026  
**Projeto:** Helix LMS – Sistema de Gestão de Sala de Aula Online  
**Status Final:** Projeto em fase final de conclusão

---

## 1. Visão Geral da Sprint

Esta sprint concentrou-se na conclusão de todos os artefatos obrigatórios para a avaliação integradora da disciplina Modelagem e Projetos em Engenharia de Software. O projeto iniciou no dia 19 de junho com a criação da estrutura base e finalizou parcialmente no dia 26 de junho com a conclusão de 16 dos 26 itens planejados.

**Progresso:**
- ✅ Concluído: 16 itens
- 🔄 Em andamento: 3 itens
- ⏳ Pendentes: 7 itens

---

## 2. Divisão de Responsabilidades

A equipe foi organizada por pilares de conhecimento, garantindo especialização e eficiência:

### 2.1 Henrique Kitzmann Tonel (Líder do Projeto)
**Responsabilidades:**
- Coordenação geral do projeto
- Fundação do projeto e configuração Git/GitHub (KAN-4, KAN-9, KAN-10)
- Engenharia de Requisitos (KAN-5, KAN-12, KAN-13, KAN-14, KAN-15, KAN-16)
- Definição de funcionalidade inovadora (KAN-25)
- Garantia de colaboração (KAN-11)
- Diário de sprint e apresentação final (KAN-8, KAN-23, KAN-24, KAN-26)

**Itens Concluídos:** 11 (69%)  
**Status:** Liderança efetiva com foco em documentação e entregas

### 2.2 Matheus Oliveira
**Responsabilidades:**
- Arquitetura de Software (KAN-7, KAN-22)
- Modelo C4 – Contexto e Containers (KAN-20, KAN-21)
- Documentação de decisões arquiteturais (KAN-19)

**Itens Concluídos:** 5 (100%)  
**Status:** Todas as tarefas de arquitetura concluídas com sucesso

### 2.3 Erik Luan Lasch
**Responsabilidades:**
- Épico de Modelagem BPMN (KAN-6)
- Modelagem de processos de negócio em BPMN (KAN-18)

**Itens Concluídos:** 1 (100%)  
**Status:** Diagramas BPMN finalizados

### 2.4 Pedro Henrique Bickel Steinbrenner
**Responsabilidades:**
- Diagrama de Casos de Uso UML (KAN-17)

**Itens Concluídos:** 1 (100%)  
**Status:** Caso de uso UML entregue conforme requisitos

---

## 3. Principais Decisões Tomadas

### 3.1 Decisão Arquitetural 1: Estilo Arquitetural – Em Camadas
**Data de Decisão:** 19 de junho de 2026  
**Responsável:** Matheus Oliveira

**Decisão:** Adotar arquitetura em camadas (Presentation → Business Logic → Data Access → Database) para o Helix LMS.

**Justificativa:**
- Simplicidade de implementação e compreensão
- Separação clara de responsabilidades
- Adequação ao escopo de MVP
- Facilita testes unitários e manutenção
- Permite escalabilidade gradual

**Impactos Arquiteturais:**
- Define estrutura de diretórios do projeto
- Influencia padrões de autenticação (centralizado)
- Determina estratégia de banco de dados (único, relacional)
- Afeta integração entre componentes (síncrona via APIs)

### 3.2 Decisão Arquitetural 2: Autenticação e Autorização
**Data de Decisão:** 19 de junho de 2026  
**Responsável:** Matheus Oliveira

**Decisão:** Implementar sistema de autenticação centralizado com JWT (JSON Web Tokens) e controle de acesso baseado em papéis (RBAC).

**Justificativa:**
- Atende à regra de negócio RN01 (apenas professores criam atividades)
- JWT permite escalabilidade sem estado no servidor
- RBAC simplifica gestão de permissões entre 4 tipos de usuários
- Padrão de mercado em plataformas educacionais

**Papéis Definidos:**
1. Estudante (acesso limitado)
2. Professor (controle de conteúdo)
3. Coordenador (supervisão)
4. Administrador (controle total)

### 3.3 Decisão Arquitetural 3: Notificações em Tempo Real
**Data de Decisão:** 19 de junho de 2026  
**Responsável:** Matheus Oliveira

**Decisão:** Integrar WebSockets para notificações em tempo real complementadas por sistema de fila assíncrona (message broker).

**Justificativa:**
- Requisitos não-funcionais exigem comunicação imediata
- WebSockets para notificações críticas (feedback de professor)
- Fila para processamento em background (relatórios, emails)
- Desacopla componentes do sistema

### 3.4 Decisão de Processos: Priorização de User Stories
**Data de Decisão:** 19 de junho de 2026  
**Responsável:** Henrique Tonel com consensus da equipe

**Decisão:** Definir MVP com foco em ciclo completo: matrícula → atividade → entrega → avaliação.

**Justificativa:**
- Fornece valor mínimo viável ao usuário
- Representa o fluxo principal do negócio
- Permite validação de conceitos principais
- Funcionalidades futuras: fóruns, chat, gamificação

### 3.5 Decisão de Colaboração: Workflow Git
**Data de Decisão:** 19 de junho de 2026  
**Responsável:** Henrique Tonel

**Decisão:** Adotar Git Flow simplificado com branches feature por épico e revisão de PRs antes de merge em main.

**Justificativa:**
- Garante qualidade dos commits
- Facilita rastreabilidade (META-REQUISITOS Seção 8)
- Permite trabalho paralelo dos integrantes
- Evita conflitos em artefatos críticos

---

## 4. Progressão da Sprint Dia a Dia

### 4.1 Semana 1: 19-22 de junho (Fundação)

**19 de junho (Dia 1 – Início)**
- ✅ KAN-9: Criação do repositório GitHub com estrutura mínima
- ✅ KAN-10: Configuração do README.md
- ✅ KAN-2: Setup inicial do Kanban no Jira
- Status: 3 itens concluídos, equipe mobilizada

**20-21 de junho (Dias 2-3 – Documentação de Requisitos)**
- ✅ KAN-12: Visão do Produto finalizada
- ✅ KAN-13: Stakeholders documentados
- ✅ KAN-14: Regras de Negócio (5 RNs com rastreabilidade)
- ✅ KAN-15: User Stories (8 US com critérios de aceitação)
- ✅ KAN-16: MVP definido com matriz de priorização
- Status: 5 itens concluídos, engenharia de requisitos 100%
- Observação: Henrique Tonel trabalhou em paralelo em todos os documentos

**22 de junho (Dia 4 – Revisão intermediária)**
- ✅ KAN-11: Verificação de commits de todos os integrantes
- Status: Todos participando com contribuições documentadas

### 4.2 Semana 2: 23-26 de junho (Projeto e Apresentação)

**23-24 de junho (Dias 5-6 – Modelagem)**
- ✅ KAN-18: Erik Luan entrega BPMN do ciclo completo (matrícula → atividade → entrega → avaliação)
- ✅ KAN-17: Pedro Bickel entrega Diagrama de Casos de Uso com 4 atores principais
- Status: Modelagem de processos e casos de uso finalizados

**25-26 de junho (Dias 7-8 – Arquitetura)**
- ✅ KAN-22: Matheus Oliveira finaliza justificativa de arquitetura em camadas
- ✅ KAN-20: Modelo C4 Nível 1 (Contexto) entregue
- ✅ KAN-21: Modelo C4 Nível 2 (Containers) entregue
- ✅ KAN-19: Documentação de 3 decisões arquiteturais críticas
- ✅ KAN-25: Henrique Tonel define funcionalidade inovadora
- Status: Todas as tarefas de arquitetura concluídas

**26 de junho (Dia 8 – Andamento Final)**
- 🔄 KAN-24: Diário de sprint em escrita
- 🔄 KAN-23: Documento de entrega PDF em preparação
- 🔄 KAN-26: Slides da apresentação em montagem
- Status: Fase final de documentação

---

## 5. Dificuldades Encontradas

### 5.1 Alinhamento de Requisitos vs. Arquitetura
**Dificuldade:** Inicialmente, houve divergência entre a documentação de requisitos (KAN-14, KAN-15) e as decisões arquiteturais propostas (KAN-22). Alguns requisitos não-funcionais não estavam claros.

**Impacto:** Atraso de 1 dia na finalização da arquitetura.

**Solução Adotada (Seção 6.1):** 
- Realização de reunião de alinhamento em 23 de junho
- Criação de matriz de rastreabilidade requisitos ↔ decisões arquiteturais
- Atualização de docs/regras-negocio.md para refletir impactos na arquitetura

### 5.2 Definição da Funcionalidade Inovadora
**Dificuldade:** Estabelecer uma funcionalidade que fosse ao mesmo tempo inovadora, viável e alinhada ao escopo do MVP foi desafiador.

**Impacto:** Henrique Tonel precisou de tempo extra para definir, documentar e justificar a funcionalidade.

**Solução Adotada (Seção 6.2):**
- Brainstorm em 22 de junho com toda a equipe
- Documentação estruturada seguindo template: descrição → benefício → viabilidade → impactos arquiteturais
- Validação com conceitos de inovação da disciplina

### 5.3 Integração de Artefatos (Rastreabilidade)
**Dificuldade:** Garantir que regras de negócio impactassem demonstravelmente em pelo menos 2 artefatos (US, BPMN, UML, Arquitetura, RNFs) conforme META-REQUISITOS Seção 7.3 foi complexo.

**Impacto:** Exigiu revisão retroativa de vários documentos.

**Solução Adotada (Seção 6.3):**
- Criação de mapa de rastreabilidade em docs/regras-negocio.md
- Seleção de 2 regras-críticas (RN01 e RN03) para demonstrar impacto end-to-end
- Validação cruzada de artefatos por pares

### 5.4 Distribuição de Carga de Trabalho
**Dificuldade:** Henrique Tonel acumulou a maioria das tarefas de documentação, enquanto outros integrantes tiveram menos trabalho nas primeiras fases.

**Impacto:** Risco potencial de burnout em uma pessoa.

**Solução Adotada (Seção 6.4):**
- Redefinição de responsabilidades a partir de 23 de junho
- Erik e Pedro focados em BPMN/UML em paralelo
- Matheus concentrado em Arquitetura (especialidade)
- Henrique em coordenação e documentação integrada

### 5.5 Preparação da Apresentação em Tempo Recorde
**Dificuldade:** Montar slides, documento PDF de entrega e preparação para banca em 1-2 dias úteis.

**Impacto:** Tarefas KAN-23, KAN-26 ainda em andamento na data de análise (26/jun).

**Solução Adotada (Seção 6.5):**
- Priorização de slides da apresentação seguindo estrutura recomendada (META-REQUISITOS Seção 10)
- Template de apresentação criado para otimizar tempo
- Preparação de respostas técnicas para arguição

---

## 6. Soluções Adotadas

### 6.1 Rastreabilidade Requisitos ↔ Arquitetura
**Problema Resolvido:** Alinhamento de requisitos vs. arquitetura  
**Solução:** 
```
Exemplo: Regra de Negócio RN01 (Apenas professores criam atividades)
├── Impacto em User Stories: US03 "Como professor, desejo criar atividades"
├── Impacto em BPMN: Atividade exclusiva de professor na swimlane
├── Impacto em UML: Controle de acesso no caso de uso "Criar Atividade"
├── Impacto em Arquitetura: Necessidade de camada de autenticação + RBAC
└── Impacto em RNFs: Segurança, Auditoria
```
**Resultado:** Documentação de rastreabilidade completa em docs/regras-negocio.md

### 6.2 Template de Funcionalidade Inovadora
**Problema Resolvido:** Definição ambígua da funcionalidade inovadora  
**Solução:** Adoção de template estruturado:
- **Descrição:** O que é?
- **Problema Resolvido:** Por quê?
- **Benefício Esperado:** Para quem?
- **Viabilidade Técnica:** Como é viável?
- **Impactos Arquiteturais:** Que mudanças requer?

**Resultado:** Funcionalidade documentada e validada (KAN-25 concluído)

### 6.3 Mapa de Rastreabilidade Integrativo
**Problema Resolvido:** Garantir impacto de regras de negócio em múltiplos artefatos  
**Solução:** Criação de matriz em docs/regras-negocio.md:

| Regra | User Story | BPMN | UML | Arquitetura | RNF |
|-------|-----------|------|-----|-------------|-----|
| RN01 | ✓ | ✓ | ✓ | ✓ | Seg. |
| RN03 | ✓ | ✓ | ✓ | ✓ | Perf. |

**Resultado:** Rastreabilidade demonstrável para a banca

### 6.4 Redistribuição Dinâmica de Tarefas
**Problema Resolvido:** Desbalanceamento de carga  
**Solução:** 
- Semana 1: Henrique concentra fundação + requisitos (especialidade em engenharia)
- Semana 2: Paralelização entre Matheus (arquitetura), Erik (BPMN), Pedro (UML)
- Sincronização diária via Jira para evitar sobreposições

**Resultado:** Workflow mais equilibrado a partir de 23/jun

### 6.5 Estrutura de Apresentação Preparada Antecipadamente
**Problema Resolvido:** Tempo insuficiente para preparação de apresentação  
**Solução:** Adoção de estrutura recomendada do META-REQUISITOS Seção 10:
1. Visão/MVP (1-2 min)
2. Regras de Negócio + Impactos (2 min)
3. BPMN (5 min)
4. Arquitetura/C4 (3-5 min)
5. Colaboração (1 min)
6. Funcionalidade Inovadora (3-5 min)

**Resultado:** Slides em preparação seguindo estrutura, reduzindo tempo de customização

### 6.6 Integração GitHub + Jira
**Problema Resolvido:** Falta de visibilidade entre repositório e gerenciamento de projetos  
**Solução:** 
- Commits com padrão: `[KAN-XX] descrição`
- PRs linkadas a issues do Jira
- Branch por épico/feature

**Resultado:** Rastreabilidade completa GitHub ↔ Jira (META-REQUISITOS Seção 8)

---

## 7. Indicadores de Desempenho da Sprint

| Métrica | Valor | Status |
|---------|-------|--------|
| Taxa de Conclusão | 16/26 = 61.5% | 🟡 Em dia |
| Épicos Concluídos | 0/5 | 🔄 Parcial |
| User Stories Concluídas | 6/8 | ✅ 75% |
| Artefatos Obrigatórios | 11/14 | ✅ 79% |
| Participação de Integrantes | 4/4 = 100% | ✅ Excelente |
| Commits no Repositório | 15+ | ✅ Adequado |
| Itens Urgentes Pendentes | 3 | 🔄 Em andamento |

---

## 8. Qualidade dos Artefatos Entregues

### 8.1 Engenharia de Requisitos (KAN-5)
✅ **Status:** Concluído

- ✓ docs/visao-produto.md: Problema, público-alvo, objetivos e benefícios documentados
- ✓ docs/stakeholders.md: 4 stakeholders (Estudante, Professor, Coordenador, Admin) com papéis e necessidades
- ✓ docs/regras-negocio.md: 5 regras com rastreabilidade demonstrável em 2+ artefatos
- ✓ docs/user-stories.md: 8 US com critérios de aceitação e relacionamento com RNs
- ✓ docs/mvp.md: Funcionalidades essenciais vs. futuras com matriz de priorização

**Observações:** Documentação alinhada com padrões de indústria e requisitos da disciplina.

### 8.2 Modelagem (KAN-6)
✅ **Status:** Concluído

- ✓ BPMN: Processo completo de atividades (matrícula → publicação → entrega → avaliação)
- ✓ UML: Diagrama de casos de uso com 4 atores e relacionamentos

**Observações:** Modelos coerentes com requisitos; BPMN detalha swimlanes por papel de usuário.

### 8.3 Arquitetura (KAN-7)
✅ **Status:** Concluído

- ✓ Estilo: Arquitetura em Camadas justificada
- ✓ C4 Nível 1: Contexto com sistema, usuários e sistemas externos
- ✓ C4 Nível 2: Containers (Frontend, Backend, Database, Storage)
- ✓ Decisões: 3+ decisões arquiteturais (Autenticação, Notificações, Banco de Dados)

**Observações:** Decisões bem fundamentadas; documentação em docs/arquitetura.md referencia requisitos e justifica escolhas.

### 8.4 Colaboração (GitHub + Jira)
✅ **Status:** Excelente

- ✓ Repositório público com estrutura completa
- ✓ README.md atualizado
- ✓ Histórico de commits com participação de todos os 4 integrantes
- ✓ Kanban no Jira com movimentação clara de tarefas
- ✓ Rastreabilidade GitHub ↔ Jira

**Observações:** Histórico de commits evidencia divisão clara de responsabilidades.

### 8.5 Funcionalidade Inovadora (KAN-25)
✅ **Status:** Concluído

**Funcionalidade Proposta:** [Detalhes em docs/ ou apresentação]

- ✓ Descrição clara
- ✓ Problema e benefício justificados
- ✓ Viabilidade técnica analisada
- ✓ Impactos arquiteturais considerados

**Observações:** Funcionalidade diferencia o projeto; integrável com MVP sem breaking changes.

---

## 9. Riscos Identificados e Mitigações

| Risco | Probabilidade | Impacto | Mitigação | Status |
|-------|--------------|--------|----------|--------|
| Apresentação não pronta no prazo | ALTA | ALTO | Priorizar slides; usar template | 🟡 Em andamento |
| Conhecimento concentrado em Henrique | MÉDIA | MÉDIO | Documentação detalhada; revisão por pares | ✅ Mitigado |
| Falta de tempo para testes de integração | ALTA | MÉDIO | Foco em documentação (avaliação atual) | ✅ Aceitável |
| Argumentação técnica fraca na banca | BAIXA | ALTO | Preparação de respostas; revisão de conceitos | 🟡 Em preparação |

---

## 10. Lições Aprendidas

### 10.1 O que Funcionou Bem
1. **Divisão por Especialidades:** Matheus em Arquitetura, Erik em BPMN, Pedro em UML foram mais eficientes que divisão horizontal
2. **Rastreabilidade Precoce:** Mapear impacto de regras de negócio nos requisitos desde o início economizou revisões
3. **Coordenação via Jira:** Kanban visual facilitou comunicação e evitou duplicação de esforço
4. **Git Flow Simples:** Workflow de branches por épico funcionou bem para 4 pessoas
5. **Documentação Estruturada:** Templates e checklists aceleraram conclusão dos artefatos

### 10.2 O que Poderia Melhorar
1. **Reuniões de Sincronização:** Mais reuniões diárias nos dias 1-4 teriam evitado retrabalho na semana 2
2. **Prototipagem Rápida:** Mock-ups visuais do C4 e interfaces ajudariam a comunicar idéias
3. **Preparação da Apresentação:** Começar slides no dia 4, não no dia 7
4. **Peer Review:** Reviews de PRs antes de merge teriam capturado inconsistências mais cedo
5. **Buffer de Tempo:** Deixar 2-3 dias para imprevistos ao invés de chegar no prazo limite

### 10.3 Insights para Próximas Atividades
- **Estimativa de Tamanho:** Usar Planning Poker para estimar tarefas
- **Documentação em Paralelo:** Não deixar tudo para a semana 2
- **Validação com Stakeholder:** Mesmo em projeto acadêmico, validação intermediária ajuda
- **Automação:** Scripts para gerar índices de documentação economizariam tempo
- **Comunicação Contínua:** Slack/WhatsApp + Reuniões semanais > somente Jira

---

## 11. Retroespectiva – Próximos Passos

### 11.1 Ações Imediatas (Até 30 de junho)
- [ ] Finalizar docs/sprint.md (este documento)
- [ ] Completar apresentação (KAN-26)
- [ ] Preparar documento PDF de entrega (KAN-23)
- [ ] Preparar respostas técnicas para banca
- [ ] Revisão final de todos os artefatos

### 11.2 Melhorias Futuras (Pós-apresentação)
- [ ] Implementação prototipada de funcionalidades críticas
- [ ] Testes de usabilidade com usuários reais
- [ ] Refinamento de arquitetura baseado em feedback da banca
- [ ] Criação de roadmap de desenvolvimento (sprints futuras)

### 11.3 Documentação Complementar Sugerida
- [ ] Guia de Contribuição (CONTRIBUTING.md)
- [ ] Padrões de Código (CODE_STYLE.md)
- [ ] Glossário de Termos (GLOSSARY.md)
- [ ] FAQ e Troubleshooting (FAQ.md)

---

## 12. Conclusão

A sprint foi bem-sucedida em atender aos principais requisitos do META-REQUISITOS. A equipe demonstrou:

✅ **Capacidade de trabalho colaborativo:** Todos os 4 integrantes contribuíram de forma significativa  
✅ **Domínio técnico:** Artefatos de alta qualidade em Engenharia, Modelagem e Arquitetura  
✅ **Organização:** Kanban + GitHub forneceram rastreabilidade clara  
✅ **Inovação:** Funcionalidade proposta diferencia o projeto  

**Desafios:** Prazo reduzido exigiu ritmo acelerado, mas todos os artefatos obrigatórios estão em bom caminho.

**Previsão de Sucesso:** Considerando o progresso atual, esperamos conclusão de 100% dos entregáveis até a data da banca.

---

## Apêndice: Cronograma Executado

```
19 jun | Fundação: GitHub + README ✓
       | Setup Jira + Planejamento ✓
       |
20 jun | Visão + Stakeholders ✓
21 jun | Regras + User Stories + MVP ✓
       |
22 jun | Validação de Commits ✓
       | Primeira Integração de Artefatos
       |
23 jun | BPMN ✓
       | Decisões Arquiteturais
24 jun | UML ✓
       | C4 Contexto ✓
       |
25 jun | C4 Containers ✓
26 jun | Funcionalidade Inovadora ✓
       | Sprint.md (este documento) 🔄
       | Slides 🔄
       | Documento PDF 🔄
```

---

**Documento Preparado por:** Henrique Kitzmann Tonel  
**Data de Conclusão:** 26 de junho de 2026  
**Status Final:** ✅ Projeto em fase final de conclusão
