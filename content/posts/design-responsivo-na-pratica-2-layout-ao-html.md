---
title: 'Design Responsivo na prática 2: do layout ao HTML'
author: Dani Guerrato
type: post
date: 2014-04-28
excerpt: Acompanhe o desenvolvimento de um HTML/CSS responsivo passo-a-passo a partir de um layout fixo, com direito a muitas dicas, comentários e demo.
url: /design-responsivo-na-pratica-2-layout-ao-html/
dsq_thread_id: 2634552725
categories:
  - Responsive Web Design (RWD)
tags:
  - responsive web design
  - rwd

---
Há um tempinho atrás eu escrevi aqui no Tableless um artigo chamado [Design Responsivo na Prática &#8211; Do Rascunho ao Digital][1]. A abordagem na época foi mais voltada para os designers, que estavam carentes de conteúdo bacana sobre o assunto. Mas, no entanto, todavia, algumas pessoas comentaram que gostariam de ver o desenvolvimento do dito cujo do layout criado passo-a-passo ou ao menos uma demo. Como eu não poderia deixar de atender os devs também, é justamente isto que vou fazer hoje. Portanto, pegue seu cafézinho pois hoje é dia de codar! 🙂

## Hora da Revisão

Não vou perder tempo aqui falando o que é design responsivo (conjunto de técnicas para melhorar a experiência do usuário independente do dispositivo que ele esteja utilizando), quais são as principais características de um site responsivo (um único conteúdo em uma única URL em um único código) ou por que você deve utilizar (são tantas que este parênteses seria gigante). Mas, como este artigo é mão na massa mesmo, antes de começar tenham certeza de entender os três pilares básicos do RWD (Responsive Web Design, que abrasileiramos carinhosamente para Design Responsivo).

Quais são?

&#8230;

&#8230;

&#8230;

**Spoiler**: fundação flexível, imagens adaptáveis e media queries. Bem, se você conseguiu lembrar todos os três de memória e está aí resmungando consigo mesmo ganhou um passe &#8220;pule a revisão&#8221;: vá direto para a prática. Se não conseguiu lembrar, sem problemas. Vamos refrescar a memória!

### 1. Fundação Flexível

Este é o esqueleto básico do layout. A fundação pode ser construída através de um sistema de grid fluído ou na unha combinando medidas relativas e um pouquinho de matemática. Como gostamos de desafios, vou ensinar por aqui a segunda opção.

#### (Quase) tudo é relativo

Para que o seu site possa se adaptar a múltiplos dispositivos e toda aquela ladainha que vocês já estão cansadinhos de saber é preciso colocar um pouco de lado os pixels. Note bem: colocar de lado, não jogar fora! Você ainda vai utilizá-los para definir alturas fixas e para definir, se for determinado no layout, um container inicial com uma largura máxima.

Para todo o resto conheça agora seus novos melhores amigos: % e EM.

(Existem também algumas outras medidas responsivas super bacanas como REM, VW, VH e FR. Mas vamos nos concentrar no básico.)

#### O que diabos é EM?

EM ou quadratim é uma medida relativa que nasceu na tipografia. 1 EM era originalmente correspondente ao tamanho da letra M maiúscula de uma determinada fonte. Isto era útil lá naquela época em que os tipógrafos utilizavam blocos de madeira ou metal para diagramar impressos, afinal, através desta letra eles teriam uma &#8220;chave&#8221; para todos as outras.

Já em se tratando de CSS, 1 EM é correspondente ao valor de font-size, que, por padrão do browser é em média 16px. E isto é bacana para a gente por que é um tamanho dinâmico. Ou seja, vamos supor que o seu usuário possua alguma deficiência de visão e precise aumentar e diminuir o tamanho do texto… Como pixel é uma medida fixa é impossível fazer isto de maneira proporcional, sem distorções ou quebras no layout. Já o EM é super proporcional. É uma questão de usabilidade.

#### Conversão de PX para EM

Como fazer contas em base 16 é meio chatinho podemos usar um truque de CSS para facilitar a conversão de pixels para EM.

<pre class="lang-css">body {
   font-size: 62.5%;
}
</pre>

Isto significa que alteramos o valor da fonte padrão de 16px para 10px. Desta forma, 12px passa a equivaler a 1.2em, 14px fica equivalente a 1.4em, etc.

Lembre-se que 1 EM é relativo ao font-size. Então uma vez que você altere este valor dentro de um article, por exemplo, todos os elementos filhos também serão alterados.

#### Conversão de PX para %

Para construir a tal da fundação flexível é preciso seguir uma formula estrutural básica: objeto : contexto = resultado.

Não fez o menor sentido? É, para mim também não fez a primeira vez que eu li. Vamos adiantar um pouquinho a prática e pensar no seguinte: temos uma div de largura 1128px. Dentro dela uma coluna com 264px de largura. A coluna é, portantom filha do container. Então vamos pegar o valor em px da coluna (objeto = 264px) e dividir pelo valor em pixel do elemento pai (contexto = 1128px). O resultado deu 0,23404255319149. Agora basta andar duas casas para a esquerda com a virgula e acrescentar um ponto que temos o valor 23.404255319149. E esta é a correspondência da nossa coluna em porcentagem: 23.404255319149%. Este número é realmente grande e a tentação é grande para chamar de 23% e acabar com a história. Mas, se você arredondar, uma hora a soma vai quebrar. Computadores são bem mais exatos que a gente. Eles sabem lidar bem com matemática&#8230;

Enfim, design responsivo é repetir esta continha a exaustão, meus caros. Usar um sistema de Grid ou Framework pronto é mais fácil? Muito! Como usar um elevador é mais fácil do que subir vários lances de escadas de um prédio a pé. Mas o dia que o nosso prédio metafórico pegar fogo saber COMO subir as tais das escadas é um conhecimento bem útil para salvar sua pele, certo? O mesmo vale para grids e frameworks. São ferramentas legais, mas tenha certeza que você sabe se virar sem elas. Pode ser que caia no seu colo um projeto onde, por uma incompatibilidade de linguagens ou escolha das outras pessoas envolvidas, você não possa usar um sistema de Grid pronto. Vai por mim. É melhor aprender a fazer na unha primeiro. Depois não diga que eu não avisei…

### 2. Imagens adaptáveis

Já que vamos trabalhar com porcentagens precisamos garantir que as imagens não vão se distorcer, certo? Então podemos acrescentar o seguinte código CSS.

<pre class="lang-css">img {
   max-width: 100%;
}
</pre>

Isto significa que o tamanho final da imagem no browser nunca vai ultrapassar o tamanho original dela. Mas, para isto funcionar, é necessário sempre envelopar as imagens em um container. Pode ser um figure, uma div, enfim, vai dá sua escolha para aquele contexto.

### 3. Consulta de mídia

O terceiro e último passo da nossa revisão é consulta de mídia ou media queries. Estes chuchuzinhos do CSS3 servem para identificar qual é o tipo, resolução e densidade do dispositivo e tornar a nossa vida mais fácil.

Para isto basta utilizar a regrinha @media combinada com parâmetros como min-width, max-width, min-height, max-height, aspect ratio, etc. e operadores como and, only e not.

Vamos supor que você queira trabalhar apenas com telas de largura máxima 1024px. O media querie ficaria assim:

<pre class="lang-css">@media screen and (max-width: 1024px) {
   /*estilos*/
}
</pre>

A tradução disto de CSS para português seria &#8220;tipo de mídia: tela E largura máxima: 1024px&#8221;.

Este tema sozinho daria um artigo inteiro. Na verdade já deu! Então, no melhor estilo escolha sua própria aventura:

&#8211; Se você tem dúvidas a respeito do funcionamento da consulta de mídia de uma lida em [Design Responsivo III – Media Queries e Compatibilidade][2] escrito pela autora que vos fala.
  
&#8211; Se você entendeu tudo desta explicação relâmpago e quer simplesmente ver mais exemplos de media queries dê uma olhadinha em [Logic in media queries][3].
  
&#8211; Se você já entendeu tudo e não precisa de mais exemplos siga em frente. 🙂

### Round Bonus &#8211; Viewport

Precisamos dizer para todos os dispositivos que a escala inicial do nosso layout é equivalente ao tamanho do dispositivo. Se não fizermos isto, alguns aparelhos móveis vão redimensionar o layout por conta própria e o design responsivo só vai funcionar no desktop! Para isto vamos manipular a metatag viewport. Cole isto no head do seu documento

<pre class="lang-html">&lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
</pre>

Quer saber mais sobre viewport? O artigo [Desenvolvimento Responsivo e Viewport][4] é super completo.

Fim da revisão!

## O HTML

Hora de colocar a mão no código!

Eu pessoalmente acredito ser mais fácil construir todo o HTML para depois desenvolver o CSS. Mas esta é uma preferência pessoal e não vou ficar aqui cagando regra. Vou manter a estrutura bem simples para nos concentrarmos no CSS. Vamos relembrar o layout que construímos juntos no artigo anterior.

<img class="alignnone size-full wp-image-42216" src="http://tableless.com.br/uploads/2014/04/layout-demo.jpg" alt="Demo Layout Responsivo" width="800" height="844" srcset="uploads/2014/04/layout-demo.jpg 800w, uploads/2014/04/layout-demo-400x422.jpg 400w" sizes="(max-width: 800px) 100vw, 800px" />

Podemos dividir este HTML em cinco estruturas básicas.

&#8211; Uma div com a classe container envolvendo todo o layout;
  
&#8211; Um cabeçalho com a classe header;
  
&#8211; Uma div &#8220;hero&#8221; com a classe banner;
  
&#8211; Quatro blocos de texto e imagem com a classe coluna;
  
&#8211; Um rodapé com a classe footer.

Até aqui não tem segredo nenhum. É um HTML normalzinho. Você pode fazer o download deste HTML no meu [repositório do GitHub][5] e acompanhar passo-a-passo.

Note que todas as imagens estão dentro de outros elementos (div ou figure).

## O CSS [Desktop]

Para facilitar vou especificar todas as medidas em pixel na versão desktop. Vamos a elas:

Container &#8211; 1128px
  
Logotipo &#8211; 234px x 36px
  
Menu &#8211; maximo 840px
  
Banner &#8211; 1128px x 450px
  
Caixa de texto &#8211; 480px
  
Colunas de texto &#8211; 264px
  
Fotos &#8211; 264px x 218px
  
Margens &#8211; 24px
  
Rodapé &#8211; 1128px

Primeiro vamos centralizar e determinar a largura máxima do container no CSS.

<pre class="lang-css">.container {
   max-width: 1128px;
   margin: 0 auto;
}
</pre>

### Clearfix

Esta é uma técnica utilizada para conter os floats e evitar que elementos entrem em colapso. Funciona basicamente adicionando um espaço vazio antes e depois dos elementos e dando um &#8220;clear&#8221; nos dois lados. Tudo isto sem precisar escrever marcação adicional. Como em design responsivo estaremos utilizando muito floats é útil conhecer. Vamos aplicar esta classe ao container do nosso layout para que ele possa conter todas as divs.

<pre class="lang-css">.clearfix:before,
.clearfix:after {
   content: " ";
   display: table;
}

.clearfix:after {
   clear: both;
}

.clearfix {
   *zoom: 1;
}
</pre>

### Proporção

A seguir vamos garantir que todas as imagens, videos e conteúdos embedados fiquem com a largura máxima de 100% do tamanho original.

<pre class="lang-css">img,
picture,
video,
embed {
   max-width: 100%;
}
</pre>

Aqui cabe uma observação. Como no nosso mock-up final as imagens em smartphones ocuparão o tamanho de uma coluna eu preferi utilizar um tamanho proporcionalmente maior (500x413px). Assim nenhuma imagem irá estourar a resolução nos smartphones.

### Border-box

Outro truque bacana de CSS para design responsivo é o box-sizing border box acompanhado do seletor *. Basicamente esta regra diz que todos os elementos agora levarão em conta apenas a largura e altura determinada, sem somar a este valor a borda e o padding. Ou seja, uma coisa a menos para nos preocuparmos.

<pre class="lang-css">*, *:before, *:after {
   -webkit-box-sizing: border-box;
   -moz-box-sizing: border-box;
   box-sizing: border-box;
}
</pre>

### O Header

A seguir vamos especificar o tamanho do header. Este é bem fácil: 100%!

<pre class="lang-css">.header {
   width: 100%;
   height: 48px;
   margin-top: 3.6em;
   margin-bottom: 3.6em;
}
</pre>

Eu dei a ele também uma altura fixa (48px) e especifiquei margens utilizando a medida EM. A minha intenção aqui foi criar uma margem dinâmica que ficasse em um tamanho bacana em relação ao texto em qualquer resolução. Por isto utilizei EM ao invés de px.

Dentro deste header temos um logotipo e um menu. Lembra da formulinha? Objeto : Contexto = Resultado. Então 234 : 1128 = 0,20744680851064. Andando duas casas para direita temos 20,744680851064. Este é o valor em porcentagem do logotipo. Eu gosto de deixar comentado o valor original em pixels para facilitar caso for preciso recalcular os elementos.

Ah, fique atento para substituir a virgula por ponto no CSS.

<pre class="lang-css">.logo {
   width: 20.744680851064%; /*234px / 1128px */
   float: left;
}
</pre>

O menu ficará flutuando a direita e a largura máxima &#8220;segura&#8221; é 840px.

<pre class="lang-css">.menu {
   width: 74.468085106383%; /*840px / 1128px */
   float: right;
}
</pre>

Coloquei também alguns elementos de estilo dos links e texto. Mas isto você já sabe fazer, certo? 😉

### Banner

O banner também é bem padrão, com 100% de largura. Aqui poderiamos ter um slider ou carrossel em JavaScript. Mas vou ficar apenas no HTML por este artigo.

<pre class="lang-css">.banner {
   background: url('../img/banner.jpg');
   height: 450px;
   margin-bottom: 4.8em;
   position: relative;
}
</pre>

Repare que a imagem está dentro do background do banner. Neste caso ela vai sendo cortada de acordo com a altura e largura que eu especificar para ele. Dentro do banner temos uma caixa que eu carinhosamente dei a classe de &#8220;caixa&#8221;. Aqui é a mesma ladainha de sempre. Objeto : Contexto = Resultado. A diferença aqui está na posição absoluta da caixa em relação ao banner.

<pre class="lang-css">.caixa {
   width: 42.553191489362%; /* 264px / 1128px */
   padding: 2.4em 4em 2.4em 4em;
   position: absolute;
   top: 48px;
   background: rgba(0,0,0,0.6);
}
</pre>

Novamente vamos pular os estilos puramente estéticos para ganharmos tempo. Mas você pode conferir todos eles na [demo][6].

### Colunas

Temos quatro destaques contendo texto e imagens que chamamos de colunas. A margem da direita também foi calculada em porcentagem. Como o último bloco não tem margem coisa nenhuma utilizamos o parâmetro last-child para especificar isto. Lembrando que versões antigas do IE não suportam isto.

<pre class="lang-css">.coluna {
   width: 23.404255319149%; /* 264px / 1128px */
   margin-right: 2.127659574468%; /* 24 / 1128px */
float: left;
}

.coluna:last-child {
   margin-right: 0;
}
</pre>

### Footer

O rodapé do nosso layout é bem simples e ocupa 100% de largura.

<pre class="lang-css">.footer {
   width: 100%;
   margin-top: 2.4em;
   margin-bottom: 2.4em;
   float: left;
   clear: both;
}
</pre>

## CSS [Mobile]

Vamos adaptar o layout aqui para tamanhos menores do que1128px. Mas poderíamos utilizar media queries para criar versões alternativas para televisores, impressão, dispositivos com maior densidade de pixel (como as telas retinas), etc.

Estes aparelhos podem ser divididos em alguns tamanhos médios de largura:

1024px &#8211; Tablets em modo paisagem;
  
768px &#8211; Tablets em modo retrato;
  
600px &#8211; eReaders;
  
480px &#8211; Smartphones;

Mas estes valores não passam de chutes calculados. Existem dezenas de resoluções intermediárias. Aqui vai entrar o conceito de break-point, ou, ponto-de-quebra. Funciona mais ou menos assim:

1. Redimensione o seu browser até identificar um problema.
  
2. Concerte o problema.
  
3. Repita.

Sério. Não tem segredo. Para isto você pode utilizar algum bookmarklet de resolução. Copie o valor para o seu Media Querie.

Por exemplo, em exatos 1128px de largura temos o primeiro problema. Não existe nenhuma margem e o layout fica coladinho na janela do browser. Entra o primeiro Media Querie.

<pre class="lang-css">@media screen and (max-width: 1128px) {
.container {
   padding: 0 2.4em 0 2.4em;
}
}
</pre>

Tradução: em telas de largura máxima 1128px aplicar os seguintes estilos: espaçamento de 2.4em para a esquerda e para a direita.

O próximo problema é que lá por volta do 768px a nossa caixa de banner parece meio apertada demais. Podemos aumentar o tamanho dela.

<pre class="lang-css">@media screen and (max-width: 768px) {
.caixa {
   width: 65%;
}
}
</pre>

O mesmo acontece com as colunas… Dentro do mesmo media querie vamos especificar duas colunas com largura de 48% e margem de 2%.

<pre class="lang-css">.coluna {
   width: 48%;
   margin-bottom: 2.4em;
   margin-right: 2%;
}

.coluna:nth-child(even) {
   margin-right: 0;
}
</pre>

Lembrando que agora a regrinha é diferente. Para cada coluna de número par zeramos a margem através do :nth-child(even).

O logotipo poderia ter uma margem maior por aqui.

<pre class="lang-css">.logo {
   margin-top: 1.2em;
}
</pre>

O próximo problema é o banner. Por volta de 718px ele poderia receber menos destaque na imagem e mais destaque no texto. Diminuimos a altura dele para 150px, e colocamos a caixa logo abaixo. O resto é correção de margem e perfumaria.

<pre class="lang-css">@media screen and (max-width: 718px) {
.banner {
   position: relative;
   float: left;
   margin:0;
   height: 150px;
}

.caixa {
   position: relative;
   display: block;
   float: left;
   margin-top:100px;
   width: 100%;
   background: #000;
}

.caixa h1 {
   font-size: 2.5em;
}

.principal {
   margin-top: 450px;
}
}
</pre>

Diminua mais ainda a janela do browser. Eventualmente o menu cairá para duas linhas, certo? Como temos apenas quatro links na navegação ele pode muito bem simplesmente ocupar 100% de largura e zerar a margem das linhas. Vamos também diminuir um pouco o tamanho dos links.

<pre class="lang-css">@media screen and (max-width: 640px) {
.menu {
   width: 100%;
}

.menu ul {
   float: left;
   font-size: 0.8em;
}

.menu li:first-child {
   margin-left: 0;
}
}
</pre>

Poderíamos, através de JavaScript e/ou CSS3, criar outras soluções de navegação como um menu retratil, com overlay, etc. Mas como já existem alguns artigos aqui no Tableless sobre o tema vamos seguir adiante.

Neste ponto já temos nosso layout em tablets. Esta é uma screenshot em um iPad 2 modo retrato.

<img src="http://tableless.com.br/uploads/2014/04/layout-demo-tablet.jpg" alt="layout-demo-tablet" width="800" height="844" class="alignnone size-full wp-image-42226" srcset="uploads/2014/04/layout-demo-tablet.jpg 800w, uploads/2014/04/layout-demo-tablet-400x422.jpg 400w" sizes="(max-width: 800px) 100vw, 800px" />

O próximo, e último passo, é criar o layout em smartphones em si. Para isto vamos especificar que todas as colunas também ocupem 100% da tela.

<pre class="lang-css">@media screen and (max-width: 520px) {
.coluna {
   width: 100%;
   margin-right: 0;
}
}
</pre>

E aqui esta o layout em um smartphone.

<img src="http://tableless.com.br/uploads/2014/04/layout-demo-smartphones.jpg" alt="layout-demo-smartphones" width="800" height="600" class="alignnone size-full wp-image-42225" srcset="uploads/2014/04/layout-demo-smartphones.jpg 800w, uploads/2014/04/layout-demo-smartphones-400x300.jpg 400w" sizes="(max-width: 800px) 100vw, 800px" />

## Saiba mais

E está finalizada nossa demo. [Baixem o layout][6] e brinquem com o código. Ainda está com dúvida em algum tema específico ou quer se aprofundar em um dos aspectos? Segue uma listinha básica de alguns outros artigos sobre o assunto:

[Design Responsivo na Prática: Do rascunho ao digital][1]
  
[Design Responsivo I – O que é e por que usar][7]
  
[Design Responsivo II – Grids e Texto][8]
  
[Design Responsivo III – Media Queries e Compatibilidade][9]
  
[Desenvolvimento Responsivo e Viewport][10]
  
[Design Responsivo & Retina Display: desenvolvimento web em alta resolução][11]
  
[Imagens em alta resolução utilizando SVG][12]
  
[Grids semânticos com LESS][13]
  
[Menu Restrátil com CSS e jQuery][14]
  
[Como testar Design Responsivo][15]
  
[Imagens Responsivas de Alta Performance][16]
  
[Responsive Web Design][17]

Espero que tenha sido proveitoso para vocês. Bons estudos, um abraço e até a próxima! 🙂

&#8212;

**Update:**
  
O Diego Eis fez um [Micro Workshop Online][18] mostrando como implementar um layout responsivo, mostrando o básico sobre Grids fluídos, Imagens (vídeos etc) fluídos, Media Queries, Fonts com REM e algumas outras coisas. Vale a pena ver.

 [1]: http://tableless.com.br/design-responsivo-na-pratica-do-rascunho-ao-digita/ "Design Responsivo na prática: do rascunho ao digital"
 [2]: http://blog.popupdesign.com.br/design-responsivo-iii-media-queries-e-compatibilidade/ "Design Responsivo III – Media Queries e Compatibilidade"
 [3]: http://css-tricks.com/logic-in-media-queries/ "Logic in media queries"
 [4]: http://blog.popupdesign.com.br/desenvolvimento-responsivo-e-viewport/ "Desenvolvimento Responsivo & Viewport"
 [5]: https://github.com/daniguerrato/design-responsivo-demo "Demo"
 [6]: https://github.com/daniguerrato/design-responsivo-demo "Demo - Design Responsivo na Prática"
 [7]: http://blog.popupdesign.com.br/design-responsivo-i-o-que-e-e-por-que-usar/ "http://blog.popupdesign.com.br/design-responsivo-i-o-que-e-e-por-que-usar/"
 [8]: http://blog.popupdesign.com.br/design-responsivo-grids-e-texto/ "http://blog.popupdesign.com.br/design-responsivo-grids-e-texto/"
 [9]: http://blog.popupdesign.com.br/design-responsivo-iii-media-queries-e-compatibilidade/ "http://blog.popupdesign.com.br/design-responsivo-iii-media-queries-e-compatibilidade/"
 [10]: http://blog.popupdesign.com.br/desenvolvimento-responsivo-e-viewport/ "Desenvolvimento Responsivo e Viewport"
 [11]: http://blog.popupdesign.com.br/design-responsivo-e-retina-display-desenvolvimento-web-em-tempos-de-alta-resolucao/ "http://blog.popupdesign.com.br/design-responsivo-e-retina-display-desenvolvimento-web-em-tempos-de-alta-resolucao/"
 [12]: http://tableless.com.br/imagens-em-alta-resolucao-utilizando-svg/ "Imagens em alta resolução utilizando SVG"
 [13]: http://tableless.com.br/grids-semanticos-com-less/ "Grids semânticos com LESS"
 [14]: http://tableless.com.br/menu-retratil-com-css-e-jquery/ "Menu Retrátil com CSS e jQuery"
 [15]: http://tableless.com.br/como-testar-design-responsivo/ "Como testar design responsivo"
 [16]: http://tableless.com.br/imagens-responsivas-de-alta-performance/ "Imagens Responsivas de Alta Performance"
 [17]: http://alistapart.com/article/responsive-web-design/ "Responsive Web Design"
 [18]: https://www.eventials.com/tableless/live-coding-implementando-um-site-responsivo/