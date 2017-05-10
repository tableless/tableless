---
title: 6 estratégias para melhorar a organização do seu CSS
author: Talita Pagani
type: post
date: 2010-09-20
excerpt: Algumas estratégias simples podem ser utilizadas para deixar o seu CSS mais organizado, consistente e de fácil manutenção.
url: /6-estrategias-para-melhorar-a-organizacao-do-seu-css-2/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356438611
shorturls:
  - 'a:3:{s:9:"permalink";s:78:"http://tableless.com.br/6-estrategias-para-melhorar-a-organizacao-do-seu-css-2";s:7:"tinyurl";s:26:"http://tinyurl.com/3k229ub";s:4:"isgd";s:19:"http://is.gd/6ALDEG";}'
twittercomments:
  - 'a:44:{i:12112820992741376;s:6:"136269";i:23173992558895104;s:7:"retweet";i:21914615130628096;s:7:"retweet";i:30796924726550528;s:6:"136924";i:44471708433915904;s:7:"retweet";i:43712740145106947;s:7:"retweet";i:52702539837227009;s:6:"137423";i:111777267012734976;s:7:"retweet";i:111614637052661760;s:7:"retweet";i:111609269954166785;s:7:"retweet";i:111438490956337152;s:7:"retweet";i:111299190050656256;s:7:"retweet";i:111298832851152896;s:7:"retweet";i:111261163957923842;s:7:"retweet";i:111261027206840320;s:7:"retweet";i:111258252972531712;s:7:"retweet";i:111257323447660544;s:7:"retweet";i:111254636324851713;s:7:"retweet";i:111254160715956225;s:7:"retweet";i:111253223683264512;s:7:"retweet";i:111252145466126337;s:7:"retweet";i:111252086351593472;s:7:"retweet";i:111031610282999808;s:7:"retweet";i:110885681634623488;s:7:"retweet";i:110797914170859520;s:7:"retweet";i:110781324041793536;s:7:"retweet";i:110779855011987456;s:7:"retweet";i:110777027820400640;s:7:"retweet";i:110774668943818753;s:7:"retweet";i:110773437466808321;s:7:"retweet";i:110772065296056321;s:7:"retweet";i:110771599808004096;s:7:"retweet";i:110770804257591298;s:7:"retweet";i:110770732589514752;s:7:"retweet";i:110770568420270080;s:7:"retweet";i:110770414522875904;s:7:"retweet";i:110769704594980864;s:7:"retweet";i:110769432078454785;s:7:"retweet";i:110769161554243584;s:7:"retweet";i:110768561630351362;s:7:"retweet";i:110768442776363008;s:7:"retweet";i:110768304238505986;s:7:"retweet";i:110768027213107201;s:7:"retweet";i:271568548596428800;s:7:"retweet";}'
tweetcount:
  - 337
dsq_thread_id: 503039521
categories:
  - Artigos
  - CSS
  - HTML
tags:
  - cotidiano
  - CSS
  - design
  - padroes web
  - tecnicascss

---
Durante a codificação do CSS para um site, é interessante que o designer/programador utilize algumas convenções para que o código fique organizado e bem documentado.

Nos casos em que um projeto é compartilhado entre vários designers e programadores, a definição destas convenções é especialmente necessária para manter o código consistente e inteligível a todos que necessitam trabalhar ou dar manutenção no CSS.

Neste artigo compartilho algumas estratégias simples que aprendi ao longo dos anos e que auxiliam a melhor organizar folhas de estilo.

### 1º Utilize a declaração abreviada das propriedades

A forma abreviada de propriedades CSS poupa linhas de código e resume as sequências de declarações, deixando o código mais limpo e fácil de entender.

Veja o exemplo de uma classe sem o uso de declarações abreviadas:

<pre class="lang-css">.box {
    margin-top: 2px;
    margin-right: 3px;
    margin-bottom: 5px;
    margin-left: 9px;
    font-weight:bold;
    font-size:12px;
    line-height:14px;
    font-family:Arial, Verdana, sans-serif;
    border-width: 1px;
    border-style: solid;
    border-color: #000;
    background-color:#FFF;
    background-image:url(imagens/background.gif);
    background-repeat:no-repeat;
    background-position:0 15px;
}</pre>

