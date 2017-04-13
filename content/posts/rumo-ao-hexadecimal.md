---
title: Rumo ao hexa(decimal)
author: Guilherme Buchalla
type: post
date: 2015-06-22
url: /rumo-ao-hexadecimal/
categories:
  - CSS
  - Design
  - O Básico
tags:
  - cor
  - CSS
  - hexadecimal
  - matemática

---
Quantas vezes na sua vida você já se deparou com um código hexadecimal? A gente sabe que seu Command-C tá em um relacionamento sério com ele. Mas afinal, como que um punhado de letras e números representam essa tralharada de cores (ou o que quer que seja) que nós vemos por aí nos dispositivos digitais?

Existe um artigo ótimo no Tableless explicando tudo o que você precisa saber sobre cor <a href="http://tableless.com.br/sobre-cor-e-webdesign/" target="_blank">aqui</a>. Sério, vai lá, mas depois volta aqui.

O hexadecimal é um sistema com base 16. Não ajudou em nada? Então vamos voltar para os tempos de escola e relembrar como funciona o sistema decimal que utilizamos todos os dias. Caso você se perguntou “mas por que o decimal?”. Porque nós temos dez dedos e fica relativamente fácil de realizar os cálculos. Foi o que os hindus disseram lá pelo ano 400 AC.

Se eu lhe mostrar qualquer número, tenho certeza que você consegue identificar num piscar de olhos. O número **2015, **por exemplo. Você não teve nenhum esforço e leu “na sua cabeça” _dois mil e quinze_, certo? Legal. Vamos esmiuçar como chegamos a essa conclusão. O sistema decimal trabalha com base 10. De novo esse negócio de base? Vamos lá:

**Sistema decimal:** 

Como sugere o nome, esse sistema trabalha com 10 símbolos: 0, 1, 2, 3, 4, 5, 6, 7, 8 e 9.

Você provavelmente tem em sua memória lembranças de alguns conceitos como: unidade, dezena, centena e milhar.

<img class="aligncenter wp-image-49638 size-full" src="http://tableless.com.br/uploads/2015/06/unidade.jpg" alt="valor decimal" width="229" height="69" />

Cada algarismo possui a base 10 elevada a uma potência de valor crescente, começando em zero da direita pra esquerda. Vemos que o primeiro algarismo posicionado à direita é a representação da unidade. A base é 10 e a potência é 0. Qualquer número elevado a zero o resultado é 1. Como eu sei que você sabe trabalhar com potências, não vou ficar explicando o que é dez ao quadrado, certo?

<img class="aligncenter size-full wp-image-49645" src="http://tableless.com.br/uploads/2015/06/101.jpg" alt="base dez" width="227" height="105" />

Agora é só multiplicar o resultado da base com o algarismo em questão. Voltando ao exemplo da unidade, temos o seguinte: 1 x 5 = 5. A lógica se aplica para todos os outros.

[<img class=" size-full wp-image-49622 aligncenter" src="http://tableless.com.br/uploads/2015/06/10-resultado.jpg" alt="sistema decimal" width="215" height="235" />][1]

Olha lá o número em que nós chegamos somando todos os resultados: 5 + 10 + 0 + 2000 = 2015. Bacana, né? Então vamos para o próximo.

Antes de chegar no sistema hexadecimal temos que passar pelo sistema binário. Mas já que recapitulamos o sistema decimal, vai ser facinho entender o binário, fique tranquilo.

Não tenho dúvidas que você já ouviu o termo bit. Até porque você está lendo esse artigo através da web e teve que contratar um serviço de internet para isso, seja ele qual for. Vamos supor que tenha sido um que forneça a velocidade de download de 30Mbps. Tá vendo esse “b” aí no meio? Ele significa bit, no caso: 30 Mega bits por segundo, quando falamos de bit o “b” é em caixa baixa. Caso você ache que escreveu errado a vida toda, até porque se você fala para alguém que seu arquivo tem 30MB, não está errado. Você está se referindo a 30 Mega Bytes, aí sim o “B” é em caixa alta.

Quer dizer que se eu tenho uma velocidade de 30Mbps eu consigo baixar um arquivo de 30MB em 1 segundo? Calma lá, já vamos chegar nisso.

**Sistema Binário:** 

