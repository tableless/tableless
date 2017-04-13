---
title: Google Web Starter Kit
author: Dani Guerrato
type: post
date: 2014-09-01
excerpt: Conheça o boilerplate focado em design responsivo e performance criado pela equipe da Google.
url: /google-web-starter-kit/
categories:
  - Artigos
tags:
  - boilerplate
  - guia de estilos
  - web starter kit

---
Organizar pastas, incluir suas bibliotecas favoritas de JavaScript, ressetar o CSS, escrever as primeiras linhas de HTML&#8230; Estas tarefas se repetem a cada projeto de desenvolvimento front-end. Ter uma base sólida e organizada como ponto de partida pode poupar muito tempo precioso de trabalho&#8230;

Acredito que cada um tem o seu próprio kit inicial a sua maneira. A galera mais old school mantém uma pastinha na área de trabalho e copia e cola os itens a cada utilização, os mais moderninhos tem repositórios super completos com todo tipo de recurso. Seja qual for o seu estilo de organização, sempre bate uma curiosidade para ver (e aprender com) o setup de outros profissionais. Iniciativas para criar projetos colaborativos nesta linha não são exatamente inéditas. O [HTML5 Boilerplate][1], por exemplo, está aí para provar. E faz um bom trabalho em ser um ponto de partida quase minimalista para projetos web. Temos lá um HTML base bacaninha, o [Normalize][2], snippets úteis e até mesmo alguns recursos de imagens pré-prontos como favicons e touch icons.

Mas e se a gente for um passo além? E incluir alguns truques extras na manga como automatizadores, guias de estilos, sincronização multi-dispositivo e otimização de performance? Foi isto que a galera do [Web Fundamentals][3] fez ao criar o [Google Web Starter Kit][4]. Vamos explorar com ele funciona!

[<img src="http://tableless.com.br/uploads/2014/08/web-starter-kit.jpg" alt="web-starter-kit" width="960" height="540" class="aligncenter size-full wp-image-44066" srcset="uploads/2014/08/web-starter-kit.jpg 960w, uploads/2014/08/web-starter-kit-247x139.jpg 247w, uploads/2014/08/web-starter-kit-400x225.jpg 400w" sizes="(max-width: 960px) 100vw, 960px" />][5]

### O que ele NÃO é

Antes de iniciarmos é importante ressaltar que o Web Starter Kit não é um Framework. A ideia não é construir uma biblioteca de elementos pré-prontos como é o caso do Bootstrap e do Foundation. O Web Starter Kit é um chute inicial, uma base para que você possa criar e editar os seus próprios componentes, sem ficar preso em padrões engessados de layout.

### Um pequeno aviso

Até a data de publicação deste artigo o Web Starter Kit ainda estava em fase Beta. Ou seja, muita coisa pode mudar até a versão final. (Mas quem quer esperar até lá, não é mesmo?) De qualquer forma, para fins de comparação, este artigo se baseia na versão 0.4.0 do kit.

## Inícios

O primeiro passo, obviamente, é baixar os arquivos. Você pode fazer isto através do [site oficial][4] clicando no botão gigante &#8220;Download Kit&#8221; ou clonar o [repositório no GitHub][6]. A partir daí temos duas opções. Você pode ficar apenas com o boilerplate e ser feliz com ele. Neste caso delete os arquivos package.json, gulpfile.js, .jshintrc e .travis.yml e, bem, pare de ler este artigo pois não tenho nenhuma outra dica pra você. Mas, se você quiser conhecer as ferramentas extras continue comigo que vou explicar melhor os paranauês.

## Ferramentas

### Boilerplate responsivo

Um arquivo HTML e um CSS inicial para servir de base para os seus projetos. O HTML inclui diversas meta-tags e alguns snippets úteis pré-prontos como Google Analytics, por exemplo. Esta parte é bem parecida com o HTML5 Boilerplate. É tudo o que os nossos amigos que pararam de ler no parágrafo de cima ganharam.

<img src="http://tableless.com.br/uploads/2014/08/web-starter-kit-home.jpg" alt="web-starter-kit-home" width="960" height="540" class="aligncenter size-full wp-image-44063" srcset="uploads/2014/08/web-starter-kit-home.jpg 960w, uploads/2014/08/web-starter-kit-home-247x139.jpg 247w, uploads/2014/08/web-starter-kit-home-400x225.jpg 400w" sizes="(max-width: 960px) 100vw, 960px" />

### Guia de Estilos

Um Guia de Estilos bacana para documentar os componentes do seu sistema. É bem organizado com tipografia, cores, botões, grids,  tabelas, etc. (Não sabe pra que cazzo serve um Guia de Estilos? Eu escrevi um [artigo inteirinho][7] sobre este tema e fiz até uma [Palestra Online][8] a respeito. Vai lá ler que eu te espero aqui).

