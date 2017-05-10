---
title: Habilitando tags em fotos com jQuery
author: Davi Ferreira
type: post
date: 2011-06-20
excerpt: Aprenda a desenvolver uma interface para permitir que usuários apliquem tags/marcações nas fotos do seu aplicativo.
url: /habilitando-tags-em-fotos-com-jquery/
tweetbackscheck:
  - 1356391426
shorturls:
  - 'a:3:{s:9:"permalink";s:60:"http://tableless.com.br/habilitando-tags-em-fotos-com-jquery";s:7:"tinyurl";s:26:"http://tinyurl.com/3wj45vf";s:4:"isgd";s:19:"http://is.gd/ArPxDe";}'
twittercomments:
  - 'a:11:{i:146190911578181632;s:7:"retweet";i:146190740920336384;s:7:"retweet";i:146190740811292672;s:7:"retweet";i:146190740911951872;s:7:"retweet";i:154981204230279170;s:7:"retweet";i:154979761498767362;s:7:"retweet";i:154978857068404736;s:7:"retweet";i:154978179969331200;s:7:"retweet";i:159802454521810945;s:7:"retweet";i:159801048658219009;s:7:"retweet";i:164941506757668865;s:7:"retweet";}'
tweetcount:
  - 11
dsq_thread_id: 503019008
categories:
  - Código
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - interface
  - JQuery
  - jquery-ui

---
Marcar seus amigos nas fotos publicadas é um dos recursos mais populares do Facebook. Neste artigo você confere como implementar uma interface semelhante utilizando o plugin _imgAreaSelect_. Veremos apenas a parte client-side, sem armazenar as informações das tags, portanto, sem nenhuma programação server-side.

### Nosso HTML/CSS

O primeiro passo é criar um HTML com a foto de exemplo. Começamos adicionando ao _head_ chamadas para os scripts e as folhas de estilo.

<pre class="lang-html">&lt;script type="text/javascript" src="js/jquery.min.js"&gt;
&lt;script type="text/javascript" src="js/jquery-ui-1.8.13.custom.min.js"&gt;
&lt;script type="text/javascript" src="js/jquery.imgareaselect-0.9.6/scripts/jquery.imgareaselect.min.js"&gt;
&lt;link href="css/ui-lightness/jquery-ui-1.8.13.custom.css" rel="stylesheet" /&gt;
&lt;link href="js/jquery.imgareaselect-0.9.6/css/imgareaselect-default.css" rel="stylesheet" /&gt;
</pre>

Além do _imgAreaSelect_, também utilizamos a biblioteca de componentes para interface jQueryUI. Ela será responsável por mover (_draggable_) e redimensionar (_resizable_) as tags nas fotos.

A marcação HTML é bem simples, apenas com a imagem e um link para exibir/ocultar as tags. O formulário para adicionar uma tag será adicionado _on the fly_, após selecionarmos uma área. E como o formulário terá posição absoluta, é importante definir, no CSS, o atributo &#8220;position:relative&#8221; para o container da imagem, no nosso caso o elemento _p_.

<pre class="lang-html">&lt;p&gt;&lt;img src="img/ramones.jpg" /&gt;&lt;/p&gt;
&lt;p&gt;&lt;a href="#" class="toggle-tags"&gt;ocultar tags&lt;/a&gt;&lt;/p&gt;
</pre>

<pre class="lang-css">p{
  position:relative
}
div.form-tag{
  position:absolute;
  top:0;
  left:0;
  z-index:1000;
}
span.tag{
  position:absolute;
  border:1px solid #df0d32;
  background-color:rgba(255, 255, 255, 0.2);
  display:inline-block;
  color:#df0d32;
}
</pre>

### Selecionando áreas na foto

Passo a passo, esse será o fluxo da nossa interação:

  1. Com o mouse, o usuário seleciona uma área da foto para marcação;
  2. Feita a seleção, o script exibe uma caixa de texto para digitação do conteúdo da tag;
  3. Ao pressionar a tecla enter, o script cria, visualmente, a tag.

Abaixo temos a chamada para o plugin _imgAreaSelect_. Precisamos armazená-lo em uma variável global, chamada aqui de &#8220;ias&#8221;, porque posteriormente vamos alterar/limpar áreas de seleções de acordo com a interação do usuário (pressionado a tecla ESC). Por isso também utilizamos a opção &#8220;instance: true&#8221;.

<pre class="lang-jquery">ias = $('img#foto').imgAreaSelect({
  handles: true,
  instance: true,
  onSelectEnd: formTag,
  onSelectStart: function(){
    $('.form-tag').remove();
  }
});
</pre>

O evento &#8220;onSelectEnd&#8221; representa o momento em que o usuário termina de marcar uma área &#8211; e é nele que executamos a função &#8220;formTag&#8221; para exibir o campo de texto para preenchimento. Já o &#8220;onSelectStart&#8221; representa o início do movimento de seleção e, nesse caso, precisamos eliminar qualquer outro form presente para evitar confusão.

### Salvando as tags

Ok, hora de exibir o formulário para o usuário adicionar uma tag. Qualquer função no evento &#8220;onSelectEnd&#8221; pode (e deve) receber dois parâmetros: _img_ e _selection_. O primeiro é um objeto que representa a imagem onde foi aplicada a seleção e o segundo contém todas as informações de tamanho e posicionamento. Os vértices X e Y, necessários para posicionar o formulário logo abaixo da marcação, são representados por _selection.x1_ e _selection.y1_, respectivamente.