O significado de bit é **Bi**nary Digi**t** (Dígito Binário), serve para medir dados de informação computacional. Utilizado em computadores por causa dos transistores, que são reunidos em circuitos e possibilitaram a criação de micro computadores, que substituíram aqueles que ocupavam uma casa inteira, literalmente. Os transistores controlam o fluxo de corrente elétrica, podendo estar ligados **ou** desligados, quer dizer, passando corrente elétrica ou não, sendo assim, duas opções. Já que são duas opções, utilizamos o sistema **bi**nário.

Quer dizer que o computador que está na minha mesa, o tablet que está na minha mochila e o celular que está no meu bolso são compostos por transistores? Sim, aliás, um monte deles.

Para que não pareça muito confuso, vamos associar o transistor a uma lâmpada. Se não há passagem de corrente elétrica a lâmpada está desligada, se há, ela está ligada. No sistema binário a lâmpada é um bit e a representação do “desligado” é o dígito **0** e do “ligado” o **1**.

<img class="aligncenter size-full wp-image-49630" src="http://tableless.com.br/uploads/2015/06/lampada_animada.gif" alt="lâmpada representando um bit" width="104" height="236" />

O que temos de informação nos computadores são combinações desses dois dígitos. Cada caractere que eu escrevo agora, por exemplo, contém alguns bits para ser armazenado. Os bits são colocados em grupos de oito e são chamados de Byte.

<img class="aligncenter size-full wp-image-49621" src="http://tableless.com.br/uploads/2015/06/8bits1byte.jpg" alt="ilustração de lâmpadas representando um bit" width="579" height="165" />

Vamos voltar à história da conexão de internet de 30Mbps. O que queremos saber é quantos Bytes, e não bits por segundo nossa conexão realiza o download de arquivos. Para isso basta dividir por 8. No caso: 30/8 = 3.75. Com uma conexão de 30Mb por segundo conseguimos baixar no máximo até 3.75MB por segundo. Claro que esse número varia por n fatores externos. Ficando claro que não conseguiríamos baixar o arquivo de 30MB em apenas 1 segundo.

Vimos que no sistema **dec**imal a base é 10, aqui no sistema **bi**nário a base é 2. A lógica é a mesma.

<img class="aligncenter size-full wp-image-49620" src="http://tableless.com.br/uploads/2015/06/2.jpg" alt="valores da base dois" width="384" height="49" />

Com o tempo você acaba decorando esses valores. Assim como fizemos com o sistema decimal, vamos esmiuçar também o sistema binário. Nesse exemplo, vamos realizar a conversão de um número no sistema binário para o sistema decimal.

<img class="aligncenter size-full wp-image-49623" src="http://tableless.com.br/uploads/2015/06/binario-decimal.jpg" alt="conversão de binário para decimal" width="512" height="193" />

Legal, né? O número 01011010 em binário é o número 90 em decimal. Vamos fazer o processo inverso agora, converter o número decimal 90 para o sistema binário. Para isso, nós vamos realizar divisões sequenciais sendo que o divisor é o 2, por causa da base 2.

<img class="aligncenter size-full wp-image-49627" src="http://tableless.com.br/uploads/2015/06/divisoes-sequenciais.jpg" alt="converter decimal com divisões sequenciais" width="322" height="235" />

Quando o resto for 0 ou 1 nós paramos por aí. Repare que nessas divisões não nos interessam as casas decimais. Quando chegamos ao quociente 1, nós paramos a divisão. A leitura do número binário gerado pelas divisões é da direita pra esquerda, e o valor que atingimos foi: 1011010. Se você observou atentamente, viu que nosso número binário está com apenas 7 dígitos, porque o número decimal 90 apenas requer 7 bits para ser armazenado. Não se incomode, se quiser representá-lo como 8 bits basta colocar um 0 à esquerda dele, resultando em: **01011010**.

Ah, mas eu não gosto de fazer conta. Tudo bem, vamos fazer uma abordagem mais lúdica. Vamos supor que nós temos 90 dinheiros, uma moeda que eu inventei, representado em apenas uma cédula. O que gera uma dificuldade imensa para jogar no fliper, já que precisamos de trocado. Vamos na padaria e pedimos para que o atendente troque esses 90 dinheiros em cédula por 90 dinheiros em moedas.

<img class="aligncenter size-full wp-image-49626" src="http://tableless.com.br/uploads/2015/06/dinheiro.jpg" alt="ilustração das moedas e cédula" width="475" height="119" />

