# Engenharia de Software

## 1. Contexto

O Helix LMS é um sistema educacional voltado para a gestão de turmas, atividades, entregas e avaliações entre professores, estudantes e coordenadores.

A parte de Engenharia de Software envolve:

- definição de requisitos funcionais e não funcionais
- modelagem de regras de negócio
- rastreabilidade entre artefatos
- alinhamento com os entregáveis do projeto
- documentação técnica clara para banca e apresentação

## 2. Requisitos de Software

### Requisitos Funcionais

- **RF01 - Autenticação e autorização**
  - O sistema deve permitir login de usuários por e-mail e senha.
  - Após autenticação, o acesso deve ser controlado pelo perfil (Professor, Estudante, Coordenador, Administrador).

- **RF02 - Gestão de turmas**
  - Professores devem poder criar turmas com nome, código e período.
  - Estudantes devem entrar em turmas usando código de acesso.
  - Estudantes visualizam apenas turmas em que estão matriculados.

- **RF03 - Publicação de atividades**
  - Professores vinculados a uma turma devem publicar atividades contendo título, descrição, data de prazo e anexos opcionais.
  - Apenas professores autorizados conseguem publicar atividades para suas turmas.

- **RF04 - Edição de atividades**
  - Professores podem editar atividades publicadas para corrigir informações ou atualizar prazos.
  - Atualizações são refletidas imediatamente para os estudantes.

- **RF05 - Submissão de entregas**
  - Estudantes podem enviar arquivos como resposta a uma atividade.
  - O sistema deve registrar data/hora da entrega e sinalizar atrasos quando o prazo já passou.
  - Arquivos devem respeitar o limite de tamanho definido.

- **RF06 - Visualização de entregas**
  - Professores visualizam lista de entregas da turma ordenadas por status e data.
  - Entregas atrasadas devem ser destacadas claramente.

- **RF07 - Avaliação e feedback**
  - Professores podem atribuir nota de 0 a 10 e adicionar comentários às entregas.
  - Estudantes recebem notificação quando a avaliação é liberada.

- **RF08 - Consulta de notas**
  - Estudantes consultam suas notas e feedbacks de atividades avaliadas.
  - O histórico de notas fica disponível no sistema.

- **RF09 - Reabertura de atividade (futuro)**
  - Professores podem reabrir atividades encerradas para permitir novas entregas em situações excepcionais.

- **RF10 - Dashboard de coordenador (futuro)**
  - Coordenadores visualizam indicadores de turmas e desempenho institucional em um painel consolidado.

### Requisitos Não Funcionais

- **RNF01 - Desempenho**
  - A API deve responder em até 500 ms para 95% das requisições.
  - O sistema deve suportar ao menos 500 usuários simultâneos na fase inicial.

- **RNF02 - Segurança**
  - Senhas devem ser armazenadas com hash bcrypt.
  - A comunicação deve ocorrer via HTTPS.
  - Autenticação deve usar tokens JWT com expiração configurável.

- **RNF03 - Usabilidade**
  - Interface deve ser responsiva e compatível com desktop e mobile.
  - Mensagens de erro devem ser claras e orientarem o usuário.

- **RNF04 - Disponibilidade**
  - O sistema deve ter disponibilidade objetivo de 99% em horário de operação.

- **RNF05 - Auditoria**
  - O sistema deve registrar log de criação, atualização e exclusão de entidades críticas (atividades, entregas, notas).

## 3. Regras de Negócio

### RN01 – Apenas professores podem criar atividades

- Descrição: Somente usuários com perfil `Professor` vinculados à turma podem criar, editar e excluir atividades.
- Justificativa: Garante controle pedagógico e evita publicação indevida de tarefas.
- Impacto: exige autenticação, autorização RBAC, validação de perfil e regras no fluxo de BPMN.

### RN02 – Entregas após prazo devem ser sinalizadas

- Descrição: O sistema compara data/hora de entrega com o prazo definido e marca entregas atrasadas.
- Justificativa: Oferece transparência ao professor e estudante sobre cumprimento de prazos.
- Impacto: adiciona lógica de validação de prazo no backend e no fluxo de submissão de entregas.

### RN03 – Estudante só pode acessar turmas nas quais está matriculado

- Descrição: O acesso a conteúdos e atividades de uma turma é restrito aos estudantes matriculados nela.
- Justificativa: Preserva privacidade e organiza o conteúdo de forma adequada.
- Impacto: exige verificação de matrícula em todas as requisições de turmas e atividades.

### RN04 – Limite de tamanho para arquivos enviados

- Descrição: Uploads de arquivos devem respeitar limite máximo de 50 MB por arquivo.
- Justificativa: Evita sobrecarga de armazenamento e problemas de transferência.
- Impacto: exige validação no front-end, backend e possível configuração do servidor web.

### RN05 – Professor pode reabrir atividade encerrada

- Descrição: Professores podem reabrir atividades cujo prazo expirou para permitir novas entregas.
- Justificativa: Oferece flexibilidade pedagógica em situações excepcionais.
- Impacto: adiciona histórico de status e controle de mudança de estado de atividades.

### RN06 – Notas devem estar entre 0 e 10

- Descrição: Todas as notas atribuídas devem obedecer ao intervalo [0, 10] com até duas casas decimais.
- Justificativa: Padroniza avaliações conforme práticas acadêmicas.
- Impacto: exige validação de dados e constraints no banco.

### RN07 – Coordenador pode visualizar todas as turmas

- Descrição: Coordenadores têm permissão de leitura para consultar todas as turmas, independentemente do professor responsável.
- Justificativa: Permite supervisão pedagógica sem alterar dados acadêmicos.
- Impacto: define um perfil de acesso especial com permissão de consulta global.

### RN08 – Turma deve ter pelo menos um professor responsável

- Descrição: Toda turma criada precisa ter um professor designado como responsável.
- Justificativa: Garante responsabilidade pedagógica e clareza de gestão.
- Impacto: exige constraint de integridade e validação de criação de turmas.

## 4. Rastreabilidade entre artefatos

- **RN01** → US03, workflow de publicação de atividade, arquitetura de autorização.
- **RN02** → US04, US05, processo de entrega e correção, status de entrega no modelo de dados.
- **RN03** → US01, US02, controle de acesso a turmas, visualização filtrada por matrícula.
- **RN04** → US03, US04, política de upload de arquivos, UI de validação de tamanho.
- **RN05** → US08, estado de atividade reaberta, histórico de alterações.
- **RN06** → US06, US07, validação de notas e relatórios de desempenho.
- **RN07** → US09, dashboard de coordenador, permissões de leitura global.
- **RN08** → RF02, US10, UC12, criação de turmas, integridade de dados.
