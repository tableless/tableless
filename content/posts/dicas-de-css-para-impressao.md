---
title: Dicas de CSS para impressão
author: Dani Guerrato
type: post
date: 2014-02-24
excerpt: Seja na hora de levar uma receita para a cozinha, ter uma cópia física de um documento ou guardar um artigo bacana para ler depois, imprimir é uma função que usamos e abusamos em nosso dia-a-dia. Mas será que estamos fazendo tudo o que poderíamos para diagramar sites no papel?
url: /dicas-de-css-para-impressao/
dsq_thread_id: 2310584424
categories:
  - CSS
tags:
  - CSS
  - print

---
Uma das premissas básicas do Design Responsivo é oferecer a melhor experiência do usuário, independente do meio utilizado para acessar a informação. Muitas vezes nos preocupamos muito com smartphones, tablets e outros dispositivos móveis e esquecemos de um tipo de mídia que ainda é essencial para a leitura: o papel. Pois é, o usuário pode sentir a necessidade de imprimir uma página na web por muitos motivos: portabilidade, guardar o conteúdo &#8220;offline&#8221; ou simplesmente por que &#8211; eReaders que me desculpem &#8211; é muito mais confortável ler em um papel. Mas nem todos os sites da web estão preparados para serem impressos. São muitos os elementos de um layout que na hora da impressão não servem para mais nada além de nos fazer gastar tinta a toa e distrair do foco do texto. Neste artigo vou dar algumas dicas básicas de CSS para impressão que vão ajudar a contornar os problemas mais comuns e deixar o seu layout prontinho para o papel. Vamos a elas!

Para ilustrar este post eu criei uma [pequena demo][1] utilizando como base um outro artigo aqui do Tabless só para ter um conteúdo.

## Primeiros passos

Você pode definir o CSS para impressão de duas maneiras.

1. Criando um arquivo .css com estilos específicos para impressão e chamando no head do site:

<pre class="lang-html">&lt;!-- CSS para impressão --&gt;
&lt;link rel="stylesheet" type="text/css" href="/print.css" media="print" /&gt;</pre>

2. Ou através de media types no final da sua folha de estilos principal:

<pre class="lang-css">/*CSS para impressão*/
@media print {
}</pre>

### Ressetando estilos

Dependendo do seu layout atual talvez seja uma boa ressetar algumas propriedades como cor de fundo, margens e espaçamentos para &#8220;começar do zero&#8221; sua folha de impressão. Definir o valor de texto para preto também é uma boa prática, já que dificilmente o usuário prefere imprimir colorido. Também desativamos sombras de texto e outros filtros.

<pre class="lang-css">* {
background:transparent !important;
color:#000 !important;
text-shadow:none !important;
filter:none !important;
-ms-filter:none !important;
}

body {
margin:0;
padding:0;
line-height: 1.4em;
}</pre>

Agora podemos definir uma margem única para todo o layout utilizando @page. Já que estamos no &#8220;mundo real&#8221; podemos descartar medidas em pixels. Repare que o valor está em centímetros.

<pre class="lang-css">@page {
margin: 0.5cm;
}</pre>

## Controlando o conteúdo

A regra essencial na hora de criar boas folhas de estilo para impressão é: aprenda a controlar o conteúdo. Muitas das áreas de um site não precisam ser impressas, ou, pelo menos não exatamente de maneira idêntica a versão online. Elementos como navegação, banner, footer podem, e devem, ser retirados para criar uma leitura mais agradável. Para se livrar deste conteúdo o bom e velho display none é seu amigo. Isto também vale para videos, audio, etc. Você pode criar uma listinha negra com o que deseja retirar:

<pre class="lang-css">nav, footer, video, audio, object, embed { 
display:none; 
}</pre>

Você pode criar duas classes para facilitar este trabalho. &#8220;Print&#8221; para os elementos que deseja que sejam mostrados apenas na impressão e &#8220;no-print&#8221; para aqueles que você quer esconder. Basta colar ese código na sua folha de estilos para impressão e aplicar as classes no HTML.

<pre class="lang-css">.print {
display:block;
}

.no-print { 
display:none; 
}</pre>

Lembre-se de inverter estes atributos no CSS normal.

<pre class="lang-css">.print {
display:none;
}

.no-print { 
display:block; 
}</pre>

Uma recomendação essencial para facilitar o seu trabalho nesta hora é: utilize tabelas apenas para dados tabulares ou você terá um grande problema para fazer esta separação entre layout e conteúdo. Mas, se você é um leitor aqui do Tableless, não preciso me preocupar em falar isto, certo?

Outro ponto importante é a questão das imagens. Não queremos que imagens grandes sejam cortadas para fora do papel. Temos duas soluções neste caso: determinar uma largura máxima em um valor fixo como pixels ou estabelecer o tamanho máximo como 100%.

<pre class="lang-css">img {
max-width: 100%;
}</pre>

Se a sidebar for algo relevante ao seu leitor, você pode posiciona-la abaixo do texto.

<pre class="lang-css">aside {
display:block;
page-break-before: always;
}</pre>

Agora é hora de dar uma espaço maior ao conteúdo principal.

<pre class="lang-css">.wrap { 
width: 100%; 
margin: 0; 
float: none !important; 
}</pre>

## Estilos de Texto

