Token de autenticação
O Token é um código de autenticação, utilizado para validar a conta do usuário e autorizar a integração com outras ferramentas.

Para saber como criar, visualizar e gerenciar o token, basta acessar aqui.

Cada usuário do RD Station CRM possui um token único e imutável, cujas permissões de uso da API são definidas pelo nível de visibilidade do usuário.

A visibilidade define quais informações referentes a negociações, empresas e contatos cada usuário poderá visualizar.

Visibilidade dos resultados
Os níveis de visibilidade são divididos entre três categorias:

Negociações
Empresas
Contatos
E os níveis possuem as seguintes especificidades:

Restrito: o usuário só poderá visualizar as informações pelas quais é responsável, dentro da categoria definida.
Equipe: o usuário poderá visualizar as informações de todos que façam parte de sua equipe, dentro da categoria definida.
Geral: o usuário poderá visualizar todas as informações da categoria definida, sem restrição.
Rotas dependentes do nível de visibilidade
As rotas cujas requisições e resultados são influenciados pelo nível de visibilidade do usuário detentor do token, são:

Negociações
Empresas
Contatos
Tarefas
Como funciona na prática?
Para exemplificar, veja abaixo como funciona o retorno da API no gerenciamento de negociações conforme o nível de visibilidade do usuário dono do token na categoria de negociações:

Nível de visibilidade: Restrito

Ao interagir com o end-point de listar negociações, serão retornadas somente as negociações cujo responsável é o dono do token.

Ao interagir com o end-point de obter negociação, a negociação só será obtida se o deal_id passado na query for referente a uma negociação que o dono do token é responsável.

Ao interagir com o end-point de atualizar negociação, você só conseguirá atualizar negociações cujo responsável é o dono do token.

Ao interagir com o end-point de criar negociação, você conseguirá criar negociações para outros usuários, mas só conseguirá visualizar negociações criadas com o dono do token como responsável.

Nível de Visibilidade: Equipes

Ao interagir com o end-point de listar negociações, serão retornadas somente as negociações cujo dono do token é responsável e dos usuários das equipes que o dono do token faz parte.

Ao interagir com o end-point de obter negociação, a negociação só será obtida se o deal_id passado na query for referente a uma negociação cujo responsável é o dono do token ou um dos usuários das equipes que o dono do token faz parte.

Ao interagir com o end-point de atualizar negociação, você só conseguirá atualizar negociações cujo responsável é o dono do token ou um dos usuários das equipes que o dono do token faz parte.

Ao interagir com o end-point de criar negociação, você conseguirá criar negociações para outros usuários, mas só conseguirá visualizar negociações criadas com o dono do token como responsável ou criadas com um dos usuários das equipes que o dono do token faz parte como responsável.

Nível de Visibilidade: Geral

Consegue listar, obter, criar e atualizar todas as negociações, independentemente de qual usuário é responsável.

ℹ️
A funcionalidade de visibilidade está disponível apenas para clientes do plano Basic e Pro.

Updated 2 days ago

