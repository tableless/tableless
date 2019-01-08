---
title: Associando eventos dinamicamente
authors: Davi Ferreira
type: post
date: 2010-10-04
excerpt: 'Você sabia que é possível associar eventos antes mesmo dos elementos estarem presentes no DOM? Conheça os métodos .live() e .delegate() e aprenda a interagir com ações do usuário no seu site. '
url: /associando-eventos-dinamicamente/
categories:
  - Javascript
  - Artigos
  - Código
tags:
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

 [1]: https://api.jquery.com/category/events/
 [2]: https://tableless.com.br/exemplos/associando-eventos-dinamicamente/ "Exemplo de associação de eventos dinâmicos no JQuery"