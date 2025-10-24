```{Javascript}
const refreshToken = 'seu_refresh_token_aqui';

const requestOptions = {
  method: 'POST',
  headers: {
    'Content-Type': 'application/x-www-form-urlencoded',
  },
  body: `grant_type=refresh_token&refresh_token=${refreshToken}`,
};

const tokenEndpoint = 'https://api.rd.services/auth/token';

fetch(tokenEndpoint, requestOptions)
  .then(response => response.json())
  .then(data => {
    const accessToken = data.access_token;
    console.log('Novo access token:', accessToken);
  })
  .catch(error => {
    console.error('Erro ao obter novo access token:', error);
  });
```