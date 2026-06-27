# User Stories

## US01 - Visualizar Turmas Matriculadas

**Como** estudante,  
**Desejo** visualizar apenas as turmas nas quais estou matriculado,  
**Para** ter uma visao organizada do meu conteudo academico.

### Criterios de Aceitacao
- [ ] O estudante acessa uma lista com todas as suas turmas ativas.
- [ ] Cada turma exibe nome, professor responsavel e codigo.
- [ ] Turmas sao ordenadas por nome ou periodo.
- [ ] Nao sao exibidas turmas de outros estudantes.
- [ ] Interface responsiva funciona em desktop e mobile.

### Regras de Negocio Relacionadas
- RN03: Estudante so pode acessar turmas nas quais esta matriculado.

### Casos de Uso Relacionados
- UC06: Visualizar Turmas.
- UC07: Acessar Conteudo da Turma.

### Prioridade
- [x] MVP essencial.

---

## US02 - Entrar em Turma via Codigo

**Como** estudante,  
**Desejo** entrar em uma turma usando um codigo de acesso,  
**Para** me matricular nas disciplinas do periodo.

### Criterios de Aceitacao
- [ ] O estudante insere um codigo alfanumerico de 6 a 8 caracteres.
- [ ] O sistema valida se o codigo existe e esta ativo.
- [ ] O sistema confirma que a turma possui professor responsavel.
- [ ] Matricula e confirmada com mensagem de sucesso.
- [ ] Turma aparece imediatamente na lista do estudante.
- [ ] Codigos invalidos exibem mensagem de erro clara.

### Regras de Negocio Relacionadas
- RN03: Estudante so pode acessar turmas nas quais esta matriculado.
- RN08: Turma deve ter pelo menos um professor responsavel.

### Casos de Uso Relacionados
- UC06: Visualizar Turmas.
- UC07: Acessar Conteudo da Turma.

### Prioridade
- [x] MVP essencial.

---

## US03 - Gerenciar Atividades

**Como** professor,  
**Desejo** criar e editar atividades com titulo, descricao, anexos e prazo,  
**Para** disponibilizar e manter tarefas atualizadas para estudantes da minha turma.

### Criterios de Aceitacao
- [ ] Professor acessa formulario de criacao de atividade.
- [ ] Campos obrigatorios: titulo, descricao e prazo.
- [ ] Campos opcionais: anexos ate 50MB e pontuacao maxima.
- [ ] Prazo nao pode ser no passado.
- [ ] Professor pode editar titulo, descricao, prazo e anexos.
- [ ] Alteracoes sao registradas em historico.
- [ ] Estudantes matriculados recebem notificacao de criacao ou atualizacao.

### Regras de Negocio Relacionadas
- RN01: Apenas professores podem criar atividades.
- RN04: Limite de tamanho para arquivos enviados.

### Casos de Uso Relacionados
- UC01: Criar Atividade.
- UC02: Editar Atividade.
- UC03: Excluir Atividade.
- UC08: Upload de Arquivo.

### Prioridade
- [x] MVP essencial.

---

## US04 - Submeter Entrega de Atividade

**Como** estudante,  
**Desejo** fazer upload do arquivo da minha atividade,  
**Para** entregar o trabalho ao professor.

### Criterios de Aceitacao
- [ ] Estudante seleciona arquivo de ate 50MB.
- [ ] Sistema valida formato e tamanho do arquivo.
- [ ] Confirmacao de upload bem-sucedido e exibida.
- [ ] Estudante pode visualizar arquivo enviado.
- [ ] Sistema registra data/hora da entrega.
- [ ] Entregas apos prazo sao sinalizadas como atrasadas.

### Regras de Negocio Relacionadas
- RN02: Entregas apos prazo devem ser sinalizadas.
- RN04: Limite de tamanho para arquivos enviados.

### Casos de Uso Relacionados
- UC04: Submeter Entrega.
- UC08: Upload de Arquivo.

### Prioridade
- [x] MVP essencial.

---

## US05 - Visualizar Entregas da Turma

**Como** professor,  
**Desejo** visualizar todas as entregas de uma atividade,  
**Para** organizar o processo de correcao.

### Criterios de Aceitacao
- [ ] Professor acessa lista de entregas por atividade.
- [ ] Cada entrega exibe nome do estudante, data/hora e status.
- [ ] Entregas atrasadas sao sinalizadas visualmente.
- [ ] Professor pode filtrar por no prazo, atrasadas e nao entregues.
- [ ] Professor pode baixar arquivos individualmente ou em lote.

