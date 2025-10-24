Obter token
get
https://crm.rdstation.com/api/v1/token/check
Obter token.

Log in to see full request history
time	status	user agent	
Make a request to see history.
0 Requests This Month

Response

200
Success

Response body
object
email
string
name
string
organization
string

Updated 2 days ago

input
```{Shell}
curl --request GET \
     --url https://crm.rdstation.com/api/v1/token/check \
     --header 'accept: application/json'
```

output
```{Json}
{
  "email": "${{email}}",
  "name": "${{name}}",
  "organization": "${{organization}}"
}
```