---
title: O Cenário do Web Design Responsivo
author: Will Sales
type: post
date: 2013-07-17
excerpt: Site responsivo é muito mais que media queries, breakpoints e redimensionamento de imagens. Nesta tradução de artigo da Smashing Magazine, Stéphanie Walter mostra o que é, o que será possível, e o que precisa ser melhorado no RWD.
url: /o-cenario-do-web-design-responsivo/
dsq_thread_id: 1505017271
categories:
  - Adaptive Web Design (AWD)
  - CSS3
  - HTML
  - HTML5
  - Mobile
  - Responsive Web Design (RWD)
  - Traduções
  - UX
tags:
  - 2013
  - CSS
  - responsive web design
  - rwd
  - smashing magazine
  - traducoes

---
O Web design responsivo está por aí há alguns anos, e foi destaque em 2012. Muitas estrelas da web, como Brad Frost e Luke Wroblewski, possuem vasta experiência neste tema e têm nos ajudado a fazer grandes melhorias. **Mesmo assim, ainda há muito a ser feito**.

Neste artigo, vamos ver o que já é possível fazer hoje, o que será possível no futuro &#8211; usando propriedades ainda não padronizadas (como CSS nível 4 e API&#8217;s do HTML5) &#8211; e o que ainda precisa ser melhorado. Este não é um artigo tão completo, por isso não entraremos a fundo em cada técnica, entretanto, você terá links e referências para explorar por conta própria.

## O Cenário das Imagens no Web Design Responsivo

Há um aspecto melhor para começar a falar no web design responsivo que não seja imagens? Este até agora tem sido o tópico principal. E fica cada vez mais importante com a chegada das telas de alta densidade. E quando digo alta densidade, quero dizer telas com uma proporção de pixel maior que 2; esses dispositivos são chamados pela Apple de tela retina, e pelo Google de XHDPI. No web design responsivo, as imagens vem relacionadas a dois grandes desafios: tamanho e desempenho.

A maioria dos designers buscam a perfeição no pixel, porém imagens de tamanho &#8220;normal&#8221; em dispositivos de alta densidade aparecem pixeladas e borradas. Servir imagens com o dobro do tamanho a esses dispositivos parece ser tentador não é mesmo? No entanto, isso pode criar um problema de performance, pois imagens com o dobro do tamanho levam mais tempo para carregar, e usuários de dispositivos com alta densidade de pixels nem sempre tem a largura de banda necessária para fazer o download dessas imagens. Além disso, dependendo do país em que o usuário vive, esta largura de banda pode ser bem cara.

O segundo problema afeta dispositivos menores: Por que um dispositivo teria que fazer o download de uma imagem de 700 pixels quando ele só necessita de uma de 300? Teríamos uma maneira de &#8220;cropar&#8221; essas imagens para que usuários de dispositivos menores possam focar no que realmente importa a eles?

### Duas soluções de marcação: O elemento <picture> e o atributo srcset

O primeiro passo para resolver o desafio de imagens responsivas é mudar a marcação das imagens embutidas em uma página HTML.

O <a href="http://responsiveimages.org/" target="_blank">&#8220;Responsive Images Community Group&#8221;</a> apoia a proposta de um elemento novo e mais flexível, o elemento <a href="http://picture.responsiveimages.org/" target="_blank"><em>picture</em></a>. O conceito é usar as já tão conhecidas media queries para **servir imagens diferentes a diferentes dispositivos**. Assim, dispositivos menores receberiam imagens menores. Funciona um pouco como a marcação para vídeo, mas com imagens diferentes sendo refenciadas no elemento de origem.

O código na especificação proposta fica da seguinte forma:

<pre class="lang-html">&lt;picture width="500"  height="500"&gt;     
  &lt;source  media="(min-width: 45em)" src="large.jpg"&gt;
  &lt;source  media="(min-width: 18em)" src="med.jpg"&gt;
  &lt;source  src="small.jpg"&gt;
  &lt;img  src="small.jpg" alt=""&gt;
  &lt;p&gt;Accessible  text&lt;/p&gt;
&lt;/picture&gt;
</pre>

Se oferecer fontes diferentes para imagens é possível, poderíamos também imaginar o fornecimento de imagens com **recortes diferentes** e focar naquilo que realmente importa aos dispositivos menores. O tópico <a href="http://usecases.responsiveimages.org/#art-direction" target="_blank">&#8220;Art Direction&#8221;</a> da W3C mostra um belo exemplo do que poderia ser feito.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307110231.jpg" target="_blank"><img alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307110231.jpg?itok=65RrJGnF" width="433" height="475" longdesc="" /></a>

(Imagem: <a href="http://www.flickr.com/photos/egorick/3754608666/" target="_blank">Egor Pasko</a>)

A solução vem sendo discutida pelo <a href="http://www.w3.org/community/respimg/" target="_blank">W3C Responsive Images Community Group</a> mas, até onde sabemos, ainda não é utilizável por nenhum browser. Um polyfill chamado <a href="https://github.com/scottjehl/picturefill" target="_blank">Picturefill</a> está disponível, e faz praticamente a mesma coisa. Utiliza uma div e um atributo na sintaxe por questões de segurança.

A segunda proposta para a marcação de imagens responsivas foi feita pela Apple para a W3C e é chamada de &#8220;atributo srcset&#8221;; Ela é equivalente ao image-set() (propriedade CSS nível 4). A proposta deste atributo é forçar os navegadores a selecionar um recurso apropriado do set, ao invés de baixar o conjunto.

A sintaxe HTML para esta proposta se baseia na própria tag _img_, e o exemplo na especificação fica desta forma:

<pre class="lang-html">&lt;img  alt="The Breakfast Combo" 
  src="banner.jpeg"
  srcset="banner-HD.jpeg  2x, banner-phone.jpeg 100w, banner-phone-HD.jpeg 100w 2x"&gt;
</pre>

Como você pode ver a **sintaxe não é não é tão intuitiva**. Os valores da tag consistem em uma string separada por vírgulas. Os valores do atributo são os nomes ou URL&#8217;s de várias imagens, a densidade de pixels do dispositivo e o tamanho máximo da viewport a que se destina.

Numa linguagem clara, o que o trecho acima diz é:

  * A imagem padrão é _banner.jpeg_.
  * O dispositivo que tiver um pixel ratio maior do que 2 deve usar o _banner-HD.jpeg_.
  * Dispositivos com um tamanho máximo da viewport de _100w_ deve utilizar o _banner-phone.jpeg_.
  * Dispositivos com um tamanho máximo da viewport de _100w_ e um pixel ratio maior que 2 devem utilizar o _banner-phone-HD.jpeg_.

Caso o atributo _srcset_ não seja suportado, a primeira fonte é a imagem padrão. O sufixo _2x_ para o _banner-HD.jpeg_ significa que esta imagem em particular deveria ser usada para dispositivos com um pixel ratio maior que 2, e o _100w_ no _banner-phone.jpeg_ representa o tamanho mínimo da viewport em que esta imagem deve ser utilizada. **Devido a sua complexidade**, a sintaxe do atributo srcset ainda não foi implementada nos navegadores.

A sintaxe da propriedade CSS _image-set()_ funciona praticamente da mesma forma e permite que você carregue uma determinada imagem de background tendo como base a resolução da tela:

<pre class="lang-css">background-image: image-set(  "foo.png" 1x,
  "foo-2x.png"  2x,
  "foo-print.png"  600dpi );
</pre>

Esta proposta ainda esta em fase de projeto na W3C, e por enquanto funciona no Safari (6+) e no Chrome (21+).

### Formatos de Imagem, Compressão e SVG: A mudança de como trabalhamos com imagens na web.

Como podem ver, as tentativas em encontrar um novo formato de marcação para imagens ainda são altamente experiementais.Isto por si só levantou uma questão sobre formatos de imagens. Podemos conceber uma solução responsiva para mudar a forma como lidamos com eles?

