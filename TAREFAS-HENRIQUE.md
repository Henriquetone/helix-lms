# TAREFAS E RESPONSABILIDADES - HENRIQUE K. TONEL

## Visão Geral

Este documento detalha as responsabilidades do estudante Henrique K. Tonel no projeto de Sistema de Gestão de Sala de Aula Online, conforme definido nos meta-requisitos da disciplina.

**Responsável por:** Fundação do Projeto e Engenharia de Requisitos  
**Carga estimada:** 8-9 horas  
**Peso na avaliação:** 40% (25% Requisitos + 15% Colaboração)

---

## 1. Git e GitHub

### Responsabilidades

#### 1.1 Criação do Repositório
- Criar repositório público no GitHub
- Nomear adequadamente (ex: `sistema-sala-aula-online`)
- Configurar README.md inicial
- Adicionar licença (se necessário)

#### 1.2 Estrutura Obrigatória do Repositório

Implementar a seguinte estrutura mínima:

```
sistema-sala-aula-online/
├── docs/
│   ├── visao-produto.md
│   ├── stakeholders.md
│   ├── regras-negocio.md
│   ├── user-stories.md
│   ├── mvp.md
│   ├── arquitetura.md
│   ├── sprint.md
│   └── README.md
├── bpmn/
├── uml/
├── c4/
├── apresentacao/
└── README.md
```

#### 1.3 Controle de Versões
- Garantir commits descritivos e frequentes
- Evidenciar participação de todos os 4 integrantes
- Manter histórico organizado do projeto
- Usar branches se necessário

#### 1.4 Documentação
- Manter README.md atualizado com:
  - Nome do projeto
  - Descrição
  - Integrantes
  - Links relevantes
  - Instruções de navegação

### Critérios de Avaliação (Seção 8 - META-REQUISITOS)

A banca observará:
- ✅ Participação dos integrantes
- ✅ Evolução dos artefatos
- ✅ Organização do repositório
- ✅ Histórico de commits

---

## 2. Gestão Ágil com Kanban

### Responsabilidades

#### 2.1 Escolha da Ferramenta
Selecionar e configurar UMA das opções:
- Jira
- Trello
- GitHub Projects

#### 2.2 Criação do Backlog
- Listar TODAS as tarefas do projeto
- Incluir todos os entregáveis obrigatórios
- Priorizar itens conforme dependências
- Vincular tarefas aos responsáveis

#### 2.3 Organização do Quadro Kanban

Estrutura mínima:
```
┌─────────────┬──────────────┬──────────────┐
│   TO DO     │ IN PROGRESS  │     DONE     │
├─────────────┼──────────────┼──────────────┤
│ Tarefa 1    │ Tarefa 5     │ Tarefa 9     │
│ Tarefa 2    │ Tarefa 6     │ Tarefa 10    │
│ Tarefa 3    │              │              │
│ Tarefa 4    │              │              │
└─────────────┴──────────────┴──────────────┘
```

#### 2.4 Distribuição de Tarefas
- Atribuir tarefas aos 4 integrantes
- Garantir equilíbrio de carga
- Considerar dependências entre tarefas
- Documentar responsabilidades

### Critérios de Avaliação (Seção 8 - META-REQUISITOS)

A banca observará:
- ✅ Backlog completo
- ✅ Quadro Kanban organizado
- ✅ Distribuição de tarefas
- ✅ Movimentação dos cartões
- ✅ Participação dos integrantes

---

## 3. Requisitos de Software

### 3.1 Visão do Produto (docs/visao-produto.md)

#### Conteúdo Obrigatório (Seção 7.1 - META-REQUISITOS)

**Problema a ser resolvido**
- Qual problema a plataforma resolve?
- Por que esse problema é relevante?
- Quais são as consequências de não resolvê-lo?

**Público-alvo**
- Quem são os usuários principais?
- Quais são suas necessidades?
- Qual contexto de uso?

