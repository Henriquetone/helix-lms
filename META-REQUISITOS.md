# AVALIAÇÃO INTEGRADORA – MODELAGEM E PROJETO DE SOFTWARE

**Disciplina:** Modelagem e Projetos em Engenharia de Software  
**Professora:** Fabricia Roos

## 1. Objetivo

Esta avaliação tem como objetivo verificar a capacidade dos estudantes de aplicar os conhecimentos desenvolvidos ao longo do semestre em um contexto próximo da prática profissional de Engenharia de Software.

Os grupos deverão conceber, modelar, documentar e defender tecnicamente a proposta de um Sistema de Gestão de Sala de Aula Online, semelhante ao Google Classroom, utilizando técnicas de Engenharia de Software, Gestão Ágil, Modelagem de Processos e Arquitetura de Software estudadas na disciplina.

O desafio deverá contemplar conhecimentos relacionados a:

- Engenharia de Software;
- Requisitos de Software;
- Regras de Negócio;
- User Stories;
- MVP (Minimum Viable Product);
- BPMN;
- UML;
- Arquitetura de Software;
- Modelo C4;
- Gestão Ágil com Kanban;
- Git e GitHub;
- Tomada de Decisões Arquiteturais.

## 2. Formação dos Grupos

- Grupos de 3 ou 4 estudantes.
- Todos os integrantes deverão participar da elaboração dos artefatos.
- A participação individual deverá ser evidenciada pelo histórico do GitHub e do gestor de projetos.
- Durante a banca, todos os integrantes deverão estar aptos a responder perguntas sobre qualquer artefato produzido pelo grupo.

## 3. Situação-Problema

Uma instituição de ensino pretende desenvolver uma plataforma digital para apoiar a gestão de turmas, atividades, avaliações e comunicação entre professores e estudantes.

Sua equipe atuará como uma consultoria de Engenharia de Software responsável pela concepção completa da solução.

A proposta deverá contemplar desde a identificação do problema até a definição da arquitetura da solução.

## 4. Organização da Atividade

### Aula 1 (2h30)

**Concepção da Solução**

- Definição do problema;
- Identificação dos stakeholders;
- Definição das regras de negócio;
- Elaboração das User Stories;
- Definição do MVP;
- Criação do backlog;
- Organização do quadro Kanban;
- Criação do repositório GitHub.

### Aula 2 (2h30)

**Projeto da Solução**

- BPMN;
- Casos de Uso;
- Arquitetura de Software;
- Modelo C4;
- Decisões arquiteturais;
- Organização da apresentação.

### Aulas 3 e 4

**Bancas de Apresentação**

Apresentação e defesa técnica da solução.

## 5. Ferramentas Obrigatórias

### GitHub

O GitHub deverá ser utilizado para:

- armazenamento dos artefatos;
- documentação do projeto;
- controle de versões;
- evidências de colaboração.
- disponibilização da entrega final do projeto.

### Gestor de Projetos

Cada grupo deverá utilizar uma das seguintes ferramentas:

- Jira;
- Trello;
- GitHub Projects.

A ferramenta será utilizada para:

- gerenciamento do backlog;
- organização do quadro Kanban;
- distribuição das tarefas;
- acompanhamento da evolução do projeto.

## 6. Estrutura Mínima do Repositório

O repositório deverá conter, no mínimo, a seguinte estrutura:

```
docs/
├── visao-produto.md
├── stakeholders.md
├── regras-negocio.md
├── user-stories.md
├── mvp.md
├── arquitetura.md
├── sprint.md
└── README.md
bpmn/
uml/
c4/
apresentacao/
```

### Exemplo

```
classroom-project/
docs/
├── visao-produto.md
├── regras-negocio.md
├── user-stories.md
├── arquitetura.md
bpmn/
└── entrega-atividade.bpmn
uml/
└── casos-de-uso.png
c4/
├── contexto.png
└── containers.png
apresentacao/
└── apresentacao-final.pdf
```

## 7. Entregáveis Obrigatórios

### 7.1 Visão do Produto

Descrever:

- problema a ser resolvido;
- público-alvo;
- objetivos da solução;
- benefícios esperados.

### 7.2 Stakeholders

Identificar os principais envolvidos no sistema.

Exemplos:

- estudantes;
- professores;
- coordenadores;
- administradores.

### 7.3 Regras de Negócio

Identifique entre 5 e 8 regras de negócio relevantes para o domínio do sistema e demonstre como pelo menos 2 delas influenciaram requisitos, processos de negócio (BPMN), modelagem ou decisões arquiteturais.