### Reload ao vivo do browser

Chega de apertar F5 que nem um louco, amigo! Edite o documento e assista seu browser recarregar em tempo real. Outra maravilha da humanidade.

### Sincronização multi-dispositivo

Coloque todos os seus dispositivos em cima da mesa e certifique que todos estão na mesma rede local, acesse um IP e observe maravilhado os navegadores sincronizando simultaneamente cliques, scrolls, formulários, reload, etc. Uma coisa linda. Isto é extremamente útil para assustar os colegas de outros departamentos falando &#8220;o meu tablet está se mexendo sozinho&#8221;. E também para testar design responsivo como se não houvesse amanhã. Eu particularmente não entendo como eu vivia antes de conhecer isto. Ah, o live reload também funciona neste caso.

### Otimização de Performance

Minificação de JS, CSS, HTML e Imagens em uma ferramenta só. Você também pode consultar relátorios do Page Speed Insights.

### Suporte a SASS

Compilação sem esforço.

## Estrutura de Pastas

Ao baixar os arquivos você recebe isto aqui:

<img src="http://tableless.com.br/uploads/2014/08/web-starter-kit-pastas.jpg" alt="web-starter-kit-pastas" width="960" height="540" class="aligncenter size-full wp-image-44065" srcset="uploads/2014/08/web-starter-kit-pastas.jpg 960w, uploads/2014/08/web-starter-kit-pastas-247x139.jpg 247w, uploads/2014/08/web-starter-kit-pastas-400x225.jpg 400w" sizes="(max-width: 960px) 100vw, 960px" />

Pode parecer um pouco óbvio para quem não é mais iniciante, mas vamos dar uma olhada em arquivo por arquivo.

  * **readme** &#8211; uma versão resumida da documentação oficial;
  * **license** &#8211; informações sobre licença (Apache 2.0);
  * **package.json** &#8211; metadados e dependências do projeto;
  * **gulpfile.js** &#8211; arquivo de automatização;
  * **pasta app** &#8211; sua pasta de produção.

&nbsp;

Vamos dar uma olhadinha mais de perto na **pasta app**:

  * **apple-touch-icon-precomposed.png** e **favicon.ico** &#8211; ícones de favoritos;
  * **humans.txt** &#8211; informações sobre a equipe de produção do projeto (ou seja, VOCÊ);
  * **robots.txt** &#8211; configuração para robôs de busca;
  * **manifest.webapp** &#8211; metadados do projeto;
  * **pasta fonts** &#8211; arquivos de fontes a serem importadas via @font-face;
  * **pasta images** &#8211; arquivos de imagens;
  * **pasta scripts** &#8211; arquivos JavaScript;
  * **pasta styles** &#8211; arquivos de CSS e SCSS;
  * **pasta styleguide** &#8211; arquivos do Guia de Estilos;

&nbsp;

Nós também temos dois arquivos HTML. A ideia é que você escolha qual deles prefere utilizar (e delete o outro).

  * **basic.html** &#8211; HTML zero bala para você iniciar seu projeto;
  * **index.html** &#8211; HTML com um menu responsivo off-canvas pré-pronto.

&nbsp;

Na **pasta styles** temos o seguinte:

  * **h5bp.css** &#8211; o CSS base do HTML5 Boilerplate com algumas normatizações;
  * **main.css** &#8211; folha de estilos principal;
  * **pasta components** &#8211; os módulos de CSS propriamente ditos. Se quiser adicionar ou remover arquivos basta editar o arquivo components.scss

&nbsp;

Bem, agora que você já conhece cada uma das ferramentas e a estrutura de pastas vamos ao passo-a-passo para fazer tudo isto funcionar.

## Requisitos

Vamos precisar de [Node][9], [Ruby][10], [Sass][11] e [Gulp][12]. Se você já tiver estes componentes pode pular esta etapa. Se não vamos instalar juntos passo-a-passo.

### Um parágrafo de consolo para quem tem medo do terminal

Esta parte do artigo envolve um conhecimento obscuro: saber utilizar linhas de comando. A maior parte dos devs tiram de letra mas, tem gente que tem receio ou verdadeiro pavor daquela telinha preta do Terminal ou do Prompt de Comando (se você for usuário de Windows)! Mas é bem tranquilo. Prometo. Galera, eu sou designer, amo interfaces gráficas e consegui. Vai lá e pega um cafezinho, respira fundo e não entre em pânico.

#### Comandos básicos

##### cd