Claro que ele não vai te dar uma moeda de 128 dinheiros, até porque é muito mais do que os 90 dinheiros em cédula que temos. Na nossa conversão binária a moeda 128 não vai ser utilizada e a representamos com o dígito 0. E a moeda 64, podemos utilizá-la? Claro, qualquer valor em moeda que seja igual ou menor do que o valor em cédula. Se utilizamos a moeda de 64, no binário atribuímos o dígito 1. A lógica se repete para o resto da conta, sendo:

<img class="aligncenter size-full wp-image-49625" src="http://tableless.com.br/uploads/2015/06/dinheiro-conta.jpg" alt="tabela com cédula e valores em moedas" width="340" height="566" />

Como já acabamos de trocar nosso dinheiro e não vamos utilizar a moeda de valor 1 colocamos o valor 0 no binário.

<img class="aligncenter size-full wp-image-49624" src="http://tableless.com.br/uploads/2015/06/dinheiro-binario.jpg" alt="decimal para binário ilustrado" width="505" height="207" />

Se você está se perguntando qual o valor máximo que conseguimos armazenar em 8 bits, aí vai: 11111111 (já que queremos o valor máximo, todos os bits tem que estar ligados), agora é só somar todos os valores dos número elevados: 1 + 2 + 4 + 8 + 16 + 32 + 64 + 128 = 255.

Acrescentamos o número zero nas possibilidades, resultando 256 (0 a 255) variações de cor, por exemplo.

Se você leu o artigo recomendado no começo do post, já deve saber que os dispositivos digitais trabalham com o sistema de cor RGB, consistindo basicamente em uma emissão de três luzes diferentes, que quando combinadas em valores específicos configuramos a cor desejada. O zero representa total ausência de luz. Temos níveis intermediários e, por fim, chegamos na emissão máxima de luz com o valor 255.

O sistema RGB significa: Red (vermelho), Green (verde) e Blue (azul). São as cores primárias que juntas no sistema aditivo trabalham melhor no ambiente digital.

Em praticamente qualquer software de computação gráfica você vai encontrar uma paleta de cores. Nela você terá alguma coisa similar a isso:

<img class="aligncenter size-full wp-image-49632" src="http://tableless.com.br/uploads/2015/06/rgb.jpg" alt="paleta rgb" width="320" height="71" />

Dá pra ver como as coisas começam a se encaixar? OIha aí novamente os valores 0 e 255. Quer dizer, sabemos que 0 a 255 (256) é a capacidade de armazenamento de 8 bits (1 Byte). Se temos o valor zero, não temos emissão de luz do canal de cor específico. Se os três canais de cor estiverem em zero, sabemos que no sistema digital é a representação da cor preta, porque nenhum canal está emitindo luz.

Com a adição máxima de todos os canais de cor (todos em 255) temos a cor branca, a cor luz como é chamada no sistema RGB. Como deve ter imaginado, para saber quantas cores o sistema RGB suporta é só multiplicar pela quantidade de canais: 256 x 256 x 256 = 16.777.216. Quer dizer que imagens de 8bpc (8 bits por canal) tem tudo isso aí de cor, em qualquer dispositivo digital.

Se você é daqueles que gosta de saber sempre o porquê das coisas, tenho uma coisa simples e interessante pra te falar. Uma imagem digital bitmap é composta por pixels (menor unidade gráfica, como se fossem tijolos que compõem as paredes da sua casa), até aí tranquilo. Como vimos, as combinações dos três canais formam as cores que nós desejamos. Numa imagem digital é como se tivéssemos três folhas vegetais sobrepostas, cada folha representando um canal de cor. Vamos supor que esse pixel aí embaixo seja um dos vários que compõem uma imagem qualquer:

<img class="aligncenter size-full wp-image-49631" src="http://tableless.com.br/uploads/2015/06/pixel.jpg" alt="pixel e valores em seus canais" width="204" height="196" />

Pra compor a cor laranja desse único pixel, em cada canal de cor teremos variações de valores para que quando combinadas formem essa informação. Como cada canal tem 8 bits e temos três canais, fica claro o porquê que chamamos de imagens de 24 bits. E também agora é nítido que precisamos de 3 Bytes para armazenar as informações de um pixel só.

Se nossa imagem tiver a dimensão de 600&#215;400, endende-se que temos 600 pixels de largura e 400 pixels de altura, totalizando 240.000 pixels. Como cada um deles utiliza 3 Bytes para ser armazenado, fazemos a multiplicação: 240.000 x 3 = 720.000 Bytes. Agora, ninguém vai chegar numa reunião e falar que a imagem do projeto tem 720.000 Bytes, né? Bom, 1024 Bytes (2 elevado a 10ª potência) equivale a 1 Kilobyte. Dividindo 720.000 por 1024 temos o valor em KB: 720.000 / 1024 = 703,1 KB.