O primeiro passo seria buscar formatos alternativos de imagens que tenham uma melhor taxa de compressão. O Google, por exemplo, desenvolveu um **novo formato de imagem** chamado <a href="https://developers.google.com/speed/webp/" target="_blank">WebP</a>, o qual é 26% menor que o PNG e 25 a 34% menor que o JPEG. O formato é suportado pelo Chrome, Opera, Yandex, Android e Safari, e pode ser ativado no Internet Explorer usando o <a href="http://www.google.com/chromeframe?quickenable=true" target="_blank">Google Chrome Frameplugin</a>. O problema principal deste formato é que o firefox não tem planos de implementá-lo. Sabendo disto, por enquanto, o seu uso generalizado é improvável.

Outra ideia que está ganhando popularidade são as **imagens JPEG progressivas**. Estas imagens são, como o nome sugere, progressivamente renderizadas. A primeira renderização é embaçada, então a imagem vai progressivamente ganhando nitidez. Já as imagens JPEG não-progressivas são renderizadas de cima pra baixo. Em seu artigo <a href="http://calendar.perfplanet.com/2012/progressive-jpegs-a-new-best-practice/" target="_blank">&#8220;JPEG&#8217;s progressivos: Uma nova boa prática&#8221;</a>, Ann Robson afirma que o JPEG progressivo aparenta ser mais veloz que o JPEG baseline. Um JPEG progressivo dá ao usuário uma impressão geral sobre a imagem antes mesmo de ela ser totalmente carregada, o que beneficia a experiência do usuário.