O primeiro comando que você precisa saber hoje é &#8220;cd&#8221;. Este comando abre o diretório que você determinar. Então basicamente você vai digitar cd e o caminho de pasta. No caso do OSX é só escrever cd e arrastar e soltar uma pasta que o terminal já preenche com o caminho completo.

##### -v ou &#8211;version

Serve para você descobrir a versão de um componente instalado. Por exemplo node -v retorna qual é a versão do Node.js. Se aparecer uma mensagem de erro é por que você provavelmente não tem este componente instalado.

##### sudo

Pode acontecer de você não ter permissão do sistema para realizar uma determinada ação no terminal. Mas você pode obter uma permissão temporária de super usuário (ou **s**uper **u**ser **do**… entendeu?). Ou seja, se um determinado comando não funcionar, tente repetir a mesma coisa digitando sudo antes.

### Instalando as ferramentas

#### 1. Node.js

Para quem não conhece, o Node é uma plataforma para desenvolver aplicações server-side escaláveis utilizando JavaScript. Você pode checar se ele existe na sua máquina digitando o seguinte comando no terminal ou cmd.

<pre>node -v</pre>

##### Se o terminal retornar &#8220;v0.10&#8221; ou superior

Ótimo! Siga para o passo 2.

##### Se o arquivo não for encontrado

Você vai precisar instalar. Visite o [nodeJS.org][13] e clique no botão gigante verde. É só baixar o instalador, clicar em próximo, próximo, próximo e ser feliz. Sem segredos até aqui.

#### 2. Ruby

Também vamos precisar de Ruby Gems para gerenciar pacotes. Se você utiliza Mac ele vem pré-instalado. De qualquer forma descubra se você possui / qual é a sua versão:

<pre>ruby -v</pre>

##### Se o terminal retornar &#8220;v1.8.8&#8221; ou superior

Ótimo! Siga para o passo 3.

##### Se o arquivo não for encontrado

Visite [www.ruby-lang.org/downloads][14] e siga as instruções. Opcionalmente você pode utilizar o [Ruby Installer][15]  se estiver no Windows.

#### 3. SASS

O SASS vai pré-processar o nosso CSS para utilizarmos diversas funções legais como variáveis, mixins, cálculos matemáticos, etc. Vá em frente e digite:

<pre>sass -v</pre>

##### Se o terminal retornar &#8220;v3.3&#8221; ou superior

Ótimo! Siga para o passo 4.

##### Se o arquivo não for encontrado

É possível instalar o SASS pelo próprio terminal. Basta digitar:

<pre>gem install sass</pre>

Se não funcionou é provável que você não tenha permissão de pastas necessárias. Neste caso você pode utilizar o comando sudo.

<pre>sudo gem install sass</pre>

Agora é só checar a versão e seguir para o próximo passo:

<pre>sass -v</pre>

Se você tiver qualquer dificuldade pode visitar também o [site oficial do SASS][16] e baixar um instalador.

#### 4. Gulp

O Gulp é um automatizador de tarefas. Verifique se ele já existe:

<pre>Gulp -v</pre>

##### Se o terminal retornar &#8220;v3.5&#8221; ou superior

Ótimo! Siga para o passo 5.

##### Se o arquivo não for encontrado

É possível instalar o Gulp pelo próprio terminal. Basta digitar:

<pre>npm install --global gulp</pre>

Se obter um erro tente novamente utilizando &#8220;sudo&#8221;.

<pre>sudo npm install --global gulp</pre>

#### 5. Dependências locais

Instale as dependências locais do Web Starter Kit da seguinte maneira:

<pre>cd web-starter-kit
npm install
</pre>

Prontinho. Agora você tem tudo o que precisa para começar a trabalhar!

## Comandos do Gulp

Agora é a parte divertida. Use estes comandos para realizar as tarefas de automação do Gulp.

### Rotina de Automatização

<pre>gulp</pre>

O comando gulp serve para executar a rotina prevista no arquivo gulpfile.js. Se esta é a primeira vez que você roda você vai notar a criação da pasta &#8220;Dist&#8221;. É aqui que vão ficar os arquivos finais do projeto, prontos para você subir onde quiser.

As outras tarefas da rotina são: verificação de erros no JavaScript, otimização de imagens, prefixação automática de CSS, compilação do SASS, minificação de HTML, CSS e JS, copia dos arquivos finais para a pasta Dist e reload do browser. Você pode retirar as ações que não quiser ou acrescentar novos comandos editando o arquivo gulpfile.js.

### Servidor local

<pre>gulp serve</pre>

Roda a rotina de automação do Gulp e gera um endereço de IP. Basta acessar este endereço através de navegadores de dispositivos que estão na sua rede local. Agora você pode testar o seu projeto sincronizadamente e todos os navegadores vão ser recarregados automaticamente a cada mudança nos arquivos.

