---
title: Templates e jQuery – parte 2
author: Davi Ferreira
type: post
date: 2010-12-13
excerpt: Agora que você já sabe como implementar templates em suas aplicações javascript, chegou a hora de conhecer técnicas avançadas de como combinar modelos HTML e scripts jQuery.
url: /templates-jquery-parte2/
tweetbackscheck:
  - 1356440859
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/templates-jquery-parte2";s:7:"tinyurl";s:26:"http://tinyurl.com/3c8owty";s:4:"isgd";s:19:"http://is.gd/3cZxnf";}'
twittercomments:
  - 'a:1:{i:147334311757103105;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503018698
categories:
  - AJAX
  - Código
  - JavaScript
  - JQuery
tags:
  - 2010
  - JavaScript
  - JQuery
  - template
  - tmpl

---
[Na primeira parte][1] deste artigo você conferiu uma introdução ao novo plugin .tmpl() que possibilita a utilização de templates para retornos e saídas de suas aplicações jQuery. O plugin certamente é um avanço considerável na organização de código &#8211; é o JavaScript ficando cada vez mais profissional e robusto, abandonando a fama de ser uma simples linguagem de script, sem padrões.

A forma mais básica de utilização do plugin .tmpl() é declarar seu template em uma variável e chamá-lo da seguinte forma:

[cce lang=&#8221;javascript&#8221;]
  
var noticias = [
	  
{
		  
titulo : &#8216;Notícia 1&#8242;,
		  
data_publicacao : &#8217;28/10/2010 20h31&#8217;,
		  
chamada : &#8216;Chamada da notícia 1&#8217;,
		  
link : &#8216;/noticia-1/&#8217;,
	  
},
	  
{
		  
titulo : &#8216;Notícia 2&#8242;,
		  
data_publicacao : &#8217;28/10/2010 20h32&#8217;,
		  
chamada : &#8216;Chamada da notícia 2&#8217;,
		  
link : &#8216;/noticia-2/&#8217;,
	  
},
	  
{
		  
titulo : &#8216;Notícia 3&#8242;,
		  
data_publicacao : &#8217;28/10/2010 20h33&#8217;,
		  
chamada : &#8216;Chamada da notícia 3&#8217;,
		  
link : &#8216;/noticia-3/&#8217;,
	  
}
  
];

var tpl\_noticia = &#8216;<li><h3>${titulo}</h3><span class=&#8221;data&#8221;>${data\_publicacao}</span><span>${chamada}</span><span><a href=&#8221;${link}&#8221;>Veja mais</a></span></li>&#8217;;

$.tmpl( tpl_noticia, noticias ).appendTo( &#8216;ul#noticias&#8217; );
  
[/cce]

Um problema do exemplo acima é que o template acaba ficando confuso dentro de uma variável. Uma outra forma de declarar um modelo seria utilizando a própria tag script, mas com um tipo diferente (text/x-jquery-tmpl):

[cce lang=&#8221;xml&#8221;]
  
<script id=&#8221;tpl-noticia&#8221; type=&#8221;text/x-jquery-tmpl&#8221;>
      
<li>
	  
<h3>${titulo}</h3>
	  
<span class=&#8221;data&#8221;>${data}</span>
	  
<p class=&#8221;chamada&#8221;>${chamada}</p>
	  
<a href=&#8221;${link}&#8221;>Leia mais</a>
     
</li>
  
</script>
  
[/cce]

Dessa forma é possível indentar o template HTML obtendo uma melhor organização/visualização do código.

## Caching

Antes de um template ser retornado através do método .tmpl(), ele é tranformado em uma função e depois executado. Uma forma de evitar esta execução toda vez que for retornado o plugin é utilizar o método .template() para criar uma versão em cache, otimizando a performance do script.

[cce lang=&#8221;javascript&#8221;]
  
// renderizando como plugin diretamente no objeto jQuery
  
$(&#8216;#tpl-noticia&#8217;).template(&#8216;tplNoticia&#8217;);

// associando diretamente a uma variável
  
var tplNoticia = $(&#8216;#tpl-noticia&#8217;).template();

// renderizando passando html/texto como parâmetro
  
$.template(&#8216;tplNoticia&#8217;, &#8216;

  * ${titulo}
&#8216;);
  
[/cce] 

No exemplo acima, a variável **tplNoticia** armazena a função responsável por nosso template. O método .template() é chamado de duas formas distintas: a primeira cria a função do template baseada no script com o id tpl-noticia. A segunda chamada funciona da mesma forma, só que dessa vez passamos o conteúdo do template diretamente como parâmetro. [Lembram do artigo sobre plugins?][2] Então, uma é um método público e a outra um utilitário jQuery.

## {{wrap}} e {{tmpl}}

As tags especiais {{wrap}} e {{tmpl}} possuem objetivos bem parecidos. A primeira permite a iteração e inclusão de trechos HTML dentro de um objeto de template. Já a tag {{tmpl}} utiliza, ao invés de trechos HTML, um outro objeto template.

[cce lang=&#8221;xml&#8221;]
  
<script id=&#8221;tplNoticia&#8221; type=&#8221;text/x-jquery-tmpl&#8221;>
      
{{wrap &#8220;#tableNoticia&#8221;}}
          
<h2>Notícia 1</h2>
          
<p><a href=&#8221;noticia-1&#8243;>Chamada da notícia 1</a></p>
          
<h2>Notícia 2</h2>
          
<p><a href=&#8221;noticia-2&#8243;>Chamada da notícia 2</p>
      
{{/wrap}}
  
</script>

<script id=&#8221;tableNoticia&#8221; type=&#8221;text/x-jquery-tmpl&#8221;>
      
<table>
        
<tbody>
          
<tr>
              
{{each $item.html(&#8220;h2&#8221;, true)}}
                  
<td>
                      
${$value}
                  
</td>
              
{{/each}}
          
</tr>
          
<tr>
              
{{each $item.html(&#8220;p&#8221;)}}
                  
<td>
                      
{{html $value}}
                  
</td>
              
{{/each}}
          
</tr>
        
</tbody>
      
</table>
  
</script>

<div id=&#8221;noticias&#8221;></div>

<script>
  
$(function(){
    
$(&#8220;#tplNoticia&#8221;).tmpl().appendTo(&#8220;#noticias&#8221;);
  
});
  
</script>
  
[/cce]

No código acima utilizamos a tag {{wrap}} para popular dados em uma tabela. A primeira linha (<tr>) da tabela recebe os títulos do nosso template de notícias &#8211; tudo o que estiver entre a tag <h2>. A iteração é feita através da tag {{each}}, explicada no [artigo anterior][1]. O que o exemplo acima faz é buscar todos os elementos H2 no item de template e adicionar o seu conteúdo, sem a tag, na célula da tabela. (Lembrando que você pode utilizar qualquer método jQuery no item de um loop dentro do template.)

Já a segunda linha da tabela recebe a chamada da notícia, preservando suas tags HTML &#8211; por isso a utilização da tag {{html}} no valor de cada notícia.

A tag {{tmpl}} é muito útil quando precisamos encadear ou utilizar uma espécie de include dentro de um outro template. No exemplo abaixo, o template para o título e o template da chamada da notícia estão separados. O método .tmpl() recebe apenas o template da chamada.

[cce lang=&#8221;xml&#8221;]
  
<script id=&#8221;tplNoticia&#8221; type=&#8221;text/x-jquery-tmpl&#8221;>
      
{{tmpl &#8220;#tplTitulo&#8221;}}
      
<p class=&#8221;chamada&#8221;>${chamada} <a href=&#8221;${link}&#8221;>Leia mais&#8230;</a></p>
  
</script>

<script id=&#8221;tplTitulo&#8221; type=&#8221;text/x-jquery-tmpl&#8221;>
      
<h2>${titulo}</h2>
      
<span class=&#8221;data&#8221;>${data_publicacao}</span>
  
</script>

<div id=&#8221;noticias&#8221;></div>

<script>
  
$(function(){
    
$( &#8220;#tplNoticia&#8221; ).tmpl( noticias ).appendTo( &#8220;#noticias&#8221; );
  
});
  
</script>
  
[/cce]

## Como e quando utilizar templates?

Templating é um conceito relativamente novo no jQuery, portanto, algumas funcionalidades ainda podem parecer confusas. Cabe a você decidir qual a melhor forma de definir e converter seus modelos. Por exemplo, se o seu template só vai ser utilizado uma única vez não é necessário utilizar caching (de repente não é necessário nem mesmo utilizar um template!).

Procure organizar bem seu código e pensar sempre em uma possível evolução do projeto &#8211; nesse caso, templates vão ser uma mão na roda.

 [1]: http://tableless.com.br/templates-e-jquery-parte-1
 [2]: http://tableless.com.br/anatomia-de-um-plugin-jquery