---
title: 'Estruturação de front-end – Parte 1: Preprocessadores, Framewoks e Bibliotecas'
author: Diego Eis
type: post
date: 2012-05-09
excerpt: Entenda a diferença entre preprocessadores, frameworks e bibliotecas de client-side. Saiba o que usar em seus projetos e quais as suas particularidades.
url: /estruturacao-de-client-side-preprocessadores-framewoks-e-bibliotecas-parte-1/
tweetbackscheck:
  - 1356453533
shorturls:
  - 'a:3:{s:9:"permalink";s:101:"http://tableless.com.br/estruturacao-de-client-side-preprocessadores-framewoks-e-bibliotecas-parte-1/";s:7:"tinyurl";s:26:"http://tinyurl.com/cmn7q57";s:4:"isgd";s:19:"http://is.gd/8dkHWG";}'
dsq_thread_id: 682660889
twittercomments:
  - 'a:14:{i:200399109390221312;s:7:"retweet";i:201014996631695360;s:7:"retweet";i:200514177591279616;s:7:"retweet";i:200412300379815936;s:7:"retweet";i:200406317574262784;s:7:"retweet";i:200379204490104834;s:7:"retweet";i:200289707714813953;s:7:"retweet";i:200271390815952896;s:7:"retweet";i:200271021058699264;s:7:"retweet";i:204618316403322880;s:7:"retweet";i:203535947080540161;s:7:"retweet";i:218776759678681088;s:7:"retweet";i:218752599552299009;s:7:"retweet";i:237612213156855808;s:7:"retweet";}'
tweetcount:
  - 52
categories:
  - Artigos
  - Código
  - CSS
  - CSS3
  - HTML
  - HTML5
  - JavaScript
  - JQuery
  - O Básico
  - Técnicas e Práticas
tags:
  - 2012
  - desenvolvimento web
  - Na Prática
  - tableless
  - tecnicascss
  - web standards

---
Existem três categorias de &#8220;ferramentas&#8221; que nos ajudam a desenvolver um projeto client-side: Preprocessadores, Frameworks e Bibliotecas.

### Preprocessadores

Preprocessadores são ferramentas onde você escreve CSS de uma determinada forma, modificando sua sintaxe, fazendo com que na hora de sua utilização o código CSS precise ser préprocessado para que o código escrito seja transformado em código CSS puro e assim então os browsers consigam entender.

Existem muitos preprocessadores no mercado como [Less][1], [Sass][2], [Turbine][3], [Switch CSS][4] e outros. 

Particularmente eu não gosto de usar preprocessadores. Para começar é necessário que você aprenda a linguagem de cada um e a ideia de que seu CSS precisa ser compilado para poder funcionar não me agrada muito. O CSS é simples demais para complicarmos desse jeito. Entretanto, há uma série de coisas interessantes que podemos fazer com os preprocessadores como variáveis, funções, operações e etc que demorarão um pouco (ou não) para fazerem parte do core definitivo da linguagem. Mesmo assim, pessoalmente, para a maioria dos projetos, não vale a pena.

### Frameworks

Frameworks são diferentes de preprocessadores mas são muito parecidos com Bibliotecas. Um Framework disponibiliza para o dev um conjunto de estilos e estruturas prontas para a utilização em projetos de forma escalável e uniforme. Normalmente os frameworks te dão uma coleção de componentes para que sejam usadas por todo o projeto. Esses componentes na maioria das vezes já vem com estilos visuais aplicados, bem como a estrutura. Veja por exemplo o [Bootstrap][5] ou o [Blueprint][6].

Com o Bootstrap você consegue, rapidamente, fazer um protótipo simples ou uma estrutura básica de sistema. É o preferido dos programadores. Os elementos visuais já foram criados e desenhados. Talvez não seja uma boa ideia você utilizar um framework em um projeto cujo design já esteja aprovado. Você teria muito retrabalho para &#8220;zerar&#8221; o estilo visual de cada elemento para depois reconstruí-lo utilizando o seu design.

É muito importante que o uso de um framework CSS/Javascript seja aprovado no início de um grande projeto. Mesmo que você planeje criar um framework do zero, específico para seu projeto. O que na maioria das vezes não vale a pena.

### Bibliotecas

Bibliotecas CSS geralmente não modificam o visual como os Frameworks fazem, mas eles disponibilizam uma coleção de classes, reutilizáveis e o melhor, combinatórias, para que se adeque a diversos cenários do seu projeto. Como essas classes não estão ligadas a nenhuma formatação visual, você consegue combinar sem grandes problemas com suas classes e IDs, modificando a hora que quiser a formatação visual dos elementos.

