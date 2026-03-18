# QA API - Restful Booker

## Sobre o projeto
Projeto prático de testes de API utilizando Postman com a API Restful-Booker, desenvolvido como parte de um plano de 21 dias para construção de portfólio em QA.

## Objetivos
- Praticar testes manuais de API
- Explorar endpoints REST
- Validar status codes, payloads e autenticação
- Evoluir para automação com Postman e Newman

## Ferramentas utilizadas
- Postman
- JSON
- Git e GitHub

## Estrutura do projeto
- `docs/` documentação da exploração e anotações dos testes
- `evidencias/` imagens de execução e registros visuais
- `postman/collections/` collections exportadas do Postman
- `postman/environments/` environments exportados do Postman

## API utilizada
Restful-Booker

## Escopo inicial
- Exploração dos endpoints
- Criação de collection
- Criação de environment
- Levantamento inicial de comportamentos da API

## Endpoints explorados até o momento
- `GET /booking`
- `GET /booking/{id}`
- `POST /auth`
- `POST /booking`

## Validações realizadas
- Listagem de reservas
- Consulta de reserva por ID
- Geração de token
- Criação de reserva
- Validação de status code 200
- Validação de retorno de `bookingid`
- Validação de campo `firstname` na resposta

## Aprendizados iniciais
Durante a exploração inicial da API, foi possível entender melhor:
- estrutura de requisições REST
- uso de variáveis de ambiente no Postman
- envio de body em formato JSON
- importância dos headers corretos
- criação de testes básicos no Postman

## Problema encontrado
Durante a primeira tentativa de criação de reserva, a API retornou erro 500 devido à configuração incorreta do body da requisição no Postman.

## Correção aplicada
- ajuste do body para `raw`
- seleção do tipo `JSON`
- validação do header `Content-Type: application/json`

Após a correção, a requisição foi executada com sucesso.

## Próximos passos
- Criar testes para PUT, PATCH e DELETE
- Adicionar cenários positivos e negativos
- Exportar collection e environment
- Executar testes com Collection Runner
- Evoluir para execução via Newman
- Integrar futuramente com CI

## Como executar
1. Importar a collection exportada em `postman/collections/`
2. Importar o environment exportado em `postman/environments/`
3. Selecionar o environment `Restful-Booker - Dev`
4. Executar as requisições manualmente ou via Collection Runner

## Autor
Luiz Felipe Carvalho
