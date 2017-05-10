---
title: Entendendo os Reflows
author: Alysson Franklin
type: post
date: 2011-07-18
excerpt: O que são e como os Reflows podem ser otimizados para aplicações ficarem ainda mais rápidas.
url: /entendendo-os-reflows-2/
tweetbackscheck:
  - 1356448139
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/entendendo-os-reflows-2";s:7:"tinyurl";s:26:"http://tinyurl.com/3bgy96v";s:4:"isgd";s:19:"http://is.gd/RF5TTH";}'
twittercomments:
  - 'a:2:{i:144739315350650880;s:7:"retweet";i:152895559601106945;s:7:"retweet";}'
tweetcount:
  - 2
dsq_thread_id: 503040345
categories:
  - AJAX
  - Código
  - CSS3
  - HTML
  - HTML5
  - JavaScript
  - JQuery
  - Mercado e Comportamento
  - Tecnologia e Tendências
tags:
  - Browsers
  - desenvolvimento
  - DOM
  - JavaScript
  - JQuery
  - navegadores
  - performance
  - reflow
  - render tree
  - repaint

---
Reflow é um assunto extenso e necessário. Ele sempre vai existir nos navegadores, então temos que entendê-lo para saber como utilizá-lo de maneira racional. O mais legal é entender todo o contexto sobre o que são e como funcionam, para a partir daí repensar o código que renderizamos no navegador para obtermos maior performance.

**Reflow é o resultado de um evento que desencadeia mudanças no jeito que a pagina deve ser renderizada, tomando tempo para cálculo e reposicionamento de elementos.**

Para explicar como isso acontece, o importante é entender como um navegador renderiza uma página web.

## DOM

Document Object Model (DOM) é uma interface independente de linguagem e plataforma para representar e interagir com objetos em HTML, XHTML e XML. Mas o DOM é mais que isso; toda linguagem estruturada tem uma arvore DOM.

<div id="attachment_3941" style="width: 490px" class="wp-caption alignleft">
  <a href="http://tableless.com.br/uploads/2011/07/DOMTree.gif"><img class="size-full wp-image-3941 " src="http://tableless.com.br/uploads/2011/07/DOMTree.gif" alt="Exemplo de arvore DOM para documento HTML" width="480" height="212" srcset="uploads/2011/07/DOMTree.gif 800w, uploads/2011/07/DOMTree-300x132.gif 300w" sizes="(max-width: 480px) 100vw, 480px" /></a>
  
  <p class="wp-caption-text">
    Exemplo de arvore DOM para documento HTML
  </p>
</div>

Mas sobre o DOM podemos dizer que programas ou scripts podem dinamicamente acessar elementos na árvore DOM e alterar seu conteúdo, estrutura e estilo. Adicional ao estado inicial da pagina, estas alterações são agregadas a árvore DOM. O resultado é a renderização &#8211; o que nós vemos em um navegador. Mas a nossa _Render Tree_ tem mais que isso:

## Render Tree e como realmente entender display X visibility

<div id="attachment_3942" style="width: 514px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2011/07/render.png"><img class="size-full wp-image-3942 " src="http://tableless.com.br/uploads/2011/07/render.png" alt="Como a render tree e montada" width="504" height="234" srcset="uploads/2011/07/render.png 630w, uploads/2011/07/render-300x139.png 300w" sizes="(max-width: 504px) 100vw, 504px" /></a>
  
  <p class="wp-caption-text">
    Como a render tree é montada
  </p>
</div>

O DOM é resultado do parse do markup HTML que você montou dentro de um navegador. Só que dentro de um HTML você não tem apenas a estrutura do documento, estilos em CSS e funcionalidades em javascript também estarão no seu markup. E a Render tree é a soma de DOM mais estilos, que depois podem ser manipulados (seus scripts).

Pode parecer estranho, mas para mim a melhor maneira de entender as diferencas entre DOM e Render Tree é encarar esta última como um <span class="c17">individuo narcisista</span>. Isso mesmo: A Render Tree gosta de aparecer, é o que vemos no browser. O DOM acontece por trás das cortinas. _À Render tree, o palco_. ([Para saber mais sobre o DOM, veja este outro artigo][1])

