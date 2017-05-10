---
title: Menu Retrátil com CSS e jQuery
author: Dani Guerrato
type: post
date: 2013-08-12
excerpt: Navegação para design responsivo sem complicações em quatro sabores diferentes.
url: /menu-retratil-com-css-e-jquery/
dsq_thread_id: 1594441368
categories:
  - JQuery
tags:
  - design responsivo
  - menus
  - navegação

---
Neste artigo vamos criar passo-a-passo um menu retrátil super versátil que, com apenas algumas linhas de modificação, poderá ser utilizado na horizontal, vertical, sobrepondo ou empurrando o conteúdo de um site. Veja ainda como evitar os <s>malditos bugs</s> problemas mais comuns deste tipo de navegação.

### Mini bibliotecas

Uma das principais vantagens de escrever um HTML semântico e bem organizado é a versatilidade. Com um mesmo código é possível criar diversas variações de estilo utilizando apenas CSS. Na verdade muitas estruturas acabam se repetindo, embora visualmente diferentes. Isto acontece geralmente com formulários, rodapés e navegação. É o motivo pelo qual os frameworks estão tão populares ultimamente. Mas, muitas vezes, não precisamos de algo tão massivo e complexo quanto uma framework para tarefas simples. É algo como tentar acertar uma formiga com uma bazuca! É muito mais prático e funcional construir uma pequena biblioteca pessoal de snippets &#8211; pequenos trechos de código. O formato não importa muito. Pode ser que você salve comentários no seu software de edição favorito, escreva em pequenos blocos de notas no seu computador, envie e-mails para si mesmo ou até mesmo utilize alguma ferramenta como [Snippets.me][1]  ou [Snippi][2]. Seja como for ter algumas cartas na manga é útil na hora de entregar aquele projeto para ontem e recuperar horas de sono. Este menu é uma das minhas.

## HTML

O HTML do menu é bem simples. Vamos usar uma div com a classe &#8220;drop&#8221;. Esta div será necessária para as versões do menu em que ele irá sobrepor o site. Ela irá funcionar como uma sustentação para a navegação. Nas demais versões, ela pode ser deletada.

Dentro da div &#8220;drop&#8221; criamos uma `nav` e, como um menu é sempre uma lista de links, vamos usar as tags `ul` e `li`.

No exemplo, o meu menu ocupa 100% da tela mas eu gostaria que os links ficassem dentro de um container centralizado. Para isso, adicionei uma div com a classe wrap e margin automática.

No final, o HTML ficou assim:

<pre class="lang-html">&lt;div class="drop"&gt;
&lt;nav class="nav nav-aberta"&gt;
&lt;div class="wrap"&gt;
&lt;ul class="listaNav"&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 1&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 2&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 3&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 4&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 5&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 6&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 7&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 8&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="#"&gt;Item 9&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/div&gt;
&lt;/nav&gt;
&lt;/div&gt;</pre>

Para ter um elemento servindo de exemplo visual e ser sobreposto ou empurrado pelo meu menu, coloquei apenas uma imagem. Mas, pense nela como todo o conteúdo do site, okay?

<pre class="lang-html">&lt;img alt="" src="http://placehold.it/1920x800/&text=Conteúdo" /&gt;</pre>

Hoje vamos criar quatro menus utilizando este mesmo html como um coringa.

## O CSS

Aqui já começamos a ter diferenças de um menu para o outro. Trabalharemos com media-queries que reordenarão os elementos de acordo com o tamanho do viewport do usuário, ou seja, da janela do browser. Para o exemplo, criei um media-querie com a max-width de 800px. É a partir desta largura que o menu se colapsa em apenas uma âncora. Altere este valor de acordo com o seu projeto, é claro.

### Menus Horizontais

Hoje vamos desenvolver dois tipos de menus horizontais diferentes. Um empurrará todo o site para baixo ao abrir ([demo][3]).

