---
title: 'jQuery: dicas de otimização e performance'
author: Davi Ferreira
type: post
date: 2012-01-10
excerpt: Performance é um aspecto muito importante em aplicações web. Confira algumas dicas simples de como otimizar seu código jQuery.
url: /jquery-dicas-de-otimizacao-e-performance/
tweetbackscheck:
  - 1356436487
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4289";s:7:"tinyurl";s:26:"http://tinyurl.com/7k4rp23";s:4:"isgd";s:19:"http://is.gd/GjnsFV";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 533617737
categories:
  - Código
  - JQuery
tags:
  - JQuery
  - otimização
  - performance

---
A grande maioria dos desenvolvedores jQuery não se preocupa muito com performance e otimização. Afinal, o mantra do framework, &#8220;write less, do more&#8221;, envolve esconder a parte feia do Javascript e, muitas vezes, acrescentar camadas desnecessárias.

Neste artigo apresento algumas dicas de como melhorar a performance de sua aplicação jQuery. No entanto, vale lembrar que não é necessário otimizar nenhum código escrito previamente, já que a otimização dificilmente compensará o trabalho.

## #1: Mantenha-se atualizado

Procure utilizar sempre a última versão estável do jQuery. A cada nova versão lançada são introduzidas inúmeras melhorias de performance nos métodos do framework.

Da versão 1.3 para a 1.4, por exemplo, houve um ganho de 50% na performance da execução dos testes padrão do jQuery.

Fique ligado nas mudanças. O lançamento de uma nova versão vem sempre acompanhando de notas sobre as novas funcionalidades, um changelog, como [este aqui][1].

## #2: Não utilize jQuery!

Em alguns momentos não é necessário utilizar jQuery. Apesar de ser fácil de utilizar e muito mais bonito de ler, o framework é apenas mais uma camada no desenvolvimento, uma &#8220;maquiagem&#8221; para o Javascript.

Em projetos pequenos você pode, se quiser, abolir totalmente o jQuery: é realmente necessário incluir os ~30kb do framework? Não dá pra resolver com Javascript puro?

Já em projetos maiores, mesmo incluindo o jQuery, em alguns casos é melhor não utilizá-lo. Por exemplo:

<pre class="javascript">size: function() {
	return this.length;
},
</pre>

Acima está o código-fonte do método size, do jQuery. O que ele faz? Nada além de retornar o tamanho do objeto utilizando o método nativo length. Logo, é mais rápido utilizar diretamente o length!

<pre class="javascript">$('.menu').size()
$('.menu').length
</pre>

O mesmo vale para retornar o ID de um elemento:

<pre class="javascript">$(this).attr('id')
this.id
</pre>

O seletor $(this), aliás, somente deve ser utilizado quando for necessário um método que só existe no jQuery. Nos outros casos, sempre dê preferência ao this nativo do Javascript.

Também é comum utilizar jQuery para alterar o CSS de um elemento, por exemplo:

<pre class="javascript">$('#menu').css('display', 'block');
</pre>

Olhando o [código-fonte][2] do jQuery, o método .css() possui aproximadamente 20 linhas (sem contar outros métodos chamados). A atribuição acima poderia ser executada da seguinte forma, com uma única linha:

<pre class="javascript">document.getElementById('menu').style.display = 'block';
</pre>

Os próprios métodos jQuery possuem camadas dentro do framework. Ao invés de utilizar o método $.getJSON, por exemplo, você pode chamar diretamente o método $.ajax com os parâmetros type: &#8216;GET&#8217; e dataType: &#8216;json&#8217;.

Vale a pena dar uma olhada no [código-fonte][3] do jQuery para entender o que o framework faz por baixo dos panos e até que ponto é válido utilizá-lo.

## #3: Seletores

Procure sempre ser o mais específico possível em um seletor. Quanto mais específico, mais rápido. Opte sempre por utilizar o ID do elemento. Mesmo quando for preciso utilizar uma classe no seletor, utilize o ID do elemento pai.

Os seletores que utilizam o ID ou a tag de um elemento são mais rápidos por um simples motivo: ambos utilizam métodos nativos do Javascript document.getElementbyId() e document.getElementsByTagname().

Evite utilizar seletores com atributos e/ou pseudo-seletores, a menos que seja extremamente necessário.