Uma página que tem controles de show/hide mostra isso muito bem. Enquanto todo o conteúdo da página está presente na árvore DOM, apenas alguns itens estarão disponíveis na Render Tree &#8211; os visíveis na página (display:block). Alterar os elementos display:none vão disparar mudanças na render tree, e não na árvore DOM.

Já tentou entender as diferenças entre display:none e visibility:hidden? A maioria das explicações que vemos é que um “deixa de mostrar o elemento totalmente, incluindo seu espaço em tela” e o outro “deixa de mostrar o elemento visual, mas sua área de exibição continua sendo utilizada”. Esta explicação não está incorreta, mas seria melhor dizer que a propriedade display altera a estrutura da render tree, adicionando algo que antes não estava ali, enquanto visibility não faz alterações, apenas o câmbio de mostrar ou não um elemento que já esta na render tree.

## Repaint

Entendido as diferenças entre display e visibility, além do contexto de área do elemento, conseguimos explicar o Repaint. Uma ação que faça alteração de propriedades de background **sem alterar dimensões ou outras propriedades do elemento** não causam o reflow, apenas o repaint, que seria a atualização da propriedade de cor ou da imagem &#8211; literalmente pintar novamente o elemento. Repaints gastam menos CPU que reflows.

## Como um navegador monta seu documento HTML

Esses vídeos são sensacionais. Eles explicam o que são os reflows e dai como minimizá-los durante a fase de desenvolvimento do documento (sempre usando <span class="c9"><a class="c7" href="http://tableless.com.br/bem-vindo-a-xangrila-parte-1">Progressive Enhancement</a></span> quando possível) é mais fácil..