<img class="alignnone size-full wp-image-38487" alt="nav-1" src="http://tableless.com.br/uploads/2013/08/nav-1.jpg" width="660" height="322" srcset="uploads/2013/08/nav-1.jpg 660w, uploads/2013/08/nav-1-329x160.jpg 329w, uploads/2013/08/nav-1-588x286.jpg 588w, uploads/2013/08/nav-1-635x310.jpg 635w" sizes="(max-width: 660px) 100vw, 660px" />

E o outro, se abrirá sobre o site ([demo][4]).

<img class="alignnone size-full wp-image-38488" alt="nav-2" src="http://tableless.com.br/uploads/2013/08/nav-2.jpg" width="660" height="322" srcset="uploads/2013/08/nav-2.jpg 660w, uploads/2013/08/nav-2-329x160.jpg 329w, uploads/2013/08/nav-2-588x286.jpg 588w, uploads/2013/08/nav-2-635x310.jpg 635w" sizes="(max-width: 660px) 100vw, 660px" />

Note que entre os dois htmls existe apenas uma classe diferente: a div &#8220;drop&#8221;. Esta divisão extra está apenas no segundo exemplo no menu que passa por cima do conteúdo do site. Ela terá uma altura fixa, que será a altura do meu menu quando fechado. Quando ele se abrir, a div que sustenta nosso menu continuará do mesmo tamanho, fazendo com que os demais elementos sobreponham o resto do site.

Primeiro, vamos ao CSS dele fechado. Como é só uma lista, eu apenas usei o parâmetro &#8220;inline-block&#8221; para que todos os itens se alinhem um ao lado do outro. Os demais parâmetros, são apenas estilização do menu. Não coloquei muitas coisas em termos visuais. Não é para ser bonito. A idéia é ter uma carcaça pronta para receber o SEU design. Eu coloquei na minha nav uma &#8220;position: fixed&#8221; para que o menu fique sempre à vista do usuário, e de fácil acesso. Mas, você não terá problemas se quiser trabalhar com uma posição relativa ou absoluta. Isso irá variar de acordo com o seu projeto.

Outra coisa importante é o parâmetro &#8220;nav-toggle&#8221;. Ele será o gatilho para abrir e fechar o meu menu, tanto em sua versão vertical quanto na horizontal. Ele é inserido no meu HTML dinamicamente via JavaScript. No entanto, eu não quero que ele apareça quando estiver em resoluções maiores que 800px, por isso coloquei nele um &#8220;display: none&#8221; e, dentro do media-querie que irá atender viewports menores que 800px ele tem o &#8220;display: block&#8221;.

Veja como ficou o CSS do menu na horizontal que empurrará o site para baixo:

<pre class="lang-css">.wrap {
max-width: 1200px;
margin: 0 auto;
}

.nav {
background: #FFF;
z-index: 200;
position: fixed;
width: 100%;
font-size: 1em;
overflow: auto;
}

.nav ul {
padding: 1em;
}

li {
display: inline-block;
margin-right: 2em;
}

a {
text-decoration: none;
color: #444;
}

a:hover {
color: red;
}

.nav-toggle {
display: none;
}

.foto {
width: 100%;
}

/*Media Queries*/
@media only screen and (max-width: 800px) {
.wrap {
max-width: 100%;
margin: 0;
}

.nav.nav-aberta {
position: relative;
padding: 0 0 0.5em 0;
height: 0;
}

.nav ul {
padding: .5em;
margin: 0;
background: #444;
}

li {
margin: 0;
padding: 0;
display: block;
border-bottom: 1px solid #FFF;
}

li a {
padding: 0.5em 0 0.5em 0;
display: block;
color: #FFF;
}

li:last-child {
border-bottom:none;
}

.nav-toggle {
display: block;
padding: .4em;
margin: .5em 0;
}
}</pre>

As principais mudanças para telas menores são o .nav-toggle que agora é visível nas versões menores que 800px, a lista que deixa de ser &#8220;inline-block&#8221; para ser apenas &#8220;block&#8221; e a .nav, que antes tinha a posição fixa e agora é relativa.

