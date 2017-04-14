---
title: Navegando com a jQuery
author: Michael Granados
type: post
date: 2008-09-11
categories:
  - Código
  - jQuery
  - Técnicas e Práticas
tags:
  - JavaScript
  - JQuery
---
Para os designers, familiarizar-se com a jQuery é um ato muito sutil. Isso se deve ao fato da mesma basear-se em um comando ( jQuery ou o seu atalho $ ) que referencia elementos e assim atribuir valores ou aplicar ações a eles. O mais interessante é que usamos as mesmas chamadas que usamos para referenciar elementos quando trabalhamos com CSS. Logo:
<!--more-->

<pre>$('p') // Chama todos os paragrafos
$('.menu') // Chama os elementos que contenham a classe menu
$('#caixas .chamada') // Chama os elementos .chamada que estão dentro de #caixas
$('.menu, .box') // Chama a classe menu e a classe box
$('#lista *') // Chama todos os elementos que estão dentro de #lista</pre>


A jQuery ainda implementa algumas chamadas especiais, baseadas no CSS3.

<pre>$('#menu &gt; li') // chama os li's filhos direto de #menu, exclui #menu li li
$('label + input') // chama apenas os inputs que tiveram um label antes &lt;label&gt;&lt;/label&gt; &lt;input /&gt;
$('.galeria ~ .fotos') // chama todas as .fotos que estão no mesmo nivel e após .galeria
$('#menu li:fist') // Chama apenas o primeiro li dentro de #menu
$('table tr:even') // Chama apenas os tr's impares
$('tr[colspan=2]') // Chama os tr's que contenham o atributo colspan definido como 2
$('form :text')  // Chama os inputs com type definido como text, caixas de texto</pre>

A lista completa pode ser [encontrada][1] no site oficial da jQuery bem documentada e com exemplos para cada caso. Com a seleção na cabeça, podemos aplicar efeitos (hide, show, fadeIn, fadeOut, slideUp, slideDown por exemplo) nos elementos que selecionarmos, colocar atributos para estes elementos como css ou mesmo colocar eventos neles, ou seja, funções que rodam quando você faz alguma coisa com eles, como por exemplo clicar, passar o mouse em cima, dar dois cliques, colocar o cursor na caixa de texto e assim por diante.

Em um exemplo prático, vamos fazer um menu com submenus onde não precisamos nos preocupar em adicionar classes e tudo mais. Primeiro vamos implantar o HTML, assim podemos fazer um belo menu semântico. Se quiser, aplique também um belo CSS, mas não se esqueça: não suma com os submenus neste momento, afinal, se o browser do usuário não possuir javascript ele não poderá mostrá-los. Então deixe os submenus à mostra porque depois vamos escondê-los via javascript.

<pre>&lt;ul id="menu"&gt;
&lt;li&gt;&lt;a href="inicio"&gt;Inicio&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#" title="Estas são as categorias do meu site"&gt;Categorias&lt;/a&gt;
&lt;ul&gt;
&lt;li&gt;&lt;a href="ferramentas"&gt;Ferramentas&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="downloads"&gt;Downloads&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="templates"&gt;Templates&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;li&gt;&lt;a href="#" title="Artigos técnicos"&gt;Artigos&lt;/a&gt;
&lt;ul&gt;
&lt;li&gt;&lt;a href="tableless"&gt;Tableless&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="javascript"&gt;JavaScript&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="php"&gt;PHP&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Banco de dados&lt;/a&gt;
&lt;ul&gt;
&lt;li&gt;&lt;a href="mysql"&gt;MySQL&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="postgree"&gt;PostGree&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;li&gt;&lt;a href="python"&gt;Python&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/li&gt;
&lt;/ul&gt;</pre>

Note que não há qualquer referência a quem é pai ou filho de sebmenu. Vamos usar as chamadas da própria jQuery para encontrar quem tiver submenu. O resultado deste menu, já com CSS aplicado pode ser visto [aqui][2].

Agora, vamos desaparecer com os submenus de forma dinâmica. Lembre-se que não podemos aplicar a jQuery em qualquer lugar, afinal o html pode ainda não ter sido gerado quando o script rodar, então colocamos o &#8220;desaparecimento&#8221; dentro da função de carregamento da própria jQuery. Isto fará com que nosso script só seja executado quando todo o HTML for carregado.

<pre>&lt;script type="text/javascript"&gt;
$(function(){ // Inicio da função de carregamento
$('#menu ul').hide()
}) // Fim da função de carregamento
&lt;/script&gt;</pre>

Com uma simples linha, sumimos com os submenus com a função hide(), note que usamos os próprios atributos para os quais chamamos esses submenus com CSS. [Veja][3] como desaparecemos com os submenus de uma forma simples e fácil.

Agora, a dinâmica! Vamos usar a chamada aos submenus usando como referencia os links que tenham como href o valor de # (tralha, sustenido, lasagna, jogo-da-velha, plus, ou como você quiser chamar). Fica assim:

<pre>$('#menu a[href=#]')</pre>

Assim, filtramos todos os nossos links pegando somente os links dentro de #menu que tenham o href como #.

Neles vamos implantar os comandos de click para mostrar o menu e o submenu, mas primeiro precisamos navegar entre os elementos. Para isso, usamos **next** ou **prev**, funções próprias da jQuery que navega entre o elemento que estiver após ou antes (respectivamente) do elemento em questão. Levando em conta que as funções de ação da jQuery (click/hover/toogle/etc) recebem como parâmetro **this** o elemento que recebeu a ação temos:

<pre>$('a[href=#]').click(function(){
this // é o elemento "a" (link) que foi clicado naquele momento
})</pre>

Então vamos navegar até o submenu, que é o elemento que está após o link:

<pre>$('a[href=#]').click(function(){
$(this).next() // Agora sim, com base no link (dinamicamente) temos o submenu
}</pre>

Perceba que apesar de recebermos em this o elemento, precisamos usar mais uma vez a jQuery pois se trata do elemento em si e não uma chamada à ele via jQuery.

Agora sim, podemos sumir ou aparecer com os submenus, usando o slideToggle da jQuery vemos como isso é implantado de forma simples e prática. Precisamos aplicar também um **return false** para cancelar a navegação do link, afinal ele não deixou de ser um link.

<pre>$('a[href=#]').click(function(){
$(this).next().slideToggle() // Some, aparece, some, aparece, incrivelmente simples com a jQuery
return false
}</pre>

Com apenas seis linhas de código (real) concluímos um menu com submenu dinâmico, navegando entre os elementos com a jQuery. Ainda aplicamos uma animação para esse submenu. O resultado pode ser visto [aqui][4].

Um dos motivos pelos quais a jQuery é uma das bibliotecas mais incríveis de se trabalhar porque seu aprendizado é simples e prático. Vale a pena investir um tempo para aprender a usá-la.

 [1]: http://docs.jquery.com/Selectors "Selectores da jQuery"
 [2]: http://dgmike.com.br/tableless/jquery/menu-submenu-parte1.html "Aplicação do HTML e JavaScript ao menu com submenu"
 [3]: http://dgmike.com.br/tableless/jquery/menu-submenu-parte2.html "Sumindo com os submenus com uma linha de código"
 [4]: http://dgmike.com.br/tableless/jquery/menu-submenu-parte3.html "Versão final do menu com submenu dinâmico"