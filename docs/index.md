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

---

## Integração com Jenkins

Este projeto conta com um arquivo Jenkinsfile (na raiz do repositório) que define uma pipeline de integração contínua para compilar automaticamente o módulo sempre que houver alterações no repositório.

### Para que serve?

- Compilação automatizada: toda alteração no repositório dispara o build do Maven, detectando problemas de compilação antes do merge.

- Imagens Docker consistentes: gera e publica automaticamente imagens multiplataforma, facilitando o deploy em diferentes ambientes (x86_64 e ARM).

- Segurança das credenciais: utiliza credenciais armazenadas no Jenkins (identificador dockerhub-credential), evitando exposição de senhas no código.

Dessa forma, a integração com Jenkins garante que o gateway-service esteja sempre compilando e empacotado corretamente, com uma imagem Docker pronta para ser implantada nos clusters de produção ou QA.
