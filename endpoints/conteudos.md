---
sort: 3
---

# Conteúdos

O processo de adicionar um conteúdo na conta consiste em carregar o arquivo e logo estabelecer os parámetros que terá esse conteúdo na biblioteca de conteúdos.

## Carregar Arquivo

Fazer o upload do arquivo (.html, .zip .mp3, .mp4, .png, .jpg) na conta. Esses conteúdos serão carregados mas não adicionados na biblioteca de conteúdos.

### GET

Obter a lista dos conteúdos carregados na conta. 

endpoint: `https://api.4yousee.com.br/v1/uploads`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/uploads"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

### POST

Carregar o conteúdo na conta para que fique disponível para ser adicionado.

endpoint: `https://api.4yousee.com.br/v1/uploads/`

#### Carregando uma imagem

```python
import requests

url = "https://api.4yousee.com.br/v1/uploads"

payload={'Content-Type': 'multipart/form-data;'}
files=[
  ('media',('4yousee.png',open('/C:/Users/Alfonso/Pictures/4yousee.png','rb'),'image/png'))
]
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Secret-Token': 'ca0c685c9b24310e6d08533a73c967db'
}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)
```

#### Resposta ao carregar uma imagem

```python
{
    "id": "8e5e3ba750d619d6b827a96351ae33e9",
    "filename": "4yousee.png"
}
```

#### Carregando um video

```python
import requests

url = "https://api.4yousee.com.br/v1/uploads"

payload={'Content-Type': 'multipart/form-data;'}
files=[
  ('media',('4YouSee Colors.mp4',open('/C:/Users/Alfonso/Videos/4YouSee Colors.mp4','rb'),'application/octet-stream'))
]
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Secret-Token': 'ca0c685c9b24310e6d08533a73c967db'
}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)

```

#### Resposta ao carregar um video

```python
{
    "id": "0e8c712c92dfba83d5614b0fc1cdb8b1",
    "filename": "4YouSee Colors.mp4"
}
```

#### Erros

`{"message":"Upload file is empty. Check the documentation for this resource for more information"}`

Voce deve verificar a rota do arquivo.


### DEL

Exclui um conteúdo carregado que ainda não foi configurado como um conteúdo da Biblioteca.

endpoint: `https://api.4yousee.com.br/v1/uploads/{uploadId}`

```tip
Para deletar um conteúdo existente da biblioteca você precisa consultar o [Deletar arquivo da Biblioteca](https://4yousee-suporte.github.io/endpoints/conteudos.html#del-1)
```

```python
import requests

url = "https://api.4yousee.com.br/v1/uploads/00fa6bba3bb250012278ae03754ad1bb"  # Esse id é o recebido na resposta ao fazer o post de carregar a media.

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

## Biblioteca de Conteúdos

A biblioteca de conteúdos são aqueles conteúdos que se encontram na plataforma com um id e ao menos uma categoria associado a ele.

### GET

### POST

### Conteúdos Individuais

#### GET

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`

#### POST

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`

#### DEL

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`
