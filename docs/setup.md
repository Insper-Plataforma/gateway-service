# Setup e Execução - Gateway Service

O `gateway-service` é o ponto de entrada para todos os microsserviços da plataforma. Ele atua como um **API Gateway**.

## Requisitos

- Java 17+
- Spring Boot
- Spring Cloud Gateway
- WebFlux
- Lombok

---

## Dependências principais (`pom.xml`)

- `spring-boot-starter-webflux`
- `spring-cloud-starter-gateway`
- `spring-boot-starter-reactor-netty`
- `lombok`
- `webclient`

---

## Como compilar

```bash
mvn clean package
```

## Segurança

O serviço depende do auth-service para validar tokens JWT:
- Tokens inválidos são rejeitados com HTTP 401
- Tokens válidos adicionam id-account aos headers das requisições internas