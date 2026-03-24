# QA API - Restful Booker

## Resumo
Projeto prático de testes de API com **Postman** e **Newman**, cobrindo autenticação, fluxo CRUD completo, validações de resposta, uso de variáveis de ambiente, scripts em JavaScript no Postman e execução automatizada da collection via terminal.

## Sobre o projeto
Este projeto foi desenvolvido com foco na prática de testes de API REST utilizando a API pública **Restful Booker**. O objetivo foi explorar endpoints, validar respostas, estruturar cenários positivos e negativos, automatizar verificações com scripts no Postman e executar a collection de forma sequencial com o Newman.

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
A API pública utilizada neste projeto foi a **Restful Booker**, voltada para simulação de operações de reservas e amplamente usada para prática de testes de API REST.

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
- Validação de `Content-Type`
- Validação de presença de `bookingid`
- Validação de campos obrigatórios da resposta
- Validação de tipos de dados
- Validação de schema JSON
- Validação de cenário de erro com retorno `404 Not Found`
- Armazenamento automático de `token` no environment
- Armazenamento automático de `bookingid` no environment
- Execução da collection via Newman com assertions no terminal

## Fluxo principal validado
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
- `docs/exploracao-inicial-api.md` → exploração inicial dos endpoints
- `docs/validacoes-de-resposta.md` → validações de resposta, estrutura JSON, campos obrigatórios, tipos e cenário de erro
- `docs/cobertura-crud-auth.md` → cobertura CRUD autenticada com criação, consulta, atualização e exclusão de reservas
- `docs/automacao-postman.md` → automação inicial da collection no Postman
- `docs/automacao-newman.md` → execução da collection via Newman

## Evidências
As evidências do projeto estão organizadas por etapa de execução:

- `evidencias/testes iniciais/` → exploração inicial e validações básicas
- `evidencias/CRUD-AUTH/` → fluxo CRUD autenticado
- `evidencias/NEWMAN/` → execução da collection via terminal com Newman
- `evidencias/TESTES AUTOMATIZADOS/` → registros visuais dos testes automatizados

## Aprendizados
Este projeto permitiu consolidar fundamentos importantes de testes de API, como manipulação de variáveis de ambiente, autenticação por token, validação de payloads JSON, encadeamento de requisições dependentes e execução automatizada da collection via Newman.

Durante a execução do projeto, foi possível praticar:
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

## Próximos passos
- Gerar relatório HTML com Newman
- Integrar futuramente a execução com CI

## Autor
Luiz Felipe Carvalho
