Passo 4: Como utilizar o refresh_token para atualizar o access_token
post
https://api.rd.services/auth/token
###[Passo 4 de 4]

Log in to see full request history
time	status	user agent	
Make a request to see history.

Após gerar os tokens, você deverá utilizar o refresh_token para atualizar o access_token a cada 24 horas; após o recebimento do access_token.

Renovando o access_token
Para isso, você vai utilizar o client_id e client_secret obtidos ao criar o App (passo 1) e o refresh_token obtido ao gerar os tokens (passo 3) no envio da sua requisição.

📘
A sua aplicação pode armazenar o refresh_token em uma variável e criar uma função condicional para verificar se o access_token retornou “200” (ok!). Caso sim, a integração continua ocorrendo. Caso não, ou seja, se apontou algum erro, você cria uma função para criar um novo access_token (utilizando o refresh_token).
Você pode utilizar o recurso de "Try It" desta página para atualizar o access_token ou se basear para desenvolver a sua aplicação!

Body Params
client_id
string
Defaults to CLIENT_ID
client_id do aplicativo

CLIENT_ID
client_secret
string
Defaults to CLIENT_SECRET
client_secret do aplicativo

CLIENT_SECRET
refresh_token
string
Defaults to REFRESH_TOKEN
refresh_token retornado na criação do token

REFRESH_TOKEN
Responses

200
200

Response body
object
access_token
string
expires_in
integer
Defaults to 0
refresh_token
string

401
401

Updated 28 days ago

input
```{Shell}
curl --request POST \
     --url https://api.rd.services/auth/token \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "client_id": "CLIENT_ID",
  "client_secret": "CLIENT_SECRET",
  "refresh_token": "REFRESH_TOKEN"
}
'
```

output
```{Json}
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6Ik5UZ3hRamM1UWpKR1FUUkNPRVE0UVRZeFJFVTBNRFEzUkRGRE9UVXdPVE5FTXpVM09UUXpRUSJ9.eyJpc3MiOiJodHRwczovL3Jkc3RhdGlvbi5hdXRoMC5jb20vIiwic3ViIjoidklUYjF2N0NoVmhmUVE2QUFTbDNLVUpYRUJTSVNCR2hAY2xpZW50cyIsImF1ZCI6Imh0dHBzOi8vYXBwLnJkc3RhdGlvbi5jb20uYnIvYXBpL3YyLyIsImV4cCI6MTUwNDI5NDQzMSwiaWF0IjoxNTA0MjA4MDMxLCJzY29wZSI6IiJ9.k7OSdhOlTgRBZmEhg_uXXaCofEq4iwDdBi6yuD8SxMF06nCA834KjIqWkmX-W-u84q8SEzGyhb_KT0zZlMvyGotoGPMry_vABXEIorC25zKCUE9BtMJpHJ_suFwQMqZQ8rK6JSnbkOKwLuuDq8_YnrutBURJiBSdSI9325MLw0DZdnw0IgXnNVCHRLdOMl4k_Ovk5Ke3yzESJvMxgJJ3UnojL0ckRExVPwxnbLCyJp1W_PsEe-FOcEl0kDEX-8JQ8MGATiB2vZOu5TJi4sbYCLzg3GInegGh9zvZQR1W4K3isDtOmlNRSYU9A5ez3dQ8HTZdCj9gT_aGWWskxWi6Cw",
  "expires_in": 86400,
  "refresh_token": "9YORmXHgOI32k-Y22tZWm-rsf--oFPr8JDCQIQhBEUY"
}
```