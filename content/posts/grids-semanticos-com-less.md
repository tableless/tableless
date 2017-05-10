---
title: Grids semânticos com LESS
author: Dani Guerrato
type: post
date: 2013-03-08
excerpt: 'Aprenda a construir rapidamente um grid semântico e responsivo utilizando CSS e uma ajudinha do LESS. '
url: /grids-semanticos-com-less/
dsq_thread_id: 1124074839
categories:
  - Artigos
  - Código
  - CSS
  - CSS3
  - Design
tags:
  - grid
  - LESS
  - semantic.gs

---
# Grids semânticos com LESS

Já reparou como os blocos da sidebar aqui do Tableless possuem todos a mesma largura? Ou como a largura do bloco de artigo somada a largura da sidebar é equivalente ao wrap do menu e do rodapé? Mesmo que você não tenha percebido isto antes de maneira consciente, a informação parece mais organizada desta forma&#8230;É por que o design do Tableless, como boa parte do conteúdo da internet, foi alinhado com o auxilio de um grid.

## O que é um grid?

Um grid é basicamente um conjunto de linhas guias, horizontais e/ou verticais, que servem de base para um design. No caso de design digital, o grid funciona como um esqueleto onde o layout será apoiado. Grids estão em todos os lugares, mesmo que você não os enxergue. Basta olhar a sua volta. A organização da informação é uma das principais vantagens na utilização de um grid, mas eu poderia citar diversas outras como precisão, consistência, hierarquia visual, ritmo&#8230; Só isto já daria um artigo inteiro. Grids são mesmo maravilhosos e a maior parte dos designers que conheço são apaixonados pro eles. Mas muitas vezes reproduzir a precisão de um grid em um código HTML/CSS é uma tarefa muito desgastante. Alguns desenvolvedores &#8211; as vezes por desconhecimento, as vezes por preguiça, as vezes por falta de tempo hábil &#8211; acabam alterando os valores. Arredondam uma porcentagem aqui, inventam uma margem ali, completamente desconsideram o valor de espaçamento entre linha&#8230; Resultado: o layout final parece bem diferente do original já que o grid foi praticamente descartado. Designers choram. Desenvolvedores se descabelam. Caos. Okay, talvez não de maneira tão dramática. Mas recriar a precisão do grid no CSS pode ser um problema. Ainda mais quando se trata de um projeto que inclui design responsivo&#8230;

## Sistemas convencionais de grids (e seus problemas)