**Objetivos da solução**
- O que o sistema deve alcançar?
- Quais são as metas principais?
- Como o sucesso será medido?

**Benefícios esperados**
- Para estudantes
- Para professores
- Para a instituição
- Para coordenadores/administradores

#### Exemplo de Estrutura

```markdown
# Visão do Produto

## 1. Problema

[Descrição detalhada do problema]

## 2. Público-Alvo

- **Estudantes:** [descrição]
- **Professores:** [descrição]
- **Coordenadores:** [descrição]

## 3. Objetivos da Solução

1. [Objetivo 1]
2. [Objetivo 2]
3. [Objetivo 3]

## 4. Benefícios Esperados

### Para Estudantes
- [Benefício 1]
- [Benefício 2]

### Para Professores
- [Benefício 1]
- [Benefício 2]
```

---

### 3.2 Stakeholders (docs/stakeholders.md)

#### Conteúdo Obrigatório (Seção 7.2 - META-REQUISITOS)

Identificar os principais envolvidos no sistema:

**Exemplos fornecidos:**
- Estudantes
- Professores
- Coordenadores
- Administradores

#### Para cada stakeholder, descrever:
- Nome/Tipo
- Papel no sistema
- Principais necessidades
- Principais interações

#### Exemplo de Estrutura

```markdown
# Stakeholders

## 1. Estudantes

**Papel:** Usuários principais que consomem conteúdo e realizam atividades

**Necessidades:**
- Acessar materiais didáticos
- Submeter atividades
- Acompanhar notas

**Interações:**
- Visualizar turmas
- Fazer upload de arquivos
- Receber notificações

## 2. Professores

[Similar ao exemplo acima]
```

---

## 4. Regras de Negócio (docs/regras-negocio.md)

### Requisitos (Seção 7.3 - META-REQUISITOS)

#### 4.1 Quantidade
- **Mínimo:** 5 regras
- **Máximo:** 8 regras

#### 4.2 Formato
- Identificador único (RN01, RN02, etc.)
- Descrição clara da regra
- Justificativa (quando necessário)

#### 4.3 CRÍTICO: Rastreabilidade de Impactos

**Demonstrar como pelo menos 2 regras influenciaram:**

1. **Requisitos**
   - Requisitos funcionais gerados
   - Requisitos não funcionais afetados

2. **User Stories**
   - Quais stories foram derivadas

3. **Processos de Negócio (BPMN)**
   - Como a regra aparece no processo
   - Restrições no fluxo

4. **Modelagem (UML)**
   - Impacto nos casos de uso
   - Atores afetados

5. **Decisões Arquiteturais**
   - Necessidades técnicas geradas
   - Componentes afetados

### Exemplo Fornecido nos META-REQUISITOS

**RN01 – Apenas professores podem criar atividades.**

Possíveis impactos:
- **User Story:** Como professor, desejo criar atividades para disponibilizar tarefas aos estudantes.
- **Caso de Uso:** Criar Atividade.
- **BPMN:** atividade executada exclusivamente pelo professor.
- **Arquitetura:** necessidade de autenticação e controle de autorização.
- **Requisito Não Funcional:** segurança.

### Estrutura Recomendada

```markdown
# Regras de Negócio

## RN01 – [Título da Regra]

**Descrição:** [descrição detalhada]

**Impactos:**

### User Stories
- US01: [descrição]

### Processos (BPMN)
- [como aparece no processo]

### Casos de Uso
- UC01: [nome do caso]

### Arquitetura
- [decisões técnicas necessárias]

### Requisitos Não Funcionais
- [requisitos de qualidade afetados]

---

## RN02 – [Próxima Regra]
[...]
```

### Sugestões de Regras para Sistema de Sala de Aula

- Controle de acesso (quem pode fazer o quê)
- Prazos e deadlines
- Limites de tamanho de arquivo
- Privacidade e compartilhamento
- Avaliação e notas
- Comunicação entre usuários
- Gerenciamento de turmas

