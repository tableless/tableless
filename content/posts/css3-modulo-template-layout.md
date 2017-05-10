---
title: CSS3 – Módulo Template Layout
author: Diego Eis
type: post
date: 2011-05-30
excerpt: Entenda como você não fará mais estruturas com a propriedade float.
url: /css3-modulo-template-layout/
tweetbackscheck:
  - 1356451976
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/css3-modulo-template-layout";s:7:"tinyurl";s:26:"http://tinyurl.com/3h77pa8";s:4:"isgd";s:19:"http://is.gd/WhBZNx";}'
twittercomments:
  - 'a:50:{i:101965952924651521;s:6:"138126";i:104305359203737600;s:7:"retweet";i:104199267819847681;s:7:"retweet";i:104197827294531584;s:7:"retweet";i:104196826252574720;s:7:"retweet";i:104194430898159617;s:7:"retweet";i:103128176347197440;s:7:"retweet";i:121650285797060608;s:7:"retweet";i:121647631352074241;s:7:"retweet";i:121646569811488768;s:7:"retweet";i:121738176011317250;s:7:"retweet";i:121731928729718785;s:7:"retweet";i:121723395955105792;s:7:"retweet";i:121708940668059648;s:7:"retweet";i:121678703204909056;s:7:"retweet";i:121659062210412544;s:7:"retweet";i:121654907915862016;s:7:"retweet";i:121650905715179521;s:7:"retweet";i:121650229782126593;s:7:"retweet";i:121649727262568448;s:7:"retweet";i:121649651437940737;s:7:"retweet";i:121649214471147521;s:7:"retweet";i:121648981603385345;s:7:"retweet";i:121648321923256320;s:7:"retweet";i:121647978120355840;s:7:"retweet";i:121647583516049408;s:7:"retweet";i:121647341311758336;s:7:"retweet";i:121647287591116800;s:7:"retweet";i:121647126735355904;s:7:"retweet";i:121647102911713280;s:7:"retweet";i:121646736467951616;s:7:"retweet";i:121646454149365760;s:7:"retweet";i:128633419264573441;s:7:"retweet";i:171940669080862720;s:7:"retweet";i:171277281052995584;s:7:"retweet";i:170547330716680192;s:7:"retweet";i:170546038829096960;s:7:"retweet";i:170545481989099520;s:7:"retweet";i:170543793475555329;s:7:"retweet";i:170543279501361155;s:7:"retweet";i:170543144302149634;s:7:"retweet";i:213080083529867264;s:7:"retweet";i:213080044401201152;s:7:"retweet";i:213036677336281088;s:7:"retweet";i:212969701691760640;s:7:"retweet";i:212960052095623169;s:7:"retweet";i:212960022748078081;s:7:"retweet";i:212959173355380737;s:7:"retweet";i:212958385417625600;s:7:"retweet";i:212957299482968065;s:7:"retweet";}'
tweetcount:
  - 241
dsq_thread_id: 503040297
categories:
  - Acessibilidade
  - CSS
  - CSS3
  - HTML
  - HTML5
  - Mercado e Comportamento
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2011
  - CSS3
  - desenvolvimento web
  - Na Prática
  - tecnicascss
  - web standards

---
Talvez você me chame de louco, mas para mim a parte mais fácil de desenvolver um site com CSS é o planejamento e diagramação do layout. Coincidentemente é a parte que mais os desenvolvedores tem problemas crossbrowser ou por falta de recursos mais avançados. Mas se você parar para pensar, apenas uma propriedade cuida dessa parte, que é a propriedade float. De longe, para mim, o float é a propriedade mais importante que há no CSS. Se o IE não soubesse o que é float, até hoje nós não estaríamos fazendo sites com CSS. O float cuida de toda a diagramação do site, desde os elementos que definirão as áreas mestres do site até os pequenos detalhes de imagens e ícones. 

A propriedade float é muito simples de se entender. O problema não é o funcionamento, mas os efeitos que a propriedade float causa nos elementos próximos. Se você pede para duas colunas ficarem flutuando à esquerda e outra coluna à direita, o rodapé sobe. Ou se você coloca um elemento envolvendo outros elementos com float, esse elemento perde a altura. Estes são problemas corriqueiros que já tem soluções inteligentes e que não apresentam chateações mais graves.

