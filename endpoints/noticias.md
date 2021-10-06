---
sort: 9
---

# Noticias

As notícias são o resultado da obtenção de informações externas a través de xml's, api's, etc.

Parámetros

`newsourceId` : Um ou mais IDs de fontes de notícias separados por vírgulas. Exemplo: `34`

`startDate` : Data de início das notícias. Exemplo `01-03-2017`

`endDate` : Data de término da notícia. Exemplo: `22-03-2019`

`content` : Conteúdo da notícia a pesquisar. Exemplo de `{"produto": "Suco"}`

`status` : Status da notícia. Os valores possíveis são: `approved`, `disapproved`, `waiting`. Exemplos: `waiting`

## GET

Obtem a lista de todas as noticias de todas as fontes rss registradas na conta.

endpoint: `https://api.4yousee.com.br/v1/news`

```python
import requests

url = "https://api.4yousee.com.br/v1/news"
# url = "https://api.4yousee.com.br/v1/news?newsourceId=34&startDate=2019-05-27"  # Filtrando

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

[Resposta com as noticias](https://gist.github.com/Alfareiza/e65f843e7178b6f673f221b74f00cd9a)

## POST

Cria uma notícia. Se você deseja criar notícias que usem imagem, antes disso você precisa criar um recurso de [Upload](https://4yousee-suporte.github.io/endpoints/conteudos.html#carregando-uma-imagem) de uma imagem.

endpoint: `https://api.4yousee.com.br/v1/news`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/news"

payload = json.dumps({
  "content": {
    "product": "Apple Juice",
    "description": "Apple Juice",
    "price": "2.50"
  },
  "startDate": "2017-03-01 09:00:00",
  "endDate": "2017-03-31 13:00:00",
  "newsourceId": 50,
  "file": {
    "id": "6480992b330223e231722f00e7e01b6b",
    "filename": "647600.jpeg"
  }
})
headers = {
  'Content-Type': 'application/json',
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Resposta ao criar uma notícia

```json
{
  "id": 479,
  "content": {
    "product": "Apple Juice",
    "description": "Apple Juice",
    "price": "2.50"
  },
  "creationDate": "2019-06-06 12:58:55",
  "status": "approved",
  "approvalDate": "2019-06-06 12:58:55",
  "startDate": "2017-03-01 09:00:00",
  "endDate": "2017-03-31 13:00:00",
  "newsourceId": 50,
  "newsourceName": "Product Sales",
  "image": "http://4usee.com/apidemo-D9F7FB/apidemo/common/imgnews/479.jpeg"
}
```

## Notícias Individuais

### GET 

Obtem o detalhe de uma notícia.

endpoint: `https://api.4yousee.com.br/v1/news/{newsId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/news/479"

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta para visualizar uma notícia

```json
{
  "approvalDate": "2019-06-06 12:58:55",
  "content": {
    "product": "Apple Juice",
    "description": "Apple Juice",
    "price": "2.50"
  },
  "creationDate": "2019-06-06 12:58:55",
  "startDate": "2017-03-01 09:00:00",
  "endDate": "2017-03-31 13:00:00",
  "status": "approved",
  "image": "http://4usee.com/apidemo-D9F7FB/apidemo/common/imgnews/479.jpeg",
  "id": 479,
  "newsourceId": 50,
  "newsourceName": "Product Sales",
  "hash": "45d06860dcc0382ef0b0eca86afa1fcc100d176a"
}
```

### PUT

Altera uma notícia.

endpoint: `https://api.4yousee.com.br/v1/news/{newsId}`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/news/479"

payload = json.dumps({
  "status": "approved",
  "content": {
    "product": "Orange Juice",
    "description": "Orange Juice",
    "price": "3.50"
  },
  "startDate": "2017-03-01 09:00:00",
  "endDate": "2017-03-31 13:00:00"
})
headers = {
  'Content-Type': 'application/json',
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("PUT", url, headers=headers, data=payload)

print(response.text)
```

Resposta ao alerar uma notícia

```json
{
  "id": 479,
  "content": {
    "product": "Orange Juice",
    "description": "Orange Juice",
    "price": "3.50"
  },
  "creationDate": "2019-06-06 12:58:55",
  "status": "approved",
  "approvalDate": "2019-06-06 12:58:55",
  "startDate": "2017-03-01 09:00:00",
  "endDate": "2017-03-31 13:00:00",
  "newsourceId": 50,
  "newsourceName": "Product Sales",
  "image": "http://4usee.com/apidemo-D9F7FB/apidemo/common/imgnews/479.jpeg"
}
```

### DEL

Exclui uma notícia.

endpoint: `https://api.4yousee.com.br/v1/news/{newsId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/news/{{newsId}}"

payload = ""
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741',
  'Content-Type': 'application/x-www-form-urlencoded'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

Resposta ao excluir uma notícia

O `status_code` da exclusão realizada com sucesso é `204`
