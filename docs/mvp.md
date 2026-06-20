# MVP - Minimum Viable Product

## 1. Funcionalidades Essenciais (MVP)

### Gestão de Usuários
- **US01:** Visualizar turmas matriculadas
  - Estudante acessa lista de suas turmas ativas
  - Visualização de informações básicas (nome, professor, código)
- **US02:** Entrar em turma via código
  - Matrícula simplificada usando código de acesso
  - Validação e confirmação imediata

**Justificativa:** Base fundamental para que estudantes e professores possam interagir no sistema. Sem gestão de turmas, não há contexto para as demais funcionalidades.

---

### Gestão de Atividades
- **US03:** Criar atividade
  - Professor cria atividades com título, descrição, anexos e prazo
  - Publicação imediata para estudantes da turma
- **US04:** Editar atividade
  - Professor atualiza informações de atividades publicadas
  - Notificação automática aos estudantes

**Justificativa:** Core do sistema - permite ao professor distribuir tarefas e exercícios. É o principal mecanismo de interação professor-estudante.

---

### Gestão de Entregas
- **US05:** Submeter entrega de atividade
  - Estudante faz upload de arquivo com validação de tamanho
  - Registro automático de data/hora e status (no prazo/atrasado)
- **US06:** Visualizar entregas da turma
  - Professor acessa todas as entregas organizadas
  - Filtros por status e download em lote

**Justificativa:** Fecha o ciclo básico de publicação-entrega. Sem isso, o sistema não cumpre seu propósito principal de gerenciar atividades acadêmicas.

---

### Avaliação
- **US07:** Atribuir nota e feedback
  - Professor avalia entregas com nota (0-10) e comentários
  - Notificação automática ao estudante
- **US08:** Acompanhar notas
  - Estudante visualiza suas notas e feedbacks
  - Histórico completo de avaliações

**Justificativa:** Essencial para fechar o ciclo pedagógico. O processo de avaliação e transparência de notas é requisito básico de qualquer plataforma educacional.

---

## 2. Funcionalidades Futuras (Versão 2.0+)

### Flexibilidade Pedagógica
- **US09:** Reabrir atividade encerrada
  - Professor pode reabrir atividades com prazo expirado
  - Registro de histórico de reabertura

**Justificativa para postergar:** Embora útil, não é crítico para o funcionamento básico. Professores podem inicialmente criar novas atividades para casos excepcionais. Adiciona complexidade de gerenciamento de estados.

---

### Gestão Institucional
- **US10:** Dashboard institucional para coordenador
  - Visão consolidada de métricas institucionais
  - Relatórios e gráficos de desempenho
  - Exportação de dados

**Justificativa para postergar:** Funcionalidade voltada para gestão e análise, não para o dia a dia de professores e estudantes. Requer coleta de dados históricos para ser realmente útil. Pode ser desenvolvida após validação do MVP com usuários principais.

---

### Comunicação Avançada (Futuro)
- Chat em tempo real entre professores e estudantes
- Sistema de mensagens privadas
- Fórum de discussão por turma
- Videoconferências integradas

**Justificativa para postergar:** Comunicação básica pode ser feita via notificações e feedback em atividades. Funcionalidades de comunicação síncrona exigem infraestrutura mais robusta e podem ser substituídas temporariamente por ferramentas externas.

---

### Recursos Avançados (Futuro)
- Sistema de pontos e gamificação
- Badges e conquistas
- Provas online com correção automática
- Banco de questões
- Integração com outros sistemas (SIGAA, Moodle)

**Justificativa para postergar:** Funcionalidades "nice-to-have" que agregam valor mas não são necessárias para validar a proposta central do sistema. Devem ser desenvolvidas após feedback dos usuários do MVP.

---

## 3. Critérios de Priorização

### Usados para definir o MVP:

1. **Valor para o usuário**
   - Resolve o problema principal identificado na Visão do Produto?
   - É essencial para o fluxo básico professor-estudante?

2. **Viabilidade técnica**
   - Pode ser implementado rapidamente?
   - Depende de integrações complexas?

3. **Dependências**
   - É funcionalidade base para outras features?
   - Outras funcionalidades dependem desta?

4. **Complexidade**
   - Quanto esforço de desenvolvimento requer?
   - Complexidade de manutenção?

5. **Risco**
   - Qual o impacto de NÃO ter na primeira versão?
   - Pode ser substituído temporariamente?

---

## 4. Matriz de Priorização

| User Story | Valor | Viabilidade | Dependências | Complexidade | Prioridade | Versão |
|------------|-------|-------------|--------------|--------------|------------|--------|
| US01       | Alto  | Alta        | Base         | Baixa        | CRÍTICA    | MVP    |
| US02       | Alto  | Alta        | Base         | Baixa        | CRÍTICA    | MVP    |
| US03       | Alto  | Alta        | Depende US01 | Média        | CRÍTICA    | MVP    |
| US04       | Médio | Alta        | Depende US03 | Baixa        | ALTA       | MVP    |
| US05       | Alto  | Alta        | Depende US03 | Média        | CRÍTICA    | MVP    |
| US06       | Alto  | Alta        | Depende US05 | Média        | CRÍTICA    | MVP    |
| US07       | Alto  | Alta        | Depende US06 | Média        | CRÍTICA    | MVP    |
| US08       | Alto  | Alta        | Depende US07 | Baixa        | ALTA       | MVP    |
| US09       | Baixo | Média       | Depende US03 | Média        | BAIXA      | v2.0   |
| US10       | Médio | Baixa       | Requer dados | Alta         | BAIXA      | v2.0   |

---

## 5. Escopo do MVP

### O que DEVE ter:
✅ Cadastro e autenticação de usuários (Professor, Estudante, Coordenador)  
✅ Criação e gerenciamento de turmas  
✅ Matrícula de estudantes via código  
✅ Publicação de atividades com prazo  
✅ Upload de arquivos (materiais e entregas)  
✅ Submissão de entregas com validação de prazo  
✅ Atribuição de notas e feedback  
✅ Visualização de notas pelos estudantes  
✅ Notificações básicas (e-mail)  
✅ Sistema de controle de acesso (RBAC)

### O que NÃO terá no MVP:
❌ Reabertura de atividades  
❌ Dashboard institucional completo  
❌ Chat em tempo real  
❌ Videoconferência  
❌ Gamificação  
❌ Provas online com correção automática  
❌ Integrações externas  
❌ Aplicativo mobile nativo  
❌ Relatórios avançados com BI

---

## 6. Validação do MVP

### Métricas de Sucesso:
- Pelo menos 80% dos professores conseguem criar e publicar atividade em < 5 minutos
- Pelo menos 90% dos estudantes conseguem submeter entrega sem dificuldade
- Taxa de adoção: 70% das turmas piloto utilizam o sistema regularmente
- Redução de 50% no tempo gasto por professores com organização de entregas
- NPS (Net Promoter Score) > 7 entre usuários piloto

### Público Piloto:
- 5-10 turmas
- 2-5 professores
- 50-200 estudantes
- Período de validação: 1 semestre letivo

### Ciclo de Feedback:
1. Lançamento do MVP para turmas piloto
2. Coleta de feedback semanal (formulários e entrevistas)
3. Ajustes e correções rápidas
4. Validação das hipóteses de valor
5. Decisão sobre desenvolvimento de funcionalidades futuras baseada em dados reais de uso
