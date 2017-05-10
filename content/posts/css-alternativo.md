---
title: CSS alternativo
author: Diego Eis
type: post
date: 2006-04-14
url: /css-alternativo/
tweetbackscheck:
  - 1356140387
shorturls:
  - 'a:3:{s:9:"permalink";s:39:"http://tableless.com.br/css-alternativo";s:7:"tinyurl";s:26:"http://tinyurl.com/3r4w434";s:4:"isgd";s:19:"http://is.gd/1eaKVl";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503035218
categories:
  - Artigos
  - Geral
tags:
  - cotidiano
  - Técnicas e Práticas

---
Para oferecer um CSS alternativo para sua página é muito fácil, e você nem precisa de fazer um style switcher para funcionar.

Para importar um CSS na página, geralmente usamos a tag link assim:

`<link rel="stylesheet" type="text/css" href="css1.css"   />`

Até aqui nada de sensacional. Agora vem o segredo (nem tão segredo assim): para servir outro CSS, você vai simplesmente duplicar esta linha com uma pequena diferença: no atributo &#8220;rel&#8221; você mudará o valor para &#8220;alternate stylesheet&#8221;, isto indicará que aquele CSS importado será alternativo, secundário. Ficará assim:
  
``Para oferecer um CSS alternativo para sua página é muito fácil, e você nem precisa de fazer um style switcher para funcionar.

Para importar um CSS na página, geralmente usamos a tag link assim:

`<link rel="stylesheet" type="text/css" href="css1.css"   />`

Até aqui nada de sensacional. Agora vem o segredo (nem tão segredo assim): para servir outro CSS, você vai simplesmente duplicar esta linha com uma pequena diferença: no atributo &#8220;rel&#8221; você mudará o valor para &#8220;alternate stylesheet&#8221;, isto indicará que aquele CSS importado será alternativo, secundário. Ficará assim:
  
`` 

Muito fácil né? Mas como alternamos estes estilos?
  
Normalmente você faria um Style Switcher simples, que faz guardar no cache a opção do camarada e tudo mais.
  
Mas, se você não ligar muito para isso, os browsers bons como Firefox e Opera detectam automaticamente seus estilos alternativos e mostram as opções para escolha.

No Firefox, você faz assim: Exibir > Estilos da Página > Escolha o estilo desejado
  
No Opera: View > Style > Escolher estilo

Para fazer um teste, lembram daquele [video tutorial que fiz sobre a implementação do CSS do layout da Visie][1]?
  
Bom, esses dias mudamos o layout do site, eu reaproveitei a estrutura XHTML e refiz apenas o CSS. Ótima experiência&#8230; Pena que só lembrei de fazer um Video Tutorial depois que eu terminei, aí já era tarde. 🙁

Coloquei o CSS antigo como alternativo. Visite a [página][2] e tente alternar os estilos da página com os navegadores.

Fácil não é?
  
Mas é bem mais legal quando você faz um script decente, que guarda a opção no cache e tudo mais. Fica mais interativo.

 [1]: http://tableless.com.br/video-tutorial-9-criando-a-home-da-visie-css
 [2]: http://visie.com.br/