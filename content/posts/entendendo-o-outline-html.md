---
title: Entendendo o Outline do HTML
author: Daniel Ramos
type: post
date: 2015-01-22
excerpt: Entenda porquê não usar tantos H1 e como funciona o fluxo de outline do HTML.
url: /entendendo-o-outline-html/
categories:
  - Acessibilidade
  - HTML
  - HTML5
tags:
  - acessibilidade
  - html
  - html 5
  - outline
  - Semântica

---
O Outline do documento HTML é a estrutura do documento que é gerada pelos títulos, títulos de formulários, títulos das tabelas e qualquer outro elemento que marque alguma seção de conteúdo no documento. Essas marcações de Outline podem ser usadas para várias iniciativas, por exemplo, um browser ou alguma outra interface possa criar uma Tabela de Conteúdo. Outras tecnologias assistivas podem usar também estas seções para formar a navegação, como em um leitor de tela, mas ou menos como acontece no WAI-ARIA, mas de maneira mais natural.

Os elementos de cabeçalho h1-h6, contribuem para o outline do documento HTML 5, criando uma estrutura hierárquica e definindo as seções da página. Os cabeçalhos são importantes para otimização de buscas e também para navegação em leitores de telas, já que usuários desses aparelhos navegam pelos títulos na página.

Nas versões HTML4 e XHTML tudo o que tinhamos para estruturar o outline eram as tags h1-h6. Tínhamos então o seguinte código:

<pre class="lang-html">&lt;body&gt;

  &lt;h1&gt;Midias reprodutiveis&lt;/h1&gt;
  &lt;h2&gt;Disco&lt;/h2&gt;
  &lt;h2&gt;Arquivo&lt;/h2&gt;
  &lt;h3&gt;Video: Avi, Divx, Mp4, Xvid&lt;/h3&gt;
  &lt;h2&gt;Disco USB de armazenamento&lt;/h2&gt;

&lt;/body&gt;
</pre>

E sua saída era:

<pre class="lang-text">1. Midias reprodutiveis
  1. Disco
  2. Arquivo
    1. Video: AVI, DIVx, MP4, Xvid
  3. Disco USB de armazenamento
</pre>

Browsers comuns não mostram o outline do documento portanto para visualiza-los é necessário usar uma ferramenta chamada HTML5 outliner([https://gsnedders.html5.org/outliner/][1]). Mesmo que o nível dos cabeçalhos dos exemplos sejam diferentes, a saída como vimos é a mesma.

Pois bem, agora com o HTML5 temos novas formas de estruturar o documento. Temos os elementos de sectioning content — article, aside, nav e sections — que demarcam diferentes seções num documento e define o escopo para os elementos de cabeçalho (assim como o header e o footer).

Isso mudou o paradigma e agora podemos ter diversos elementos seccionados com sua própria hierarquia de h1-h6. Isso tem efeito no outline. Num documento onde temos:

<pre class="lang-html">&lt;body&gt;

   &lt;h1&gt;Midias reprodutiveis&lt;/h1&gt;

   &lt;section&gt;
      &lt;h1&gt;Disco&lt;/h1&gt;
   &lt;/section&gt;

   &lt;section&gt;
      &lt;h1&gt;Arquivo&lt;/h1&gt;
      &lt;section&gt;&lt;!-- essa é uma section de outra --&gt;
      &lt;h1&gt;Video: Avi, Divx, Mp4, Xvid&lt;/h1&gt;
      &lt;/section&gt;
   &lt;/section&gt;

   &lt;section&gt;
      &lt;h1&gt;Disco USB de armazenamento&lt;/h1&gt;
   &lt;/section&gt;
&lt;/body&gt;
</pre>

Temos esse outline:

<pre class="lang-text">1. Midias reprodutiveis
  1. Disco
  2. Arquivo
    1. Video: AVI, DIVx, MP4, Xvid
  3. Disco USB de armazenamento
</pre>

Como pode ser observado cada section tem o seu h1, mas o outline não sofre alteração.

Mas e se o segundo exemplo não tivesse as sections? Então teriamos um resultado distinto:

<pre class="lang-text">1. Midias reprodutiveis
 2. Disco
 3. Arquivo
 4. Video: AVI, DIVx, MP4, Xvid
 5. Disco USB de armazenamento
</pre>

Dentre o primeiro e o segundo exemplo, claro que o segundo é mais válido por sua importância semântica.

Mas todas as sections tem as tags h1. Isso pode ser perigoso. Os leitores de tela não são atualizados no mesmo passo um do outro (assim como os browsers comuns). Sendo assim esse tipo de marcação pode impactar severamente, comprometendo a acessibilidade. Poderíamos usar o segundo exemplo e em alguns leitores de tela o resultado da saída ser o da ultima abordagem:

<pre class="lang-text">1. Midias reprodutiveis
 2. Disco
 3. Arquivo
 4. Video: AVI, DIVx, MP4, Xvid
 5. Disco USB de armazenamento
</pre>

Isso ocorre por quê esses leitores não distinguem a marcação dentro das tags section. Sendo assim o ideal seria usar as tags sections proporcionando uma melhor marcação, mas uma hierarquia de cabeçalhos semelhante a do HTML4.

Então fazemos assim:

<pre class="lang-html">&lt;body&gt;

   &lt;h1&gt;Midias reprodutiveis&lt;/h1&gt;

   &lt;section&gt;  
     &lt;h2&gt;Disco&lt;/h2&gt; 
   &lt;/section&gt; 

   &lt;section&gt; 
     &lt;h2&gt;Arquivo&lt;/h2&gt; 
     &lt;section&gt;&lt;!-- essa é uma section de outra --&gt; 
       &lt;h3&gt;Video: Avi, Divx, Mp4, Xvid&lt;/h3&gt; 
     &lt;/section&gt; 
   &lt;/section&gt; 

   &lt;section&gt; 
     &lt;h2&gt;Disco USB de armazenamento &lt;/h2&gt; 
   &lt;/section&gt; 

&lt;body&gt;
</pre>

e a saída nos leitores de tela; atualizados ou não; será a mesma:

<pre class="lang-text">1. Midias reprodutiveis
  1. Disco
  2. Arquivo
    1. Video: AVI, DIVx, MP4, Xvid
  3. Disco USB de armazenamento
</pre>

Assim preservamos a acessibilidade em leitores de tela atualizados ou não, privilegiando todos os usuários.

[Bruce Lawson &#8211; Headings in HTML 5 and accessibility][2]

 [1]: http://gsnedders.html5.org/outliner/ "Link do Html 5 Outliner"
 [2]: http://http://www.brucelawson.co.uk/2009/headings-in-html-5-and-accessibility/ "Link para Bruce Lawson - Headings in HTML 5 and accessibility"