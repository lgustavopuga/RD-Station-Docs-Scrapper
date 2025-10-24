Passo 4: Renovar token de acesso
Como renovar o access_token
O access_token do RD Station CRM tem validade de 2 horas. Quando ele expirar, sua aplicação deverá usar o refresh_token para obter um novo access_token de forma programática, sem que o usuário precise passar pelo fluxo de autorização novamente.

O refresh_token expirará caso não seja utilizado por um período de 14 dias. Contanto que sua aplicação o utilize para renovar o access_token dentro desse intervalo, a conexão se manterá ativa indefinidamente.

Quando renovar o token
Você deve renovar o access_token quando:

Receber o erro 401 Unauthorized em uma requisição;
O access_token estiver prestes a expirar (recomenda-se renovar quando faltar menos de 5 minutos);
O usuário retornar ao aplicativo após um período de inatividade.
Fazendo a requisição de renovação
Envie uma requisição POST para o end-point de tokens com grant_type=refresh_token.

Exemplo com cURL:
```{Shell}
curl -X POST https://api.rd.services/oauth2/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d 'client_id=seu-client-id-aqui' \
  -d 'client_secret=seu-client-secret-aqui' \
  -d 'refresh_token=seu-refresh-token-aqui' \
  -d 'grant_type=refresh_token'
```
Importante sobre o refresh_token
O refresh_token é renovado a cada uso (rolling refresh token);
O novo refresh_token terá uma nova data de expiração (14 dias a partir da renovação);
Sempre armazene o novo refresh_token retornado, o antigo já não funciona mais;
Se o refresh_token expirar, o usuário precisará fazer o fluxo de autorização novamente.
Implementação recomendada
Antes de cada requisição à API:

Verifique se o access_token atual está expirado ou prestes a expirar (recomenda-se renovar quando faltar menos de 5 minutos);
Se sim, use o refresh_token para obter um novo access_token;
Substitua o par de tokens anterior (access_token e refresh_token) pelo novo par recebido na resposta da API;
Repita a requisição original com o novo token.
Updated about 24 hours ago