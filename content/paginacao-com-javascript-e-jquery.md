---
title: Paginação com JavaScript e jQuery
author: Dyemerson Almeida
type: post
date: 2016-06-29
excerpt: Como fazer um script de paginação usando JavaScript e jQuery
url: /paginacao-com-javascript-e-jquery/
categories:
  - JavaScript
  - JQuery
tags:
  - JavaScript
  - JQuery

---
Algumas vezes, vamos deparar com uma situação onde é preciso fazer uma paginação sem a ajuda de uma linguagem de backend. É exatamente isso que vou ensinar aqui: fazer um sistema de paginação utilizando JavaScript , jQuery e Bootstrap.

Vamos primeiramente criar a nossa estrutura HTML e chamar as bibliotecas:

<pre class="lang-html prettyprint linenums prettyprinted">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;script src="/jquery/1.11.3/jquery.min.js"&gt;&lt;/script&gt;
&lt;link rel="stylesheet"href="/css/bootstrap.min.css"&gt;
// somente para ficar mais "bonito o layout" vamos dar um padding-bottom no select
&lt;style type="text/css"&gt;
.col-lg-12{
   padding-bottom: 20px;
  } 
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div class="col-lg-12"&gt;
    &lt;p&gt;itens por pagina&lt;/p&gt;
      &lt;select id="qtd"  class="form-control input-sm input-order"&gt;
        &lt;option value="1"&gt;1&lt;/option&gt;
        &lt;option value="2"&gt;2&lt;/option&gt;
         &lt;option value="3"&gt;3&lt;/option&gt;
       &lt;/select&gt;
     &lt;/div&gt;
&lt;div class="all" id="conteudo"&gt;
  &lt;div class="col-lg-3 col-md-6"&gt;
    &lt;div class="panel panel-primary "&gt;
        &lt;p&gt;Tabless 1&lt;/p&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;div class="col-lg-3 col-md-6"&gt;
    &lt;div class="panel panel-primary "&gt;
        &lt;p&gt;Tabless 2&lt;/p&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;div class="col-lg-3 col-md-6"&gt;
    &lt;div class="panel panel-primary "&gt;
        &lt;p&gt;Tabless 3&lt;/p&gt;
      &lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;
&lt;div id="pagi"&gt;&lt;/div&gt; //div responsável por mostrar a paginação
&lt;/body&gt;
&lt;/html&gt;
</pre>

Reparem que eu escrevi 3 vezes a mesma div. Vocês podem repetir quantas vezes quiserem ou até coloca-lá em _loop_ (_foreach_ do PHP, por exemplo). É exatamente essa repetição que vamos paginar. Vamos agora criar as funções em JavaScript:

