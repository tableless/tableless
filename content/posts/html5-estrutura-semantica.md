---
title: HTML 5 – Mudanças na estrutura e semântica
author: Diego Eis
type: post
date: 2009-02-16
excerpt: Todos os dias sites e mais sites são publicados na internet e nenhum deles com um padrão de nomenclatura de classes e ids.
url: /html5-estrutura-semantica/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356454344
shorturls:
  - 'a:3:{s:9:"permalink";s:49:"http://tableless.com.br/html5-estrutura-semantica";s:7:"tinyurl";s:26:"http://tinyurl.com/3kpur8s";s:4:"isgd";s:19:"http://is.gd/BlH9VO";}'
twittercomments:
  - 'a:3:{i:19728203417387008;s:6:"136503";i:102575489302003712;s:7:"retweet";i:102563722484133888;s:7:"retweet";}'
tweetcount:
  - 4
dsq_thread_id: 503016649
categories:
  - Artigos
  - Código
  - HTML
  - Tecnologia e Tendências
tags:
  - clientside
  - html5
  - padroes
  - Semântica
  - tableless
  - xhtml

---
A **Semântica** sempre um dos pontos mais importantes do **desenvolvimento com Padrões Web**. Algumas iniciativas com o **[Microformats][1]** vieram na tentativa de trazer mais semântica ainda para nossos códigos, com o intuito de novas aplicações e oportunidades pudessem utilizar melhor a informação distribuída na web.<!--more--> Acontece que o resto do HTML não foi a bastante tempo modificado. Por exemplo, como você consegue distinguir de forma automática as informações do &#8220;header&#8221; (cabeçalho) dos sites? Não consegue. Você não consegue por exemplo, de maneira automatizada, identificar o que é um rodapé ou a parte do layout que está exibindo um artigo, por exemplo.

Todos os dias sites e mais sites são publicados na internet e nenhum deles com um padrão de nomenclatura de classes e ids que possamos utilizar para extrair informação de maneira inteligente. O **HTML 4.01** é a versão atual da linguagem básica da Web, e não é atualizado a alguns anos. Esses detalhes de semântica não podem ser supridos para sempre por tecnologias como o Microformats. A versão 5 do HTML tende a suprimir essas necessidades e também atualizar pontos antigos do HTML 4, por exemplo, formulários.

Como disse no começo deste post, a estrutura de um site não é óbvia para as máquinas. Não existe nenhum padrão de construção dos elementos para indicar o que é o cabeçalho e o que é o rodapé, por exemplo. No [HTML 5][2], iremos utilizar um padrão de tags que nos ajudará a marcar estas estruturas. Uma estrutura conhecida é mais ou menos assim:

<pre class="lang-html">&lt;body&gt;
  &lt;div id="header"&gt;...&lt;/div&gt;
   &lt;div id="menu"&gt;...&lt;/div&gt;
   &lt;div class="post"&gt;...&lt;/div&gt;
   &lt;div id="sidebar"&gt;...&lt;/div&gt;
   &lt;div id="rodape"&gt;...&lt;/div&gt;
&lt;/body&gt;
</pre>

Na estrutura acima, utilizei alguns nomes de classes e ids que costumamos utilizar no dia-a-dia. eu mesmo não utilizo a classe POST, uso mais CONTENT ou algo parecido. A estrutura do HTML acabará com isso. A idéia é substituir esse amontoado de DIVS por elementos que se encarreguem dessas funções, um exemplo da estrutura serial esse:

<pre class="lang-html">&lt;body&gt;
  &lt;header&gt;...&lt;/header&gt;
  &lt;nav&gt;...&lt;/nav&gt;
&lt;section&gt;
  &lt;article&gt;
      ...
  &lt;/article&gt;
&lt;/section&gt;
  &lt;aside&gt;...&lt;/aside&gt;
  &lt;footer&gt;...&lt;/footer&gt;