<pre class="lang-jquery">var formTag = function(img, selection){
  $('.form-tag').remove();
  if(selection.width &gt; 0 && selection.height &gt; 0){
    $('&lt;div class="form-tag"&gt;&lt;input type="text" size="20" class="tag-name" /&gt;&lt;/div&gt;').insertAfter(img);
    $('.form-tag')
      .css({
        top : (selection.y1 + selection.height),
        left : selection.x1
      })
      .find('input.tag-name')
        .focus()
        .data('selection', selection);
  }
};
</pre>

Notem que, antes de exibir o formulário verificamos com <code class="lang-jquery">if(selection.width &gt; 0 && selection.height &gt; 0)</code> se de fato a seleção existe ou se o usuário apenas clicou na área da foto (acredito ser uma falha do plugin, já que nenhuma seleção foi criada). E, ao adicionar o formulário, jogamos o foco do cursor para o campo de texto e armazenamos as posições, para usarmos mais tarde, no atributo data do input.

Agora precisamos identificar quando o usuário pressionar enter ou ESC no input. Pressionando enter, nosso script deve salvar e exibir a tag na foto, enquanto a tecla ESC representa o cancelamento da ação, ou seja, remove o formulário. Utilizamos o evento keyup no input com uma função recebendo o parâmetro &#8220;e&#8221; (o próprio evento keyup). Os atributos &#8220;keyCode&#8221; e &#8220;which&#8221; equivalem à tecla pressionada pelo usuário, onde 13 é o enter e 27 ESC. Precisamos utilizar ambos porque alguns navegadores utilizam keyCode e outros which.

<pre class="lang-jquery">$('input.tag-name').live('keyup', function(e){
  if(e.keyCode == 13 || e.which == 13){ // enter
    if($(this).val() != ""){
      var selection = $(this).data('selection');
      $('&lt;span class="tag"&gt;'+$(this).val()+'&lt;/span&gt;').appendTo($(this).parent().parent());
      $('.tag:last')
        .css({
          height: selection.height,
          width: selection.width,
          top: selection.y1,
          left:selection.x1
        })
        .draggable({ containment: '#foto' })
        .resizable({ containment: '#foto', ghost: true });
      limpaFormTag();
    }
  }else if(e.keyCode == 27 || e.which == 27){ // esc
    limpaFormTag();
  }
});
</pre>

Primeiro validamos o conteúdo do input &#8211; não pode ser vazio. Caso o usuário tenha informado o conteúdo da tag, adicionamos o elemento span com a classe tag ao parágrafo da imagem. Com a tag recém adicionada, buscamos as dimensões e posicionamento armazenadas no atributo data-selection do input e definimos o css do span. Para dar um toque especial à nossa interface, conforme mencionado anteriormente, a tag ainda recebe os efeitos _draggable_ e _resizable_, da jQueryUI, permitindo assim mover ou alterar seu tamanho depois de criada.

A função &#8220;limpaFormTag&#8221; esconde o formulário e atualiza nossa instânce do plugin imgAreaSelect, removendo qualquer seleção em andamento.

<pre class="lang-jquery">var limpaFormTag = function(){
  $('.form-tag').remove();
  ias.setOptions({hide:true});
  ias.update();
};
</pre>

Com tudo pronto, falta definir a ação do link que exibe/oculta as tags. O método &#8220;toggle&#8221; automaticamente identifica se o seletor, nossas tags, estão visíveis ou não e executa a ação (exibir/ocultar) de acordo com o estado atual do elemento.

<pre class="lang-jquery">$('.toggle-tags').click(function(e){
  $('.tag').toggle();
  if($('.tag:visible').length &gt; 0) {
    $(this).text('ocultar tags');
  } else {
    $(this).text('exibir tags');
  }
  e.preventDefault();
});
</pre>

### E agora, para onde ir?

É claro que, para essa interface de fato funcionar, seria necessário armazenar as informações das tags em banco de dados. No nosso exemplo, ao atualizar a página, todas as essas informações serão perdidas. Logo, um dos próximos passos seria um script server-side executado quando o usuário pressionar a tecla enter no input.

Também seria legal desenvolver opções para edição do conteúdo e exclusão das tags.

E que tal <a href="http://tableless.com.br/anatomia-de-um-plugin-jquery" target="_blank">transformar tudo em um plugin</a>? Só não esqueça de compartilhá-lo com a gente!

### Downloads & referências

  * <a href="http://jqueryui.com/" target="_blank">jQuery UI</a>
  * <a href="http://odyniec.net/projects/imgareaselect/" target="_blank">plugin imgAreaSelect</a>
  * <a href="http://tableless.github.io/exemplos/habilitando-tags-em-fotos-com-jquery/" target="_blank">Visualizar exemplo</a>
  * <a href="https://github.com/tableless/exemplos/tree/gh-pages/habilitando-tags-em-fotos-com-jquery" target="_blank">Download do código fonte</a>
  * <a href="http://www.cambiaresearch.com/c4/702b8cd1-e5b0-42e6-83ac-25f0306e3e25/javascript-char-codes-key-codes.aspx" target="_blank">Tabela com KeyCodes para JavaScript</a>