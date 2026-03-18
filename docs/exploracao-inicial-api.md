# Exploração Inicial da API - Restful Booker

## Objetivo
Realizar o primeiro contato com a API Restful-Booker para entender sua estrutura, principais endpoints, comportamento das requisições e respostas, autenticação e possibilidades de testes manuais e futuros testes automatizados.

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

---

## Endpoints explorados

### 1. GET /booking
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

### 2. GET /booking/{id}
**Objetivo:** buscar os detalhes de uma reserva específica.

- **Método:** GET
- **URL testada:** `{{baseUrl}}/booking/17`
- **Autenticação:** não
- **Body:** não se aplica
- **Status code esperado:** 200
- **Resultado obtido:** 200 OK
- **Observações:** a resposta retorna os dados completos da reserva, incluindo:
  - firstname
  - lastname
  - totalprice
  - depositpaid
  - bookingdates
  - additionalneeds

**Conclusão:** endpoint funcionando corretamente para consulta detalhada de reserva específica.

---

### 3. POST /auth
**Objetivo:** gerar token de autenticação para operações protegidas.

- **Método:** POST
- **URL:** `{{baseUrl}}/auth`
- **Autenticação:** não
- **Body:** JSON com credenciais válidas
- **Status code esperado:** 200
- **Resultado obtido:** 200 OK
- **Observações:** a resposta retorna um token de autenticação para uso em endpoints protegidos, como atualização e exclusão de reservas.

**Conclusão:** endpoint funcionando corretamente para geração de token.

#### Exemplo de body utilizado
```json
{
  "username": "admin",
  "password": "password123"
}
```

---

### 4. POST /booking
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
- execução inicial de endpoints principais
- validação básica de respostas
- primeiros testes automatizados no próprio Postman

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
- uso de variáveis de ambiente
- automação de execuções com Collection Runner
- exportação da collection e environment
- execução via Newman
- integração futura com CI

---

## Conclusão
A exploração inicial da API Restful-Booker foi concluída com sucesso. Os principais endpoints de consulta, autenticação e criação de reserva foram executados corretamente no Postman. Também foi possível identificar um erro inicial de configuração no endpoint de criação, que foi corrigido durante a execução. Com isso, a base do projeto de testes de API foi montada com sucesso para continuidade nos próximos dias.
