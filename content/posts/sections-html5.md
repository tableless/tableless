---
title: 'Sections: seções do HTML5 – Parte 1'
author: Diego Eis
type: post
date: 2010-09-23
excerpt: O site é dividido em seções. Cada seção tem seu significado e carrega informações de diversos assuntos. Os elementos do seção do HTML5 separam cada um desses elementos.
url: /sections-html5/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356460068
shorturls:
  - 'a:3:{s:9:"permalink";s:38:"http://tableless.com.br/sections-html5";s:7:"tinyurl";s:26:"http://tinyurl.com/3ul3roy";s:4:"isgd";s:19:"http://is.gd/4mycqs";}'
twittercomments:
  - 'a:2:{i:12673607016652800;s:6:"136331";i:25731677342924801;s:6:"136705";}'
tweetcount:
  - 2
dsq_thread_id: 503039561
categories:
  - HTML5
  - SEO
tags:
  - 2010
  - desenvolvimento web
  - html5
  - Na Prática
  - Semântica
  - tableless
  - tutorial
  - web standards

---
A estrutura de um site é dividida em diversas seções. Cada seção representa uma fatia do layout e também representa um grupo de conteúdo. Cada um destes grupos tem seu assunto específico. Nas minhas aulas eu costumava apresentar estas seções como **seções mestres** ou **seções principais**. Normalmente para descrever em HTML estas seções, usávamos a tag `div`. O elemento `div` é um elemento genérico que serve para criar DIVISÕES. Estas divisões não tinham significado semântico nenhum, não levavam nenhum tipo de informação &#8220;extra&#8221;, mas a nível de formatação resolvia nosso problema. Nós agrupávamos o conteúdo das seções e conseguíamos distinguir cada seção nomeando os divs com CLASSES e IDs e assim formatávamos o código com CSS. 

A nível de semântica ou seja, para entregar informação útil para o usuário, sistemas ou aplicações, estas seções não eram eficazes. Não havia como distinguir um cabeçalho de um rodaé. Não era possível diferenciá-los pelo nome porque cada desenvolvedor dava seu próprio nome para o elemento: alguns chamavam de header, outro cabeçalhos, outros testeira (acredite se quiser) e assim por diante. Por estes motivos que no **HTML5** as seções ganharam mais significado.

### Cada coisa em seu lugar

As novas seções também fazem divisões, mas além disso elas servem significado para o código. Neste novo cenário o `div` perdeu um pouco o foco e será utilizado em detalhes. Ele ficou bem mais genérico que antes. Essa é uma das razões que o `div` é coisa do passado. Abaixo veja uma breve descrição dos novos elementos de seção do HTML5:

HEADER
:   Define um grupo de títulos ou o cabeçalho de uma determinada seção.

FOOTER
:   Define o rodapé das seções ou da página.

NAV
:   Define um grupo ou bloco de links de navegação.

ASIDE
:   Define um elemento lateral que pode conter blocos de navegação (NAVs), citações e outras informações que costumamos colocar em uma sidebar.

ARTICLE
:   Define a área onde há um artigo, texto, redação, conteúdo e etc&#8230;

SECTION
:   Define um bloco ou um grupo de um assunto específico. É importante entender que a section agrupa diversos elementos que tenham relação entre si. Por exemplo, se há uma área no site que há links, conteúdo, imagens e etc de um assunto em comum, você agrupará esses elementos com uma section. Nesse caso, ele entrou no lugar daquele div que fazíamos para dividir grandes blocos de assuntos em comum.

### E o div? Exemplo.

E onde entra o `div`? O Div servirá para agruparmos elementos dentro destes sections ou fazer outros detalhes que não precisam de significado semântico, apenas visual.
  
Imagine que exista uma section chamada NOTÍCIAS:

<pre class="lang-html">&lt;section id="noticias"&gt;
...
&lt;/section&gt;
</pre>

Dentro dessa `section` há 3 colunas de assuntos diversos ou randomizados que dividem as chamadas.

<pre class="lang-html">&lt;section id="noticias"&gt;
   &lt;div&gt;
      ...
   &lt;/div&gt;
   &lt;div&gt;
      ...
   &lt;/div&gt;
   &lt;div&gt;
      ...
   &lt;/div&gt;
&lt;/section&gt;
</pre>

Suponha que cada uma colunas seja de um assunto diferente, por exemplo: Esporte, Política e Educação. Aí nesse caso não usaríamos `div` mas sim outras `sections`:

<pre class="lang-html">&lt;section id="noticias"&gt;
   &lt;section id="esporte"&gt;
      ...
   &lt;/section&gt;
   &lt;section id="politica"&gt;
      ...
   &lt;/section&gt;
   &lt;section id="educacao"&gt;
      ...
   &lt;/section&gt;
&lt;/section&gt;
</pre>

Você poderia utilizar DIVs com os IDs? Sim, claro. Mas lembre-se que o DIV é genérico, para os sistemas de busca, leitores de tela, aplicações e etc, os DIVs não indicam seções de conteúdo, mas o elemento `section` sim.

Há uma polêmica ainda com algumas ordens nas estruturas. No exemplo acima colocamos `sections` em vez de `divs`. Poderíamos ter colocado `article` dentro da `section` principal. Não vou entrar no que é mais certo ou no que é mais semântico porque neste contexto, ainda é subjetivo. Há alguns conceitos que iremos amadurecer durante um tempo. Contudo, temos que começar por algum lugar e claro, devemos estudar as melhores formas tanto para o projeto quanto para a semântica do código.

Você já deve ter lido isso aqui, mas lembre-se: semântica é o nome do jogo.