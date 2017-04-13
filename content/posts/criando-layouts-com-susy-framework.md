---
title: Criando Layouts com Susy Framework
author: Felipe César
type: post
date: 2015-08-03
excerpt: Conheça o Susy Framework e desenvolva layouts facilmente com ele.
url: /criando-layouts-com-susy-framework/
categories:
  - CSS
  - Pré-processadores
  - SASS
tags:
  - CSS
  - design
  - grid
  - layout
  - SASS
  - susy

---
Com a alta demanda e prazos cada vez menores somos obrigados a trabalhar cada vez mais rápido e isso serve de incentivo para que novos frameworks sejam feitos buscando melhorar a qualidade no desenvolvimento. Um desses frameworks é o Susy e nesse artigo vamos conhecer e dar os primeiros passos com ele.

## O que é Susy?

Susy é um framework que permite criar grids de acordo com as necessidades do seu site. Diferente de outros como Bootstrap e Foundation, você não vai precisar importar um arquivo cheio de classes em que vai usar apenas algumas delas. O Susy trabalha direto no estilo das classes que você definiu e personalizou.

Para começar a usá-lo você precisa ter o Sass instalado e o mínimo de conhecimento sobre ele. Não vou me aprofundar em Sass, pois não é o foco desse artigo, mas para quem tiver alguma dúvida a respeito pode ver uma série de <a href="http://goo.gl/PmuwuA" target="_blank">artigos</a> aqui mesmo no Tableless.

Agora que já sabemos do que se trata vamos começar a desenvolver nosso layout com Susy.

## Criando seu primeiro layout com Susy

Assumindo que você já tem o Sass instalado, vamos instalar o Susy. Abra o prompt de comando e digite:

<pre class="lang-shell">gem install susy</pre>

Após concluir a instalação vamos criar uma pasta para o projeto e dentro dela um arquivo index.html, uma pasta css e uma pasta scss com um arquivo style.scss dentro dela.

<img class="alignnone size-full wp-image-50233" src="http://tableless.com.br/uploads/2015/07/estrutura-de-pastas.jpg" alt="Learning Susy" width="617" height="76" />

## Iniciando o desenvolvimento

Vamos construir o seguinte layout:

<img class="alignnone size-full wp-image-50282" src="http://tableless.com.br/uploads/2015/07/layout.png" alt="layout" />

Primeiramente vamos iniciar o Sass para que nosso código possa ser compilado. Abra a pasta do projeto na linha de comando e digite:

<pre class="lang-shell">sass --watch scss:css -r susy</pre>

Feito isso um arquivo style.css foi criado dentro da pasta css. Vamos adiciona-lo no head no html:

<pre class="lang-html">&lt;link rel="stylesheet" href="css/style.css"&gt;</pre>

Vamos adicionar o normalize ao nosso projeto

Para usar o Susy no projeto temos apenas que adicionar a seguinte linha no style.scss:

<pre class="lang-css">@import "susy";</pre>

### Susy Map

Susy Map é um conjunto de instruções que são declaradas no início do projeto.  O grid é gerado de acordo com as informações declaradas nele. Abaixo temos o Map do nosso projeto, vamos adiciona-lo no style.scss, mais informações podem ser adicionadas , mas para nosso projeto é o suficiente. As linhas estão comentadas informando o que cada uma faz.

<pre class="lang-sass">$susy:(
    columns: 8, // número de colunas do grid
    container: 1140px, // largura do container
    debug: (image: show), // exibe as colunas do grid
);</pre>

Vou adicionar o código completo, mas somente as funções do Susy serão explicadas. Então vamos começar! No HTML, vamos adicionar o header da página:

<pre class="lang-html">&lt;header class="site-header"&gt;
    &lt;div class="container"&gt;
        &lt;div class="logo"&gt;&lt;a href="#"&gt;Logo&lt;/a&gt;&lt;/div&gt;
        &lt;nav class="menu"&gt;
            &lt;ul&gt;
                &lt;li&gt;&lt;a href="#"&gt;Home&lt;/a&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;About&lt;/a&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;Photos&lt;/a&gt;&lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;Contact&lt;/a&gt;&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/nav&gt;
    &lt;/div&gt;
&lt;/header&gt;</pre>

Vamos adicionar o estilo dele:

<pre class="lang-sass">.container {
    @include container(); // inclui na classe o container definido no Susy Map
}
.logo {
    float: left;
    padding: 0.9375rem;
    line-height: 2rem;
    font-size: 1.5rem;
}
nav {
    float: right;
    li {
        list-style: none;
        float: left;
        margin-left: 2rem;
        line-height: 2rem;
    }
}</pre>

