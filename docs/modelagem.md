# Modelagem do Projeto

## Papel dos artefatos

- **BPMN:** mostra o processo de negócio, incluindo criação de turma, matricula, publicação de atividade, entrega, correção e validação.
- **UML:** representa os atores e principais casos de uso do sistema.
- **C4:** descreve a arquitetura, seus containers e as responsabilidades tecnicas de cada parte.

Esses artefatos não são independentes: eles formam uma linha de rastreabilidade entre problema, regra de negocio, comportamento esperado e suporte arquitetural.

## Leitura integrada

| Tema | BPMN | UML | C4 |
|---|---|---|---|
| Autorizacao de professor | Publicacao de atividade na raia Professor | UC01, UC02, UC03 | API Server com JWT e RBAC |
| Prazo de entrega | Gateway de prazo no envio | UC04, UC05 | Servico de prazo e PostgreSQL |
| Acesso a turma | Matricula antes de acessar conteudo | UC06, UC07 | Middleware valida matricula |
| Upload de arquivos | Validacao antes do envio | UC08 | Web App, API e Object Storage |
| Avaliacao | Correcao e liberacao de feedback | UC10 | Regra de nota e persistencia relacional |
| Criacao de turma | Definicao de professor responsavel | UC12 | Constraint no banco e validacao na API |

## Regras criticas representadas

- RN01 aparece no fluxo de publicacao, nos casos de uso do professor e no RBAC da arquitetura.
- RN02 aparece na decisao de prazo, na visualizacao de entregas e no status persistido no banco.
- RN03 aparece na matricula via codigo e na validacao de acesso a conteudos.
- RN06 aparece na correcao de entregas e na validacao de notas.
- RN08 aparece na criacao de turma e na integridade referencial do banco.

## Como defender na banca

A defesa deve mostrar pelo menos um caminho completo, por exemplo:

```text
RN01 -> US03 -> BPMN publicacao de atividade -> UC01 -> API Server com JWT/RBAC
```

Outro caminho importante:

```text
RN08 -> US10 -> BPMN criacao de turma -> UC12 -> constraint turma-professor
```

O documento `docs/rastreabilidade.md` contem a matriz completa para consulta.
