---
sort: 4
---

# Categorias

As categorias são "pastas" que armazenam conteúdos dentro delas. Dessa forma facilita a organização de mídias no 4yousee manager.

## GET

Obtem todas as categorias registradas na conta.

endpoint: `https://api.4yousee.com.br/v1/medias/categories/`

```python
import requests

url = "https://api.4yousee.com.br/v1/medias/categories"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

[Resposta para ver todas as categorias da conta.](https://gist.github.com/Alfareiza/81849492b4c0169faeb930d4c5422ffe#gistcomment-3917521)

## POST

Cria uma nova categoria. É possível criar uma categoria de primeiro nível ou uma subcategoria

endpoint: `https://api.4yousee.com.br/v1/medias/categories/`

Atributos do Payload
- `name` (String, obrigatório) Nome de exibição da categoria/subcategoria
- `description` (String) - Descrição detalhada da categoria
- `parent` (Number) - Quando informado cria uma subcategoria

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/medias/categories/"

payload = json.dumps({
  "name": "Marketing",
  "description": "Content related to market of company",
  "parent": 24
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

## Categorias Individuais

### GET

Obtem o detalhe de uma categoría.

endpoint: `https://api.4yousee.com.br/v1/medias/categories/{{mediaCategoryId}}`

```python
import requests

url = "https://api.4yousee.com.br/v1/medias/categories/24"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta para visualizar uma categoría

```json
{
    "id": 1,
    "name": "DEMO",
    "description": "",
    "parent": null,
    "children": [],
    "autoShuffle": false,
    "updateFlow": "1"
}
```

Se a categoría não existe, a resposta com `status_code` igual a `404` será a seguinte:

```json
{
    "message": "Category with ID 120 was not found"
}
```

### PUT

Atualiza uma categoría. É possível atualizar o nome, a descrição, o pai da categoria, updateflow, sequence e autoShuffle.

endpoint: `https://api.4yousee.com.br/v1/medias/categories/{{mediaCategoryId}}`

Atributos do Payload
- `name` (String, opcional) Nome de exibição da categoria.
- `description` (String, opcional) - Descrição detalhada da categoria.
- `parent` (Número ou null, opcional) - Quando é enviado, converte a categoria em subcategoria da categoria pai informado. Se o valor for **null**, ele converte a subcategoria em uma categoria de primeiro nível.
- `updateflow` (Número, opcional) - 1: para reiniciar o carrossel após a atualização do carrossel; 2: Não reinicie após a atualização do carrossel.
- `sequence` (Lista, opcional) - Lista (Array) que contém os IDs de mídia na ordem em que deseja que apareçam no carrossel.
- `autoShuffle` (booleano, opcional) - Defina o valor de uma opção que embaralha seu carrossel toda vez que termina sua execução.

```python
import requests

url = "https://api.4yousee.com.br/v1/medias/categories/1"

payload = json.dumps({
  "name": "Sample Category Renamed",
  "description": "",
  "parent": null,
})
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
}

response = requests.request("PUT", url, headers=headers, data=payload)

print(response.text)
```
