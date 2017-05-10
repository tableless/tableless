---
title: Carrinho de compras com drag and drop
author: Davi Ferreira
type: post
date: 2011-01-13
excerpt: O mercado de e-commerce não para de crescer e este crescimento vem acompanhando de diversas novidades e melhorias nas interfaces das lojas virtuais. Uma delas é opção de arrastar e soltar produtos no carrinho de compras e é isso que você aprende neste artigo.
url: /carrinho-de-compras-com-drag-and-drop/
tweetbackscheck:
  - 1356445540
shorturls:
  - 'a:3:{s:9:"permalink";s:61:"http://tableless.com.br/carrinho-de-compras-com-drag-and-drop";s:7:"tinyurl";s:26:"http://tinyurl.com/3qlwdgu";s:4:"isgd";s:19:"http://is.gd/MvBfd8";}'
twittercomments:
  - 'a:8:{i:56077022778245120;s:7:"retweet";i:56041067266576384;s:7:"retweet";i:56038506014842882;s:7:"retweet";i:146373139260125184;s:7:"retweet";i:146550053937491968;s:7:"retweet";i:145800535042297856;s:7:"retweet";i:154025101187235841;s:7:"retweet";i:153890668647956480;s:7:"retweet";}'
tweetcount:
  - 13
dsq_thread_id: 503039908
categories:
  - Artigos
  - Código
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - 2011
  - e-commerce
  - interface
  - JavaScript
  - JQuery
  - jquery-ui

---
Se você comprou alguma coisa recentemente no Submarino deve ter notado uma nova opção na interface do site: agora é possível arrastar os produtos exibidos na página para o seu carrinho, que fica exibido de forma permanente no topo do site.

De uma forma simples, vou tentar mostrar pra vocês como implementar uma solução parecida utilizando jQuery e sua biblioteca para interfaces, a <a href="http://jqueryui.com/" target="_blank">jQuery UI</a> &#8211; é nela que encontramos os plugins draggable() e droppable(), responsáveis, como os nomes sugerem, por toda nossa operação de arrastar e soltar produtos.

Também veremos um pouco sobre o vasto universo de animações com jQuery através do método animate(). Diferente do Submarino, onde a barra superior é um novo elemento e não o próprio carrinho original, a nossa irá acompanhar de forma fluida o movimento do usuário na página.

  * [Download do código-fonte][1]
  * <a href="http://tableless.github.com/exemplos/carrinho-compras/" target="_blank">Visualizar o exemplo no navegador</a>

## Estrutura básica

