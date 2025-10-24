Mensagens de erro
Usamos códigos HTTP convencionais nas respostas para indicar o sucesso ou a falha de uma solicitação da API. Em geral, os códigos no intervalo 2xx indicam sucesso, os códigos no intervalo 4xx indicam um erro que falhou dado a informação fornecida (por exemplo, um parâmetro obrigatório foi omitido, uma falha de carga, etc.) e os códigos no intervalo 5xx indicam um erro com nossos servidores (estes são raros).



Códigos HTTP
Código	Description
400 (Bad request)	Malformed body request
401 (Unauthorized)	Unauthorized request
403 Forbidden	Forbidden request
404 (Not found)	Resource Not Found
415 (Unsupported Media Type)	Invalid Content-Type header
429 Too Many Requests	API usage limit exceeded
422 (Unprocessable Entity)	Invalid Data type
500 (Internal Server Error)	Service temporarily unavailable


Tipos de erros
Os possíveis tipos de erro que darão feedback mais detalhado para pedidos inválidos:

Tipos de erros relacionados à requisições
Error type	Message
UNAUTHORIZED	Invalid token.
BAD_REQUEST	Could not parse the body of the request according to the provided Content-Type.
UNSUPPORTED_MEDIA_TYPE	The payload is in a format not supported by this method on the target resource.
RESOURCE_NOT_FOUND	The resource couldn't be found.
Tipos de erro relacionados à validação
Error type	Message
CANNOT_BE_NULL	Cannot be null
CANNOT_BE_BLANK	Can not be blank
INVALID	It is not valid
TAKEN	Already in use
TOO_SHORT	Is too short (minimum 0 characters)
TOO_LONG	Is too long (maximum 0 characters)
EXCLUSION	Already in use
INCLUSION	It is not included in the list
MUST_BE_BOOLEAN	It must be boolean
MUST_BE_STRING	It must be string
MUST_BE_LESS_THAN_OR_EQUAL	It must less than or equal to
MUST_BE_VALID_OPTION	It must be one of the valid options
MUST_BE_STRING_ARRAY	It muast be an array of strings


Exemplo de erros
Unauthorized Request
Se o token ou as credenciais forem inválidas, ou o code estiver expirado, ou o usuário não estiver autorizado.

Status 401 Unauthorized

Exemplo
```{Json}
 {
    "errors": [
        {
          "error_type": "UNAUTHORIZED",
          "error_message": "Invalid token."
        },
        {
          "error_type": "ACCESS_DENIED",
          "error_message": "Wrong credentials provided."
        },
        {
           "error_type": "EXPIRED_CODE_GRANT",
           "error_message": "The authorization code grant has expired."
        },
        {
          "error_type": "INVALID_REFRESH_TOKEN",
          "error_message": "The provided refresh token is invalid or was revoked."
        }
    ]
}
```


Unable to load CDP Schema
Se a chave gerada para a API Key for referente a uma conta do RD Station CRM e não do RD Station Marketing.

Status 400 Bad Request

Exemplo
```{Json}
 {
    "errors": [
        {
            "error_type": "UNABLE_TO_LOAD_CDP_SCHEMA",
            "error_message": "Unable to load schema for tenant_id '575000000001107348'"
        }
    ]
}
```



Resource Not Found
Se o recurso não existir no RD Station.

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




Invalid Content-Type Header
Se o Content-Type não estiver configurado corretamente.

Status 415 Unsupported Media Type

Exemplo
```{Json}
 {
    "errors": {
        "error_type": "UNSUPPORTED_MEDIA_TYPE",
        "error_message": "The payload is in a format not supported by this method on the target resource."
    }
}
```




Malformed Body Request
Se a solicitação do corpo for mal formada de acordo com o cabeçalho Content-Type.

Status 400 Bad Request

Exemplo
```{Json}
 {
    "errors": {
        "error_type": "BAD_REQUEST",
        "error_message": "Could not parse the body of the request according to the provided Content-Type."
    }
}
```




Invalid format
Se um formato inválido para um atributo for enviado.

Status 400 Bad Request

Exemplo
```{Json}
 {
    "errors": {
        "email": [
            {
                "error_type": "CANNOT_BE_NULL",
                "error_message": "email cannot be null."
            }
        ],
           "contact_owner_email": [
      {
        "error_type": "MUST_BE_STRING",
        "error_message": "url must be string"
      }
             {
        "error_type": "MUST_BE_LESS_THAN_OR_EQUAL",
        "error_message": "url must less than or equal to 100"
      },
      {
        "error_type": "INVALID_EMAIL_FORMAT",
        "error_message": "contact_owner_email has an invalid format"
      },
      {
        "error_type": "INVALID_USER",
        "error_message": "The user {user} was not found in your account."
      }
        ],
        "linkedin": [
            {
                "error_type": "INVALID_FORMAT",
                "error_message": "linkedin must use only letters, numbers, '.', '-' and '_'"
            }
        ],
        "name" : [
          { "error_type": "CANNOT_BE_BLANK", "error_message": "Can not be blank" }
        ]
    }
}
```




Uppercase Tags
Se for enviado tags com caracteres maiúsculos.

Exemplo
```{Json}
 {
    "errors": {
        "tags": [
            {
                "error_type": "VALUES_MUST_BE_LOWERCASE",
                "error_message": "must not contain capital letters"
            }
        ]
    }
}
```




