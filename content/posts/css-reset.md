---
title: CSS Reset
author: Diego Eis
type: post
date: 2007-09-13
url: /css-reset/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356387085
shorturls:
  - 'a:3:{s:9:"permalink";s:33:"http://tableless.com.br/css-reset";s:7:"tinyurl";s:26:"http://tinyurl.com/3uolg4b";s:4:"isgd";s:19:"http://is.gd/x7KX3h";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503027891
categories:
  - Artigos
  - Código
  - CSS
  - O Básico
tags:
  - Na Prática

---
Sempre que começo a escrever meu CSS, eu inicio colocando um * (asterísco) e zero algumas propriedades. Esse técnica se chama CSS Reset.

Alguns elementos do HTML já tem um valor de margin, padding, borda e outros tipos de formatação definidos como padrão. O que acontece é que esses valores pré-definidos são necessários para que quando o site seja visto sem CSS algum, o usuário conseguirá ter um mínimo de legibilidade na visita.
  
Quando você vai implementar o CSS, esses valores atrapalham um bocado. Por isso, usamos essa técnica para zerar todas esses valores pré-definidos e inserir os valores que realmente usaremos para reproduzir o layout.

O asterísco é um seletor de CSS. Muito útil por sinal. A função dele é simples: selecionar todos os elementos.
  
`div#geral #texto * {<br />
  color:red;<br />
}`
  
Neste caso, o asterísco irá &#8220;selecionar&#8221; todos os elementos que estão dentro do objeto **#texto** que está dentro do **div #geral**. Não importa quais elementos eles sejam, o ***** captura todos.
  
Infelizmente, não funciona no IE6.

Eu reseto meu CSS desta maneira:
  
`* {<br />
margin:0;<br />
padding:0;<br />
list-style:none;<br />
vertical-align:baseline;<br />
}`
  
Não se preocupe, usar o asterísco sozinho no seletor funciona em todos os browsers.

Se você tiver a necessidade de zerar mais propriedades, fique à vontade. O [Eric Meyer][1] já é mais violento e [faz um reset geral em seu CSS][2], note que ele não usou asterísco.
  
Não acho necessário tanta coisa. Mas isso vai da maneira de trabalho de cada um. O código que mostrei aqui é simples resolve meus problemas e é isso que importa. Você vai adaptá-lo com sua maneira de desenvolvimento.

 [1]: http://meyerweb.com/eric/
 [2]: http://meyerweb.com/eric/thoughts/2007/05/01/reset-reloaded/