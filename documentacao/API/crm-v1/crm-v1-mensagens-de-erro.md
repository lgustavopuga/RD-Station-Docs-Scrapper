Mensagens de erro
Usamos códigos HTTP convencionais nas respostas para indicar o sucesso ou a falha de uma solicitação da API. Em geral, os códigos no intervalo 2xx indicam sucesso, os códigos no intervalo 4xx indicam um erro que falhou dado a informação fornecida (por exemplo, um parâmetro obrigatório foi omitido, uma falha de carga, etc.) e os códigos no intervalo 5xx indicam um erro com nossos servidores (estes são raros).

Códigos HTTP
Código	Description
400 (Bad request)	Malformed body request
401 (Unauthorized)	Unauthorized request
404 (Not Found)	Resource Not Found
429 (Too Many Requests)	API usage limit exceeded
422 (Unprocessable Entity)	Invalid Data type
500 (Internal Server Error)	Service temporarily unavailable
Tipos de erros
Os possíveis tipos de erro que darão feedback mais detalhado para pedidos inválidos:

Tipos de erros relacionados à requisições
Error type	Message
UNAUTHORIZED	Invalid token.
BAD_REQUEST	Could not parse the body of the request according to the provided Content-Type.
RESOURCE_NOT_FOUND	The resource couldn't be found.
Estrutura em JSON da requisição:
Os erros de requisições enviadas via API serão exibidos na estrutura da requisição, com o nome do campo e um array contendo os detalhes do erro.

```{Json}
{
  "errors": {
    "name_field": [
      "messages"
    ]
  }
}
```

O que fazer caso estiver ocorrendo um erro na requisição
Verifique se o erro retornou uma mensagem indicando o motivo;
Verifique se a requisição está seguindo o modelo disponibilizado no recurso de "Try it" da API;
Verifique se os IDs enviados na requisição são válidos (existem na conta integrada);
Exemplos de erros
Unauthorized Request
Se o Token do usuário não for passado na Query, se o Token for inválido ou estiver desativado .

Status 401 Unauthorized

Exemplo
```{Json}
{
  "error": "Permission denied."
}
```

Resource Not Found
Se o recurso não existir no RD Station ou o Token do usuário que autoriza a consulta não tiver o nível de Visibilidade necessário para consultar essa informação ou se o ID informado na consulta for inválido.

Veja aqui sobre o nível de visibilidade do Token.

Status 404 not found

Exemplo
```{Json}
{
  "errors": {
    "error_type": "RESOURCE_NOT_FOUND",
    "error_message": "Lead not found."
  }
}
```

Internal Server Error
Se enviar um parâmetro inválido em uma requisição.

500 Internal Server Error

Exemplo
HTML

<p>Problemas técnicos são sempre inesperados, mas estamos correndo para voltar a funcionar perfeitamente. Tente de novo em alguns minutos.</p>
Inexistent fields
Quando o valor enviado no id do campo personalizado for inválido.

Status 400 Bad Request

Exemplo
```{Json}
{
  "errors": "Could not find a custom field that matches: {:custom_field_id=>\"XXXXXXXXXXXXXXXXX\"}"
}
```

Inexistent fields
Se o parâmetro "date" ao criar uma tarefa for preenchido com uma data em um período maior do que 4 anos a partir da data de criação da tarefa.

Status 422 Unprocessable Entity

Exemplo
```{Json}
{
  "errors": {
    "date": [
      "Não é válido."
    ]
  }
}
```

Invalid Parameter
Se plano Free tentar criar Tarefas que não sejam type: "task".

Status 422 Unprocessable Entity

Exemplo
```{Json}
{
  "errors": [
    {
      "error_type": "ACCESS_DENIED",
      "error_MESSAGE": "This account is not allowed to create tasks of the requested type",
      "feature": "extended_task_types",
      "access": "false"
    }
  ]
}
```

Invalid Parameter
Se ao tentar criar Tarefas, enviar um parâmetro inválido no campo type.

Status 422 Unprocessable Entity

Exemplo
```{Json}
{
  "errors": {
    "type": [
      "Não está incluído na lista."
    ]
  }
}
```

Invalid data type
Se um tipo de dado inválido for enviado.

Status 422 Unprocessable Entity

Exemplo
```{Json}
{
  "errors": {
    "name": [
      {
        "error_type": "MUST_BE_STRING",
        "error_message": "Name must be string."
      }
    ]
  }
}
```

Required Parameter
Ao criar uma Tarefa sem o parâmetro obrigatório "subject".

422 Unprocessable Entity

Exemplo
```{Json}
{
  "errors": {
    "subject": [
      "Assunto está muito curto, use no mínimo 3 caracteres."
    ]
  }
}
```

Rate Limit Exceeded
Ao ultrapassar o limite de requisições da API.

Status 429 Too Many Requests

Exemplo
```{Json}
{
  "errors": {
    "error_type": "RATE_LIMIT_EXCEDDED",
    "error_message": "API usage limit exceeded"
  }
}
```

Forbidden
Ao utilizar o Token de um usuário que não tem autorização para acessar uma funcionalidade da API.

Status 403 Forbidden

Exemplo
```{Json}
{
  "error": "forbidden"
}
```

Updated 2 days ago