Outra dica importante: dê preferência ao método .find() quando precisar achar elementos filhos de um elemento com ID. Por exemplo, ao invés de $(&#8216;#container p&#8217;) utilize $(&#8216;#container&#8217;).find(&#8216;p&#8217;), dessa forma o escopo da busca fica limitado ao primeiro objeto. O mesmo vale para seletores de classes e pseudo-seletores.

## #4: Cache de elementos

Esta é uma dica simples, mas que pode adicionar ganhos de performance consideráveis. Procure sempre armazenar em uma variável o objeto jQuery retornado por um seletor, principalmente quando o seletor está dentro de um loop.

Por exemplo:

<pre class="javascript">var menu = $('#menu');
var itens = ['Home', 'Contato', 'Sobre'];
for(x in itens)
	menu.append('

<li>
  '+itens[x]+'
</li>');
</pre>

Ao invés de:

<pre class="javascript">var itens = ['Home', 'Contato', 'Sobre'];
for(x in itens)
	$('#menu').append('

<li>
  '+itens[x]+'
</li>');
</pre>

No exemplo acima, o seletor $(&#8216;#menu&#8217;) seria executado 3 vezes, ou seja, o elemento seria buscado no DOM três vezes seguidas, sem nenhuma alteração.

Conforme citei na abertura do artigo, cachear seletores é uma prática que vai contra o &#8220;write less, do more&#8221; do jQuery. Seu código pode ficar um pouco mais &#8220;sujo&#8221;, mas, em contrapartida, fica também mais rápido.

## #5: Encadeamento de métodos

Encadear métodos sempre foi uma das funcionalidades mais legais do jQuery e, se você ainda não faz uso dessa técnica, é por aqui que você deve começar.

<pre class="javascript">$('#container').addClass('corpo');
$('#container').width(940);
$('#container').height(300);
</pre>

Vira:

<pre class="javascript">$('#container').addClass('corpo')
			   .width(940)
			   .height(300);
</pre>

Quase todos os métodos e plugins retornam (ou deveriam retornar) um objeto jQuery. Além de melhorar a leitura, essa prática também afeta diretamente a performance do seu código já que o seletor só é executado uma única vez.

## #6: DOM

Qualquer tipo de manipulação no DOM envolve um processo bem lento. No geral, você deve fugir desse tipo de implementação, principalmente se ela não possuir nenhum tipo de cache.

O ideal é manipular já com os dados finais e completos. Não manipule o DOM em um loop, por exemplo. 

Utilizando o exemplo da dica de caching, poderíamos alterar para ficar ainda mais otimizado:

<pre class="javascript">var menu = $('#menu');
var itens = ['Home', 'Contato', 'Sobre'];
var html = '';
for(x in itens){
	html += '

<li>
  '+itens[x]+'
</li>';
}
menu.append(html);
menu.show();
</pre>

Repare que o método .append() foi chamado apenas uma vez, já recebendo o HTML completo concatenado.

## #7: DRY (Don&#8217;t Repeat Yourself)

O jQuery disponibiliza um alto nível de personalização, permitindo que você [escreva seus seletores][4] e [seus plugins][5].

Evite repetir blocos de código. Evite repetir seletores. Evite repetir manipulações no DOM (faça tudo o que precisa fazer uma única vez!). Esta é uma dica muito importante para performance, já que qualquer código repetido significa alguns bytes ou kbytes a mais na sua aplicação.

Mathias Bynens disponibilizou um [uma apresentação genial][6] sobre DRY e Javascript, vale a pena conferir.

## Como medir a performance da sua aplicação?

O site [jsPerf][7] permite a criação de testes de performance para códigos javascript, utilizando jQuery ou não. É um bom lugar para você começar a comparar diferentes tipos de implementação. [Esta apresentação][8] dá dicas e ensina a utilizar a ferramenta.

Você também pode (e deve) utilizar a aba profile do Firebug e/ou do Chrome Developer Tools. [Aqui][9] tem um tutorial antigo, mas bacana, sobre o Firebug e [aqui][10] você encontra um tutorial sobre o Chrome Developer Tools.

 [1]: http://blog.jquery.com/2011/11/21/jquery-1-7-1-released/ ""
 [2]: https://github.com/jquery/jquery/blob/master/src/css.js#L121
 [3]: https://github.com/jquery/jquery ""
 [4]: http://tableless.com.br/jquery-seletores-personalizados/ ""
 [5]: http://tableless.com.br/anatomia-de-um-plugin-jquery/ ""
 [6]: http://speakerdeck.com/u/mathiasbynens/p/faster-javascript-execution-for-the-lazy-developer
 [7]: http://jsperf.com/
 [8]: http://www.slideshare.net/mathiasbynens/using-jsperf-correctly
 [9]: http://michaelsync.net/2007/09/10/firebug-tutorial-logging-profiling-and-commandline-part-ii
 [10]: http://www.youtube.com/watch?v=OxW1dCjOstE