---
title: Tudo que você gostaria de saber sobre plugins jQuery e ninguém teve paciência de explicar
author: Zeno Rocha
type: post
date: 2012-11-02
excerpt: Pra você que cansou de ser um mero manipulador de plugins alheios
url: /tudo-que-voce-gostaria-de-saber-sobre-plugins-jquery-e-ninguem-teve-paciencia-de-explicar/
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5999";s:7:"tinyurl";s:26:"http://tinyurl.com/7ppv8w6";s:4:"isgd";s:19:"http://is.gd/52YlXT";}'
twittercomments:
  - 'a:0:{}'
tweetbackscheck:
  - 1356447386
dsq_thread_id: 672764821
categories:
  - JQuery

---
Então quer dizer que você anda brincando com jQuery. Volta e meia utiliza uns plugins que mais parecem mágica e se duvidar até se aventurou em criar o seu próprio, acertei?

Acontece que, caso você já saiba desenvolver os seus, talvez possam existir melhores formas de escrevê-lo. Será que você está seguindo as melhores práticas? Será que realmente entende o que está acontecendo por trás de cada linha?

Hoje vou tentar responder as dúvidas mais frequentes, explorando as melhores práticas para se construir um plugin. E no fim lhe mostrar um padrão interessante que você pode seguir agora que já entendeu os conceitos.

A ideia aqui não é simplesmente mostrar como criar um plugin, mas sim como criar direito, explorando tudo o que o jQuery tem de melhor para nos oferecer.

## Por que eu deveria construir um plugin?

Encapsulamento e reaproveitamento de código, essas são as palavras-chave. Se você está codificando algo que talvez sirva para futuros projetos, pode ser uma boa encapsular tudo isso em um plugin.

## Entendi, quero criar um! Como faz?

Existem diversas formas, mas vamos começar com essa:

<pre class="lang-javascript">$.fn.meuPlugin = function() {
    // aqui vem a lógica
};</pre>

Esse é o mínimo que você precisa para iniciar o desenvolvimento de um plugin, basta adicionar uma propriedade ao **$.fn**.

Por mais trivial que isso possa parecer, muita gente não entende o que está acontecendo por trás disso exatamente. Portanto, antes de evoluirmos esse padrão, vamos recorrer ao [código fonte da biblioteca][1], na sua versão mais recente, para entender de verdade esse pequeno trecho de código.

## O que significa o cifrão ($) ?

O famoso **$** nada mais é do que um “apelido” para o objeto **jQuery**. Próximo ao fim do [código fonte da biblioteca][1] encontramos a seguinte definição:

<pre class="lang-javascript">window.jQuery = window.$ = jQuery;</pre>

Isso significa que o mesmo objeto em memória pode ser referenciado de diversas formas: **window.jQuery**, **window.$**, **jQuery** ou simplesmente **$**.

## Qual a diferença entre $.meuPlugin e $.fn.meuPlugin?

Possivelmente você já se deparou com plugins que não utilizavam a propriedade **.fn**. Mas afinal, por que eu deveria utilizar o **.fn**? Por que não apenas **$.meuPlugin** ao invés de **$.fn.meuPlugin**?

Novamente, ao nos aventurarmos no [código fonte][1] percebemos, logo nas primeiras linhas, como o objeto **jQuery** é definido.

<pre class="lang-javascript">var jQuery = function( selector, context ) {
    return new jQuery.fn.init( selector, context, rootjQuery );
}</pre>

Note que **jQuery** é uma função e no Javascript uma função é também um objeto do tipo **Function**. Por isso **jQuery.meuPlugin** (ou **$.meuPlugin**) irá atribuir **meuPlugin** para o objeto jQuery do tipo **Function**.

Dito isso, voltamos ao [código fonte][2] e veremos que **jQuery.fn** é a mesma coisa que dizer **jQuery.prototype**.

<pre class="lang-javascript">jQuery.fn = jQuery.prototype;</pre>

Portanto, a cada vez que você atribuir uma função (ou propriedade) para **jQuery.fn**, como em **$.fn.meuPlugin**, a função estará disponível para todas as instâncias desse objeto.

