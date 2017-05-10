---
title: Tenha o DOM
author: Alysson Franklin
type: post
date: 2011-07-25
excerpt: Entenda o que é o Document Object Model e tenha o DOM.
url: /tenha-o-dom/
tweetbackscheck:
  - 1356390917
shorturls:
  - 'a:3:{s:9:"permalink";s:35:"http://tableless.com.br/tenha-o-dom";s:7:"tinyurl";s:26:"http://tinyurl.com/3qxwvyg";s:4:"isgd";s:19:"http://is.gd/WQ9qEg";}'
twittercomments:
  - 'a:29:{i:102724647971340288;s:7:"retweet";i:109638504400683009;s:7:"retweet";i:109638482850349056;s:7:"retweet";i:109572897433059328;s:7:"retweet";i:109414012059525120;s:7:"retweet";i:109318730282045440;s:7:"retweet";i:109317022919303168;s:7:"retweet";i:109306943092428800;s:7:"retweet";i:109304883156500480;s:7:"retweet";i:109304181214552064;s:7:"retweet";i:109304089732595712;s:7:"retweet";i:109303596650209281;s:7:"retweet";i:109303518837489665;s:7:"retweet";i:109303462617026560;s:7:"retweet";i:109303416068653056;s:7:"retweet";i:109303312528060417;s:7:"retweet";i:144248143767277568;s:7:"retweet";i:153015068055973888;s:7:"retweet";i:153091102742822912;s:7:"retweet";i:156541353759748096;s:7:"retweet";i:156490352939905025;s:7:"retweet";i:217744387311009792;s:7:"retweet";i:217686733897207809;s:7:"retweet";i:217667087500455939;s:7:"retweet";i:217653827464212480;s:7:"retweet";i:217653795516198912;s:7:"retweet";i:217653531941945348;s:7:"retweet";i:217650874930053122;s:7:"retweet";i:217649300941975552;s:7:"retweet";}'
tweetcount:
  - 105
dsq_thread_id: 503040353
categories:
  - Artigos
  - HTML
  - JavaScript
  - O Básico
tags:
  - Browsers
  - DOM
  - Extensions
  - navegadores
  - Semântica
  - web standards

---
Muito ja foi falado sobre DOM e posso estar sendo repetitivo aqui, mas é importante falar deste assunto que em dias de manipulação pesada de seletores, percebo que pouca atenção é dada. Temos muita literatura boa sobre o assunto mas muitas vezes o foco acaba sendo o novo plugin que saiu e faz mais-do-mesmo-no-front-end-só-que-mais-fácil (E se você tiver sorte ele é free).

Entender realmente como um navegador funciona é importante, e garante seu entendimento do **real** dos problemas que está enfrentando no código que está implementando. Tem mais! Criar um código que manipula o layout (leia-se DOM) fica mais fácil, é uma relação _win-win_.

Criado pelo W3C, **O DOM é uma multi-plataforma que representa como as marcações em HTML, XHTML e XML são organizadas e lidas pelo navegador que você usa**. Uma vez indexadas, estas marcações se transformam em elementos de uma árvore que você pode manipular via API &#8211; que é o que fazemos quando usamos programas ou scripts para alterar funcionalidades de uma página: conteudo, estrutura ou folha de estilo.

## Um pouco de história

Não tem graça falar sobre o assunto sem mostrar como ele surgiu. Isso só reforça ainda mais a importância de conhecermos bem o assunto pois mostra sua relevância (e porque falar de _browser wars_ é bem legal, apesar de evidenciar os cabelos brancos).

Netscape e Microsoft guerreavam com Netscape 2 e IE3.0 lá em 1996 e enquanto a Netscape lançava o **Javascript** a Microsoft lançava o **JScript**. A diferença entre um e outro não é nada mais além do nome &#8211; acredite! Por razões comerciais devido as “<span>sangrentas” <em>browser wars</em> as empresas decidiram adotar nomes diferentes para a mesma coisa &#8211; que na verdade era (e continua sendo) o <strong>ECMAScript</strong>, a linguagem que comecou a ser criada em 1994 quando o W3C colocou na mesma mesa as duas empresas e várias outras para desenvolver um padrão para linguagens de script para os navegadores. <strong>Javascript, JScript e ActionScript não são nada mais que </strong><strong><em>dialetos</em> de ECMAScript.</strong></p> 