Utilizando as declarações abreviadas, teríamos a seguinte definição para a mesma classe:

<pre class="lang-css">.box {
    margin: 2px 3px 5px 9px;
    font: bold 12px/14px Arial, Verdana, sans-serif;
    border: 1px solid #000;
    background: #FFF url(images/background.gif) 0 15px no-repeat;
}</pre>

### 2º Utilize identação para elementos encadeados

Na utilização de seletores contextuais que fazem uso de herança, também chamados de seletores encadeados (saiba mais [aqui][1]), uma opção interessante é a identação dos níveis de encadeamento para melhor visualizar qual a relação entre determinadas classes e elementos.

Exemplo:

<pre class="lang-css">h3 {
    font: italic bold 12px/24px Arial, Helvetica, sans-serif;
}

    h3 a, h3 a:visited {
        color: #000;
    }</pre>

Neste exemplo, temos a definição de estilo para o elemento _h3_. Abaixo, o elemento a que estiver dentro da tag _h3_, receberá a cor preta. Note que, com a identação, é possível compreender melhor que o estilo dos seletores encadeados está relacionada com o seletor _h3_.

Entretanto, esta técnica pode se tornar contraproducente caso haja muitos níveis de encadeamento, por exemplo:

<pre class="lang-css">.content
{ … }

    .content p
    { … }

        .content p strong
        { … }

            .content p strong a
            { … }</pre>

Portanto, sugiro utilizar apenar o primeiro nível de identação para relacionar com o contexto do primeiro elemento, caso opte por esta técnica.

### 3º Faça uma divisão lógica do seu CSS

Organize o estilo em determinadas seções, para facilitar a criação e a manutenção dos estilos e marque estas divisões com comentários CSS.

Uma sugestão de seções para realizar esta divisão:

  * Global (reset, corpo da pagina, estilo padrão para parágrafos, listas, etc.)
  * Cabeçalho da página
  * Estrutura da página
  * Rodapé
  * Estilos de títulos
  * Estilos de texto
  * Navegação
  * Formulários
  * Extras ou Miscelâneas

Os _estilos de título_ e _estilos de texto_ diferem dos estilos globais pois contém também definições de classes, enquanto que os estilos globais tratam apenas de definição para os seletores de tags.
  
Exemplos de comentários CSS que você pode utilizar para marcar a divisão de seções:

<pre class="lang-css">/* -----------------------------------*/
/* ----------&gt;&gt;&gt; GLOBAL &lt;&lt;&lt;-----------*/
/* -----------------------------------*/

/* GLOBAL &gt; RESET
//////////////////////////////////////*/

/**
* Estilos Globais
*
* @section global reset
*/</pre>

O terceiro exemplo é do CSSDoc, um projeto que visa estabelecer um padrão para documentação de CSS utilizando comentários, mas isso é assunto para outro artigo.

### 4º Estabeleça padrões de nomenclaturas para classes e IDs

O nome de uma classe ou um ID deve possibilitar a identificação de sua finalidade, de seu uso e de sua semântica.

Deve-se evitar nomear classes e IDs indicando aspectos estéticos e de posicionamento. Imagine as seguintes situações:

  1. Você nomeia uma classe como _conteudoEsquerda_, e depois precisa mudar o posicionamento para a direita durante um redesign. Será mais custoso, pois terá que mudar o nome da classe e a intenção não é essa. Se a classe tivesse sido definida como _conteudoRelacionado_ ou _sidebar_, a mudança ficaria a cargo apenas do CSS;
  2. Você nomeia uma classe como _tituloVerde_. Depois, precisa fazer uma manutenção rápida, pois o cliente quer o título em vermelho. Você muda apenas no CSS e a classe perde toda a semântica.

É importante definir também qual a forma de escrever as classes e IDs. Por exemplo: você utiliza _camelCase_, outro designer utiliza _nome-com-hífen_ e outro utiliza _nome\_com\_underline_. Estabeleça um único padrão junto a equipe, para que as nomenclaturas permaneçam consistentes. Pode ser, por exemplo, com hífen para classe e camel case para ID.

### 5º Especialize classes ao invés de criar seletores semelhantes

