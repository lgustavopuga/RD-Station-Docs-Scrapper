Passo 3: Como obter os tokens (access_token e refresh_token)
post
https://api.rd.services/auth/token?token_by=code
###[Passo 3 de 4]

Log in to see full request history
time	status	user agent	
Make a request to see history.

Obtendo os tokens
Uma vez recebido o parâmetro code, só falta obter o access_token e refresh_token.

Para isso, você vai utilizar o client_id e client_secret obtidos ao criar o App (passo 1) e o code obtido no passo anterior no envio da sua requisição.

❗️
O code tem duração de 1 hora.
Por isso, esse passo precisa ser realizado antes que ele expire. Se o code tiver expirado, você receberá o erro "EXPIRED_CODE_GRANT".

Objetivo dos tokens recebidos neste passo
O access_token é utilizado para autorizar suas requisições. Ele possui data de expiração pré-determinada definida pelo atributo expires_in em segundos, que é de 86400 segundos (24 Horas).
O refresh_token é utilizado para obter um novoaccess_token quando ele expirar. O refresh_token não expira.
👍
Agora que você obteve os tokens, o CODE não é mais necessário.
Apenas será necessário trabalhar com o refresh_token recebido nesta etapa, para gerar um novo access_token.

Você pode utilizar o recurso de "Try It" desta página para obter os seus tokens ou se basear para desenvolver a sua aplicação!

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
code
string
Defaults to CODE
code recebido na URL de callback

CODE
Response

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
Updated 28 days ago

input
```{Shell}
curl --request POST \
     --url 'https://api.rd.services/auth/token?token_by=code' \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "client_id": "CLIENT_ID",
  "client_secret": "CLIENT_SECRET",
  "code": "CODE"
}
'
```

output
```{JSON}
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6Ik5UZ3hRamM1UWpKR1FUUkNPRVE0UVRZeFJFVTBNRFEzUkRGRE9UVXdPVE5FTXpVM09UUXpRUSJ9.eyJpc3MiOiJodHRwczovL3Jkc3RhdGlvbi5hdXRoMC5jb20vIiwic3ViIjoidklUYjF2N0NoVmhmUVE2QUFTbDNLVUpYRUJTSVNCR2hAY2xpZW50cyIsImF1ZCI6Imh0dHBzOi8vYXBwLnJkc3RhdGlvbi5jb20uYnIvYXBpL3YyLyIsImV4cCI6MTUwNDI5NDQzMSwiaWF0IjoxNTA0MjA4MDMxLCJzY29wZSI6IiJ9.k7OSdhOlTgRBZmEhg_uXXaCofEq4iwDdBi6yuD8SxMF06nCA834KjIqWkmX-W-u84q8SEzGyhb_KT0zZlMvyGotoGPMry_vABXEIorC25zKCUE9BtMJpHJ_suFwQMqZQ8rK6JSnbkOKwLuuDq8_YnrutBURJiBSdSI9325MLw0DZdnw0IgXnNVCHRLdOMl4k_Ovk5Ke3yzESJvMxgJJ3UnojL0ckRExVPwxnbLCyJp1W_PsEe-FOcEl0kDEX-8JQ8MGATiB2vZOu5TJi4sbYCLzg3GInegGh9zvZQR1W4K3isDtOmlNRSYU9A5ez3dQ8HTZdCj9gT_aGWWskxWi6Cw",
  "expires_in": 86400,
  "refresh_token": "9YORmXHgOI32k-Y22tZWm-rsf--oFPr8JDCQIQhBEUY"
}
```