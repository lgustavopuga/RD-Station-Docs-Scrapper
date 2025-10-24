Autenticação
A Autenticação para utilização da API do RD Station Marketing é baseada no protocolo de segurança OAuth2, o que significa que ela trabalha com tokens com prazo de expiração pré-determinados.

Como funciona a Autenticação?
ℹ️
As credenciais de autenticação dão acesso a apenas um produto RD Station escolhido. Para cada produto deverá ter suas próprias credenciais de acesso. Isso é válido para todas as credenciais, como client_id, client_secret e access_token

Ao criar o seu aplicativo na RD Station App Store você receberá as duas credenciais, que chamamos de client_id e client_secret.

Essas credenciais são utilizadas para gerar o code, que autoriza a conexão do aplicativo à uma conta específica do RD Station Marketing.

O code será utilizado uma única vez para gerar os tokens: access_token e o refresh_token.

Uma vez que os tokens tenham sido gerados, o access_token será utilizado no Header das requisições para autorizar as trocas de mensagens via API.

Para manter o access_token válido, basta você utilizar o refresh_token como uma variável no script da integração para atualizar o access_token quando ele expirar.

Passo a Passo para realizar a Autenticação
Acesse as páginas abaixo para conferir o passo a passo com a explicação detalhada do processo de Autenticação:

Passo 1: Como criar o aplicativo e gerar as Credenciais (client_id e client_secret)
Passo 2: Como utilizar as Credenciais para gerar o code
Passo 3: Como obter os tokens (access_token e refresh_token)
Passo 4: Como utilizar o refresh_token para atualizar o access_token
Ao concluir o passo 4, estará autorizado para operar a API e saberá como atualizar o seu token.

Updated 14 days ago