Na versão em que o menu irá passar por cima do site, defina uma altura para a classe .drop no media querie equivalente ao menu fechado, posição relativa e o z-index maior que os outros elementos para que ele possa se sobrepor. Veja o código:

<pre class="lang-css">.drop {
height: 48px;
position: relative;
z-index: 1000;
}</pre>

Uma maneira interessante de testar o menu funcionando antes de aplicar o JavaScript é modificar a altura da .nav para &#8220;auto&#8221; ou a altura que você quer que o seu menu tenha quando estiver aberto. Isso fará com que, ao redimensionar o seu browser, o menu apareça como se estivesse aberto. No entanto, para o nosso exemplo, vamos usar a altura 0.

### Menus Verticais

&nbsp;

<img class="alignnone size-full wp-image-38499" alt="menu-lateral" src="http://tableless.com.br/uploads/2013/08/menu-lateral.jpg" width="660" height="322" srcset="uploads/2013/08/menu-lateral.jpg 660w, uploads/2013/08/menu-lateral-329x160.jpg 329w, uploads/2013/08/menu-lateral-588x286.jpg 588w, uploads/2013/08/menu-lateral-635x310.jpg 635w" sizes="(max-width: 660px) 100vw, 660px" />

São dois os modelos de menu vertical:
  
Um abrirá a partir da esquerda empurrando todo o site para a direita ao abrir ([demo][5]).

<img class="alignnone size-full wp-image-38489" alt="nav-3" src="http://tableless.com.br/uploads/2013/08/nav-3.jpg" width="660" height="322" srcset="uploads/2013/08/nav-3.jpg 660w, uploads/2013/08/nav-3-329x160.jpg 329w, uploads/2013/08/nav-3-588x286.jpg 588w, uploads/2013/08/nav-3-635x310.jpg 635w" sizes="(max-width: 660px) 100vw, 660px" />

E o outro, se abrirá sobre o conteúdo ([demo][6]).

<img class="alignnone size-full wp-image-38490" alt="nav-4" src="http://tableless.com.br/uploads/2013/08/nav-4.jpg" width="660" height="322" srcset="uploads/2013/08/nav-4.jpg 660w, uploads/2013/08/nav-4-329x160.jpg 329w, uploads/2013/08/nav-4-588x286.jpg 588w, uploads/2013/08/nav-4-635x310.jpg 635w" sizes="(max-width: 660px) 100vw, 660px" />

Primeiro, vamos ao CSS do menu quando o viewport for maior que 800px. Neste exemplo, deixei o menu em um background escuro e ocupando 20% do viewport. Assim, o conteúdo, ocupará os 80% restantes. Como os itens da minha lista não ficarão mais uns aos lados dos outros, neste caso eu a mantive o display &#8220;block&#8221; desde o CSS desktop. E, também deixei o gatilho com &#8220;display:none&#8221; e a minha imagem com 80% de largura.

Quanto ao CSS para telas menores o primeiro ponto é que, neste exemplo, trabalharemos com uma largura fixa para o menu. Deixei o padrão de 175px de largura. Usei esta medida pela segurança de não ficar muito grande em smartphones, já que o tamanho mais comum é de 320px de largura com ele em pé, 175px é uma medida segura para trabalharmos.

Minha sidebar terá também a posição absoluta no exemplo. Isso serve para que ela possa &#8220;passar por cima&#8221; do conteúdo do site sem problemas. Na versão em que o site irá caminhar para o lado, faremos isso pelo JS.

E, não podemos esquecer, do gatilho que irá ativar o nosso menu. Assim como no exemplo anterior, usei um item de classe .nav-toggle que será adicionado dinamicamente pelo Javascript. Deixei ele com o display:none fora do media-query e ele irá ter a posição absoluta quando o viewport for menor que 800px. Deixei o topo dele em 0 e ele será alinhado à partir da borda direita dele. Usei, neste caso, um valo negativo. Assim, ele ficará visível quando o meu menu estiver fechado, para ser clicado e, ao abrir, caminhará junto com o meu menu para ser clicado novamente e fecha-lo.

<pre class="lang-css">.wrap {
max-width: 1200px;
margin: 0 auto;
}