[youtube http://www.youtube.com/watch?v=ZTnIxIA5KGw]

<p class="c6 anotacao">
  Esta é uma representação de como a página da Mozilla é montada. Quer mais? Veja também como a <span class="c9"><a class="c7" href="http://video.google.com/videoplay?docid=-5863446593724321515">Wikipedia</a></span> e a página do <span class="c9"><a class="c7" href="http://video.google.com/videoplay?docid=-1471976166301235697">Google</a></span> no Japão são renderizadas.
</p>

Analisando o primeiro vídeo, perceba que ao finalizar a montagem do rodapé, “algo mais” acontece (a partir de 12seg). São os Reflows. A maioria dos elementos são recalculados e reposicionados. Se ponderarmos que o rodapé acaba de ser montado aos 14 segundos e a renderização termina aos 26 segundos da pagina, estamos falando quase de 50% do tempo de renderização sendo gasto com Reflows, o que é muito, dependendo do que a sua página deve fazer.

### O que causam exatamente os reflows?

##### `Reflow é um assunto extenso e necessário. Ele sempre vai existir nos navegadores, então temos que entendê-lo para saber como utilizá-lo de maneira racional. O mais legal é entender todo o contexto sobre o que são e como funcionam, para a partir daí repensar o código que renderizamos no navegador para obtermos maior performance.

**Reflow é o resultado de um evento que desencadeia mudanças no jeito que a pagina deve ser renderizada, tomando tempo para cálculo e reposicionamento de elementos.**

Para explicar como isso acontece, o importante é entender como um navegador renderiza uma página web.

## DOM

Document Object Model (DOM) é uma interface independente de linguagem e plataforma para representar e interagir com objetos em HTML, XHTML e XML. Mas o DOM é mais que isso; toda linguagem estruturada tem uma arvore DOM.

<div id="attachment_3941" style="width: 490px" class="wp-caption alignleft">
  <a href="http://tableless.com.br/uploads/2011/07/DOMTree.gif"><img class="size-full wp-image-3941 " src="http://tableless.com.br/uploads/2011/07/DOMTree.gif" alt="Exemplo de arvore DOM para documento HTML" width="480" height="212" srcset="uploads/2011/07/DOMTree.gif 800w, uploads/2011/07/DOMTree-300x132.gif 300w" sizes="(max-width: 480px) 100vw, 480px" /></a>
  
  <p class="wp-caption-text">
    Exemplo de arvore DOM para documento HTML
  </p>
</div>

Mas sobre o DOM podemos dizer que programas ou scripts podem dinamicamente acessar elementos na árvore DOM e alterar seu conteúdo, estrutura e estilo. Adicional ao estado inicial da pagina, estas alterações são agregadas a árvore DOM. O resultado é a renderização &#8211; o que nós vemos em um navegador. Mas a nossa _Render Tree_ tem mais que isso:

## Render Tree e como realmente entender display X visibility

<div id="attachment_3942" style="width: 514px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2011/07/render.png"><img class="size-full wp-image-3942 " src="http://tableless.com.br/uploads/2011/07/render.png" alt="Como a render tree e montada" width="504" height="234" srcset="uploads/2011/07/render.png 630w, uploads/2011/07/render-300x139.png 300w" sizes="(max-width: 504px) 100vw, 504px" /></a>
  
  <p class="wp-caption-text">
    Como a render tree é montada
  </p>
</div>

O DOM é resultado do parse do markup HTML que você montou dentro de um navegador. Só que dentro de um HTML você não tem apenas a estrutura do documento, estilos em CSS e funcionalidades em javascript também estarão no seu markup. E a Render tree é a soma de DOM mais estilos, que depois podem ser manipulados (seus scripts).

Pode parecer estranho, mas para mim a melhor maneira de entender as diferencas entre DOM e Render Tree é encarar esta última como um <span class="c17">individuo narcisista</span>. Isso mesmo: A Render Tree gosta de aparecer, é o que vemos no browser. O DOM acontece por trás das cortinas. _À Render tree, o palco_. ([Para saber mais sobre o DOM, veja este outro artigo][1])

Uma página que tem controles de show/hide mostra isso muito bem. Enquanto todo o conteúdo da página está presente na árvore DOM, apenas alguns itens estarão disponíveis na Render Tree &#8211; os visíveis na página (display:block). Alterar os elementos display:none vão disparar mudanças na render tree, e não na árvore DOM.

Já tentou entender as diferenças entre display:none e visibility:hidden? A maioria das explicações que vemos é que um “deixa de mostrar o elemento totalmente, incluindo seu espaço em tela” e o outro “deixa de mostrar o elemento visual, mas sua área de exibição continua sendo utilizada”. Esta explicação não está incorreta, mas seria melhor dizer que a propriedade display altera a estrutura da render tree, adicionando algo que antes não estava ali, enquanto visibility não faz alterações, apenas o câmbio de mostrar ou não um elemento que já esta na render tree.

## Repaint

Entendido as diferenças entre display e visibility, além do contexto de área do elemento, conseguimos explicar o Repaint. Uma ação que faça alteração de propriedades de background **sem alterar dimensões ou outras propriedades do elemento** não causam o reflow, apenas o repaint, que seria a atualização da propriedade de cor ou da imagem &#8211; literalmente pintar novamente o elemento. Repaints gastam menos CPU que reflows.

## Como um navegador monta seu documento HTML

Esses vídeos são sensacionais. Eles explicam o que são os reflows e dai como minimizá-los durante a fase de desenvolvimento do documento (sempre usando <span class="c9"><a class="c7" href="http://tableless.com.br/bem-vindo-a-xangrila-parte-1">Progressive Enhancement</a></span> quando possível) é mais fácil..

[youtube http://www.youtube.com/watch?v=ZTnIxIA5KGw]

<p class="c6 anotacao">
  Esta é uma representação de como a página da Mozilla é montada. Quer mais? Veja também como a <span class="c9"><a class="c7" href="http://video.google.com/videoplay?docid=-5863446593724321515">Wikipedia</a></span> e a página do <span class="c9"><a class="c7" href="http://video.google.com/videoplay?docid=-1471976166301235697">Google</a></span> no Japão são renderizadas.
</p>

Analisando o primeiro vídeo, perceba que ao finalizar a montagem do rodapé, “algo mais” acontece (a partir de 12seg). São os Reflows. A maioria dos elementos são recalculados e reposicionados. Se ponderarmos que o rodapé acaba de ser montado aos 14 segundos e a renderização termina aos 26 segundos da pagina, estamos falando quase de 50% do tempo de renderização sendo gasto com Reflows, o que é muito, dependendo do que a sua página deve fazer.

### O que causam exatamente os reflows?

#####` 

Reflows são excessivamente pesados e para reduzir efeitos uma das táticas que navegadores usam é processar nossos scripts em lote. Uma fila é criada para todos os comandos que causam reflow sejam processados de uma única vez. Porém o foco é entender o que causa um reflow e tentar minimizar o seu uso para ganhar performance na aplicação.

Este assunto é novo, e com certeza, A lista que mostro abaixo deve crescer. É importante mantermos a atenção a este assunto porque pequenos cuidados podem significar muito. Em um site web visualizado em desktops a diferença é óbvia sobre o tempo de renderização. Mas isso implica em outras coisas, que podem fazer a diferença não apenas em montar uma página mais rápido, mas também para menor gasto de processamento, o que garante também mais tempo de bateria em mobiles e tablets por exemplo.

<ol start="1">
  <li>
    Adicionar, remover ou atualizar o DOM;
  </li>
  <li>
    Esconder nós do DOM usando display:none;
  </li>
  <li>
    Mover e animar o DOM na página;
  </li>
  <li>
    Adicionar folhas de estilo on-the-fly que mudem o comportamento dos elementos;
  </li>
  <li>
    Redimensionar janelas;
  </li>
  <li>
    Alterar tamanho de fontes;
  </li>
  <li class="c6 c15">
    Scroll de página;
  </li>
</ol>

Em um dos posts sobre o assunto, Tony G mapeou pesquisas prévias e montou a seguinte tabela, que também está sendo constantemente atualizada.

<table class="c16" cellspacing="0" cellpadding="0">
  <tr>
    <td>
      <h4>
        <strong>Element</strong>
      </h4>
    </td>
    
    <td>
      <h4>
        <strong>Frame, Image</strong>
      </h4>
    </td>
    
    <td>
      <h4>
        <strong>Range</strong>
      </h4>
    </td>
    
    <td>
      <h4>
        <strong>SVGLocatable</strong>
      </h4>
    </td>
    
    <td>
      <h4>
        <strong>SVGTextContent</strong>
      </h4>
    </td>
    
    <td>
      <h4>
        <strong>SVGUse</strong>
      </h4>
    </td>
    
    <td>
      <h4>
        <strong>window</strong>
      </h4>
    </td>
  </tr>
  
  <tr>
    <td>
      <span class="c0">clientHeight,<br /> </span><span class="c0">clientLeft,<br /> </span><span class="c0">clientTop,<br /> </span><span class="c0">clientWidth,<br /> focus(), getBoundingClientRect(), getClientRects(), innerText,<br /> offsetHeight,<br /> offsetLeft,<br /> offsetParent,<br /> offsetTop,<br /> offsetWidth,<br /> outerText,<br /> scrollByLines(), scrollByPages(), scrollHeight, scrollIntoView(), scrollIntoViewIfNeeded(), scrollLeft,<br /> scrollTop,<br /> </span>scrollWidth
    </td>
    
    <td>
      <span class="c0">height, width</span>
    </td>
    
    <td>
      <span class="c0">getBoundingClientRect(), getClientRects()</span>
    </td>
    
    <td>
      <span class="c0">computeCTM(), getBBox()</span></p> 
      
      <p class="c5">
        </td> 
        
        <td>
          <span class="c0">getCharNumAtPosition(), getComputedTextLength(), getEndPositionOfChar(), getExtentOfChar(), getNumberOfChars(), getRotationOfChar(), getStartPositionOfChar(), getSubStringLength(), selectSubString()</span>
        </td>
        
        <td>
          <span class="c0">instanceRoot</span>
        </td>
        
        <td>
          <span class="c0">getComputedStyle(),<br /> scrollBy(),<br /> scrollTo(),<br /> scrollX,<br /> scrollY, webkitConvertPointFromNodeToPage(), webkitConvertPointFromPageToNode()</span>
        </td></tr> </tbody> </table> 
        
        <h2>
          Como melhorar o meu código para minimizar os reflows?
        </h2>
        
        <p>
          É simples. Basta minimizar o uso de requisições de estilo, que façam o navegador executar reflows ou repaints.
        </p>
        
        <ol start="1">
          <li>
            <span class="c11">Planejar a sua aplicação e entender como plugins e scripts criados vão se comportar em relação a reflow e repaints. Arquitetar o uso de plugins de acordo com a personalização que deve ser feita. Minimize o uso de alteração de estilos on-the-fly.</span>
          </li>
          <li>
            <span class="c11">Quando precisar alterar a propriedade de um estilo, troque o nome da classe, planeje a existência deste estado e adicione-o ao CSS previamente. Se o valor desta nova classe for dinâmica, use cssText. Evite alterar a propriedade diretamente para qualquer mudança.</span>
          </li>
          <li>
            <span class="c0">Pense como suas mudanças afetam a render tree e o quanto precisará ser revalidado depois desta mudanca. Se você usa position:absolute em um elemento, ele deixa de pertencer ao nó que está, e passa a ser filho do BODY. Alterá-lo então, não será tão custoso em termos de performance. Mesmo que alterações neste nó sobreponha outras areas, o reflow acontecerá apenas neste nó, e não em toda a render tree. </span>
          </li>
          <li>
            <span class="c11">Limpe seu CSS. Classes não utilizadas devem ser removidas.</span>
          </li>
          <li>
            <span class="c11">Reduza o número de mudanças no DOM. Ele vai causar mudanças estruturais em todas as outras etapas. E mais tempo de reflow. </span>
          </li>
          <li>
            <span class="c11">Animações na página, transições? Pondere sobre posicioná-la de maneira absoluta e trabalhar com ela a partir do BODY.</span>
          </li>
          <li>
            <span class="c11">Vá com calma nos seletores CSS &#8211; os descendentes em particular &#8211; pois usam maior poder de CPU para executar a tarefa (CPU = Bateria).</span>
          </li>
        </ol>
        
        <h2>
          Referências
        </h2>
        
        <ul>
          <li>
            <a href="http://en.wikipedia.org/wiki/Document_Object_Model">DOM</a> pela wikipedia
          </li>
          <li>
            <a href="http://video.google.com/videoplay?docid=-1471976166301235697#docid=1020647662203348823">Gecko Reflow</a>
          </li>
          <li>
            <a href="http://paulirish.com/2011/dom-html5-css3-performance/">DOM, HTML5, CSS3 e Performance</a> &#8211; <a href="http://dl.dropbox.com/u/39519/talks/gperf/index.html">Slides</a> por Paul Irish
          </li>
          <li>
            <a href="http://www.mozilla.org/newlayout/doc/reflow.html">Reflow</a> pelo Mozilla Labs
          </li>
          <li>
            <a href="http://ajaxian.com/archives/browser-reflows-how-do-they-affect-performance">Reflow e Repaint</a> na Ajaxian
          </li>
          <li>
            <a href="http://code.google.com/speed/articles/reflow.html">Reflow</a> pelo Google Code
          </li>
          <li>
            <a href="http://www.w3.org/DOM/">W3C Overview do DOM</a>
          </li>
          <li>
            <a href="http://www.dayofjs.com/videos/22158462/web-browsers_alex-russel">1 dia de javascript com Alex Russel: Como Navegadores Veem as suas Apps</a>
          </li>
          <li>
            <a href="http://gent.ilcore.com/2011/03/how-not-to-trigger-layout-in-webkit.html">Como (não) criar um layout no webkit por Tony G</a>
          </li>
          <li>
            <a href="http://www.webkit.org/blog/1091/more-web-inspector-updates/#timeline_panel">Usando a timeline panel em navegadores webkit</a>
          </li>
          <li>
            <a href="http://www.bookofspeed.com/">The book of Speed</a>
          </li>
          <li>
            <a href="http://www.phpied.com/rendering-repaint-reflowrelayout-restyle/">Reflow/Repaint</a> por Stoyan Stefanov
          </li>
          <li>
            <a href="http://calendar.perfplanet.com/2009/the-new-game-show-will-it-reflow/">Inconsistências dos navegadores em Reflows</a> por Stoyan Stefanov
          </li>
          <li>
            <a href="http://www.browserscope.org/?category=reflow">BrowserScope tests para reflows</a>
          </li>
          <li>
            <a href="http://www.youtube.com/watch?v=a2_6bGNZ7bA">Browsers para Web Developers</a> David Baron da Mozilla labs
          </li>
          <li>
            <a href="http://www.webkit.org/blog/114/webcore-rendering-i-the-basics/">Renderização no webkit, o básico</a>
          </li>
        </ul>

 [1]: http://tableless.com.br/tenha-o-dom "Tenha o DOM"