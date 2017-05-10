---
title: Criando slideshow do zero com javascript puro
author: Clovis Neto
type: post
date: 2014-03-15
excerpt: Veremos neste artigo como criar um slideshow do zero apenas com javascript e uma doze elegante de css3.
url: /criando-slideshow-zero-com-javascript-puro-2/
dsq_thread_id: 2310599889
categories:
  - JavaScript
tags:
  - criando slideshow do zero com javascript puro
  - criando slideshow do zero sem jquery
  - criando slideshow do zero sem plugins
  - criando slideshow sem jquery
  - criando slideshow sem utilizar plugins
  - javascript puro
  - o slideshow com css3 e javascript
  - o slideshow com javascript
  - o slideshow do zero

---
Depois de criar um artigo no devmedia de [como criar um slideshow do zero em Jquery sem plugins][1], recebi vários pedidos para fazer o mesmo com javascript, também pude notar que muitas pessoas estavam com dificuldade em colocar link nas imagens e os botões de anterior/próximo. Veremos neste artigo como criar um slideshow do zero apenas com javascript e uma dose elegante de CSS3, com controladores, legendas e links nas imagens.

Abaixo o resultado final do nosso slide:

<div id="attachment_40991" style="width: 579px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2014/02/slide.fw_.png"><img class="size-medium wp-image-40991" title="Criando slideshow do zero com javascript puro" alt="Criando slideshow do zero com javascript puro" src="http://tableless.com.br/uploads/2014/02/slide.fw_-569x310.png" width="569" height="310" srcset="uploads/2014/02/slide.fw_-569x310.png 569w, uploads/2014/02/slide.fw_-308x168.png 308w, uploads/2014/02/slide.fw_.png 1365w" sizes="(max-width: 569px) 100vw, 569px" /></a>
  
  <p class="wp-caption-text">
    Resultado final do nosso slide
  </p>
</div>

## Estrutura HTML

Nossa estrutura html é bem simples, veja na listagem 1:

**Listagem 1** &#8211; Estrutura html do slideshow

<pre class="lang-html">&lt;figure&gt;
   &lt;span class="trs next"&gt;&lt;/span&gt;
   &lt;span class="trs prev"&gt;&lt;/span&gt;

   &lt;div id="slider"&gt;
      &lt;a href="#" class="trs"&gt;&lt;img src="imagem1.jpg" alt="Legenda da imagem 1" /&gt;&lt;/a&gt;
      &lt;a href="#" class="trs"&gt;&lt;img src="imagem2.jpg" alt="Legenda da imagem 2" /&gt;&lt;/a&gt;
   &lt;/div&gt;

   &lt;figcaption&gt;&lt;/figcaption&gt;
&lt;/figure&gt;</pre>

Onde:

<figure></figure> &#8211;> Figura que será responsável de gerenciar todos os elementos do nosso slide

<span class=&#8221;next trs&#8221;>, <span class=&#8221;prev trs&#8221;> &#8211;> Serão os controladores do nosso slide

<div id=&#8221;slide&#8221;> &#8211;> div que abriga as imagens do nosso slide, facilitará nosso controle no javascript

<figcaption> &#8211;> Legenda do slide, será baseada pelo o atributo &#8220;alt&#8221; das imagens

Let&#8217;s go! vamos agora estilizar nosso slide.

## Estilo CSS

Abaixo na listagem 2, o nosso estilo css, não explicarei a fundo nossa estilização, irei focar apenas nos principais pontos

**Listagem 2 &#8211; **Estilo css

