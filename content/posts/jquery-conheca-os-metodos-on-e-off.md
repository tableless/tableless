---
title: 'jQuery: conheça os métodos on() e off()'
author: Davi Ferreira
type: post
date: 2012-03-13
excerpt: A versão 1.7 do framework jQuery implementa dois novos métodos que pretendem acabar de vez com a confusão gerada em torno da associação de eventos.
url: /jquery-conheca-os-metodos-on-e-off/
tweetbackscheck:
  - 1356439497
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5521";s:7:"tinyurl";s:26:"http://tinyurl.com/6nq99g3";s:4:"isgd";s:19:"http://is.gd/Rw4F23";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 609422080
categories:
  - JavaScript
  - JQuery
tags:
  - eventos
  - JavaScript
  - JQuery

---
Em outubro de 2010 escrevi um [artigo][1] aqui mesmo no Tableless sobre a associação dinâmica de eventos. Na época, reinava uma confusão sobre quais métodos utilizar e quando utilizá-los. Eram três as opções: bind(), live() e delegate().

Com o lançamento da versão 1.7 do jQuery, dois métodos definitivos (assim espero) devem acabar com a confusão em torno da associação de eventos: os métodos on() e off().

## Eventos diretos

A associação direta de eventos ocorre quando o seletor (ou escopo) é omitido nos parâmetros do on(). Por exemplo:

<pre class="lang-javascript">function exibeMenu(e) {
  e.preventDefault();
  $('#menu').show();
}
$('#lnk-menu').on('click', exibeMenu);
</pre>

No código acima, o elemento com id #lnk-menu recebe uma associação no evento click para executar a função exibeMenu(). A associação ocorre de forma direta, ou seja, quando o on() é executado o evento passa a estar associado ao elemento, antes mesmo do clique ocorrer.

Essa opção equivale ao bind() e deve ser utilizada em casos de elementos únicos, ou com poucos elementos, para evitar problemas de performance.

## Múltiplos eventos

Também é possível associar múltiplos eventos a um ou mais elementos. Para isso, basta passar um mapa onde cada chave representa um evento ao invés de um evento como string:

<pre class="lang-javascript">$('#lnk-menu').on({
  click: function(){
    $('#menu').show();
  },
  dblclick: function(){
    $('#submenu').show();
  },
  mouseenter: function(){
    $(this).addClass('ativo');
  }
});
</pre>

## Removendo associações de eventos diretos

Remover associações de eventos diretos é simples:

<pre class="lang-javascript">$('#lnk-menu').off();</pre>

Para remover eventos específicos, mantendo qualquer outra associação, basta informar o nome do evento:

<pre class="lang-javascript">$('#lnk-menu').off('click');</pre>

## Eventos delegados

A delegação de eventos (antigos live() e delegate()) ocorre quando passamos um ou mais seletores nos parâmetros do on. O evento não será
  
associado diretamente quando o código for executado, tampouco será executado para o seletor que chama o on() e sim para os elementos descendentes que se encaixem no parâmetro passado.

A associação ocorre quando o evento é acionado. Esse tipo de associação funciona tanto para elementos já presentes no DOM como para elementos criados posteriormente.

<pre class="lang-javascript">function exibeConteudo(e){
  $(this).find('conteudo').fadeIn();
}

$('table').on('click', 'a', exibeConteudo);
</pre>

## Removendo a associação de eventos específicos

Em alguns momentos será preciso associar eventos diretos e, ao mesmo tempo, delegar eventos. Nesses casos, é possível remover apenas os eventos delegados utilizando o parâmetro especial &#8220;**&#8221;.

<pre class="lang-javascript">$('a').off('click', '**');</pre>

Outra opção é remover a associação com base na função utilizada:

<pre class="lang-javascript">$('#lnk-menu').off('click', 'a', exibeConteudo);</pre>

## Namespaces

Uma importante implementação do on() é a possibilidade de utilizar namespaces nos eventos &#8211; uma grande novidade para desenvolvedores de plugins. Um evento pode, agora, ser associado a um namespace específico, facilitando o controle sobre associações específicas de um plugin ou uma funcionalidade.

<pre class="lang-javascript">$('#lnk-menu').on('click.menu', exibeMenu);
$('.menu-item').on('mouseleave.menu', escondeMenu);

$('#lnk-menu, .menu-item').off('.menu');
</pre>

## Enviando dados para o evento

O método on() também permite enviar dados específicos para um evento. O objeto de dados fica associado ao objeto do evento.

<pre class="lang-javascript">function exibeMenu(e) { 
  $('.ativo').text(e.data.descricao);
}

$('#lnk-home').on('click', { descricao: 'Página inicial' }, exibeMenu);
$('#lnk-sobre').on('click', { descricao: 'Sobre a empresa' }, exibeMenu);
</pre>

No exemplo acima, cada link passa uma descrição diferente durante o evento. Essa descrição passa a ser o conteúdo dos elementos com a classe &#8220;.ativo&#8221;.

## Este evento se autodestruirá…

O método .one() poderia ter entrado na lista dos [métodos desconhecidos do meu último artigo][2], já que existe desde a versão 1.1 do jQuery. No entanto, junto com a implementação do .on() ele ganhou uma nova cara.

Sua implementação segue as mesmas regras do .on() com uma importante diferença: o evento associado é executado apenas uma vez. Após a execução a associação é automaticamente removida, seja ela uma associação direta ou delegada.

<pre class="lang-javascript">$('#lnk-menu').one('click', function() {
  alert('Este evento não será mais executado.');
});
</pre>

Caso o seletor possua mais de um elemento, o evento será associado uma vez a cada um deles, ou seja, cada elemento possuirá uma execução do evento.

* * *

Essas são as novidades com relação a eventos utilizando jQuery. Os métodos .on() e .off() devem &#8220;matar&#8221; seus antecessores (.live() e .delegate()) e padronizar de uma vez por todas a associação de eventos em aplicações.

 [1]: http://tableless.com.br/associando-eventos-dinamicamente/ "jQuery: associando eventos dinamicamente"
 [2]: http://tableless.com.br/jquery-metodos-desconhecidos/ "jQuery: métodos desconhecidos"