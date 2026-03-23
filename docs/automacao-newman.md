# Execução da Collection com Newman

## Objetivo
Executar a collection de testes da API Restful Booker via terminal utilizando o Newman, validando os cenários fora da interface do Postman e aproximando o projeto de um fluxo mais próximo de automação de testes em ambiente real.

## Contexto
Após a criação dos testes no Postman, a collection foi exportada junto com o environment para permitir a execução via linha de comando.

Durante a configuração, foi necessário revisar:
- o valor da variável `baseUrl` no environment exportado
- a padronização da variável `bookingid`
- a ordem de execução dos requests
- testes redundantes e cenários que não faziam mais sentido dentro do fluxo atual

Esses ajustes foram importantes para garantir uma execução estável e coerente do fluxo CRUD.

## Estrutura utilizada
```text
postman/
├─ collection/
│  └─ Restful-Booker API.postman_collection.json
└─ environment/
   └─ Restful-Booker - Dev.postman_environment.json

docs/
└─ execucao-newman.md

evidencias/
└─ NEWMAN/
   └─ EV-API-001-execucao-teste-newman-sucesso.png
```

## Instalação do Newman
```powershell
npm install -g newman
```

## Comando de execução
```powershell
newman run ".\postman\collection\Restful-Booker API.postman_collection.json" -e ".\postman\environment\Restful-Booker - Dev.postman_environment.json"
```

## Cenários validados
A execução via Newman contemplou os seguintes cenários:

- geração de token de autenticação
- listagem de reservas
- criação de reserva
- busca de reserva por ID
- validação de campos obrigatórios e tipos
- atualização completa de reserva
- atualização parcial de reserva
- exclusão de reserva
- validação de erro 404 após exclusão
- health check da API
- validação da estrutura da resposta no create booking
- validação de booking inexistente

## Ajustes realizados
Durante a execução via terminal, alguns pontos precisaram ser corrigidos para estabilizar a collection:

### Environment
Foi necessário revisar o arquivo exportado do environment para garantir que a variável `baseUrl` estivesse corretamente definida, evitando falhas de URL inválida na execução do Newman.

### Variáveis
Foi feita a padronização do uso da variável `bookingid` ao longo da collection, garantindo consistência entre criação, leitura, atualização e exclusão de reservas.

### Ordem de execução
A collection foi reorganizada para respeitar a dependência entre os cenários. Requests que dependiam da criação prévia de uma reserva passaram a ser executados somente após o `Create Booking`.

### Testes redundantes
Alguns testes foram removidos ou ajustados por estarem redundantes ou por validarem cenários incompatíveis com o fluxo final da collection.

## Resultado final
Após os ajustes, a execução da collection com Newman foi concluída com sucesso, com todos os requests e assertions passando no terminal.

### Resumo da execução
- 12 requests executados
- 0 falhas de request
- 11 scripts de teste executados
- 37 assertions executadas
- 0 assertions falhadas

## Evidências
As evidências da execução foram armazenadas na pasta `evidencias/NEWMAN/`.

### Arquivo de evidência
- `./evidencias/NEWMAN/EV-API-001-execucao-teste-newman-sucesso.png`

## Conclusão
A execução com Newman permitiu validar a collection fora da interface do Postman, reforçando a reprodutibilidade dos testes e preparando a base do projeto para evoluções futuras, como integração com CI/CD e execução automatizada em pipeline.
