# Exploração Inicial da API - Restful Booker

## Objetivo
Realizar a exploração inicial da API Restful Booker para entender sua estrutura, principais endpoints, comportamento das requisições e respostas, autenticação, uso de variáveis de ambiente e oportunidades de evolução para testes automatizados.

## Base URL
`https://restful-booker.herokuapp.com`

## Ferramenta utilizada
- Postman

## Collection criada
- `Restful-Booker API`

## Environment criado
- `Restful-Booker - Dev`

## Variáveis utilizadas
- `baseUrl = https://restful-booker.herokuapp.com`
- `bookingId = ID da reserva criada dinamicamente`
- `token = token gerado dinamicamente`

---

## Endpoints explorados

### 1. GET /ping
**Objetivo:** validar disponibilidade da API.

- **Método:** GET
- **URL:** `{{baseUrl}}/ping`
- **Autenticação:** não
- **Body:** não se aplica
- **Status code esperado:** 201
- **Resultado obtido:** 201 Created
- **Observações:** endpoint utilizado para confirmar que a API está disponível para testes.

**Conclusão:** endpoint funcionando corretamente para validação de disponibilidade.

---

### 2. GET /booking
**Objetivo:** listar reservas cadastradas na aplicação.

- **Método:** GET
- **URL:** `{{baseUrl}}/booking`
- **Autenticação:** não
- **Body:** não se aplica
- **Status code esperado:** 200
- **Resultado obtido:** 200 OK
- **Observações:** a resposta retorna uma lista de reservas contendo identificadores (`bookingid`).

**Conclusão:** endpoint funcionando corretamente para listagem inicial de reservas.

---

### 3. GET /booking/{id}
**Objetivo:** buscar os detalhes de uma reserva específica.

- **Método:** GET
- **URL:** `{{baseUrl}}/booking/{{bookingId}}`
- **Autenticação:** não
- **Body:** não se aplica
- **Status code esperado:** 200
- **Resultado obtido:** 200 OK
- **Observações:** a resposta retorna os dados completos da reserva, incluindo:
  - `firstname`
  - `lastname`
  - `totalprice`
  - `depositpaid`
  - `bookingdates`
  - `additionalneeds`

**Conclusão:** endpoint funcionando corretamente para consulta detalhada de reserva específica.

---

### 4. POST /auth
**Objetivo:** gerar token de autenticação para operações protegidas.

- **Método:** POST
- **URL:** `{{baseUrl}}/auth`
- **Autenticação:** não
- **Body:** JSON com credenciais válidas
- **Status code esperado:** 200
- **Resultado obtido:** 200 OK
- **Observações:** a resposta retorna um token de autenticação para uso em endpoints protegidos, como atualização e exclusão de reservas. O token foi armazenado automaticamente na variável de ambiente `token`.

**Conclusão:** endpoint funcionando corretamente para geração e armazenamento de token.

#### Exemplo de body utilizado
```json
{
  "username": "admin",
  "password": "password123"
}
```

#### Testes adicionados no Postman
- Status code deve ser 200
- Resposta deve conter token

---

### 5. POST /booking
**Objetivo:** criar uma nova reserva.

- **Método:** POST
- **URL:** `{{baseUrl}}/booking`
- **Autenticação:** não
- **Body:** JSON
- **Status code esperado:** 200
- **Resultado obtido:** 200 OK
- **Observações:** a resposta retorna:
  - `bookingid`
  - objeto `booking` com os dados cadastrados

Além disso, o `bookingid` retornado foi armazenado automaticamente na variável de ambiente `bookingId`, permitindo o reaproveitamento dinâmico em outras requisições.

#### Exemplo de body utilizado
```json
{
  "firstname": "Luiz",
  "lastname": "Carvalho",
  "totalprice": 1500,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2026-03-18",
    "checkout": "2026-03-20"
  },
  "additionalneeds": "Breakfast"
}
```

#### Testes adicionados no Postman
- Status code deve ser 200
- Resposta deve conter bookingid
- Resposta deve conter firstname correto

**Conclusão:** endpoint funcionando corretamente após ajuste da configuração do body da requisição no Postman.

---

## Problema encontrado durante a exploração
Durante a execução inicial do endpoint `POST /booking`, a API retornou erro **500 Internal Server Error**.

### Causa identificada
A falha ocorreu devido à configuração incorreta da requisição no Postman, especificamente no envio do body.

### Ação realizada
Foi ajustado o envio da requisição para o formato correto:
- Body em `raw`
- Tipo `JSON`
- Header `Content-Type: application/json`

### Resultado após correção
Após o ajuste, a requisição foi executada com sucesso e retornou **200 OK** com criação da reserva e retorno do `bookingid`.

---

## Estrutura inicial validada
Até o momento, a estrutura inicial do projeto contempla:
- exploração manual da API
- criação de collection no Postman
- criação de environment no Postman
- execução dos endpoints principais
- validação básica de respostas
- criação de testes básicos no Postman
- armazenamento automático de dados dinâmicos em variáveis de ambiente

---

## Riscos iniciais percebidos
Durante a exploração inicial, foram identificados os seguintes pontos de atenção para as próximas etapas de teste:

- falhas de validação de campos obrigatórios
- comportamento inconsistente para payloads inválidos
- necessidade de validar autenticação em endpoints protegidos
- necessidade de validar atualização total e parcial de reservas
- necessidade de validar remoção de reservas
- necessidade de validar contrato de resposta e tipos de dados

---

## Próximos passos
Nas próximas etapas do projeto, os testes deverão evoluir para:

- validação mais completa de GET e POST
- testes de autenticação
- testes de PUT, PATCH e DELETE
- cenários positivos e negativos
- ampliação dos testes automatizados no Postman
- execução com Collection Runner
- exportação e versionamento da collection e environment
- execução via Newman
- integração futura com CI

---

## Conclusão
A exploração inicial da API Restful Booker foi concluída com sucesso. Os principais endpoints de disponibilidade, consulta, autenticação e criação de reserva foram executados corretamente no Postman. Também foi possível identificar e corrigir um erro de configuração no endpoint de criação de reserva. Com isso, a base inicial do projeto foi estruturada com collection, environment, testes básicos e reaproveitamento de variáveis dinâmicas, preparando o repositório para as próximas etapas de evolução dos testes de API.
