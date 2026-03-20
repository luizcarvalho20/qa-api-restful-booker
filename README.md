# QA API - Restful Booker

## Sobre o projeto
Projeto prático de testes de API utilizando Postman com a API Restful Booker, com foco em exploração de endpoints REST, validação manual de respostas, autenticação, uso de variáveis de ambiente e criação de testes básicos com scripts no Postman.

## Objetivos
- Praticar testes manuais de API
- Explorar endpoints REST
- Validar status codes, estrutura de resposta e comportamento da API
- Trabalhar com autenticação via token
- Utilizar variáveis de ambiente no Postman
- Estruturar uma base para evolução em automação com Postman, Newman e CI

## Ferramentas utilizadas
- Postman
- JSON
- Git
- GitHub
- Markdown

## Estrutura do projeto
- `docs/` → documentação da exploração inicial e das validações realizadas
- `evidencias/` → imagens de execução e registros visuais dos testes
- `postman/collections/` → collections exportadas do Postman
- `postman/environments/` → environments exportados do Postman

## API utilizada
Restful Booker

## Escopo do projeto
- Criação da collection no Postman
- Criação do environment com variáveis reutilizáveis
- Exploração inicial dos endpoints principais da API
- Execução de requisições GET e POST
- Geração de token de autenticação
- Criação de testes básicos com scripts no Postman
- Validação de estrutura JSON, campos obrigatórios e tipos de dados
- Validação de cenário de erro para recurso inexistente

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
- Validação de Content-Type
- Validação de presença de `bookingid`
- Validação de campos obrigatórios da resposta
- Validação de tipos de dados
- Validação de schema JSON
- Validação de cenário de erro com retorno `404 Not Found`
- Armazenamento automático de `token` no environment
- Armazenamento automático de `bookingId` no environment

## Variáveis de ambiente utilizadas
- `baseUrl`
- `bookingId`
- `token`

## Documentação disponível
- `docs/exploracao-inicial-api.md` → documentação da exploração inicial dos endpoints
- `docs/validacoes-de-resposta.md` → documentação das validações de resposta, incluindo estrutura JSON, campos obrigatórios, tipos e cenário de erro

## Evidências
- `evidencias/EV-API-001-testes-iniciais-criar-reserva.png` → evidência da validação inicial do endpoint de criação de reserva
- `evidencias/EV-API-002-validacao-get-booking-by-id.png` → evidência da execução e validação do endpoint `GET /booking/:id`
- `evidencias/EV-API-003-validacao-post-create-booking.png` → evidência da execução e validação do endpoint `POST /booking`
- `evidencias/EV-API-004-validacao-get-booking-inexistente-404.png` → evidência do cenário de erro para recurso inexistente
- `evidencias/EV-API-005-runner-validacoes-resumo.png` → evidência do resumo geral das execuções no Collection Runner

## Aprendizados
Durante a execução deste projeto, foi possível praticar:
- estrutura de requisições REST
- uso de variáveis de ambiente no Postman
- envio de body em formato JSON
- análise de payload de resposta
- validações com scripts no Postman
- reaproveitamento de dados dinâmicos entre requisições
- validação de estrutura de resposta JSON
- análise de comportamento da API em cenários positivos e negativos

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