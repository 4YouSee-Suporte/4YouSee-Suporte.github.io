---
sort: 3
---

# Players

Os players são os elementos responsáveis por definir o que vai ser estabelecido no 4yousee player.

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

endpoint: `https://api.4yousee.com.br/v1/players

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

endpoint: `https://api.4yousee.com.br/v1/players

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

endpoint: `https://api.4yousee.com.br/v1/players/{{playerId}}`

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

endpoint: `https://api.4yousee.com.br/v1/players/{{playerId}}`

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

