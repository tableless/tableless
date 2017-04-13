---
title: JAVA – Estruturas de Decisão
author: Fellipe Filgueiras
type: post
date: 2015-05-22
excerpt: Entenda o que são as estruturas de decisão no Java.
url: /java-estruturas-de-decisao/
categories:
  - Back-end
  - Java
tags:
  - back-end
  - java

---
As estruturas de decisão são utilizadas para controlar o fluxo de execução dos aplicativos, possibilitando que a leitura das instruções siga caminhos alternativos em função da análise de determinadas condições. Com elas, é possível condicionar a leitura de uma instrução ou de um bloco delas a uma ou mais condições que precisam ser satisfeitas.

Todos os aplicativos de exemplo precedentes executam suas instruções de forma linear, ou seja, todas elas são lidas sequencialmente, na ordem em que foram escritas no código. Com o uso de estruturas de decisão, alguns trechos dos programas somente serão executados sob determinadas condições.

## Estrutura if

A estrutura de decisão if é utilizada para impor uma ou mais condições que deverão ser satisfeitas para a execução de uma instrução ou bloco de instruções. A sua forma geral é a seguinte:

<pre class="lang-java">If (&lt;condição&gt;) &lt;instrução ou bloco&gt;
</pre>

A condição sempre irá figurar entre parênteses, após a palavra reservada if, e deve ser uma expressão booleana que resulte em um valor true ou false. A instrução ou o bloco de instruções somente será executado caso o resultado dessa expressão seja true. Caso o resultado seja false, o fluxo de execução será desviado e a instrução ou o bloco de instruções não será executado.

Havendo uma única instrução condicionada pela estrutura if, ela figura logo após a condição e termina com um ponto e vírgula. A sintaxe é a seguinte:

<pre class="lang-java">If(&lt;Condição&gt;) &lt;Instrução&gt;;
</pre>

## Estrutura if-else

A estrutura de decisão if-else é uma variação da estrutura if. Ela é utilizada para impor uma ou mais condições que deverão ser satisfeitas para a execução de uma instrução ou bloco de instruções e possibilita a definição de uma instrução ou bloco de instruções a serem executados caso as condições não sejam satisfeitas. A sua forma geral é a seguinte:

<pre class="lang-java">If(&lt;Condição&gt;) &lt;instrução ou bloco&gt;

else &lt;instrução ou bloco&gt;
</pre>

A condição sempre irá figurar entre parênteses, após a palavra reservada if, e deve ser uma expressão booleana que resulte em um valor true ou false. A primeira instrução ou o bloco de instruções somente será executado caso o resultado dessa expressão seja true. Caso o resultado seja false, o fluxo de execução será desviado e a instrução ou o bloco posterior ao else será executado.

## Equals

O método equals é usado para a comparação. A classe String e as classes Wrapper sobrescrevem o equals para garantir que dois objetos desses tipos, com o mesmo conteúdo, possam ser considerados iguais. Para descobrir se as referências são iguais, deve-se utilizar o   “ == ” para que seja comparado os bits das variáveis.

Toda comparação utilizando o equals irá verificar, primeiro se existe uma sobrescrita do mesmo nas classes comparadas. Caso não haja, o método padrão da classe Object é utilizado.

[<img class=" wp-image-48938 size-full aligncenter" src="http://tableless.com.br/uploads/2015/05/equals-com-objeto.bmp" alt="" width="456" height="238" />][1]

O resultado será falso, pois as classes, apesar de terem os mesmos atributos e métodos, a referência é diferente, como eu disse mas acima, para descobrir se as referências são iguais, deve-se utilizar “ == ”.

O equals também poderá ser utilizado para a comparação de Strings:

[<img class=" wp-image-48939 size-full aligncenter" src="http://tableless.com.br/uploads/2015/05/equals-com-string.bmp" alt="" width="527" height="201" />][2]

Nesse caso, a primeira instrução irá gerar uma resposta false, pois não estamos utilizando o método equalsIgnoreCase, que ignora as letras maiúsculas e minúsculas, portanto, a segunda instrução irá gerar uma resposta true.

## Operador Ternário

Esse código trata-se de um operador matemático, com um condicional. Em alguns casos, ambos podem ter comportamento um pouco diferente. Lembrando também que o ternário sempre deve retornar valor, e o valor será sempre do mesmo tipo, para ambos os lados da expressão.

[<img class=" size-full wp-image-48941 aligncenter" src="http://tableless.com.br/uploads/2015/05/if-ternario.bmp" alt="operador ternario" width="632" height="288" />][3]

Nesse caso, temos duas condições, essas duas condições são iguais, porém a de cima utiliza o operador ternário.

## SWITCH

A estrutura de decisão switch-case, ou simplesmente switch, é uma forma simples para se definir diversos desvios no código a partir de uma única variável ou expressão. Havendo uma variável com diversos valores possíveis e sendo necessário um tratamento específico para cada um deles, o uso da estrutura if-else se torna confuso e dificulta a leitura do código. Nesse caso, a clareza e a facilidade estão do lado da estrutura switch.

A sintaxe geral da estrutura switch é a seguinte:

[<img class=" size-full wp-image-48942 aligncenter" src="http://tableless.com.br/uploads/2015/05/switch.bmp" alt="switch" width="514" height="408" />][4]

Se for utilizada uma expressão, ela deve retornar um tipo de dados compatível com todos os valores especificados através das declarações case. Por dedução, todas as declarações devem conter valores de um mesmo tipo. Caso esteja utilizada uma variável, seu tipo também deve ser compatível com os valores das declarações.

Cada um dos valores especificados com as declarações case deve ser um valor literal exclusivo. Se houver algum valor duplicado, será gerado um erro no momento em que você tentar compilar seu código.

A palavra reservada break é utilizada na estrutura switch para promover um desvio da execução para a linha posterior ao final de seu bloco. Geralmente, ele é utilizado como a última instrução de cada declaração case.

A palavra default indica que caso nenhum dos cases seja utilizado, a instrução que se encontra no default será executada.

 [1]: http://tableless.com.br/uploads/2015/05/equals-com-objeto.bmp
 [2]: http://tableless.com.br/uploads/2015/05/equals-com-string.bmp
 [3]: http://tableless.com.br/uploads/2015/05/if-ternario.bmp
 [4]: http://tableless.com.br/uploads/2015/05/switch.bmp