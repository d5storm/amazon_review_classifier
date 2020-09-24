# Amazon Review Classifier

Amazon Review Classifier é uma API que acessa um modelo de classificação de categoria de produtos
de acordo com seu nome.

# Documentação da API

Para receber a previsão de classe de uma lista de títulos (já tokenizados) basta uma chamada POST com um header X-API-KEY, onde é inserido o token de acesso, e com o body abaixo:

```json
{
    "instances": ["tokens"], (required)
    "configuration": { (optional)
        "k": (int)
    }
}
```

- A lista "instances" recebe a lista de títulos a serem classificados.

- O parâmetro "k" em "configuration" é opcional, com padrão 1, e configura o número de classes possíveis de classificação do título, ordenada por probabilidade.

### Exemplo de utilização em Python
```python
data = json.dumps(
        {
            "instances": ["harry potter cracudão"], 
            "configuration": {
                "k": 3
            }
        })
        
response = requests.post('https://achcfrolwd.execute-api.us-east-2.amazonaws.com/deploy/predict',
                         data=data,
                         headers={'X-API-KEY': <token>}
                         )
```

## Obtenção de Acesso
A API é protegida por um token de acesso. Para obtenção da chave, entrar em contato com murilobs@gmail.com.

### Autor
Murilo Brugger Stockinger, 2020