.nav {
background: #FFF;
z-index: 200;
position: relative;
width: 20%;
font-size: 1em;
float: left;
background: #444;
}

.nav ul {
padding: 1em;
}

li {
display: block;
width: 100%;
margin: 1em 2em 1em 0;
}

a {
text-decoration: none;
color: #FFF;
}

a:hover {
color: red;
}

.nav-toggle {
display: none;
}

.foto {
 width: 80%;
float: right;
}

/*Media Queries*/
@media only screen and (max-width: 800px) {
.wrap {
max-width: 100%;
margin: 0;
}

.nav {
width: 175px;
position: absolute;
top: 0;
left: 0;
}

.nav ul {
padding: .5em;
margin: 0;
background: #444;
}		

li {
margin: 0;
padding: 0;
display: block;
}

li a {
padding: 0.5em 0 0.5em 0;
display: block;
color: #FFF;
}

.nav-toggle {
position: absolute;
top: 0;
right: -56px;
color: #FFF;
cursor: pointer;
width: 44px;
height: 24px;
z-index: 1000;
display: block;
background: #444;
padding: 12px 6px 6px 6px;
}

.foto {
width: 100%;
position: relative;
float: none;
}
}</pre>

## Javascript

Como o nosso código utiliza jQuery a primeira coisa a fazer é chamar a biblioteca.

<pre class="lang-html">&lt;script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"&gt;&lt;/script&gt;
&lt;script&gt;window.jQuery || document.write('&lt;script src="js/vendor/jquery-1.9.1.min.js"&gt;&lt;\/script&gt;')&lt;/script&gt;</pre>

Menus na Horizontal

Para os dois casos do menu na horizontal, tanto o que empurra quanto o que sobrepõe o site, usei exatamente o mesmo JS. O que irá garantir que ele irá sobrepor o site é a classe .drop . Quando ela estiver com uma altura definida, ela será como um suporte para o menu e fará com que tudo passe por cima dos outros objetos do site. Quando ela não existir, ou não estiver com uma altura definida ela irá aumentar de tamanho, empurrando os demais elementos para baixo.

A primeira coisa a fazer é utilizar addClass para colocar a classe &#8220;fechada&#8221; no menu. Esta classe será retirada quando o menu for aberto e irá aparecer quando ele fechar novamente. Servirá como um elemento para indicar ao meu JS o que irá fazer.

Em seguida, utilize o comando de jQuery after para adicionar o gatilho para o menu. Caso queira que ele fique antes do menu, você pode substituir o &#8220;after&#8221; por &#8220;before&#8221;.

A animação acontece através dos eventos &#8220;click&#8221; e &#8220;animate&#8221;.

O JavaScript fica assim:

<pre class="lang-js">$(".nav").addClass("fechada");
$(".nav").after("&lt;a class=\"nav-toggle\"&gt;Menu&lt;/a&gt;");

$(".nav-toggle").click(function() {
var altura = $(".nav ul").height();
if($(".nav").hasClass("fechada")) {
$(".nav").animate({height:altura},{queue:false, duration:200}).removeClass("fechada");
}
else {
$(".nav").animate({height:"0px"},{queue:false, duration:200}).addClass("fechada");
}
});</pre>

A mágica é a seguinte: quando o usuário clica no gatilho do menu (no caso, o .nav-toggle), ele pega a altura da minha lista de links. Depois, ele faz uma verificação na minha .nav . Se ela possuir a classe &#8220;fechada&#8221;, ela irá animar aumentando a altura dela e mostrando o menu. Caso esta classe não exista, ele diminui a altura escondendo o menu. Tudo isso na velocidade de 200 milisegundos.

Escolhi este método por uma questão de praticidade. Existem outras maneiras de realizar o mesmo processo. Ao invés de adicionar uma classe, é possível, por exemplo, verificar a altura da .nav. Se for maior que 0px, significa que ela estava aberta e, ao clicar, será fechada. Se for igual a 0, é porque ela está fechada e precisará ser aberta.

### E uma dica!

