# Gateway Service

O `gateway-service` é o ponto de entrada para todos os microsserviços da plataforma. Ele atua como um **API Gateway** com:

- **Encaminhamento de requisições (routing)**
- **Validação de rotas seguras**
- **Autenticação de tokens via Auth Service**
- **Suporte a CORS**
- **Endpoint informativo (`/info`)**

---

## Principais responsabilidades

- Encaminhar requisições com base nas rotas definidas no `application.yaml`
- Validar se uma rota exige autenticação
- Consultar o `auth-service` para validar tokens JWT
- Repassar o `idAccount` no header para os microsserviços internos
