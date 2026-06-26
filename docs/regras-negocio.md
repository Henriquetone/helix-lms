# Regras de Negócio

## RN01 – Apenas professores podem criar atividades

**Descrição:** Somente usuários com perfil de Professor têm permissão para criar, editar e excluir atividades em suas turmas. Estudantes e outros perfis não possuem essa funcionalidade.

**Justificativa:** Manter o controle pedagógico e garantir que apenas conteúdo validado seja publicado aos estudantes.

### Impactos

#### User Stories
- **US03:** Como professor, desejo criar atividades com título, descrição, anexos e prazo, para disponibilizar tarefas aos estudantes da minha turma.
- **US04:** Como professor, desejo editar atividades já publicadas, para corrigir informações ou atualizar requisitos.

#### Processos (BPMN)
- No processo "Publicação de Atividade", a ação de criação é executada exclusivamente pelo ator Professor
- Gateway de validação verifica o perfil do usuário antes de permitir acesso ao formulário de criação

#### Casos de Uso
- **UC01:** Criar Atividade (Ator: Professor)
- **UC02:** Editar Atividade (Ator: Professor)
- **UC03:** Excluir Atividade (Ator: Professor)

#### Arquitetura
- Necessidade de sistema de autenticação robusto
- Implementação de RBAC (Role-Based Access Control) para controlar permissões
- Middleware de autorização nas rotas de criação/edição de atividades
- Camada de serviço valida perfil antes de executar operações

#### Requisitos Não Funcionais
- **Segurança:** Controle de acesso baseado em perfis
- **Auditoria:** Registro de todas as operações de criação/edição

---

## RN02 – Entregas após prazo devem ser sinalizadas

**Descrição:** O sistema deve automaticamente identificar e marcar entregas realizadas após a data/hora limite estabelecida pelo professor. Entregas atrasadas são aceitas, mas claramente sinalizadas.

**Justificativa:** Permitir flexibilidade ao professor na aceitação de entregas atrasadas, mantendo transparência sobre o cumprimento de prazos.

### Impactos

#### User Stories
- **US07:** Como estudante, desejo visualizar se minha entrega foi realizada no prazo ou com atraso, para ter transparência sobre minha situação.
- **US08:** Como professor, desejo visualizar quais entregas foram feitas após o prazo, para considerar isso na avaliação.

#### Processos (BPMN)
- No processo "Entrega de Atividade", gateway de decisão verifica se a data/hora atual é posterior ao prazo
- Fluxo alternativo para entregas atrasadas inclui marcação automática

#### Casos de Uso
- **UC04:** Submeter Entrega (inclui validação de prazo)
- **UC05:** Visualizar Entregas (filtragem por status de prazo)

#### Arquitetura
- Serviço de validação de prazos com comparação de timestamps
- Campo adicional no modelo de dados: `entregue_atraso` (boolean)
- Notificação assíncrona para estudante sobre status da entrega

#### Requisitos Não Funcionais
- **Confiabilidade:** Sincronização de horário via NTP
- **Usabilidade:** Indicação visual clara de entregas atrasadas

---

## RN03 – Estudante só pode acessar turmas nas quais está matriculado

**Descrição:** O acesso a materiais, atividades e informações de uma turma é restrito aos estudantes matriculados nela. Estudantes não podem visualizar conteúdo de turmas em que não estão inscritos.

**Justificativa:** Garantir privacidade e organização, evitando acesso indevido a conteúdo de outras turmas.

### Impactos

#### User Stories
- **US01:** Como estudante, desejo visualizar apenas as turmas nas quais estou matriculado, para ter uma visão organizada do meu conteúdo.
- **US02:** Como professor, desejo que apenas estudantes matriculados acessem minha turma, para garantir privacidade do conteúdo.

#### Casos de Uso
- **UC06:** Visualizar Turmas (filtrado por matrícula)
- **UC07:** Acessar Conteúdo da Turma (validação de matrícula)

#### Arquitetura
- Relacionamento muitos-para-muitos entre Estudantes e Turmas (tabela de matrícula)
- Middleware de autorização valida matrícula antes de servir conteúdo
- Cache de permissões por sessão para otimizar validações

#### Requisitos Não Funcionais
- **Segurança:** Validação de matrícula em todas as requisições de conteúdo
- **Performance:** Cache de relações estudante-turma

---

## RN04 – Limite de tamanho para arquivos enviados

**Descrição:** Arquivos enviados por estudantes (entregas) e professores (materiais) devem respeitar um limite máximo de 50MB por arquivo. Uploads acima desse limite são rejeitados.

**Justificativa:** Garantir viabilidade técnica de armazenamento e transferência de arquivos, evitando sobrecarga do sistema.

