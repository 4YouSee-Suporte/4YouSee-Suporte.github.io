---
sort: 3
---

# Conteúdos

O processo de adicionar um conteúdo na conta consiste em carregar o arquivo e logo estabelecer os parámetros que terá esse conteúdo na biblioteca de conteúdos.

# Carregar Arquivo

Fazer o upload do arquivo (.html, .zip .mp3, .mp4, .png, .jpg) na conta. Esses conteúdos serão carregados mas não adicionados na biblioteca de conteúdos.

## GET

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

## POST

Carregar o conteúdo na conta para que fique disponível para ser adicionado.
endpoint: `https://api.4yousee.com.br/v1/uploads/{uploadId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/uploads/00fa6bba3bb250012278ae03754ad1bb"

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

## DEL

Exclui um conteúdo carregado que ainda não foi configurado como um conteúdo da Biblioteca.
endpoint: `https://api.4yousee.com.br/v1/uploads/{uploadId}`

```tip
Para deletar um conteúdo existente da biblioteca você precisa consultar o 
```

```python
import requests

url = "https://api.4yousee.com.br/v1/uploads/00fa6bba3bb250012278ae03754ad1bb"

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

# Biblioteca de Conteúdos

A biblioteca de conteúdos são aqueles conteúdos que se encontram na plataforma com um id e ao menos uma categoria associado a ele.

## GET

## POST

## Conteúdos Individuais

### GET

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`

### POST

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`

### DEL
endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`
