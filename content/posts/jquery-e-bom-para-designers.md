---
title: jQuery é bom para designers
author: Michael Granados
type: post
date: 2008-08-05
url: /jquery-e-bom-para-designers/
aktt_tweeted:
  - 1
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356204785
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/jquery-e-bom-para-designers";s:4:"isgd";s:19:"http://is.gd/xpGS0V";s:7:"tinyurl";s:26:"http://tinyurl.com/4y4oo7d";}'
twittercomments:
  - 'a:1:{i:216197732229066753;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503038371
categories:
  - JQuery
tags:
  - criação
  - JavaScript
  - JQuery
  - menu
  - padroes
  - programação
  - script
  - slide
  - solução
  - submenu
  - tableless
  - tutorial

---
No começo da web JavaScript era considerado uma linguagem de programação completamente difícil e inútil. Afinal, depois de uma semana estudando a linguagem, o sujeito só conseguia escrever um script que validasse um formulário de contato que muitas vezes dava erro em outros browsers que não o Internet Explorer. Isso acontecia porque tanto o Netscape quanto o Browser azul tinha seus prórpios padrões de implementações de solução para o Javascript que era ainda estava engatinhando como linguagem.

<!--more-->

Dessa forma, muitos códigos proprietários solucionavam problemas em determinado browser, que faziam o programador javascript (sim, isso já foi cargo) fazer muita volta para solucionar em outro browser. Isso acarretava em problemas imensos em manutenção. O cliente, em um belo domingo de sol ligava e dizia que o formulário estava &#8220;pulando&#8221;, muitas vezes acompanhado de um não sei nem o que é browser/navegador: &#8220;eu dou dois cliques no ícone da internet e entro&#8221;. Então lá ia o programador e precisava revisar dois, três códigos que faziam a mesma coisa em navegadores diferentes.

Ainda bem que, assim como o HTML e o CSS, o JavaScript também sofreu sua padronização, facilitando a criação de [scripts que facilitam muito a vida do designer][1], deixando o designer cada vez mais feliz sem precisar consultar um programador. Uma dessas soluções foi a biblioteca [jQuery][2]. Uma biblioteca tão simples que designers conseguem fazer ótimos efeitos com apenas algumas linhas de comando.

Vamos a um exemplo/tutorial prático: um menu com submenus. Quando a pessoa clicar no link o submenu deve aparecer, com um efeito de slide.

Para o html usamos uma marcação simples, indicando quem é o menu e quem é o submenu.

<pre lang="html" line="1"><ul class="menu">
  <li>
    <a href="#">Item 1</a>
  </li>
  
  
  <li class="itemPai">
    Item 2
  </li>
  
  
  <ul class="subMenu">
    <li>
      <a href="#">SubItem 1</a>
    </li>
    
    
    <li>
      <a href="#">SubItem 2</a>
    </li>
    
    
    <li>
      <a href="#">SubItem 3</a>
    </li>
    
  </ul>
  
  
  <li>
    <a href="#">Item 3</a>
  </li>
  
  
  <li>
    <a href="#">Item 4</a>
  </li>
  
  
  <li>
    <a href="#">Item 5</a>
  </li>
  
</ul>
</pre>

Para ativar o jQuery você precisa baixá-la do site oficial (é apenas um aquivo js pequenininho) e coloque-a de preferencia na pasta ou em uma subpasta de onde está seu aquivo html, precisamos colocar a seguinte linha (de preferencia entre as tags <head> e </head> ):

<pre>&lt;script type="text/javascript" src="pasta/onde/está/a/jquery.js"&gt;&lt;/script&gt;</pre>

Após a inclusão da jQuery podemos usá-la sem problemas. Coloque seu código entre as tags <script> e <script> depois da chamada da jQuery. Tenha em mente que todo o que você vai fazer é chamado pela chave $ e interligamos os comandos com pontos. Então, para chamarmos o elemento que queremos colocar uma ação, no caso clicar, usamos a chave $ e para referenciamos, usamos as mesmas chamadas que usamos para o css.

<pre>$('ul.menu li.itemPai')</pre>

Agora, linkamos esse objeto com a ação click, ou seja quando a pessoa clicar no link propriamente dito.

<pre>$('ul.menu li.itemPai').click()</pre>

E passamos para ele uma função que fará nosso efeito de slide.

<pre lang="javascript" line="1">$('ul.menu li.itemPai').click(function(){
// Aqui virá a função
})
</pre>

Agora, a função que fará o efeito. Chamamos com a chave $ quem queremos animar e o linkamos com o tipo de animação. Para o efeito de slide (ou seja, encolher e esticar o elemento dando a ilusão de que ele está saindo de trás do outro elemento para baixo) a jQuery tem dois efeitos prontos que são: slideUp que recolhe o elemento e slideDown que expande o elemento. Ainda temos o slideToggle, que recolhe o elemento se estiver expandido ou vice-versa. Então iremos usar slideToggle para este efeito. Também usamos o return false para fazer com que o link não seja executado, retirando o usuario da nossa página.

<pre lang="javascript" line="1">$('ul.menu li.itemPai').click(function(){
$('.menu .submenu').slideToggle()
return false
})</pre>

E voilá, o efeito está pronto. Exceto por um problema&#8230; Se você colocar este script antes do seu menu, ele não vai funcionar porque você esta referenciando um elemento que ainda não existe para o navegador, logo ele não pode referenciar ninguém. Uma solução seria colocar o seu script após o seu código html, mas isso vai contra uma das práticas de [tableless][3] que é trabalhar com camadas e, assim como o CSS, não é interessante deixar ele entre o código html por n razões. A outra solução faz parte do escopo do jQuery que faz com que seu script só rode após o carregamento completo do seu código html. Para isso basta criar uma função que englobe seu script dentro da chave $. Ficando assim:

<pre lang="javascript" line="1">$(function(){
$('ul.menu li.itemPai').click(function(){
$('.menu .submenu').slideToggle()
return false
})
})</pre>

Isto resolve nosso problema. Agora, precisamos esconder nosso submenu quando a página carregar. Fazemos isso via javascript e não via css porque não queremos que o menu fique invisivel para pessoas que não usam javascript. Para isso, a jQuery tem a função hide que esconde um elemento (display:none). Se você quiser fazer o contrario, basta usar show no lugar de hide.

<pre lang="javascript" line="1"></pre>

E esse é o nosso script final que pode ser visto [aqui][4] e [aqui com aplicação de CSS básico][5]. O interessante da jQuery é que ela é bem inuitiva e tem muitas coisas que já vem no escopo dela que resolvem muitos problemas que os designers querem desenvolver, mas não querem que um programador faça por ser uma coisa tão simples de fazer. jQuery é a parte da programação que os designers sentiam falta e muitas vezes contornavam com um arquivo flash que destruia a semantica de área como o menu que acabamos de construir.

 [1]: http://elcio.com.br/reusable/jquery/diretrizes.pt
 [2]: http://jquery.com
 [3]: http://tableless.com.br/faq
 [4]: http://dgmike.com.br/tableless/jquery/menu-simples.html
 [5]: http://dgmike.com.br/tableless/jquery/menu-simples-arquivos-importados.html