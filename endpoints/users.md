---
sort: 1
---

# Users

Um usuário é quem possui um acesso na plataforma de 4yousee manager.

## GET 

### Todos os usuários

Obter a lista dos usuários registrados na conta.

endpoint: `https://api.4yousee.com.br/v1/users`

```python
import requests

url = "https://api.4yousee.com.br/v1/users"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta com todos os usuarios

```json
{
    "results": [
        {
            "id": 2,
            "name": "alfonso",
            "username": "alfareiza",
            "email": "alf****@****.com",
            "group": {
                "id": 2,
                "name": "Administrador"
            }
        }
    ],
    "total": 1,
    "currentPage": 1,
    "totalPages": 1
}
```
