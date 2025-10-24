Introdução e requisitos
A API (Application Programming Interface ou Interface de Programação de Aplicativos) é um padrão de programação, com conjuntos de instruções cuja finalidade é desenvolver a integração entre diferentes plataformas de softwares, como o RD Station Marketing e outra ferramenta que você utilize.

Aqui você vai encontrar a coleção de recursos do RD Station Marketing para realizar a integração com o seu sistema.

Veja a seguir alguns pontos importantes:

API RESTful - Todas as nossas APIs são organizadas em torno da arquitetura REST e são acessadas via HTTP.
Então, se você já interagiu com uma API RESTful, muitos dos conceitos serão familiares.

Domínio base - Todas as chamadas de API para o RD Station Marketing devem ser feitas para o domínio base <https://api.rd.services>.

Respostas da API - Todas as respostas da API, incluindo casos de erro, serão retornados em formato JSON.

URLs previsíveis - As APIs são projetadas para ter URLs previsíveis para acessar recursos e utilizam os códigos de resposta HTTP para indicar erros da API.

Requisitos para começar
Possuir uma conta do RD Station, se ainda não tiver, crie uma aqui.
Possuir um aplicativo com uma API que você pode acessar.
Um pouco de conhecimento de programação.
Token de acesso
Dentro do escopo da nossa API 2.0, existem duas formas de autenticação: Oauth2 e API Key.

Oauth2: é utilizada para enviar eventos, marcar e desmarcar oportunidades, registrar vendas, atualizar contatos sem conversão, consultar diversas informações do RD Station Marketing, e os demais recursos disponíveis.
API Key: é utilizada exclusivamente para envio de eventos de conversão para criar e atualizar contatos com o registro de uma conversão. É recomendada para integração de formulários e sistemas internos que enviam conversões para o RD Station Marketing.
Segurança
As APIs são fornecidas somente sob o protocolo TLS (Transport Layer Security) na versão 1.3 utilizado pelo HTTPs. Isto se deve ao fato que a versão atual (1.3) de aumentar a segurança da comunicação por ser uma evolução dos protocolos de segurança mais modernos, abandonou compatibilidade com outros protocolos antigos defasados que possuem vulnerabilidades de segurança.

Outro motivo para o uso do TLS1.3 é a melhora na latência pois foram implementadas otimizações principalmente no handshake (momento em que a comunicação é estabelecida).

📘
Quer saber mais sobre RESTful?
Caso você não tenha ouvido falar de RESTful, recomendamos este guia externo como referência.

💬
Precisa de suporte?
Nós também temos uma Central de Ajuda bem completa.

Continua com dúvida? Não se preocupe! Contamos com uma equipe especializada que pode te ajudar.

Updated 28 days ago

