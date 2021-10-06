---
sort: 6
---

# Playlists

As playlists possuim a programação e ordem em que os conteúdos vão ser exibidos no 4YouSee Player.

## GET

Obtem a lista de todas as playlists

endpoint: `https://api.4yousee.com.br/v1/playlists`

```python
import requests

url = "https://api.4yousee.com.br/v1/playlists"

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

[Resposta com todas as playlists](https://gist.github.com/Alfareiza/7452c81a54fb6c6048f0c1374fcf0786#gistcomment-3918561)

## POST

Cria uma nova playlist

endpoint: `https://api.4yousee.com.br/v1/playlists`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/playlists"

payload = json.dumps({
  "name": "Playlist Created via API",
  "isSubPlaylist": False,
  "category": None,
  "items": [
    {
      "type": "layout",
      "id": 1
    },
    {
      "type": "videowall",
      "abortIfError": False,
      "ignoreLayout": False,
      "grid": [
        [
          {
            "type": "media",
            "id": 4
          },
          {
            "type": "media",
            "id": 1
          }
        ],
        [
          {
            "type": "media",
            "id": 2
          },
          {
            "type": "media",
            "id": 4
          }
        ]
      ]
    },
    {
      "type": "media",
      "id": 5
    },
    {
      "type": "news"
    }
  ],
  "sequence": [
    0,
    1,
    2,
    3
  ]
})
headers = {
  'Content-Type': 'application/json',
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

## Playlists Individuais

### GET

Obtem o detalhe de uma playlist

endpoint: `https://api.4yousee.com.br/v1/playlists/{playlistId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/playlists/2"

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta para visualizar uma playlist

```json
{
    "id": 1,
    "name": "Contenido Vertical",
    "durationInSeconds": 246,
    "isSubPlaylist": false,
    "category": null,
    "items": [
        {
            "type": "media",
            "id": 66,
            "name": "gran impacto digimedios vertical 30s",
            "file": "i_66.mp4",
            "durationInSeconds": 30,
            "categories": [
                {
                    "id": 2,
                    "name": "Contenidos Verticales"
                }
            ]
        },
        {
            "type": "carousel",
            "id": 9,
            "name": "Festival Perro Caliente",
            "items": []
        },
        {
            "type": "media",
            "id": 80,
            "name": "imagen_oficial_evento_festival_del_perro_caliente",
            "file": "i_80.png",
            "durationInSeconds": 15,
            "categories": [
                {
                    "id": 2,
                    "name": "Contenidos Verticales"
                }
            ]
        },
        {
            "type": "media",
            "id": 69,
            "name": "contenido actualizado colors digimedios vertical 30s",
            "file": "i_69.mp4",
            "durationInSeconds": 30,
            "categories": [
                {
                    "id": 2,
                    "name": "Contenidos Verticales"
                }
            ]
        },
        {
            "type": "media",
            "id": 99,
            "name": "Noticia museo del carnaval",
            "file": "i_99.mp4",
            "durationInSeconds": 15,
            "categories": [
                {
                    "id": 2,
                    "name": "Contenidos Verticales"
                }
            ]
        },
        {
            "type": "media",
            "id": 100,
            "name": "nueva_plaza_de_la_paz",
            "file": "i_100.mp4",
            "durationInSeconds": 22,
            "categories": [
                {
                    "id": 2,
                    "name": "Contenidos Verticales"
                }
            ],
            "contentSchedule": {
                "endDate": "2019-12-30"
            }
        },
        {
            "type": "media",
            "id": 102,
            "name": "Último día perro caliente",
            "file": "i_102.mp4",
            "durationInSeconds": 10,
            "categories": [
                {
                    "id": 2,
                    "name": "Contenidos Verticales"
                }
            ],
            "contentSchedule": {
                "endDate": "2019-12-22"
            }
        },
        {
            "type": "media",
            "id": 101,
            "name": "puente pumarejo",
            "file": "i_101.mp4",
            "durationInSeconds": 31,
            "categories": [
                {
                    "id": 2,
                    "name": "Contenidos Verticales"
                }
            ]
        }
    ],
    "sequence": [
        0,
        1,
        2,
        3,
        4,
        5,
        3,
        6,
        7,
        0,
        2
    ]
}
```

### PUT

Altera uma playlist existente.

endpoint: `https://api.4yousee.com.br/v1/playlists/{playlistId}`

```python
import requests
import json

url = "https://api.4yousee.com.br/v1/playlists/38"

payload = json.dumps({
  "name": "Playlist Created via API",
  "isSubPlaylist": False,
  "category": None,
  "items": [
    {
      "type": "videowall",
      "abortIfError": False,
      "ignoreLayout": False,
      "grid": [
        [
          {
            "type": "media",
            "id": 4
          },
          {
            "type": "media",
            "id": 1
          }
        ],
        [
          {
            "type": "media",
            "id": 2
          },
          {
            "type": "media",
            "id": 4
          }
        ]
      ]
    },
    {
      "type": "media",
      "id": 5
    }
  ],
  "sequence": [
    0,
    1
  ]
})
headers = {
  'Content-Type': 'application/json',
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("PUT", url, headers=headers, data=payload)

print(response.text)
```

Resposta ao alterar uma playlist

```json
{
  "id": 38,
  "name": "Playlist Created via API",
  "durationInSeconds": 36,
  "isSubPlaylist": false,
  "category": null,
  "items": [
    {
      "type": "videoWall",
      "abortIfError": false,
      "ignoreLayout": false,
      "grid": [
        [
          {
            "id": 4,
            "name": "4YouSee Analyse",
            "file": "i_4.mp4",
            "durationInSeconds": 10,
            "contentSchedule": {
              "startDate": "2021-02-01"
            }
          },
          {
            "id": 1,
            "name": "4YouSee Play",
            "file": "i_1.mp4",
            "durationInSeconds": 10,
            "contentSchedule": {
              "times": [
                {
                  "startTime": "11:00",
                  "endTime": "19:00",
                  "weekDays": [
                    0,
                    1,
                    2,
                    3,
                    4,
                    5,
                    6
                  ]
                }
              ]
            }
          }
        ],
        [
          {
            "id": 2,
            "name": "4YouSee Manage",
            "file": "i_2.mp4",
            "durationInSeconds": 10,
            "contentSchedule": {
              "startDate": "2021-02-02",
              "endDate": "2021-06-05",
              "times": [
                {
                  "startTime": "05:00",
                  "endTime": "21:00",
                  "weekDays": [
                    0,
                    2,
                    3,
                    4,
                    6
                  ]
                }
              ]
            }
          },
          {
            "id": 4,
            "name": "4YouSee Analyse",
            "file": "i_4.mp4",
            "durationInSeconds": 10,
            "contentSchedule": {
              "startDate": "2021-02-01"
            }
          }
        ]
      ]
    },
    {
      "type": "media",
      "id": 5,
      "name": "Walking",
      "file": "i_5.mp4",
      "durationInSeconds": 26,
      "contentSchedule": {
        "times": [
          {
            "startTime": "00:00",
            "endTime": "23:59",
            "weekDays": [
              0,
              2,
              4,
              6
            ]
          }
        ]
      }
    }
  ],
  "sequence": [
    0,
    1
  ]
}
```

### DEL

Exclui uma playlist.

endpoint: `https://api.4yousee.com.br/v1/playlists/{playlistId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/playlists/{{playlistId}}"

payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("DELETE", url, headers=headers, data=payload)

print(response.text)
```

Resposta ao deletar uma playlist

O `status_code` da exclusão realizada com sucesso é `204`
