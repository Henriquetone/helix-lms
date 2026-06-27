# Decisoes Arquiteturais

## DA01 - Arquitetura hibrida

**Decisao:** Combinar arquitetura em camadas para o fluxo principal com eventos para notificacoes e analises pedagogicas.

**Motivacao:** O MVP precisa ser simples, mas algumas operacoes nao devem bloquear a API, como envio de e-mails e calculo de indicadores.

**Alternativas consideradas:**
- Camadas puras: mais simples, mas acopla notificacoes e analises ao fluxo principal.
- Microservicos: mais escalavel, mas excessivo para o escopo academico e para o MVP.

**Trade-off:** A fila aumenta a complexidade operacional, mas reduz acoplamento e melhora a capacidade de evolucao.

---

## DA02 - Autenticacao JWT

**Decisao:** Usar JWT para autenticar requisicoes entre Web App e API Server.

**Motivacao:** Permite autenticacao stateless, integracao simples com frontend web e evolucao futura para aplicativo mobile.

**Alternativas consideradas:**
- Sessao server-side: mais simples em aplicacoes pequenas, mas menos flexivel para multiplos clientes.
- OAuth externo: robusto, mas desnecessario para a proposta inicial.

**Trade-off:** JWT exige cuidado com expiracao, renovacao e armazenamento seguro no cliente.

---

## DA03 - Autorizacao centralizada com RBAC

**Decisao:** Centralizar regras de permissao no backend usando controle de acesso baseado em papeis.

**Motivacao:** As regras RN01, RN03 e RN07 dependem diretamente de perfis e vinculos: professor, estudante, coordenador e administrador.

**Alternativas consideradas:**
- Autorizacao apenas no frontend: melhora experiencia, mas nao garante seguranca.
- Permissoes totalmente customizadas por usuario: flexivel, mas complexa para o MVP.

**Trade-off:** RBAC e menos granular que politicas customizadas, mas e adequado para os papeis definidos no dominio.

---

## DA04 - Banco de dados relacional

**Decisao:** Usar banco relacional para os dados estruturados do sistema.

**Motivacao:** O dominio possui relacoes fortes entre usuarios, turmas, matriculas, atividades, entregas e avaliacoes.

**Alternativas consideradas:**
- Banco NoSQL: flexivel, mas menos adequado para integridade referencial.
- Armazenamento em arquivos: inviavel para consultas, auditoria e consistencia.

**Trade-off:** O modelo relacional exige modelagem cuidadosa, mas oferece constraints importantes para RN06 e RN08.

---

## DA05 - Object Storage para arquivos

**Decisao:** Armazenar materiais e entregas em object storage, mantendo no banco apenas metadados e referencias.

**Motivacao:** Arquivos binarios podem crescer rapidamente e nao devem sobrecarregar o banco relacional.

**Alternativas consideradas:**
- Salvar arquivos no banco: simplifica backup logico, mas prejudica desempenho e escalabilidade.
- Salvar no filesystem local: simples, mas dificulta distribuicao e recuperacao.

**Trade-off:** Object storage adiciona integracao externa, mas separa responsabilidades de forma mais sustentavel.

---

## DA06 - Eventos para notificacoes e analise pedagogica

**Decisao:** Publicar eventos de negocio para processar notificacoes e indicadores de forma assincrona.

**Motivacao:** Publicacao de atividade, entrega avaliada e reabertura disparam comunicacoes. Esses passos nao precisam bloquear a operacao principal.

**Alternativas consideradas:**
- Envio sincrono na propria requisicao: mais simples, mas piora tempo de resposta e tolerancia a falhas.
- Agendamentos manuais: menos integrado ao fluxo real de uso.

**Trade-off:** Eventos exigem monitoramento da fila, mas tornam o sistema mais resiliente.
