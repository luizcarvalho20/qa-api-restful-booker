# Validações de Resposta - Restful Booker

## Objetivo
Documentar as validações realizadas nas respostas da API Restful Booker utilizando Postman, com foco em estrutura JSON, campos obrigatórios, tipos de dados e cenários de erro.

---

## Endpoint validado
### GET /booking/:id

### Validações realizadas
- Status code 200
- Content-Type contendo application/json
- Presença dos campos obrigatórios:
  - firstname
  - lastname
  - totalprice
  - depositpaid
  - bookingdates
- Presença de:
  - bookingdates.checkin
  - bookingdates.checkout
- Validação de tipos:
  - firstname → string
  - lastname → string
  - totalprice → number
  - depositpaid → boolean
  - bookingdates → object
  - bookingdates.checkin → string
  - bookingdates.checkout → string
- Validação de schema JSON

### Resultado
Passou

---

## Endpoint validado
### POST /booking

### Validações realizadas
- Status code 200
- Content-Type contendo application/json
- Presença de bookingid
- Presença do objeto booking
- Validação dos campos obrigatórios do objeto booking
- Comparação entre payload enviado e resposta retornada

### Resultado
Passou

---

## Cenário de erro validado
### GET /booking/999999999

### Validações realizadas
- Retorno diferente de 200
- Validação de status de erro para recurso inexistente

### Resultado observado
A API retornou status 404 Not Found para um booking inexistente, comportamento compatível com o cenário de recurso não encontrado.

### Resultado
Passou

---

## Evidências

- `EV-API-002-validacao-get-booking-by-id.png` — evidência da execução do endpoint `GET /booking/:id`, com validações de status code, Content-Type, campos obrigatórios, tipos de dados e schema JSON.
- `EV-API-003-validacao-post-create-booking.png` — evidência da execução do endpoint `POST /booking`, com validações de status code, presença de `bookingid`, objeto `booking` e comparação entre payload enviado e resposta retornada.
- `EV-API-004-validacao-get-booking-inexistente-404.png` — evidência do cenário de erro para recurso inexistente, demonstrando retorno `404 Not Found`.
- `EV-API-005-runner-validacoes-resumo.png` — evidência do resumo geral da execução no Collection Runner, consolidando os testes realizados e seus respectivos resultados.

---

## Conclusão
As validações confirmaram que a API retorna estruturas JSON consistentes nos cenários testados, com presença de campos obrigatórios, tipos esperados e comportamento adequado para recurso inexistente.