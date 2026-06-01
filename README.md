# coolify-n8n-main

Repositório de deploy Git-based do `n8n-main` no Coolify.

Este recurso executa somente a UI, API, triggers e coordenação do n8n em queue mode. Ele não executa worker local e não inclui task runner.

## Responsabilidade

- Subir `n8n-main` com `command: start`.
- Conectar no Postgres externo do n8n.
- Conectar no Redis dedicado do n8n.
- Publicar o domínio público do n8n.
- Enviar execuções para workers com `OFFLOAD_MANUAL_EXECUTIONS_TO_WORKERS=true`.

## Fora do repositório

- `.env` real.
- Segredos.
- Postgres.
- Redis.
- Worker.
- Task runner.

As variáveis reais devem ser configuradas no recurso Git-based do Coolify.
