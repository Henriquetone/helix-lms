# Regras de Negocio

Este documento registra as regras de negocio centrais do Helix LMS e mostra como elas influenciam requisitos, processos, casos de uso, arquitetura e requisitos nao funcionais.

## RN01 - Apenas professores podem criar atividades

**Descricao:** Somente usuarios com perfil Professor, vinculados a uma turma, podem criar, editar e excluir atividades nessa turma.

**Justificativa:** Mantem controle pedagogico e evita publicacao indevida de tarefas.

**Impactos:**
- User Story: US03.
- BPMN: publicacao de atividade ocorre na raia Professor e depende de validacao de perfil.
- Casos de Uso: UC01 Criar Atividade, UC02 Editar Atividade, UC03 Excluir Atividade.
- Arquitetura: autenticacao JWT, RBAC e validacao no backend.
- RNFs: seguranca e auditoria.

---

## RN02 - Entregas apos prazo devem ser sinalizadas

**Descricao:** O sistema deve identificar entregas feitas depois do prazo. A entrega pode ser aceita, mas deve ficar marcada como atrasada.

**Justificativa:** Preserva flexibilidade pedagogica sem esconder o descumprimento de prazo.

**Impactos:**
- User Stories: US04 e US05.
- BPMN: gateway compara data/hora de envio com o prazo da atividade.
- Casos de Uso: UC04 Submeter Entrega e UC05 Visualizar Entregas.
- Arquitetura: servico de prazo calcula `entregue_atraso` e persiste o status.
- RNFs: confiabilidade de horario e usabilidade na sinalizacao.

---

## RN03 - Estudante so pode acessar turmas nas quais esta matriculado

**Descricao:** Conteudos, atividades e entregas de uma turma so podem ser acessados por estudantes matriculados nela.

**Justificativa:** Garante privacidade, organizacao e controle de acesso ao conteudo academico.

**Impactos:**
- User Stories: US01 e US02.
- BPMN: a matricula via codigo antecede o acesso ao conteudo da turma.
- Casos de Uso: UC06 Visualizar Turmas e UC07 Acessar Conteudo da Turma.
- Arquitetura: middleware valida o vinculo estudante-turma em requisicoes protegidas.
- RNFs: seguranca e desempenho com cache de permissoes.

---

## RN04 - Limite de tamanho para arquivos enviados

**Descricao:** Arquivos enviados por professores ou estudantes devem respeitar limite maximo de 50MB por arquivo.

**Justificativa:** Evita sobrecarga de armazenamento, transferencia e processamento.

**Impactos:**
- User Stories: US03 e US04.
- BPMN: validacao antes do envio de material ou entrega.
- Casos de Uso: UC08 Upload de Arquivo.
- Arquitetura: validacao no Web App e na API, com armazenamento em Object Storage.
- RNFs: desempenho e usabilidade.

---

## RN05 - Professor pode reabrir atividade encerrada

**Descricao:** Professores podem reabrir atividades cujo prazo expirou para permitir novas entregas em situacoes excepcionais.

**Justificativa:** Da autonomia pedagogica ao professor sem apagar o historico do processo.

**Impactos:**
- User Story: US08.
- BPMN: fluxo alternativo de reabertura com notificacao aos estudantes.
- Caso de Uso: UC09 Reabrir Atividade.
- Arquitetura: campo de status da atividade, historico de mudancas e evento de notificacao.
- RNFs: auditoria e rastreabilidade.

---

## RN06 - Notas devem estar entre 0 e 10

**Descricao:** Todas as notas atribuidas devem estar no intervalo de 0 a 10, com ate duas casas decimais.

**Justificativa:** Padroniza a avaliacao conforme pratica academica brasileira.

**Impactos:**
- User Stories: US06 e US07.
- BPMN: correcao de entrega inclui validacao da nota antes da liberacao.
- Caso de Uso: UC10 Atribuir Nota.
- Arquitetura: validacao de dominio no backend e tipo `DECIMAL(4,2)` no banco.
- RNFs: integridade e usabilidade.

---

## RN07 - Coordenador pode visualizar todas as turmas

**Descricao:** Coordenadores possuem permissao de leitura sobre todas as turmas da instituicao, independentemente do professor responsavel.

**Justificativa:** Permite supervisao pedagogica e acompanhamento institucional.

**Impactos:**
- User Story: US09.
- BPMN: consulta institucional separada do fluxo operacional do estudante.
- Caso de Uso: UC11 Visualizar Dashboard Institucional.
- Arquitetura: permissao `read:all_turmas` e endpoint institucional.
- RNFs: seguranca e desempenho com paginacao.

---

## RN08 - Turma deve ter pelo menos um professor responsavel

**Descricao:** Toda turma criada no sistema deve ter ao menos um professor responsavel. Nao e permitida turma sem professor.

**Justificativa:** Garante responsabilidade pedagogica e clareza de gestao.

**Impactos:**
- User Story: US10.
- BPMN: criacao da turma exige professor responsavel antes de liberar codigo de acesso.
- Caso de Uso: UC12 Criar Turma.
- Arquitetura: validacao na API e constraint `NOT NULL` no relacionamento turma-professor.
- RNFs: integridade e usabilidade.

---

## Matriz resumida de rastreabilidade

| Regra | User Stories | BPMN | UML | Arquitetura/C4 |
|---|---|---|---|---|
| RN01 | US03 | Publicacao por Professor | UC01, UC02, UC03 | JWT, RBAC e middleware no API Server |
| RN02 | US04, US05 | Gateway de prazo | UC04, UC05 | Servico de prazo e status no PostgreSQL |
| RN03 | US01, US02 | Matricula antes do acesso | UC06, UC07 | Validacao de vinculo estudante-turma |
| RN04 | US03, US04 | Validacao de upload | UC08 | Web App, API e Object Storage |
| RN05 | US08 | Reabertura e notificacao | UC09 | Status, historico e evento assincrono |
| RN06 | US06, US07 | Validacao de nota | UC10 | Regra de dominio e `DECIMAL(4,2)` |
| RN07 | US09 | Consulta institucional | UC11 | Permissao de leitura global |
| RN08 | US10 | Criacao com professor | UC12 | Integridade referencial |