Vamos começar com um pouco de HTML/CSS para apresentar nossa loja. A página terá os seguintes elementos:

  * Barra localizada no topo (#carrinho-top) &#8211; essa barra, no carregamento inicial, estará relativa ao corpo do site. Assim que o usuário mover o mouse abaixo da metade da altura da barra, ela será &#8220;fixada&#8221; e acompanhará a navegação.
  * Box do mini-carrinho (#carrinho-container) &#8211; ficará dentro da barra no topo e é a área onde o usuário pode &#8220;soltar&#8221; os produtos.
  * Lista de produtos (#produtos) &#8211; a listagem de produtos, contendo os elementos que podem ser arrastados para o carrinho.

<pre class="lang-html">&lt;div&gt;
    &lt;div&gt;
        &lt;p&gt;Arraste produtos para esta área&lt;/p&gt;
    &lt;/div&gt;
    &lt;div&gt;
        &lt;ul&gt;
            &lt;li class="adicione"&gt;Arraste produtos para esta área&lt;/li&gt;
        &lt;/ul&gt;
    &lt;/div&gt;
&lt;/div&gt;

...

&lt;ul&gt;
     &lt;li class="produto-dd"&gt;&lt;h3&gt;Livro 1&lt;/h3&gt;&lt;p&gt;&lt;img src='_img/twa.jpg' width='75' height='90' /&gt;&lt;/p&gt;&lt;p class='preco-de'&gt;De: R$31,00&lt;/p&gt;&lt;p class='preco-por'&gt;Por: R$13,00&lt;/p&gt;&lt;/li&gt;
    ...
&lt;/ul&gt;
</pre>

<pre class="lang-css">div#carrinho-top{background-color:#C92D21;width:960px;color:#fff;border-bottom:1px dashed #fff;opacity:.8;position:relative;}
div#carrinho-info{padding:10px;}
div#carrinho-container{height:240px;position:absolute;width:240px;background-color:#fff;border:2px solid #c92d21;display:none;}
div#carrinho-container ul{overflow:auto;height:200px;list-style:none;margin:10px;}
div#carrinho-container ul li{color:#333;font-size:12px;border-bottom:1px dotted #ccc;text-align:center;margin:10px;}
ul#produtos li{float:left;background-color:#fff;-moz-box-shadow:5px 5px 5px #ccc;-webkit-box-shadow:5px 5px 5px #ccc;box-shadow:5px 5px 5px #ccc;width:270px;text-align:center;margin:15px;padding:10px;}
</pre>

## Animando a barra superior

O primeiro passo da nossa implementação é fazer com que a barra superior acompanhe os movimentos do usuário, fazendo com que a área de _drop_ dos produtos fique sempre visível. Para tornar isso possível associaremos uma função ao evento scroll da janela (window).

Toda vez que a a distância do scroll para o topo for maior do que a metade da altura da barra, o CSS será alterado para que a barra fique sempre visível e uma leve animação levará a barra para onde for o scroll.

<pre class="lang-jquery">// associando uma função ao evento scroll da janela
$(window).scroll(function(){
    // valor do scroll - distância entre a barrinha menor e o início do scroll
    var wtop	 	= $(this).scrollTop();
    // objeto da barra superior
    var carrinho 	= $('#carrinho-top');
    // objeto container do site
    var container	= $('#container');
    // altura do carrinho
    var cheight 	= $(carrinho).height();
    // distância do scroll é maior do que a altura da barra / 2 ?
    if( wtop &gt; ( cheight / 2 ) )
    {
        // adiciona uma margem ao container para evitar quebra do lay-out
        $(container).css('margin-top', cheight+'px');
        // transforma a position da barra em absolute
        $(carrinho)
            .css({
                position: 'absolute'
            })
            // anima utilizando a propriedade marginTop, com velocidade de 100ms
            .animate({
                marginTop: ( wtop - cheight ) + 'px'
            }, 100);
    }
});
</pre>

O funcionamento básico do método animate() segue o formato acima. O primeiro parâmetro é composto por um ou vários atributos CSS que farão a animação do elemento. No nosso caso, a barra será animada do valor original da sua margem superior até a especificada na função (a distância do scroll subtraída da altura da barra). Já o segundo parâmetro recebe um valor em milissegundos para efetuar a transição.

Precisamos agora de uma outra condição: quando o usuário voltar para o topo da página, nossa barra precisa recuperar o estado inicial, &#8220;fixado&#8221; no corpo:

<pre class="lang-jquery">// distância do scroll é menor do que a metade da altura da barra
else
{
    $(container).css('margin-top', 0);
    $(carrinho)
        .stop(true, true)
        .css({
            position: 'relative',
            marginTop: 0
        });
}
</pre>

## Definindo as áreas de drag and drop

Utilizando a biblioteca jQuery UI vamos definir os elementos que podem ser arrastados (qualquer li dentro da lista #produtos) e a área que vai recebê-los, no nosso caso o div #carrinho-container.

<pre class="lang-jquery">$('#produtos li').draggable({
    helper: 'clone',
    start: function()
    {
        $('#carrinho-container').show();
    }
});
</pre>

Os produtos, que podem ser arrastados, recebem o método **draggable**. Já ao box do carrinho é aplicado o método **droppable**. A chamada dos ítens recebe apenas o parâmetro helper e o evento start. O parâmetro helper pode receber os valores &#8216;original&#8217;, &#8216;clone&#8217; ou uma função. Utilizaremos &#8216;clone&#8217; que, como o nome sugere, clona o elemento original na ação de arrastar.

Já evento _start_ acontece assim que o elemento começa a ser arrastado. Quando um produto sofre a ação de arrastar, precisamos exibir o carrinho, que é nossa área de drop.

<pre class="lang-jquery">$('#carrinho-produtos').droppable({
    hoverClass: 'ui-state-hover',
    drop: function( event, ui )
    {
        // remove a marcação "arraste produtos para esta área"
        $(this).find('.adicione').remove();
        // busca o ID do produto no campo hidden
        var cod = ui.draggable.find('.produto-id').val();
        // verifica se o produto existe
        if( $(this).find('#clone-'+cod).length == 0 )
        {
            // adiciona o elemento li à lista de produtos do carrinho
            $('&lt;li&gt;&lt;/li&gt;').html(ui.draggable.html()).prependTo( this );
            // animação para indicar que o produto foi adicionado
            $(this).find('li:first').slideDown();
            // atualiza total de produtos do carrinho
            var total_produtos = $(this).find('li').length;
            $('#carrinho-info').html('&lt;p&gt;' + total_produtos + ' produto' + ( total_produtos &gt; 1 ? 's' : '' ) + '&lt;/p&gt;' );
        }
    }
});
</pre>

No método **droppable** utilizaremos também um parâmetro e um evento. O parâmetro é o hoverClass, que especifica uma classe que será aplicada a àrea de drop quando um ítem estiver sendo arrastado (vamos utilizar o padrão da jQuery UI). E o evento drop é acionado toda vez que um elemento for &#8220;solto&#8221; no carrinho. Nossa função primeiro verifica se o produto já existe no carrinho. Caso não exista, cria um novo elemento li na lista com os dados do produto.

Para uma lista completa dos parâmetros e eventos visite <a href="http://jqueryui.com/demos/draggable" target="_blank">jqueryui.com/demos/draggable</a> e <a href="http://jqueryui.com/demos/droppable" target="_blank">jqueryui.com/demos/droppable</a>

## Melhorando a exibição do carrinho

O código mostrado até agora tem um problema básico. Toda vez que o produto é adicionado o carrinho &#8220;some&#8221;. Seria legal que ele ficasse visível por uma certa quantidade detempo e só depois de um período de inatividade fosse escondido. Para isso vamos implementar um timer global na variável timerCarrinho.

Toda vez que o mouse estiver sobre o carrinho o timer é zerado. E, quando o mouse deixar a área, depois de 5 segundos, o carrinho é escondido.

<pre class="lang-jquery">var timerCarrinho = '';
$('#produtos li').draggable({
    helper: 'clone',
    start: function()
    {
        clearTimeout( timerCarrinho );
        $('#carrinho-container').show();
    }
});
$('#carrinho-container').mouseenter(function(){
    clearTimeout( timerCarrinho );
});

$('#carrinho-container').mouseleave(function(){
    var carrinho = $(this);
    timerCarrinho = setTimeout( function(){
        $(carrinho).slideUp();
    }, 5000 );
});
</pre>

## Dever de casa

Essa é uma versão básica de um carrinho drag and drop que pode sofrer diversas melhorias. Segue abaixo uma lista de implementações e funcionalidades novas pra vocês praticarem um pouco:

  * Remover animação da barra, fazendo todo o posicionamento via CSS;
  * Ao adicionar um produto que já exista no carrinho, aumentar a quantidade ao invés de ignorar;
  * Adicionar funcionalidade para excluir produtos do carrinho;
  * Salvar em cookie o carrinho do usuário, ou via AJAX, ou com o <a href="http://plugins.jquery.com/project/Cookie" target="_blank">plugin de cookies</a> do jQuery.

 [1]: http://tableless.com.br/uploads/2011/01/exemplo.zip