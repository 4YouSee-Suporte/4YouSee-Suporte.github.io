---
sort: 5
---

# Players

Os players são os elementos responsáveis por definir o que vai ser estabelecido no 4yousee player.

Os players possuim os seguintes parámetros:

- `playerStatus` : O playerStatus é um dos objetos retornados pelo terminal do Player. Este objeto mostra o último contato do player com o servidor. Existem seis valores padrão possíveis. O valor do campo time representa o intervalo de tempo do último contato do player em minutos. Por exemplo: O playerStatus com o nome Online e tempo 10 significa que o último contato do player foi entre 0 e 10 minutos.:

**Online**

```json
playerStatus: {
    "id": 1,
    "name": "Online",
    "time": 10
}
```

**Alert**

```json
playerStatus: {
    "id": 2,
    "name": "Alert",
    "time": 20
}
```

**Offline**

```json
playerStatus: {
    "id": 3,
    "name": "Offline",
    "time": 30
}
```

**Assistance needed**

```json
playerStatus: {
    "id": 4,
    "name": "Assistance needed",
    "time": 1440
}
```

**Local assist needed**

```json
playerStatus: {
    "id": 5,
    "name": "Local assist needed",
    "time": 9999999
}
```

**Never accessed**

```json
playerStatus: {
    "id": 6,
    "name": "Never accessed",
    "time": 0
}
```

- `playlists` : Um objeto que contém o ID da playlist associada ao player por dia da semana. A representação da semana é numérica e é feita da seguinte forma:

  - "0": Domingo
  - "1": Segunda-feira
  - "2": Terça-feira
  - "3": Quarta-feira
  - "4": Quinta-feira
  - "5": Sexta-feira
  - "6": Sábado

Por exemplo:

```json
"playlists": {
    "0": 2,
    "1": 3,
    "2": 3,
    "3": 3,
    "4": 3,
    "5": 3,
    "6": 2
}
```

- `platform` : Valor (string) que define qual plataforma o player poderá ser utilizado. Pode ser `LG`, `SAMSUNG`, `ANDROID` ou `4YOUSEE_PLAYER` (uso do player em linux ou windows)

- `lastContactInMinutes` : Valor (inteiro) que define há quantos minutos que o servidor fez contato com o player.

- `lastLogReceived` : Valor (Date) que determina quando foi a última vez que o player enviou os playlogs ao servidor.

## GET

Obtem a lista de todos os players registrados na conta.

endpoint: `https://api.4yousee.com.br/v1/players`

```python
import requests

url = "https://api.4yousee.com.br/v1/players"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

[Resposta com todos os players](https://gist.github.com/Alfareiza/01e7a5cf4dbe5fbbb3c347fc7e92c9a9#gistcomment-3918440)

## POST

Cria um novo player

endpoint: `https://api.4yousee.com.br/v1/players`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/players"

payload = json.dumps({
  "name": "Player name example",
  "description": "Player description example",
  "platform": "4YOUSEE_PLAYER",
  "group": 1,
  "playlists": {
    "0": 1,
    "1": 1,
    "2": 1,
    "3": 1,
    "4": 1,
    "5": 1,
    "6": 1
  },
  "audios": {
    "0": 1
  }
})
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
````

Resposta ao adicionar um player

```json
{
  "id": 2,
  "name": "Player Android",
  "description": "Player Android",
  "platform": "ANDROID",
  "lastContactInMinutes": null,
  "group": {
    "id": 1,
    "name": "Group DEMO"
  },
  "playerStatus": {
    "id": 6,
    "name": "Never accessed",
    "time": 0
  },
  "playlists": {
    "0": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "1": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "2": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "3": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "4": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "5": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "6": {
      "id": 3,
      "name": "Playlist Sample"
    }
  },
  "audios": {
    "0": {
      "id": 1,
      "name": "Playlist DEMO"
    }
  }
}
```

## Players Individuais

### GET

Obtem a informação em detalhe de um player.

endpoint: `https://api.4yousee.com.br/v1/players/{playerId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/players/5"

payload={}
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta para visualizar um player

```json
{
  "id": 5,
  "name": "Player API",
  "description": "Player created by API",
  "platform": "4YOUSEE_PLAYER",
  "lastContactInMinutes": null,
  "group": {
    "id": 1,
    "name": "Group DEMO"
  },
  "playerStatus": {
    "id": 6,
    "name": "Never accessed",
    "time": 0
  },
  "playlists": {
    "0": {
      "id": 1,
      "name": "Playlist DEMO"
    },
    "1": {
      "id": 1,
      "name": "Playlist DEMO"
    },
    "2": {
      "id": 1,
      "name": "Playlist DEMO"
    },
    "3": {
      "id": 1,
      "name": "Playlist DEMO"
    },
    "4": {
      "id": 1,
      "name": "Playlist DEMO"
    },
    "5": {
      "id": 1,
      "name": "Playlist DEMO"
    },
    "6": null
  },
  "audios": {
    "0": {
      "id": 1,
      "name": "Playlist DEMO"
    }
  },
  "lastLogReceived": null
}
```

### PUT

Atualiza um player

endpoint: `https://api.4yousee.com.br/v1/players/{playerId}`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/players/2"

payload = json.dumps({
  "name": "Player Android",
  "description": "Player Android",
  "group": 1,
  "platform": "ANDROID",
  "playlists": {
    "0": 3,
    "1": 3,
    "2": 3,
    "3": 3,
    "4": 3,
    "5": 3,
    "6": 3
  },
  "audios": {
    "0": 1
  }
})
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d',
  'Content-Type': 'application/json'
}

response = requests.request("PUT", url, headers=headers, data=payload)

print(response.text)
```

Resposta ao alterar um player

```json
{
  "id": 2,
  "name": "Player Android",
  "description": "Player Android",
  "platform": "ANDROID",
  "lastContactInMinutes": null,
  "group": {
    "id": 1,
    "name": "Group DEMO"
  },
  "playerStatus": {
    "id": 6,
    "name": "Never accessed",
    "time": 0
  },
  "playlists": {
    "0": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "1": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "2": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "3": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "4": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "5": {
      "id": 3,
      "name": "Playlist Sample"
    },
    "6": {
      "id": 3,
      "name": "Playlist Sample"
    }
  },
  "audios": {
    "0": {
      "id": 1,
      "name": "Playlist DEMO"
    }
  }
}
```

### DEL

Exclui um player

endpoint: `https://api.4yousee.com.br/v1/players/{playerId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/players/10"

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

Resposta ao deletar um player

O `status_code` da exclusão realizada com sucesso é `204`