A maior parte das pessoas imprime em preto e branco pois é mais prático e econômico. Lembre-se disto na hora de definir seus estilos de texto. Nesta hora também é legal aproveitar para reajustar o tamanho, margem, padding e altura da linha dos elementos para garantir uma melhor leiturabilidade. Ah, se você estiver utilizando uma fonte display maluca super estilosa para os títulos e parágrafos talvez seja interessante trocar para algo mais &#8220;normal&#8221;, de preferência serifado já que existe um consenso que este tipo de letra é melhor para a leitura impressa. Alterar a únidade de px/em para pontos (pt) também é uma boa prática. Não se esqueça de definir novos tamanhos também para os títulos.

<pre class="lang-css">body {
font: 12pt Georgia, "Times New Roman", Times, serif;
color: #000;
}

h1 {
font-size: 24pt;
}

h2 {
font-size: 18pt;
}

h3 {
font-size: 14pt;
}</pre>

Outra dica bacana é expandir a atribuição de citações.

<pre class="lang-css">q:after {
content: " (" attr(cite) ")";
}</pre>

### Links

Muitas vezes diferenciamos links de texto apenas por cores. Isto obviamente não vai funcionar para quem imprimir em preto e branco. Vamos garantir que todos fiquem grifadinhos para facilitar a identificação.

<pre class="lang-css">a, a:visited {
text-decoration: underline;
}</pre>

Ok, agora seu usuário já sabe dizer o que é texto e o que é link. Mas não é preciso nem dizer que é impossível clicar em um papel. Um truque bacana para solucionar este problema é especificar a URL entre parenteses após o link para que seja fácil encontrar a referência no futuro.

<pre class="lang-css">a:link:after, a:visited:after {
content: " (" attr(href) ") ";
}</pre>

Este parâmetro não é compatível com browsers antigos. Mas temos que nivelar por cima, certo? Não é interessante mostrar links internos para imagens ou JavaScript. Para isto utilizamos o seguinte parâmetro.

<pre class="lang-css">a:after, a[href^="javascript:"]:after, a[href^="#"]:after { 
content: ""; 
}</pre>

Como links muito grandes podem quebrar o parágrafo vale a pena acrescentar mais uma regrinha.

<pre class="lang-css">p a {
word-wrap: break-word;
}</pre>

### Sobre viúvas e orfãs

Já reparou que na hora de imprimir as vezes fica uma última linha solitária de texto ou palavra perdida em uma página por falta de espaço na página anterior? Em tipografia esta linha chata é chamada de viúva e pode causar um desperdício enorme de espaço como, por exemplo, imprimir uma página inteira a mais com uma única palavra. Para controlar melhor o fluxo de texto podemos utilizar a propriedade &#8220;widows&#8221; e determinar o número mínimo de linhas que podem sobrar sozinhas no topo de uma página.

<pre class="lang-css">p {
widows: 3;
}</pre>

Outro pepino tipográfico semelhante é quando resta apena a primeira linha na página atual pois, por falta de espaço, o restante do parágrafo foi empurrado para a próxima página. Neste caso a linha é chamada de orfã. Mas podemos resolver este problema mais uma vez com o poder do CSS determinando um número mínimo de linhas que devem ficar no final da página.

<pre class="lang-css">p {
orphans: 3;
}</pre>

### Quebras de página

Se o seu texto é especialmente longo (no caso de um artigo ou até mesmo um livro) talvez seja interessante acrescentar quebras de página. Para isto adicione a classe .page-break ao seu CSS. É possível determinar quebras anteriores (page-break-before) ou posteriores (page-break-after) ao elemento html. Estas duas propriedades aceitam os seguintes valores:
  
auto, always, avoid, left, right e inherit.

Exemplo de aplicação em uma classe de CSS.

<pre class="lang-css">.page-break { 
page-break-before: always; 
}</pre>

## Elementos customizados

Talvez seja interessante incluir um cabeçalho ou rodapé especialmente criado para a impressão, com uma versão em preto e branco do logotipo ou qualquer outro elemento que você desejar incluir. É só criar uma classe especial para a impressão. Basta usar a nossa classe especial &#8220;print&#8221;. Vale até deixar uma mensagem com a URL do site.

<pre class="lang-html">&lt;header class="header print"&gt;
&lt;h1&gt;Artigo "Dicas de CSS para a impressão" escrito pela autora Dani Guerrato retirado do site www.tableless.com.br.&lt;/h1&gt;
&lt;/header&gt;</pre>

## Demo

Se você quiser testar o resultado final baixe a [folha de estilos utilizada neste artigo][2] no GitHub e use como base e crie seus próprio layout pronto para a impressão. Não se esqueça de ler alguns dos artigos indicados abaixo para mais dicas ótimas. Até a próxima!

### Leia mais

[How to set up a print style sheet][3]
  
[Optimizing structure print CSS][4]
  
[Optimizing content print CSS][5]
  
[HTML5 Boilerplate][6]
  
[6 things I learned about print stylesheets from HTML5 Boilerplate][7]

 [1]: https://github.com/daniguerrato/css-print "Css-print"
 [2]: https://github.com/daniguerrato/css-print "CSS-print"
 [3]: http://coding.smashingmagazine.com/2011/11/24/how-to-set-up-a-print-style-sheet/ "How to set up a print style sheet"
 [4]: http://davidwalsh.name/optimizing-structure-print-css "Optimizing structure print css"
 [5]: http://davidwalsh.name/optimizing-content-print-css "Optimizing content print CSS"
 [6]: http://html5boilerplate.com/ "HTML5 Boilerplate"
 [7]: http://designshack.net/articles/css/6-thinks-i-learned-about-print-stylesheets-from-html5-boilerplate/ "6 things I learned about print stylesheets"