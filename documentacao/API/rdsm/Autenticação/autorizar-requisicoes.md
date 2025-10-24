Como utilizar o access_token para autorizar suas requisições
Após obter o access_token, ele será utilizado para autorizar a troca de mensagens via API.

Para isso, ele deverá ser enviado no Cabeçalho ("Header") de cada requisição para a API Pública.

O seu Header deve conter, obrigatoriamente, os seguintes parâmetros:

Header	Required
Authorization: Bearer access_token	Required on client request
Content-Type: application/json	Required on client request
Esse é um exemplo de como os parâmetros devem ser configurados no Header das suas requisições:
```{cURL}
curl --request POST \
     --url https://api.rd.services/platform/contacts \
     --header 'accept: application/json' \
     --header 'authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwczovL2FwaS5yZC5zZXJ2aWNlcyIsInN1YiI6InlURlh3ZUxKbkJWVGxaeUk3VEVSQXhQa0pNYkVZT2NHZDVEUXpzcGFQOUlAY2xpZW50cyIsImF1ZCI6Imh0dHBzOi8vYXBwLnJkc3RhdGlvbi5jb20uYnIvYXBpL3YyLyIsImFwcF9uYW1lIjoiMjIxQiBCYWtlciBTdHJlZXQiLCJleHAiOjE2ODU1NTcxNTAsImlhdCI6MTY4NTQ3MDc1MCwic2NvcGUiOiIifQ.rHgZb-2373-4i8UzzhKAoFhJu4EMPTIwUf6GqHmCLDGTboAzF1AiBZFas-3yKy71WUE7whVXFXg664PwwT8Y18Ruv8ktoqbO0HaXebkZNxN4SxjRmtgcbaMgSxlH1NvwRXhbT6yFWOTzREcj_5zDm8EWs-7KeXe_3BCoD6NPbPpsHblMdVy4oKHwQCcFf8F-pXsWUOGv1_4jNnrONo_nfC8hzo8o7nNMBiZhHQy0BPcgC0u6zdTUakaUO9btX6SB3E_ZOn6Z_U5HSBM9ldTf-s61xmjzRobuUQQrrITkiKm2HMGoAHK_Ak4L97DlVtQMaeXUtdnEQ06Vb-7YIAGs-w' \
     --header 'content-type: application/json'
```
Se o access_token for é válido, a API retornará sucesso 2xx e processará a solicitação, conforme as suas especificações.

Se o access_token estiver expirado ou mesmo inválido, a API retornará um erro deUnauthorized Request e será necessário atualizar o access_token para enviar as requisições.

Updated 28 days ago

