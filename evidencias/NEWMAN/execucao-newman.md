Restful-Booker API

□ Auth
└ Create Token
  POST https://restful-booker.herokuapp.com/auth [200 OK, 766B, 615ms]
  √  Status code deve ser 200
  √  Resposta deve conter token
  √  Salvar token no environment
  √  Tempo de resposta menor que 1000ms

□ Booking
└ Listar reservas
  GET https://restful-booker.herokuapp.com/booking [200 OK, 66.29kB, 411ms]

└ Create Booking
  POST https://restful-booker.herokuapp.com/booking [200 OK, 953B, 136ms]
  √  Status code de criação válido
  √  Resposta contém bookingid e booking
  √  Salvar bookingid no environment
  √  Tempo de resposta menor que 1000ms

└ Buscar reserva
  GET https://restful-booker.herokuapp.com/booking/5071 [200 OK, 924B, 139ms]
  √  Status code deve ser 200
  √  Resposta deve conter campos obrigatórios
  √  Campos devem ter tipos válidos
  √  Tempo de resposta menor que 1000ms

└ Get Booking by ID - Sucesso
  GET https://restful-booker.herokuapp.com/booking/5071 [200 OK, 924B, 139ms]
  √  Status code should be 200
  √  Firstname is correct
  √  Lastname is correct

└ Update Booking
  PUT https://restful-booker.herokuapp.com/booking/5071 [200 OK, 932B, 143ms]
  √  Status code deve ser 200
  √  Reserva atualizada com sucesso
  √  Tempo de resposta menor que 1000ms

└ Partial Update Booking
  PATCH https://restful-booker.herokuapp.com/booking/5071 [200 OK, 924B, 140ms]
  √  Status code deve ser 200
  √  Atualização parcial realizada com sucesso
  √  Tempo de resposta menor que 1000ms

└ Delete booking
  DELETE https://restful-booker.herokuapp.com/booking/5071 [201 Created, 751B, 142ms]
  √  Status code de exclusão válido
  √  Resposta deve conter Created
  √  Tempo de resposta menor que 1000ms

└ Get Booking by ID - Após Delete
  GET https://restful-booker.herokuapp.com/booking/5071 [404 Not Found, 755B, 140ms]
  √  Status code deve ser 404
  √  Tempo de resposta menor que 1000ms

□ Health
└ PING
  GET https://restful-booker.herokuapp.com/ping [201 Created, 751B, 139ms]
  √  Status code deve ser 201
  √  Resposta deve conter Created
  √  Tempo de resposta menor que 1000ms

□ Validações
└ Create Booking - Validacao
  POST https://restful-booker.herokuapp.com/booking [200 OK, 949B, 137ms]
  √  Status code deve ser 200
  √  Content-Type deve conter application/json
  √  Resposta deve conter bookingid
  √  Resposta deve conter objeto booking
  √  Objeto booking deve conter os campos obrigatórios
  √  Dados retornados devem bater com o enviado

└ Booking Inexistente - Erro
  GET https://restful-booker.herokuapp.com/booking/999999999 [404 Not Found, 751B, 139ms]
  √  Deve retornar status de erro ou não encontrado
  √  Resposta de erro não deve ser sucesso 200

┌─────────────────────────┬─────────────────────┬────────────────────┐
│                         │            executed │             failed │
├─────────────────────────┼─────────────────────┼────────────────────┤
│              iterations │                   1 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│                         │            executed │             failed │
├─────────────────────────┼─────────────────────┼────────────────────┤
│              iterations │                   1 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│                requests │                  12 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│            test-scripts │                  11 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│      prerequest-scripts │                   0 │                  0 │
├─────────────────────────┼─────────────────────┼────────────────────┤
│              assertions │                  37 │                  0 │
├─────────────────────────┴─────────────────────┴────────────────────┤
│ total run duration: 3.2s                                           │
├────────────────────────────────────────────────────────────────────┤
│ total data received: 66.7kB (approx)                               │
├────────────────────────────────────────────────────────────────────┤
│ average response time: 201ms [min: 136ms, max: 615ms, s.d.: 145ms] │