---

## 5. User Stories (docs/user-stories.md)

### Requisitos (Seção 7.4 - META-REQUISITOS)

#### 5.1 Quantidade
- **Mínimo:** 5 User Stories
- **Máximo:** 10 User Stories

#### 5.2 Formato Obrigatório

Cada User Story DEVE conter:

1. **Identificador único** (US01, US02, etc.)
2. **Descrição no formato padrão:**
   ```
   Como [tipo de usuário],
   Desejo [ação/funcionalidade],
   Para [benefício/objetivo].
   ```
3. **Critérios de aceitação** (checklist de validação)

### Estrutura Recomendada

```markdown
# User Stories

## US01 – [Título Descritivo]

**Como** professor,  
**Desejo** criar atividades com título, descrição e prazo,  
**Para** disponibilizar tarefas aos estudantes da minha turma.

### Critérios de Aceitação
- [ ] O professor consegue acessar o formulário de criação de atividade
- [ ] Todos os campos obrigatórios são validados
- [ ] A atividade criada aparece na lista da turma
- [ ] Estudantes recebem notificação da nova atividade
- [ ] O prazo é validado (não pode ser no passado)

### Regras de Negócio Relacionadas
- RN01: Apenas professores podem criar atividades

### Prioridade
- [ ] MVP (essencial)
- [x] Futuro

---

## US02 – [Próxima Story]
[...]
```

### Sugestões de User Stories

**Para Professores:**
- Criar/editar/deletar atividades
- Corrigir entregas
- Gerenciar turmas
- Visualizar relatórios

**Para Estudantes:**
- Visualizar atividades
- Submeter entregas
- Acompanhar notas
- Participar de turmas

**Para Coordenadores:**
- Gerenciar professores
- Visualizar estatísticas
- Configurar períodos letivos

---

## 6. MVP - Minimum Viable Product (docs/mvp.md)

### Requisitos (Seção 7.5 - META-REQUISITOS)

#### 6.1 Conteúdo Obrigatório

**Funcionalidades essenciais**
- Listar funcionalidades que DEVEM estar na primeira versão
- Priorizar com base em valor para o usuário
- Considerar viabilidade técnica

**Funcionalidades futuras**
- Listar funcionalidades importantes mas não essenciais
- Explicar por que ficaram para depois
- Indicar possível roadmap

**Justificativa da priorização**
- Critérios usados para decidir
- Trade-offs considerados
- Alinhamento com objetivos do produto

### Estrutura Recomendada

```markdown
# MVP - Minimum Viable Product

## 1. Funcionalidades Essenciais (MVP)

### Gestão de Usuários
- [x] US01: Cadastro de usuários
- [x] US02: Login/Logout
- [x] US03: Perfis (Estudante, Professor, Coordenador)

### Gestão de Turmas
- [x] US04: Professor cria turma
- [x] US05: Estudante entra em turma via código

### Gestão de Atividades
- [x] US06: Professor cria atividade
- [x] US07: Estudante submete entrega
- [x] US08: Professor visualiza entregas

**Justificativa:**
[Por que essas funcionalidades são essenciais?]

---

## 2. Funcionalidades Futuras (Versão 2.0+)

### Comunicação Avançada
- [ ] US09: Chat em tempo real
- [ ] US10: Videoconferências integradas

### Analytics e Relatórios
- [ ] US11: Dashboard de desempenho
- [ ] US12: Exportação de relatórios

### Gamificação
- [ ] US13: Sistema de pontos
- [ ] US14: Badges e conquistas

**Justificativa:**
[Por que podem esperar?]

---

## 3. Critérios de Priorização

### Usados para definir o MVP:
1. **Valor para o usuário:** Resolve o problema principal?
2. **Viabilidade técnica:** Possível implementar rapidamente?
3. **Dependências:** Funcionalidade base para outras?
4. **Complexidade:** Esforço de desenvolvimento
5. **Risco:** Impacto de não ter na primeira versão

### Matriz de Priorização

| User Story | Valor | Viabilidade | Prioridade | Versão |
|------------|-------|-------------|------------|--------|
| US01       | Alto  | Alta        | CRÍTICA    | MVP    |
| US02       | Alto  | Alta        | CRÍTICA    | MVP    |
| US09       | Médio | Baixa       | BAIXA      | v2.0   |
```

