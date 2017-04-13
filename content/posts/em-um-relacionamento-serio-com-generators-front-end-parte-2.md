---
title: Em um relacionamento sério com generators front-end – Parte 2
author: Pedro Polisenso
type: post
date: 2014-12-10
excerpt: Na parte 2 de nossa série, vamos falar de Yeoman, um generator que, na minha opinião, é bem completo e atende a grandes necessidades na criação de um projeto.
url: /em-um-relacionamento-serio-com-generators-front-end-parte-2/
categories:
  - AngularJS
  - Artigos
  - CSS3
  - HTML
  - HTML5
  - JavaScript
  - JQuery
  - LESS
  - Pré-processadores
  - SASS
  - Técnicas e Práticas
  - Tecnologia e Tendências

---
# O início

O objetivo desse post não é para fazer com que os desenvolvedores só usem esta ferramenta, e sim para apresentar opções de desenvolvimentos ágeis que podem ser úteis no seu dia a dia. É uma ferramenta a qual lhe oferece um stack completo de estrutura de projeto, basta você saber como usar e para que vai usar.

### O Yeoman

O Yeoman é considerado uma ferramenta web de andaimes para criação de webapp modernos, nele você consegue montar um esquema de trabalho facilitando seu desenvolvimento. Seu fluxo de trabalho é composto por 3 ferramentas melhorando sua produtividade e satisfação.

  * YO &#8211; Conjunto de geradores que nos permite prototipar
  * Gruntjs &#8211; Gerencia suas tarefas de forma automatizadas
  * Bower &#8211; Gerencia suas dependências aplicadas no projeto

PS: São ferramentas que por padrão já vem com o Yeoman, porém temos a opção de usar o Gulp para gerenciar nossas tarefas.

### Ta, me convence!

[<img class="alignnone size-full wp-image-46124" src="http://tableless.com.br/uploads/2014/12/convence.jpg" alt="convence" width="477" height="275" srcset="uploads/2014/12/convence.jpg 477w, uploads/2014/12/convence-241x139.jpg 241w, uploads/2014/12/convence-400x230.jpg 400w" sizes="(max-width: 477px) 100vw, 477px" />][1]

O Yeoman sendo uma ferramenta completa, pode proporcionar para você formas práticas e ágeis de desenvolvimento com menos tempo e com boa qualidade. Alguns criticam, outros elogiam, mas você só saberá o resultado se positivo ou negativo, quando usar esse brinquedinho.

Penso o seguinte: Uma ferramenta nova no marcado ou até mesmo uma antiga com novas versões e novas features, precisam ser exploradas para saber o que a mesma pode nos proporcionar. Por isso nunca se intimide com novas tecnologias e sim aproveite para ganhar conhecimentos.

### Dicas importantes antes de praticar

[<img class="alignnone size-full wp-image-46127" src="http://tableless.com.br/uploads/2014/12/dica.jpg" alt="dica" width="400" height="245" srcset="uploads/2014/12/dica.jpg 400w, uploads/2014/12/dica-226x139.jpg 226w" sizes="(max-width: 400px) 100vw, 400px" />][2]

Antes de mais nada já saiba que não ter medo do terminal é um diferencial. Sacanagem Hahaha. Mas é importante saber que a maioria das configurações e monitoramento serão via terminal, por isso é bom entender e interpretar cada linha de comando digitada.

Lembrando que para usar o Yeoman é preciso ter Nodejs instalado em sua máquina, por isso se você não tem essa plataforma, baixe [aqui][3], instale e parte para a próxima etapa. Após a instalação do nodejs o resto é mágica!

Uma observação válida a ser feita é o seguinte: Você que desenvolve com Mac OS ou Linux \*-\* por padrão já vem instalado o Ruby e para quem desenvolve em windows é preciso instalar os dois: Nodejs e Ruby. Você pode baixar o ruby bem [aqui][4].

### Vendo teorias na prática

[<img class="alignnone size-full wp-image-46128" src="http://tableless.com.br/uploads/2014/12/vendo-tv.jpg" alt="vendo-tv" width="381" height="315" srcset="uploads/2014/12/vendo-tv.jpg 381w, uploads/2014/12/vendo-tv-168x139.jpg 168w" sizes="(max-width: 381px) 100vw, 381px" />][5]

Conforme comentado acima, precisa ter nodejs instalado, por isso instale e após a instalação seguia os passos seguintes.

  1. Digite o código abaixo via linha de comando na raiz do seu projeto. O mesmo instala o Yo, Gruntjs e Bower de forma global, podendo usar também Gulp. <pre class="lang-html">npm install -g yo grunt-cli bower</pre>

  2. Instale o generator da aplicação, nesse caso o generator escolhido para uso é o &#8220;webapp&#8221;. <pre class="lang-html">npm install generator-webapp</pre>

  3. Inicie a aplicação com YO. <pre class="lang-html">yo webapp</pre>

