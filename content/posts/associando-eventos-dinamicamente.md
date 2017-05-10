---
title: Associando eventos dinamicamente
author: Davi Ferreira
type: post
date: 2010-10-04
excerpt: 'Você sabia que é possível associar eventos antes mesmo dos elementos estarem presentes no DOM? Conheça os métodos .live() e .delegate() e aprenda a interagir com ações do usuário no seu site. '
url: /associando-eventos-dinamicamente/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356395239
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/associando-eventos-dinamicamente";s:7:"tinyurl";s:26:"http://tinyurl.com/44bj9hd";s:4:"isgd";s:19:"http://is.gd/Ezuwh1";}'
twittercomments:
  - 'a:88:{i:10234654846091264;s:7:"retweet";i:10226583423950848;s:7:"retweet";i:10132079106850816;s:7:"retweet";i:10122776652288000;s:7:"retweet";i:10117978813112321;s:7:"retweet";i:10117379405119489;s:7:"retweet";i:10107142543515648;s:7:"retweet";i:10083882288283648;s:7:"retweet";i:10062992011952128;s:7:"retweet";i:10061347316305920;s:7:"retweet";i:10054112229986305;s:7:"retweet";i:10040333253484544;s:7:"retweet";i:10040002083819520;s:7:"retweet";i:10039999428829184;s:7:"retweet";i:10038907974451200;s:7:"retweet";i:10034934429261824;s:7:"retweet";i:10029357141598209;s:7:"retweet";i:10028990265827328;s:7:"retweet";i:10020505109139457;s:7:"retweet";i:10019872658427904;s:7:"retweet";i:10015569944248320;s:7:"retweet";i:10015525656596480;s:7:"retweet";i:10012496672849920;s:7:"retweet";i:10012187393269761;s:7:"retweet";i:10008580115664896;s:7:"retweet";i:10000230804094978;s:7:"retweet";i:9999302088728576;s:7:"retweet";i:9997672656150528;s:7:"retweet";i:9997597276119040;s:7:"retweet";i:9997058303852544;s:7:"retweet";i:9995831633518592;s:7:"retweet";i:9994332962557952;s:7:"retweet";i:9993677065691136;s:7:"retweet";i:9992560642625536;s:7:"retweet";i:9992271797690369;s:7:"retweet";i:9992240164249600;s:7:"retweet";i:9992095951491072;s:7:"retweet";i:9991684825808898;s:7:"retweet";i:9991632740941824;s:7:"retweet";i:9991357779156992;s:7:"retweet";i:9990925174439936;s:7:"retweet";i:9990894933516288;s:7:"retweet";i:9990371127857152;s:7:"retweet";i:9989984597581824;s:7:"retweet";i:9989096608890880;s:7:"retweet";i:9988548845379584;s:7:"retweet";i:9988461419302912;s:7:"retweet";i:9988181130747904;s:7:"retweet";i:9987707337973760;s:7:"retweet";i:9985191024005120;s:7:"retweet";i:9984341899747329;s:7:"retweet";i:9984215722500096;s:7:"retweet";i:9982235306364928;s:7:"retweet";i:9981930791501825;s:7:"retweet";i:9981704236171264;s:7:"retweet";i:9981424417374208;s:7:"retweet";i:9981055041806336;s:7:"retweet";i:9980633052876800;s:7:"retweet";i:9980374515982337;s:7:"retweet";i:9980117610668034;s:7:"retweet";i:9979681377886209;s:7:"retweet";i:9979246806040576;s:7:"retweet";i:9978974948032512;s:7:"retweet";i:9978490958905345;s:7:"retweet";i:9978204898983936;s:7:"retweet";i:9978173668204546;s:7:"retweet";i:9978092105768960;s:7:"retweet";i:9977978968612864;s:7:"retweet";i:9977821380214784;s:7:"retweet";i:9977782935232513;s:7:"retweet";i:9977709966925825;s:7:"retweet";i:9977617549627392;s:7:"retweet";i:9977443037224960;s:7:"retweet";i:9977406093795328;s:7:"retweet";i:9977076308246528;s:7:"retweet";i:9977048034451456;s:7:"retweet";i:9976948973375489;s:7:"retweet";i:9976926789701636;s:7:"retweet";i:9976719574310912;s:7:"retweet";i:9976633599463425;s:7:"retweet";i:9976534290927616;s:7:"retweet";i:9976158812643328;s:7:"retweet";i:9975908962144256;s:7:"retweet";i:9975539590762496;s:7:"retweet";i:26971966841815040;s:7:"retweet";i:26630448339755008;s:7:"retweet";i:272038225881747456;s:7:"retweet";i:283267680818057217;s:7:"retweet";}'
tweetcount:
  - 829
dsq_thread_id: 503039602
categories:
  - Artigos
  - Código
  - JavaScript
  - JQuery
tags:
  - JavaScript
  - JQuery

---
No JavaScript, eventos correspondem à qualquer interação do usuário com o navegador. O clássico addEventListener ganhou sua versão no jQuery através do método .bind() ou com seus respectivos métodos (.click(), .focus(), .keyup() etc. ). Da mesma forma, é possível remover/desassociar um evento através do método .unbind(). O assunto eventos é tão rico que merece um outro artigo.

