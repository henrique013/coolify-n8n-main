# Deploy do n8n-main

## Configuração no Coolify

Criar uma aplicação Git-based com:

```text
Repository: henrique013/coolify-n8n-main
Branch: main
Build Pack: Docker Compose
Base Directory: /
Docker Compose Location: docker-compose.yml
```

## Variáveis obrigatórias

As variáveis reais ficam somente no Coolify:

```text
N8N_IMAGE
N8N_HOST
N8N_PROTOCOL
N8N_PORT
WEBHOOK_URL
GENERIC_TIMEZONE
N8N_ENCRYPTION_KEY
OFFLOAD_MANUAL_EXECUTIONS_TO_WORKERS
N8N_POSTGRES_HOST
N8N_POSTGRES_PORT
N8N_POSTGRES_DATABASE
N8N_POSTGRES_USER
N8N_POSTGRES_PASSWORD
N8N_REDIS_HOST
N8N_REDIS_PORT
N8N_REDIS_PASSWORD
N8N_REDIS_DB
```

O diretório persistente do host é `/data/n8n/shared/.n8n`. Na migração do serviço manual antigo, copie para esse diretório o conteúdo do volume que guardava `/home/node/.n8n`.

O recurso Coolify deve ficar com `Connect to Predefined Network` habilitado. O domínio deve ser configurado no serviço Compose `n8n-main`, com a porta interna `5678`.

## Migração

Não deixe dois `n8n-main` ativos usando o mesmo Postgres e Redis.

Sequência segura:

1. Criar o recurso Git-based sem deploy ativo.
2. Configurar as variáveis no Coolify.
3. Confirmar a janela de migração.
4. Parar o serviço manual antigo.
5. Mover ou liberar o domínio público.
6. Fazer deploy deste recurso.
7. Validar saúde, UI, Postgres e Redis.

Não remova o serviço manual antigo na primeira validação.
