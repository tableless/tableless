+++
authors = "Lucas Lo Ami Alvino Silva"
canonical = ""
categories = ["backend", "datascience"]
date = "2018-09-03T09:40:07-03:00"
excerpt = "A série de textos que mostram como resolver o desafio de classificação textual do HackerRank finaliza por aqui."
image = "https://i.imgur.com/SGrw9RR.jpg"
publishdate = "2018-09-03T09:40:00-03:00"
tags = ["datascience", "machinelearning"]
title = "Classificando o conteúdo do Stack Exchange (parte 03/03)"
type = "post"

+++
Urfa, chegamos no último texto dessa série. Já fizemos a [exploração dos dados, abordamos possíveis _features_](https://tableless.com.br/classificando-o-conteudo-do-stack-exchange-parte-1/) para classificação de texto e mostramos [como implementar tudo isso na prática e combinar com classificadores](https://tableless.com.br/classificando-o-conteudo-do-stack-exchange-parte-2/) de _machine learning_. 

Nesse texto vou explorar algumas estratégias alternativas que podem ser usadas para melhorar os resultados do nosso modelo. Nem sempre elas vão gerar o efeito desejado, mas acho válido tentá-las.

Vou abordar dois tópicos principais nesse texto:

* Uso de bigramas
* Stemização

# Bigramas ao invés de unigramas como _features_

Lá no [primeiro texto](https://tableless.com.br/classificando-o-conteudo-do-stack-exchange-parte-1/) dessa série, eu falei sobre algumas variações de n-gramas existentes, tais como os unigramas (usados na resolução do desafio até agora), bigramas, trigramas e por aí vai. Ao utilizar n-gramas com n > 1 a intenção é conseguir capturar algumas relações entre palavras no conjunto de dados e que possam ajudar a identificar uma frase específica. Por exemplo, considere as frases abaixo extraídas do dataset de treino:

* _Do computers speed up at higher temperatures?_
* _Looking for 80’s series or movie about programmable short term memory_

Perceba que na primeira frase bigramas como “_computers speed_”, “_speed up_”, e “_higher temperatures_” podem ajudar a identificar a frase como pertencente ao tópico “_electronics_”. Já na segunda frase bigramas como “_80’s series_”, “_movie about_” e também o trigrama “_short term memory_” podem ajudar a identificar a frase como pertencente ao tópico “_scifi_”. Para resolver o desafio de [classificação textual do Stack Exchange](https://www.hackerrank.com/challenges/stack-exchange-question-classifier/problem), optei por usar bigramas, pois eles apresentam resultados melhores do que trigramas e n-gramas com n > 3, como podem ver [neste artigo](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.2.1938&rep=rep1&type=pdf) e [neste aqui também](https://www.mitpressjournals.org/doi/pdf/10.1162/COLI_a_00149) (se estiverem com muita vontade de ler, também vale a leitura deste [pequeno artigo](https://www.aclweb.org/anthology/P12-2018), de 2012).

Para implementar os bigramas no dataset de treino, usaremos a mesma estrutura de texto mostrada no [segundo texto dessa série](https://medium.com/tableless/classificando-o-conteudo-do-stack-exchange-02-6d9975e00ff7), no qual reuni as colunas “_question_” e “_excerpt_” em uma só. Combinei os bigramas gerados com gerados com as três métricas das quais falamos: contagem de palavras, frequência de termos e TF-IDF, apliquei neles o Multinomial Naive Bayes (MNB) e o _Support Vector Machines_ (SVM) com kernel linear. O código abaixo mostra como tudo isso foi implementado.

<script src="https://gist.github.com/lucasloami/7859708e653d53804bb5d7f6a5d1b116.js"></script>

Os classificadores criados foram avaliados com a métrica de acurácia. O código que a calcula é bem simples e pode ser visto nas últimas linhas do código acima. Já a tabela a seguir mostra um resumo dos resultados obtidos, nos quais o SVM com TF-IDF teve o melhor resultado, com 82% de acurácia. De maneira geral o uso de bigramas como features piorou o desempenho do dois algoritmos de classificação.

![](https://cdn-images-1.medium.com/max/800/1*8em9Z1j6Sh75BJeKmt8TsA.png)

Agora que sei qual o melhor modelo criado, vou aplicá-lo na base de testes e vou checar a acurácia final. O código abaixo mostra como fazer isso.

<script src="https://gist.github.com/lucasloami/d2ff1644137d498ac4d542a74afa8532.js"></script>

A acurácia final que conseguimos foi de: 0,83 (83%).

# Stemização

Quando projetos de NLP são desenvolvidos , lidamos com palavras que estão conjugadas em diferentes tempos verbais, graus (ex: advérbios no superlativo), gênero e número, mas que essencialmente continuam representando o mesmo conceito. As abordagens que usei até agora para resolver o desafio do HackerRank não levam em consideração esse fator, o que pode acarretar na existência de _features_ redundantes, ou seja, que representam o mesmo conceito.

Para lidar com essa situação, precisamos normalizar as palavras presentes no dataset de treino. Em NLP, as duas principais formas de normalizar palavras são:

1. Stemização (_stemming_): é o processo de redução das palavras a sua base (_stem_). Em alguns lugares vocề encontrará que é o processo de remoção das flexões/derivações das palavras, mantendo apenas o seu radical (morfema básico que guarda o significado da palavra)
2. Lematização (_lemmatization_): é o processo que deflexiona uma palavra a fim de obter o seu lema (forma canônica), que é a representação singular masculino para substantivos e adjetivos e infinitivo para verbos.

Neste desafio, vamos usar a técnica de stemização. Para isso, vamos usar uma biblioteca do Python focada em NLP, a [NLTK](https://www.nltk.org/) e o algoritmo de stemização de Porter, o mais famoso entre os existentes. Não vou entrar em detalhes do funcionamento do mesmo, mas se você tem muita curiosidade pra saber mais a respeito dele, recomendo dar uma olhadinha [nesses slides do professor Jesús Mena](https://professor.ufabc.edu.br/\~jesus.mena/courses/pln-1q-2018/PLN-aula04.pdf), da UFABC. O código abaixo mostra como usei a NLTK para stemizar os dados de treino.

<script src="https://gist.github.com/lucasloami/efe7952000c56ee46c3581af6e981f17.js"></script>

A tabela a seguir mostra um resumo dos resultados obtidos, nos quais o SVM com TF-IDF teve o melhor resultado, com 92% de acurácia.

![](https://cdn-images-1.medium.com/max/800/1*Yn7DH80heJIaFRI76wjAMQ.png)

Agora que sei qual o melhor modelo criado, vou aplicá-lo na base de testes e vou checar a acurácia final. O código abaixo mostra como fazer isso.

<script src="https://gist.github.com/lucasloami/af367fbba74a16812efa87ae752bf3a6.js"></script>

A acurácia final que conseguimos foi de: 0,92 (92%).

# Conclusões

Nesse texto abordei duas técnicas alternativas para melhorar a acurácia dos modelos criados, o uso de bigramas como _features_ e também a stemização para normalizar os dados. De maneira geral, nenhum dos novos modelos superou os resultados apresentados no [segundo texto dessa série](https://tableless.com.br/classificando-o-conteudo-do-stack-exchange-parte-2/).

Também tive algumas outras ideias que poderiam ser implementadas e que você também pode testar por aí. Elas são:

* Usar outros algoritmos de classificação: em especial, eu testaria algum ensemble, como _Random Forest_ com todos os conjuntos de _features_descritos nesta série de textos. Outra opção interessante é usar redes neurais com _word embeddings_.
* Combinar os diferentes tipos de _features_ geradas: talvez colocar no conjunto de dados de treino unigramas e bigramas possa ajudar.

A série de textos que mostram como resolver o [desafio de classificação textual do HackerRank](https://www.hackerrank.com/challenges/stack-exchange-question-classifier/problem) finaliza por aqui. O código completo que criei para resolver esse desafio está no [meu Github](https://github.com/lucasloami/automatic_brain) (se forem reutilizar meu código, lembrem de dar uma olhadinha na licença do projeto).