<h2>
  O DOM em sua forma e como é reconhecido pelos navegadores
</h2>

<p>
  <img src="http://tableless.com.br/uploads/2011/07/dom_tree.gif" alt="dom_tree" width="700" height="365" class="alignnone size-full wp-image-43633" />
</p>

<p>
  A figura acima mostra a estrutura de uma árvore DOM, a linearização  das marcações de modo que ela possa ser montada inicialmente por um navegador. Esta estrutura não será o que veremos no navegador &#8211; o layout em si. O DOM é a base para uma outra árvore que é o que realmente um browser monta na tela, a <strong>Árvore de Renderização </strong>&#8211; <em>aka </em><em>Render Tree</em>.
</p>

<p>
  A base para todos os nós da árvore DOM é o base class chamado <strong>Node.h</strong>. Ele possui várias categorias, e as relevantes para renderizarmos código no navegador são os nós de <strong>documentos, elementos </strong>e<strong> texto</strong>.
</p>

<ol start="1">
  <li>
    <strong>Documentos </strong>é o nó mais importante do DOM, com três classes diferentes: <strong>Document</strong>, que é usado por todos os documentos XML e outros que não sejam SVG (que também é um XML, porém com marcação já padronizada), <strong>HTMLDocument </strong>que como o nome diz, cuida de documentos HTML e SVGDocument, responsável pelos documentos SVG e tambem por outros documentos herdados da classe Document (Como o <strong>Document.h </strong>e o <strong>HTMLDocument.h</strong>).
  </li>
  <li>
    <strong>Elementos</strong> são todas as tags que estão em arquivos HTML ou XML se transformam em elementos da árvore DOM. Considerando a renderização do navegador, um elemento é um nó com uma tag que pode ser usada para fazer subclasses específicas que podem ser processadas de acordo com as necessidades da <em><span class="c4 c9">Render Tree </em>(<strong>Element.h</strong>).</li> 
    
    <li>
      <strong>Texto</strong>: É o texto que vai entre os elementos. Todo o conteúdo das tags (<p>Isto é um text node</p>). O nó de Texto guarda basicamente texto puro, que pode ser renderizado ou trabalhado via script.
    </li></ol> 
    
    <h2>
      A Render Tree
    </h2>
    
    <div id="attachment_3942" style="width: 413px" class="wp-caption alignnone">
      <a href="http://tableless.com.br/uploads/2011/07/render.png"><img class="size-full wp-image-3942  " src="http://tableless.com.br/uploads/2011/07/render.png" alt="Como a render tree e montada" width="403" height="187" srcset="uploads/2011/07/render.png 630w, uploads/2011/07/render-300x139.png 300w" sizes="(max-width: 403px) 100vw, 403px" /></a>
      
      <p class="wp-caption-text">
        Como a render tree é montada
      </p>
    </div>
    
    <p>
      A <em>Render Tree</em> é a parte mais importante do processo de renderização. Bem parecida com a árvore DOM, cada objeto corresponde a nós de <strong>Documentos, Elementos ou</strong><strong> Texto</strong>. A diferença é que q <em>Render Tree</em> possui tambem objetos que não possuem nós na árvore DOM, como <strong>scripts e folhas de estilos</strong>.
    </p>
    
    <p>
      O processo de criação da<strong> Render Tree</strong> passa pelos seguintes passos:
    </p>
    
    <ol start="1">
      <li>
        <strong>Attachment</strong>: Após finalizar o parse do DOM e a criação de seus nós, os navegadores chamam um método chamado <strong>attach </strong>para começar a renderização. O attach adiciona primeiramente as folhas de estilo a árvore DOM e começa a estilização da página. Um bom exemplo é o uso das propriedades CSS display x visibility: Caso um elemento da árvore DOM tenha uma propriedade display:none, este elemento (e seus nós filhos) não será criado na<em> Render Tree</em>. Ao contrário do uso de visibility:hidden, que vai renderizar o elemento na <span>árvore, porém  ele irá remover (ou adicionar quando visibility:visible) via<strong> Repaint </strong>as cores (ou propriedades) que formam este elemento. Vale lembrar também que este processo de attach é <em>top down</em>, criando sempre inicialmente os nós parent e depois seus descendentes (nós filhos). (<a href="http://tableless.com.br/entendendo-os-reflows-2" title="Entendendo os Reflows">Para saber mais sobre Repaint e Reflows, veja este outro artigo</a>)</li> 
        
        <li>
          <strong>RenderStyle.h</strong>: Durante o processo de attach um método é criado, o <strong>RenderStyle.h</strong> que vai guardar objetos de referência com cada uma das propriedades CSS do documento. O nó criado no DOM é verificado no documento de CSS e caso existam propriedades que incidam naquele elemento, ela é aplicada. Esta propriedade fica salva dentro da <em>Render Tree </em>até que ela seja destruída ou que este valor seja alterado por algum script.
        </li>
        <li>
          <strong>CSS Box Model: </strong>Após o método <strong>RenderStyle</strong> ser criado, ele é acessado via <strong>RenderObject</strong>. O Box model é usado para posicionar um elemento dentro da página, oferecendo suporte para o conteúdo, padding, bordas e margens que envolvem este elemento
        </li></ol> 
        
        <p>
          <img class="alignnone" src="http://www.w3.org/TR/CSS21/images/boxdim.png" alt="Uma representação visual do CSS box model" width="455" height="340" />
        </p>
        
        <h2>
          Destruindo (ou atualizando) a Render Tree
        </h2>
        
        <p>
          A <em>Render Tree</em> é destruída quando nós da árvore DOM são removidos, causando a necessidade de um novo parse no DOM, ou quando uma tab do navegador com a árvore DOM usada é fechada. Após o refresh da árvore DOM, todo o processo acima é refeito, com attach chamando o RenderStyle, que montado chama o método <strong>style()</strong> do RenderObject que acessa o CSS BOX model.
        </p>
        
        <h2>
          Como os navegadores interpretam todos estes elementos criados por DOM e Render Tree antes de aplicar o estilo?
        </h2>
        
        <p>
          Todo navegador tem uma lista de elementos HTML suportados. Quando o seu markup possui tags presentes na lista, a árvore DOM é montada e o processo de attachment começa logo na sequência e os estilos são aplicados, dando continuidade a criação da <span><em>Render tree</em>.</p> 
          
          <p>
            O grande problema é que cada navegador tem a sua própria lista, que trata situações similares de maneiras diferentes. Obviamente já sabemos que o navegador que mais apresenta problemas para as situações acima é o Internet Explorer, mas acredite, <strong>todos </strong>os navegadores apresentam problemas quando um elemento não está em sua lista de elementos permitidos, e precisa de um trabalho para fazer tudo acontecer na <span>Render Tree como deve ser feito.</p> 
            
            <p>
              Elementos fora desta lista são tratados como Elementos desconhecidos. E eles são uma grande fonte de problemas:
            </p>
            
            <ol start="1">
              <li>
                <strong>Como estilizar este elemento?</strong>Por exemplo, a tag <p> tem por padrão espacamento no topo e bottom, <blockquote> possui uma indentação automática adicionando uma margem à esquerda ou <h1> tem uma fonte maior que o <p> por ser um cabeçalho. Tudo isso esta padronizado, mas como cuidar de algo que não existe?
              </li>
              <li>
                <strong>Como este elemento deve aparecer na árvore DOM?</strong>Os navegadores também possuem uma lista que mostra quais elementos podem ser filhos de outros elementos. Por exemplo, se você adiciona por engano no seu markup <p><p> o segundo paragrafo implicitamente fechará o primeiro <p>, fazendo que os dois elementos sejam irmãos (no mesmo nível na árvore DOM) e nao como nós filhos como de maneira linear pode parecer. Porém se vc adiciona um <p><span>, este paragrafo inicial não será fechado, porque o navegador permite que <span> seja filho de elementos de paragrafo, fazendo assim o <span> ser nó filho de <p>
              </li>
            </ol>
            
            <p>
              Para elementos desconhecidos, a ideia é não estilizar. Caso queira algum estilo em elementos desconhecidos, você deve colocá-lo no nó acima (se necessário um <em>wrapper</em>), para fazer com que ele herde o estilo.
            </p>
            
            <p>
              Perceba a sutileza de como isso funciona. Os dois diagramas mostram uma árvore DOM, montada por um navegador suporte HTML5 nativo e o Internet Explorer 8 (navegadores que não suportam HTML5 tem funcionamento semelhante):
            </p>
            
            <div id="attachment_3988" style="width: 570px" class="wp-caption alignnone">
              <a href="http://tableless.com.br/uploads/2011/07/renderizaao_HTML5-5.png"><img class="size-full wp-image-3988 " src="http://tableless.com.br/uploads/2011/07/renderizaao_HTML5-5.png" alt="Arvore DOM com suporte HTML5" width="560" height="472" srcset="uploads/2011/07/renderizaao_HTML5-5.png 800w, uploads/2011/07/renderizaao_HTML5-5-300x252.png 300w" sizes="(max-width: 560px) 100vw, 560px" /></a>
              
              <p class="wp-caption-text">
                Arvore DOM com suporte HTML5
              </p>
            </div>
            
            <div id="attachment_3987" style="width: 576px" class="wp-caption alignnone">
              <a href="http://tableless.com.br/uploads/2011/07/renderizacaoIE-5.png"><img class="size-full wp-image-3987  " src="http://tableless.com.br/uploads/2011/07/renderizacaoIE-5.png" alt="Arvore DOM IE e outros navegadores sem suporte HTML5" width="566" height="458" srcset="uploads/2011/07/renderizacaoIE-5.png 1178w, uploads/2011/07/renderizacaoIE-5-300x243.png 300w, uploads/2011/07/renderizacaoIE-5-1024x830.png 1024w" sizes="(max-width: 566px) 100vw, 566px" /></a>
              
              <p class="wp-caption-text">
                Arvore DOM IE e outros navegadores sem suporte HTML5
              </p>
            </div>
            
            <p>
              É por essas e outras que a gente usa o modernizr, o HTML5shiv ou um simples document.create(“SECTION”) / document.create(“ARTICLE”). E é isso que acontece quando navegadores interpretam elementos desconhecidos. Eles desconsideram o nó real aonde o elemento está, e o reconhece como filho de <BODY>. E por favor, sem trocadilhos com o <span>filho dos outros.</p> 
              
              <p>
                Ver como uma árvore DOM é montada  e como a <em>Render tree </em>é feita nos dá idéia do quão importante é ter um documento semântico. <strong>Realmente semântico</strong>. Uma vez entendidos os conceitos, a manipulação e a programação dos elementos fica mais fácil.
              </p>
              
              <p>
                E você começa a entender como os navegadores funcionam.
              </p>
              
              <h2>
                Referências
              </h2>
              
              <ul>
                <li>
                  <a href="http://tableless.com.br/entendendo-os-reflows-2">Entendendo os Reflows</a> por Alysson Franklin
                </li>
                <li>
                  <a href="http://www.modernizr.com/">Modernizr</a> para suporte HTML5
                </li>
                <li>
                  <a href="http://code.google.com/p/html5shiv/">HTML5shiv</a> para suporte HTML5
                </li>
                <li>
                  <a href="http://en.wikipedia.org/wiki/Browser_wars">Browser Wars</a> pela Wikipedia
                </li>
                <li>
                  <a href="http://en.wikipedia.org/wiki/ECMAScript">ECMAScript</a> pela Wikipedia
                </li>
                <li>
                  <a href="http://en.wikipedia.org/wiki/JavaScript">Javascript</a> pela Wikipedia
                </li>
                <li>
                  <a href="http://en.wikipedia.org/wiki/JScript">JScript</a> pela Wikipedia
                </li>
                <li>
                  <a href="http://www.w3.org/TR/CSS21/box.html#box-dimensions">CSS Box model</a> pelo W3C
                </li>
                <ul>