No (X)HTML, podemos utilizar mais de uma classe para o mesmo elemento. Com isso podemos especializar os elementos de utilizam uma determinada classe. Esta técnica é útil quando precisa-se aplicar apenas alguma propriedade diferente a um elemento que já utiliza uma classe, evitando a duplicação de estilos ou utilização de estilo inline.

No exemplo abaixo, temos dois parágrafos com a mesma classe, _verMais_ e o CSS correspondente.

**HTML**

<pre class="lang-html">&lt;h2&gt;Artigos Recentes&lt;/h2&gt;
…
&lt;p class="verMais"&gt;&lt;a href=”artigos.php”&gt;Ver Mais&lt;/a&gt;&lt;/p&gt;

&lt;h2&gt;Artigos Mais Comentados&lt;/h2&gt;
…
&lt;p class="verMais"&gt;&lt;a href=”artigos_comentarios.php”&gt; Ver Mais&lt;/a&gt;&lt;/p&gt;</pre>

**CSS**

<pre class="lang-css">.verMais {
    border-top: 1px solid #CCC;
    font-size: 11px;
    line-height: 24px;
    margin: 0 0 10px 0;
    text-align: right;
    text-transform: lowercase;
}</pre>

Porém, para o Segundo parágrafo, não queremos que ele tenha o border-top. Para isso, utilizamos uma segunda classe, chamada &#8220;semBorda&#8221;, ficando dessa forma:

**HTML**

<pre class="lang-html">&lt;h2&gt;Artigos Recentes&lt;/h2&gt;
…
&lt;p class="verMais"&gt;&lt;a href=”artigos.php”&gt;Ver Mais&lt;/a&gt;&lt;/p&gt;

&lt;h2&gt;Artigos Mais Comentados&lt;/h2&gt;
…
&lt;p class="verMais semBorda"&gt;&lt;a href=”artigos_comentarios.php”&gt; Ver Mais&lt;/a&gt;&lt;/p&gt;</pre>

**CSS**

<pre class="lang-css">.verMais {
    border-top: 1px solid #CCC;
    font-size: 11px;
    line-height: 24px;
    margin: 0 0 10px 0;
    text-align: right;
    text-transform: lowercase;
}

    .semBorda {
        border: none;
    }</pre>

Dessa forma, especializamos os elementos com a classe _verMais_, combinando mais uma classe que modifica apenas uma das propriedades, ao invés de criar uma classe _verMais2_ com as mesmas definições, retirando apenas a borda.

### 6º Ordene as propriedades dos seletores

Independente se você utiliza uma propriedade por linhas ou todas as propriedades CSS em uma única linha, escolher uma ordem para as propriedades é importante para facilitar a identificação, a adição de novas propriedades e também ajuda e encontrar mais rápido uma propriedade que você precisa alterar.

Longe de ser pragmática e indicar apenas 1 técnica com a qual tive contato (e que muitas pessoas às vezes têm dificuldade de se adaptar), sugiro duas formas de realizar essa ordenação:

#### Por ordem alfabética

No começo é um pouco mais complicado para conseguir localizar determinadas propriedades, pois acaba quebrando um pouco a organização lógica. Por exemplo, neste método propriedades como width e height ficarão amplamente distanciadas se o seletor contiver _margin_, _padding_, _text-align_, _text-transform_, entre outros. Porém, é um padrão mais conciso e que não gera ambiguidades de utilização.

#### Por agrupamento lógico

Este método pode ser mais produtivo, mas deve ser muito bem definido e documentado como será o agrupamento e qual será a ordem que estes agrupamentos aparecerão nos seletores. Além disso, deve-se ter certeza de que todas as propriedades foram devidamente mapeadas e agrupadas, para não se surpreender com uma propriedade &#8220;esquecida&#8221; e depois não conseguir saber onde irá colocá-la no seletor.

Um exemplo de agrupamento lógico:

<pre class="lang-css">.seletor {
    [fonte e propriedades de texto]
    [plano de fundo]
    [tamanho]
    [bordas]
    [espaçamentos]
    [posicionamento]
}</pre>

Com técnicas simples como esta é possível tornar o CSS mais funcional, semântico e compreensível, mantendo, principalmente, a flexibilidade do código.

 [1]: http://tableless.com.br/seletores-agrupados-e-encadeados