### Regras de Negocio Relacionadas
- RN02: Entregas apos prazo devem ser sinalizadas.

### Casos de Uso Relacionados
- UC05: Visualizar Entregas.

### Prioridade
- [x] MVP essencial.

---

## US06 - Atribuir Nota e Feedback

**Como** professor,  
**Desejo** atribuir nota e comentarios a uma entrega,  
**Para** avaliar o desempenho do estudante.

### Criterios de Aceitacao
- [ ] Professor insere nota de 0 a 10 com ate 2 casas decimais.
- [ ] Campo de comentarios aceita ate 500 caracteres.
- [ ] Sistema valida intervalo da nota.
- [ ] Estudante recebe notificacao quando avaliado.
- [ ] Nota e feedback ficam visiveis para o estudante.

### Regras de Negocio Relacionadas
- RN06: Notas devem estar entre 0 e 10.

### Casos de Uso Relacionados
- UC10: Atribuir Nota.

### Prioridade
- [x] MVP essencial.

---

## US07 - Acompanhar Notas

**Como** estudante,  
**Desejo** visualizar minhas notas e feedbacks,  
**Para** acompanhar meu desempenho academico.

### Criterios de Aceitacao
- [ ] Estudante acessa lista de atividades avaliadas.
- [ ] Cada atividade exibe titulo, nota e data de avaliacao.
- [ ] Feedback do professor e exibido por completo.
- [ ] Estudante pode visualizar historico de todas as notas.
- [ ] Sistema calcula e exibe media da turma quando configurado.

### Regras de Negocio Relacionadas
- RN06: Notas devem estar entre 0 e 10.

### Casos de Uso Relacionados
- UC10: Atribuir Nota.

### Prioridade
- [x] MVP essencial.

---

## US08 - Reabrir Atividade Encerrada

**Como** professor,  
**Desejo** reabrir uma atividade cujo prazo expirou,  
**Para** permitir entregas de estudantes em situacoes excepcionais.

### Criterios de Aceitacao
- [ ] Professor acessa opcao "Reabrir atividade" em atividades encerradas.
- [ ] Sistema solicita confirmacao da acao.
- [ ] Atividade volta ao status "reaberta".
- [ ] Estudantes recebem notificacao da reabertura.
- [ ] Historico registra quem e quando reabriu.

### Regras de Negocio Relacionadas
- RN05: Professor pode reabrir atividade encerrada.

### Casos de Uso Relacionados
- UC09: Reabrir Atividade.

### Prioridade
- [ ] Futuro, versao 2.0.

---

## US09 - Dashboard Institucional para Coordenador

**Como** coordenador,  
**Desejo** visualizar dashboard com metricas de todas as turmas,  
**Para** acompanhar o desempenho institucional.

### Criterios de Aceitacao
- [ ] Coordenador acessa dashboard com visao geral.
- [ ] Metricas exibidas: total de turmas, estudantes e atividades.
- [ ] Graficos de desempenho por turma ou disciplina.
- [ ] Filtros por periodo, professor e disciplina.
- [ ] Opcao de exportar relatorios em PDF ou Excel.

### Regras de Negocio Relacionadas
- RN07: Coordenador pode visualizar todas as turmas.

### Casos de Uso Relacionados
- UC11: Visualizar Dashboard Institucional.

### Prioridade
- [ ] Futuro, versao 2.0.

---

## US10 - Criar Turma com Professor Responsavel

**Como** administrador,  
**Desejo** criar turmas informando obrigatoriamente ao menos um professor responsavel,  
**Para** garantir que toda turma tenha responsabilidade pedagogica definida desde sua criacao.

### Criterios de Aceitacao
- [ ] Administrador acessa formulario de criacao de turma.
- [ ] Campos obrigatorios: nome da turma, periodo, codigo e professor responsavel.
- [ ] Sistema impede salvar turma sem professor responsavel.
- [ ] Sistema valida se o professor informado possui perfil Professor ativo.
- [ ] Turma criada fica imediatamente disponivel para matriculas por codigo.
- [ ] Evento de criacao registra usuario, data/hora e professor vinculado.

### Regras de Negocio Relacionadas
- RN08: Turma deve ter pelo menos um professor responsavel.

### Casos de Uso Relacionados
- UC12: Criar Turma.

### Prioridade
- [x] MVP essencial.