&lt;/body&gt;
</pre>

  * O elemento **header** define o cabeçalho. Nav define o menu ou a navegação do site. 
  * **Article** define uma parte da página que tem uma composição de formulários, textos etc. Por exemplo, pode ser um post de forum, blog, comentários etc. 
  * O elemento **Section** define uma seção do layout em um determinado element. Ele pode conter um **header** e também um **footer** se preciso. 
  * O elemento **aside** consiste em envolver informações que tem algo a ver com o conteúdo principal do site. Pode ser um menu lateral, um sidebar padrão com menu, banner, busca etc&#8230;
  * Footer define o rodapé do elemento ou do layout. 

Entenda que agora, qualquer elemento pode ter seu conteúdo separado por seções com o elemento **section**. Note também que os elementos podem ter também um **header** e um **footer** independentes do resto do layout. Como na imagem.

[<img src="http://tableless.com.br/uploads/1999/11/printtableless-300x167.gif" alt="Exemplo Elemento HEADER" title="Exemplo Elemento HEADER" width="300" height="167" class="alignnone size-medium wp-image-1178" srcset="uploads/1999/11/printtableless-300x167.gif 300w, uploads/1999/11/printtableless.gif 603w" sizes="(max-width: 300px) 100vw, 300px" />][3]

Uma dúvida comum entre os desenvolvedores é como fazer a estruturação e distribuição das tags de títulos (h1 até h6). Por exemplo, se eu utilizei já a tag H1 no logo do site, poderei utilizar para o título do artigo? Se repetirmos muitas vezes as mesmas tags de títulos, a importância que cada título tem sobre o outro se perderá. O Google poderá indexar de forma diferente e etc.
  
No HTML 5 esse problema ser resolverá, porque cada section que você inicia, você poderá começar novamente uma nova ordem de títulos. Por exemplo:

<pre class="lang-html">&lt;header&gt;
  &lt;h1&gt;Logo&lt;/h1&gt;
&lt;/header&gt;
&lt;article&gt;
    &lt;h1&gt;T&iacute;tulo do artigo&lt;/h1&gt;
    &lt;p&gt;texto&lt;/p&gt;
    &lt;h2&gt;Subtitulo&lt;/h2&gt;
    &lt;p&gt;Mais texto&lt;/p&gt;
&lt;/article&gt;
</pre>

Dessa forma você conseguirá definir exatamente qual a importância de cada título e os leitores de tela, sistemas de busca e outras aplicações conseguirão fazer uma separação mais eficaz dos elementos textuais.

Entenda que os divs não irão deixar de existir. Você os usará em casos muito específicos, por exemplo, para fazer caixas de destaque:

<pre class="lang-html">&lt;section&gt;
    &lt;div class="destaque"&gt;
       &lt;h1&gt;Destaque 1&lt;/h1&gt;
       &lt;p&gt;Texto&lt;/p&gt;
    &lt;/div&gt;
    &lt;div class="destaque"&gt;
       &lt;h1&gt;Destaque 1&lt;/h1&gt;
       &lt;p&gt;Texto&lt;/p&gt;
    &lt;/div&gt;
  &lt;/section&gt;
</pre>

Nesse caso estou usando os DIVs apenas por motivos de formatação. Ali não caberia um article, porque o conteúdo não é uma redação de um post, artigo e etc&#8230; Também não caberia uma section porque eu já agrupei este conteúdo dentro de uma section pai.

Para saber mais sobre isso, leia: [The Elements Of HTML 5][4].
  
Irei escrever outros artigos sobre a inserção de vídeo e audio no código e uma série de outros assuntos interessantes sobre HTML 5. E o que você acha disso tudo? Deixe seu comentário!

 [1]: http://tableless.com.br/microformatos-internet-movel-e-quem-ainda-nao-entendeu-nada
 [2]: http://tableless.com.br/html-5-semantica-e-o-que-e-importante-na-web
 [3]: http://tableless.com.br/uploads/1999/11/printtableless.gif
 [4]: http://www.whatwg.org/specs/web-apps/current-work/multipage/semantics.html