Para finalizar, vamos nos livrar de um bug chato que normalmente acontece: ao aumentar a tela para os valores maiores que o nosso media querie (no caso, 800px), o menu poderá ficar com a altura que ele estava quando aberto, e isso obviamente desalinha todo o layout.

Resolver isso é bem fácil. Podemos fazer com que o nosso JS verifique, ao redimensionar a janela, qual é o tamanho do viewport. Se for maior que 800, ele volta a altura que deveria ter originalmente. Se for menor, ele simplesmente se fecha ou mantém a altura que estava quando aberta. No exemplo, eu fiz com que ele se fechasse. Veja como ficou o JS inteiro:

<pre class="lang-js">$(".nav").addClass("fechada");
$(".nav").after("&lt;a class=\"nav-toggle\"&gt;Menu&lt;/a&gt;");

$(".nav-toggle").click(function() {
var altura = $(".nav ul").height();
if($(".nav").hasClass("fechada")) {
$(".nav").animate({height:altura},{queue:false, duration:200}).removeClass("fechada");
}
else {
$(".nav").animate({height:"0px"},{queue:false, duration:200}).addClass("fechada");
}
});

$(window).resize(function() {
var tamanhoViewport = $(window).width();
if (tamanhoViewport &gt; 800) {
$(".nav").css("height","auto").addClass("fechada");
} else {
$(".nav").css("height","0px").addClass("fechada");
}
});</pre>

Menu Vertical

Neste caso, a verificação da largura do viewport acontece em dois momentos. Uma quando o usuário redimensionar o browser e outra no momento que o documento é aberto. Em ambos, a condição é a mesma: se o tamanho da janela for menor que 800px, ele adiciona a classe &#8220;side-fechado&#8221;, o gatilho &#8220;nav-toggle&#8221; que irá animar o menu e colocar a posição dele como -175px à esquerda, o que garante que o menu ficará fechado logo após o usuário redimensionar o browser. Se for maior que 800px a posição à esquerda fica 0.

(Lembrando que estas medidas de largura são subjetivas e devem ser alteradas a cada projeto.)

O JS ficou assim:

<pre class="lang-js">//Menu Sidebar
$(window).resize(function() {
var tamanhoJanela = $(window).width();
$(".nav-toggle").remove();

if (tamanhoJanela &lt; 800) {
$('.nav').css('left', '-175px').addClass('side-fechado');
$('.nav').append( "&lt;div class='nav-toggle'&gt;Menu&lt;/div&gt;" );
$('.foto').css("left", 0);
} else {
$('.nav').css('left', '0px').addClass('side-fechado');
}
});

$(document).ready(function() {
var tamanhoJanela = $(window).width();
$(".nav-toggle").remove();

if (tamanhoJanela &lt; 800) {
$('.nav').css('left', '-175px').addClass('side-fechado');;
$('.nav').append( "&lt;div class='nav-toggle'&gt;Menu&lt;/div&gt;" );
} else {
$('.nav').css('left', '0px').addClass('side-fechado');
}
});</pre>

Para animar o menu, vamos criar uma função de nome &#8220;menu&#8221;. Nesta função, ao clicar no gatilho &#8220;.nav-toggle&#8221;, acontecem duas coisas: verificação da existência da classe &#8220;side-fechado&#8221; e animação do menu. Se possuir, o JavaScript anima a navegação para 0px da borda esquerda do menu. Caso não possua (o que indica para nós que o menu está aberto) a navegação volta para os -175px negativos.

O JS fica assim:

<pre class="lang-js">function menu() {
$('.nav-toggle').click(function() {
if($(".nav").hasClass("side-fechado")) {
$('.nav').animate({
left: "0px",
}, 100, function() {
$(".nav").removeClass("side-fechado");
});
}
else {
$('.nav').animate({
left: "-175px",
}, 100, function() {
$(".nav").addClass("side-fechado");
});
}
});
}</pre>