Infelizmente o float não é o ideal para a diagramação e organização dos elementos do layout. Ele resolve muitos problemas, mas deixa a desejar em diversos sentidos. O float está completamente ligado a ordem dos elementos no HTML. Existem técnicas que você consegue fazer quase que qualquer oganização visual sem encostar no código HTML. Mas há outras necessidades que invariavelmente você precisará modificar a ordem dos elementos no meio do HTML para que a diagramação do site saia conforme o esperado. Essa organização do HTML pode alterar desde programação server-side e até resultados de SEO e acessibilidade. Por isso é interessante que o HTML fique organizado de forma que ele supre as necessidades dessas bases. Sua organização visual deve ser independente desta organização.

Tendo em vista estes e outros problemas o W3C criou um novo módulo. Na verdade ele não é o único, e nem pode ser para que tenhamos diversas formas de trabalhar. O módulo em questão é chamado de Template Layout. Esse módulo consiste em uma forma de criarmos e organizarmos os elementos e informações do layout de forma menos espartana e mais flexível.

Podemos dividir a construção do layout em duas grandes partes: 1) Definição dos elementos mestres e grid a ser seguido. 2) Formatação de font, cores, background, bordas etc.

As propriedades nesta especificação trabalham associando uma política de layout de um elemento. Essa política é chamada de template-based positioning (não tem nada a ver com a propriedade position, pelo contrário é uma alternativa) que dá ao elemento uma grid invisível para alinhar seus elementos descendentes.
  
Porque o layout deve se adaptar em diferentes janelas e tamanhos de papéis, as colunas e linhas do grid deve ser fixas ou flexiveis dependendo do tamanho.

O W3C mostra alguns casos comuns:

  * Páginas complexas com múltiplas barras de navegação em áreas com posições fixas como publicidade, submenus e etc.
  * Formulários complexos, onde o alinhamento de labels e campos pode
  
    m ser facilmente definidos com as propriedades deste módulo com a ajuda das propriedades de margin, padding e tables.
  * GUIs, onde botões, toolbars, labels,
  
    ícones etc, tem alinhamentos complexos e precisam estar sempre alinhados caso o tamanho ou a resolução da tela mudam.
  * Medias que são paginadas, como medias de impressão onde cada página são divididos em áreas fixas para conteúdos de gêneros diferentes.

Template-based positioning são uma alternativa para a propriedade position com o valor absolute. Antigamente lembro-me que quase todos os desenvolvedores tentavam organizar e diagramar layouts utilizando position. Não que seja errado, mas definitivamente não é a melhor forma. Costumo dizer em meus cursos e palestras que position é para detalhes. Nada muito grande, mas para pequenos detalhes. Usamos position para posicionarmos elementos que não tem relação direta com sua posição no código HTML. Ou seja, não importa onde o elemento esteja, o position:absolute; irá posicionar o elemento nas coordenadas que você quiser.

### Sintaxe e funcionamento

O módulo Template Layout basicamente define slots de layout para que você encaixe e posicione seus elementos. O mapeamento dos slots é feito com duas propriedades que já conhecemos que este módulo adiciona mais alguns valores e funcionalidades, são as propriedades position e display. 

A propriedade display define como será o Grid, ou seja, quantos espaços úteis terá o layout.
  
A propriedade position irá posicionar seus elementos nestes slots. 

Veja o código HTML abaixo:

