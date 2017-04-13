---
title: Material Design com Materialize
author: Tiago Luiz
type: post
date: 2015-09-30
excerpt: Crie seu site utilizando um Framework totalmente material design, que não deixa a desejar em nada e seus resultados podem te surpreender. Do Conceito à prática com layout Material.
url: /material-design-com-materialize/
categories:
  - CSS3
  - Design
  - HTML
  - UX
tags:
  - CSS
  - framework
  - front-end
  - html
  - iniciante
  - material
  - material design
  - material design lite

---
Há muito tempo quero falar um pouco sobre desenvolvimento de sites utilizando layouts baseados no Material Design do Google, mas entre **fazer** e **falar** há um abismo enorme. Minha verdadeira intenção é compartilhar um pouco a maneira mais fácil de desenvolver um layout utilizando todos aqueles conceitos que a Google tem implementado atualmente.

## Primeiros Passos

O <a href="http://materializecss.com/" target="_blank">Materialize</a> é um Framework desenvolvido para facilitar e agilizar nosso desenvolvimento quando o assunto é Material Design. Além de ágil, possui uma infinidade de vantagens que permitem que na maioria das vezes dispensam o uso de outros frameworks para complementá-lo.

Para baixar os arquivos do Materialize clique em <a href="http://materializecss.com/getting-started.html" target="_blank">Getting Started</a>, lá você verá uma documentação explicando como fazer o download dos arquivos e todas as maneiras que você tem para fazer isso, ou também pode usar a CDN dele como geralmente muitos fazem com o JQUERY. Os arquivos são bem distribudos e não diferem dos demais Frameworks que existem.

### Vamos para as vantagens dele

Uma das principais vantagens é o fato de ser muito similar ao Material Design desenvolvido pela google. Outra vantagem que podemos observar são os amplos recursos de JQuery que ele possui como: Slider, Lightbox, Captions, Modais, Transitions, Waves entre muitos outros. Melhor do que falar é mostrar. Esses recursos ficam na categoria <a href="http://materializecss.com/media.html" target="_blank">JAVASCRIPT</a>.

O sistema de grid usado é bastante parecido com os frameworks já existentes, como o Bootstrap. 

![][1]

<pre class="lang-html">&lt;body&gt;
      &lt;div class="container"&gt; &lt;!-- Container similar ao utilizado em outros Frameworks --&gt;
            &lt;div class="row"&gt; &lt;!-- Row também similar ao utilizado em outros Frameworks --&gt;
                 &lt;div class="col s12 m4 l4"&gt;Eu sou uma coluna&lt;/div&gt; &lt;!-- Coluna com 3 tamanhos--&gt;
            &lt;/div&gt;
      &lt;/div&gt;
&lt;/body&gt;
</pre>

#### Entendendo as colunas

É muito simples, assim como o bootstrap que trabalha com 4 tamanhos de coluna, muito pequeno, pequeno, médio e grande, o materialize decidiu trabalhar com 3 tamanhos que são pequeno médio e grande, nada que assuste ou prejudique o andamento do projeto. Para saber mais entre no <a href="http://materializecss.com/grid.html" target="_blank">menu CSS e acesse o submenu Grid</a>

### Alguns pequenos diferenciais que ele possui

Alguns diferenciais que ele possui são os botões, o modal, os cards, as collections e o mais importante talves de todos o menu lateral, vou mostrar alguns desses abaixo.

#### Cards

![][2]

#### Sidenav

![][3]

### Vendo essa belezinha funcionar ^^

Eu poderia colocar um milhão de exemplos feitos aqui, mas não tenho os direitos autorais deles então caso queira ver o showcase do site acesse o link <a href="http://materializecss.com/showcase.html" target="_blank">Showcase</a> e veja. Mas para não deixar vocês sem nenhum exemplo deixo aqui um site feito por mim através do materialize, espero que gostem o link está na imagem e abaixo dela.
  
<a href="http://blog.loguei.com/" target="_blank"><br /> <img src="http://tableless.com.br/uploads/2015/09/263dfd28861105.55d5d38e09a6f.jpg" alt="" /><br /> </a>
  
<a href="http://blog.loguei.com/" target="_blank">blog.loguei.com</a>

Bem, aqui terminamos esse maravilhoso assunto sobre um Framework bem simples e maneiro de usar. Espero ter ajudado um pouco a todos. Obrigado ^^.

 [1]: http://tableless.com.br/uploads/2015/09/materialize-css-framework-01.jpg
 [2]: http://tableless.com.br/uploads/2015/09/Sem-Título-1.jpg
 [3]: http://tableless.com.br/uploads/2015/09/menu.gif