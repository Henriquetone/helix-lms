# Arquitetura de Software – Helix LMS

## Visão geral

O Helix LMS é um sistema de gestão de sala de aula online projetado para centralizar a gestão de turmas, atividades, entregas e avaliações entre professores e estudantes. Esta documentação registra as principais decisões arquiteturais tomadas durante o projeto, suas justificativas e impactos técnicos.

## Estilo arquitetural

A solução foi modelada com uma arquitetura híbrida, combinando:

- camadas para o fluxo principal do sistema;
- eventos para operações assíncronas, como notificações e análise pedagógica.

Essa abordagem é adequada porque o MVP precisa ser claro e simples, mas também precisa suportar processos que não devem bloquear a experiência do usuário.

### Arquitetura em camadas

O fluxo principal segue uma estrutura em camadas com separação entre apresentação, aplicação, domínio e infraestrutura:

```text
Camada de apresentação -> API -> Camada de domínio -> Banco de dados
```

### Processamento assíncrono

Ações como publicação de atividade, registro de entrega e liberação de nota podem gerar eventos para uma fila, permitindo que workers processem notificações e análises sem travar a operação principal.

## Principais decisões arquiteturais

### DA01 – Controle de acesso baseado em papéis (RBAC)

O sistema possui perfis distintos e exige controle granular de acesso. A solução foi pensada para validar permissões no backend, garantindo consistência entre regras de negócio e arquitetura.

### DA02 – Autenticação via JWT

A comunicação entre frontend e backend é autenticada de forma segura e stateless, favorecendo escalabilidade e integração futura com aplicações móveis.

### DA03 – Banco de dados relacional

O domínio é fortemente relacional, com entidades como usuário, turma, atividade, entrega e avaliação. Por isso, o uso de um banco relacional é a escolha mais adequada.

### DA04 – Armazenamento de arquivos separado

Arquivos de atividades e entregas podem ser armazenados em um serviço de object storage, desacoplando o armazenamento do servidor de aplicação.

### DA05 – Processamento assíncrono para notificações

Notificações e ações complementares não devem bloquear o retorno da API ao usuário. O uso de fila de eventos é uma decisão importante para manter a resposta rápida.

### DA06 – Módulo de análise pedagógica isolado

A funcionalidade inovadora foi separada em um módulo próprio para evoluir independentemente do fluxo principal do MVP.

## Rastreabilidade com a modelagem

A arquitetura foi construída para refletir o que foi modelado em BPMN, UML e C4:

- o BPMN mostra o fluxo de negócio e as validações;
- o UML representa o domínio e os casos de uso;
- o C4 explica a estrutura arquitetural e a comunicação entre partes do sistema.

## Observação sobre a entrega individual

A parte de modelagem do Erik manteve a visão do processo, do domínio e da arquitetura de forma coerente com estas decisões, contribuindo para a documentação final do projeto.
