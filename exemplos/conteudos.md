# Conteúdos


## Filtrando conteúdos
Para filtrar conteúdos é possível enviar os seguintes valores dentro do payload :
- id (Integer, optional)
- name (String, optional) - Full or part name
- categoryId (Integer, optional) - ID media category
- metadata (Boolean, optional) - set to true to retrieve media metadata (poster, thumbnail, meta-description)

Resposta sem resultado: `{"results":[],"total":0,"currentPage":1,"totalPages":0}`

### Alfabéticamente

Por padrão o resultado virá ordenado por id de forma ascendente, porém é possível trocar essa ordem.

```python
import requests
url = "https://api.4yousee.com.br/v1/medias"

payload = {'sort': 'name'} 

headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}
response = requests.request("GET", url, headers=headers, params=payload)
print(response.text)
```



### Por Id(s)

```python
import requests
url = "https://api.4yousee.com.br/v1/medias"

payload = {'id': '15'}  # Caso queira filtrar por 2 id's.
# payload = {'categoryId': '2, 26'}  # Caso queira filtrar por 2 id's.

headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}
response = requests.request("GET", url, headers=headers, params=payload)
print(response.text)
```

### Por Nome

É possível fazer a consulta com um nome o parte de um nome.

```python
import requests
url = "https://api.4yousee.com.br/v1/medias"

payload = {'name': 'erro'}

headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}
response = requests.request("GET", url, headers=headers, params=payload)
print(response.text)
```

### Por Categoria(s)

É possível fazer a consulta com um ou multiplas id de categorias.

```python
import requests
url = "https://api.4yousee.com.br/v1/medias"

payload = {'categoryId': '26'}  # Caso queira filtrar por 1 categoria.
# payload = {'categoryId': '2, 26'}  # Caso queira filtrar por 2 categorias.

headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}
response = requests.request("GET", url, headers=headers, params=payload)
print(response.text)
```

### Por Tipo

## Adicionando multiplos conteúdos

## Alterando multiplos conteúdos

## Excluindo multiplos conteúdos