Isso é importante, pois quando você invoca a função **$()**, como em **$(&#8220;#algumID&#8221;)**, uma nova instância é criada nessa linha:

<pre class="lang-javascript">return new jQuery.fn.init( selector, context );</pre>

E essa instância terá todos os métodos que atribuirmos ao **prototype**, mas não todos os métodos que foram atribuídos direto ao objeto **Function**.

Logo, vá de **.fn**.

## Evite conflitos

Sabia que existem outras bibliotecas Javascript que também utilizam o símbolo cifrão para referenciar seus objetos? Pois é, isso pode lhe causar uma baita dor de cabeça se utilizar apenas aquele primeiro padrão proposto.

Logo, uma boa prática seria encapsular a lógica do plugin em uma função anônima. Assim, garantimos que não irá haver conflito entre o **$** do jQuery com o **$** de outras bibliotecas.

<pre class="lang-javascript">(function( $ ){
    $.fn.meuPlugin = function() {
        // aqui vem a lógica
    }; 
})( jQuery );</pre>

Dessa forma mapeamos o **$** para que não seja afetado por nada fora desse escopo.

## Não quebre a corrente

Então, você já entendeu como funcionam algumas coisas, vamos criar nosso primeiro plugin! Começaremos com o clássico exemplo de um Tooltip (aquelas caixinhas que aparecem no mouseover).

Criamos então a chamada para o plugin a partir de determinado seletor:

<pre class="lang-javascript">$(function() {
    $(".BlaBlaBla").tooltip();
});</pre>

E código do nosso plugin ficará definido assim:

<pre class="lang-javascript">(function( $ ){
    $.fn.tooltip = function() {
        this.css({ background: 'yellow' });
    }; 
})( jQuery );</pre>

Aparentemente tudo certo, já que o plugin funciona direitinho, certo?

Na verdade não, pois dessa forma estamos ferindo um dos princípios importantes que diferem os plugins bons dos ruins, e esse princípio se chama encadeamento.

No jQuery é muito comum vermos declarações do tipo:

<pre class="lang-javascript">$('div').show().addClass('BlaBlaBla').fadeIn();</pre>

Isso, porque é possível encadear diversas chamadas, a um mesmo seletor. E uma excelente prática por sinal, já que não criamos diversas instâncias como em:

<pre class="lang-javascript">$('div').show();
$('div').addClass('BlaBlaBla');
$('div').fadeIn();</pre>

Para permitirmos comportamento similar com nosso plugin basta retornar o **this**.

<pre class="lang-javascript">(function( $ ){
    $.fn.tooltip = function() {
        return this.each (function() {
            $(this).css({ background: 'yellow' });
        });
    }; 
})( jQuery );</pre>

Assim, além de garantirmos o encadeamento, também manipulamos a coleção passada para o plugin através do método **each**, muito similar a um loop com **for** por exemplo.

## Como passar parâmetros e lidar com eles depois?

E que tal se evoluíssemos nosso plugin e resolvessemos passar como parâmetro a cor de fundo do nosso elemento.

<pre class="lang-javascript">$(function() {
    $(".BlaBlaBla").tooltip({
      'corDeFundo' : 'blue'
    });
}); </pre>

Agora preparamos nosso plugin para receber os parâmetros através da variável **options** e aplicamos a propriedade **corDeFundo** no **background**.

<pre class="lang-javascript">(function( $ ){
    $.fn.tooltip = function(options) {
        return this.each (function() {
            $(this).css({ background: options.corDeFundo });
        });
    }; 
})( jQuery );</pre>

Maravilha, funcionou! Mas o que acontece se você resolve mais tarde não passar como parâmetro a cor de fundo? Nosso plugin quebra.

Portanto, não podemos nos esquecer de que precisamos nos preparar para receber esse conjunto de opções e assegurar que, caso não seja passado nenhum valor como parâmetro, nós possamos lidar com valores padrão.

<pre class="lang-javascript">(function( $ ){
    $.fn.tooltip = function(options) {

        var defaults = {
          'corDeFundo' : 'yellow'
        };

        var settings = $.extend( {}, defaults, options );

        return this.each(function() {
            $(this).css({ background: settings.corDeFundo });
        });

    }; 
})( jQuery );</pre>

Para isso recorremos a função [$.extend][3] que irá buscar os valores passados pela variável **options** e mesclar com os valores definidos na variável **defaults**, armazenando em outra variável chamada **settings**.

## A procura da batida perfeita

Esse é só o começo para você que deseja se aprofundar um pouquinho mais nessa arte de criar plugins, para entender mais visite o [guia oficial][4].

Mesmo que a ideia de se formar um padrão único para criar plugins seja utópico, sugiro fortemente que dê uma olhadinha no [jQuery Boilerplate][5], lá você vai encontrar um padrão bem sólido para iniciar seus projetos, sem contar que a versão traduzida para português foi lançada hoje!

Mas se o buraco for mais em baixo e você for lidar com plugins [stateful][6] que controlam o estado dos objetos, confira o [jQuery UI Widget Factory][7].

Lembre-se que o jQuery não é apenas uma caixa preta que faz mágicas pra você. Aventure-se no código fonte e verá que não é nada muito diferente do que você já faz com JavaScript puro.

E é isso, espero que depois desse artigo, você tenha evoluido de um simples “manipulador de plugins” para um criador de fato. Até a próxima!

 [1]: http://code.jquery.com/jquery-1.7.1.js
 [2]: http://code.jquery.com/jquery-latest.js
 [3]: http://api.jquery.com/jQuery.extend/
 [4]: http://docs.jquery.com/Plugins/Authoring
 [5]: http://jqueryboilerplate.com/
 [6]: http://en.wikipedia.org/wiki/State_(computer_science
 [7]: http://wiki.jqueryui.com/w/page/12138135/Widget%20factory