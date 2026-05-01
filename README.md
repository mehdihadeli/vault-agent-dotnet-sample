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

docker compose -f docker-compose.infrastructure.yml up -d
while ! docker logs vault-init 2>&1 | grep -q "Vault configured"; do sleep 2; done
docker compose -f docker-compose.apps.yml up -d --build
