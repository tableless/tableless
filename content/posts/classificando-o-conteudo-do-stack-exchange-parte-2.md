+++
authors = "Lucas Lo Ami Alvino Silva"
categories = ["Data Science"]
date = "2018-08-16T04:54:00-03:00"
excerpt = "Resolvendo um desafio de classificação das questões do Stack Exchange proposto no HackerRank."
image = "https://cdn-images-1.medium.com/max/1000/1*LmBD9OaRAJPnBYBoZwyZMw.jpeg"
publishdate = "2018-08-16T04:54:00-03:00"
tags = ["Machine Learning"]
title = "Classificando o conteúdo do Stack Exchange - Parte 2"
type = "post"

+++
Se você tá lendo esse texto, provavelmente já deve ter lido a [parte 01](https://medium.com/tableless/classificando-o-conteudo-do-stack-exchange-8f3ea68fb2af). Se não, corre lá pra entender o cenário do que vou escrever abaixo. 

Nesse artigo vamos falar sobre três tópicos:

* _Feature engineering_ na prática
* Algoritmos de predição escolhidos para resolver esse problema
* Validação dos resultados do modelo usando métricas

### Criar as features do modelo

No [último texto](https://medium.com/tableless/classificando-o-conteudo-do-stack-exchange-8f3ea68fb2af) expliquei como funciona a contagem de termos, frequência de termos e o TF-IDF. No scikit-learn é bem fácil de construir cada uma dessas _features_ com pouco código, basta usar uma combinação do **CountVectorizer**com o **TfidfTransformer** (há outras formas de fazer chegar ao mesmo resultado, mas esse método que vou usar é descrito na [documentação do scikit-learn](https://medium.com/r/?url=http%3A%2F%2Fscikit-learn.org%2Fstable%2Ftutorial%2Ftext_analytics%2Fworking_with_text_data.html%23tokenizing-text-with-scikit-learn)).

Um ponto de atenção importante o utilizar esses métodos é a parte da normalização dos dados. Nós usaremos o **TfidfTransformer** para calcular possui dois métodos possíveis:

* L1 (_least absolute deviation_ — LAD): também conhecido como o método que a gente vai usar para resolver nosso desafio, ele consiste em dividirmos a contagem de cada termo numa entrada do dataset de treino pela soma da contagem de todos os termos daquela mesma entrada.
* L2 (_least square error_ — LSE): consiste em dividirmos a contagem de cada termo numa entrada do dataset de treino pela raiz quadrada da soma dos quadrados de cada termo daquela mesma entrada

Lembram das _stopwords_? A gente também precisa removê-las. Mas a notícia boa é que conseguimos fazer isso dentro do **CountVectorizer**. Mas antes de começar a implementar os elementos citados acima, precisamos ajustar nossos dados para que eles possam ser enviados para o scikit learn. Para isso, precisaremos de duas coisas:

1. Usar as colunas _excerpt_ e _question_ juntas, pois elas contém texto capaz de identificar o tópico. O conteúdo delas deve estar minúsculo também
2. Transformar os tópicos do dataset em valores inteiros usando o **LabelEncoder** do scikit learn, pois a biblioteca não trabalha com strings em seus modelos

<script src="https://gist.github.com/lucasloami/8796c61079b35356aec34bdb480ef85f.js"></script>

Agora sim podemos criar nossas _features_ como mostrado no código abaixo:

<script src="https://gist.github.com/lucasloami/e10dbd64397e1df6e15559845d080a8c.js"></script>


### A predição

Escolhi dois algoritmos para tentar resolver esse desafio: o _Multinomial Naive Bayes_ e o _Support Vector Machines_. Mas por que os escolhi? Essa resposta é simples: eles são usado em pesquisas científicas de NLP.

Em toda atividade de aprendizado supervisionado (classificação e regressão) precisamos dividir nossa base em treino e teste. A priori os dados para esse problema já estão divididos, pois temos um arquivo apenas com dados de treino e outros dois com dados de teste (não lembra disso? Então refresca a memória no [primeiro texto](https://medium.com/tableless/classificando-o-conteudo-do-stack-exchange-8f3ea68fb2af)). Não vamos mexer na base de testes por enquanto; ela vai ser usada quando eu descobrir qual o melhor algoritmo de predição.

Vamos focar na base de treino então. Vou dividi-la em duas bases, uma que vai servir para treinar o algoritmo e outra que vai servir como teste; vou usar um split de 80% dos dados para treino e 20% dos dados para teste. Ora bolas, mas por que eu tô fazendo isso? Porque na maioria das situações cotidianas vividas por um cientista de dados, não existe essa separação bonitinha de base de treino e base de teste, mas sim uma base única com os dados coletados e existem aqueles dados que você nunca viu antes e nos quais você quer aplicar o algoritmo que treinado. Para a resolução desse desafio do Stack Exchange, eu tô fingindo que a base de treino corresponde a essa base única com todos os dados coletados e que a base de testes é o conjunto de dados que eu nunca vi antes.

O código abaixo mostra como fazer essa divisão nos dados de treino para cada um dos tipos de _features_ gerados.

<script src="https://gist.github.com/lucasloami/d7b8a23dfabaa9d0affca0a9fd01bb25.js"></script>

### Desmistificando o Multinomial Naive Bayes

Os classificadores _naive bayes_ são algoritmos probabilísticos baseados no teorema de Bayes e eles tem uma característica interessante de assumir independência total entre as _features_ do modelo. Para entendermos o funcionamento do _Multinomial Naive Bayes_, vamos lembrar um pouquinho de probabilidade condicional: dada uma frase w que precisa ser classificada, ou melhor, suas _features_ w=(w1, w2, w3, …, wn), nós temos que a probabilidade de escolhermos a classe ck , onde ck ∈ Ck (conjunto de todas as classes) dado w é p(ck | w1, w2, w3, …, wn). Podemos generalizar essa probabilidade da seguinte forma:

![](https://cdn-images-1.medium.com/max/800/1\*WZNyL5bx6ruDoOHWNC1VkQ.png)

Não vamos entrar em detalhes matemáticos aqui, mas essa expressão pode ser representada como uma probabilidade conjunta.

![](https://cdn-images-1.medium.com/max/800/1\*5Nlpmo0DmeN07GQpPdgfhA.png)

Onde p(ck) é a probabilidade anterior (_prior probability_) da classe ck e p(wi | ck) é a probabilidade condicional da _feature_ wi dada a classe ck . Como estamos trabalhando com um classificador, precisamos de uma regra que defina uma classe para a frase w e, para isso, usamos a _maximum a posteriori_, que basicamente usa a classe com a maior probabilidade de aparecer. Representamos isso com a fórmula abaixo:

![](https://cdn-images-1.medium.com/max/800/1\*x5UXLMqJm93JB1gTF0crlg.png)

O Multinomial Naive Bayes usa todos os conceitos acima, com a adição de que a probabilidade condicional de uma _feature_ wi dada uma classe ck é calculada a partir da frequência relativa de wi nos documentos com a classe ck.

Você pode ler detalhes sobre o classificadores Naive Bayes e suas variantes neste excelente [blog post](https://medium.com/r/?url=http%3A%2F%2Fblog.datumbox.com%2Fmachine-learning-tutorial-the-naive-bayes-text-classifier%2F), [nesse aqui também](https://medium.com/syncedreview/applying-multinomial-naive-bayes-to-nlp-problems-a-practical-explanation-4f5271768ebf) e nesse [artigo científico](https://medium.com/r/?url=http%3A%2F%2Fwww.cs.cmu.edu%2F\~knigam%2Fpapers%2Fmultinomial-aaaiws98.pdf). O código abaixo mostra como treinar um classificador desse tipo:

<script src="https://gist.github.com/lucasloami/3ae30356e30f7abd35534a1ecd198b16.js"></script>

### Desmistificando o _Support Vector Machines_ (SVM)

Por trás desse nome complicado jaz um algoritmo que não é tão difícil assim de entender e ao mesmo tempo é bem poderoso. Ele pode ser usado tanto para atividades de regressão quanto para atividades de classificação. Neste último caso o SVM encontra o melhor hiperplano que diferencia as classes do modelo de um jeito bom.

Para entender o SVM, é preciso aprender os conceitos de hiperplano, _support vectors_, margens e funções de kernel. Vou explicar usando a imagem abaixo:

![](https://cdn-images-1.medium.com/max/800/1\*-8OHzmkbIADmgwQwCb4U2Q.png)

A linha vermelha é o que chamamos de hiperplano, que basicamente um conceito que generaliza a noção de reta e plano para várias dimensões. Então, o SVM acha a melhor posição do hiperplano que divide as bolinhas laranjas dos quadrados roxos. E como ele faz isso? Baseado em duas coisas principais: os _support vectors_ e as margens.

Os _support vectors_ os pontos mais próximos do hiperplano e que, se forem removidos do conjunto de dados, alterariam a posição do hiperplano. Em outras palavras, são elementos críticos para que o SVM executar a classificação adequadamente. Já as margens são as distâncias entre os _support vectors_ e os possíveis hiperplanos. O SVM seleciona o hiperplano que maximiza as distâncias entre todos os _support vectors_.

Mas e quando o conjunto de dados não é linearmente separável como na imagem abaixo da esquerda? É aí que entra o que chamamos de _kernel trick_. As funções de kernel visam transformar um espaço n-dimensional em um espaço m-dimensional, tal que m > n. Em outras palavras, elas transformam um problema que não é linearmente separável em um que seja. É o que aconteceu na imagem abaixo da direita, pois no espaço bidimensional os pontos não são separáveis linearmente, mas no espaço tridimensional são.

![](https://cdn-images-1.medium.com/max/800/1\*trZF-_-hbbslLHhjBASaRg.png)

Você pode ler detalhes sobre o svm e suas variantes neste [blog post](https://medium.com/r/?url=http%3A%2F%2Fblog.aylien.com%2Fsupport-vector-machines-for-dummies-a-simple%2F), [nesse aqui também](https://medium.com/r/?url=https%3A%2F%2Fwww.analyticsvidhya.com%2Fblog%2F2017%2F09%2Funderstaing-support-vector-machine-example-code%2F) e nesse [artigo científico](https://medium.com/r/?url=http%3A%2F%2Fweb.cs.iastate.edu%2F\~honavar%2Ftext-classification-SVM.pdf), que aborda classificação de texto usando esse algoritmo. Ah, você não pode esquecer de olhar rapidinho a [documentação do SVM no scikit learn](https://medium.com/r/?url=http%3A%2F%2Fscikit-learn.org%2Fstable%2Fmodules%2Fsvm.html) para entender alguns parâmetros dele.

O código abaixo mostra como treinar um classificador desse tipo. Para resolver esse desafio, usaremos um kernel linear por questões de performance (usar outros kernels faz a etapa de treino demorar muito no meu computador) e também um pequeno GridSearch para determinar o melhor valor para o parâmetro C, que trabalha a regularização dentro do modelo:

<script src="https://gist.github.com/lucasloami/ec68bf46ef9da2cdcc9dd1e101d9c7bf.js"></script>

### Medindo os resultados

Agora que o modelo está criado precisamos validar o quão bom ele está. Para isso, vamos usar a mesma métrica descrita no [desafio do HackerRank](https://medium.com/r/?url=https%3A%2F%2Fwww.hackerrank.com%2Fchallenges%2Fstack-exchange-question-classifier%2Fproblem): a acurácia. Em problemas do mundo real, a acurácia muitas vezes não é a única métrica que precisa ser avaliada para definir a qualidade de um modelo, mas vamos manter as coisas simples nesse desafio e no futuro podemos ver mais métricas. O código abaixo mostra como calcular a acurácia dos modelos que criamos:

<script src="https://gist.github.com/lucasloami/f5d5361d9d7dfd957c06242bf122b9ab.js"></script>

A tabela a seguir, que resume os resultados obtidos aplicando cada uma dos classificadores, mostra que o SVM com TF-IDF foi o melhor classificador que criamos.

![](https://cdn-images-1.medium.com/max/800/1\*xJckW_55nzZB5RloVLyPUg.png)

Agora que descobri qual o melhor modelo, eu vou usá-lo na base de testes e vou checar a acurácia final. O código abaixo mostra como fazer isso:

<script src="https://gist.github.com/lucasloami/cc22cf50f728dfc4f3f72aa71bd2db70.js"></script>

A acurácia final foi de: 0,92 (92%).

### Resumindo…

O objetivo desse texto era mostrar, na prática, como implementar _feature engineering_ nos dados de texto e depois usá-los com classificadores de _machine learning_. 

O próximo texto vai abordar algumas variações que podemos aplicar na resolução desse desafio, tais como usar outras features e usar técnicas de lematização de palavras. 

Ah, vale lembrar que o código completo que criei para resolver esse desafio está no [meu Github](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2Flucasloami%2Fautomatic_brain) (se forem reutilizar meu código, lembrem de dar uma olhadinha na licença do projeto).