Neste exemplo, ele está sobrepondo o conteúdo do site. Mas, eu posso fazer com que ele empurre o site para a direita quando surgir e para a esquerda quando fechar. Para isso, eu coloco um animate no conteúdo do site também (no exemplo, o meu objeto de classe &#8220;.foto&#8221;). O JS fica assim:

<pre class="lang-js">function menu() {
$('.nav-toggle').click(function() {
if($(".nav").hasClass("side-fechado")) {
$('.nav').animate({
left: "0px",
}, 100, function() {
$(".nav").removeClass("side-fechado");
});
$('.foto').animate({
left: "175px",
}, 100);
}
else {
$('.nav').animate({
left: "-175px",
}, 100, function() {
$(".nav").addClass("side-fechado");
});
$('.foto').animate({
left: "0px",
}, 100);
}
});
}</pre>

Agora, é só chamar a função &#8220;menu&#8221; depois das verificações de tamanho da janela. O JS completo fica assim:

<pre class="lang-js">function menu() {
$('.nav-toggle').click(function() {
if($(".nav").hasClass("side-fechado")) {
$('.nav').animate({
left: "0px",
}, 100, function() {
$(".nav").removeClass("side-fechado");
});
$('.foto').animate({
left: "175px",
}, 100);
}
else {
$('.nav').animate({
left: "-175px",
}, 100, function() {
$(".nav").addClass("side-fechado");
});
$('.foto').animate({
left: "0px",
}, 100);
}
});
}

//Menu Sidebar
$(window).resize(function() {
var tamanhoJanela = $(window).width();
$(".nav-toggle").remove();

if (tamanhoJanela &lt; 800) {
$('.nav').css('left', '-175px').addClass('side-fechado');
$('.nav').append( "&lt;div class='nav-toggle'&gt;Menu&lt;/div&gt;" );
$('.foto').css("left", 0);
} else {
$('.nav').css('left', '0px').addClass('side-fechado');
}

menu();
});

$(document).ready(function() {
var tamanhoJanela = $(window).width();
$(".nav-toggle").remove();

if (tamanhoJanela &lt; 800) {
$('.nav').css('left', '-175px').addClass('side-fechado');;
$('.nav').append( "&lt;div class='nav-toggle'&gt;Menu&lt;/div&gt;" );
} else {
$('.nav').css('left', '0px').addClass('side-fechado');
}

menu();
});</pre>

## Demos

Você pode fazer aqui o [download dos arquivos][7] com os exemplos criados ou brincar com as demos online no Codepen.

&#8211; [Navegação 1 &#8211; Menu horizontal empurrando o conteúdo para baixo.][3]
  
&#8211; [Navegação 2 &#8211; Menu horizontal passando sobre o conteúdo.][4]
  
&#8211; [Navegação 3 &#8211; Menu lateral empurrando o conteúdo para o lado.][5]
  
&#8211; [Navegação 4 &#8211; Menu lateral passando sobre o conteúdo.][6]

## Conclusão

A navegação é sempre uma parte fundamental de qualquer layout. Cuidar para que ela apareça da maneira mais otimizada possível, não apenas em aparelhos mobile, mais em dispositivos com o viewport reduzido não é mais um luxo, mas uma necessidade. Existem algumas outras abordagens até mesmo utilizando apenas CSS3. É importante conhecer diversas soluções para adequar as necessidades de cada projeto. Reaproveitando trechos de código como este podemos garantir que o processo de desenvolvimento seja ágil e preciso, sem sacrificar qualidade, semântica e a experiência do usuário.

 [1]: http://snippets.me/ "Snippets.me"
 [2]: http://snippi.com/ "Snippi"
 [3]: http://codepen.io/daniguerrato/pen/fbgLl "Navegação Responsiva 1"
 [4]: http://codepen.io/daniguerrato/pen/iAeyx "Navegação Responsiva 2"
 [5]: http://codepen.io/daniguerrato/pen/EKylp "Navegação Responsiva 3"
 [6]: http://codepen.io/daniguerrato/pen/wcCEK "Navegação Responsiva 4"
 [7]: http://cl.ly/0E0C3O0j2r2T "Navegação Responsiva - Demo"