Como já conhecemos o sistema binário podemos finalmente trabalhar com o sistema hexadecimal.

Como vimos até agora, o sistema decimal trabalha com a base 10 e o sistema binário com a base 2. Para esses dois sistemas, já está claro o porquê.

O sistema hexadecimal utiliza a base 16, agora vamos ver do que se trata.

**Sistema hexadecimal**

Amiiigo, você tá cansado de ouvir o Galvão falar de hexa, e sabe que significa seis. Nesse caso, são seis as letras utilizadas: A a F. O decimal você já sabe que são dez símbolos: 0 a 9. Isso mesmo o que você pensou: 6 + 10 = 16.

Não se assuste achando temos algo complicado pela frente, na verdade muito pelo contrário. O sistema hexadecimal veio pra facilitar a utilização do que já conhecemos, o sistema binário.

Como sabemos que toda estrutura computacional dos sistemas utiliza código binário para representar suas informações, utilizamos o sistema hexadecimal justamente para compactar esse código binário e facilitar sua aplicação no dia a dia.

Cada símbolo em hexadecimal consegue representar quatro dígitos no sistema binário, o que seria 4 bits. A tabela abaixo mostra a representação de mesmos valores em sistemas diferentes.

<img class="aligncenter size-full wp-image-49639" src="http://tableless.com.br/uploads/2015/06/tabela.jpg" alt="tabela decimal, binário e hexadecimal" width="473" height="621" />

Por enquanto não parece fazer muito sentido apenas olhando essa tabela, mas com certeza você está acostumado com o tripleto hexadecimal. Sabe aquele carinha que você copia do Photoshop e cola no seu CSS? Então, é o tripleto. Como foi explicado acima, um símbolo no sistema hexadecimal armazena 4 bits de informação. Porém, já vimos também que a cor no sistema digital utiliza 8 bits por canal. Então vamos lá: 4 + 4 = 8. Consequentemente para representar um canal de cor do sistema digital precisamos de dois símbolos em hexadecimal. Como sabemos que temos três canais de cor, precisamos exatamente do que você pensou: tripleto hexadecimal. Coloquei abaixo o código hexadecimal que representa a cor branca, só por já estarem acostumados com ele.

<img class="aligncenter size-full wp-image-49633" src="http://tableless.com.br/uploads/2015/06/tripleto.jpg" alt="tripleto hexadecimal" width="361" height="145" />

Bom, não precisa nem pensar pra saber quanto que esse código hexadecimal vale em binário, é só bater o olho na tabela, mas de qualquer forma, vamos lá:

[<img class=" wp-image-49692 size-full aligncenter" src="http://tableless.com.br/uploads/2015/06/hexa-binario.jpg" alt="" width="505" height="209" />][2]

Nós já aprendemos a converter do sistema binário para o decimal, mas de qualquer forma vamos finalizar:

<img class="aligncenter size-full wp-image-49628" src="http://tableless.com.br/uploads/2015/06/final.jpg" alt="conversão binário para decimal" width="512" height="192" />

Agora vai lá no Photoshop e coloca na paleta de cor o valor 255 em cada canal: R, G e B. O resultado é a cor branca, que já sabemos o porquê. O hexadecimal é o tal do #FFFFFF.

O único detalhe que temos que prestar atenção é que se pegarmos um valor hexadecimal, como por exemplo o 5, na tabela vemos que em binário ele vale 101, isso porque apenas 3 bits são necessários para representá-lo. Para fazer a conversão, cada valor hexadecimal tem que ser representado em 4 bits. No caso do valor hexadecimal 5 é só acrescentar um 0 antes de tudo, então ao invés de deixar 101, deixamos ****101. Sempre preenchemos com zero à esquerda e não à direita.

Se está acostumado a escrever seu código hexadecimal dessa forma no seu CSS: #FFF, não tem problema. Na verdade isso é a abreviação do tripleto hexadecimal. Quando os valores de cada canal são iguais, podemos abreviá-lo.

Pronto! Agora faça um teste você mesmo com as conversões. 🙂

 [1]: http://tableless.com.br/uploads/2015/06/10-resultado.jpg
 [2]: http://tableless.com.br/uploads/2015/06/hexa-binario.jpg