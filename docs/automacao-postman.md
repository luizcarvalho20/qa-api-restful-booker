# Automação de testes no Postman

## Objetivo
Implementar testes automatizados na collection do Postman para validar endpoints da API Restful Booker, cobrindo autenticação, criação, consulta, atualização e exclusão de reservas.

## O que foi desenvolvido
Foram adicionados scripts de testes utilizando `pm.test` nas requests da collection, com validações automáticas para status code, conteúdo da resposta, tempo de resposta e reutilização de variáveis de ambiente.

## Endpoints automatizados
- `GET /ping`
- `POST /auth`
- `POST /booking`
- `GET /booking/{{bookingid}}`
- `PUT /booking/{{bookingid}}`
- `PATCH /booking/{{bookingid}}`
- `DELETE /booking/{{bookingid}}`
- `GET /booking/{{bookingid}}` após exclusão

## Validações implementadas
- Status code
- Campos obrigatórios da resposta
- Tipos de dados
- Tempo de resposta
- Retorno de token
- Captura e reutilização de `token`
- Captura e reutilização de `bookingid`

## Variáveis de ambiente utilizadas
- `baseUrl`
- `token`
- `bookingid`

## Problemas encontrados
Durante a execução do fluxo, algumas requests falharam por inconsistência no nome da variável do ID da reserva.

## Correção aplicada
Foi realizada a padronização do nome da variável `bookingid`, corrigindo o encadeamento entre criação, consulta, atualização e exclusão da reserva.

## Resultado
Fluxo CRUD automatizado com sucesso no Postman, incluindo autenticação e validação pós-exclusão.

## Evidências
- `./evidencias/EV-API-001-runner-execucao-testes-automatizados.png`
- `./evidencias/EV-API-002-create-booking.png`

## Aprendizados
- Uso de `pm.test` para automação no Postman
- Uso de variáveis de ambiente para encadear requests
- Importância da padronização no nome das variáveis
- Validação automatizada de respostas e tempo de execução