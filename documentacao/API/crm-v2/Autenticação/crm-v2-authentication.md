Autenticação
ℹ️
As credenciais de autenticação dão acesso a apenas um produto RD Station escolhido. Para cada produto deverá ter suas próprias credenciais de acesso. Isso é válido para todas as credenciais, como client_id, client_secret e access_token.

A autenticação da API do RD Station CRM é baseada no protocolo de segurança OAuth2. Para essa integração, optamos por definir um prazo de expiração de 2 horas (7200 segundos) para os tokens.

End-point de autenticação OAuth2:


https://api.rd.services/oauth2/
Como funciona a autenticação?
Ao criar o seu aplicativo na RD Station App Store você receberá as duas credenciais, que chamamos de client_id e client_secret.

Essas credenciais são utilizadas para gerar o code, que autoriza a conexão do aplicativo à uma conta específica do RD Station CRM.

O code será utilizado uma única vez para gerar os tokens: access_token e o refresh_token.

Uma vez que os tokens tenham sido gerados, o access_token será utilizado no Header das requisições para autorizar as trocas de mensagens via API.

Para manter o access_token válido, basta você utilizar o refresh_token para renovar o access_token.

Ao utilizar o refresh_token para obter um novo access_token, um novo refresh_token também será retornado na resposta. É crucial que a sua aplicação armazene e utilize este novo refresh_token para as futuras renovações, descartando o anterior.

Passo a passo para realizar a autenticação
Acesse as páginas abaixo para conferir o passo a passo com a explicação detalhada do processo de Autenticação:

Passo 1: Criar um aplicativo e credenciais
Passo 2: Gerar código de autorização
Passo 3: Obter token de acesso
Passo 4: Renovar token de acesso
Ao concluir o passo 3, estará autorizado para operar a API e saberá como atualizar o seu token. Com o passo 4, você saberá como renovar o access_token.

Updated about 24 hours ago