Invalid data type
Se a tag for enviada em uma string, em vez de uma array of strings.

Status 400 Bad Request

Exemplo
```{Json}
 {
    "errors": [
        {
            "error_type": "INVALID_DATA_TYPE",
            "error_message": "Must be of type 'SET'.",
            "validation_rules": {
                "data_type": "SET"
            },
            "path": "$.payload.tags"
        }
    ]
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




Read only fields
Ao tentar atualizar um atributo que é somente leitura.

Status 400 Bad Request

Exemplo
```{Json}
{
    "errors": {
        "error_type": "INVALID_FIELDS",
        "error_message": "Payload contains fields that cannot be modified: (available_for_mailing)"
    }
} 
```




Inexistent fields
Ao tentar atualizar um atributo que não existe.

Status 400 Bad Request

Exemplo
```{Json}
{
    "errors": {
        "error_type": "INVALID_FIELDS",
        "error_message": "Payload contains fields that do not exist: (attr)"
    }
}
```




Conflicting field
Ao usar o endpoint de PATCH UPSERT e um campo de Contato que identifica o Lead é usado corpo da requisição.

Status 400 Bad Request

Exemplo
```{Json}
{
    "errors": {
        "error_type": "CONFLICTING_FIELD",
        "error_message": "The payload contains an attribute that was used to identify the lead"
    }
}
```




Inclusion
Ao criar um campo personalizado "presentation_type": "MULTIPLE_CHOICE" e preencher o campo "data_type" com um valor diferente de "STRING[]".

Status 400 Bad Request

Exemplo
```{Json}
{
    "errors": {
        "data_type": [
            {
                "error_type": "INCLUSION",
                "error_message": "invalid options, the valid options are: [STRING[]]"
            }
        ]
    }
}
```




Email already in use
Ao usar o endpoint de POST para criar contato e enviar o email de Lead já existente.

Status 400 Bad Request

Exemplo
```{Json}
{
    "errors": {
        "error_type": "EMAIL_ALREADY_IN_USE",
        "error_message": "email already in use"
    }
}
```




Values must be unique
Ao usar o endpoint de POST para criar uma tag para o lead pelo uuid/email e o lead já possui a tag.

Status 400 Bad Request

Exemplo
```{Json}
{
	"errors": {
		"tags": [
			{
				"error_type": "VALUES_MUST_BE_UNIQUE",
				"error_message": "must not contain duplicate values"
			}
		]
	}
}

```

Required Parameter
Ao usar o endpoint de GET para melhor Horário para Mensagem e não enviar um parâmetro obrigatório.

Status 400 Bad Request

Exemplo
```{Json}
{
  "errors": {
    "error_type": "REQUIRED_PARAMETER",
    "error_message": "Required parameter not informed"
  }
}
```

Invalid Parameter
Ao usar o endpoint de GET para melhor Horário para Mensagem e enviar um parâmetro fora do formato esperado.

Status 400 Bad Request

Exemplo
```{Json}
{
  "errors": {
    "error_type": "INVALID_PARAMETER",
    "error_message": "Value informed in the parameter is invalid or does not match the expected format"
  }
}
```

Parameter Unknown
Ao usar o endpoint de GET para melhor Horário para Mensagem e enviar um parâmetro desconhecido ou inexperado.

Status 400 Bad Request

Exemplo
```{Json}
{
  "errors": {
    "error_type": "PARAMETER_UNKNOWN",
    "error_message": "Unknown or unexpected parameter"
  }
}
```

Date Out of Range
Ao usar o endpoint de GET para melhor Horário para Mensagem e enviar o parâmetro de message_date com uma data que excede o limite mínimo 1 dia e máximo 7 dias.

Status 400 Bad Request

Exemplo
```{Json}
{
  "errors": {
    "error_type": "DATE_OUT_OF_RANGE",
    "error_message": "Entered date range exceeds limit"
  }
}
```

Invalid Value
Ao usar o endpoint de GET para melhor Horário para Mensagem e enviar um parâmetro inválido para essa requisição.

Status 400 Bad Request

Exemplo
```{Json}
{
  "errors": {
    "error_type": "INVALID_VALUE",
    "error_message": "Parameter informed is not contained in the list of valid attributes"
  }
}
```

Account Requirement Missing
Ao usar o endpoint de GET para melhor Horário para Mensagem e a conta em questão não é Pro ou Advanced.

Status 403 Forbidden

Exemplo
```{Json}
{
  "errors": {
    "error_type": "ACCOUNT_REQUIREMENT_MISSING",
    "error_message": "The account is not part of the account group that has access to smart send."
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

Workflow Status Error
Ao usar o endpoint de POST para Inserir leads em um fluxo e o valor enviado no parâmetro id for referente a um fluxo desativado ou inexistente.

Status 400 Bad Request

Exemplo
```{Json}
{
  "errors": [
    {
      "error_type": "WORKFLOW_STATUS_ERROR",
      "error_message": "Workflow must be activated or does not exist",
      "validation_rules": {},
      "path": "$.id"
    }
  ]
}
```

Service Unavailable
Serviço indisponível temporariamente.

Status 500 Internal Server Error

Exemplo
```{Json}
{
  "errors": {
    "error_type": "SERVICE_UNAVAILABLE",
    "error_message": "Service temporarily unavailable"
  }
}
```
Updated 28 days ago