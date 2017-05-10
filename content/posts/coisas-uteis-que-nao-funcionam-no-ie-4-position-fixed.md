---
title: 'Coisas úteis que não funcionam no IE #4 – Position Fixed'
author: Diego Eis
type: post
date: 2007-01-22
url: /coisas-uteis-que-nao-funcionam-no-ie-4-position-fixed/
tweetbackscheck:
  - 1355690746
shorturls:
  - 'a:3:{s:9:"permalink";s:77:"http://tableless.com.br/coisas-uteis-que-nao-funcionam-no-ie-4-position-fixed";s:7:"tinyurl";s:26:"http://tinyurl.com/3u8rfrv";s:4:"isgd";s:19:"http://is.gd/sbzce4";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036557
categories:
  - Tecnologia e Tendências
tags:
  - Técnicas e Práticas

---
Há na propriedade &#8216;position&#8217; do CSS um valor chamado &#8216;fixed&#8217;. Quando usado, este valor determina que o elemento deve ficar fixo na posição que você mandar, e quando a barra de rolagem é movida, este elemento fica fixado na posição que você definiu. Veja o código:

<code id="line1">body{margin:0; padding:0;}</code>

div {
  
position:fixed;
  
top:10px;
  
left:10px;
  
width:150px;
  
height:200px:
  
border:1px solid black;
  
background:#CCC;
  
}
  
[Resultado do código acima, sem funcionar no IE.][1]

Eu apenas defini um position: fixed; para o DIV. Quando a rolagem é ativada o elemento fica fixado na posição que você definiu.

Só que isso não funciona no IE. Pelo menos por vias normais. Há uma maneira para fazer isso funcionar no IE. Para tanto usaremos [CSS HACKS][2]. Já digo que essa é uma daquelas soluções que não há explicação. Simplesmente funciona e pronto. [Eu vi essa solução aqui][3].

Para o IE, você vai usar o seguinte código:
  
`Há na propriedade &#8216;position&#8217; do CSS um valor chamado &#8216;fixed&#8217;. Quando usado, este valor determina que o elemento deve ficar fixo na posição que você mandar, e quando a barra de rolagem é movida, este elemento fica fixado na posição que você definiu. Veja o código:

<code id="line1">body{margin:0; padding:0;}</code>

div {
  
position:fixed;
  
top:10px;
  
left:10px;
  
width:150px;
  
height:200px:
  
border:1px solid black;
  
background:#CCC;
  
}
  
[Resultado do código acima, sem funcionar no IE.][1]

Eu apenas defini um position: fixed; para o DIV. Quando a rolagem é ativada o elemento fica fixado na posição que você definiu.

Só que isso não funciona no IE. Pelo menos por vias normais. Há uma maneira para fazer isso funcionar no IE. Para tanto usaremos [CSS HACKS][2]. Já digo que essa é uma daquelas soluções que não há explicação. Simplesmente funciona e pronto. [Eu vi essa solução aqui][3].

Para o IE, você vai usar o seguinte código:
  
` 

[Olha como ficou!][4]

Sim, o código não vai validar, mas você pode escolher outro hack que passe no validador.

 [1]: http://tableless.com.br/estudo/positionfixed/semie.html
 [2]: http://tableless.com.br/csshacks
 [3]: http://home.tampabay.rr.com/bmerkey/examples/fake-position-fixed.html
 [4]: http://tableless.com.br/estudo/positionfixed/ie.html