<pre class="lang-css">&lt;style&gt;
* {margin: 0; padding: 0;}
body {background: #000}
a,img {border: none;}
.trs {-webkit-transition:all ease-out 0.5s;
    -moz-transition:all ease-out 0.5s;
    -o-transition:all ease-out 0.5s;
    -ms-transition:all ease-out 0.5s;
    transition:all ease-out 0.5s;}	
#slider {position: relative; z-index: 1;}
#slider a { position: absolute; top: 0; left: 0; opacity: 0;filter:alpha(opacity=0);}
.ativo {opacity: 1!important; filter:alpha(opacity=100)!important;}

/*controladores*/
span {background: #0190EE; cursor: pointer; opacity: 0;filter:alpha(opacity=0); position: absolute; bottom: 40%; width: 43px; height: 43px; z-index: 5;}
.next {right: 10px;}
.next:before,.next:after {left: 21px;}
.next:before {
    -webkit-transform: rotate(-42deg);
    top: 5px;
}
.next:after {
    -webkit-transform: rotate(-132deg);
    top: 19px;
}
.next:before,.next:after,.prev:before,.prev:after {content: "";
    height: 20px;
    background: #fff;
    width: 1px;
    position: absolute;
}
.prev {left: 10px;}
.prev:before,.prev:after {left: 18px;}
.prev:before {
    -webkit-transform: rotate(42deg);
    top: 5px;
}
.prev:after {
    -webkit-transform: rotate(132deg);
    top: 19px;
}

figure:hover span {opacity: 0.76;filter:alpha(opacity=76);}
    figure {
    max-width: 937px;
    height: 354px;
    position: relative;
    overflow: hidden;
    margin: 50px auto;
}

figcaption {padding-left: 20px;color: #fff; font-family: "Kaushan Script","Lato","arial"; font-size: 22px; background: rgba(1, 144, 238, 0.76); width: 100%; position: absolute; bottom: 0; left: 0; line-height: 55px; height: 55px; z-index: 5}
&lt;/style&gt;</pre>

Onde:
  
.trs &#8211;> class que define a transição das imagens do nosso slide e dos nossos controladores
  
.ativo &#8211;> class que define qual imagem está ativa
  
figure:hover span &#8211;> faz com que mostre nossos controladores ao passar o mouse no nosso slide

Parece que tudo está indo bem, vamos começar a brincar agora com nosso slider, gogo ninja lvl2 😀

&nbsp;

## Javascript

Veremos cada passo do código javascript bem detalhado para que não haja dúvida alguma ao termino do post.

Primeiramente vamos criar uma função **setaImagem **e colocar para que ela rode quando a janela (window) for carregada:

**Listagem 3** &#8211; Criação da função &#8220;setaImagem&#8221;

<pre class="lang-javascript">&lt;script type="text/javascript"&gt;
   function setaImagem(){
   }
   window.addEventListener("load",setaImagem,false);
&lt;/script&gt;</pre>

onde:
  
window.addEventListener(&#8220;load&#8221;,setaImagem,false); &#8211;> faz com que a função &#8220;setaImagem&#8221; seja executada quando a janela for carregada

Agora iremos criar nossa variável &#8220;settings&#8221; que receberá alguns objetos e funções anonimas.

**Listagem 4 **&#8211; Criando nossa varável &#8220;settings&#8221;, já com duas funções anonimas dentro, que são &#8220;legenda&#8221; e &#8220;primeiraImg&#8221;

<pre class="lang-javascript">var settings = {
  primeiraImg: function(){
    elemento = document.querySelector("#slider a:first-child");
    elemento.classList.add("ativo");
    this.legenda(elemento);
  },
  legenda: function(obj){
    var legenda = obj.querySelector("img").getAttribute("alt");
    document.querySelector("figcaption").innerHTML = legenda;
  }
 }</pre>

Onde:

var settings = {} **&#8211;>** define uma variavel &#8220;settings&#8221; que conterá as configurações do nosso slide

primeiraImg: function(){&#8230;} **&#8211;>** Função que seta a imagem que aparecerá inicialmente no nosso slide

elemento = document.querySelector(&#8220;#slider a:first-child&#8221;);<span style="color: #888888"><strong> &#8211;></strong></span> captura a primeira tag &#8220;<a>&#8221; da &#8220;div#slider&#8221; e coloca numa variavel elemento.

elemento.classList.add(&#8220;ativo&#8221;); **&#8211;>** coloca a classe ativo na tag capturada (elemento.classList.add(&#8220;ativo&#8221;)).

this.legenda(elemento); **&#8211;>** chama a função anonima &#8220;legenda&#8221; e passa como parâmetro a variável elemento que acabamos de criar

legenda:function(obj){&#8230;} **&#8211;>** função anonima que coloca captura o atributo &#8220;alt&#8221; da tag &#8220;<img>&#8221; que tem como pai, o parâmetro determinado como &#8220;obj&#8221; e coloca como legenda do slideshow

var legenda = obj.querySelector(&#8220;img&#8221;).getAttribute(&#8220;alt&#8221;); **&#8211;>** captura o atributo &#8220;alt&#8221; da tag &#8220;<img>&#8221; que tem como pai, o parâmetro determinado como &#8220;obj&#8221; (que neste caso é a primeira tag &#8220;<a>&#8221;) e coloca numa variável legenda

document.querySelector(&#8220;figcaption&#8221;).innerHTML = legenda; **&#8211;>** coloca o html, que está dentro do atributo alt da variavel legenda, dentro da tag &#8220;<figcaption>&#8221; que neste caso é a nossa legenda do slideshow.

Até agora tudo certo, mas note que se você executar nosso documento, nada acontece, isto porque não chamamos nossa função de setar a imagem.

**Listagem 5 **&#8211; chamando nossa variavel settings e suas respectivas funções anonimas

<pre class="lang-javascript">//chama o slide
settings.primeiraImg();

//chama a legenda
settings.legenda(elemento);

//chama o slide à um determinado tempo
var intervalo = setInterval(settings.slide,4000);</pre>

Primeiro chamamos nossa função de setar a imagem no slideshow, depois setamos sua legenda e por fim, acionamos um temporizador que roda nosso slide a cada 4 segundos.

Vamos agora adicionar mais uma função à configuração do nosso slide, seu nome será &#8220;slide&#8221;. Esta função servirá para controlar as transições automáticas do nosso slideshow.

_**obs: Adicione a linha de código abaixo, dentro da variável settings**_

**Listagem 6 **&#8211; Criação da função slide

<pre class="lang-javascript">slide: function(){
    elemento = document.querySelector(".ativo");
    if(elemento.nextElementSibling){
        elemento.nextElementSibling.classList.add("ativo");
        settings.legenda(elemento.nextElementSibling);
        elemento.classList.remove("ativo");
    }else{
        elemento.classList.remove("ativo");
        settings.primeiraImg();
    }
},</pre>

Primeiro criamos nossa função slide, dentro dela, capturamos a tag que contém a class &#8220;ativo&#8221; e colocamos numa variável &#8220;elemento&#8221;, logo em seguida fazemos uma verificação, se ouver uma tag após a tag &#8220;ativo&#8221; colocamos nesta outra tag a classe ativo, adicionamos a legenda dela no nosso slide e retiramos a classe ativo da nossa imagem que está ativa. Se não ouver nenhuma outra tag, tiramos a classe &#8220;ativo&#8221; da imagem que está ativa, e chamamos a função &#8220;primeiraImg&#8221; que servirá para setar a primeira imagem no nosso slide.

show de bola! nosso slide está rodando, mas note que nossos controladores ainda não funcionam, vamos agora fazer eles funcionarem.

Primeiro vamos criar nossa função que mostra a próxima imagem &#8220;próximo&#8221;:

**Listagem 7 **&#8211; Função &#8220;próximo&#8221;

<pre class="lang-javascript">proximo: function(){
    clearInterval(intervalo);
    elemento = document.querySelector(".ativo");

    if(elemento.nextElementSibling){
        elemento.nextElementSibling.classList.add("ativo");
        settings.legenda(elemento.nextElementSibling);
        elemento.classList.remove("ativo");
    }else{
        elemento.classList.remove("ativo");
        settings.primeiraImg();
    }
    intervalo = setInterval(settings.slide,4000);
},</pre>

O processo da função anonima &#8220;proximo&#8221; é o mesmo da função slide, apenas adicionamos um clearInterval(intervalo), que irá limpar o temporizador(tempo de execução) do nosso slide, e ao final da função reiniciamos nosso temporizador.

Agora iremos criar a função para mostrar a imagem anterior

**Listagem 8 **&#8211; função &#8220;anterior&#8221;

&nbsp;

<pre class="lang-javascript">anterior: function(){
	clearInterval(intervalo);
	elemento = document.querySelector(".ativo");

	if(elemento.previousElementSibling){
		elemento.previousElementSibling.classList.add("ativo");
		settings.legenda(elemento.previousElementSibling);
		elemento.classList.remove("ativo");
	}else{
		elemento.classList.remove("ativo");						
		elemento = document.querySelector("a:last-child");
		elemento.classList.add("ativo");
		this.legenda(elemento);
	}
	intervalo = setInterval(settings.slide,4000);
},</pre>

Esta função também é quase a mesma que a anterior, so mudamos onde tem &#8220;next&#8221;(próximo) e colocamos &#8220;previous&#8221;(anterior).

Ainda falta anexar o evento de click nos nossos controladores, segue abaixo

**Listagem 9** &#8211; Anexando a função de clique nos controladores

<pre class="lang-javascript">document.querySelector(".next").addEventListener("click",settings.proximo,false);
	document.querySelector(".prev").addEventListener("click",settings.anterior,false);</pre>

_**Obs: Coloque a função de clique nos controladores no final da função &#8220;setaImagem&#8221;**_

Disponibilizei nosso código no github para quem quiser contribuir ou esteja tendo algum problema no slide [(clique aqui)][2]

Bem amigos ninjas javascript&#8217;s, com isso terminamos nosso post, um forte abraço e até a próxima

Abaixo nosso código javascript completo:

<pre class="lang-html">&lt;script type="text/javascript"&gt;
function setaImagem(){
    var settings = {
        primeiraImg: function(){
            elemento = document.querySelector("#slider a:first-child");
            elemento.classList.add("ativo");
            this.legenda(elemento);
        },

        slide: function(){
            elemento = document.querySelector(".ativo");

            if(elemento.nextElementSibling){
                elemento.nextElementSibling.classList.add("ativo");
                settings.legenda(elemento.nextElementSibling);
                elemento.classList.remove("ativo");
            }else{
                elemento.classList.remove("ativo");
                settings.primeiraImg();
            }

        },

        proximo: function(){
            clearInterval(intervalo);
            elemento = document.querySelector(".ativo");

            if(elemento.nextElementSibling){
                elemento.nextElementSibling.classList.add("ativo");
                settings.legenda(elemento.nextElementSibling);
                elemento.classList.remove("ativo");
            }else{
                elemento.classList.remove("ativo");
                settings.primeiraImg();
            }
            intervalo = setInterval(settings.slide,4000);
        },

        anterior: function(){
            clearInterval(intervalo);
            elemento = document.querySelector(".ativo");

            if(elemento.previousElementSibling){
                elemento.previousElementSibling.classList.add("ativo");
                settings.legenda(elemento.previousElementSibling);
                elemento.classList.remove("ativo");
            }else{
                elemento.classList.remove("ativo");						
                elemento = document.querySelector("a:last-child");
                elemento.classList.add("ativo");
                this.legenda(elemento);
            }
            intervalo = setInterval(settings.slide,4000);
        },

        legenda: function(obj){
            var legenda = obj.querySelector("img").getAttribute("alt");
            document.querySelector("figcaption").innerHTML = legenda;
        }

    }

    //chama o slide
    settings.primeiraImg();

    //chama a legenda
    settings.legenda(elemento);

    //chama o slide à um determinado tempo
    var intervalo = setInterval(settings.slide,4000);
    document.querySelector(".next").addEventListener("click",settings.proximo,false);
    document.querySelector(".prev").addEventListener("click",settings.anterior,false);
}

window.addEventListener("load",setaImagem,false);
&lt;/script&gt;</pre>

 [1]: http://www.devmedia.com.br/criando-slideshow-do-zero-com-jquery-sem-usar-plugins/28297 "Clique para ir ao artigo"
 [2]: https://github.com/clovisdasilvaneto/slide-com-javascript-puro "visualizar exemplo pelo github"