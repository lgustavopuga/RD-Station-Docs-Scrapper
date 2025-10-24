Como revogar o acesso de um token
post
https://api.rd.services/auth/revoke
Log in to see full request history
time	status	user agent	
Make a request to see history.
0 Requests This Month

Existem algumas razões pelas quais você pode precisar revogar o acesso de um aplicativo à conta de um usuário, por isso, o acesso dos clientes com Autenticação do tipo OAuth pode ser revogado sempre que necessário.

Ao revogar o acesso, os tokens (access_token e refresh_token) se tornarão inválidos e resultarão em uma solicitação401 (Unauthorized).

Para isso, você vai utilizar ovalor do token e o tipo do token no envio da sua requisição.

Você pode utilizar o recurso de "Try It" desta página para revogar o acesso dos tokens ou se basear para desenvolver a sua aplicação!

Form Data
token
string
Defaults to TOKEN
valor do token

TOKEN
token_type_hint
string
Defaults to TOKEN_TYPE
O tipo de token que você está revogando (refresh_token ou access_token)

TOKEN_TYPE
Response

200
200

Response body
object
Updated 28 days ago

input
```{Shell}
curl --request POST \
     --url https://api.rd.services/auth/revoke \
     --header 'accept: application/json' \
     --header 'content-type: application/x-www-form-urlencoded' \
     --data token=TOKEN \
     --data token_type_hint=TOKEN_TYPE
```

output
```{Json}
{}
```