As bibliotecas são indicadas para projetos mais simples, sem grandes apetrechos técnicos, como um site ou algo parecido. Para fazer um sistema, as bibliotecas irão reforçar os Frameworks, facilitando a organização e formatação da estrutura do site. A biblioteca também ajuda na manipulação dos elementos via Javascript se baseando por estas classes prontas. 

A verdade é que hoje é muito difícil diferenciar uma biblioteca de um framework.

### Como todos eles trabalham juntos?

Você pode usar todos os três ao mesmo tempo em um projeto. Mas não é muito inteligente, já que se você estiver utilizando um framework, muito provavelmente ele terá uma &#8220;biblioteca&#8221; em sua base. Imagine que a biblioteca pode ser específica de estrutura ou formatação visual. O Framework, basicamente, junta os dois. Obviamente há mais coisas envolvidas. Mas para simplificarmos a explicação, imagine que um Framework é a mistura dessas duas bibliotecas.

O Preprocessador é independente do Framework e da Biblioteca. O seu ganho está ao escrever um código mais escalável, muitas vezes melhorando ou piorando a sintaxe do código. É pura sintaxe, não são classes prédefinidas. Mesmo assim você pode basear seu Framework/Biblioteca em um Préprocessador. O Bootstrap faz isso para facilitar features dinâmicas como grids, cores e etc.

Como eu disse, eu não gosto de misturar as coisas. Prefiro utilizar o Bootstrap puro, sem a interferência de nenhum préprocessador. Mas, há gosto para tudo. 😉

### Qual deles é melhor para o meu projeto

Eu não sugiro que você utilize um framework para criar websites institucionais. Websites geralmente não usam os mesmos elementos, nem as mesmas estruturas, nem o mesmo design. Logo, se você utilizasse um framework como o Bootstrap, ou o JQuery UI, você acabaria gastando mais tempo reestilizando e brigando com o CSS já criado dos frameworks do que fazendo o que realmente importa: o seu trabalho.
  
Logo, para projetos de pequeno porte eu sugiro que você utilize uma biblioteca simples. Sugiro ainda que essa biblioteca seja criada por você.

Não precisa de muito. Em uma biblioteca você só precisa ter algumas propriedades que fazem tarefas básicas, como fazer o elemento flutuar para a esquerda, para direita, clear, retirar margens e etc. Normalmente eu utilizo um reset chamado [Normalize][7]. Ele já reseta meu CSS inteiro e então eu me foco apenas nas propriedades que eu reutilizarei no resto do projeto.

Se seu projeto for médio ou grande, você já pode pensar em utilizar um Framework. Principalmente se seu projeto for um sistema. Você já vai ter à disposição estilos para formulários (que são um saco pra fazer), botões, grids, reset CSS e outras coisas. O trabalho fica mais fácil por que você tem menos arestas para acertar. Ainda mais se o designer aceitar utilizar alguns dos estilos já prontos do Framework, assim você não precisa reconfigurar formatações visuais e etc.

A utilização do Preprocessadores é totalmente opcional. Mas se você decidir utilizá-lo juntamente com algum Framework, procure saber se o Framework escolhido suporta algum tipo de préprocessador. O Bootstrap, por exemplo, tem uma versão para LESS.

No próximo artigo vou contar como estamos fazendo aqui na Locaweb. Estamos criando uma grande biblioteca visual e de front-end que será utilizado por todos os serviços. Os programadores conseguem subir um sistema sem precisar esperar um código HTML definitivo, utilizando os módulos dessa biblioteca. A galera de design faz todos os layouts padronizados visualmente, garantindo a uniformidade de todos os sistemas. E o pessoal de front? Bom o pessoal de front cuida para que tudo isso funcione. 😉

Veja a segunda parte deste artigo: [Designers e Programadores][8]

 [1]: http://lesscss.org/
 [2]: http://sass-lang.com/
 [3]: http://turbine.peterkroener.de/index.php
 [4]: http://sourceforge.net/projects/switchcss/
 [5]: http://twitter.github.com/bootstrap
 [6]: http://blueprintcss.org
 [7]: http://necolas.github.com/normalize.css/
 [8]: http://tableless.com.br/estruturacao-de-client-side-designers-e-programadores-parte-2/ "Estruturação de Client-side – Parte 2: Designers e Programadores"