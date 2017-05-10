---
title: Anatomia de um plugin jQuery
author: Davi Ferreira
type: post
date: 2010-09-14
excerpt: jQuery é um framework JavaScript, o mais sexy do pedaço, que transformou essa linguagem em uma das mais importantes ferramentas presentes no set de um webdesigner ou um desenvolvedor frontend. O que antes era chato e complicado, passou a ser extremamente dinâmico e elegante.
url: /anatomia-de-um-plugin-jquery/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356445418
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/anatomia-de-um-plugin-jquery";s:7:"tinyurl";s:26:"http://tinyurl.com/3dv2fyc";s:4:"isgd";s:19:"http://is.gd/8RzJRK";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039503
categories:
  - Artigos
  - Código
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - JavaScript
  - JQuery
  - plugin

---
Um dos grandes trunfos do jQuery é a sua vasta gama de plugins. Praticamente qualquer efeito, ação ou manipulação que você consiga imaginar já deve possuir um plugin. Caso contrário, quem sabe você mesmo não desenvolve um?

Neste artigo, você confere técnicas de como criar o seu próprio plugin. Vamos ver dois exemplos. O primeiro plugin adiciona classes ao primeiro e último ítem de uma lista, tabela, div etc. e o segundo simula a busca por textos do navegador Safari (aquele highlight bacana, como um marcador de textos, no termo procurado).

Vale lembrar ainda a importáncia de conhecer pelo menos um pouco de JavaScript antes de começar a trabalhar a fundo com jQuery.

#### O que é e como funciona um plugin jQuery?

Existem dois tipos de plugins: as funções e os métodos públicos. A função é anexada diretamente ao objeto jQuery e fica sem acesso a qualquer atributo/elemento encadeado.

<pre class="lang-javascript">jQuery.titulo = function(campeonato) {
         if($('div#flamengo').html()) {
             $('div#flamengo').append(campeonato);
         } else {
             alert(campeonato);
         }
     };</pre>

A função criada acima recebe um parâmetro **campeonato** e busca a existência de uma div com o id &#8220;flamengo&#8221; (o método **.html()** retorna null quando o elemento não está presente, logo é uma ótima maneira de validar sua existência). Se encontrar a div, ele adiciona o parâmetro passado ao seu conteúdo. Caso não encontre, nossa função utiliza o bom e velho **alert()**.

Para ser executada, a função titulo precisaria ser chamada assim:

<pre class="lang-javascript">$.titulo('Mundial 81');</pre>

O tipo de plugin acima deve ser desenvolvido apenas quando o mesmo for um utilitário, ou seja, que não necessite herdar propriedades do seletor. Um bom exemplo é o método isArray da API do jQuery.

Já plugins desenvolvidos como método público herdam toda a cadeia de propriedades e elementos disponíveis. Isso porque ele é chamado diretamente em um seletor jQuery. Dentro desse método, o termo **this** representa o objeto jQuery selecionado. É dessa forma que, provavelmente, você vai desenvolver a maioria dos seus plugins e é assim também que vamos desenvolver nossos plugins nesse tutorial.

Como ficaria nossa função titulo transformada em um método público do jQuery?

<pre class="lang-javascript">jQuery.fn.titulo = function(campeonato){
        this.append(campeonato);
        return this;
     };</pre>

A nova versão do plugin seria executada da seguinte maneira:

<pre class="lang-javascript">$('#flamengo').titulo('Libertadores 2011');</pre>