O comando &#8220;generator-webapp&#8221; é o gerador de aplicações web padrão que será um projeto contendo HTML5 Boilerplate , jQuery , Modernizr e Bootstrap . Você vai ter uma opção durante as instruções interativas para não incluir muitos destes.

### Mas o que vem depois?

[<img class="alignnone  wp-image-46228" src="http://tableless.com.br/uploads/2014/12/01.jpg" alt="01" width="338" height="190" srcset="uploads/2014/12/01.jpg 400w, uploads/2014/12/01-247x139.jpg 247w" sizes="(max-width: 338px) 100vw, 338px" />][6]

Após o processo de instalação seguida passo a passo, a ferramenta já pode ser usada para criar suas aplicações. Você vai perceber que o YO já te retorna uma estrutura de pasta bem completa com tudo que você precisa e ainda alguns recursos a mais. Veja abaixo!

[<img class="alignnone  wp-image-46230" src="http://tableless.com.br/uploads/2014/12/estrutura-raiz.jpg" alt="estrutura raiz" width="193" height="269" srcset="uploads/2014/12/estrutura-raiz.jpg 233w, uploads/2014/12/estrutura-raiz-99x139.jpg 99w" sizes="(max-width: 193px) 100vw, 193px" />][7]

Analisando a estrutura, digo o seguinte:

  * A pasta **app** é onde vai rodar toda sua aplicação em modo de desenvolvimento. É lá que você cria seus arquivos HTML / CSS / JavaScript e entre outros. Mas essa pasta vamos ver com detalhes já já.
  * A pasta **bower_componnets** é criada pelo bower, onde você vai baixar e usar componentes como bootstrap, AngularJS, Backbone e entre outros e por padrão ele já traz o jQuery para você. Caso você não goste do nome “bower_componentes” você tem a opção de criar uma pasta como “libs” ou “componentes” e apontar seus componentes baixados para está nova pasta, só precisa criar um arquivo “.bowerrc” e lá você aponta para tal pasta. Exemplo: { app/libs ou app/componentes }
  * A pasta **node_modules** são os módulos instalados pelo nodejs, lá você vai ver alguns plugins do Gruntjs instalados por padrão, podendo ainda instalar outros plugins.
  * Os arquivos **Gruntfile** e **Bower.json** são de configurações de componentes, onde o Gruntfile armazena todas as tarefas automatizadas do gruntjs como: minificação, compilação e otimização. Já o bower.json é um arquivo simples que retorna dados importantes dos componentes gerenciados no bower e armazena os componentes usados e suas versões.
  * Os outros arquivos são de configuração da ferramenta, incluindo os arquivos ocultos.

### A tal pasta APP da minha aplicação

[<img class="alignnone  wp-image-46231" src="http://tableless.com.br/uploads/2014/12/02.jpg" alt="02" width="355" height="239" srcset="uploads/2014/12/02.jpg 425w, uploads/2014/12/02-206x139.jpg 206w, uploads/2014/12/02-400x269.jpg 400w" sizes="(max-width: 355px) 100vw, 355px" />][8]

Enfim chegamos a pasta de desenvolvimento, é aqui que começa toda a sua aplicação, você não precisa mexer em nenhuma outra pasta, tudo que você precisa mexer e criar vai ser dentro deste diretório, beleza? Veja como funciona a estrutura da pasta e logo após vamos ver funcionando e depois daremos o **build** \*-\*

[<img class="alignnone  wp-image-46232" src="http://tableless.com.br/uploads/2014/12/estrutura-app.jpg" alt="estrutura-app" width="134" height="277" srcset="uploads/2014/12/estrutura-app.jpg 154w, uploads/2014/12/estrutura-app-67x139.jpg 67w" sizes="(max-width: 134px) 100vw, 134px" />][9]

Acredito que detalhar essa estrutura não tem tanta necessidade, pois as pastas e arquivos já falam por si, não é mesmo? Mas qualquer dúvida pode deixar seu comentário que responderei com prazer.

Bom, você já instalou as ferramentas (Yo/Gruntjs/bower), já instalou o generator que será usado (generator-webapp) e executou o “yo” que retornou essa estrutura de pasta. Agora para ver como funciona é simples. Execute o comando abaixo, ele vai criar um server local para você ir debugando sua aplicação e vendo como ela está se comportanto no browser e o mais legal é que você não precisa dar F5, pois por padrão já vem instalado o “livereload” plugin do grunt que atualiza automaticamente sua aplicação no browser  =)

<pre class="lang-html">grunt server</pre>

Após isso você criar sua aplicação normalmente, usando como ponto de partida o arquivo index.html e os diretórios presentes.

