---
title: CSS on steroids
author: Jean Carlo Emer
type: post
date: 2013-11-12
excerpt: E se pudéssemos escrever folhas de estilo de forma mais poderosa, melhorar nosso código? Vamos lá, vamos ver quais as reais vantagens de se utilizar um pré-processador.
url: /css-steroids/
dsq_thread_id: 1957733368
categories:
  - Artigos
  - Código
  - CSS
  - CSS3

---
Os pré-processadores de CSS têm a função de adicionar funcionalidades não nativas às folhas de estilo. Estes açúcares sintáticos, como são chamados, estabelecem uma nova linguagem cujo código precisa ser processado para se tornar CSS e então ser interpretado por qualquer navegador.

Cá entre nós, pré-processadores não são nenhuma novidade, o mais antigo deles surgiu em 2007. O que talvez não seja conhecido por muita gente, inclusive por aqueles que já utilizam um pré-processador, são quais os problemas que eles se propõe a solucionar. Mas estudar pré-processadores como uma linguagem que abrange variáveis, regras aninhadas e _helpers_, maneira como muitos textos e tutoriais apresentam, é leviano demais. Que tal se formos apresentados a folhas de estilos comuns, identificando o que nelas pode ser considerado problemático, e como podemos tornar estes códigos melhores inserindo uma etapa de pré-processamento?

## Medidas

Medidas são elementos bastante importantes na definição de um layout. Mesmo layouts responsivos, que são menos engessados, possuem algumas delas seja na forma de percentual ou mesmo de pixel.

Abaixo um típico código de layout desktop:

<pre class="lang-css">body {       
  width: 960px;
}

.header {
  width: 940px;
}

.speaker-list {
  width: 480px;
}</pre>

A uma primeira vista, estas medidas parecem não ter uma relação. **A tarefa de identificar a relação entre as medidas necessita de raciocínio** **(um pouco) mais apurado**. Assim, identificamos o primeiro e mais importante conceito que pode tornar nosso código melhor: devemos evitar ao máximo que seja preciso raciocinar para compreender relações entre medidas, por exemplo.

Voltando ao código de layout desktop, suas medidas podem ser relacionadas da seguinte maneira: os 940px representam a largura total menos um respiro de 20px e os 480px são simplesmente a metade da largura total.

> The ratio of time spent reading (code) versus writing is well over 10 to 1 &#8230; (therefore) making it easy to read makes it easier to write.<cite>&#8211; Robert C. Martin</cite>

Reescrevendo o código em uma linguagem que será pré-processada podemos utilizar variáveis e tornar estas relações óbvias para futuros codificadores que irão manter o projeto e até para nós mesmos que estamos tendo contato com ele neste momento. Confere o resultado:

<pre class="lang-sass">$site-width: 960px;
$site-gap: 20px;

body {
  width: $site-width;
}

.header {
  width: $site-width - $site-gap;
}

.speaker-list {
  width: $site-width / 2;
}</pre>

## Cores

As cores no CSS são definidas através de um modelo aditivo por ser este comumente utilizado em monitores. Tradicionalmente, definimos as cores no formato RGB hexadecimal.

<pre class="lang-css">.about {
  background: #3F4955;
}

.contact a:hover {
  color: #3F4956;
}

.speaker-list {
  border: 1px solid #3F4955;
}</pre>

A não ser que você seja um exímio conhecedor do formato, é relativamente incomum você identificar qual a aparência da cor com base nestas numerações que indicam os níveis de vermelho, verde e azul.

O mais natural é [atribuir nome às cores][1]. Desta forma, evitamos que seja novamente **necessário raciocínio extra** para identificar quais as cores com base na sua numeração. Além disto, evitamos que erros de digitação passem desapercebidos. Se você mal reparou, a segunda cor está com uma variação diferente em nosso código, típico fruto da falta de atenção ao digitar ou definição errada nos arquivos do layout.

Claro, a grande maioria das cores não possuem nomes, teremos que nomea-las por nós mesmos. Indo um pouco além, o ideal ainda é adicionalmente definir nomes para as cores em uma semântica que faça sentido para o projeto. É papel do designer fornecer as informações que nos levariam a um código que, utilizando variáveis suportadas pelos pré-processadores, se parece com o seguinte:

<pre class="lang-sass">$grey-color: #3F4955;
$main-color: $grey-color;

body {
  color: $main-color;
}

.about {
  background: $main-color;
}

.contact a:hover {
  color: $main-color;
}

.speaker-list {
  border: 1px solid $main-color;
}</pre>

Acho que não é preciso comentar o quão mais fácil de entender este código acabou de ser tornar.

### Variações de cores

Layouts geralmente utilizam diferentes variações de uma mesma cor apenas escurecendo, clareando, adicionando um canal de transparência ou mexendo na saturação.

<pre class="lang-css">body {
  color: #3F4955;
}

.slider {
  color: #293038;
}

.carousel {
  background: rgba(63, 73, 85, 0.8);
}</pre>