Muito parecido com os plugins de jQuery que você já implementou em seus sites, certo? Note que utilizamos o nome jQuery por extenso. Poderíamos ter utilizado seu apelido: $.fn.titulo = function([&#8230;]. No entanto, quando você precisar do jQuery no modo **no conflict** (com outros frameworks), é importante utilizar o nome por extenso para o plugin funcionar corretamente. Outra observação importante é nunca esquecer o ponto e vírgula ao final da função, senão o plugin não funciona quando o código for compactado. E, por último, é interessante que seu plugin sempre retorne o objeto jQuery (this), possibilitando assim o encadeamento com outros métodos.

O problema em utilizar a palavra jQuery e não o apelido ($) é que você precisaria utilizar sempre a palavra dentro do seu método para referenciar o framework. Para resolver isso, vamos utilizar uma função anônima, recurso muito legal do JavaScript, encapsulando nosso plugin. A função anônima recebe como parâmetro o objeto jQuery. Dentro dela, uma outra função engloba o plugin &#8220;convertendo&#8221; o objeto para seu apelido normal. O cifrão ($), nesse caso, pode ser qualquer apelido que você queira trabalhar dentro do seu plugin.

<pre class="lang-javascript">(function($) {
        // $ é o jQuery no escopo do plugin
        // Poderia ser qualquer apelido
        $.fn.titulo= function(campeonato){
            this.append(campeonato);
            return this;
         };
     })(jQuery);</pre>

Acima temos um modelo quase ideal para nossos plugins (ainda faltam as opções, veremos mais adiante).

Agora que vimos a estrutura básica, vamos estabelecer algumas metas para nossos plugins:

  * **Reutilizável:** o principal objetivo de um plugin é que ele venha a ser utilizado por mais de um projeto, mais de uma pessoa. Não adianta desenvolver um plugin muito específico;
  * **Leve & rápido:** tamanho é sempre documento no caso de JavaScript e arquivos web em geral. Aqui quanto menor, melhor. O plugin também deve ser otimizado para trabalhar com 1 ou 100 elementos;
  * **Flexível:** fácil de adaptar, com diversas opções. Tenha isso em mente quando for desenvolver um plugin. Evite utilizar IDs de elementos, nomes, classes e cores fixas.

#### Meu primeiro plugin: jquery.fila()

Não existe melhor maneira para aprender do que na prática, vamos então desenvolver nosso primeiro plugin. Para todo elemento que possua &#8220;filhos&#8221;, por exemplo uma lista ou uma tabela, o plugin vai adicionar uma classe ao primeiro e ao último ítem. Nosso plugin vai receber como opções os nomes das classes a serem adicionadas.

Vamos chamar nosso plugin de fila (FIrst-LAst). Ele terá um conjunto de opções básicas e, utilizando a função jQuery .extend, sobreescreverá o conjunto com opções passadas na chamada do plugin. As classes &#8216;first&#8217; e &#8216;last&#8217; serão adicionadas caso o plugin seja executado sem nenhum parâmetro.

<pre class="lang-javascript">(function($){
    $.fn.fila = function(opcoes) {

     // opções padrão
     var defaults = {
         first: 'first',
         last: 'last'
     };

     opcoes = $.extend(defaults, opcoes);

    };
})(jQuery);</pre>

Agora só precisamos varrer o seletor em busca de elementos que possuam &#8220;filhos&#8221;. Quando existir uma classe definida nas opções, o plugin adicionará a mesma aos elementos encontrados. Note que estamos utilizando os seletores &#8216;:first-child&#8217; e &#8216;:last-child&#8217; para buscar o primeiro e o último filho e adicionar as classes especificadas nas opções.

<pre class="lang-javascript">return this.each(function(){
         if(opcoes.first) $(this).find(':first-child').addClass(opcoes.first);
         if(opcoes.last) $(this).find(':last-child').addClass(opcoes.last);
     });</pre>

##### jQuery.fila.js

<pre class="lang-javascript">(function($){
    $.fn.fila = function(opcoes) {

     // opções padrão
     var defaults = {
         first: 'first',
         last: 'last'
     };

     opcoes = $.extend(defaults, opcoes);

     return this.each(function(){
         if(opcoes.first) $(this).find(':first-child').addClass(opcoes.first);
         if(opcoes.last) $(this).find(':last-child').addClass(opcoes.last);
     });

    };
})(jQuery);</pre>

Exemplos de uso do plugin:

<pre class="lang-javascript">// define ambas as classes
     $('ul').fila({
        first: 'primeiro',
        last: 'ultimo'
     });

     // opções padrão
     $('#resultado tbody').fila();

     // marca apenas o último filho
     $('div').fila({
        first: null,
        last: 'omega'
     });</pre>

#### Marcando textos com estilo

Nosso segundo plugin de exemplo vai fazer o seguinte: pesquisar por um termo em um texto e destacar os resultados. Começamos com um pouco de CSS, que vai servir para a nossa marcação:

<pre class="lang-javascript">span.marcaTexto {
        position: relative;
        z-index: 180!important;
        -moz-box-shadow: 0 0 1em #889;
        -webkit-box-shadow: 0 0 1em #888;
        box-shadow: 0 0 1em #889;
        padding: 4px;
    }</pre>

A ideia é adicionar o texto ao span marcaTexto, que também será o nome do plugin, mas você poderá utilizar a classe que quiser (essa opção estará presente na configuração). Uma das diferenças desse plugin em relação ao primeiro exemplo é que vamos aceitar tanto uma palavra como um conjunto de opções, dessa forma a chamada pode ser feita só com o termo a ser pesquisado ou com todas as opções disponíveis.

<pre class="lang-javascript">// opções padrão
     var defaults = {
         termo: '',
         corTexto: '#000',
         corFundo: '#ffff00',
         classe: 'marcaTexto'
     };

     // se o parâmetro passado for um array, carrega as opções
     if( $.isArray( opcoes ) )
     {
         opcoes = $.extend(defaults, opcoes);
     }
     // caso seja string, o usuário passou apenas o termo a ser marcado
     else
     {
         defaults.termo = opcoes;
         opcoes = defaults;
     }</pre>

Utilzamos a função jQuery.isArray para identificar se o parâmetro passado é um array ou uma string e assim definimos como tratar as opções. Além do termo a ser pesquisado, o plugin também pode receber as cores do texto e do fundo do span, além da classe CSS que define a estrutura básica da marcação.

Uma das dificuldades deste plugin é tratar tags HTML. Pra não complicar muito o exemplo, vamos simplesmente remover qualquer tag presente no texto utilizando a função text(). Para a pesquisa, um pouquinho de expressões regulares &#8211; precisamos verificar se o termo a ser pesquisado existe no seletor. Caso exista, o plugin entra em ação e marca o texto com o span e suas opções definidas anteriormente.

##### jquery.marcaTexto.js

<pre class="lang-javascript">(function($){
    $.fn.marcaTexto = function(opcoes) {
     // opções padrão
     var defaults = {
         termo: '',
         corTexto: '#000',
         corFundo: '#ffff00',
         classe: 'marcaTexto'
     };

     // se o parâmetro passado for um array, carrega as opções
     if( $.isArray( opcoes ) )
     {
         opcoes = $.extend(defaults, opcoes);
     }
     // caso seja string, o usuário passou apenas o termo a ser marcado
     else
     {
         defaults.termo = opcoes;
         opcoes = defaults;
     }

     // varre o seletor passado
     return this.each(function(){
         // armazena o texto do elemento
         var content = $(this).text();
         // pesquisa por termo no texto
         var re = new RegExp( opcoes.termo, 'i' );
         var result = content.match( re );
         // caso tenha encontrado ocorrências do texto...
         if( result )
         {
             // busca novamente, só que agora adicionando a marcação ao(s) termo(s)
             re = new RegExp( opcoes.termo, 'gi' );
             content = content.replace( re, '&lt;span class="' + opcoes.classe + '" style="color: ' + opcoes.cortexto + ';background-color: ' + opcoes.corfundo + '"&gt;' + opcoes.termo + '&lt;/span&gt;');
             // altera o HTML do elemento original
             $(this).html( content );
         }
     });

    };
})(jQuery);</pre>

Esse plugin tem diversas &#8220;falhas&#8221; que vão ficar de dever de casa. Por exemplo, atualmente ele ignora maiúsculas e minúsculas. Poderíamos ter uma opção definindo que tipo de busca utilizar, case sensitive ou insenstive. Outra falha é que ele busca qualquer elemento, mesmo um que não tenha conteúdo. Para esses casos, como um table, ele deveria buscar o conteúdo em seus filhos. E, conforme mencionado anteriormente, é necessário fazer com que o plugin preserve as tags HTML encontradas no texto.

#### Compartilhe seus plugins!

No início pode ser um pouco difícil saber identificar o que é transformado em um plugin e o que continua como um simples trecho de código. O que eu costumo fazer, até para praticar, é olhar elementos em interfaces de aplicativos: filtros, pesquisas, animações, botões. Aplicativos desktop são uma ótima inspiração para o desenvolvimento de plugins jQuery.

Espero que esse tutorial tenha explicado bem a arte de desenvolver plugins para jQuery e espero ainda mais que vocês possam criar e compartilhar novos plugins, a comunidade web brasileira precisa disso.

E, não esqueça: se você já tiver desenvolvido um plugin, deixe o link nos comentários.

  * [Download dos plugins][1]
  * [Exemplo online: jquery.fila][2]
  * [Exemplo online: jquery.marcaTexto][3]

 [1]: http://tableless.com.br/uploads/2010/09/plugins.zip
 [2]: http://tableless.github.com/exemplos/anatomia-plugin-jquery/fila.html
 [3]: http://tableless.github.com/exemplos/anatomia-plugin-jquery/