<pre class="lang-javascript ">&lt;script type="text/javascript"&gt;
//acionamos o jquery para iniciar a paginação quando o documento estiver "pronto"
$(document).ready(function() {
    //Pegamos o valor selecionado default no select id="qtd"
     var mostrar_por_pagina = $('#qtd').val(); 
    //quantidade de divs
      var numero_de_itens = $('#conteudo').children('.col-lg-3').size();
     //fazemos uma calculo simples para saber quantas paginas existiram
      var numero_de_paginas = Math.ceil(numero_de_itens / mostrar_por_pagina)
    //Colocamos a div class controls dentro da div id pagi
    $('#pagi').append('&lt;div class=controls&gt;&lt;/div&gt;
      &lt;input id=current_page type=hidden&gt;&lt;input id=mostrar_por_pagina type=hidden&gt;');
      $('#current_page').val(0);
      $('#mostrar_por_pagina').val(mostrar_por_pagina);
      //Criamos os links de navegação
      var nevagacao = '&lt;li&gt;&lt;a class="prev" onclick="anterior()"&gt;Prev&lt;/a&gt;&lt;/li&gt;';
      var link_atual = 0;
      while (numero_de_paginas &gt; link_atual) {
          nevagacao += '&lt;li&gt;&lt;a class="page" onclick="ir_para_pagina(' + link_atual + ')" longdesc="' 
          + link_atual + '"&gt;' + (link_atual + 1) + '&lt;/a&gt;&lt;/li&gt;';
          link_atual++;
      }
      nevagacao += '&lt;li&gt;&lt;a class="proxima" onclick="proxima()"&gt;proxima&lt;/a&gt;&lt;/li&gt;';
      //colocamos a nevegação dentro da div class controls
      $('.controls').html("&lt;div class='paginacao'&gt;\
        &lt;ul class='pagination pagination-sm'&gt;"+nevagacao+"&lt;/ul&gt;&lt;/div&gt;");
      //atribuimos ao primeiro link a class active
      $('.controls .page:first').addClass('active');
      $('#conteudo').children().css('display', 'none');
      $('#conteudo').children().slice(0, mostrar_por_pagina).css('display', 'block');
  });
&lt;/script&gt;
</pre>

Até aqui, a paginação já é mostrada, porém, ao clicar nos links, nada acontece. Vamos criar as seguintes funções em JavaScript para que funcione:  _ir\_para\_pagina()_, _anterior()_ e _proxima()_.

Então mãos à obra:

<pre class="lang-javascript">&lt;script type="text/javascript"&gt;
function ir_para_pagina(numero_da_pagina) {
      //Pegamos o número de itens definidos que seria exibido por página
      var mostrar_por_pagina = parseInt($('#mostrar_por_pagina').val(), 0);
      //pegamos  o número de elementos por onde começar a fatia
      inicia = numero_da_pagina * mostrar_por_pagina;
     //o número do elemento onde terminar a fatia
      end_on = inicia + mostrar_por_pagina;
     $('#conteudo').children().css('display', 'none').slice(inicia, end_on).css('display', 'block');
     $('.page[longdesc=' + numero_da_pagina+ ']').addClass('active')
       .siblings('.active').removeClass('active');
    $('#current_page').val(numero_da_pagina);
  }

 function anterior() {
     nova_pagina = parseInt($('#current_page').val(), 0) - 1;
      //se houver um item antes do link ativo atual executar a função
      if ($('.active').prev('.page').length == true) {
          ir_para_pagina(nova_pagina);
      }
  }

function proxima() {
      nova_pagina = parseInt($('#current_page').val(), 0) + 1;
      //se houver um item após o link ativo atual executar a função
      if ($('.active').next('.page').length == true) {
          ir_para_pagina(nova_pagina);
      }
  }
&lt;/script&gt;
</pre>

Pronto, agora temos um sistema de paginação baseado em div&#8217;s com JavaScript + jQuery, porém, precisamos pegar a quantidade de itens por página que o usuário escolher e remontar toda a paginação. Para isso, vamos usar a função _change_ do jQuery:

<pre class="lang-javascript">&lt;script type="text/javascript"&gt;
// Pegamos o evento change do select id="qtd" e remontamos toda a paginação default
  $( "#qtd" ).change(function() {
    //Removemos os "controles" de paginação
      $(".controls").remove();
    //Pegamos o valor selecionado
      var mostrar_por_pagina = this.value;
     //remontamos a paginação
      var numero_de_itens = $('#conteudo').children('.col-lg-3').size();
      var numero_de_paginas = Math.ceil(numero_de_itens / mostrar_por_pagina);
      //Colocamos a div class controls dentro da div id pagi
    $('#pagi').append('&lt;div class=controls&gt;&lt;/div&gt;
      &lt;input id=current_page type=hidden&gt;&lt;input id=mostrar_por_pagina type=hidden&gt;');
      $('#current_page').val(0);
      $('#mostrar_por_pagina').val(mostrar_por_pagina);
  //Criamos os links de navegação
      var nevagacao = '&lt;li&gt;&lt;a class="prev" onclick="previous()"&gt;Prev&lt;/a&gt;&lt;/li&gt;';
      var link_atual = 0;
      while (numero_de_paginas &gt; link_atual) {
          nevagacao += '&lt;li&gt;&lt;a class="page" onclick="ir_para_pagina(' + link_atual + ')" longdesc="' 
          + link_atual + '"&gt;' + (link_atual + 1) + '&lt;/a&gt;&lt;/li&gt;';
          link_atual++;
      }
      nevagacao += '&lt;li&gt;&lt;a class="next" onclick="next()"&gt;Next&lt;/a&gt;&lt;/li&gt;';
   //colocamos a navegação dentro da div class controls
      $('.controls').html("&lt;div class='paginacao'&gt;
        &lt;ul class='pagination pagination-sm'&gt;"+nevagacao+"&lt;/ul&gt;&lt;/div&gt;");
      $('.controls .page:first').addClass('active');
      $('#conteudo').children().css('display', 'none');
      $('#conteudo').children().slice(0, mostrar_por_pagina).css('display', 'block');
    
  });
&lt;/script&gt;
</pre>

Nosso sistema de paginação completo, totalmente no HTML, é uma das vantagens dessa paginação. O ganho de performance, claro, depende da quantidade de dados.

Adaptado de <a href="http://web.enavu.com/tutorials/making-a-jquery-pagination-system/" target="_blank">http://web.enavu.com/tutorials/making-a-jquery-pagination-system/</a>