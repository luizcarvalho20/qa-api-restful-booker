# Cobertura CRUD + Auth

## Objetivo
Validar o fluxo completo de operações autenticadas na API Restful Booker, cobrindo autenticação, criação, consulta, atualização completa, atualização parcial e exclusão de reservas.

## Fluxos testados
- Create Token
- Create Booking
- Get Booking by ID - Sucesso
- Update Booking
- Partial Update Booking
- Delete Booking
- Get Booking Inexistente - Erro

## Variáveis utilizadas
- `baseUrl`
- `token`
- `bookingId`

## Validações realizadas
- Status codes esperados para cada endpoint
- Presença de token na autenticação
- Presença de `bookingId` após criação
- Integridade dos dados retornados no GET
- Alteração correta dos dados no PUT
- Alteração parcial apenas dos campos esperados no PATCH
- Exclusão do recurso no DELETE
- Confirmação de inexistência do recurso após exclusão

## Resultado
Execução completa da collection com todos os testes aprovados no Runner.

## Evidências
```
/evidencias/CRUD-AUTH/EV-API-008-runner-execucao.png
```
