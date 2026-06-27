# Arquitetura de Software - Helix LMS

## Visao geral

O Helix LMS foi modelado para centralizar turmas, atividades, entregas, avaliacoes e acompanhamento pedagogico. A arquitetura precisa atender ao MVP sem perder coerencia com regras de seguranca, prazo, integridade de dados e evolucao futura.

## Estilo arquitetural escolhido

A solucao adota uma **arquitetura hibrida**:

- O nucleo transacional usa arquitetura em camadas.
- Notificacoes e analises pedagogicas usam eventos e processamento assincrono.

Essa escolha evita uma arquitetura pesada para o MVP, mas prepara o sistema para operacoes que nao devem bloquear a experiencia do usuario, como envio de e-mails e calculo de indicadores.

```text
Web App -> API Server -> Dominio/Servicos -> Banco de Dados
                          |
                          `-> Fila -> Workers -> Email/Analises
```

## Por que nao apenas camadas?

Uma arquitetura em camadas pura seria suficiente para cadastro, turmas, atividades, entregas e notas. Porem, notificacoes e analise pedagogica preditiva ficariam acopladas ao tempo de resposta da API. A abordagem hibrida mantem o fluxo principal simples e desloca tarefas secundarias para processamento assincrono.

## Principais responsabilidades

### Web App
- Interface para estudante, professor, coordenador e administrador.
- Validacoes de usabilidade, como tamanho de arquivo antes do envio.
- Exibicao de status de entregas, notas e dashboards.

### API Server
- Autenticacao JWT.
- Autorizacao por RBAC.
- Regras de negocio de turmas, atividades, entregas e avaliacoes.
- Publicacao de eventos para notificacoes e analises.

### Banco de Dados Relacional
- Persistencia de usuarios, turmas, matriculas, atividades, entregas e avaliacoes.
- Constraints de integridade, como professor obrigatorio na turma e nota entre 0 e 10.

### Object Storage
- Armazenamento de materiais e entregas.
- Separacao entre arquivos binarios e dados transacionais.

### Fila e Workers
- Envio de notificacoes sem bloquear a API.
- Processamento de indicadores da funcionalidade inovadora.

## Rastreabilidade arquitetural

| Regra/Requisito | Decisao arquitetural |
|---|---|
| RN01 - Apenas professores criam atividades | JWT + RBAC + validacao no backend |
| RN02 - Entregas atrasadas sinalizadas | Servico de prazo e status persistido |
| RN03 - Estudante acessa turmas matriculadas | Middleware valida vinculo estudante-turma |
| RN04 - Limite de arquivos | Validacao no Web App, API e Object Storage |
| RN06 - Notas entre 0 e 10 | Regra de dominio e constraint no banco |
| RN08 - Turma com professor responsavel | Validacao de criacao e integridade referencial |
| Funcionalidade inovadora | Eventos, fila e worker de analise pedagogica |

## Funcionalidade inovadora

O modulo de analise pedagogica preditiva fica isolado do fluxo principal. Ele consome dados ja produzidos pelo MVP, como atrasos, notas e participacao, para gerar indicadores de risco para professores e coordenadores.

Essa separacao reduz acoplamento e permite evoluir a inovacao sem comprometer as operacoes essenciais do LMS.

## Conclusao

A arquitetura hibrida e justificavel porque o MVP permanece simples e compreensivel, enquanto os pontos que exigem desacoplamento, como notificacoes e analises, sao tratados por eventos. Assim, a arquitetura responde diretamente aos requisitos e nao apenas a uma escolha tecnologica generica.
