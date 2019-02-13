+++
authors = "Morvana Bonin"
canonical = ""
categories = ["ia", "inteligencia artificial", "dados", "data science"]
date = "2019-02-13T09:00:00-02:00"
excerpt = "Um pouco sobre Regressão Linear."
image = "https://i.imgur.com/961FCPS.jpg"
publishdate = "2019-02-13T09:00:00-02:00"
sponsor = "kinghost"
tags = ["estatistica", "data science"]
title = "Regressão Linear Simples"
type = "post"

+++
Regressão Linear é um modelo de Supervised Learning e provavelmente um dos mais conhecidos e um dos mais populares modelos em Machine Learning (para saber mais sobre Supervised Learning e Machine Learning, [leia esse post introdutório](https://king.host/blog/2018/03/machine-learning-uma-introducao/).

![](https://i.imgur.com/6mPgnyJ.png)

A Regressão Linear tenta modelar, assumindo uma relação linear entre a variável de entrada (nesse caso o x) com a variável de saída (nesse caso o y), ou seja, a variável y pode ser calculada a partir da combinação linear da variável de entrada x.

![](https://i.imgur.com/Xf6GLhL.png)

y é a predição numérica de saída, baseando-se no valor de entra χi

# Modelo de representação
Regressão Linear é um dos modelos mais atrativos devido a sua representação entendível, no caso da regressão linear simples sua utilização é mais para aprendizado, já que na prática ela não é muito aplicada, visto que, em muitos casos a gama de variáveis de entradas é maior, fazendo-se uso da Regressão Linear Multivariável, ao qual não adentraremos nesse post.
O modelo de representação da regressão linear simples é a tradicional equação conhecida como equação da reta ou em inglês slope-intercept form, usaremos a notação mais utilizada em exemplos de Machine Learning e não da matemática, mas você pode saber mais sobre a própria equação neste [link](https://medium.com/r/?url=https%3A%2F%2Fpt.khanacademy.org%2Fmath%2Falgebra%2Ftwo-var-linear-equations%2Fslope-intercept-form%2Fa%2Fintroduction-to-slope-intercept-form).

![](https://i.imgur.com/jstzcUy.png)

Temos o y a variável dependente que representa a predição, as letras gregas β (Beta), também conhecidos como coeficientes, que são a representação das variáveis que o algoritmo irá utilizar para “aprender” a produzir as previsões mais precisas e o x a variável independente que representa o dado de entrada.
As letras gregas β também são conhecidas como inclinação e interceptação ou em inglês intercept-slope.

# Função de custo
Função de custo, no inglês cost function ou ainda ordinary least squares é uma função utilizada para medir o quão errado o modelo está, os chamados resíduos. Isto é, consiste no cálculo da distância de cada ponto (distância essa entre as variáveis x e y) em relação a reta de regressão, esse valor é elevado ao quadrado e somado, o total é a quantidade média de erro do modelo.

![](https://i.imgur.com/mVRWWbg.png)

A [MSE](https://medium.com/r/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FMean_squared_error) (Mean squared error) é uma função frequentemente usada para efetuar esse cálculo.
O objetivo da função de custo é medir o desempenho do modelo, pois o custo é maior quando o modelo está com desempenho ruim, dessa forma mede-se os parâmetros que dão o mínimo custo possível.

# Gradient Descent
Com a função de custo tem-se o cálculo da média do erro, para minimizar esse erro e ajustar o modelo, usamos a operação Gradient Descent.

A operação Gradient Descent é utilizada para otimizar os valores coeficientes, assim, minimizando iterativamente o erro do modelo em seus dados de treinamento (training data).
Na prática, a operação Gradient Descent é útil em uma larga quantidade de dados, principalmente em Regressão Linear Multivariável onde se tem uma grande quantidade tanto de linhas, como colunas de dados e que podem não caber na memória.

# Conclusão
Foi dado um conceito mais teórico sobre Regressão Linear Simples, e não entrando muito em suas funções matemáticas. Essa é uma parte inicial, como um “Hello World”, no campo de Machine Learning, pertencente a Supervised Learning , muitas nomenclaturas foram mantidas em inglês devido a sua facilidade em buscas por materiais de estudos e por algumas palavras não terem sido encontradas uma tradução oficial em português.
As referências são materiais que não só foram utilizados como forma de pesquisa nesse post, mas também para melhor aprofundamento sobre o conteúdo, todos são em inglês.
 
# Fontes de pesquisas:
- [https://youtu.be/nk2CQITm_eo](https://youtu.be/nk2CQITm_eo)
- [https://dzone.com/asset/download/259](https://dzone.com/asset/download/259)
- [https://www.coursera.org/learn/machine-learning](https://www.coursera.org/learn/machine-learning)
- [http://onlinestatbook.com/2/regression/intro.html](http://onlinestatbook.com/2/regression/intro.html)
- [https://www.amazon.com/gp/product/B07335JNW1](https://www.amazon.com/gp/product/B07335JNW1)
- [http://www.stat.yale.edu/Courses/1997-98/101/linreg.htm](http://www.stat.yale.edu/Courses/1997-98/101/linreg.htm)
- [https://www.statisticssolutions.com/what-is-linear-regression](https://www.statisticssolutions.com/what-is-linear-regression)
- [https://ml-cheatsheet.readthedocs.io/en/latest/linear_regression.html](https://ml-cheatsheet.readthedocs.io/en/latest/linear_regression.html)
- [https://ml-cheatsheet.readthedocs.io/en/latest/gradient_descent.html](https://ml-cheatsheet.readthedocs.io/en/latest/gradient_descent.html)
- [https://machinelearningmastery.com/master-machine-learning-algorithms](https://machinelearningmastery.com/master-machine-learning-algorithms)