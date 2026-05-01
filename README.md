```bash
project/
├── docker-compose.infrastructure.yml
├── docker-compose.apps.yml
├── infrastructure/
│   ├── postgres/init.sql
│   └── vault/configure.sh
├── agent-config/
│   ├── orders/
│   │   ├── vault-agent.hcl
│   │   └── appsettings.ctmpl
│   └── users/
│       ├── vault-agent.hcl
│       └── appsettings.ctmpl
├── src/
│   ├── Contracts/Contracts.csproj
│   ├── OrdersApi/
│   │   ├── Dockerfile
│   │   ├── OrdersApi.csproj
│   │   └── Program.cs
│   └── UsersApi/
│       ├── Dockerfile
│       ├── UsersApi.csproj
│       └── Program.cs
└── deploy.sh
```

In deployments directory:

```bash
docker compose -f docker-compose.infrastructure.yml up -d
docker compose -f docker-compose.apps.dev.yml up -d
```
