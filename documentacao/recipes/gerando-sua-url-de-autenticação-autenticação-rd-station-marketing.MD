```{Shell}
client_id="APP_CLIENT_ID"
secret_id="APP_SECRET_ID"
redirect_uri="https://redirecturl.com.br/callback" // Esta é a sua URL de callback.

// Cole a URL acima no seu navegador e autorize o aplicativo.
"https://api.rd.services/auth/dialog?client_id=${client_id}&redirect_uri=${redirect_uri}"

// O código será enviado para o callback. Defina ele com o comando abaixo.
"https://yourapp.org/auth/callback?code=${code}"

code="CODIGO_RETORNADO"
```