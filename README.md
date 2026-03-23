# QA API - Restful Booker

## Sobre o projeto
Projeto prático de testes de API utilizando Postman com a API Restful Booker, com foco em exploração de endpoints REST, validação manual de respostas, autenticação, uso de variáveis de ambiente, criação de testes com scripts no Postman e execução da collection via Newman.

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
- Newman
- JSON
- JavaScript
- Git
- GitHub
- Markdown

## Estrutura do projeto
- `docs/` → documentação da exploração inicial, validações realizadas, cobertura CRUD autenticada e execução com Newman
- `evidencias/` → imagens de execução e registros visuais dos testes
- `postman/collection/` → collection exportada do Postman
- `postman/environment/` → environment exportado do Postman

## API utilizada
Restful Booker

## Escopo do projeto
- Criação da collection no Postman
- Criação do environment com variáveis reutilizáveis
- Exploração inicial dos endpoints principais da API
- Execução de requisições `GET`, `POST`, `PUT`, `PATCH` e `DELETE`
- Geração de token de autenticação
- Criação de testes com scripts no Postman
- Validação de estrutura JSON, campos obrigatórios e tipos de dados
- Validação de cenário de erro para recurso inexistente
- Cobertura do fluxo CRUD completo de reservas autenticadas
- Execução da collection via terminal com Newman

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
- Armazenamento automático de `bookingid` no environment
- Execução da collection via Newman com assertions no terminal

## Fluxo CRUD validado
- `Create Token`
- `Create Booking`
- `Buscar reserva`
- `Get Booking by ID - Sucesso`
- `Update Booking`
- `Partial Update Booking`
- `Delete Booking`
- `Get Booking by ID - Após Delete`
- `Create Booking - Validacao`
- `Booking Inexistente - Erro`

## Variáveis de ambiente utilizadas
- `baseUrl`
- `bookingid`
- `token`

## Documentação disponível
- `docs/exploracao-inicial-api.md` → documentação da exploração inicial dos endpoints
- `docs/validacoes-de-resposta.md` → documentação das validações de resposta, incluindo estrutura JSON, campos obrigatórios, tipos e cenário de erro
- `docs/cobertura-crud-auth.md` → documentação da cobertura CRUD autenticada com criação, consulta, atualização e exclusão de reservas
- `docs/automacao-postman.md` → documentação da automação inicial da collection no Postman
- `docs/automacao-newman.md` → documentação da execução da collection via Newman

## Evidências

### Testes iniciais
- `evidencias/testes iniciais/EV-API-001-testes-iniciais-criar-reserva.png` → evidência da validação inicial do endpoint de criação de reserva
- `evidencias/testes iniciais/EV-API-001-validacao-get-booking-by-id-sucesso.png` → evidência da execução e validação do endpoint `GET /booking/:id`
- `evidencias/testes iniciais/EV-API-002-validacao-post-create-booking-sucesso.png` → evidência da execução e validação do endpoint `POST /booking`
- `evidencias/testes iniciais/EV-API-003-validacao-get-booking-inexistente-erro-404.png` → evidência do cenário de erro para recurso inexistente
- `evidencias/testes iniciais/EV-API-004-runner-validacoes-resumo-execucao.png` → evidência do resumo geral das execuções iniciais no Collection Runner

### CRUD + Auth
- `evidencias/CRUD-AUTH/EV-API-001-create-token.png` → evidência da geração de token de autenticação
- `evidencias/CRUD-AUTH/EV-API-002-create-booking.png` → evidência da criação de reserva
- `evidencias/CRUD-AUTH/EV-API-003-get-booking-by-id.png` → evidência da consulta de reserva por ID
- `evidencias/CRUD-AUTH/EV-API-004-update-booking.png` → evidência da atualização completa de reserva com `PUT`
- `evidencias/CRUD-AUTH/EV-API-005-partial-update-booking.png` → evidência da atualização parcial de reserva com `PATCH`
- `evidencias/CRUD-AUTH/EV-API-006-delete-booking.png` → evidência da exclusão de reserva com `DELETE`
- `evidencias/CRUD-AUTH/EV-API-007-delete-booking-confirm.png` → evidência da validação de inexistência do recurso após exclusão
- `evidencias/CRUD-AUTH/EV-API-008-runner-execucao.png` → evidência da execução completa da collection com cobertura CRUD + Auth e todos os testes aprovados