Existem algumas alternativas que prometem ajudar nesta tarefa. Sistemas como o [1140 Grid System][1] e o clássico [960gs][2] quebram um galho e são faceis de utilizar, mas diversos aspectos me incomodavam nestes sistemas: classes não semânticas que sujavam o código (.onecol, .twocol&#8230; argh!), a necessidade de utilizar excessivamente truques como clearfix para &#8220;abrir&#8221; as fileiras e o aspecto engessado já que em nenhum destes sistemas existia a opção de customizar a largura das margens e colunas de acordo com o projeto. O jeito então era escrever manualmente um grid para cada job. Falo por mim mesma quando digo que matemática nunca foi o meu forte e aqueles pequenos segundos quebrando a cabeça na calculadora acabavam deixando todo processo mais lento quando somados no fim do dia. Mas tudo isto mudou com o adventos dos pré-processadores de CSS.

## Para que servem pré-processadores?

Basicamente eles pegam o texto escrito em uma linguagem e convertem ele para outra. Ou seja, literalmente pré-processam o código. No que isto é útil? Bem, é possível adicionar funcionalidades novas em linguagens pré existentes. Sistemas como [LESS][3], [SASS][4] e [Stylus][5] tornam possível trabalhar com velhos conhecidos dos programadores como variáveis, mixins, funções e operações matemáticas dentro do próprio CSS. É algo como uma folha de estilos com esteróides. E são estas funcionalidades extras que permitem a criação de um grid semântico.

## Um aviso aos navegantes

Vamos utilizar o sistema [Semantic.gs][6]. Existem muitos outros do tipo, mas a vantagem dele é que não se trata de um framework cheio de classes inúteis ou de um plugin de js que pesará no final. Este grid é todo escrito usando apenas CSS compatível com as linguagens do LESS, SASS e Stylus. Para este artigo eu escolhi utilizar LESS por ser a linguagem mais popular. Mas é facinho de adaptar para as outras, só vai mudar a sintaxe. Ainda não sabe utilizar o LESS? Sugiro que você leia o artigo aqui do Tableless &#8220;[CSS Dinâmico com Less][7]&#8220;. Entendeu tudo direitinho? Então você esta pronto para começar.

## O design

O primeiro passo, obviamente, é criar o grid no seu editor de imagens favoritos. No caso do Photoshop você pode quebrar a cabeça puxando linhas guias, utilizar algum plugin como o [GuideGuide][8] ou ainda utilizar usar um gerador online. Eu recomendo o [Grid Calculator][9]. Você insere o tamanho das colunas, das margens e a largura total do arquivo e magicamente ele gera um script de Photoshop ou Ilustrator ou ainda um arquivo em png com o grid prontinho. Mais fácil que tirar sarro do Internet Explorer.

> Um grid é basicamente um conjunto de linhas guias, horizontais e/ou verticais, que servem de base para um design.

Então vamos considerar uma estrutura basica bem simples. Header, um bloco de conteúdo, sidebar e footer em um wrap de 960 pixes de largura.

<img class="alignnone size-full wp-image-13192" alt="grid-exemplo-layout" src="http://tableless.com.br/uploads/2013/03/layout.jpg" width="580" height="407" srcset="uploads/2013/03/layout.jpg 580w, uploads/2013/03/layout-239x168.jpg 239w, uploads/2013/03/layout-441x310.jpg 441w" sizes="(max-width: 580px) 100vw, 580px" />

Para criar este layout eu utilizei um grid de 12 colunas com 60 pixels de largura. Okay. Layout feito. Hora de desenvolver.

<img class="alignnone size-full wp-image-13191" alt="grid-exemplo-colunas" src="http://tableless.com.br/uploads/2013/03/grid.jpg" width="580" height="407" srcset="uploads/2013/03/grid.jpg 580w, uploads/2013/03/grid-239x168.jpg 239w, uploads/2013/03/grid-441x310.jpg 441w" sizes="(max-width: 580px) 100vw, 580px" />

## Construindo o Grid

Baixe a [Demo][10] ou crie um novo arquivo HTML com a seguinte estrutura.

<pre>&lt;body&gt;

&lt;div class="wrap"&gt;
&lt;header class="cabecalho"&gt;
&lt;h1&gt;Header&lt;/h1&gt;
&lt;/header&gt;

&lt;section class="conteudo"&gt;
&lt;h1&gt;Conteúdo&lt;/h1&gt;
&lt;/section&gt;

&lt;aside class="sidebar"&gt;
&lt;h1&gt;Sidebar&lt;/h1&gt;
&lt;/aside&gt;

&lt;footer class="footer"&gt;
&lt;h1&gt;Footer&lt;/h1&gt;
&lt;/footer&gt;
&lt;/div&gt; &lt;!-- /wrap--&gt;

&lt;/body&gt;</pre>

Crie também um arquivo de CSS na linguagem LESS (style.less, por exemplo) e coloque o link entre as tags head do seu layout.

<pre>&lt;link rel="stylesheet/less" href="css/style.less" /&gt;</pre>

Não se esqueça de fazer o download da [última versão do LESS][11] e referencia-la também head do seu HTML. Lembrando sempre que este script deve aparecer depois da folha de estilos.

    <script src="js/less-1.3.3.min.js"></script>

Hora de setar o nosso grid. Inclua o seguinte código na sua folha de estilos LESS:

<pre class="lang-css">/* ==|=======================================================================
   Grid //  http://semantic.gs/ 
========================================================================== */

/*Altere estes valores de acordo com a largura das colunas, largura das margens e o número de colunas do seu grid.*/
@column-width: 60;
@gutter-width: 20;
@columns: 12;

@gridsystem-width: (@column-width*@columns) + (@gutter-width*@columns) * 1px;

/*Delete a linha abaixo se desejar trabalhar com valores em pixel.*/
@total-width: 100%;

.clearfix() {
	*zoom:1;

	&:before,
	&:after {
	    content:"";
	    display:table;
	}
	&:after {
	    clear:both;
	}
}

body {
	width: 100%;
	.clearfix;
}

.row(@columns:@columns) {
	display: block;
	width: @total-width*((@gutter-width + @gridsystem-width)/@gridsystem-width);
	margin: 0 @total-width*(((@gutter-width*.5)/@gridsystem-width)*-1);
	.clearfix;
}
.column(@x,@columns:@columns) {
	display: inline;
	float: left;
	width: @total-width*((((@gutter-width+@column-width)*@x)-@gutter-width) / @gridsystem-width);
	margin: 0 @total-width*((@gutter-width*.5)/@gridsystem-width);
	}

.push(@offset:1) {
	margin-left: @total-width*(((@gutter-width+@column-width)*@offset) / @gridsystem-width) + @total-width*((@gutter-width*.5)/@gridsystem-width);
}
.pull(@offset:1) {
	margin-right: @total-width*(((@gutter-width+@column-width)*@offset) / @gridsystem-width) + @total-width*((@gutter-width*.5)/@gridsystem-width);
}

/*Determine a largura do seu container.*/
.wrap {
	max-width: 960px;
	margin: 0 auto;
}</pre>

Para customizar de acordo com o seu grid é bem fácil. Basta alterar os valores deste trecho:

<pre class="lang-css">@column-width: 60;
@gutter-width: 20;
@columns: 12;</pre>

Na opção @column-width você escreve a largura em pixels da coluna, em @gutter-width você escolhe a largura das margens e em @columns o número de colunas. E pronto! A matemática é toda feita pra você e o semantic.gs converte todas as medidas de pixel para porcentagem.

## Como aplicar o grid

Segundo o nosso (belíssimo) layout o header deve ocupar a largura total do wrap, ou seja, o espaço equivalente a 12 colunas. Para isto basta acrescentar a classe .column(12) na folha de estilos.

<pre class="lang-css">.cabecalho {
      .column(12);
}</pre>

E isto no CSS final é compilado para os valores em porcentagens com uma margem de 10px:

<pre class="lang-css">.cabecalho  {
   display: inline;
   float: left;
   width: 97.61904761904762%;
   margin: 0 1.1904761904761905%;
}</pre>

Legal, né? Da mesma forma podemos determinar o espaço destinado ao conteúdo e a sidebar.

<pre class="lang-css">.conteudo {
        .column(9);
}
.sidebar {
        .column(3);
}</pre>

E isto será compilado para:

<pre class="lang-css">.conteudo {
  display: inline;
  float: left;
  width: 64.58333333333334%;
  margin: 0 1.0416666666666665%;
}
.sidebar {
  display: inline;
  float: left;
  width: 31.25%;
  margin: 0 1.0416666666666665%;
}</pre>

## Dominando o mundo com media queries

Agora para fazer o conteúdo se adaptar a dispositivos mobile é moleza. É só utilizar os bons e velhos media-queries. Vamos supor que para smartphones tanto a section conteúdo quanto a sidebar devem ocupar a largura total do wrap.

<pre class="lang-css">@media screen and (max-width: 480px) {
   .conteudo, .sidebar {
      .column(12);
   }
 }</pre>

E pronto! Desenvolvimento responsivo de maneira prática e semântica, sem se preocupar com a matemática.

## Como a magia acontece

É tudo através desta função. Basicamente ele considera a largura total do sistema de grid como a largura das colunas multiplicado pelo número de colunas somado com a largura das margens multiplicado pelo número de colunas vezes um pixel.

<pre class="lang-css">@gridsystem-width: (@column-width*@columns) + (@gutter-width*@columns) * 1px;</pre>

Não quer trabalhar com porcentagens? Sem problema. Delete esta linha que os valores ficam em pixel.

<pre class="lang-css">@total-width: 100%;</pre>

## Saiba mais

Existem algumas outras funções interessantes como a possibilidade de puxar e empurrar as divs e trabalhar com colunas aninhadas. Vale a pena ler a [documentação do semantic.gs][6] e seguir o projeto no [GitHub][12] para conferir futuras atualizações. O sistema é compatível com Firefox 3.5+, Safari 4+, Chrome, Opera 9+ e IE6.

E vocês? Utilizam algum sistema de grid? Quais são as vantagens e desvantagens? Deixem as sugestões nos comentários.

## Demo

[Demo][10]

 [1]: http://cssgrid.net/ "1140 Grid System"
 [2]: http://960.gs/ "960gs"
 [3]: http://lesscss.org/ "LESS "
 [4]: http://sass-lang.com/ "SASS"
 [5]: http://learnboost.github.com/stylus/ "Stylus"
 [6]: http://semantic.gs/ "Semantic.gs"
 [7]: http://tableless.com.br/css-dinamico-com-less/ "CSS dinâmico com LESS"
 [8]: http://guideguide.me/ "GuideGuide"
 [9]: http://gridcalculator.dk/ "Grid Calculator"
 [10]: http://tableless.com.br/uploads/2013/03/grid.zip
 [11]: https://raw.github.com/cloudhead/less.js/master/dist/less-1.3.3.min.js "LESS"
 [12]: https://github.com/twigkit/semantic.gs/ "Semantic.gs no GitHub"