---

## Conexões e Rastreabilidade

### Fluxo de Dependências

```
visao-produto.md
    ↓
stakeholders.md
    ↓
regras-negocio.md
    ↓
user-stories.md
    ↓
mvp.md
```

### Garantir Consistência

- Stakeholders mencionados na visão devem aparecer nas stories
- Regras de negócio devem gerar user stories
- User stories devem referenciar regras de negócio
- MVP deve listar user stories priorizadas

---

## Cronograma Sugerido

### Aula 1 (2h30) - Concepção

**Primeiros 30 minutos:**
- [ ] Criar repositório GitHub
- [ ] Implementar estrutura de pastas
- [ ] Configurar ferramenta Kanban

**60 minutos:**
- [ ] Brainstorm colaborativo (todos os integrantes)
- [ ] Rascunho de visao-produto.md
- [ ] Identificar stakeholders
- [ ] Listar possíveis regras de negócio

**60 minutos:**
- [ ] Finalizar visao-produto.md
- [ ] Finalizar stakeholders.md
- [ ] Escrever 3-4 regras de negócio iniciais

**Últimos 30 minutos:**
- [ ] Popular Kanban com todas as tarefas
- [ ] Distribuir responsabilidades
- [ ] Primeiro commit no GitHub

### Entre Aulas (trabalho assíncrono)

- [ ] Finalizar regras-negocio.md (5-8 regras)
- [ ] Documentar rastreabilidade de 2 regras
- [ ] Escrever user-stories.md (5-10 stories)
- [ ] Definir mvp.md
- [ ] Atualizar Kanban conforme progresso
- [ ] Commits frequentes

### Aula 2 (2h30) - Projeto

- [ ] Revisar integração dos seus artefatos
- [ ] Apoiar outros integrantes com dúvidas
- [ ] Validar rastreabilidade (regras → stories → BPMN → UML → arquitetura)
- [ ] Atualizar Kanban
- [ ] Preparar parte da apresentação (requisitos)

### Antes da Banca

- [ ] Revisão final de todos os documentos
- [ ] Validar links e referências cruzadas
- [ ] Garantir formatação consistente
- [ ] Ensaiar apresentação (parte de requisitos)
- [ ] Preparar respostas para possíveis perguntas

---

## Critérios de Avaliação Específicos

### Engenharia de Requisitos - 25%

| Nível | Descrição | Seu Objetivo |
|-------|-----------|--------------|
| **Insuficiente** | Artefatos incompletos ou inconsistentes | ❌ Evitar |
| **Adequado** | Artefatos coerentes | ⚠️ Mínimo aceitável |
| **Excelente** | Artefatos completos, consistentes e rastreáveis | ✅ Almejar |

### Colaboração - 15%

| Nível | Descrição | Seu Objetivo |
|-------|-----------|--------------|
| **Insuficiente** | Poucas evidências de participação | ❌ Evitar |
| **Adequado** | Participação adequada | ⚠️ Mínimo aceitável |
| **Excelente** | Excelente colaboração e organização | ✅ Almejar |

---

## Checklist Final de Entrega

### Repositório GitHub
- [ ] Estrutura de pastas completa
- [ ] README.md atualizado
- [ ] Todos os 5 documentos commitados
- [ ] Histórico de commits de todos os integrantes
- [ ] Repositório acessível à professora