O código acima possui apenas cores cinza azuladas. Acho difícil que tenha reparado, mas a cor base é a primeira, a segunda é apenas uma variação mais escura e a última tem apenas o canal de transparência definido. Eu sei, não é evidente, ao menos para mim não é.

Os pré-processadores possuem funções específicas para manipular cores. Com elas, podemos **nos preocupar menos** com as variações das cores enquanto escrevemos nosso código, veja:

<pre class="lang-sass">$grey-color: #3F4955;
$grey-dark-color: darken($grey-color, 10);
$transparent-grey-color: rgba($grey-color, .8);

body {
  color: $grey-color;
}

.slider {
  color: $grey-dark-color;
}

.carousel {
  background: $transparent-grey-color;
}</pre>

## Vendor prefixes

_Vendor prefixes_ possuem implicações fora do escopo deste texto. Mas em linhas gerais, saiba que são a maneira que os fabricantes adicionam suporte para funcionalidades de maneira experimental. O mais importante: estas funcionalidades podem não fazer parte de uma especificação ou fazerem parte de uma especificação ainda não finalizada, cuidado.

_Designeres_ como o Bernard, [são grandes amantes de gradiente][2]. Não nego, quando bem aplicados em um layout fazem toda a diferença. O problema é definir todos os malditos prefixos. Vejamos, em um site como o [Ultimate CSS Gradient Generator][3], o resultado de um gradiente linear simples é o seguinte:

<pre class="lang-css">.slider {
  background: #1e5799; /* Old browsers */
  background: -moz-linear-gradient(left, #1e5799 0%, #7db9e8 100%); /* FF3.6+ */
  background: -webkit-gradient(linear, left top, right top, color-stop(0%,#1e5799), color-stop(100%,#7db9e8)); /* Chrome,Safari4+ */
  background: -webkit-linear-gradient(left, #1e5799 0%,#7db9e8 100%); /* Chrome10+,Safari5.1+ */
  background: -o-linear-gradient(left, #1e5799 0%,#7db9e8 100%); /* Opera 11.10+ */
  background: -ms-linear-gradient(left, #1e5799 0%,#7db9e8 100%); /* IE10+ */
  background: linear-gradient(to right, #1e5799 0%,#7db9e8 100%); /* W3C */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#1e5799', endColorstr='#7db9e8',GradientType=1 ); /* IE6-9 */
}</pre>

Sério, acho complicado demais dar manutenção em código como este. Para poupar este trabalho árduo e, digamos, de resultado duvidoso, os pré-processadores possuem bibliotecas como: [Compass][4], [Nib][5] e [Bourbon][6].

Com o [Compass, é possível declarar o background][7] facilmente e ainda configurar quais navegadores serão suportados:

<pre class="lang-sass">$blue-color: #1E5799;
$light-blue-color: #7DB9E8;

.slider {
  @include background(
    linear-gradient($blue-color, $light-blue-color)
  );
}</pre>

As bibliotecas dão suporte a muitas outras funcionalidades e nunca se esqueça que ainda é possível definir seus próprios _mixins_, veremos a utilidade na sequência.

## Agrupando regras

Talvez você esteja seguindo a risca uma metodologia como [BEM][8] e esta seção então não fará tanto sentido. Em todos os outros casos, é  comum utilizar uma classe para determinar um escopo e passar a estilizar outros elementos descendentes levando em conta esta classe. Sim, estamos falando dos tais componentes e outras abstrações mais simples também.

Todas as regras que estilizam um componente são então escritas próximas uma das outras. O que não garante que por falta de atenção seja inserido no futuro um código sem relação alguma em meio as minhas regras que definem um componente. Alguns desenvolvedores então, por clareza e de modo a evitar futuros deslizes, costumam indentar as regras dos elementos descendentes para deixar mais óbvia a relação entre as regras. Sei não, acho estranho.

Pré-processadores permitem que as regras sejam declaradas umas dentro das outras fazendo com que os seletores sejam somados no resultado final. Muito **mais simples de ler e manter a organização do código**.

<pre class="lang-sass">.slider {
  p {
    margin-bottom: 1em;
  }
  a {
    font-weight: bold;
    &:hover {
      background: $color-secondary;
    }
  }
}</pre>

### Cuidado com os seletores

Um erro comum inspirado pela possibilidade de se escrever código com regras dentro uma das outras é a escrita de toda a árvore de elementos do HTML no CSS. Propriedades aplicadas a seletores como: html body section p a:hover estão longe de ser uma boa prática.

É muito importante sempre ter em mente qual o código gerado pelo pré-processador. **Utilizar um pré-processador não substitui o uso de boas práticas de escrita de CSS**. Na dúvida, [teste o peso dos seletores gerados neste serviço][9].

## Reaproveitando regras

Os frameworks de CSS tem se tornado cada vez mais populares. Uma característica importante a se notar é que todo framework evita a redundância de código CSS criando diversas classes com semântica de aparência para que sejam incluídas no documento: button-large e text-right, por exemplo.

Alguns projetos são ideais para serem desenvolvidos utilizando um framework. Outros estão bem distantes disto sendo que suas classes então devem respeitar a semântica do seu conteúdo ou função. Nestes projetos, sempre acontece de os elementos possuírem igual aparência mas diferente função ou conteúdo, como ilustrado abaixo:

<pre class="lang-css">.address {
  width: 200em;
  height: 300em;
  background: #666;
  color: white;
}

.profile {
  width: 200em;
  height: 300em;
  background: #666;
  color: white;
  font-size: 20em;
}</pre>

De maneira a evitar estas repetições, os pré-processadores permitem estender outras regras e acabam por **agrupar seus seletores sem repetir as propriedades**. Assim, é possível escrever o código do .profile apenas como uma extensão de .address mais esta última propriedade que altera o tamanho da fonte.

<pre class="lang-css">.address {
  width: $box-width;
  height: $box-height;
  background: $box-color;
  color: white;
}

.profile {
  @extend .address;
  font-size: 20em;
}</pre>

Legal, mas a semântica disto é um pouco estranha. Por que estamos fazendo endereço estender perfil, qual a relação entre eles? Alguns pré-processadores acrescentam um seletor especial chamado _placeholder_. Sua função é unicamente ser estendido por outras regras, o _placeholder_ não é impresso diretamente no resultado final.

<pre class="lang-sass">%box {
  width: $box-width;
  height: $box-height;
  background: $box-color;
  color: white;
}

.address {
  @extend %box;
}

.profile {
  @extend %box;
  font-size: 20em;
}</pre>

## Helpers

Novamente, vou deixar vocês com o código parcial de uma folha de estilo:

<pre class="lang-css">.profile {
  position: relative;
  width: 100px;
  background: red;
}
.profile:before {
  content: "";
  position: absolute;
  width: 0;
  height: 0;
  border: 7px solid transparent;
  left: 50%;
  margin-left: -7px;
  top: -13px;
  border-bottom: 7px red solid;
}</pre>

Agora, a pergunta: o que este código representa? Não sei, não faço a menor ideia, até mesmo para mim que o escrevi, em uma primeira análise, é difícil identificar. A dica aqui é: **dê nome a todo conjunto de propriedades que definem um elemento da aparência do seu projeto**, placeholders são ideais para isto.

<pre class="lang-sass">%arrow-top {
  position: relative;
  &:before {
    content: "";
    position: absolute;
    width: 0; height: 0;
    border: 7px solid transparent;
    left: 50%;
    margin-left: -7px;
    top: -13px;
    border-bottom: 7px red solid;
  }
}

.profile {
  width: 100px;
  background: red; 
  @extend %arrow-top;
}</pre>

> Name everything you can. <cite>&#8211; Martin Odersky</cite>

Para o caso de utilizarmos diferentes cores de setas, podemos ainda definir um _mixin_ exclusivo para nos auxiliar nesta tarefa, confere:

<pre class="lang-sass">@mixin arrow-top-color($color) {
  &:before {
    border-bottom-color: $color;
  }
}

.profile {
  width: 100px;
  background: blue; 
  @extend %arrow-top;
  @include arrow-top-color(blue);
}</pre>

Os _helpers_ são bastante úteis. Saber quando usar _mixins_ ou _placeholders_ é simples: os _mixins_ são para quando é preciso passar algum parâmetro, como, em nosso caso, a cor.

Um outro exemplo bem interessante é o do site do [Front in Poa][10]. Para ele, [criei uma série de _helpers_][11] para representar as linhas que são renderizadas através de gradientes radiais.

## Concluindo

Espero que estes exemplos o tenham convencido a considerar o uso de um pré-processador. E para você que já utiliza, espero que os conceitos abram um pouco mais sua mente e o façam escrever folhas de estilo cada vez melhores.

A respeito da escolha do pré-processador, saiba que os mais populares são [Sass][12], [Stylus][13] e [Less][14]. Não se esqueça de sempre levar em consideração a preferência e habilidades da sua equipe para auxiliar na tarefa de escolha. Vou apenas bancar o intrometido e deixar uma dica: o Less não possui suporte a _placeholders_.

 [1]: http://www.w3.org/TR/css3-color/#svg-color
 [2]: http://tableless.com.br/como-usar-gradient-no-css-de-forma-consciente
 [3]: //www.colorzilla.com/gradient-editor
 [4]: http://compass-style.org
 [5]: http://visionmedia.github.io/nib
 [6]: http://bourbon.io
 [7]: http://compass-style.org/reference/compass/css3/images
 [8]: http://bem.info/method
 [9]: //josh.github.io/css-explain
 [10]: http://frontinpoa.com.br
 [11]: https://gist.github.com/jcemer/7130218
 [12]: http://sass-lang.com
 [13]: http://learnboost.github.io/stylus/
 [14]: http://lesscss.org/