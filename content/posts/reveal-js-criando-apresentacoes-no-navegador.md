---
title: 'Reveal.js: criando apresentações no navegador'
author: Davi Ferreira
type: post
date: 2013-02-15
excerpt: Conheça a biblioteca reveal.js, uma ferramenta poderosa para a criação de apresentações de slides que não dependem de nenhum software especial, apenas um navegador moderno.
url: /reveal-js-criando-apresentacoes-no-navegador/
dsq_thread_id: 1084909678
categories:
  - JavaScript
tags:
  - CSS3
  - html5
  - JavaScript
  - revealjs

---
Apresentações não estão mais limitadas a softwares e plataformas específicas – hoje em dia é possível criar slides utilizando o navegador e tecnologias como HTML5, CSS3 e JavaScript. 

Uma das responsáveis por isto é a biblioteca JavaScript <a href="http://lab.hakim.se/reveal-js/" target="_blank">reveal.js</a>, criada por Hakim El Hattab, desenvolvedor mais conhecido por seus <a href="http://lab.hakim.se/" target="_blank">experimentos com animações CSS3</a>.

Neste artigo vamos criar uma apresentação básica e conhecer as opções disponíveis para personalizar nossos slides.

## Estrutura da apresentação

Vamos começar fazendo o download da última versão da biblioteca reveal.js disponível no GitHub: <a href="https://github.com/hakimel/reveal.js/downloads" target="_blank">https://github.com/hakimel/reveal.js/downloads</a>.

Feito isso, basta criar um arquivo index.html e copiar os arquivos da biblioteca para o diretório da apresentação. Nosso HTML inicial fica assim:

<pre class="lang-html">&lt;!doctype html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;meta charset="utf-8"&gt;
    &lt;title&gt;Apresentação Exemplo Tableless&lt;/title&gt;
    &lt;link rel="stylesheet" href="css/reveal.min.css"&gt;
    &lt;link rel="stylesheet" href="css/theme/default.css"&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;div class="reveal"&gt;
      &lt;div class="slides"&gt;&lt;/div&gt;
    &lt;/div&gt;
    &lt;script src="lib/js/head.min.js"&gt;&lt;/script&gt;
    &lt;script src="js/reveal.min.js"&gt;&lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;</pre>

A apresentação precisa seguir uma estrutura pré-definida: a biblioteca irá procurar um _div_ com a classe _reveal_ que contenha outro _div_ com a classe _slides_.

O elemento _div.slides_ receberá os slides de nossa apresentação. Os slides precisam ser elementos do tipo _section_. Vamos, então, adicionar nossos três slides à apresentação:

<pre class="lang-html">...
&lt;div class="reveal"&gt;
  &lt;div class="slides"&gt;
    &lt;section&gt;
      &lt;h1&gt;Apresentações no navegador&lt;/h1&gt;
      &lt;h3&gt;Exemplo de apresentação Tableless&lt;/h3&gt;
    &lt;/section&gt;
    &lt;section&gt;
      &lt;h1&gt;Sobre o autor&lt;/h1&gt;
      &lt;ul&gt;
        &lt;li&gt;15 anos de experiência&lt;/li&gt;
        &lt;li&gt;desenvolvedor na globo.com&lt;/li&gt;
      &lt;/ul&gt;
    &lt;/section&gt;
    &lt;section&gt;
      &lt;h1&gt;reveal.js&lt;/h1&gt;
        &lt;ul&gt;
          &lt;li&gt;desenvolvida por Hakim El Hattab&lt;/li&gt;
          &lt;li&gt;open source&lt;/li&gt;
        &lt;/ul&gt;
    &lt;/section&gt;
  &lt;/div&gt;
&lt;/div&gt;
...</pre>

O último passo é iniciar o objeto Reveal:

<pre class="lang-html">...
&lt;script src="lib/js/head.min.js"&gt;&lt;/script&gt;
&lt;script src="js/reveal.min.js"&gt;&lt;/script&gt;
&lt;script&gt;
  Reveal.initialize();
&lt;/script&gt;
...</pre>

