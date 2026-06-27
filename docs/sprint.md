# Diario de Sprint - Helix LMS

**Periodo:** 19 de junho a 26 de junho de 2026  
**Projeto:** Helix LMS - Sistema de Gestao de Sala de Aula Online  
**Status final:** Artefatos obrigatorios consolidados para banca

## 1. Visao geral da sprint

A sprint foi dedicada a concepcao, modelagem, documentacao e preparacao da defesa tecnica do Helix LMS. O trabalho partiu dos meta-requisitos da disciplina e resultou em artefatos de requisitos, modelagem, arquitetura, rastreabilidade, colaboracao e apresentacao.

## 2. Responsabilidades

| Integrante | Responsabilidades principais | Evidencias no repositorio |
|---|---|---|
| Henrique Kitzmann Tonel | Coordenacao, README, requisitos, sprint, rastreabilidade, inovacao e apresentacao | `README.md`, `docs/sprint.md`, `docs/rastreabilidade.md`, `docs/funcionalidade-inovadora.md`, `apresentacao/apresentacao-final.md` |
| Matheus Oliveira | Arquitetura, C4 e decisoes arquiteturais | `docs/arquitetura.md`, `docs/decisoes-arquiteturais.md`, `c4/contexto.md`, `c4/containers.md`, `c4/C4.png` |
| Erik Luan Lasch | Modelagem BPMN e processo de negocio | `bpmn/BPMN.png`, `docs/modelagem.md` |
| Pedro Henrique Bickel Steinbrenner | UML, casos de uso e engenharia de software | `uml/UML.png`, `docs/engenharia-software.md`, `docs/user-stories.md` |

## 3. Decisoes tomadas

### Arquitetura hibrida

A equipe adotou arquitetura hibrida: camadas no fluxo principal e eventos para notificacoes e analise pedagogica. A decisao equilibra simplicidade do MVP com evolucao futura.

### Controle de acesso com JWT e RBAC

JWT autentica as requisicoes e RBAC controla permissoes por perfil. Essa decisao suporta RN01, RN03, RN07 e RN08.

### Banco relacional

O dominio possui relacoes fortes entre usuarios, turmas, matriculas, atividades, entregas e avaliacoes. Por isso, banco relacional foi escolhido para preservar integridade e rastreabilidade.

### Priorizacao do MVP

O MVP foi organizado em torno do ciclo:

```text
criar turma -> matricular estudante -> publicar atividade -> entregar -> corrigir -> consultar nota
```

Funcionalidades como reabertura e dashboard institucional foram deixadas como evolucao, exceto a base da analise pedagogica, documentada como funcionalidade inovadora.

## 4. Dificuldades e solucoes

| Dificuldade | Solucao adotada |
|---|---|
| Rastreabilidade fraca entre artefatos | Criacao de `docs/rastreabilidade.md` e inclusao de casos de uso em cada User Story |
| RN08 sem User Story correspondente | Inclusao da US10 e ajuste em regras, MVP e rastreabilidade |
| Conflito entre arquitetura em camadas e hibrida | Consolidacao da decisao como arquitetura hibrida com nucleo em camadas |
| Funcionalidade inovadora pouco concreta | Criacao de `docs/funcionalidade-inovadora.md` com problema, beneficio, viabilidade e impacto arquitetural |
| Apresentacao ainda em formato de roteiro | Criacao de `apresentacao/apresentacao-final.md` como deck final em Markdown |

## 5. Evidencias objetivas de conclusao

| Entregavel | Evidencia |
|---|---|
| Visao do Produto | `docs/visao-produto.md` |
| Stakeholders | `docs/stakeholders.md` |
| Regras de Negocio | `docs/regras-negocio.md` |
| User Stories | `docs/user-stories.md` com 10 historias |
| MVP | `docs/mvp.md` |
| BPMN | `bpmn/BPMN.png` |
| UML | `uml/UML.png` |
| Arquitetura | `docs/arquitetura.md` |
| C4 | `c4/contexto.md`, `c4/containers.md`, `c4/C4.png` |
| Decisoes arquiteturais | `docs/decisoes-arquiteturais.md` |
| Rastreabilidade | `docs/rastreabilidade.md` |
| Funcionalidade inovadora | `docs/funcionalidade-inovadora.md` |
| Apresentacao | `apresentacao/apresentacao-final.md` |

## 6. Colaboracao

O trabalho foi organizado por pilares: requisitos, modelagem, arquitetura e apresentacao. O Jira/Kanban foi usado para distribuir tarefas e o GitHub para versionar a evolucao dos artefatos.

Para defesa oral, a equipe deve mostrar:

- o historico de commits do GitHub;
- o quadro Jira/Kanban;
- a divisao de responsabilidades desta sprint;
- a relacao entre cada integrante e os artefatos sob sua responsabilidade.

## 7. Liçoes aprendidas

- Rastreabilidade precisa ser planejada desde o inicio, nao adicionada apenas no final.
- Diagramas ficam mais defensaveis quando cada elemento e conectado a uma regra ou historia.
- A arquitetura deve ser explicada por trade-offs, nao por lista de tecnologias.
- A funcionalidade inovadora precisa mostrar viabilidade tecnica, limites e impacto arquitetural.

