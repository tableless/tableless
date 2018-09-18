+++
authors = "Lucas Lo Ami Alvino Silva"
categories = ["Data Science"]
date = "2018-08-09T05:40:00-03:00"
excerpt = "Resolvendo um desafio de classificação das questões do Stack Exchange proposto no HackerRank."
image = "https://cdn-images-1.medium.com/max/1000/1*Llq4dw2tSfEU7FKBJG-fJg.jpeg"
publishdate = "2018-08-09T05:40:00-03:00"
tags = ["Machine Learning"]
title = "Classificando o conteúdo do Stack Exchange - Parte 1"
type = "post"

+++
O [Stack Exchange](https://stackexchange.com/) é um conjunto de sites de Q&A (_question-and-answer_) que abordam diversos temas diferentes. Provavelmente você conhece e participa do mais famosos desses sites, o Stack Overflow, que aborda a temática de programação. Existem outros tópicos abordados nos diversos sites, como matemática, estatística, eletrônica, etc., cada um com seu site especializado. A maioria tem uma comunidade bem ativa e participante, como pode ser visto em seu [Data Explorer](https://data.stackexchange.com/).

Neste texto eu vou começar a resolver um desafio de [classificação das questões do Stack Exchange proposto no HackerRank](https://www.hackerrank.com/challenges/stack-exchange-question-classifier/problem). Ele vai ser dividido em duas partes principais:

* Leitura e exploração dos datasets do desafio
* Exploração das possibilidades _features_ que se encaixam na resolução do problema

Todo o projeto foi implementado utilizando uma stack baseada em frameworks do Python: Pandas e Scikit Learn.

***

### Os dados estão com formatos diferentes

O desafio nos fornece o conjunto de dados de treino e de teste separadamente e em formatos ligeiramente diferentes. O arquivo de treino contém duas partes principais: a primeira linha contendo um número inteiro N indicando quantas linhas subsequentes existem e N linhas com objetos JSON que representam uma observação, composta pelas JSON _keys_ tópico (_topic_), excerto (_excerpt_) e questão (_question_). Já o conjunto de teste é dividido em dois arquivos, o primeiro tem um formato semelhante ao arquivo de treino, exceto que a JSON _key_ tópico não está presente; segundo arquivo contém uma lista de tópicos para cada entrada do arquivo anterior. O código abaixo mostra como é feita a leitura dos dados.

Neste desafio, usaremos 10 tópicos diferentes para classificação das questões e uma base de treino que contém 20219 exemplos. O código abaixo mostra como ler os arquivos de treino e teste sem a necessidade de alterar a formatação dos mesmos (dica, se você eliminar a primeira linha do arquivo de treino fica bem mais fácil de lê-lo com o Pandas).

<script src="https://gist.github.com/lucasloami/4f3f41f9a486fe9775eb8e955c35cfad.js"></script>

***

### A investigação dos dados começa aqui

Se você explorar um pouquinho o dataset de treino, vai perceber que diversas questões e excertos contém palavras-chave que nos indicam já de cara sobre qual tópico estão falando. Por exemplo, termos como “_node_”, “_transmission_”, “_LEDs_”, “_raspberry_” são bons indicativos do tópico “_electronics_”; já termos como “_trilogy_”, “_wolverine_”, “film”, “_demendor_”, “_battle_” nos remetem ao tópico “scifi”. Esse é um insight super interessante, pois como veremos na próxima seção, algumas _features_ que definimos em NLP partem do princípio que existem conjuntos de palavras que têm maior “chance” de aparecer em determinados tópicos do que em outros.

Por outro lado, existem palavras que são muito comuns dentro de textos e que não necessariamente carregam um significado naquele contexto, ou seja, não são palavras-chave. Elas são geralmente preposições, artigos, advérbios, verbos, etc. Se olharmos novamente o dataset de treino, vemos alguns exemplos como “_in_”, “_I’m_”, “_about_”, “_this_”, “_be_”, etc. A esses termos chamamos de _stopwords_.

Exemplos de algumas questões presentes na base de treino:

![](https://cdn-images-1.medium.com/max/800/1\*JqC1yZoAOp1QJjG41p2i1g.png)

Uma das preocupações que existem quando se cria um modelo de classificação é a do enviesamento do mesmo. Uma das formas de isso acontecer é ter, no dataset de treino uma quantidade muito maior de um dos valores da variável alvo em relação aos demais. Por exemplo, se, no dataset desse projeto, a quantidade de exemplos do tópico _electronics_ for muito maior do que a dos demais tópicos, o modelo tenderá a classificar a maior parte dos novos documentos como _electronics_.

Vale a ressalva de que nem sempre esse viés do classificador é algo ruim. No exemplo citado, se o fórum do Stack Exchange for muito focado no tópico _electronics_, talvez o classificador só esteja refletindo uma distribuição dos dados reais, porém se isso for um problema do dataset utilizado, o classificador provavelmente errará boa parte das predições.

A partir do gráfico abaixo, é possível perceber que a quantidade de exemplos do tópico _matematica_ é menor do que a dos demais. Por outro lado, os tópicos _gis_ e _scifi_ são os que tem a maior quantidade de exemplos. Esse insight pode sugerir a necessidade de realizarmos um balanceamento de classes antes de treinar o modelo.

<script src="https://gist.github.com/lucasloami/9e8f470abc797ed2588d1db8cebf0af9.js"></script>

![](https://cdn-images-1.medium.com/max/800/1\*mkyYrlcytqIQy6ZyR6cuqA.png)

Além da presença _stopwords_ no texto, um outro valor que talvez influencie o desafio de classificação de texto é o tamanho dos textos em si. Se pensarmos nesse desafio de uma forma mais intuitiva, é possível imaginar que talvez alguns tipos de questão exijam respostas de tamanhos maiores ou perguntas maiores, para melhor explicitar o problema e a solução ali presentes. Dado isso, talvez essa informação esteja relacionada com algum tópico.

<script src="https://gist.github.com/lucasloami/5a52df80063b160e61c5b11992d81b2e.js"></script>

![](https://cdn-images-1.medium.com/max/800/1\*2oej-IwzFfTIJgiC_4ALiQ.png)

![](https://cdn-images-1.medium.com/max/800/1\*SJD2Wtsii5XOjA2lMjRmKA.png)

A partir dos gráficos acima, é possível perceber que:

* O tamanho dos excertos se concentra em torno de 200 caracteres
* O tamanho das questões tem uma variação maior. A distribuição dos tamanhos se assemelha a uma curva normal com uma cauda mais esticada para a direita
* O tamanho médio dos excertos e das questões dentro de cada um dos tópicos não tem uma variação muito grande. Dado isso, será que é relevante considerarmos o tamanho do documento como uma _feature_?

***

### Quais features podemos utilizar?

No contexto de NLP, as _features_ utilizadas são, em sua maioria, as próprias palavras que compõem o seu dataset, ou melhor, são métricas relacionadas a essas palavras, tais como contagem de aparições de palavras, frequência de aparição das palavras, etc.

Essas métricas podem ser combinadas com outros elementos para gerar novas _features_, tais como part-of-speech tagging, que identifica a função morfológica das palavras dentro de uma sentença. Ou seja, é possível usar a contagem de adjetivos e verbos dentro de uma frase como _features_.

Outro conceito importante é o de n-gramas (_n-grams_), que são um conjunto de palavras que co-ocorrem numa determinada janela de uma sentença textual. Por exemplo, vamos considerar a frase “_tomorrow will be a cloudy day_”; se n=2, teremos os seguintes n-gramas:

* tomorrow will
* will be
* be a
* a cloudy
* cloudy day

Os n-gramas com n=1 são chamados de unigramas, aqueles com n=2 são chamados de bigramas, com n=3, trigramas e por aí vai. É possível combinar as métricas citadas no primeiro parágrafo com n-gramas.

E para deixar as coisas mais claras, vou explorar abaixo como funcionam algumas desses atributos. Eles serão explicados utilizando unigramas como exemplo.

**Contagem de palavras**

Essa é a _feature_ mais básica em NLP. Ela também é conhecida como _bag of words_ ou _word count_ e consiste basicamente em contar a quantidade de aparições de uma mesma palavra (no contexto de NLP muitas vezes chamadas de _token_) dentro de cada entrada do seu dataset.

Podemos ver um exemplo de como ela funciona abaixo a partir de duas questões extraídas do dataset de treino:

* Questão 01: URL displays different page (a loop)?
* Questão 02: How to Block a url not a website?

![](https://cdn-images-1.medium.com/max/800/1\*oAOrhP6oqhqLgCev2Tphxg.png)

Dá pra perceber que o artigo “a” aparece duas vezes na segunda questão e os demais termos aparecem apenas uma vez ou nenhuma. Se tocaram também que existe uma quantidade enorme de brancos dentro dessa tabela? Isso acontece porque o conjunto de palavras existentes no dataset é muito maior do que a quantidade de entradas no mesmo, causando o efeito de esparsidade na tabela construída. Por isso, pode ser interessante remover as _stopwords_, uma vez que elas não agregam grandes informações para descobrir o tópico ao qual pertence uma frase.

**Frequência de termos**

Apesar de contagem de palavras ser uma _feature_ legal, ela traz alguns vieses negativos. Um deles é que entradas do dataset que tiverem um tamanho maior de caracteres tendem a ter maiores valores de contagem, enquanto entradas menores, tendem a ter contagens menores, mesmo para um único tópico.

Uma forma de normalizar esses valores dentro de um mesmo intervalo é usando a frequência de termos (_term frequency_ — TF), cuja fórmula é:

![](https://cdn-images-1.medium.com/max/800/1\*F1YegO-N-GvcT6iMQNYRKg.png)

Vamos fazer um exemplo com as duas frases usadas anteriormente:

![](https://cdn-images-1.medium.com/max/800/1\*kUs_jXXvtnq8VLJUG6_k8w.png)

Tanto a contagem de palavras quanto a frequência de palavras mensuram a importância/relevância dos termos dentro de uma entrada do dataset a partir da sua abundância naquele contexto, ou seja, as palavras que aparecem mais tem um maior peso.

**Frequência do termo–inverso da frequência nos documentos (TF-IDF)**

A partir dos exemplos acima, note que o artigo “_a_” ainda tem a maior relevância dentro de toda a tabela. O TF-IDF lida exatamente com esse cenário. Ele parte do pressuposto de que palavras importantes não aparecem muito em todas as entradas do dataset. Para isso, ele combina a TF com um elemento de “peso”, o IDF, que é calculado a partir da seguinte fórmula:

![](https://cdn-images-1.medium.com/max/800/1\*Ze1jM2G5toAd3cms6tJkQA.png)

O TF-IDF é resultado da multiplicação desses dois elementos:

![](https://cdn-images-1.medium.com/max/800/1\*YHP7ndqe72AKFUH-T-ZNCQ.png)

Vamos fazer um exemplo com as duas frases usadas anteriormente:

![](https://cdn-images-1.medium.com/max/800/1\*J6AilTlrmC4PS6eqaCiUFg.png)

É possível notar nesse exemplo que as palavras que são comuns aos dois documentos tiveram seu peso drasticamente reduzido a zero e as demais tiveram redução leve em seus pesos.

***

### Resumindo…

Nesse primeiro texto lemos os dados de treino e teste em dataframes do pandas, fizemos uma exploração dos dados de treino, observando elementos-chave que compõem as questões e excertos e também como é a distribuição de exemplos para cada um dos tópicos. Além disso exploramos as possíveis _features_ que podemos usar para resolver esse desafio de classificação de documentos.

O próximo texto vai abordar a implementação prática da parte de _feature_ _engineering_ bem como aplicação de alguns algoritmos de classificação.

***

_Ah, vale lembrar que o código completo que criei para resolver esse desafio está no_ [_meu Github_](https://github.com/lucasloami/automatic_brain) _(se forem reutilizar meu código, lembrem de dar uma olhadinha na licença do projeto)._