Neste, vou falar dos métodos .live() e .die() e dos novos .delegate() e .undelegate(). O que eles fazem é trabalhar com esse eventos em elementos criados dinamicamente.

#### Dicas rápidas

Antes de começar, vamos a algumas dicas rápidas sobre a associação de eventos no jQuery.

Por exemplo, você sabia que é possível associar mais de um evento? Basta utilizar o método bind() com os eventos separados por espaço:

<pre lang="javascript" line="1">$('input[type="text"]').bind('mouseenter mouseleave', function(){
	$(this).toggleClass('ativo');
});</pre>

Ou então, para o caso de funções diferentes:

<pre lang="javascript" line="1">$('a').bind({
	mouseover: function(){
		$(this).addClass('ativo');
		$('#menu').slideDown();
	},
	mouseout: function(){
		$(this).removeClass('ativo');
		$('#menu').slideUp();
	}
});</pre>

O exemplo acima pode ser substiuído com o evento personalizado do jQuery, .hover(), que define uma função para o mouseover e outra para o mouseout:

<pre lang="javascript" line="1">$('a').hover(
	function(){
		$(this).addClass('ativo');
		$('#menu').slideDown();
	},
	function(){
		$(this).removeClass('ativo');
		$('#menu').slideUp();
	});
</pre>

Para uma lista completa de eventos e recursos visite o link [api.jquery.com/category/events/][1].

#### Live and let die

Desde a versão 1.4 do jQuery, graças ao método .live() é possível associar eventos a elementos adicionados dinamicamente em uma página. Toda vez que um novo elemento for criado, o mesmo receberá o evento associado via .live(). Ou seja, o .live() funciona tanto para elementos que já existam no DOM como para aqueles que serão adicionados após o carregamento da página.

Antes dessa funcionalidade, o link criado no exemplo abaixo não herdaria a propriedade do link que ativou o evento click:

<pre lang="javascript" line="1">$(function(){
	$('a.lnk-confirmar').click(function(e){
		$('<a class="lnk-confirmar">novo</a>').insertAfter(this);
		alert('Clique');
		e.preventDefault();
	});
});</pre>

Com o .live() resolvemos este problema, ficando assim:

<pre lang="javascript" line="1">$('a.lnk-confirmar').live('click', function(e){
	$('<a class="lnk-confirmar">novo</a>').insertAfter(this);
	alert('Clique');
	e.preventDefault();
});</pre>

Dessa forma, tanto os elementos já existentes, quanto os criado dinamicamente, receberão a função no evento click. Diferente do método .bind(), não precisamos esperar o DOM estar todo carregado ($(function(){&#8230;})).

E assim como utilizamos o .unbind() para dessassociar eventos anexados via .bind(), temos o .die() como companheiro do .live(). O .die() remove todos ou alguns eventos especificados, anulando qualquer .live() declarado anteriormente.

<pre lang="javascript" line="1">$('a.add').live('click', function(e){
	var total = $('ul#lista li').length;
	$('ul#lista').append('
	

<li>
  Ítem ' + ( total + 1 ) +'
</li>
');
	 // armazenamos o total antes de adicionar a última
	if( total == 9 )
	{
		$('a.add').die('click');
	}
	e.preventDefault();
});</pre>

O link com a classe add vai adicionar ítens à uma lista. Quando o número de ítens for maior do que 10, e evento click é removido do link.

A partir da versão 1.4.1 do jQuery o método .live() também aceita múltiplos eventos como parâmetro, conforme mostrado anteriormente no .bind().

#### Estendendo a funcionalidade do .live()

Um dos problemas do .live() e que foi assunto para muita polêmica é que ele não funciona com encadeamento de métodos, a não ser que esteja no topo. Por exemplo, o código abaixo retorna erro:

<pre lang="javascript" line="1">$('body').children().find('li').live('click', function(){
	$(this).toggleClass('ativo');
});</pre>

Encadeamento é uma das principais características do jQuery, e por isso o .live() foi alvo de muitas críticas. Para resolver a situação, a versão 1.4.2 ganhou os métodos .delegate() e .undelegate().

<pre lang="javascript" line="1">$('ul').parent().parent().delegate('input[type="text"]', 'hover', function(){
	$(this).val('Passei aqui!');
});

$('ul').parent().parent().undelegate('input[type="text"]', 'hover');</pre>

Note que com o delegate não há problemas com encadeamento. Sua chamada é um pouco diferente, recebendo como primeiro parâmetro o seletor a ser utilizado e depois o evento e sua função/ação.

#### Qual método utilizar: live ou delegate?

Com a chegada do .delegate() o .live() está, provavelmente, com os dias contados. Seu propósito inicial era bacana, mas o nome foi muito mal escolhido e o fato de não aceitar encadeamento é quase que inadmissível em se tratando de um método jQuery. A tendência é que o .live() passe a ser _deprecated_ nas próximas versões.

[Clique aqui para ver os exemplos em ação.][2]

 [1]: http://api.jquery.com/category/events/
 [2]: http://tableless.com.br/exemplos/associando-eventos-dinamicamente/ "Exemplo de associação de eventos dinâmicos no JQuery"