Uma outra solução aos problemas de performance e tamanho de imagem está em **alterar a taxa de compressão das imagens**. Durante muito tempo, pensamos que o alargamento da taxa de compressão de uma imagem prejudicaria a sua qualidade. Entretanto, Daan Jobsis fez uma extensa pesquisa sobre o assunto e escreveu um artigo a respeito chamado [&#8220;Retina Revolution&#8221;][1]. Em seus experimentos, ele testou diferentes tamanhos de imagens e taxas de compressão, o que gerou uma solução muito interessante. Se você dobrar o tamanho de uma imagem, mas também usar uma taxa de compressão mais alta, a imagem terá um arquivo com um tamanho menor que o original, mas ainda serão nítidas em telas normais e de alta densidade. Com esta técnica, Jobsis reduziu em 75% o peso da imagem.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307110629.jpg" target="_blank"><img title="Demonstração de compressão de imagens por Daan Jobsis." alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307110629.jpg?itok=DCu9elrj" width="473" height="242" longdesc="" /></a>

Dadas as dores de cabeça das imagens responsivas, a ideia de ganhar a independência do pixel a partir de imagens, sempre que possível, está seduzindo cada vez mais designers e desenvolvedores. O formato SVG, por exemplo, pode ser usado para criar todos os elementos da interface de um website <a style="line-height: 1.538em" href="http://coding.smashingmagazine.com/2012/01/16/resolution-independence-with-svg/" target="_blank">independente da resolução</a>. Os elementos serão dimensionados para dispositivos menores e não ficarão pixelados nos dispositivos de alta densidade de pixels. <a style="line-height: 1.538em" href="http://css-tricks.com/using-fonts-for-icons/" target="_blank">Font icons</a> são outra tendência crescente. Eles envolvem o uso de uma fonte, onde os caracteres alfanuméricos são substituídos por ícones glifos, dando a flexibilidade que uma fonte oferece. Infelizmente, esta solução ainda não funciona com imagens, o que faz com que seja ansiosamente esperado uma marcação ou formato de imagem viável.

## O Desafio do Layout Responsivo: Reorganizar e Trabalhar o Conteúdo sem Tocar no HTML?

Sejamos realistas, os grids fluidos usados atualmente, produzidos com floats e blocos inline, são um pobre improviso aguardando uma solução melhor. Trabalhar com o layout e rearranjar blocos numa página mobile sem recorrer ao JavaScript hoje em dia é um pesadelo, e não é nem um pouco flexível. Isto é algo crucial a websites criados com CMS, onde o designer não pode alterar o HTML de cada página ou versão do site.

E aí, como isto pode ser melhorado?

### Quatro Soluções com CSS3 que abordam o problema do Layout Flexível

A solução mais óbvia possível é o <a href="http://www.w3.org/TR/css3-flexbox/" target="_blank">modelo de box flexível do CSS3</a> (ou **flexbox**). Seu status atual é a de &#8220;candidato a recomendação&#8221; na W3C, e é suportado pela <a href="http://caniuse.com/#feat=flexbox" target="_blank">maioria dos browsers mobile e desktop</a> (no IE começou na versão 10). O model permite reorganizar facilmente os elementos na tela, independente do HTML. Você também pode alterar o fluxo e a orientação do box, distribuir o espaço e alinhá-lo de acordo com o contexto. Abaixo um exemplo de layout que poderia ser reorganizado para mobile. A sintaxe ficaria assim:

<pre class="lang-css">.parent {
   display: flex;
   flex-flow: column; /* exibe itens na coluna */
}

.children {
   order: 1; /* muda a ordem dos elementos */
}
</pre>

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307110724.jpg" target="_blank"><img alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307110724.jpg?itok=jmzs81k7" width="479" height="297" /></a>

O artigo <a href="http://coding.smashingmagazine.com/2011/09/19/css3-flexible-box-layout-explained/" target="_blank">&#8220;CSS3 Flexible Box Layout Explained&#8221;</a> dará a você uma compreensão mais profunda de como o flexbox funciona. (nota do tradutor: o bbburp traduziu um <a href="http://www.bbburp.com.br/artigos/layout-com-flexbox-e-como-tirar-doce-de-crianca" target="_blank">excelente artigo sobre flexbox</a>)

Outra solução bastante próxima do conceito flexbox de reordenação de blocos na página, porém com JavaScript, é o <a href="https://github.com/edenspiekermann/minwidth-relocate" target="_blank">Relocate</a>.

Um segundo tipo de layout, que hoje em dia é bastante utilizado no design responsivo, é o **layout multiple-column do CSS3**. O módulo está no estágio de &#8220;candidato a recomendação&#8221; na W3C, e <a href="http://www.w3.org/TR/css3-multicol/" target="_blank">funciona muito bem na maioria dos browsers</a> (aguardado para IE9 e abaixo). A principal vantagem deste model é que o conteúdo pode fluir de uma coluna a outra, proporcionando um ganho enorme na flexibilidade. No que diz respeito a responsividade, o número de colunas pode ser alterado de acordo com o tamanho da viewport.

É possível apenas ajustar o tamanho das colunas e deixar com que o browser calcule o seu número de acordo com o espaço disponível. Também é possível ajustar o número de colunas, com gaps e regras entre elas, e deixar que o browser calcule a sua largura.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307110803.jpg" target="_blank"><img alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307110803.jpg?itok=1MS5s-6X" width="477" height="297" /></a>

A sintaxe se parece com isto:

<pre class="lang-css">.container {
   column-width: 10em ;
   /* O browser vai criar uma coluna de 10em.
   O número de colunas vai depender dos espaço disponível */
}

.container {
   columns: 5;
   /* O browser vai criar 5 colunas.
   O tamanho das colunas vai depender do espaço disponível. */
   column-gap: 2em;
}
</pre>

Para aprender mais, leia o artigo de David Walsh: <a href="http://davidwalsh.name/css-columns" target="_blank">“CSS Columns”</a>.

Uma terceira propriedade CSS3 que pode ganhar mais atenção no futuro é a <a href="http://dev.w3.org/csswg/css-grid/" target="_blank">CSS3 grid layout</a>. Esta propriedade dá a designers e desenvolvedores um **grid flexível**, onde eles podem trabalhar com na criação de layouts diferentes. Ela permite que os elementos de conteúdo sejam exibidos nas linhas e colunas sem uma estrutura definida. Primeiro você deve declarar um grid no container, e então colocar todos os elementos filhos neste grid virtual. Você pode, então, definir um grid diferente para dispositivos menores ou alterar a posição dos elementos no grid. Isto gera uma enorme flexibilidade quando usado com media queries, em mudanças de orientação, etc.

A sintaxe para esta propriedade é assim (projeto de trabalho no W3C &#8211; working draft &#8211; a partir de 2 de abril de 2013):

<pre class="lang-css">.parent {
   display: grid; /* declare o grid */
   grid-definition-columns: 1stgridsize  2ndgridsize …;
   grid-definition-rows: 1strowsize  2ndrowsize …;
}

.element {
   grid-column: 1;
   grid-row: 1;
}

.element2 {
   grid-column: 1; 
   grid-row: 3;
}
</pre>

Para definir o tamanho das linhas e colunas você pode usar diversas unidades, conforme [detalhado na especificação][2]. Para posicionar os elementos, a especificação diz o seguinte: &#8220;Cada parte está posicionada entre as linhas do grid, fazendo referência a linha de grid inicial e então especificando, se houver mais de uma, o número de linhas ou colunas distribuídas para determinar a linha de grid final, delimitando a área do layout&#8221;.

O maior problema com esta propriedade é que é <a href="http://caniuse.com/#feat=css-grid" target="_blank">suportada apenas pelo IE10</a>. Para aprender mais sobre este layout, leia o artigo &#8220;<a href="http://24ways.org/2012/css3-grid-layout/" target="_blank">Giving Content Priority With CSS3 Grid Layout</a>&#8221; de Rachel Andrew. Além disso, note que a especificação e a sintaxe para grid layouts com CSS foi alterada no dia 2 de abril de 2013. Andrew escreveu uma atualização sobre a sintaxe, a qual foi intitulada de <a href="http://www.rachelandrew.co.uk/archives/2013/04/10/css-grid-layout---what-has-changed/" target="_blank">&#8220;CSS Grid Layout: What Has Changed?&#8221;</a> (CSS Grid Layout: O que mudou?).

O último layout, que pode tornar-se bastante útil no futuro se implementado nos browsers, é o <a href="http://www.w3.org/TR/2009/WD-css3-layout-20090402/" target="_blank">CSS3 template layout</a>. Este módulo CSS3 funciona associando um elemento ao &#8220;nome&#8221; do layout, e em seguida ordenando os elementos num grid invisível. O grid pode ser fixo ou flexível, e pode ser alterado de acordo com o tamanho da viewport.

A sintaxe fica assim:

<pre class="lang-css">.parent {
   display: "ab"
            "cd"; /* criando um grid invisível */
}

.child1 {
   position: a;
}

.child2 {
   position: b;
}

.child3 {
   position: c;
}

.child4 {
   position: d;
}
</pre>

E é renderizado assim:

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307110848.jpg" target="_blank"><img alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307110848.jpg?itok=y7SmFn5a" width="477" height="297" /></a>

Infelizmente, o suporte a navegadores para este módulo é praticamente nulo. Talvez algum dia, se designers e desenvolvedores mostrarem interesse suficiente nesta especificação, algum fabricante de browser possa implementá-lo. Por enquanto, você pode testá-lo usando <a href="https://code.google.com/p/css-template-layout/" target="_blank">um polyfill</a>.

### Unidades Relativas da Viewport e o fim do Layout baseado em pixels

<a href="http://www.w3.org/TR/css3-values/#viewport-relative-lengths" target="_blank">Medidas de comprimento baseadas na viewport</a> &#8211; _vw_, _vh_, _vm_, _vmin_ e _vmax_ &#8211; são unidades de medida relativa das dimensões da própria viewport.

Uma unidade vw é igual a 1% da largura do bloco inicial que a contém. Se a largura da viewport é 320, então 1_vw_ é 1 x 320/100 = 3.2 pixels.

A unidade vh funciona da mesma maneira, mas é relativa a altura da viewport. Desta forma, 50 _vh_ equivale a 50% da altura do documento. A esta altura você pode se perguntar qual a diferença desta unidade para a percentual. A diferença é que enquanto a unidade percentual é relativa ao tamanho do elemento pai, as unidades _vh_ e _vw_ serão sempre relativas ao tamanho da viewport, independente do tamanho dos seus elementos-pai.

Isso fica bem interessante quando você quer, por exemplo, criar um container e ter a certeza de que ele nunca se extenderá abaixo da altura do viewport para que o usuário não precise rolar a página para baixo para achar o conteúdo.  Também possibilita que criemos um elemento com 100% da altura sem alterar todos os containers pai.

A unidade _vmin_ é igualada ao menor valor da unidade _vm_ ou _vh_, e _vmax_ ao maior valor; por isso, essas unidades também respondem perfeitamente às alterações na orientação dos dispositivos. Infelizmente, por enquanto, <a href="http://caniuse.com/#feat=viewport-units" target="_blank">essas unidades não são suportadas pelo browser do Android</a>. Sendo assim, pode ser que você ainda tenha que aguardar um tempo para utilizá-las.

### Uma Palavra sobre Tipografia Adaptável (Adaptive Typography)

O layout de um site vai depender muito do conteúdo. Não posso concluir uma seção que fala sobre as diversas possibilidades do layout responsivo sem abordar a tipografia. O CSS3 introduziu uma unidade para fontes que pode ser bastante útil a tipografia responsiva: <a href="http://www.w3.org/TR/css3-values/#font-relative-lengths" target="_blank">a unidade “<em>rem</em>”</a>. Enquanto as fontes medidas pela unidade “_em_” apresentam um tamanho herdado do seu elemento pai, a fonte medida pela unidade “rem” é relativa ao tamanho da fonte do seu elemento root (ou raiz). Para um site responsivo, você poderia escrever o CSS como o código abaixo, e em seguida alterar o tamanho de todas as fontes simplesmente mudando o tamanho da fonte especificada no elemento _html_:

<pre class="lang-css">html {
   font-size: 14px;
}

p {
   font-size: 1rem /* isto tem 14px */
}

@media screen and (max-width:380px) {
   html {
      font-size: 12px;
      /* tornando a fonte menor para dispositivos mobile */
   }

   p {
      font-size: 1rem;
      /* isto agora equivale a 12px */
   }
}
</pre>

Com exceção do IE8 e do Opera mini, o <a href="http://caniuse.com/#search=rem" target="_blank">suporte ao &#8220;<em>rem</em>&#8220;</a> é excelente. Para aprender mais sobre a unidade _rem_, leia o artigo de Matthew Lettini [&#8220;In Defense of Rem Units&#8221;][3].

## A Melhor Maneira de Trabalhar Responsivamente com Outros Conteúdos Complexos

Aos poucos vamos ficando cada vez melhor em lidar com imagens e textos em layouts responsivos, embora ainda seja necessário encontrar soluções para outros tipos mais complexos de conteúdo

### Lidando com Formulários no Website Responsivo

De um modo geral, lidar com formulários, especialmente os muito grandes, no web design responsivo é um enorme desafio! Quanto maior o formulário, mais complicado será adaptá-lo a dispositivos menores. A adaptação física não é tão difícil; a maioria dos designers simplesmente colocam os elementos do formulário numa única coluna e esticam os inputs completando a largura da tela. Entretanto, fazer formulários visualmente atraentes não é o bastante. Temos que torná-los fáceis de usar também nos dispositivos mobile.

Para começar, <a href="http://uxdesign.smashingmagazine.com/2010/03/11/forms-on-mobile-devices-modern-solutions/" target="_blank">Luke Wroblewski aconselha</a> evitar inputs de texto, **contando com checkboxes, radio buttons e menus drop-downs**, e utilizando o select sempre que possível. Desta forma, o usuário precisa digitar o mínimo de informação. Outra dica é não fazer com que o usuário aperte o botão &#8220;enviar&#8221; antes de obter um feedback sobre o conteúdo a ser submetido. A checagem de erros imediata é extremamente importante no mobile, onde a maioria dos formulários ultrapassa a altura da tela. Se o usuário digitar um campo incorretamente e tiver que enviar o formulário para só assim perceber o erro, provavelmente ele não verá onde o erro está.

No futuro, novos inputs e atributos HTML5 serão de grande ajuda na melhoria dos formulários, e não haverá a necessidade de utilizar tanto JavaScript. Por exemplo, você poderia usar o <a href="http://www.w3.org/wiki/HTML5_form_additions#required" target="_blank">atributo</a> _required_ para dar feedback imediato sobre um campo específico. Infelizmente, por enquanto, <a href="http://caniuse.com/#search=required" target="_blank">o suporte para dispositivos mobile</a> ainda é ruim. O <a href="http://www.w3.org/TR/2011/WD-html5-20110525/common-input-element-attributes.html#the-autocomplete-attribute" target="_blank">atributo</a> _autocomplete_ também poderia ajudar a montar formulários mais responsivos.

Um smartphone é um bem pessoal, por isso podemos assumir que dados como nome e endereço serão algo consistente. Usando o atributo _autocomplete_ do HTML5 **poderíamos fazer um auto-preenchimento dos campos** sem que o usuário tivesse que digitar todas as informações. Há ainda uma <a href="http://www.w3.org/wiki/HTML5_form_additions#New_form_controls" target="_blank">lista inteira de novos inputs HTML5</a> que podem ser utilizados muito em breve, a fim de tornar os formulários mais responsivos.

Datas em elementos de formulário são um bom exemplo do que se pode melhorar com o HTML5. Já estamos acostumados a contar com JavaScript ao criar calendários. Eles podem ser muito úteis se utilizados em grandes telas desktop, mas difíceis de usar em dispositivos touch screen, pois selecionar a data certa com o dedo é difícil quando a área sensível ao toque é muito pequena.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307110938.jpg" target="_blank"><img title="Como posso selecionar uma data se meu dedo está tocando três ao mesmo tempo?" alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307110938.jpg?itok=sakIwk63" width="478" height="248" longdesc="" /></a>

Uma solução promissora está no novo _input type=&#8221;date&#8221;_ do HTML5 , que define uma string no formato de data. Já o _input type=&#8221;datetime&#8221;_ define uma string no formato de data e hora. A grande vantagem deste método é que deixamos o browser decidir qual UI utilizar. Desta forma, a UI é automaticamente otimizada em dispositivos mobile. Abaixo um exemplo da aparência de um _input type=&#8221;date&#8221;_ no desktop, em smartphone e tablet com Android (com o browser Chrome), Iphone e Ipad.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307111218.jpg" target="_blank"><img title="Renderização do input input type=&quot;date&quot; em diferentes dispositivos." alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307111218.jpg?itok=dEKeEFpj" width="402" height="478" longdesc="" /></a>

Note que as screenshots foram feitas em meu browser e no Android phone, então a linguagem foi automaticamente adaptada ao sistema de linguagem (Francês). Ao utilizar componentes nativos, você não precisa mais adaptar a lingua para diferentes versões do site.

Por enquanto, com exceção do Opera e do Chrome, <a href="http://caniuse.com/input-datetime" target="_blank">não há suporte</a> ao _input type=&#8221;date&#8221;_ para o desktop. Browsers nativos do Android ainda não o suportam completamente, mas o Chrome Android sim, e também o Safari para iOS. O fato é que ainda há muito a ser trabalhado para sermos capazes de utilizar esta solução em sites responsivos. Enquanto isto, você pode usar um polyfill como o <a href="http://demo.mobiscroll.com/calendar/calendartime" target="_blank">Mobiscroll</a> para browsers mobile que não suportarem o atributo nativamente.

Além destas soluções de inputs HTML5, foram feitas tentativas para melhorar outros padrões de design, como as <a href="http://www.lukew.com/ff/entry.asp?1653" target="_blank">senhas do mobile</a> e <a href="http://www.lukew.com/ff/entry.asp?756" target="_blank">inputs complexos utilizando máscaras</a>. Como você pode notar, isto tudo é experimental. O formulário responsivo perfeito não existe no momento; Muito ainda deve ser feito neste campo.

### Lidando com Tabelas em Sites Responsivos

Outro tipo de conteúdo que fica bastante confuso em sites mobile e responsivos são as tabelas. A maioria das tabelas são orientadas horizontalmente e apresentam uma grande quantidade de dados de uma só vez. Imagine então que exibi-las corretamente em small screens seja bem complicado. Tabelas HTML são bastante flexíveis &#8211; você pode usar porcentagens para mudar a largura das colunas &#8211; o que também pode rapidamente tornar o conteúdo ilegível.

Ainda não encontraram uma forma perfeita de mostrar tabelas, mas algumas sugestões foram feitas:

Uma forma de abordagem é **esconder colunas consideradas &#8220;menos importantes&#8221;**, e oferecer checkboxes para que o usuário escolha quais ele deseja ver. No desktop, todas as colunas seriam mostradas, enquanto no mobile o número de colunas dependeria do tamanho da tela. O Filament Group <a href="http://filamentgroup.com/lab/responsive_design_approach_for_complex_multicolumn_data_tables/" target="_blank">explica este método</a> e <a href="http://filamentgroup.com/examples/rwd-table-patterns/" target="_blank">demonstra</a> em um de seus artigos. A solução também é usada no <a href="http://view.jquerymobile.com/tables/docs/tables/table-column-toggle.html" target="_blank">table column toggle do jQuery Mobile</a>.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307111308.jpg" target="_blank"><img title="Alguns exemplos de tabelas responsivas." alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307111308.jpg?itok=buAWCW1w" width="479" height="429" longdesc="" /></a>

A segunda abordagem brinca com a ideia de **scroll em tabelas**. Você poderia &#8220;fixar&#8221; uma única coluna com tamanho fixo a esquerda, e então deixar uma scroll bar numa pequena parte da tabela a direita. <a href="http://dbushell.com/2012/01/05/responsive-tables-2/" target="_blank">David Bushell implementa esta ideia</a> em um artigo usando CSS para exibir todo o conteúdo da _
  
_ 

&nbsp;

__ do lado esquerdo da tabela, deixando o usuário mover-se pelo conteúdo a direita através da scroll bar. **Zurb** utiliza a mesma ideia, mas de um jeito diferente, <a href="http://zurb.com/playground/responsive-tables" target="_blank">neste plug in</a>. Neste caso, as headers ficam no topo da tabela, e a tabela é duplicada com JavaScript de modo que apenas a primeira coluna seja mostrada a esquerda, e as demais colunas sejam mostradas do lado direito através da scroll bar.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307111348.jpg" target="_blank"><img title="Dois exemplos de tabelas responsivas com scroll" alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307111348.jpg?itok=2bOK8ygE" width="477" height="455" longdesc="" /></a>

A grande questão em utilizar scroll bars e propriedades CSS tais como _overflow: auto_ é que muitos dispositivos mobile e tablets simplesmente não exibem uma scroll bar visível. A área da direita da tabela permite a rolagem, mas o usuário não terá qualquer indício visual desta possibilidade. Precisamos encontrar uma maneira de indicar que há mais conteúdo a ser exibido à direita.

Uma terceira abordagem é em **reestruturar a tabela e dividir as colunas** em listas de itens com cabeçalhos.Esta técnica é utilizada no <a href="http://view.jquerymobile.com/tables/docs/tables/table-reflow.html" target="_blank">&#8220;reflow mode&#8221;</a> no jQuery Mobile e foi explicada por Chris Coyier em seu artigo [“Responsive Data Tables”][4].

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307111441.jpg" target="_blank"><img title="Reestruturando uma tabela para dispositivos móveis" alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307111441.jpg?itok=nOmy8Tpm" width="478" height="438" longdesc="" /></a>

Existem <a href="http://css-tricks.com/responsive-data-table-roundup/" target="_blank">diversas outras técnicas</a>, e qual usar depende muito do seu projeto. Não há dois projetos iguais, por isso só posso mostrar como outras pessoas estão lidando com isto. Se você chegar a uma boa solução, por favor compartilhe nos comentários, no Twitter ou em qualquer outro lugar. Estamos no mesmo barco, e exibir tabelas no mobile está uma droga (é sério). Então vamos melhorá-las juntos!

## Incorporando Conteúdo de Terceiros: O problema do Iframe Responsivo

Muitos desses conteúdos, ao serem incorporados, fazem você utilizar iframes. Mas vamos encarar: lidar com iframes no design responsivo é doloroso. O  grande problema é que iframes exigem largura e altura fixa diretamente no seu código HTML. Forçar uma largura de 100% no iframe deveria resolver, mas daí você perderia a proporção do conteúdo incorporado. Então, para incorporar um vídeo ou slideshow e preservar a proporção original, seria necessário encontrar uma solução alternativa.

### Uma solução com HTML e CSS

<a href="http://www.tjkdesign.com/" target="_blank">Thierry Koblentz</a> escreveu um ótimo artigo chamado <a href="http://alistapart.com/article/creating-intrinsic-ratios-for-video" target="_blank">&#8220;Creating Intrinsic Ratios for Vídeo&#8221;</a> (criando proporções intrínsecas para vídeos), onde ele propõe uma forma de incorporar vídeos responsivos usando uma proporção 16:9. Esta solução pode ser estendida a outros tipos de conteúdos, como apresentações em SlideShare e Google Maps. Koblentz envolve o iframe num container usando uma classe a qual podemos manipular no CSS. O container torna possível o iframe ser redimensionado fluidamente, mesmo tendo um valor fixo de pixels no HTML. O <a href="http://amobil.se/2011/11/responsive-embeds/" target="_blank">código, adaptado por Anders M. Andersen</a>, fica assim:

<pre class="lang-css">.embed-container  {
   position: relative;
   padding-bottom: 56.25%; /* 16:9 ratio */
   padding-top: 30px; /* solução para IE 6 */
   height: 0;
   overflow: hidden;
}

.embed-container iframe,
.embed-container object,
.embed-container embed {
   position: absolute;
   top: 0;
   left: 0;
   width: 100%;
   height: 100%;
}
</pre>

Isto vai funcionar em todos os iframes. O único problema é que você terá que envolver todos os iframes de seu site em um elemento. Enquanto esta técnica funcionaria muito bem para desenvolvedores que tivessem controle total de seu código, ou para clientes que estivessem razoavelmente familiarizados com HTML, não funcionaria com clientes que não tivessem qualquer habilidade técnica. Você poderia, é claro, usar JavaScript para detectar os elementos iframe e automaticamente incorporá-los na classe, mas como podemos ver, seria uma grande solução, mas não a solução perfeita.

## Lidando com Vídeos Responsivos no Futuro

O HTML5 abre um mundo de possibilidades para o vídeo &#8211; particularmente com o [elemento video][5]. A grande notícia é que o <a href="http://caniuse.com/#feat=video" target="_blank">suporte a este elemento é surpreendentemente bom em dispositivos mobile</a>! Com exceção do Opera Mini, a maioria dos browsers o suportam. O elemento video também é bastante flexível, e apresentar um vídeo responsivo é tão simples quanto isto:

<pre class="lang-css">video {
   max-width: 100%;
   height: auto;
}
</pre>

Você provavelmente está se perguntando, &#8220;Então, qual o problema?&#8221;

O problema é que, embora YouTube e Vimeo suportem o elemento video, você ainda precisa incorporar vídeos usando o tal método do iframe. E isso meu amigo, é uma droga. Sendo assim, até que YouTube e Vimeo ofereçam um meio de incorporar vídeos em sites utilizando a tag video do HTML5, **teremos que descobrir soluções** para que incorporações de vídeo trabalhem adequadamente em sites responsivos. Pensando nisto, Chris Coyier criou uma solução com um plugin jQuery chamado <a href="http://fitvidsjs.com/" target="_blank">FitVids.js</a>. Ele usa a primeira técnica mencionada acima: cria um container em torno do iframe e preserva a sua proporção.

### Incorporando Google Maps

Se você incorporou um Google Map em seu site, a técnica descrita acima com container e CSS funcionará. Mas, de novo, é um hackzinho sujo. Além disso, o mapa vai redimensionar proporcionalmente e pode ficar tão pequeno, que poderá perder a área de foco que você quer mostrar ao usuário. A <a href="https://developers.google.com/maps/" target="_blank">página do Google Maps para mobile</a> diz que você pode utilizar uma <a href="https://developers.google.com/maps/documentation/staticmaps/" target="_blank">API de mapas estáticos</a> para incorporações mobile. Usar um mapa estático de fato eliminaria os problemas com iframe. Brad Frost escreveu um belo artigo a respeito, e criou uma demo de <a href="http://bradfrostweb.com/blog/post/adaptive-maps/" target="_blank">mapas adaptáveis (adaptive maps)</a> onde utiliza a mesma técnica. Um JavaScript detecta o tamanho da tela, em seguida o iframe é substituído pelo mapa estático em celulares. Como podemos ver, temos novamente que recorrer a técnicas que lidem com problemas de iframe, devido a ausência de uma solução nativa (ou seja, do Google).

### Precisamos de APIS Melhores

Agora a grande pergunta: Há um jeito melhor? O maior problema em usar iframes para incorporar o conteúdo de terceiros responsivamente é a falta de controle sobre o código gerado. **Desenvolvedores e designers são muito dependentes** de conteúdo de terceiros e, por extensão, o seu HTML gerado. E o número de sites que oferecem conteúdo de outros sites cresce rapidamente. Precisamos de soluções muito melhores do que iframes para incorporar este conteúdo.

Agora, fale a verdade: incorporar iframes do Facebook é um verdadeiro sofrimento. A falta de controle sobre o CSS pode fazer nosso trabalho parecer bem desleixado e algumas vezes arruinar o design. A web é um lugar aberto, por isso talvez fosse um bom momento em começar a pensar em mais API&#8217;s abertas! No futuro, vamos precisar de API&#8217;s que sejam melhores e mais simples de utilizar, de modo que qualquer pessoa possa incorporar um conteúdo de maneira flexível, sem ter que contar com iframes fixos não responsivos. No entanto, até que decidam criar essas API&#8217;s, estamos presos a iframes medíocres, tendo que recorrer a truques para torná-los viáveis.

## Navegação Responsiva: Um Panorama pelas Soluções Atuais

Outro grande desafio é o que fazer com a navegação. Quanto mais complexa e profunda a arquitetura de um website, mais inventivos precisamos ser.

(Nota do tradutor: publiquei aqui no Tableless uma tradução sobre [padrões complexos de navegação no web design responsivo][6])

Uma das primeiras tentativas de lidar com isto de maneira simples foi <a href="http://css-tricks.com/convert-menu-to-dropdown/" target="_blank">converter a navegação em um menu dropdown</a> para telas pequenas. Infelizmente, esta forma não é a ideal. Primeiro porque esta solução fica terrivelmente complicada numa navegação multi-level, podendo também causar problemas de acessibilidade. Eu recomendo o artigo <a href="http://uxmovement.com/forms/stop-misusing-select-menus/" target="_blank">&#8220;Stop Misusing Select Menus&#8221;</a> para entender todos os problemas consequentes desta técnica.

Algumas pessoas, incluindo <a href="http://bradfrostweb.com/blog/web/responsive-nav-patterns/" target="_blank">Brad Frost</a> e Luke Wroblewski, têm tentado resolver este problema. Brad Frost compilou algumas de suas técnicas no site [This Is Responsive][7], na seção de navegação.

A navegação alternada (toggle navigation) envolve ocultar o menu nos dispositivos mobile, exibindo um único link. Quando o usuário dá um clique todos os links aparecem como um bloco de elementos abaixo do link, empurrando o conteúdo principal pra baixo da navegação.

Uma variante deste tipo de menu, inspirado em alguns padrões de aplicativos nativos, é a navegação <a href="http://coding.smashingmagazine.com/2013/01/15/off-canvas-navigation-for-responsive-website/" target="_blank">off-canvas</a>. Essa navegação fica escondida debaixo de um link no menu ou ícone. Quano o usuário clica, a navegação desliza em forma de painel pela esquerda ou direita, empurrando o conteúdo principal.

<a href="http://www.bbburp.com.br/sites/default/files/images/20130307111531.jpg" target="_blank"><img title="Alguns exemplos do toggle navigation" alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307111531.jpg?itok=LzZHvbzg" width="478" height="225" longdesc="" /></a>

<div>
  <p>
    O problema com essas técnicas é que a navegação permanece no topo da tela. Neste artigo <a href="http://www.lukew.com/ff/entry.asp?1649">&#8220;Responsive Navigation: Optimizing for Touch Across Devices&#8221;</a>, Luke Wroblewski mostra <strong>quais zonas são facilmente acessíveis aos diferentes tipos de dispositivos</strong>. A área superior esquerda é a mais difícil de chegar num dispositivo mobile.
  </p>
  
  <p>
    <a href="http://www.bbburp.com.br/sites/default/files/images/20130307111609.jpg" target="_blank"><img title="Áreas facilmente acessíveis na tela de celulares e tablets, de acordo com Luke Wroblewski." alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307111609.jpg?itok=1xGtEHVW" width="478" height="356" longdesc="" /></a>
  </p>
</div>

Com base nisto, Jason Weaver criou <a href="http://jasonweaver.name/lab/touchnav/v2/" target="_blank">algumas demos</a> com a navegação no bottom da tela. Uma solução é o <a href="http://codepen.io/bradfrost/full/mlyvu" target="_blank">footer anchor</a> (âncora de rodapé), com a navegação fixada no bottom da página para dispositivos menores, e um menu link que envia o usuário até lá. Esta técnica utiliza o sistema link âncora do HTML.

<div>
  <p>
    <a href="http://codepen.io/bradfrost/full/orJwL" target="_blank">Diversas</a> outras <a href="http://codepen.io/bradfrost/full/vcuem" target="_blank">tentativas</a> foram <a href="http://codepen.io/bradfrost/full/qwJvF" target="_blank">feitas</a> para solucionar problemas de navegação no web design responsivo. Como você pode ver, ainda não há uma solução perfeita; isso realmente depende do projeto e da profundidade da navegação. Felizmente para nós, alguma pessoas estão tentando resolver esse problema e têm compartilhado suas experiências com a comunidade.
  </p>
  
  <p>
    <strong>Outra questão não resolvida é qual ícone usar</strong> para dizer ao usuário &#8220;Olá! há um menu escondido aqui. Clique em mim!&#8221;. Alguns websites tem um símbolo de mais (+), outros uma grade de quadrados e alguns têm três linhas (como um ícone de hamburger).
  </p>
  
  <p>
    <a href="http://www.bbburp.com.br/sites/default/files/images/20130307111659.jpg" target="_blank"><img alt="" src="http://www.bbburp.com.br/sites/default/files/styles/large/public/images/20130307111659.jpg?itok=Sa8jlYOv" width="477" height="138" /></a>
  </p>
  
  <p>
    Para ver esses ícones usado em websites reais, dê uma olhada no <a href="http://stuffandnonsense.co.uk/blog/about/we_need_a_standard_show_navigation_icon_for_responsive_web_design" target="_blank">&#8220;We Need a Standard ‘Show Navigation’ Icon for Responsive Web Design”</a> (precisamos de um ícone padrão no web design responsivo para &#8220;mostrar a navegação&#8221;).
  </p>
  
  <p>
    O maior problema é descobrir qual desses ícones seria o mais reconhecível a uma quantidade de usuários. Se todos concordássemos em usar um deles, os usuários seriam instruídos a reconhecê-los. O problema é, qual escolher? Eu realmente gostaria de saber qual ícone vocês usam, então não hesite em compartilhar nos comentários 1 (1 &#8211; nota do tradutor: para deixar sua opinião sobre qual o ícone você utiliza, acesse o artigo original).
  </p>
  
  <h2>
    Especificidades Mobile: &#8220;O usuário está com um dispositivo mobile? Se sim, o que pode ser feito?&#8221;
  </h2>
  
  <p>
    Dispositivos mobile e tablets são um mundo novo &#8211; longe dos computadores desktops -, com suas próprias regras, comportamentos e capacidades. Podemos querer adaptar nossos projetos a esta nova gama de capacidades.
  </p>
  
  <h3>
    Detectando Capacidades Touch com JavaScript Nativo
  </h3>
  
  <p>
    Além do tamanho da tela, aposto que se você perguntasse qual a principal diferença entre mobiles (incluindo tablets) e desktops, a maioria das pessoas diriam ser a capacidade touch. Não há mouse num celular (é verdade!), e com exceção de alguns dispositivos híbridos raros, em que você pode plugar um mouse, você não vai poder realizar muitos eventos num tablet com um mouse. Isto significa que, dependendo do browser, a pseudo-classe <em>:hover</em> do CSS pode não funcionar. Alguns browsers são inteligentes o bastante para oferecer um fallback nativo ao evento do hover traduzindo em um evento touch. Infelizmente, nem todos os browsers são tão flexíveis assim. Criar um design que não dependa de elementos ocultos, a serem revelados sob eventos <em>:hover</em>, seria o mais sensato.
  </p>
  
  <p>
    <strong>Capturar eventos touch</strong> poderia também ser uma outra solução. A W3C working group começou a trabalhar numa <a href="http://www.w3.org/TR/touch-events/" target="_blank">especificação de eventos touch</a>. Futuramente, seremos capazes de capturar eventos tais como <em>touchstart</em>, <em>touchmove</em> e <em>toucheend</em>. Seremos capazes de lidar com esses eventos diretamente no JavaScript sem a necessidade de frameworks de terceiros como <a href="http://eightmedia.github.io/hammer.js/" target="_blank">Hammer.js</a> ou <a href="http://jgestures.codeplex.com/" target="_blank">jGestures</a>. Mas JavaScript é uma coisa &#8211; E o que acontece com o CSS?
  </p>
  
  <h3>
    CSS nível 4 &#8211; Media Query &#8220;Pointer&#8221;
  </h3>
  
  <p>
    O CSS nível 4 especifica uma <a href="http://dev.w3.org/csswg/mediaqueries4/#pointer" target="_blank">nova media querry chamada &#8220;pointer&#8221;</a>, que pode ser usada para capturar a existência e precisão de um dispositivo apontador (pointing device), tal como um mouse. A media query tem um dos três valores:
  </p>
  
  <ul>
    <li>
      <em>none</em><br /> O dispositivo não tem nenhum pointing device.
    </li>
    <li>
      <em>coarse</em><br /> O dispositivo tem um pointing device com precisão limitada, por exemplo, um celular ou tablet com capacidades touch, onde o &#8220;pointer&#8221; seria um dedo.
    </li>
    <li>
      <em>fine</em><br /> O dispositivo tem um pointing device preciso, como um mouse, trackpad ou caneta (stylus).
    </li>
  </ul>
  
  <p>
    Usando esta media query, nós podemos ampliar a maneira de utilização de botões e links para dispositivos móveis:
  </p>
  
  <pre class="lang-css">
@media  (pointer:coarse) {
   input[type="submit"],
       a.button {
       min-width: 30px;
       min-height: 40px;
       background: transparent;
   }
}
</pre>
  
  <p>
    A media query pointer ainda não é suportada &#8211; apenas sendo proposta. Todavia, ser potencial é enorme, pois seria permitiria <strong>detectar dispositivos touch via CSS</strong>, sem a necessidade de uma bilbioteca, como <a href="http://modernizr.com/docs/#touch" target="_blank">Modernizr</a>.
  </p>
  
  <h3>
    CSS nível 4 &#8211; Media Query &#8220;Hover&#8221;
  </h3>
  
  <p>
    A especificação CSS nível 4 propõe uma nova <a href="http://dev.w3.org/csswg/mediaqueries4/#hover" target="_blank">media query hover</a>, que detecta se o sistema primário do dispositivo dá suporte ao hover. Ele retorna valores<em> boleanos: 1</em> se o dispositivo suporta hover, <em></em> se não suporta. Note que isto não tem nada a ver com a pseudo-classe <em>:hover</em>.
  </p>
  
  <p>
    Usando a media query hover podemos melhorar a interface e ocultar certas características dos dispositivos que o suportam. O código fica mais ou menos assim:
  </p>
  
  <pre class="lang-css">
@media  (hover) {
   .hovercontent { display: none; }
   /* oculta o conteúdo apenas para dispositivos com suporte ao hover. */
   .hovercontent:hover { display: block; }
}
</pre>
  
  <p>
    Pode também ser usado para criar menus dropdowns com hover; e o fallback para dispositivos mobile é em CSS nativo, sem a necessidade de um framework que detecte a feature.
  </p>
  
  <h3>
    CSS nível 4 &#8211; Media Query Luminosity
  </h3>
  
  <p>
    Outra capacidade dos dispositivos mobile é o sensor de luminosidade. A especificação CSS nível 4 tem a <a href="http://dev.w3.org/csswg/mediaqueries4/#luminosity" target="_blank">media query luminosity</a>, que nos dá acesso ao sensor de luz dos dispositivos diretamente no CSS. Abaixo a descrição da especificação.
  </p>
  
  <blockquote>
    <p>
      A característica da media &#8220;luminosity&#8221; é usada para verificar a luminosidade do ambiente o qual o dispositivo está sendo usado, e permitir que o autor ajuste o estilo do documento responsivamente.
    </p>
  </blockquote>
  
  <p>
    No futuro, seremos capazes de criar <strong>websites que respondam a luminosidade do ambiente</strong>. Isto vai melhorar muito a experiência do usuário. Seremos capazes de detectar, por exemplo, ambientes extremamente brilhantes usando o valor <em>washed</em>, adaptando o contraste do site ao local. O valor <em>dim</em> é usado para ambientes escuros (a noite por exemplo), e o valor <em>normal</em> para quando o nível de luminosidade não necessita de qualquer tipo de adaptação.
  </p>
  
  <p>
    O código fica assim:
  </p>
  
  <pre class="lang-css">
@media  (luminosity: washed) {
   p { background: white; color: black; font-size: 2em; }
}
</pre>
  
  <p>
    Como podemos ver, as CSS4 prometem um monte de coisas novas. Se você está curioso em ver o que vem por aí &#8211; não só para mobile &#8211; então dê uma olhada na <a href="http://coding.smashingmagazine.com/2013/01/21/sneak-peek-future-selectors-level-4/" target="_blank">&#8220;Sneak Peek Into the Future: Selectors, Level 4&#8221;</a>
  </p>
  
  <h3>
    Mais Recursos Mobile para Detectar o Uso de API&#8217;s e JavaScript
  </h3>
  
  <p>
    Muitas outras coisas poderiam ser detectadas para tornar a experiência do usuário surpreendente num site responsivo. Por exemplo, poderíamos ter acesso nativo ao giroscópio, bússola e acelerômetro para detectar a orientação do dispositivo usando o <em>DeviceOrientationEvent</em> do HTML5. O <a href="http://caniuse.com/#feat=deviceorientation">suporte ao DeviceOrientationEvent</a> nos browsers do Android e iOS está ficando cada vez melhor, mas a especificação ainda está em fase de rascunho. No entanto, a API parece promissora. Imagine jogar jogos HTML5 diretamente no browser!
  </p>
  
  <p>
    Outra API que seria particularmente utilizada por alguns usuários mobile é a de <a href="http://dev.w3.org/geo/api/spec-source.html" target="_blank">geolocation</a>. A boa notícia é que ela já é <a href="http://caniuse.com/#search=geolocation" target="_blank">bem suportada</a>. Esta API <strong>nos permite localizar geograficamente o usuário usando o GPS</strong> e inferir sua localização a partir de sinais de rede, como IP, RFID, Wi-Fi e endereços MAC Bluetooth. Isto pode ser usado em alguns sites responsivos para oferecer informações contextuais aos usuários. Uma grande cadeia de restaurantes poderia melhorar sua experiência mobile mostrando aos usuários a localização de seus restaurantes em sua área. As possibilidades são infinitas.
  </p>
  
  <p>
    A W3C também propôs um rascunho para uma <a href="http://dev.w3.org/2009/dap/vibration/" target="_blank">API de vibração</a>. Nele o browser pode oferecer um feedbacl tátil ao usuário em forma de vibração. Isto, no entanto, ainda está engatinhando em campos mais específicos de aplicações Web and mobile games in the browser.
  </p>
  
  <p>
    Outra API que tem sido altamente discutida é a <a href="http://www.w3.org/TR/netinfo-api/" target="_blank">network information API</a>. A possibilidade de medir a largura de banda do usuário, e otimizar conforme o resultado, tem seduzido muitos desenvolvedores. Seriamos capazes de servir imagens com qualidade de alta definição para usuários com alta largura de banda e imagens de baixa qualidade aos usuários com baixa largura de banda. Com o atributo <em>bandwith</em> da network API, seria possível calcular a velocidade de download de um usuário em megabytes por segundo. O segundo atributo, <em>metered</em>, é um booleano que nos diz se o usuário tem uma conexão aferida (como um cartão pré-pago). Esses dois atributos são atualmente acessíveis via JavaScript.
  </p>
  
  <p>
    Infelizmente, <strong>medir a conexão de um usuário é algo tecnicamente complicado</strong>, pois uma conexão poderia mudar de forma abrupta. O usuário poderia, por exemplo, entrar num túnel e perder sua conexão, ou sua velocidade poderia cair de repente. Sendo assim, a media query mágica que mede a largura de banda parece ser hipotética no momento. Yoav Weiis escreveu um belo artigo sobre os problemas criados por essa media query e sobre medição de largura de banda chamado <a href="http://mobile.smashingmagazine.com/2013/01/09/bandwidth-media-queries-we-dont-need-em/" target="_blank">“Bandwidth Media Queries? We Don’t Need ’Em!”</a> (media queries de largura de banda? Não precisamos delas!&#8221;)
  </p>
  
  <p>
    Muitas outras API&#8217;s lidam com recursos mobile. Se você estiver interessado em aprender mais, a Mozilla tem uma <a href="https://wiki.mozilla.org/WebAPI" target="_blank">lista bem detalhada</a>. A maioria ainda não está completamente disponível ou padronizada, e é destinada mais a aplicações web do que a sites responsivos. No entanto, é um ótimo panorama de como grandes e complexos sites mobile podem ser no futuro.
  </p>
  
  <h2>
    Repensando a Maneira Como Nós e o Usuário Lidamos com o Conteúdo
  </h2>
  
  <p>
    Do ponto de vista técnico, ainda existem muitos desafios ao lidar com o conteúdo em grande escala. O método mobile-first tem sido parte do processo de desenvolvimento e design já há algum tempo. Poderíamos, por exemplo, servir a dispositivos mobile o mínimo de dados necessários, e então usar JavaScript e AJAX para condicionalmente carregar mais conteúdo e imagens para desktop e tablets. No entanto, para isto, também teríamos que <strong>repensar como lidar com o conteúdo</strong> e ser capaz de priorizar uma forma de gerar um conteúdo suficientemente flexível e adaptável. Um bom exemplo disto é o mapa de solução responsiva descrito acima: Carregamos uma imagem para mobile, e melhoramos a experiência com um mapa real para desktops. Quanto mais responsivo o website, mais complexo será lidar com o conteúdo. Um código flexível pode nos ajudar a formatar um conteúdo adaptável.
  </p>
  
  <p>
    Uma forma sugerida por alguns é criar frases responsivas e marcá-las com spans que tenham classes, e então exibi-los de acordo com o tamanho da tela. Aparar trechos das frases para dispositivos menores é possível com media querries. Você pode ver esta técnica no 37signals&#8217; <a href="http://37signals.com/svn/" target="_blank">Signal vs. Noise</a> blog e no artigo de Frankie Roberto <a href="http://www.frankieroberto.com/responsive_text" target="_blank">&#8220;Responsive Text&#8221;</a>. Mesmo que tal técnica pudesse ser usada para melhorar pequenas partes de um website, tais como um slogan do footer, aplicando isto a todos os textos de um site é difícil de imaginar.
  </p>
  
  <p>
    Isto levanta uma questão no web design responsivo que se tornará mais e mais importante no futuro: a importância de meta dados e a estrutura semântica de conteúdo. Se quisermos ser capazes de reutilizar o conteúdo de outros websites automaticamente, eles deverão estar bem estruturados e preparados para isto. Novas tags HTML5 como <em>article</em> e <em>section</em> são um bom começo para ganhar algum significado semântico. O objetivo é pensar e estruturar o conteúdo de modo que um único item (por exemplo, um post em um blog), possa ser reutilizado e exibido em diferentes dispositivos, e em diferentes formatos.
  </p>
  
  <p>
    O grande desafio será <strong>fazer com que os metadados sejam facilmente compreendidos</strong> a todas as pessoas que fazem parte da criação de conteúdo do website. Teremos que explicar a todos eles como os metadados podem ser utilizados para priorizar o conteúdo e programaticamente reunir o conteúdo, sendo uma plataforma independente. Um grande desafio será o de ajudá-los a pensar em blocos reutilizáveis, em vez de um grande pedaço de texto no qual eles copiam e colam conteúdo do Microsoft Word no seu sistema de gerenciamento de conteúdo WYSIWYG. Teremos que ajudá-los a entender que conteúdo e estrutura são coisas distintas e independentes, como quando os designers tiveram que entender que o conteúdo (HTML) e a apresentação (CSS) eram mantidos melhor separados.
  </p>
  
  <p>
    <strong>Não podemos nos dar ao luxo de escrever um conteúdo que seja orientado a uma única plataforma</strong>. Quem sabe em qual dispositivo ele será publicado daqui a seis meses, ou um ano? <a href="http://mobile.smashingmagazine.com/2013/01/14/preparing-websites-for-the-unexpected/" target="_blank">Precisamos preparar nossos websites para o inesperado</a>. Mas, para isto, precisamos de ferramentas melhores de publicação também. Karen McGrane deu uma palestra intitulada <a href="http://karenmcgrane.com/2012/09/04/adapting-ourselves-to-adaptive-content-video-slides-and-transcript-oh-my/" target="_blank">&#8220;Adapting Ourselves to Adaptive Content&#8221;</a> (Nos Adaptando a um Conteúdo Adaptável), com alguns exemplos reais da indústria editorial. Ela fala sobre o processo de criação de conteúdo reutilizável e apresenta a ideia do COPE: create once and publish everywhere (Criar uma vez e publicar em todos os lugares). Precisamos construir CMS&#8217;s melhores, que possam utilizar e gerar metadados para priorizar o conteúdo. Precisamos explicar às pessoas como o sistema funciona e pensar em objetos de módulos de conteúdo reutilizáveis em vez de páginas WYSIWYG. Como McGrane diz:
  </p>
  
  <blockquote>
    <p>
      &#8220;Você pode escrever três versões diferentes de título; você pode escrever duas versões diferentes de resumos e anexar diversas imagens para isto, com diferentes cortes e tamanhos, e você pode não ser a pessoa responsável em decidir qual imagem ou qual título será exibido em uma determinada plataforma. Essa decisão será tomada pelos metadados. Será feita pelas regras de negócios. [&#8230;] Metadados é a nova direção de arte.&#8221;
    </p>
  </blockquote>
  
  <p>
    Truncar o conteúdo para dispositivos menores não é uma estratégia de conteúdo &#8220;à prova do futuro&#8221;. Precisamos de CMS&#8217;s que ofereçam a estrutura necessária para criar esse conteúdo reutilizável. Precisamos de melhores workflows de publicação em CMS&#8217;s também. Interfaces desajeitadas assustam os usuários, e a maioria das pessoas que geram conteúdo não estão particularmente confortáveis com ferramentas complicadas. Temos que oferecer a essas pessoas ferramentas mais fáceis de entender e que lhe ajudem a publicar um conteúdo limpo e semântico, independente da apresentação.
  </p>
  
  <h2>
    Conclusão
  </h2>
  
  <p>
    Por mais longo que este artigo seja, <strong>ele só abrange o básico</strong>. Mas agora, a maioria dos leitores da Smashing Magazine entendem que o web design responsivo é muito mais que usar media queries, escolher breakpoints certos e dobrar o tamanho das imagens para celulares de alta densidade. Como você pode ver, o caminho é longo e ainda não chegamos lá. Há ainda muitas questões não resolvidas, e a solução responsiva perfeita ainda não existe.
  </p>
  
  <p>
    Soluções técnicas podem ser descobertas no futuro usando alguma nova tecnologia apresentada neste artigo, com a ajuda da <a href="http://www.w3.org/" target="_blank">W3C</a>, <a href="http://www.whatwg.org/" target="_blank">WHATWG</a> e organizações como o <a href="http://filamentgroup.com/" target="_blank">Filament Group</a>.
  </p>
  
  <p>
    Mais importante, nós web designers e desenvolvedores podemos ajudar a encontrar soluções ainda melhores. Pessoas como <a href="http://www.lukew.com/" target="_blank">Luke Wroblewski</a> e <a href="http://bradfrostweb.com/" target="_blank">Brad Frost</a>, e todas as incríveis pessoas mencionadas neste artigo estão experimentando uma série de soluções e técnicas diferentes. Se serão bem ou mal sucedidas, <strong>a coisa mais importante é compartilhar</strong> o que nós &#8211; designers, desenvolvedores, estrategistas de conteúdo e membros da comunidade web &#8211; estamos fazendo para tentar resolver alguns dos desafios da comunidade do web design. Afinal, estamos todos no mesmo barco, tentando tornar a web um lugar melhor, não estamos?
  </p>
  
  <p>
    &#8212;
  </p>
  
  <p>
    Traduzido com autorização da <a href="http://www.smashingmagazine.com/" target="_blank">Smashing Magazine</a>.
  </p>
  
  <p>
    Artigo original escrito por <a href="http://mobile.smashingmagazine.com/author/stephanie-walter/?rel=author" target="_blank">Stéphanie Walter</a>.
  </p>
  
  <p>
    Acesse o artigo original na <a href="http://mobile.smashingmagazine.com/2013/05/29/the-state-of-responsive-web-design/" target="_blank">Smashing Magazine</a> &#8211; &#8220;The State Of Responsive Web Design&#8221; &#8211; 29 de maio de 2013.
  </p>
  
  <p>
    &#8212;
  </p>

 [1]: http://blog.netvlies.nl/design-interactie/retina-revolution/
 [2]: http://www.w3.org/TR/css3-grid-layout/#grid-definition-columns
 [3]: http://techtime.getharvest.com/blog/in-defense-of-rem-units
 [4]: http://css-tricks.com/responsive-data-tables/
 [5]: http://www.w3.org/wiki/HTML/Elements/video
 [6]: http://tableless.com.br/padroes-complexos-de-navegacao-no-design-responsivo
 [7]: http://bradfrost.github.io/this-is-responsive/patterns.html#navigation