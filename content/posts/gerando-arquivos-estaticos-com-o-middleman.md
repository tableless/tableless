---
title: Gerando arquivos estáticos com o Middleman
author: Diego Eis
type: post
date: 2014-08-04
excerpt: Criar projetos usando geradores de arquivos estáticos podem ser uma saída estratégica para evitar ambientes complexos, o Middleman pode te ajudar a desenvolver projetos simples e rápidos.
url: /gerando-arquivos-estaticos-com-o-middleman/
dsq_thread_id: 2899659611
categories:
  - Código
  - middleman
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - html
  - jekyll
  - middleman

---

O Middleman, assim como o [Jekyll][1], serve sites estáticos, sem banco de dados, baseados em puro código HTML e informação. Existem uma [série de sistemas][2] desse tipo e é uma das minhas armas em muitos projetos.

## Instalando

Supondo que você tem o Ruby e RubyGems na sua máquina, basta instalar a GEM do Middleman:

<pre class="lang-terminal">$ gem install middleman
</pre>

Depois de instalado, os comandos básicos são:

  * **middleman init** para iniciar um projeto.
  * **middleman server** para rodar essa aplicação/projeto.
  * **middleman build** para compilar os assets e preparar uma pasta com os arquivos estáticos.

## Iniciando um site

Abra novamente o terminal e digite o seguinte comando:

<pre class="lang-terminal">middleman init <strong>nome_do_projeto</strong>
</pre>

Se a pasta não existir, ele vai criá-la. Lá dentro ele vai colocar toda a estrutura de arquivos para funcionar seu projeto. Desapegue da estrutura de arquivos que você ama e adora. A estrutura que o Middleman monta é bastante simples e bem enxuta. Basicamente é formada da pasta `source` e do arquivo `config.rb`.

O arquivo `config.rb` é onde você vai define as configurações do Middleman e informações de como habilitar algumas features que podem ser úteis aos desenvolver seu projeto e principalmente de como habilitar o módulo de blog (isso mesmo, blog).

Na pasta `source` é onde tem todo o seu projeto. A estrutura inicial dessa pasta é a seguinte:

<pre class="lang-shell">images
index.html.erb
javascripts
layouts
stylesheets
</pre>

Logo no começo eu já mudo algumas configurações para modificar um pouco essa estrutura, deixando tudo assim:

<pre class="lang-shell">assets/
  images
  javascripts
  stylesheets
index.html.erb
layouts
</pre>

Depois que movi as pastas do jeito que eu quis, mudo lá no `config.rb` três variáveis:

<pre class="lang-ruby">set :css_dir, 'stylesheets'
set :js_dir, 'javascripts'
set :images_dir, 'images'
</pre>

Fica isso aqui:

<pre class="lang-ruby">set :css_dir, 'assets/stylesheets'
set :js_dir, 'assets/javascripts'
set :images_dir, 'assets/images'
</pre>

E basicamente essa é a única mudança que faço para deixar meu ambiente funcionando!

## Rodando o projeto

Agora que seu ambiente está configurado, vamos rodar. Estando dentro da pasta do projeto, rode:

<pre class="lang-terminal">middleman server
</pre>

Isso vai subir o projeto na porta **http://localhost:4567/**.

Se você já tiver algum projeto nessa porta, você pode mudar colocando a flag **&#8211;p** no comando escolhendo a porta:

<pre class="lang-terminal">middleman server --p 3001
</pre>

Depois que seu projeto está rodando, você pode escrever CSS, HTML e o que quiser.

## Templates e Partials

Acho que você percebeu ali em cima que além dos assets, existe uma pasta chamada **layouts**. Essa pasta é a responsável por guardar os templates que você vai usar nas páginas. Você tem um template para páginas de texto, para galerias e etc. Esses templates diferentes, vão ali e você vai indicar indicar em cada arquivo, qual template de layout ele vai utilizar.

Esse aqui é o código que **layout.erb** vem como padrão:

<pre class="lang-html">&lt;!doctype html>
&lt;html&gt;
  &lt;head&gt;
    &lt;meta charset="utf-8"&gt;

    &lt;!-- Always force latest IE rendering engine or request Chrome Frame --&gt;
    &lt;meta content="IE=edge,chrome=1" http-equiv="X-UA-Compatible"&gt;

    &lt;!-- Use title if it's in the page YAML frontmatter --&gt;
    &lt;title&gt;&lt;%= current_page.data.title || "The Middleman" %&gt;&lt;/title&gt;

    &lt;%= stylesheet_link_tag "normalize", "all" %&gt;
    &lt;%= javascript_include_tag  "all" %&gt;
  &lt;/head&gt;

  &lt;body class="&lt;%= page_classes %&gt;"&gt;
    &lt;%= yield %&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>

