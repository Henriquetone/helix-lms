# MVP - Minimum Viable Product

## Objetivo do MVP

O MVP do Helix LMS valida o ciclo essencial de uma sala de aula online: criacao de turma, matricula, publicacao de atividade, entrega, correcao e acompanhamento de notas.

O escopo foi priorizado para entregar valor direto a professores e estudantes antes de expandir para relatorios avancados, comunicacao sincronica ou recursos institucionais mais sofisticados.

## Funcionalidades essenciais

### Gestao de turmas e acesso

- US01 - Visualizar turmas matriculadas.
- US02 - Entrar em turma via codigo.
- US10 - Criar turma com professor responsavel.

**Justificativa:** Turma, matricula e professor responsavel formam a base do dominio. Sem isso, nao ha contexto seguro para atividades, entregas ou avaliacoes.

### Gestao de atividades

- US03 - Gerenciar atividades.

**Justificativa:** A atividade e o principal mecanismo de organizacao do trabalho academico entre professor e estudante. A mesma historia cobre criacao e edicao para manter o conjunto dentro do limite de 5 a 10 User Stories.

### Gestao de entregas

- US04 - Submeter entrega de atividade.
- US05 - Visualizar entregas da turma.

**Justificativa:** Fecha o fluxo de publicacao e permite ao professor acompanhar cumprimento de prazos, arquivos enviados e pendencias.

### Avaliacao

- US06 - Atribuir nota e feedback.
- US07 - Acompanhar notas.

**Justificativa:** Completa o ciclo pedagogico com devolutiva ao estudante e registro de desempenho.

## Funcionalidades futuras

- US08 - Reabrir atividade encerrada.
- US09 - Dashboard institucional para coordenador.
- Chat em tempo real.
- Forum por turma.
- Videoconferencia integrada.
- Gamificacao.
- Provas online com correcao automatica.
- Integracoes externas com sistemas academicos.

## Justificativa de priorizacao

As funcionalidades de avaliacao e entrega foram priorizadas antes de comunicacao avancada porque resolvem o problema central do produto: organizar o ciclo de atividades academicas. Chat, forum e videoconferencia sao uteis, mas podem ser substituidos temporariamente por canais externos. Ja entrega, prazo, correcao e nota sao parte do processo principal que o Helix LMS precisa controlar.

## Criterios usados

| Criterio | Pergunta de avaliacao |
|---|---|
| Valor para usuario | Resolve o problema principal de professores e estudantes? |
| Dependencia | Outras funcionalidades precisam disso para existir? |
| Viabilidade tecnica | Pode ser modelado e implementado sem dependencias externas complexas? |
| Risco | A ausencia dessa funcionalidade compromete o MVP? |
| Rastreabilidade | A funcionalidade deriva de regras de negocio e aparece nos artefatos? |

## Matriz de priorizacao

| User Story | Valor | Viabilidade | Dependencia | Complexidade | Prioridade | Versao |
|---|---|---|---|---|---|---|
| US01 | Alto | Alta | Base | Baixa | Critica | MVP |
| US02 | Alto | Alta | US10 | Baixa | Critica | MVP |
| US03 | Alto | Alta | US01, US10 | Media | Critica | MVP |
| US04 | Alto | Alta | US03 | Media | Critica | MVP |
| US05 | Alto | Alta | US04 | Media | Critica | MVP |
| US06 | Alto | Alta | US05 | Media | Critica | MVP |
| US07 | Alto | Alta | US06 | Baixa | Alta | MVP |
| US08 | Medio | Media | US03 | Media | Baixa | v2.0 |
| US09 | Medio | Baixa | Dados historicos | Alta | Baixa | v2.0 |
| US10 | Alto | Alta | Base | Baixa | Critica | MVP |

## Metricas de validacao

- Pelo menos 80% dos professores conseguem criar e publicar uma atividade em menos de 5 minutos.
- Pelo menos 90% dos estudantes conseguem submeter uma entrega sem suporte externo.
- Reducao de 50% no tempo de organizacao manual de entregas.
- 70% das turmas piloto usam o sistema regularmente durante o periodo de validacao.
- Satisfacao media acima de 7 em escala de 0 a 10 entre usuarios piloto.

## Escopo fora do MVP

O MVP nao inclui comunicacao sincronica, BI avancado, aplicativo mobile nativo, integracoes externas ou automacao complexa de provas. Essas funcionalidades exigem mais infraestrutura e so devem ser priorizadas apos validacao do ciclo principal.
