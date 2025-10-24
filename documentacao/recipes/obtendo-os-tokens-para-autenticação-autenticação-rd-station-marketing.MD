```{Javascript}
const clientId = "APP_CLIENT_ID";
const clientSecret = "APP_SECRET_ID";
const authorizationCode = "CODIGO_RETORNADO";

const options = {
  method: 'POST',
  headers: {accept: 'application/json', 'content-type': 'application/json'},
  body: JSON.stringify({client_id: 'CLIENT_ID', client_secret: 'CLIENT_SECRET'})
};

fetch('https://api.rd.services/auth/token?token_by=code', options)
  .then(response => response.json())
  .then(response => console.log(response))
  .catch(err => console.error(err));
```