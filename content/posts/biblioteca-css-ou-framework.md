---
title: Biblioteca CSS ou Framework?
author: Diego Eis
type: post
date: 2011-10-10
excerpt: 'O que é melhor utilizar: biblioteca de CSS ou um Framework?'
url: /biblioteca-css-ou-framework/
tweetbackscheck:
  - 1356390219
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4327";s:7:"tinyurl";s:26:"http://tinyurl.com/3atpckk";s:4:"isgd";s:19:"http://is.gd/bT0wGW";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503015394
categories:
  - Artigos
  - Código
  - HTML
tags:
  - 2011
  - biblioteca
  - CSS
  - desenvolvimento
  - desenvolvimento web
  - frameworks

---
Primeiro você precisa entender a diferença entre os dois. A [Talita Pagani][1] [em um dos seus artigos][2] descreve o que é um framework assim:

> Framework é um conjunto de componentes que provêm uma estrutura básica de elementos reutilizáveis, tendo uma arquitetura consistente de funcionalidade genérica sob a qual a aplicação será construída.

O uso de uma Biblioteca (CSS, Javascript, etc) é bastante parecido com a utilização de um framework. Eu prefiro a utilização de uma biblioteca por ser menos instrusiva e muito mais personalizável. Existem algumas diferenças que você deve prestar sua atenção para entender qual das duas formas é melhor para o projeto. 

### Modificação visual

Enquanto o framework modifica as características visuais, a biblioteca se restringe manipulando a diagramação ou a posição dos elementos. 

Na grande maioria, os frameworks modificam automaticamente o visual de alguns elementos, gerando um certo retrabalho, porque geralmente o design aplicado não é o design aprovado pelo cliente ou pelo designer do projeto. Veja por exemplo o [Bootstrap][3] feito pelo pessoal do Twitter. Assim que linkado em seu código, os elementos como os campos de formulários e parágrafos tem suas características visuais modificadas para seguir um design pré definido pelos donos do framework &#8211; diga-se de passagem, o trabalho de design feito pelo pessoal do Bootstrap é muito bacana. Já as bibliotecas, na maioria das vezes, não faz nenhuma modificação no design ou na posição dos elementos sem a inserção de Classe ou ID. Geralmente as bibliotecas são restritas para manipular a posição e as dimensões dos elementos, facilitando a diagramação de layouts, sem modificar as características visuais, já que os layouts de cada site tem o design diferente. É por isso que eu gosto de definir que frameworks são ótimos para construir sistemas, já as bibliotecas ajudam muito mais ao construir websites. Sistemas tem muitos formulários, botões de ação, pouco texto e etc. A utilização de um framework é muito interessante nesse caso porque não perdemos tempo manipulando e definindo um padrão visual para estes elementos &#8211; como os tamanhos dos campos de formulário de texto.

Já a biblioteca é muito útil para definir quando os elementos terão float, position, largura variável e etc. São características de posição e diagramação, que não afetam a questão do design. 

### Quantidade de código não utilizado

Geralmente ao utilizar uma biblioteca, talvez você estará linkando mais código do que o necessário para o seu projeto. Você pode não utilizar todas essas classes/ids pré definidos pelo autor da biblioteca, o que é normal dependendo do projeto e do design criado. Este risco diminui quando utilizamos frameworks, já que eles modificam as características de todos os elementos principais do projeto. Praticamente todo o código estará do framework estará sendo usado porque eles são aplicados nos elementos assim que o framework é linkado no código. Porém, com a biblioteca, é fácil mapearmos quais as classes utilizadas e excluir o código que não está sendo usado para diminuir o tamanho dos arquivos e do código.

### Personalização e criação

A personalização ou criação de uma biblioteca CSS é muito mais fácil do que se resolvermos criar do zero um framework. Você consegue facilmente criar uma biblioteca de CSS contendo algumas classes úteis para qualquer projeto, por exemplo:
  
[cc lang=&#8221;css&#8221;]
  
* {
    
margin:0;
    
padding:0;
  
}

.fLeft {float: left}
  
.fRight {float: right;}
  
.fNone {float: none;}

.dBlock {display: block;}
  
.dInline {display: inline;}
  
.dInlineBlock {display: inline-block;}
  
.dNone {display: none;}

.pAbsolute {position: absolute;}
  
.pRelative {position: relative;}

.cBoth {clear: both;}
  
.cLeft {clear: left;}
  
.cRight {clear: right;}
  
[/cc]

O código acima é um bom começo para uma biblioteca CSS personalizada. Contém ali classes básicas que se combinadas dão diferentes características para um determinado elemento. Essas classes também se mostram muito úteis se reutilizarmos no código javascript do projeto.

### Sistema e Site

Design de sistemas são sempre parecidos. Todos eles tem muitos campus de formulário, checkboxes, combos, radio buttons e etc. É basicamente manipulação de formulários, alertas de erro e mensagens para o usuário, manipulação de botões de ação e etc. Não foge muito disso.
  
Já o design de sites são todos bem diferentes. Por isso que a manipulação visual dos frameworks se torna inútil e gera muito retrabalho. 

Eu prefiro utilizar bibliotecas para a criação de sites. Para o desenvolvimento de sistemas, prefiro utilizar framworks.

Mas tenha em mente: se for decidir utilizar qualquer um dos dois, é bom que essa decisão seja feita logo no começo do projeto. Aplicar um framework no meio de um projeto pode dar muitos problemas e tomar muito tempo. Por isso é importante que essa decisão seja feita no início do projeto.

### Concluindo

Entenda que um framework pode ter uma biblioteca de CSS embutida em seu core. Tendo também a possibilidade de manipular o visual dos elementos, o framework se mostra muito mais completo que uma biblioteca CSS, embora a bilioteca ganhe por ser mais fácil de personalizar e por não manipular o visual dos elementos, te deixando livre para formatar da forma que você bem entender.

 [1]: http://tableless.com.br/?author=8
 [2]: http://bit.ly/qbkeRb
 [3]: http://twitter.github.com/bootstrap/