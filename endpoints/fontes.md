---
sort: 8
---

# Fontes

As Fontes RSS estabelecem a forma como a informação chega no sistema.

Atributos do Payload

`id`: Uma ou mais IDs de fontes de notícias separados por vírgulas. Exemplo: `1,2,3`

`name` : Nome da fonte de notícias a pesquisar. Exemplo: `clima`

`template` : Id do template para pesquisar. Exemplo: `4`

`insertContentAutomatically` : `1` se pesquisar apenas inserção automática de conteúdo ou `0` para manual. Exemplos: `1`

## GET

Obtem a lista de todas as fontes rss registradas na conta.

endpoint: `https://api.4yousee.com.br/v1/newsources`

```python
import requests

url = "https://api.4yousee.com.br/v1/newsources"
# url = "https://api.4yousee.com.br/v1/newsources?id=&name&template=&insertContentAutomatically="  # Filtrando


payload={}
headers = {
  'Secret-Token': '2848d026950a961c15b3518901a54741'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

[Resposta para visualizar todas as fontes](https://gist.github.com/Alfareiza/de188db307c1f745c71bdcdd453ff35a)
