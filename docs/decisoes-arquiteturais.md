# Decisões arquiteturais

## DA01 — Arquitetura híbrida

A arquitetura foi pensada para combinar fluxo síncrono e assíncrono. O núcleo do sistema funciona em camadas, enquanto notificações e análises são processadas por eventos.

## DA02 — Autorização centralizada

As regras de permissão foram tratadas no backend para garantir consistência e segurança. Isso é essencial para regras como publicação de atividade por professor vinculado.

## DA03 — Comunicação via eventos

A publicação de atividades, registro de entregas e liberação de notas geram eventos, o que evita acoplamento direto entre o fluxo principal e os serviços de notificação.

## DA04 — Banco relacional

Foi escolhido um modelo relacional porque o domínio envolve relações fortes entre turma, atividade, entrega e avaliação.
