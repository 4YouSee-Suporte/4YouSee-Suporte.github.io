---
sort: 1
---

# Users

Obter a lista dos usuários registrados na conta.

```
import requests

url = "https://api.4yousee.com.br/v1/users"

payload={}
headers = {
  'Secret-Token': '{{ Secret-Token }}'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
