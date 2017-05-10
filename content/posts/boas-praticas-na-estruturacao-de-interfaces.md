---
title: Boas práticas na estruturação de interfaces.
author: Thaiana Poplade
type: post
date: 2011-01-24
excerpt: O planejamento estrutural de seu código html é também de grande importância para organização de tags e propriedades css, para o trabalho em equipe e para uma manutenção facilitada.
url: /boas-praticas-na-estruturacao-de-interfaces/
tweetbackscheck:
  - 1356439211
shorturls:
  - 'a:3:{s:9:"permalink";s:67:"http://tableless.com.br/boas-praticas-na-estruturacao-de-interfaces";s:7:"tinyurl";s:26:"http://tinyurl.com/3qzu4l7";s:4:"isgd";s:19:"http://is.gd/ZEaZ4P";}'
twittercomments:
  - 'a:20:{i:111112119088447489;s:7:"retweet";i:111089713993105409;s:7:"retweet";i:111082540995055617;s:7:"retweet";i:111073797037232128;s:7:"retweet";i:111073656448360448;s:7:"retweet";i:111072716769071105;s:7:"retweet";i:111071400218996736;s:7:"retweet";i:111071242471211008;s:7:"retweet";i:111071187353878528;s:7:"retweet";i:111071123382353920;s:7:"retweet";i:111071109834739713;s:7:"retweet";i:111070911091838976;s:7:"retweet";i:111070764370890752;s:7:"retweet";i:111070503707484161;s:7:"retweet";i:148810136826290176;s:7:"retweet";i:149147571988873216;s:7:"retweet";i:148823733514153985;s:7:"retweet";i:148823730938851328;s:7:"retweet";i:148810782115766272;s:7:"retweet";i:169575188172783617;s:7:"retweet";}'
tweetcount:
  - 61
dsq_thread_id: 503039968
categories:
  - Artigos
  - HTML
  - Técnicas e Práticas
tags:
  - 2011
  - aprenda
  - cotidiano
  - Na Prática
  - padroes web

---
Ao iniciar um novo projeto, precisamos estabelecer um planejamento de tempo de trabalho X modelo de trabalho. Em geral, não há uma regra estabelecida, pois muitos desenvolvedores Front-End acabam por utilizar suas próprias lógicas de estruturação de códigos levando em consideração qualidade em menor tempo.
  
Conforme vamos adquirido experiência na área, acabamos assimilando e adotando os métodos utilizados na empresa ou agência em que trabalhamos somados à troca de experiência com os outros profissionais. Ainda assim, existem boas práticas, percebidas por profissionais que já estão no mercado há algum tempo, que podem colaborar para que qualidade e velocidade sejam pontos primordiais no desenvolvimento de um website.

### Identificando os 3 principais elementos de uma interface

O primeiro passo é identificar os 3 principais elementos do projeto &#8211; topo, conteúdo e rodapé. Esses elementos são comuns à maioria das estruturas que temos na web, trazem as principais informações do website e tendem a repetir-se em todas as páginas internas com as mesmas características visuais estabelecidas na “home”.
  
Ao identificá-los &#8211; ainda no arquivos de layout &#8211; é importante já observar propriedades básicas desses elementos como: altura, largura e tipo de propriedade que será utilizada para o background desta interface, levando em consideração principalmente a versatilidade deste projeto à diferentes resolução de tela.
  
Identificadas essas informações, inicie a estruturação da interface pelo código html criando estes 3 elementos:

<table>
  <tr>
    <td>
      HTML 4
    </td>
    
    <td>
      HTML5
    </td>
  </tr>
  
  <tr>
    <td>
      <body><br /> <div id=&#8221;header&#8221;>conteúdo topo</div><br /> <div id=&#8221;content&#8221;>conteúdo corpo</div><br /> <div id=&#8221;footer&#8221;>conteúdo rodapé</div><br /> </body>
    </td>
    
    <td>
      <body><br /> <header>conteúdo topo</header><br /> <div id=&#8221;content&#8221;>conteúdo corpo</div><br /> <footer>conteúdo rodapé<footer><br /> </body>
    </td>
  </tr>
</table>

### Folhas de estilo externas

O uso de folhas de estilos externas para declaração de propriedades css é uma das práticas que incansavelmente vem sendo ressaltada e com objetivo: propriedades declaradas de forma “inline” dificultam a manutenção de website, deixam o código carregado de informações não relevantes para mecanismos de busca e para leitores de tela além de, devido este tipo de declaração ter maior relevância na renderização realizada pelos browsers, o que é declarado “inline” vai sobrescrever o que foi declarado nas folhas externas, fazendo com que você se obrigue a utilizar hacks, ou seja, um “conserto” atrás de outro.
  
Reforçado o recado continuamos, para estruturação inicial de uma interface, podemos criar uma folha de estilos com as propriedades básicas (diagramação de sustentação dos 3 principais elementos), reset nas pré-formatações de alguns elementos (<a href="http://tableless.com.br/evite-incompatibilidade-browsers" target="_blank">já comentado em outro artigo</a>) e declaração dos estilos dos elementos de repetição do projeto (elementos de topo, menus, breadcrumbs, etc). Esta folha de estilo, por exemplo, chamaremos de: estrutura.css.
  
Para as demais páginas, além da “home”, caso seu projeto seja um projeto de médio a grande porte (websites institucionais, e-commerces e portais) uma dica é o uso de, além da folha de estruturação, uma folha para cada página com suas respectivas propriedades. Por exemplo: home.css, noticias.css, empresa.css, etc.

### Visualize a interface em blocos

Após estabelecer os principais elementos e determinar as folhas de estilos externas que serão criadas, as primeiras declarações css serão feitas a fim de criar uma estrutura de sustentação do website e com a estrutura principal pronta, podemos iniciar a inserção das demais informações que estão atreladas à estes elementos, por exemplo, no elemento topo podemos ter um menu, mas só iniciaremos sua codificação após diagramar o topo do website e verificá-lo em todos os browsers possíveis. Esta prática facilita a visualização da interface em blocos e a hierarquia que pode ser criada entre eles; hierarquia esta que pode ser traduzida nas folhas de estilo que permitem propriedades herdadas entre classes e ID’s, traduzindo esta prática em velocidade na determinação das características visuais do projeto.

### Outras pessoas podem fazer a manutenção de seu código? 

Iniciada a codificação da interface, esta última prática servirá principalmente para os casos de trabalho em equipe. Se sua resposta foi “sim” para a pergunta acima, reforçamos o uso de comentários tanto nas estruturas html quanto nas estruturas css, separação de imagens por pastas, folhas de estilos diferenciadas e etc. Se sua resposta foi “não”, ainda assim reforçamos o uso das possibilidades citadas acima, em prol das boas práticas entre profissionais Front-End.

Portanto, comente seus código, se organize para estruturar informações e crie métodos, pois você com certeza perceberá, mais velocidade, facilidade de manutenção e mostrará a diferença entre profissionais Front-End e o “amigo do sobrinho que faz sites”.