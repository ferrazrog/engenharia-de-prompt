---
share: "true"
---
---
# Regras Práticas e Exemplos

---
## Separe as instruções
Coloque instruções no início do prompt e use """ para separar a instrução e o contexto

**Menos eficaz ❌:**
``` text
Resuma o texto abaixo em uma lista de tópicos com os pontos mais importantes.

{texto aqui}
```

**Melhor ✅:**
``` text
Resuma o texto abaixo em uma lista de tópicos com os pontos mais importantes.  
Texto: 
"""  
{texto aqui}  
"""
```

---
## Seja detalhista

Seja específico, descritivo e o mais detalhado possível sobre o contexto desejado, resultado, comprimento, formato, estilo, etc

Menos eficaz ❌:
```
Escreva um poema sobre a OpenAI.
```

Melhor ✅:
```
Escreva um poema curto e inspirador sobre a OpenAI, focando no recente lançamento do
produto DALL-E (DALL-E é um modelo de IA que transforma texto em imagem) no estilo de
um {poeta famoso}
```

---
## Use exemplos

Articule o formato de saída desejado através de exemplos

Menos eficaz ❌:
```
Extraia as entidades mencionadas no texto abaixo. Extraia os seguintes 4 tipos de
entidades: nomes de empresas, nomes de pessoas, tópicos específicos e temas gerais.
  
Texto: {texto}
```

Mostre e diga - os modelos respondem melhor quando mostramos requisitos de formato específicos. Isso também facilita a extração programática de múltiplas saídas de forma confiável.

---
Melhor ✅:
```
Extraia as entidades importantes mencionadas no texto abaixo. Primeiro extraia todos os nomes de empresas, depois todos os nomes de pessoas, em seguida, extraia tópicos específicos que se adequem ao conteúdo e, finalmente, extraia os temas gerais
abrangentes  
  
Formato desejado:  
Nomes de empresas: <lista_separada_por_vírgulas_dos_nomes_das_empresas>  
Nomes de pessoas: -||-  
Tópicos específicos: -||-  
Temas gerais: -||-  
  
Texto: {texto}
```


---
##  Comece com zero-shot, depois few-shot

✅ Zero-shot

``` prompt
Extraia palavras-chave do texto abaixo.  
  
Texto: {texto}  
  
Palavras-chave:
```


✅ Few-shot - forneça um par de exemplos
``` prompt
Extraia palavras-chave dos textos correspondentes abaixo.  
  
Texto 1: A Stripe oferece APIs que desenvolvedores web podem usar para integrar processamento de pagamento em seus sites e aplicações móveis.  
Palavras-chave 1: Stripe, processamento de pagamento, APIs, desenvolvedores web, sites, aplicações móveis  
##  
Texto 2: A OpenAI treinou modelos de linguagem de ponta que são muito bons em entender e gerar texto. Nossa API fornece acesso a esses modelos e pode ser usada para resolver praticamente qualquer tarefa que envolva o processamento da linguagem.  
Palavras-chave 2: OpenAI, modelos de linguagem, processamento de texto, API.  
##  
Texto 3: {texto}  
Palavras-chave 3:
```


---
## Seja preciso

Menos eficaz ❌:
```
A descrição para este produto deve ser bastante curta, apenas algumas frases, e não muito mais.
```

Melhor ✅:
```
Use um parágrafo de 3 a 5 frases para descrever este produto.
```
---

Este texto foi traduzido e adaptado da seguinte fonte original:
[Best practices for prompt engineering with the OpenAI API | OpenAI Help Center](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-the-openai-api)
