Filtrando com RDQL
A API v2 do CRM utiliza a RDQL (RD Query Language) para realizar filtros avançados em listagens de recursos. Para aplicar um filtro, utilize o parâmetro de query filter.

A sintaxe básica é filter=campo:valor. Por exemplo, para buscar negociações com o nome "Teste", a query seria filter=name:Teste.

Operadores
Operador	Exemplo	Descrição
=	status:won	Status é "won"
!=	-status:won	Status é diferente de "won"
>	total_price:>100	Preço total é maior que 100
<	total_price:<100	Preço total é menor que 100
>=	total_price:>=100	Preço total é maior ou igual a 100
<=	total_price:<=100	Preço total é menor ou igual a 100
IN	status:(won,lost)	Status é "won" ou "lost"
NIN	-status:(won,lost)	Status não é "won" nem "lost"
MATCH	name:~Test	Nome contém "Test" (case-insensitive)
Tipos de dados
Tipo	Exemplo
String	string, "string com espaços"
Integer	10
Float	10.5
Date	2023-01-01
DateTime	"2023-01-01 12:00:00"
Time	12:00:00
Array	(1, "2 b", 3c)
Agrupamentos e operadores lógicos
É possível agrupar expressões com parênteses e utilizar operadores lógicos como and (padrão) e or.

Exemplo	Descrição
status:won total_price:>100	Status é "won" E preço total é maior que 100
status:won or status:lost	Status é "won" OU "lost"
(status:won or status:lost) and total_price:>100	(Status é "won" OU "lost") E preço total é maior que 100
Filtro por campos personalizados
Campos personalizados podem ser filtrados usando o prefixo @ seguido do slug do campo personalizado.

Exemplo	Descrição
@setor:tecnologia	Campo personalizado "setor" é igual a "tecnologia".
-@ativo:true	Campo personalizado "ativo" é diferente de "true".
@prioridade:(alta,media)	Campo personalizado "prioridade" é "alta" ou "media".
Recursos que suportam filtro por campos personalizados:

Negociações (Deals)
Contatos (Contacts)
Empresas (Organizations)
Produtos (Products)
Updated about 24 hours ago