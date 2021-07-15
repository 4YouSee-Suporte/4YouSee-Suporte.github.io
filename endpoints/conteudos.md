---
sort: 3
---

# Conteúdos

O processo de adicionar um conteúdo na conta consiste em carregar o arquivo e logo estabelecer os parámetros que terá esse conteúdo na biblioteca de conteúdos.

## Carregar Arquivo

Fazer o upload do arquivo (.html, .zip .mp3, .mp4, .png, .jpg) na conta. Esses conteúdos serão carregados mas não adicionados na biblioteca de conteúdos.

### GET

Obter a lista dos conteúdos carregados na conta disponíves a serem adicionados na biblioteca de conteúdos.

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

Carregar o conteúdo na conta para que fique disponível para ser adicionado na biblioteca posteriormente.

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
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
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
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
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

`{"message":"File type not allowed. Check the documentation for this resource for more information"}`

`{"message":"An unexpected error occurred","detail":"no decode delegate for this image format ' @ error\/constitute.c\/ReadImage\/504"}`

Certificar-se de que está sendo enviado no header o `'Content-Type': 'application/x-www-form-urlencoded',`

### DEL

Exclui um conteúdo carregado que ainda não foi configurado como um conteúdo da Biblioteca.

endpoint: `https://api.4yousee.com.br/v1/uploads/{uploadId}`

```tip
Para deletar um conteúdo existente da biblioteca você precisa consultar o [Deletar arquivo da Biblioteca](https://4yousee-suporte.github.io/endpoints/conteudos.html#del-1)
```
É enviado o id recebido na [resposta](https://4yousee-suporte.github.io/endpoints/conteudos.html#carregando-um-video) ao fazer o post de carregar a media.

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

## Biblioteca de Conteúdos

A biblioteca de conteúdos são aqueles conteúdos que se encontram na plataforma com um id e ao menos uma categoria associado a ele.

### GET

Retorna a lista de todas as medias existentes na biblioteca de conteúdos.

endpoint: `https://api.4yousee.com.br/v1/medias/`

Os parámetros possíveis para adicionar dentro do payload são:

- `id` (Integer, opcional) - Id da(s) mídia(s).
- `name` (String, opcional) - Nome completo o parte dele.
- `categoryId` (Integer, opcional) - Id da(s) categoría(s).
- `metadata` (Boolean, opcional) - Definido como `true` para obter os metadados de mídia (pôster, miniatura, meta-descrição)

 Esses parámetros são explicados na seção de [Filtrando Conteúdos](https://4yousee-suporte.github.io/exemplos/conteudos.html#filtrando-conte%C3%BAdos)
 
```python
import requests
import json

url = "https://api.4yousee.com.br/v1/medias"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

### POST

Cria uma nova mídia, conseguindo adicionar esse arquivo carregado anteriormente para a biblioteca de conteúdos.

endpoint: `https://api.4yousee.com.br/v1/medias/`

```tip
Para criar uma nova mídia é necessário ter carregado o arquivo através do [POST de Upload](https://4yousee-suporte.github.io/endpoints/conteudos.html#post)
```

Os parámetros para adicionar dentro do payload são:

- `name` (String, obrigatório)
- `file` (Object, obrigatório) - [Objeto](https://4yousee-suporte.github.io/endpoints/conteudos.html#resposta-ao-carregar-um-video) respondido ao carregar o arquivo.
- `duration` (Number, obrigatório) - duração da Mídia, usado só para arquivos .html ou imagens.
- `categories` (Array de inteiros, obrigatório) - Lista de id de categorías ao qual vai ser associada a mídia.
- `schedule` (Object, opcional) - Informação de agendamento.

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/medias"

payload = json.dumps({
  "name": "4YouSee Sample Media",
  "file": {
    "id": "8e8034bca7517716bca6a0350eea8294",
    "filename": "i_7.mp4"
  },
  "duration": 25,
  "categories": [1, 24],
  "schedule": {
    "startDate": "2019-01-01",
    "endDate": "2019-12-31",
    "times": [
      {
        "startTime": "08:00",
        "endTime": "11:00",
        "weekDays": [1, 2, 3, 4, 5]
      }
    ]
  }
})
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

#### Resposta de Conteúdo Adicionado na Biblioteca

```python
{
  "id": 5,
  "name": "4YouSee Sample Media",
  "file": "http://4usee.com/apidemo-D9F7FB/apidemo/common/videos/i_5.mp4",
  "duration": 25,
  "schedule": {
    "startDate": "2019-01-01",
    "endDate": "2019-12-31",
    "times": [
      {
        "startTime": "08:00",
        "endTime": "11:00",
        "weekDays": [ 1, 2, 3, 4, 5 ]
      }
    ]
  },
  "categories": [1, 24]
}
```


### Conteúdos Individuais

#### GET

O seguinte exemplo vai trazer as informações do contéudo de id 5.

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/medias/5"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

#### DEL

O seguinte exemplo vai eliminar o conteúdo de id 5.

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`

```warning
esta operação, uma vez realizada, não pode ser desfeita.
```

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/medias/5"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

### PUT

Altera as propriedades de uma mídia existente na biblioteca de conteúdos.

endpoint: `https://api.4yousee.com.br/v1/medias/{{mediaId}}`

Os parámetros para adicionar dentro do payload são:

- `name` (String, obrigatório)
- `file` (Object, obrigatório) - Use apenas para atualização do arquivo. Para atualizar o arquivo de mídia, você precisa primeiro criar um recurso de upload.
- `duration` (Number, obrigatório) - duração da Mídia, usado só para arquivos .html ou imagens.
- `categories` (Array de inteiros, obrigatório) - Lista de id de categorías ao qual vai ser associada a mídia.
- `schedule` (Object, opcional) - Informação de agendamento.

O seguinte exemplo vai alterar as propriedades do conteúdo de id 5.

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/medias/5"

payload = json.dumps({
  "name": "Sample Media Renamed"
})
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("PUT", url, headers=headers, data=payload)

print(response.text)
```

#### Resposta ao Alterar um Conteúdo

```python
{
  "id": 5,
  "name": "Sample Media Renamed",
  "file": "http://4usee.com/apidemo-D9F7FB/apidemo/common/videos/i_5.mp4",
  "duration": 25,
  "schedule": {
    "startDate": "2019-01-01",
    "endDate": "2019-12-31",
    "times": [
      {
        "startTime": "08:00",
        "endTime": "11:00",
        "weekDays": [1, 2, 3, 4, 5]
      }
    ]
  },
  "categories": [1, 24]
}
```

