# Helix LMS

Sistema de Gestao de Sala de Aula Online  
Modelagem e Projetos em Engenharia de Software

Integrantes: Henrique Kitzmann Tonel, Erik Luan Lasch, Pedro Henrique Bickel Steinbrenner, Matheus Oliveira

---

# 1. Problema e Proposta

- Gestao academica dispersa entre canais, arquivos e planilhas.
- Professores precisam publicar atividades, receber entregas e avaliar com menos retrabalho.
- Estudantes precisam de clareza sobre turmas, prazos, entregas e notas.
- Coordenadores precisam acompanhar a evolucao pedagogica sem interferir no trabalho do professor.

**Proposta:** centralizar o ciclo de turma, atividade, entrega e avaliacao em uma plataforma unica.

---

# 2. Stakeholders

| Stakeholder | Necessidade principal |
|---|---|
| Estudante | Acessar turmas, enviar entregas e consultar feedbacks |
| Professor | Criar atividades, acompanhar entregas e avaliar |
| Coordenador | Visualizar indicadores institucionais |
| Administrador | Gerenciar usuarios, perfis e turmas |

---

# 3. MVP

Fluxo principal:

```text
Criar turma -> Matricular estudante -> Publicar atividade -> Entregar -> Corrigir -> Consultar nota
```

Funcionalidades essenciais:

- US01, US02 e US10: turmas, matricula e professor responsavel.
- US03: gerenciamento de atividades.
- US04 e US05: entrega e visualizacao de entregas.
- US06 e US07: nota e feedback.

---

# 4. Regras de Negocio Criticas

| Regra | Impacto direto |
|---|---|
| RN01 - Apenas professores criam atividades | Exige JWT, RBAC e validacao no backend |
| RN02 - Entregas atrasadas sinalizadas | Exige gateway de prazo e status persistido |
| RN03 - Estudante acessa apenas turmas matriculadas | Exige validacao de vinculo estudante-turma |
| RN08 - Turma com professor responsavel | Exige validacao de criacao e integridade referencial |

---

# 5. User Stories

As historias foram organizadas em torno do ciclo do MVP.

Exemplos:

- US03: Como professor, desejo criar atividades para disponibilizar tarefas.
- US04: Como estudante, desejo submeter entrega para enviar meu trabalho.
- US06: Como professor, desejo atribuir nota e feedback.
- US10: Como administrador, desejo criar turma com professor responsavel.

Cada historia possui criterios de aceitacao, regras e casos de uso relacionados.

---

# 6. Rastreabilidade

| Regra | User Story | BPMN | UML | Arquitetura |
|---|---|---|---|---|
| RN01 | US03 | Publicacao por professor | UC01, UC02, UC03 | JWT + RBAC |
| RN02 | US04, US05 | Gateway de prazo | UC04, UC05 | Servico de prazo |
| RN03 | US01, US02 | Matricula antes do acesso | UC06, UC07 | Middleware de matricula |
| RN08 | US10 | Criacao com professor | UC12 | Constraint turma-professor |

Documento completo: `docs/rastreabilidade.md`.

---

# 7. BPMN

Artefato: `bpmn/BPMN.png`

O BPMN representa:

- criacao e acesso a turma;
- publicacao de atividade;
- submissao de entrega;
- validacao de prazo;
- correcao e liberacao de feedback.

Pontos de defesa: regras de prazo, autorizacao e avaliacao aparecem como decisoes do processo.

---

# 8. UML - Casos de Uso

Artefato: `uml/UML.png`

Principais atores:

- Estudante.
- Professor.
- Coordenador.
- Administrador.

Casos centrais:

- Criar Atividade.
- Submeter Entrega.
- Atribuir Nota.
- Criar Turma.
- Visualizar Dashboard Institucional.

---

# 9. Arquitetura

Estilo escolhido: arquitetura hibrida.

- Camadas para o fluxo principal.
- Eventos para notificacoes e analise pedagogica.

```text
Web App -> API Server -> Dominio/Servicos -> Banco
                          |
                          `-> Fila -> Workers
```

Justificativa: manter o MVP simples e separar tarefas que nao devem bloquear a resposta da API.

---

# 10. C4

Artefatos:

- `c4/contexto.md`
- `c4/containers.md`
- `c4/C4.png`

Containers principais:

- Web App.
- API Server.
- PostgreSQL.
- Object Storage.
- Fila Redis.
- Worker de Email.
- Servico externo de Email.

---

# 11. Decisoes Arquiteturais

| Decisao | Justificativa |
|---|---|
| JWT | Autenticacao stateless para Web App e evolucao mobile |
| RBAC | Perfis claros: estudante, professor, coordenador e administrador |
| Banco relacional | Dominio com relacoes fortes e integridade |
| Object Storage | Arquivos fora do banco transacional |
| Eventos | Notificacoes e analises sem bloquear o fluxo principal |

---

# 12. Funcionalidade Inovadora

**Analise Pedagogica Preditiva**

O modulo identifica estudantes e turmas com sinais de risco usando dados ja produzidos pelo MVP:

- entregas atrasadas;
- ausencia de entregas;
- notas recentes;
- recorrencia de reaberturas;
- indicadores por turma.

Beneficio: apoiar intervencao pedagogica antes que o problema fique critico.

---

# 13. Viabilidade da Inovacao

Primeira versao com regras explicaveis:

| Indicador | Regra inicial |
|---|---|
| Risco de atraso | 2 ou mais entregas atrasadas |
| Risco de desempenho | Media abaixo de 6,0 |
| Baixa participacao | Sem entregas em atividades abertas |
| Turma em atencao | Mais de 30% com atraso |

Impacto arquitetural: eventos, fila, worker e dashboard institucional.

---

# 14. Colaboracao

Evidencias:

- Repositorio GitHub com artefatos versionados.
- Jira/Kanban para backlog e distribuicao de tarefas.
- Divisao por pilares: requisitos, BPMN, UML, arquitetura e apresentacao.
- Diario de sprint com responsabilidades e evidencias.

Documento: `docs/sprint.md`.

---

# 15. Encerramento

O Helix LMS apresenta uma solucao coerente para o ciclo academico:

- problema claro;
- regras de negocio explicitas;
- User Stories rastreaveis;
- BPMN, UML e C4 integrados;
- arquitetura justificada por requisitos;
- funcionalidade inovadora viavel.

Perguntas.