Depois do header vamos inserir o banner no html:

<pre class="lang-html">&lt;div class="container"&gt;
    &lt;img src="img/banner.jpg" class="banner"&gt;
&lt;/div&gt;</pre>

Agora o estilo do banner:

<pre class="lang-sass">img {
    width:100%;
}
.banner {
    @include span(8 of 8);
    margin: gutter() 0;
    height: 100%;
}</pre>

O &#8220;@include span (8 of 8)&#8221; é uma função do Susy que diz que o banner irar ocupar 8 colunas das 8 declaradas no Susy Map, mas não é só isso, reparem que no margin adicionamos um valor &#8220;gutter()&#8221;, isso é outra função do Susy que adiciona o valor que existe entre os grids, pode ver como o espaço que está entre o header e o banner é o mesmo que está entre as 8 colunas que definimos no grids.

Agora vamos adicionar o conteúdo do layout:

<pre class="lang-html">&lt;div class="container"&gt;
    &lt;div class="sidebar"&gt;
        &lt;ul&gt;
            &lt;li&gt;&lt;a href="#"&gt;Fortaleza&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="#"&gt;Natal&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="#"&gt;Recife&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href="#"&gt;Salvador&lt;/a&gt;&lt;/li&gt;
        &lt;/ul&gt;
    &lt;/div&gt;
    &lt;div class="content"&gt;
        &lt;div class="content-item"&gt;&lt;img src="img/001.jpg"&gt;&lt;/div&gt;
        &lt;div class="content-item"&gt;&lt;img src="img/002.jpg"&gt;&lt;/div&gt;
        &lt;div class="content-item"&gt;&lt;img src="img/003.jpg"&gt;&lt;/div&gt;
        &lt;div class="content-item"&gt;&lt;img src="img/004.jpg"&gt;&lt;/div&gt;
        &lt;div class="content-item"&gt;&lt;img src="img/005.jpg"&gt;&lt;/div&gt;
        &lt;div class="content-item"&gt;&lt;img src="img/006.jpg"&gt;&lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;</pre>

E o estilo delas:

<pre class="lang-sass">.sidebar {
    @include span (2 of 8);
    ul {
        margin: 0;
        padding: 1.2rem;
    }
    li {
        list-style: none;
        font-size: 1.1rem;
        border-bottom: 2px dotted #c6c6c6;
        &:last-child {
            border:none;
        }
    }	
    a {
        display: block;
        padding: 1rem .5rem;
        color: #333;
        line-height: 2;
        text-decoration: none;
    }
}
.content {
    @include span (6 of 8 last);
}
.content-item {
    @include gallery(2 of 6);
    margin-bottom: gutter();
}</pre>

Repare nos includes que acabamos de usar. Na mesma linha usamos 2 colunas para o sidebar e as 6 para o content, veja que adicionamos um last no final do include na classe content, esse last serve para dizer que são as ultimas colunas da linha. O espaço entre os grids é feito com um margin-right e o last serve parar remover esse margin-right do ultimo item do grid. Olha lá o aquivo style.css para entender melhor o que está sendo feito.

O footer não tem muito o que falar, então vamos apenas adicionar o código:

<pre class="lang-html">&lt;footer class="site-footer"&gt;
    &lt;div class="container"&gt;
        &lt;p&gt;Copyright © 2015 - Desenvolvido por Felipe César para o Tableless&lt;/p&gt;
    &lt;/div&gt;
&lt;/footer&gt;</pre>

E o estilo:

<pre class="lang-sass">.site-footer {
    margin-top: 2rem;
    padding: 0.6rem 0;
    color: #fff;
}</pre>

Por fim vamos apenas remover do Susy Map a linha que exibe os grids:

<pre class="lang-sass">debug: (image: show),</pre>

Pronto, finalizamos o nosso layout, fácil não é?! Esse projeto foi bem simples apenas para apresentar o framework e mostrar como funciona, mas não pare por aí, faça o <a href="https://github.com/felipecesr/layout-susy-framework" target="_blank">download do código</a>, brinque com ele, acesse a documentação do <a href="http://susydocs.oddbird.net/en/latest/" target="_blank">Susy</a> e conheça outros recursos que podem te ajudar bastante no desenvolvimento.

Espero que tenham gostado do artigo, bons estudos!