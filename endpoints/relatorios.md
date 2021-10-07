---
sort: 10
---

# Relatórios

Os relatórios são a prova que os conteúdos foram exibidos com sucesso nos players. Recursos para criar, listar e recuperar relatórios do 4YouSee Manager. 

## GET

Obtem todos los relatórios gerados ou em processo de geração.

endpoint: `https://api.4yousee.com.br/v1/reports`

```python
import requests

url = "https://api.4yousee.com.br/v1/reports"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

[Resposta para visualizar todos os relatórios](https://gist.github.com/Alfareiza/7735d87967b6a4ade533e6da5e23f4a2)


## POST

Solicita a geração de um relatório para download posterior como um arquivo csv, conforme exemplificado em uma seção a seguir. 

```tip
O intervalo máximo para gerar um relatório é de 30 dias.
```

O atributo webhook é opcional e pode ser utilizado para fornecer um url onde você pode receber uma notificação contendo o link onde o relatório gerado está disponível para download. O arquivo contem um json por playlog.

endpoint: `https://api.4yousee.com.br/v1/reports`

```python
import requests

url = "https://api.4yousee.com.br/v1/reports"

payload = json.dumps({
  "type": "detailed",
  "webhook": "http://7593822c1d06.ngrok.io/",
  "filter": {
              "startDate": "2020-07-26",
              "startTime": "00:00:00",
              "endDate": "2020-07-26",
              "endTime": "00:00:00",
              "mediaId": [],
              "playerId": [],
              "sort" : -1
              }
  })
headers = {
  'Secret-Token': 'a1be7c9dced06d34e7a6d061924ea99d'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Ao receber este objeto, a url do seu webhook deve enviar uma resposta 200 (OK), para garantir que você não receberá a mesma notificação novamente.

Caso haja algum erro durante o processo de geração do relatório, você obterá o seguinte objeto json:

```json
{
  "id": 234,
  "status": "failed",
  "error": {
      "code": 422,
      "message": "There was an error generating the report"
  },
  "filter": {
      "startDate": "2020-09-01",
      "startTime": "00:00:00",
      "endDate": "2020-09-18",
      "endTime": "23:59:59",
      "mediaId": [],
      "playerId": [],
      "sort": -1
  }
}
```

Por último, se por algum motivo a notificação de geração de relatório não for enviada, ela será repetida mais 3 vezes: a segunda tentativa acontece 2 minutos após a primeira, a próxima acontece 6 minutos após a segunda e, finalmente, a última tentativa leva lugar 18 minutos após a terceira tentativa. Se a última tentativa não for bem-sucedida, não haverá outra tentativa de notificação. Nesse cenário, é aconselhável usar o endpoint GET `/reports/reportId` com o id do seu relatório para recuperar a url no qual ele está disponível para download. Outro método que você pode usar é fazer login em sua conta 4YouSee Manager e ir para a lista de relatórios gerados (/admin/reports_api.php), onde seu relatório deve ser listado, se gerado com sucesso.

## Relatórios Individuais

### GET

Obtem o detalhe de um relatório que pode ter sido gerado ou pode estar em processo de geração.

endpoint: `https://api.4yousee.com.br/v1/reports/{reportId}`

```python
import requests

url = "https://api.4yousee.com.br/v1/reports/336"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Resposta para visualizar um relatório

```json
{
  "id": 336,
  "type": "detailed",
  "format": "json",
  "filter": {
    "startDate": "2020-08-01",
    "startTime": "00:00:01",
    "endDate": "2020-08-09",
    "endTime": "23:59:59",
    "mediaId": [],
    "playerId": [],
    "sort": 1
  },
  "status": "success",
  "url": "https://4yousee-playlogs-reports.s3.amazonaws.com/qa/336-5f5962da8e150.gz",
  "createdAt": "2020-09-09T23:18:45+00:00",
  "updatedAt": "2020-09-09T23:18:45+00:00"
}
```