### Impactos

#### User Stories
- **US09:** Como estudante, desejo receber feedback claro se meu arquivo excede o limite, para ajustá-lo antes de enviar.
- **US10:** Como professor, desejo fazer upload de materiais dentro do limite estabelecido, para disponibilizá-los aos estudantes.

#### Casos de Uso
- **UC08:** Upload de Arquivo (validação de tamanho)

#### Arquitetura
- Validação client-side (JavaScript) antes do upload
- Validação server-side no controller antes de processar
- Configuração de limite no servidor web (nginx/apache)
- Armazenamento em serviço de object storage (S3, MinIO)

#### Requisitos Não Funcionais
- **Usabilidade:** Mensagem clara sobre o limite e tamanho atual do arquivo
- **Performance:** Rejeição rápida de arquivos grandes sem processamento completo

---

## RN05 – Professor pode reabrir atividade encerrada

**Descrição:** Professores têm autonomia para reabrir atividades cujo prazo já expirou, permitindo novas entregas ou entregas tardias de estudantes.

**Justificativa:** Oferecer flexibilidade pedagógica ao professor para lidar com situações excepcionais.

### Impactos

#### User Stories
- **US11:** Como professor, desejo reabrir uma atividade encerrada, para permitir entregas de estudantes em situações excepcionais.

#### Casos de Uso
- **UC09:** Reabrir Atividade (Ator: Professor)

#### Arquitetura
- Campo de status da atividade: `aberta`, `encerrada`, `reaberta`
- Histórico de mudanças de status com timestamp e responsável
- Notificação aos estudantes quando atividade é reaberta

#### Requisitos Não Funcionais
- **Auditoria:** Registro de todas as reabertura de atividades
- **Rastreabilidade:** Histórico completo de mudanças de status

---

## RN06 – Notas devem estar entre 0 e 10

**Descrição:** Todas as notas atribuídas pelo professor devem estar no intervalo de 0 a 10, com precisão de até 2 casas decimais (ex: 7.25, 9.50).

**Justificativa:** Padronizar o sistema de avaliação conforme práticas educacionais brasileiras.

### Impactos

#### User Stories
- **US12:** Como professor, desejo atribuir notas de 0 a 10 com decimais, para avaliar precisamente o desempenho dos estudantes.

#### Casos de Uso
- **UC10:** Atribuir Nota (validação de intervalo)

#### Arquitetura
- Validação de input no frontend (range 0-10)
- Validação de domínio no backend (regra de negócio)
- Tipo de dado: DECIMAL(4,2) no banco de dados

#### Requisitos Não Funcionais
- **Integridade:** Garantir que notas fora do intervalo sejam rejeitadas
- **Usabilidade:** Mensagem clara sobre o formato aceito

---

## RN07 – Coordenador pode visualizar todas as turmas

**Descrição:** Usuários com perfil de Coordenador possuem permissão de leitura sobre todas as turmas da instituição, independentemente do professor responsável.

**Justificativa:** Permitir supervisão pedagógica e geração de relatórios institucionais.

### Impactos

#### User Stories
- **US13:** Como coordenador, desejo visualizar todas as turmas da instituição, para acompanhar o andamento pedagógico.

#### Casos de Uso
- **UC11:** Visualizar Dashboard Institucional (Ator: Coordenador)

#### Arquitetura
- RBAC com permissão especial para coordenadores: `read:all_turmas`
- Query sem filtro de relacionamento para perfil coordenador
- Endpoint específico para visão institucional

#### Requisitos Não Funcionais
- **Performance:** Paginação e cache para listagens grandes
- **Segurança:** Coordenador tem apenas leitura, não pode modificar turmas de outros professores

---

## RN08 – Turma deve ter pelo menos um professor responsável

**Descrição:** Toda turma criada no sistema deve obrigatoriamente ter ao menos um professor designado como responsável. Não é permitida a existência de turmas sem professor.

**Justificativa:** Garantir responsabilidade pedagógica e gestão adequada de cada turma.

### Impactos

#### User Stories
- **US14:** Como administrador, ao criar uma turma, devo obrigatoriamente designar um professor responsável.

#### Casos de Uso
- **UC12:** Criar Turma (validação de professor obrigatório)

#### Arquitetura
- Relacionamento obrigatório entre Turma e Professor no modelo de dados
- Validação de integridade referencial no banco (NOT NULL)
- Validação no formulário de criação de turma

#### Requisitos Não Funcionais
- **Integridade:** Constraint de banco de dados impede turma sem professor
- **Usabilidade:** Campo professor marcado como obrigatório no formulário
