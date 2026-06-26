# Modelo C4 – Nível 1: Diagrama de Contexto

## Helix LMS – Visão de Contexto do Sistema

O Diagrama de Contexto mostra o sistema Helix LMS e suas relações com os usuários externos (atores) e sistemas externos.

---

## Representação Textual (C4 Context)

```
+-------------------------------------------------------------------+
|                        HELIX LMS                                  |
|         Sistema de Gestão de Sala de Aula Online                  |
|                                                                   |
|  Permite que professores publiquem atividades, estudantes         |
|  entreguem trabalhos e coordenadores acompanhem turmas.           |
+-------------------------------------------------------------------+
         ^                    ^                    ^               ^
         |                    |                    |               |
   [Estudante]          [Professor]          [Coordenador]  [Administrador]
   Acessa turmas,       Cria atividades,     Visualiza       Gerencia usuários
   submete entregas,    avalia entregas,     todas as        e configurações
   visualiza notas      gerencia turmas      turmas          do sistema

                                |
                                v
                    [Serviço de E-mail]
                   (SMTP / SendGrid)
                   Envia notificações
                   automáticas aos usuários
```

---

## Atores

### Estudante
- Usuário primário do sistema.
- Acessa turmas via código de matrícula.
- Submete entregas de atividades.
- Visualiza notas e feedbacks.

### Professor
- Cria e gerencia turmas.
- Publica, edita e encerra atividades.
- Avalia entregas dos estudantes.
- Acompanha desempenho da turma.

### Coordenador
- Visualiza todas as turmas da instituição (leitura).
- Acompanha métricas de desempenho acadêmico.
- Não modifica turmas de outros professores.

### Administrador
- Gerencia cadastro de usuários e perfis.
- Configura parâmetros do sistema.
- Mantém a infraestrutura da plataforma.

---

## Sistema Externo

### Serviço de E-mail (SMTP)
- Responsável pelo envio de notificações automáticas.
- Acionado em eventos como: nova atividade publicada, entrega avaliada, atividade reaberta, matrícula confirmada.
- Integração via protocolo SMTP (ex.: SendGrid, Mailgun ou servidor SMTP próprio).

---

## Fronteiras do Sistema

O Helix LMS é responsável por:
- Autenticação e controle de acesso (RBAC).
- Gestão completa de turmas, atividades, entregas e avaliações.
- Armazenamento de arquivos (delegado a object storage externo).
- Disparo de notificações (delegado a serviço de e-mail externo).

O Helix LMS **não** é responsável por:
- Gestão financeira ou de matrículas institucionais (sistemas legados da instituição).
- Videoconferência (prevista para versões futuras via integração com serviços externos).
- Aplicativo mobile (previsto para versões futuras).

---

## Referências

- Diagrama de Containers (Nível 2): `c4/containers.md`
- Decisões Arquiteturais: `docs/arquitetura.md`
- Regras de Negócio: `docs/regras-negocio.md`