**Exemplo**

RN01 – Apenas professores podem criar atividades.

Possíveis impactos:

- User Story: Como professor, desejo criar atividades para disponibilizar tarefas aos estudantes.
- Caso de Uso: Criar Atividade.
- BPMN: atividade executada exclusivamente pelo professor.
- Arquitetura: necessidade de autenticação e controle de autorização.
- Requisito Não Funcional: segurança.

O objetivo não é apenas listar regras, mas demonstrar sua influência na solução proposta.

### 7.4 User Stories

Produzir entre 5 e 10 User Stories.

Cada User Story deverá conter:

- identificador;
- descrição;
- critérios de aceitação.

### 7.5 MVP

Definir:

- funcionalidades essenciais;
- funcionalidades futuras;
- justificativa da priorização.

### 7.6 BPMN

Modelar pelo menos um processo de negócio relevante.

Exemplos:

- matrícula em turma;
- publicação de atividade;
- entrega de atividade;
- correção de atividade.

### 7.7 UML

Produzir um Diagrama de Casos de Uso representando as principais funcionalidades do sistema.

### 7.8 Arquitetura de Software

Escolher e justificar uma arquitetura:

- Em Camadas;
- Microserviços;
- Publish-Subscribe;
- Híbrida.

A justificativa deverá considerar os requisitos e o contexto do sistema.

### 7.9 Modelo C4

Produzir:

Nível 1 – Contexto  
Nível 2 – Containers

### 7.10 Decisões Arquiteturais

Identificar e justificar pelo menos 3 decisões arquiteturais relevantes.

Exemplos:

- escolha do estilo arquitetural;
- mecanismo de autenticação;
- estratégia de notificações;
- integração entre componentes.

### 7.11 Diário de Sprint

Criar um arquivo:

```
docs/sprint.md
```

Descrevendo:

- divisão das responsabilidades;
- principais decisões tomadas;
- dificuldades encontradas;
- soluções adotadas.

## 8. Evidências de Colaboração

Os grupos deverão demonstrar que o trabalho foi desenvolvido de forma colaborativa.

### GitHub

Serão observados:

- participação dos integrantes;
- evolução dos artefatos;
- organização do repositório;
- histórico de commits.

Não serão avaliados apenas os artefatos finais, mas também o processo de construção da solução.

### Gestor de Projetos

Serão observados:

- backlog;
- quadro Kanban;
- distribuição de tarefas;
- movimentação dos cartões;
- participação dos integrantes.

O objetivo é evidenciar a colaboração e a organização do trabalho da equipe.

A banca poderá incluir perguntas sobre a contribuição individual de cada integrante e sobre o processo de desenvolvimento adotado pelo grupo.

## 9. Entrega da Avaliação

A entrega deverá ser realizada até a data e horário definidos pelo professor.

Cada grupo deverá submeter:

### 1. Link do Repositório GitHub

O repositório deverá conter todos os artefatos produzidos durante a atividade, incluindo:

- documentação;
- diagramas;
- modelos BPMN;
- modelos UML;
- modelos C4;
- apresentação final;
- demais materiais produzidos pelo grupo.

O repositório deverá permanecer acessível ao professor até o encerramento da disciplina.

### 2. Link do Gestor de Projetos

O grupo deverá disponibilizar o link do quadro utilizado no projeto:

- Jira;
- Trello;
- GitHub Projects.

O quadro deverá permitir a visualização do:

- backlog;
- quadro Kanban;
- histórico de atividades;
- distribuição de tarefas.

Caso a ferramenta utilizada possua restrições de acesso, o grupo deverá conceder permissão de visualização ao professor.

### 3. Apresentação

A apresentação utilizada durante a banca deverá estar disponível no repositório GitHub, preferencialmente na pasta:

```
apresentacao/
```

### Formato de Entrega

O grupo deverá enviar um único documento pdf contendo:

- Nome do Projeto:
- Integrantes:
- Link do GitHub:
- Link do Gestor de Projetos:
- Funcionalidade Inovadora (resumo em até 5 linhas):

## 10. Apresentação Oral

**Tempo:** 20 minutos por grupo

- Até 20 minutos para apresentação da solução;
- Até 5 minutos para arguição da banca.

A apresentação poderá ser realizada por um ou mais integrantes do grupo. Entretanto:

- Todos os integrantes deverão estar presentes durante a banca;
- Todos os integrantes poderão ser questionados individualmente;
- Todos deverão demonstrar conhecimento sobre a solução proposta e os artefatos produzidos.

