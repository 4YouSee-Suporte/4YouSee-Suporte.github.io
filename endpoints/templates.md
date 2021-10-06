---
sort: 7
---

# Templates

Os templates são os os elementos responsáveis pelo desenho onde as notícias vão ser exibidas.

## GET

Obtem a lista de todos os templates registrados na conta.

endpoint: `https://api.4yousee.com.br/v1/templates`

Atributos do Payload

`id`: Um ou mais IDs de template separados por vírgulas. Exemplo: 1,2,3

`name`: Nome do template para pesquisar. Exemplo: finance

`type`: Tipo de template para pesquisar (zip ou swf). Exemplo: zip

```python
import requests

url = "https://api.4yousee.com.br/v1/templates"
# url = "https://api.4yousee.com.br/v1/templates?id&name=Horizontal&type=zip&sort=-name,id&page=1&limit=10"  # Filtrando 

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta com todos os templates

```json
{
  "results": [
    {
      "id": 21,
      "name": "Terra Últimas Notícias Horizontal HTML5",
      "width": 1280,
      "height": 720,
      "type": "zip"
    },
    {
      "id": 22,
      "name": "Clima Tempo Nuvens Horizontal HTML5",
      "width": 1280,
      "height": 720,
      "type": "zip"
    },
    {
      "id": 24,
      "name": "Mega Sena Horizontal HTML5",
      "width": 1280,
      "height": 800,
      "type": "zip"
    },
    {
      "id": 25,
      "name": "Quina Horizontal HTML5",
      "width": 1280,
      "height": 800,
      "type": "zip"
    },
    {
      "id": 26,
      "name": "Dupla Sena Horizontal HTML5",
      "width": 1280,
      "height": 800,
      "type": "zip"
    },
    {
      "id": 27,
      "name": "Loto Fácil Horizontal HTML5",
      "width": 1280,
      "height": 800,
      "type": "zip"
    },
    {
      "id": 28,
      "name": "Loto Mania Horizontal HTML5",
      "width": 1280,
      "height": 800,
      "type": "zip"
    },
    {
      "id": 32,
      "name": "Barra G1 Horizontal HTML5",
      "width": 1280,
      "height": 100,
      "type": "zip"
    },
    {
      "id": 35,
      "name": "Barra Logo Horizontal HTML5",
      "width": 402,
      "height": 100,
      "type": "zip"
    },
    {
      "id": 39,
      "name": "Facebook Horizontal HTML5",
      "width": 1280,
      "height": 720,
      "type": "zip"
    }
  ],
  "total": 24,
  "currentPage": 1,
  "totalPages": 3
}
```