### Newman
- `evidencias/NEWMAN/EV-API-001-execucao-teste-newman-sucesso.png` → evidência da execução da collection com sucesso via Newman no terminal
- `evidencias/NEWMAN/resultado-newman-terminal.txt` → registro textual da execução da collection via Newman

## Aprendizados
Durante a execução deste projeto, foi possível praticar:
- estrutura de requisições REST
- uso de variáveis de ambiente no Postman
- envio de body em formato JSON
- análise de payload de resposta
- validações com scripts em JavaScript no Postman
- reaproveitamento de dados dinâmicos entre requisições
- validação de estrutura de resposta JSON
- autenticação por token
- validação de fluxo CRUD completo
- análise de comportamento da API em cenários positivos e negativos
- organização de collection para execução sequencial no Runner
- execução de collections via terminal com Newman
- estabilização de fluxo automatizado com dependência entre requests

## Problemas encontrados
Durante o desenvolvimento do projeto, alguns problemas foram identificados:
- na primeira tentativa de criação de reserva, a API retornou erro `500` devido à configuração incorreta do body da requisição no Postman
- durante a etapa de atualização com `PUT`, houve retorno `403 Forbidden` em tentativas iniciais por conta de execução fora da ordem ideal do fluxo e necessidade de reutilização correta de `token` e `bookingid`
- na execução com Newman, ocorreram falhas iniciais por conta de variável `baseUrl` incorreta no environment exportado
- alguns cenários falharam inicialmente por conta da ordem de execução da collection e da dependência entre criação, consulta e exclusão da reserva
- alguns testes estavam redundantes ou associados a cenários incompatíveis com o fluxo final

## Correções aplicadas
- ajuste do body para `raw`
- seleção do formato `JSON`
- conferência do header `Content-Type: application/json`
- reorganização da sequência de execução da collection
- separação entre cenários positivos e negativos
- adaptação dos scripts para cada etapa do fluxo CRUD
- reutilização correta das variáveis `token` e `bookingid` no environment
- correção do `baseUrl` no environment exportado para execução via Newman
- reorganização da collection para garantir execução estável no terminal
- remoção de testes redundantes e ajustes em validações dependentes da ordem dos requests

Após os ajustes, a collection passou a executar com sucesso tanto no Collection Runner quanto no Newman, com todos os testes aprovados.

## Como executar

### Via Postman
1. Importe a collection disponível em `postman/collection/`
2. Importe o environment disponível em `postman/environment/`
3. Selecione o environment `Restful-Booker - Dev`
4. Execute as requisições manualmente ou pelo Collection Runner

### Via Newman
```powershell
newman run ".\postman\collection\Restful-Booker API.postman_collection.json" -e ".\postman\environment\Restful-Booker - Dev.postman_environment.json"
```

### Fluxo principal validado
- `Create Token`
- `Create Booking`
- `Buscar reserva`
- `Get Booking by ID - Sucesso`
- `Update Booking`
- `Partial Update Booking`
- `Delete Booking`
- `Get Booking by ID - Após Delete`
- `Create Booking - Validacao`
- `Booking Inexistente - Erro`

## Próximos passos
- Adicionar mais cenários negativos para autenticação e atualização
- Ampliar a cobertura de validações automatizadas no Postman
- Gerar relatório HTML com Newman
- Integrar futuramente a execução com CI
- Evoluir o projeto para uma abordagem mais próxima de testes automatizados de API

## Autor
Luiz Felipe Carvalho
