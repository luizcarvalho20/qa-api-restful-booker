# QA API - Restful Booker

## Sobre o projeto
Projeto prático de testes de API utilizando Postman com a API Restful Booker, com foco em validação manual de endpoints REST, status codes, estrutura de payloads, autenticação e uso de variáveis de ambiente.

## Objetivos
- Praticar testes manuais de API
- Explorar endpoints REST
- Validar status codes e respostas
- Trabalhar com autenticação via token
- Estruturar uma base para evolução em automação com Postman, Newman e CI

## Ferramentas utilizadas
- Postman
- JSON
- Git
- GitHub

## Estrutura do projeto
- `docs/` → documentação da exploração e anotações dos testes
- `evidencias/` → imagens de execução e registros visuais
- `postman/collections/` → collections exportadas do Postman
- `postman/environments/` → environments exportados do Postman

## API utilizada
Restful Booker

## Escopo inicial
- Criação da collection no Postman
- Criação do environment com variáveis reutilizáveis
- Exploração inicial dos endpoints principais da API
- Execução de requisições GET e POST
- Validação inicial de respostas e comportamento da API

## Endpoints explorados
- `GET /booking`
- `GET /booking/{id}`
- `POST /auth`
- `POST /booking`
- `GET /ping`

## Validações realizadas
- Listagem de reservas
- Consulta de reserva por ID
- Geração de token de autenticação
- Criação de reserva
- Validação de status code
- Validação de presença de `bookingid`
- Validação de campo `firstname` na resposta
- Armazenamento automático de `token` no environment
- Armazenamento automático de `bookingId` no environment

## Variáveis de ambiente utilizadas
- `baseUrl`
- `bookingId`
- `token`

## Aprendizados
Durante a execução deste projeto, foi possível praticar:
- estrutura de requisições REST
- uso de variáveis de ambiente no Postman
- envio de body em formato JSON
- análise de payload de resposta
- validações básicas com scripts no Postman
- reaproveitamento de dados dinâmicos entre requisições

## Problema encontrado
Na primeira tentativa de criação de reserva, a API retornou erro 500 devido à configuração incorreta do body da requisição no Postman.

## Correção aplicada
- ajuste do body para `raw`
- seleção do formato `JSON`
- conferência do header `Content-Type: application/json`

Após a correção, a requisição passou a ser executada com sucesso.

## Como executar
1. Importe a collection disponível em `postman/collections/`
2. Importe o environment disponível em `postman/environments/`
3. Selecione o environment `Restful-Booker - Dev`
4. Execute as requisições manualmente ou pelo Collection Runner

## Próximos passos
- Criar testes para PUT, PATCH e DELETE
- Adicionar cenários positivos e negativos
- Ampliar as validações automatizadas no Postman
- Executar a collection com Newman
- Integrar a execução futuramente com CI

## Autor
Luiz Felipe Carvalho