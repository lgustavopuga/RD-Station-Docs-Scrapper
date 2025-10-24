Introdução e requisitos
A API (Application Programming Interface ou Interface de Programação de Aplicativos) é um padrão de programação, com conjuntos de instruções cuja finalidade é desenvolver a integração entre diferentes plataformas de softwares, como o RD Station CRM e outra ferramenta que você utilize.

Aqui você vai encontrar a coleção de recursos do RD Station CRM para realizar a integração com o seu sistema.

Veja a seguir alguns pontos importantes:

API RESTful: Todas as nossas APIs são organizadas em torno da arquitetura REST e são acessadas via HTTP.
Então, se você já interagiu com uma API RESTful, muitos dos conceitos serão familiares.
Respostas da API: Todas as respostas da API, incluindo casos de erro, serão retornados em formato JSON.
URLs previsíveis: As APIs são projetadas para ter URLs previsíveis para acessar recursos e utilizam os códigos de resposta HTTP para indicar erros da API.
Requisitos para começar
Possuir uma conta do RD Station CRM, se ainda não tiver, crie uma aqui.
As requisições devem ser enviadas no formato JSON;
Todas as requisições devem ter o código Token do usuário da conta do RD Station CRM;
O Modo Desenvolvedor deve ser previamente ativado, para facilitar a coleta do ID dos componentes;
Ter uma conta do plano Basic, Pro ou Advanced do RD Station CRM.
Um pouco de conhecimento de programação.
Limites
Ao utilizar o método listar de cada entidade (negociação, empresa e contato) é possível listar apenas os 10 mil primeiros registros a cada requisição.
A API tem um limite de 120 requisições por minuto.
Mapeamento de nomenclaturas
As nomenclaturas de negociações, empresas e contatos, utilizadas no corpo da requisição, deverão seguir o padrão da API, conforme o exemplo abaixo:

RD Station CRM	API
Negociação	deal
Empresa	organization
Contato	contact
Ações possíveis com o uso da API v1
Modelo/Ação	Criar	Atualizar	Excluir	Listar	Obter
Token	✘	✘	✘	✘	✓
Tarefas	✓	✓	✘	✓	✓
Anotações	✓	✘	✘	✓	✓
Negociações	✓	✓	✘	✓	✓
Contatos da negociação	✘	✘	✘	✓	✘
Produtos na negociação	✓	✓	✓	✓	✘
Usuários	✘	✘	✘	✓	✓
Equipes	✘	✘	✘	✓	✓
Empresas	✓	✓	✘	✓	✓
Contatos	✓	✓	✘	✓	✓
Produtos	✓	✓	✘	✓	✓
Campos personalizados	✓	✓	✓	✓	✓
Funil de vendas	✓	✓	✘	✓	✓
Etapas do funil de vendas	✓	✓	✘	✓	✓
Campanhas	✓	✓	✘	✓	✓
Fontes	✓	✓	✘	✓	✓
Motivo de perda	✓	✓	✘	✓	✓
📘
Quer saber mais sobre RESTful?
Caso você não tenha ouvido falar de RESTful, recomendamos este guia externo como referência.

💬
Precisa de suporte?
Nós também temos uma Central de Ajuda bem completa.

Continua com dúvida? Não se preocupe! Contamos com uma equipe especializada que pode te ajudar.

Updated 2 days ago