[cc lang=&#8221;html&#8221;]

<div class="geral">
  <nav class="menu">&#8230;</nav> <aside class="menulateral">&#8230;</aside> <aside class="publicidade">&#8230;</aside> <article class="post">&#8230;</article> <footer>&#8230;</footer>
</div>

[/cc]

Agora iremos definir a posição destes elementos. O código CSS seria assim:

[cc lang=&#8221;css&#8221;]

.geral {
     
display: &#8220;aaa&#8221;
              
&#8220;bcd&#8221;
              
&#8220;eee&#8221;;
  
}

nav.menu {position:a;}
  
aside.menulateral {position:b;}
  
aside.publicidade {position:d;}
  
article.post {position:c;}
  
footer {position:e;}
  
[/cc]

### O funcionamento da propriedade display

A propriedade display define a organização dos slots. Um slot é o local onde os elementos serão colocados.
  
Aqui o elemento display trabalha como um table, onde seu conteúdo será colocando em colunas e linhas. A única diferença é que o número de linhas e colunas não dependem do conteúdo. A outra principal diferença é que a ordem dos descendentes no código não importa. Ou seja, não importa a estrutura dos elementos no HTML, você pode colocá-los em qualquer lugar do layout.

Cada letra diferente é um slot de conteúdo diferente. O @ define um sinal para um slot padrão. E o &#8220;.&#8221; (ponto) define um espaço em branco.

Quando repetimos as letras como no exemplo anterior, tanto na horizontal quanto na vertical, é formado um slot único que se expande para o tamanho da quantidade de slots. Lembra do colspan ou rowspan utilizados na tabela? Pois é, funciona igualzinho.

Não é possível fazer um slot que não seja retangular ou vários slots com a mesma letra. Um template sem letra nenhuma também não é possível. Um template com mais de um @ também é proibido. Se houverem esses erros a declaração é ignorada pelo browser.

Pra definir a altura da linha (row-height) podemos utilizar o valor padrão &#8220;auto&#8221;, que define altura que a altura da linha é feito de acordo com a quantidade de conteúdo no slot. Você pode definir um valor fixo para a altura. Não é possível definir um valor negativo. Quando definimos um * (asterísco) para a altura, isso quer dizer que todas as alturas de linha serão iguais.

A largura da coluna (col-width) é definida com valores fixos, como o row-height. Podemos definir também o valor de * que funciona exatamente igual ao altura de linha, mas aplicados a largura da coluna. Há dois valores chamados max-content e min-content que fazem com que a largura seja determinada de acordo com o conteúdo. Outro valor é o minmax(p,q) que funciona assim: a largura das colunas são fixadas para ser maiores ou iguais a p e menores ou iguais a q. Pode haver um espaço branco (white space) em volta de p e q. Se q > p, então q é ignorado e o minmax(p,q) é tratado como minmax(p,p). O valor fit-content é o equivalente a minmax(min-content, max-content).

#### Definindo a largura e altura dos slots

Para definir a altura dos slots, utilizamos uma sintaxe diretamente na propriedade display. Veja abaixo um exemplo de como podemos fazer isso:

[cc lang=&#8221;css&#8221;]
  
.geral {
    
display: &#8220;a a a&#8221; /150px
             
&#8220;b c d&#8221;
             
&#8220;e e e&#8221; / 150px
             
100px 400px 100px;
  
}
  
[/cc]

Formatando de uma maneira que você enteda, fica assim:

[cc lang=&#8221;css&#8221;]
  
.geral {
    
display: &#8220;a a a&#8221; /150px
             
&#8220;b c d&#8221;
             
&#8220;e e e&#8221; /150px
             
100px 400px 100px;
  
}
  
[/cc]

Ou seja, a primeira coluna do grid terá 100px de largura, a segunda 400px e a terceira 100px.
  
As medidas que coloquei ao lado, iniciando com uma / (barra) definem a altura das linhas. Logo a primeira linha terá 150px e a terceira linha também. A linha do meio, como não tem altura definida terá a altura de acordo com a quantidade de conteúdo.

O espaço entre as colunas são definidos com &#8220;.&#8221; (pontos). Veja o exemplo abaixo:

[cc lang=&#8221;css&#8221;]
  
.geral {
    
display: &#8220;a a a&#8221; /150px
             
&#8220;. . .&#8221; /50px
             
&#8220;b c d&#8221;
             
&#8220;. . .&#8221; /50px
             
&#8220;e e e&#8221; /150px
             
100px 400px 100px;
  
}
  
[/cc]

No exemplo acima fiz duas colunas no código compostos por pontos em vez de fazer com letras. Isso quer dizer que entre as colunas do grid haverá um espaço em branco de 50px de altura. Veja a imagem abaixo para entender melhor o código:

<img src="http://tableless.com.br/uploads/2011/05/templatelayout1.gif" alt="" title="templatelayout1" width="364" height="336" class="alignnone size-full wp-image-3767" srcset="uploads/2011/05/templatelayout1.gif 364w, uploads/2011/05/templatelayout1-300x276.gif 300w" sizes="(max-width: 364px) 100vw, 364px" />

### O funcionamento da propriedade position

O valor da propriedade position especifica qual linha e coluna o elemento será colocado no template. Você escreve apenas uma letra por elemento. Vários elementos podem ser colocados em um mesmo slot. Logo estes elementos terão o mesmo valor de position.

Abaixo veja uma imagem que pegamos diretamente do exemplo do W3C. O layout é muito simples:
  
[<img src="http://tableless.com.br/uploads/2011/05/Untitled-300x89.png" alt="" title="Untitled" width="300" height="89" class="alignnone size-medium wp-image-3768" srcset="uploads/2011/05/Untitled-300x89.png 300w, uploads/2011/05/Untitled.png 914w" sizes="(max-width: 300px) 100vw, 300px" />][1]

Este layout é representado pelo código abaixo. Primeiro o HTML:

[cc lang=&#8221;html&#8221;]

<ul id="nav">
  <li>
    navigation
  </li>
</ul>

<div id="content">
  <div class="module news">
    <h3>
      Weather
    </h3>
    
    <p>
      There will be weather
    </p></p>
  </div>
  
  <div class="module sports">
    <h3>
      Football
    </h3>
    
    <p>
      People like football.
    </p></p>
  </div>
  
  <div class="module sports">
    <h3>
      Chess
    </h3>
    
    <p>
      There was a brawl at the chess tournament
    </p></p>
  </div>
  
  <div class="module personal">
    <h3>
      Your Horoscope
    </h3>
    
    <p>
      You&#8217;re going to die (eventually).
    </p></p>
  </div>
  
  <p id="foot">
    Copyright some folks
  </p>
</div>

[/cc]

Agora veja o CSS com toda a mágica:
  
[cc lang=&#8221;css&#8221;]
  
body {
       
display: &#8220;a b&#8221;
                
10em *;
  
}
  
#nav {
       
position: a;
  
}
  
#content {
       
position: b;
       
display: &#8220;c . d . e &#8221;
                
&#8220;. . . . . &#8221; /1em
                
&#8220;. . f . . &#8221;
                 
\* 1em \* 1em *;
  
}
  
.module.news {position: c;}
  
.module.sports {position: d;}
  
.module.personal {position: e;}
  
#foot {position: f;}
  
[/cc]

Lembre-se que não importa a posição dos elementos no código. E essa é a mágica. Podemos organizar o código HTML de acordo com nossas necessidades e levando em consideração SEO, Acessibilidade e processo de manutenção. O HTML fica totalmente intacto separado de qualquer formatação. Muito, mas muito interessante.

### Pseudo-elemento ::slot()

Você pode formatar um slot especifico simplesmente declarando-o no CSS. Suponha que você queira que um determinado slot tenha um fundo diferente, alinhamento e etc&#8230; Essa formatação será aplicada diretamente no slot e não no elemento que você colocou lá. Fica mais simples de se formatar porque você não atrela um estilo ao elemento e sim ao slot. Se você precisar posicionar aquele elemento em outro lugar, você consegue facilmente.

[cc lang=&#8221;css&#8221;]
  
body { display: &#8220;aaa&#8221;
                  
&#8220;bcd&#8221; }
  
body::slot(b) { background: #FF0 }
  
body::slot(c), body::slot(d) { vertical-align: bottom }
  
[/cc]

As propriedades aplicadas no pseudo elemento slot() seguem abaixo:

  * Todos as propriedades background. 
  * vertical-align
  * overflow
  * box-shadow, block-flow e direction ainda estão sendo estudados pelo W3C se elas entrarão ou não.

### Mas e o float?

É senhores&#8230; Eu acho que o float tem seus dias contados para a criação de estruturas de layouts. Quando utilizamos o float para estruturar o layout, nós dependemos profundamente da organização e posição dos elementos no código HTML. Não estou dizendo que o float ficará obsoleto, você ainda vai utilizá-lo e muito. Você vai pará-lo de utilizar para criar a base estrutural do site. Ou seja, a estrutura básica de divisão de conteúdo será feita pelo Template Layout, mas muitos dos detalhes internos e organização dos elementos contidos nos elementos mestres serão feitos com float. 

Com o Template Layout a estrutura do layout não depende da posição dos elementos do HTML no código, você poderá otimizar o código ao máximo para os leitores de tela e sistemas de busca, já que estes meios de acesso prezam pela estrutura do seu conteúdo. 

### Já funciona?

Sim, já funciona, mas não nativamente nos browser. Esta especificação ainda é um rascunho do W3C e por isso os browsers ainda não a suportam. Mesmo assim um desenvolvedor criou um script em Javascript que entende o CSS desta especificação e simula os resultados. Você [pode baixar o script aqui][2]. 

Veja um [exemplo funcionando aqui][3].

 [1]: http://tableless.com.br/uploads/2011/05/Untitled.png
 [2]: http://migre.me/4FL7D
 [3]: http://migre.me/4FLGU "exemplo do módulo template layout do CSS3"