Esse seria o template padrão usado para as páginas. Como vou ter vários templates, que usarão as mesmas informações da tag HEAD e do FOOTER, eu prefiro separar essas informações em partials. Ou se você escreve PHP, em includes. Funcionam diferente, mas a ideia geral é a mesma: reutilizar blocos de código em arquivos do projeto.

Para isso, geralmente crio também uma pasta **partials** para guardar esses pedaços que serão reutilizados várias vezes no projeto. Talvez esta é a parte mais legal de usar geradores como o Middleman e o Jekyll. Como tudo é arquivo estático, facilitando minha vida, eu ainda consigo ter a facilidade de separar meus arquivos da maneira que eu quiser.

A estrutura de código que mostrei lá em cima, pode ficar assim:

<pre class="lang-ruby">&lt;%= partial 'partials/header'%&gt;
&lt;%= yield %&gt;
&lt;%= partial 'partials/footer'%&gt;
</pre>

Mas se não tem Banco de Dados, como que você define informações de título, descrição da página ou qualquer outra coisa? Simples: todos os arquivos de conteúdo tem um cabeçalho em formato YAML, no início no arquivo que leva essas informações.

### Um pouco sobre YAML

O formato **YAML** é conhecido pela facilidade de leitura. Ele foi criado para estruturarmos informação de maneira que seja fácil de entender e escrever. Ou seja, ele é um formato simples para escrevermos manualmente, mas que também possamos manipular via programação.

Qualquer arquivo que contém um bloco YAML – que geralmente é chamado de **front-matter** – será processado como um arquivo especial. O front-matter precisa ser a primeira coisa do arquivo e deve estar num formato válido de YAML. Toda página do seu site, tanto no Jekyll quanto no Middleman, precisam começar com uma estrutura assim:

<pre class="lang-yaml">---
title: Home
layout: default
---
</pre>

Simples, ahn? O bloco é demarcado pelos três traços no começo e no fim. TEM que ser três traços. Nem mais, nem menos. O código YAML são as duas variáveis **layout** e **title**.

Ambos os sistemas usam essa notação para organizar seus arquivos e informações. Você pode definir variáveis em cada um dos arquivos para fazer condições nas páginas. Se em uma página, por exemplo, eu quero que a sidebar apareça, a notação YAML dela vai se algo assim:

<pre class="lang-yaml">---
title: Contato
layout: interna
sidebar: true
---
</pre>

A variável **sidebar** com o valor **false** foi criada por mim. No template, usarei algo parecido com isso, no Middleman:

<pre class="lang-ruby">&lt;% if current_page.data.sidebar? %&gt;
  &lt;%= partial 'partials/header'%&gt;
&lt;% end %&gt;
</pre>

Lindo e simples. Quando buildar o projeto. O sistema já vai compilar os arquivos da maneira correta, com o código sidebar, no lugar que você pediu.

## Fazendo o build do projeto

O comando **middleman build** vai compilar seu projeto em uma pasta **build**. Lá dentro terão os arquivos usados no projeto, praticamente na mesma estrutura que você deixou no projeto original, só que agora tudo estático em HTML.

Geralmente, nos projetos que me envolvo, onde o cliente precisa apenas de arquivos estáticos, eu envio essa pasta build. Facilita muito minha vida. Se eu preciso fazer o HTML/CSS de um projeto com milhares de páginas, eu posso simplesmente usar o Middleman ou qualquer outro gerador similar, para me ajudar a separar partials/includes dos pedaços comuns de código, como HEADER, FOOTER, SIDEBAR e etc&#8230; Depois é só buildar o projeto e pronto. Ele monta as partes automaticamente para mim.

Há uma série de outras dicas sobre o Middleman aqui, como fazer um blog por exemplo, mas deixo para próxima. Por enquanto, isso aqui já consegue te ajudar bastante.

Estou estudando [Ghost][3] ultimamente. Em um projeto de duas páginas, é muito prático usar um Middleman da vida, mas o cliente ainda quer ter a facilidade de criar páginas ou modificar o conteúdo. Certamente eu não vou instruí-lo para que ele faça isso editando arquivos no Sublime. Logo, uma interface administrativa faz bastante falta. O Ghost trabalha com arquivos estáticos e tem uma interface administrativa básica, para gerenciar o conteúdo. Tendo mais novidades, escrevo por aqui.

 [1]: http://tableless.com.br/jekyll-servindo-sites-estaticos/
 [2]: https://www.staticgen.com
 [3]: https://ghost.org/download/
