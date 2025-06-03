# Arquitetura

## Estrutura de Pastas

```bash
src/main/java/store/gateway/
├── GatewayApplication.java # Classe principal
├── GatewayResource.java # Endpoint de status/sistema
├── security/
│ ├── AuthorizationFilter.java # Valida tokens e injeta idAccount
│ ├── CorsFilter.java # Libera CORS
│ ├── RouterValidator.java # Verifica se rota é protegida
│ ├── TokenOut.java # Token recebido
│ └── SolveOut.java # ID extraído do token
└── resources/
│ └── application.yaml # Configurações de ambiente
```

---

## Requisições seguras

O filtro `AuthorizationFilter`:

- Ignora rotas abertas (ex: `/auth/login`)
- Para rotas protegidas:
  - Exige header `Authorization: Bearer <token>`
  - Envia o token para `auth-service` (`/auth/solve`)
  - Se válido, adiciona `id-account` no header

---

## Encaminhamento de rotas

As rotas estão definidas no `application.yaml` usando `spring.cloud.gateway.routes`.

Exemplo:

```yaml
- id: account
  uri: http://account:8080
  predicates:
    - Path=/account/**
```
