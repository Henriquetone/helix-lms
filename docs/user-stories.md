# User Stories

## US01 – Visualizar Turmas Matriculadas

**Como** estudante,  
**Desejo** visualizar apenas as turmas nas quais estou matriculado,  
**Para** ter uma visão organizada do meu conteúdo acadêmico.

### Critérios de Aceitação
- [ ] O estudante acessa uma lista com todas as suas turmas ativas
- [ ] Cada turma exibe: nome, professor responsável e código
- [ ] Turmas são ordenadas por nome ou período
- [ ] Não são exibidas turmas de outros estudantes
- [ ] Interface responsiva funciona em desktop e mobile

### Regras de Negócio Relacionadas
- RN03: Estudante só pode acessar turmas nas quais está matriculado

### Prioridade
- [x] MVP (essencial)

---

## US02 – Entrar em Turma via Código

**Como** estudante,  
**Desejo** entrar em uma turma usando um código de acesso,  
**Para** me matricular nas disciplinas do período.

### Critérios de Aceitação
- [ ] O estudante insere um código alfanumérico de 6-8 caracteres
- [ ] O sistema valida se o código existe e está ativo
- [ ] Matrícula é confirmada com mensagem de sucesso
- [ ] Turma aparece imediatamente na lista do estudante
- [ ] Códigos inválidos exibem mensagem de erro clara

### Regras de Negócio Relacionadas
- RN03: Estudante só pode acessar turmas nas quais está matriculado

### Prioridade
- [x] MVP (essencial)

---

## US03 – Criar Atividade

**Como** professor,  
**Desejo** criar atividades com título, descrição, anexos e prazo,  
**Para** disponibilizar tarefas aos estudantes da minha turma.

### Critérios de Aceitação
- [ ] Professor acessa formulário de criação de atividade
- [ ] Campos obrigatórios: título, descrição e prazo
- [ ] Campos opcionais: anexos (até 50MB), pontuação máxima
- [ ] Prazo não pode ser no passado
- [ ] Atividade criada aparece imediatamente na turma
- [ ] Estudantes matriculados recebem notificação

### Regras de Negócio Relacionadas
- RN01: Apenas professores podem criar atividades
- RN04: Limite de tamanho para arquivos enviados

### Prioridade
- [x] MVP (essencial)

---

## US04 – Editar Atividade

**Como** professor,  
**Desejo** editar atividades já publicadas,  
**Para** corrigir informações ou atualizar requisitos.

### Critérios de Aceitação
- [ ] Professor pode editar título, descrição, prazo e anexos
- [ ] Alterações são salvas e refletidas imediatamente
- [ ] Estudantes recebem notificação sobre atualização
- [ ] Histórico de alterações é registrado
- [ ] Não é possível editar atividade com entregas já avaliadas sem confirmação

### Regras de Negócio Relacionadas
- RN01: Apenas professores podem criar atividades

### Prioridade
- [x] MVP (essencial)

---

## US05 – Submeter Entrega de Atividade

**Como** estudante,  
**Desejo** fazer upload do arquivo da minha atividade,  
**Para** entregar o trabalho ao professor.

### Critérios de Aceitação
- [ ] Estudante seleciona arquivo de até 50MB
- [ ] Sistema valida formato e tamanho do arquivo
- [ ] Confirmação de upload bem-sucedido é exibida
- [ ] Estudante pode visualizar arquivo enviado
- [ ] Sistema registra data/hora da entrega
- [ ] Entregas após prazo são sinalizadas como atrasadas

### Regras de Negócio Relacionadas
- RN02: Entregas após prazo devem ser sinalizadas
- RN04: Limite de tamanho para arquivos enviados

### Prioridade
- [x] MVP (essencial)

---

## US06 – Visualizar Entregas da Turma

**Como** professor,  
**Desejo** visualizar todas as entregas de uma atividade,  
**Para** organizar o processo de correção.

### Critérios de Aceitação
- [ ] Professor acessa lista de entregas por atividade
- [ ] Cada entrega exibe: nome do estudante, data/hora, status
- [ ] Entregas atrasadas são sinalizadas visualmente
- [ ] Professor pode filtrar por: no prazo, atrasadas, não entregues
- [ ] Professor pode baixar arquivos individualmente ou em lote

### Regras de Negócio Relacionadas
- RN02: Entregas após prazo devem ser sinalizadas

### Prioridade
- [x] MVP (essencial)

---

## US07 – Atribuir Nota e Feedback

**Como** professor,  
**Desejo** atribuir nota e comentários a uma entrega,  
**Para** avaliar o desempenho do estudante.

### Critérios de Aceitação
- [ ] Professor insere nota de 0 a 10 com até 2 casas decimais
- [ ] Campo de comentários aceita até 500 caracteres
- [ ] Sistema valida intervalo da nota (0-10)
- [ ] Estudante recebe notificação quando avaliado
- [ ] Nota e feedback ficam visíveis para o estudante

### Regras de Negócio Relacionadas
- RN06: Notas devem estar entre 0 e 10

### Prioridade
- [x] MVP (essencial)

---

## US08 – Acompanhar Notas

**Como** estudante,  
**Desejo** visualizar minhas notas e feedbacks,  
**Para** acompanhar meu desempenho acadêmico.

### Critérios de Aceitação
- [ ] Estudante acessa lista de atividades avaliadas
- [ ] Cada atividade exibe: título, nota, data de avaliação
- [ ] Feedback do professor é exibido por completo
- [ ] Estudante pode visualizar histórico de todas as notas
- [ ] Sistema calcula e exibe média da turma (opcional)

### Regras de Negócio Relacionadas
- RN06: Notas devem estar entre 0 e 10

### Prioridade
- [x] MVP (essencial)

---

## US09 – Reabrir Atividade Encerrada

**Como** professor,  
**Desejo** reabrir uma atividade cujo prazo expirou,  
**Para** permitir entregas de estudantes em situações excepcionais.

### Critérios de Aceitação
- [ ] Professor acessa opção "Reabrir atividade" em atividades encerradas
- [ ] Sistema solicita confirmação da ação
- [ ] Atividade volta ao status "aberta"
- [ ] Estudantes recebem notificação da reabertura
- [ ] Histórico registra quem e quando reabriu

### Regras de Negócio Relacionadas
- RN05: Professor pode reabrir atividade encerrada

### Prioridade
- [ ] Futuro (versão 2.0)

---

## US10 – Dashboard Institucional para Coordenador

**Como** coordenador,  
**Desejo** visualizar dashboard com métricas de todas as turmas,  
**Para** acompanhar o desempenho institucional.

### Critérios de Aceitação
- [ ] Coordenador acessa dashboard com visão geral
- [ ] Métricas exibidas: total de turmas, estudantes, atividades
- [ ] Gráficos de desempenho por turma/disciplina
- [ ] Filtros por período, professor, disciplina
- [ ] Opção de exportar relatórios em PDF/Excel

### Regras de Negócio Relacionadas
- RN07: Coordenador pode visualizar todas as turmas

### Prioridade
- [ ] Futuro (versão 2.0)
