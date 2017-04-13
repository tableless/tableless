---
title: JAVA – Estruturas de Repetição
author: Fellipe Filgueiras
type: post
date: 2015-06-10
url: /java-estruturas-de-repeticao/
categories:
  - Back-end
  - Java
tags:
  - java

---
As estruturas de repetição também são conhecidas como laços (loops) e são utilizados para executar, repetidamente, uma instrução ou bloco de instrução enquanto determinada condição estiver sendo satisfeita.

Qualquer que seja a estrutura de repetição, ela contém quatro elementos fundamentais: inicialização, condição, corpo e iteração. A inicialização compõe-se de todo código que determina a condição inicial da repetição. A condição é uma expressão booleana avaliada após cada leitura do corpo e determina se uma nova leitura deve ser feita ou se a estrutura de repetição deve ser encerrada. O corpo compõe-se de todas as instruções que são executadas repetidamente. A iteração é a instrução que deve ser executada depois do corpo e antes de uma nova repetição.

## While

O termo while pode ser traduzido para o português como “enquanto”. Este termo é utilizado para construir uma estrutura de repetição que executa, repetidamente, uma única instrução ou um bloco delas “enquanto” uma expressão booleana for verdadeira.

Veja que a inicialização precede o início da repetição. Isso significa que você deve definir o estado inicial dos elementos que serão utilizados nesse laço antes de seu cabeçalho. A palavra reservada while sempre será seguida de um par de parênteses, que delimitam a condição desta estrutura de repetição. Essa condição deve ser uma expressão booleana e, enquanto ela for verdadeira, esta estrutura continuará executando as instruções contidas no seu corpo.

[<img class=" size-full wp-image-49309 aligncenter" src="http://tableless.com.br/uploads/2015/06/while.bmp" alt="while" width="599" height="225" />][1]

## Do-while

A estrutura de repetição do-while é uma variação da estrutura while. Existe uma diferença sutil, porém importante, entre elas. Em um laço while, a condição é testada antes da primeira execução das instruções que compõem seu corpo. Desse modo, se a condição for falsa na primeira vez em que for avaliada, as instrução desse laço não serão executadas nenhuma vez. Em um laço do-while, por outro lado, a condição somente é avaliada depois que suas instruções são executadas pela primeira vez, assim, mesmo que a condição desse laço seja falsa antes de ele iniciar, suas instruções serão executadas pelo menos uma vez.

[<img class=" size-full wp-image-49310 aligncenter" src="http://tableless.com.br/uploads/2015/06/do-while.bmp" alt="do-while" width="612" height="240" />][2]

## Estrutura For

O laço for é uma estrutura de repetição compacta. Seus elementos de inicialização, condição e iteração são reunidos na forma de um cabeçalho e o corpo é disposto em seguida.

Veja a sintaxe geral de uma estrutura for:

Observe que a inicialização, condição e iteração aparecem, entre parênteses, após a palavra reservada “for” e elas são separadas apenas por um ponto-e-vírgula. A instrução ou bloco de instruções que este tipo de laço repete são transcritos a partir da linha subsequente ao seu cabeçalho.

O laço for e o laço while são apenas formas diferentes de uma mesma estrutura básica de repetição. Qualquer laço for pode ser transcrito em termos de um laço while e vice-versa. Do mesmo modo que em um laço while, se a condição de um laço for já é falsa logo na primeira avaliação que se fizer dela, as instruções contidas em seu corpo jamais serão executadas.

[<img class=" size-full wp-image-49311 aligncenter" src="http://tableless.com.br/uploads/2015/06/for.bmp" alt="for" width="459" height="157" />][3]

## Quebras de Laço

As quebras de laço são utilizadas para interromper o fluxo normal das estruturas de repetição while, do-while e for. Há dois tipos distintos de quebras de laço, representadas pelas palavras reservadas break e continue.

Há situações em que é preciso interromper um laço antes que sua condição se torne falsa. É para isso que serve o break. Figurando dentro do bloco de instruções de um laço qualquer, essa instrução encerra a estrutura de repetição, desviando a execução do aplicativo para a linha seguinte ao final desse laço.

Enquanto a instrução break é utilizada para encerrar um laço, a instrução continue serve para iniciar uma nova repetição em que todas as instruções tenham sido executadas. Em laços while e do-while, uma instrução continue desvia o fluxo de execução para a condição. Em um laço for, ela desvia o fluxo de execução para a iteração e, em seguida, a condição é lida novamente.

## Enhanced-for

O enhanced-for foi introduzido a partir do&nbsp;Java 5, e é utilizado para realizar as varreduras em collections. Para cada iteração do for, o elemento da iteração é atribuído à variável. Utilizando o enhanced-for, você é obrigado a percorrer um array por exemplo.

[<img class=" size-full wp-image-49312 aligncenter" src="http://tableless.com.br/uploads/2015/06/enhanced-for.bmp" alt="enhanced-for" width="410" height="204" />][4]

Bom galera, essa foi uma passada rápida pelas estruturas de repetição que o java oferece, sugestões e críticas serão sempre bem recebidas, obrigado.

&nbsp;

 [1]: http://tableless.com.br/uploads/2015/06/while.bmp
 [2]: http://tableless.com.br/uploads/2015/06/do-while.bmp
 [3]: http://tableless.com.br/uploads/2015/06/for.bmp
 [4]: http://tableless.com.br/uploads/2015/06/enhanced-for.bmp