### Documentos
- [ ] docs/visao-produto.md (completo)
- [ ] docs/stakeholders.md (completo)
- [ ] docs/regras-negocio.md (5-8 regras + rastreabilidade de 2)
- [ ] docs/user-stories.md (5-10 stories com critérios)
- [ ] docs/mvp.md (essenciais + futuras + justificativa)

### Gestor de Projetos
- [ ] Ferramenta configurada (Jira/Trello/GitHub Projects)
- [ ] Backlog completo
- [ ] Quadro Kanban organizado
- [ ] Todas as tarefas distribuídas
- [ ] Movimentação dos cartões evidenciada
- [ ] Permissão de visualização concedida à professora

### Rastreabilidade
- [ ] Pelo menos 2 regras de negócio com impactos documentados em:
  - [ ] User Stories
  - [ ] BPMN (validar com Integrante 2)
  - [ ] Casos de Uso (validar com Integrante 3)
  - [ ] Arquitetura (validar com Integrante 4)
  - [ ] Requisitos não funcionais

### Preparação para Banca
- [ ] Capaz de explicar cada documento produzido
- [ ] Capaz de justificar decisões de priorização
- [ ] Capaz de explicar rastreabilidade das regras
- [ ] Capaz de defender escolhas no MVP
- [ ] Preparado para perguntas sobre requisitos

---

## Perguntas Esperadas na Banca

Prepare-se para responder:

### Sobre Requisitos
1. Por que esse problema é relevante?
2. Como validaram as necessidades dos stakeholders?
3. Quais foram os critérios para definir o MVP?

### Sobre Regras de Negócio
4. Como essa regra impactou a arquitetura?
5. Por que essa regra é importante para o negócio?
6. Existem exceções a essa regra?

### Sobre User Stories
7. Como derivaram as stories das regras de negócio?
8. Esses critérios de aceitação são testáveis?
9. Por que essa story ficou fora do MVP?

### Sobre Colaboração
10. Como organizaram o trabalho da equipe?
11. Como lidaram com dependências entre tarefas?
12. Qual foi sua contribuição específica?

---

## Recursos e Referências

### Ferramentas Recomendadas

**Para Markdown:**
- VSCode com extensão Markdown Preview
- Typora
- StackEdit

**Para Kanban:**
- Trello (mais simples)
- GitHub Projects (integrado ao repo)
- Jira (mais robusto)

### Templates e Exemplos

Consultar no repositório:
- Exemplos de user stories
- Templates de documentação
- Guias de estilo

### Documentação de Apoio

- Meta-requisitos da disciplina
- Materiais das aulas
- Bibliografia da disciplina

---

## Observações Importantes

### Do META-REQUISITOS (Seção 11)

> "É permitido utilizar ferramentas de IA generativa como apoio aos estudos e à elaboração dos artefatos. Entretanto, todos os integrantes deverão ser capazes de compreender, explicar e justificar tecnicamente as soluções apresentadas."

⚠️ **ATENÇÃO:** Você deve entender profundamente cada artefato que criar, independente de usar IA ou não.

### Foco na Qualidade

Do META-REQUISITOS (Considerações Finais):

> "O objetivo desta atividade não é produzir a maior quantidade possível de documentação, mas demonstrar a capacidade de aplicar os conceitos estudados [...]. A qualidade das decisões, a coerência entre os artefatos produzidos e a capacidade de argumentação técnica terão maior relevância do que a quantidade de documentos gerados."

✅ **Priorize:** Consistência, rastreabilidade e argumentação técnica  
❌ **Evite:** Documentação excessiva sem propósito claro

---

## Contato e Dúvidas

Para dúvidas sobre:
- **Requisitos técnicos:** Consultar professora ou materiais da disciplina
- **Divisão de tarefas:** Alinhar com os outros 3 integrantes
- **Ferramentas:** Documentação oficial das ferramentas escolhidas

---

**Última atualização:** [Data]  
**Responsável:** Henrique K. Tonel  
**Disciplina:** Modelagem e Projetos em Engenharia de Software  
**Professora:** Fabricia Roos
