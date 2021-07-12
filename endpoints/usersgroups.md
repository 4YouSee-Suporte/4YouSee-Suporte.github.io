---
sort: 2
---

# Users Groups

Obter a lista dos grupos de usuários registrados na conta.

```
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