### ****_E se eu quiser baixar outros componentes e plugins?_****

[<img class="alignnone  wp-image-46233" src="http://tableless.com.br/uploads/2014/12/03.jpg" alt="03" width="335" height="216" srcset="uploads/2014/12/03.jpg 400w, uploads/2014/12/03-215x139.jpg 215w" sizes="(max-width: 335px) 100vw, 335px" />][10]

É uma boa pergunta e simples de responder. Para baixar outro componente como por exemplo AngularJS vamos usar o Bower, nosso gerenciador de componentes. E para baixar um novo plugin como por exemplo JSHINT vamos usar o Gruntjs que gerencia nossas tarefas. Os comandos abaixo mostra como baixar componentes e plugins.

  * Baixando componentes

<pre class="lang-html">bower install [nome do componente]</pre>

  * Baixando plugins

<pre class="lang-html">npm install [nome do plugin] --save-dev</pre>

### E meu ambiente de produção?

[<img class="alignnone  wp-image-46234" src="http://tableless.com.br/uploads/2014/12/04.jpg" alt="04" width="363" height="252" srcset="uploads/2014/12/04.jpg 392w, uploads/2014/12/04-200x139.jpg 200w" sizes="(max-width: 363px) 100vw, 363px" />][11]

Chegamos ao nosso momento de build da aplicação. O yeoman compila todos os arquivos da pasta app e nos retorna uma pasta chamada “dist” é lá que encontram seus arquivos de produção prontos para serem usados e testados. Lembrando que qualquer alteração não poderá ser feita na pasta “dist” e sim em “app”.

Dando o build no projeto e gerando meu diretório de produção:

<pre class="lang-html">grunt build</pre>

### Visão geral

Hoje aprendemos realmente a usar o yeoman, desde seus conceitos até o modo de produção, é só seguir os passos e dicas. E por falar em dica, lá vai uma dica para melhorar mais ainda a sua transferência de arquivos para o ambiente de produção.

Ao dar o build ele gera o diretório “dist” contendo nele os arquivos de produção. Já que estamos automatizando tudo, evite o uso do FTP e sim faça deploy =) Abaixo segue algumas referências de um módulo do grunt que você pode acrescentar em sua aplicação e deixá-la mais interessante. Assim você miniminiza retrabalhos. Estou falando de [rsync][12].

Links de referência Yeoman que podem complementar o Post

&#8211; [Site oficial do yeoman][13]
  
&#8211; [Projeto yeoman no github para contribuição][14]
  
&#8211; [Outro Post de referência explicativo e conceitual][15]
  
&#8211; [Palestra sobre generators (yeoman)][16]

### 

### Considerações finais

Chegamos ao final desse capítulo tentando expor as qualidades que o Yeoman pode nos dar e sua forma de uso. No próximo capítulo teremos nosso amigo Beto Muniz ([@obetomuniz][17]) falando sobre Slush dentro da série. Não perca os próximos capítulos da série, onde no 4º capítulo finalizaremos com algumas dicas, apresentaremos projetos que foram criados a parir de um desses generators e mostrar como criar seu próprio generator. Valeu =]

 [1]: http://tableless.com.br/uploads/2014/12/convence.jpg
 [2]: http://tableless.com.br/uploads/2014/12/dica.jpg
 [3]: http://nodejs.org/download/
 [4]: https://www.ruby-lang.org/pt/downloads/
 [5]: http://tableless.com.br/uploads/2014/12/vendo-tv.jpg
 [6]: http://tableless.com.br/uploads/2014/12/01.jpg
 [7]: http://tableless.com.br/uploads/2014/12/estrutura-raiz.jpg
 [8]: http://tableless.com.br/uploads/2014/12/02.jpg
 [9]: http://tableless.com.br/uploads/2014/12/estrutura-app.jpg
 [10]: http://tableless.com.br/uploads/2014/12/03.jpg
 [11]: http://tableless.com.br/uploads/2014/12/04.jpg
 [12]: Ao%20dar o build ele gera o diretório “dist” contendo nele os arquivos de produção. Já que estamos automatizando tudo, jamais em toda sua vida use FTP e sim faça deploy =) Abaixo segue algumas referências de um módulo do grunt que você pode acrescentar em sua aplicação e deixá-la mais interessante. Assim você miniminiza retrabalhos. Estou falando de rsync
 [13]: http://yeoman.io/
 [14]: https://github.com/yeoman/yeoman
 [15]: http://blog.caelum.com.br/experimente-o-yeoman-em-seu-workflow-de-projetos-front-end/
 [16]: http://pt.slideshare.net/pedropolisenso/em-um-relacionamento-srio-com-generators-front-end
 [17]: https://twitter.com/obetomuniz