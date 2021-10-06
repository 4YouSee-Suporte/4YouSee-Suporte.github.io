---
sort: 2
---

# Users Groups

Todo usuário deve possuir um grupo de usuário. Nele é possível estabelecer quais módulos do sistema o usuário possui acesso.

## GET

Obter a lista dos grupos de usuários registrados na conta.

endpoint: `https://api.4yousee.com.br/v1/users/groups`


```python
import requests
import json

url = "https://api.4yousee.com.br/v1/users/groups"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta para ver todos os usuários

```json
{
  "results": [
    {
      "id": 2,
      "name": "Administrator",
      "description": "Group responsible for account management"
    },
    {
      "id": 20,
      "name": "Publishers",
      "description": "Group responsible for publishing content."
    }
  ],
  "total": 2,
  "currentPage": 1,
  "totalPages": 1
}
```