(Se quiser parar o processo basta usar o atalho Control + C).

### Relatório de Velocidade

<pre>gulp pagespeed</pre>

Através deste comando você obtém um relatório completo, utilizando a API do [Google Pagespeed Insights][17].

<img src="http://tableless.com.br/uploads/2014/08/web-starter-kit-pagespeed.jpg" alt="web-starter-kit-pagespeed" width="960" height="540" class="aligncenter size-full wp-image-44064" srcset="uploads/2014/08/web-starter-kit-pagespeed.jpg 960w, uploads/2014/08/web-starter-kit-pagespeed-247x139.jpg 247w, uploads/2014/08/web-starter-kit-pagespeed-400x225.jpg 400w" sizes="(max-width: 960px) 100vw, 960px" />

### Outros comandos

Você pode ler uma [lista completa de comandos][18] disponível na documentação oficial.

## Veja tudo funcionando

Vamos apenas fazer uma pequena modificação nos arquivos para verificar se está tudo ok. Use o gulp serve no terminal dentro da pasta app.

<pre>cd web-starter-kit
gulp serve</pre>

Agora abra o arquivo index.html no seu editor favorito (eu sou fã do [Sublime][19], mas fique a vontade). Vamos trocar o este título aqui:

<pre class="lang-html">&lt;h1&gt;Hello.&lt;/h1&gt;
</pre>

Por algo mais brasuca.

<pre class="lang-html">&lt;h1&gt;Olá mundo!&lt;/h1&gt;
</pre>

Salve e assita a magia acontecer. Agora o meu trabalho termina e o seu começa. Boa diversão!

## Suporte

O Web Starter Kit foi criado para funcionar bem nos seguintes navegadores:

  * IE9, IE10, IE11, IE Mobile 10
  * FF 30, 31
  * Chrome 34, 35
  * Safari 7, 8
  * Opera 23, 24
  * iOS Safari 7, 8
  * Opera Coast
  * Android / Chrome 4.4, 4.4.3
  * BlackBerry 10

Isto não significa que o kit não funciona em browsers mais antigos. É só que eles não são exatamente o foco da ferramenta.

## Desconstrua!

A intenção deste artigo é demonstrar uma possibilidade de configuração inicial. Mas lembre-se que este tipo de kit deve ser usado como uma bussula, não como uma muleta! Copie o repositório, explore os códigos e comentários dos arquivos e aprenda com eles. Estude o que eles oferecem de bacana, delete o que não for. Acha grids fixos uma porcaria (e eu sou a primeira a levantar a mão neste caso)? Use um grid semântico. Não curte pré-processadores? Vá em frente e use CSS baunilha. Renomeie os assets como quiser. Ou jogue tudo fora e construa o seu do zero. O bacana de boilerplates é que (cof cof… diferentemente de frameworks… cof cof) eles não te prendem a um estilo específico de design ou códigos legados gigantes. Enfim, faça uma engenharia reversa e construa o seu próprio kit de ferramentas. E não se esqueça de compartilhar as ideias boas com a gente depois… Até a próxima!

 [1]: http://html5boilerplate.com/ "HTML5 Boilerplate"
 [2]: http://necolas.github.io/normalize.css/ "Normalize"
 [3]: https://developers.google.com/web/fundamentals/ "Web Fundamentals"
 [4]: https://developers.google.com/web/starter-kit/ "Web Starter Kit"
 [5]: https://developers.google.com/web/starter-kit/
 [6]: https://github.com/google/web-starter-kit "Web Starter Kit - GitHub"
 [7]: http://tableless.com.br/guia-de-estilos/ "Guia de Estilos"
 [8]: https://www.eventials.com/locaweb/guias-de-estilo-para-a-interface-do-usuario/ "Guia de Estilos - Palestra"
 [9]: http://nodejs.org/ "nodejs"
 [10]: https://www.ruby-lang.org "Ruby"
 [11]: http://sass-lang.com/ "Sass"
 [12]: http://gulpjs.com/ "Gulp"
 [13]: http://nodejs.org/ "nodejs.org"
 [14]: https://www.ruby-lang.org/en/downloads/ "Ruby Lang"
 [15]: http://www.rubyinstaller.org/downloads "Ruby Installer"
 [16]: http://sass-lang.com/install%20 "SASS - Install"
 [17]: https://developers.google.com/speed/pagespeed/insights "Page Speed Insights"
 [18]: https://developers.google.com/web/fundamentals/tools/build/build_site#summary-of-web-starter-kit-tools "Summary of web starter kit tools"
 [19]: http://www.sublimetext.com/ "Sublime Text"