Agora basta abrir o arquivo index.html no seu navegador favorito e conferir o resultado.

## Opções

O método _initialize_ pode receber como parâmetro um objeto com as opções da apresentação. É possível, por exemplo, esconder os controles de navegação, habilitar navegação via teclado, alterar o efeito de transição dos slides, entre outros.

Vamos agora mudar nossa inicialização, alterando algumas configurações:

<pre class="lang-javascript">Reveal.initialize({
  autoSlide: 6000,
  center: true,
  controls: false,
  mouseWheel: true,
  transition: 'concave'
});</pre>

Com as configurações acima nós habilitamos a troca automática de slides após 6 segundos, centralizamos o conteúdo dos nossos slides, desabilitamos os controles de navegação, habilitamos a navegação utilizando o scroll do mouse e alteramos a transição dos slides para o efeito &#8216;concave&#8217;.

Para conferir uma lista completa de opções disponíveis, leia o <a href="https://github.com/hakimel/reveal.js/blob/master/README.md#configuration" target="_blank">README</a> do projeto no github.

## Fragmentos

Para utilizar fragmentos com reveal.js basta adicionar a classe _fragment_ a um ou mais conteúdos dentro de um slide. 

Vamos alterar o nosso slide &#8220;Sobre o autor&#8221; e exibir os ítens da lista de forma fragmentada:

<pre class="lang-html">...
   &lt;h1&gt;Sobre o autor&lt;/h1&gt;¬
   &lt;ul&gt;¬
     &lt;li class="fragment"&gt;15 anos de experiência&lt;/li&gt;¬
     &lt;li class="fragment"&gt;desenvolvedor na globo.com&lt;/li&gt;¬
   &lt;/ul&gt;¬
...</pre>

Atualizando a apresentação no navegador, ao chegar no slide acima, os elementos da lista serão exibidos passo a passo.

## Temas & Plugins

Além do tema padrão, a biblioteca reveal.js disponibiliza outros temas para nossas apresentações. São eles: _beige_, _night_, _serif_, _simple_ e _sky_.

Para utilizar um tema diferente, basta alterar o link do CSS de _default_ para o tema desejado. No exemplo abaixo passamos a utilizar o tema _night_.

<pre class="lang-html">...
&lt;link rel="stylesheet" href="css/reveal.min.css"&gt;
&lt;link rel="stylesheet" href="css/theme/night.css"&gt;
...</pre>

Outra forma de alterar e estender nossa apresentação é utilizar o pacote de plugins que acompanha a biblioteca. Dentro do diretório _plugin_ estão disponíveis extensões para adicionar conteúdo com Markdown, zoom, notas e highlight de código.

Para ativar um plugin, basta adicionar a opção _dependencies_ na inicialização do objeto Reveal:

<pre class="lang-javascript">Reveal.initialize({
  autoSlide: 6000,
  center: true,
  controls: false,
  mouseWheel: true,
  transition: 'concave',
  dependencies: [{ src: 'plugin/zoom-js/zoom.js' }]
});</pre>

No exemplo acima habilitamos o plugin de zoom. Agora, ao utilizar a combinação _alt + clique do mouse_ aplicamos zoom in/zoom out nos slides.

## E mais&#8230;

Isso foi só uma parte do que a biblioteca reveal.js oferece. É possível ainda criar temas próprios (o diretório de temas inclui um esqueleto em Sass), tirar proveito da API JavaScript do objeto Reveal (com métodos para controlar a navegação dos slides), escutar os eventos disparados por trocas de slides e fragmentos, entre outras coisas.

Além do pacote JavaScript, você pode criar suas apresentações utilizando o serviço <a href="http://www.rvl.io/" target="_blank">www.rvl.io</a>, sem a necessidade de código.

Para finalizar, seguem os links do código fonte do exemplo e da apresentação criada aqui:

  * <a href="https://github.com/tableless/exemplos/tree/gh-pages/revealjs" target="_blank">código fonte da apresentação</a>
  * <a href="http://tableless.github.com/exemplos/revealjs/" target="_blank">visualizar a apresentação no navegador</a>