A incapacidade de explicar ou justificar elementos do projeto poderá impactar a avaliação.

### Estrutura Recomendada da Apresentação

**1. Visão do Produto e MVP (1 a 2 minutos)**

Apresentar:

- problema a ser resolvido;
- público-alvo;
- MVP definido.

**2. Regras de Negócio e Impactos (2 minutos)**

Selecionar uma ou duas regras de negócio relevantes e demonstrar seus impactos na solução.

Exemplo:

```
Regra de Negócio
↓
User Story
↓
BPMN
↓
Arquitetura
↓
Decisão Arquitetural
```

**3. Processo de Negócio (5 minutos)**

Apresentar o BPMN principal do sistema e explicar seu funcionamento.

**4. Arquitetura da Solução (3 a 5 minutos)**

Apresentar:

- arquitetura escolhida;
- justificativas;
- C4 Contexto;
- C4 Containers.

O foco deve estar na explicação das decisões adotadas.

**5. Evidências de Colaboração (1 minuto)**

Apresentar brevemente:

- repositório GitHub;
- histórico de evolução;
- quadro Kanban;
- organização do trabalho da equipe.

**6. Funcionalidade Inovadora (3 a 5 minutos)**

Apresentar:

- a funcionalidade proposta;
- o problema que ela resolve;
- benefícios para os usuários;
- viabilidade técnica;
- impactos na arquitetura.

Esta seção deverá receber atenção especial, pois representa a capacidade do grupo de propor soluções criativas e inovadoras para o contexto apresentado.

## 11. Uso de Inteligência Artificial

É permitido utilizar ferramentas de IA generativa como apoio aos estudos e à elaboração dos artefatos.

Entretanto, todos os integrantes deverão ser capazes de compreender, explicar e justificar tecnicamente as soluções apresentadas.

O uso de IA não substitui o entendimento dos conceitos envolvidos.

## 12. Funcionalidade Inovadora

Cada grupo deverá propor pelo menos uma funcionalidade inovadora para o sistema.

A proposta deverá apresentar:

- descrição;
- benefício esperado;
- viabilidade técnica;
- possíveis impactos arquiteturais.

## 13. Critérios de Avaliação

| Dimensão | Peso |
|----------|------|
| Engenharia de Requisitos (Visão do Produto, Regras de Negócio, User Stories e MVP) | 25% |
| Modelagem (BPMN e Casos de Uso) | 20% |
| Arquitetura (C4, decisões arquiteturais e justificativas) | 25% |
| Colaboração (GitHub e Gestor de Projetos) | 15% |
| Defesa Oral e Inovação | 15% |

## 13. Rubrica de Avaliação

| Critério | Insuficiente | Adequado | Excelente |
|----------|--------------|----------|-----------|
| Engenharia de Requisitos | Artefatos incompletos ou inconsistentes | Artefatos coerentes | Artefatos completos, consistentes e rastreáveis |
| Modelagem | Modelos incompletos ou incorretos | Modelos corretos | Modelos completos e bem integrados |
| Arquitetura | Justificativas superficiais | Decisões coerentes | Decisões bem fundamentadas e alinhadas aos requisitos |
| Colaboração | Poucas evidências de participação | Participação adequada | Excelente colaboração e organização |
| Defesa Oral e Inovação | Domínio limitado do projeto | Boa compreensão da solução | Excelente argumentação técnica, pensamento crítico e capacidade de inovação |

## 14. Relação com a Taxonomia de Bloom

| Nível Cognitivo | Evidências Esperadas |
|-----------------|----------------------|
| Conhecer | Identificação dos conceitos, técnicas e artefatos de Engenharia de Software |
| Compreender | Explicação dos requisitos, processos e decisões tomadas |
| Aplicar | Construção dos artefatos solicitados |
| Analisar | Identificação de impactos entre regras de negócio, requisitos, modelagem e arquitetura |
| Avaliar | Justificativa e defesa das decisões adotadas |
| Inovar | Proposição de funcionalidades e soluções diferenciadas |

## Considerações Finais

O objetivo desta atividade não é produzir a maior quantidade possível de documentação, mas demonstrar a capacidade de aplicar os conceitos estudados ao longo do semestre para conceber, modelar, justificar e defender uma solução de software de forma colaborativa.

A qualidade das decisões, a coerência entre os artefatos produzidos e a capacidade de argumentação técnica terão maior relevância do que a quantidade de documentos gerados.
