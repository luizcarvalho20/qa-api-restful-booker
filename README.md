# QA API - Restful Booker

## Sobre o projeto
Projeto prático de testes de API utilizando Postman com a API Restful Booker, com foco em exploração de endpoints REST, validação manual de respostas, autenticação, uso de variáveis de ambiente e criação de testes com scripts no Postman.

## Objetivos
- Praticar testes manuais de API
- Explorar endpoints REST
- Validar status codes, estrutura de resposta e comportamento da API
- Trabalhar com autenticação via token
- Utilizar variáveis de ambiente no Postman
- Validar o fluxo completo de vida de um recurso com operações CRUD
- Estruturar uma base para evolução em automação com Postman, Newman e CI

## Ferramentas utilizadas
- Postman
- JSON
- JavaScript
- Git
- GitHub
- Markdown

## Estrutura do projeto
- `docs/` → documentação da exploração inicial, validações realizadas e cobertura CRUD
- `evidencias/` → imagens de execução e registros visuais dos testes
- `postman/collections/` → collections exportadas do Postman
- `postman/environments/` → environments exportados do Postman

## API utilizada
Restful Booker

## Escopo do projeto
- Criação da collection no Postman
- Criação do environment com variáveis reutilizáveis
- Exploração inicial dos endpoints principais da API
- Execução de requisições GET, POST, PUT, PATCH e DELETE
- Geração de token de autenticação
- Criação de testes com scripts no Postman
- Validação de estrutura JSON, campos obrigatórios e tipos de dados
- Validação de cenário de erro para recurso inexistente
- Cobertura do fluxo CRUD completo de reservas autenticadas

## Endpoints explorados
- `GET /booking`
- `GET /booking/{id}`
- `POST /auth`
- `POST /booking`
- `PUT /booking/{id}`
- `PATCH /booking/{id}`
- `DELETE /booking/{id}`
- `GET /ping`

## Validações realizadas
- Listagem de reservas
- Consulta de reserva por ID
- Geração de token de autenticação
- Criação de reserva
- Atualização completa de reserva com `PUT`
- Atualização parcial de reserva com `PATCH`
- Exclusão de reserva com `DELETE`
- Validação de inexistência do recurso após exclusão
- Validação de status code
- Validação de Content-Type
- Validação de presença de `bookingid`
- Validação de campos obrigatórios da resposta
- Validação de tipos de dados
- Validação de schema JSON
- Validação de cenário de erro com retorno `404 Not Found`
- Armazenamento automático de `token` no environment
- Armazenamento automático de `bookingId` no environment

## Fluxo CRUD validado
- `Create Token`
- `Create Booking`
- `Get Booking by ID - Sucesso`
- `Update Booking`
- `Partial Update Booking`
- `Delete Booking`
- `Get Booking Inexistente - Erro`

## Variáveis de ambiente utilizadas
- `baseUrl`
- `bookingId`
- `token`

## Documentação disponível
- `docs/exploracao-inicial-api.md` → documentação da exploração inicial dos endpoints
- `docs/validacoes-de-resposta.md` → documentação das validações de resposta, incluindo estrutura JSON, campos obrigatórios, tipos e cenário de erro
- `docs/cobertura-crud-auth.md` → documentação da cobertura CRUD autenticada com criação, consulta, atualização e exclusão de reservas

## Evidências
- `evidencias/EV-API-001-testes-iniciais-criar-reserva.png` → evidência da validação inicial do endpoint de criação de reserva
- `evidencias/EV-API-002-validacao-get-booking-by-id.png` → evidência da execução e validação do endpoint `GET /booking/:id`
- `evidencias/EV-API-003-validacao-post-create-booking.png` → evidência da execução e validação do endpoint `POST /booking`
- `evidencias/EV-API-004-validacao-get-booking-inexistente-404.png` → evidência do cenário de erro para recurso inexistente
- `evidencias/EV-API-005-runner-validacoes-resumo.png` → evidência do resumo geral das execuções no Collection Runner
- `evidencias/EV-API-006-runner-crud-auth-sucesso.png` → evidência da execução completa da collection com cobertura CRUD + Auth e todos os testes aprovados

## Aprendizados
Durante a execução deste projeto, foi possível praticar:
- estrutura de requisições REST
- uso de variáveis de ambiente no Postman
- envio de body em formato JSON
- análise de payload de resposta
- validações com scripts em JavaScript no Postman
- reaproveitamento de dados dinâmicos entre requisições
- validação de estrutura de resposta JSON
- autenticação por token via cookie
- validação de fluxo CRUD completo
- análise de comportamento da API em cenários positivos e negativos
- organização de collection para execução sequencial no Runner

## Problemas encontrados
Durante o desenvolvimento do projeto, alguns problemas foram identificados:
- na primeira tentativa de criação de reserva, a API retornou erro `500` devido à configuração incorreta do body da requisição no Postman
- durante a etapa de atualização com `PUT`, houve retorno `403 Forbidden` em tentativas iniciais por conta de execução fora da ordem ideal do fluxo e necessidade de reutilização correta de `token` e `bookingId`
- na execução da collection, uma falha inicial ocorreu porque a validação de recurso inexistente foi aplicada em um `GET` que ainda fazia parte do fluxo positivo

## Correções aplicadas
- ajuste do body para `raw`
- seleção do formato `JSON`
- conferência do header `Content-Type: application/json`
- reorganização da sequência de execução da collection
- separação entre `Get Booking by ID - Sucesso` e `Get Booking Inexistente - Erro`
- adaptação dos scripts para cada etapa do fluxo CRUD
- reutilização correta das variáveis `token` e `bookingId` no environment

Após os ajustes, a collection passou a executar com sucesso no Runner, com todos os testes aprovados.

## Como executar
1. Importe a collection disponível em `postman/collections/`
2. Importe o environment disponível em `postman/environments/`
3. Selecione o environment `Restful-Booker - Dev`
4. Execute as requisições manualmente ou pelo Collection Runner
5. Para o fluxo CRUD completo, execute na ordem:
   - `Create Token`
   - `Create Booking`
   - `Get Booking by ID - Sucesso`
   - `Update Booking`
   - `Partial Update Booking`
   - `Delete Booking`
   - `Get Booking Inexistente - Erro`

## Próximos passos
- Adicionar mais cenários negativos para autenticação e atualização
- Ampliar a cobertura de validações automatizadas no Postman
- Executar a collection com Newman
- Gerar relatórios de execução
- Integrar futuramente a execução com CI
- Evoluir o projeto para uma abordagem mais próxima de testes automatizados de API

## Autor
Luiz Felipe Carvalho