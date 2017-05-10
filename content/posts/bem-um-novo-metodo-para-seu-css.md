---
title: BEM, um novo método para seu CSS
author: Thaiana Poplade
type: post
date: 2014-02-10
excerpt: |
  A busca por padrões na criação de classes CSS é missão em diversas equipes front-end pelo mundo e o pessoal da Yandex parece ter conseguido definir uma metodologia, simples e funcional.
  Com vocês, BEM.
url: /bem-um-novo-metodo-para-seu-css/
dsq_thread_id: 2246439187
categories:
  - Artigos
  - CSS
  - CSS3

---
## O que é BEM?

A sigla BEM significa _block, element, modifier_ e segue essas propriedades para definir uma nova metodologia de criação de nomes para classes de folhas de estilo.

A estrutura é simples:
  
.elementopai, .elementopai\_\_filho, .elementopai\_\_filho- -primeiro

## Como assim?

As marcas registradas da estruturação BEM são o uso do &#8220;__&#8221; e do &#8220;- -&#8220;: sendo que o primeiro define um elemento (filho do elemento pai), e o segundo define um modificador.

Na prática:

<pre class="lang-html">.formcontent (elemento pai)
.formcontent__field (elemento filho)
.formcontent__field--first (elemento filho modificado)</pre>

Visualizando a estrutura HTML:

<pre class="lang-html">&lt;form class="formcontent"&gt;
  &lt;input type="text" class="formcontent__field--first" /&gt;
  &lt;input type="text" class="formcontent__field" /&gt;
  &lt;input type="submit" class="formcontent__field--button" /&gt;
&lt;/form&gt;</pre>

Simples, não é?

A grande ideia é padronizar para que qualquer front-end, ao se deparar com essa estrutura, separada por &#8220;__&#8221; ou &#8220;- -&#8220;, identifique os elementos e os modificadores só de analisar um HTML.

No geral, a aplicação BEM está sendo bem aceita por vários desenvolvedores, porém alguns outros argumentam alegando que as classes ficam &#8220;feias&#8221; com a aplicação desses caracteres a mais para definição dos nomes.

Particularmente, me soa como um argumento fraco, visto que em alguns artigos, já encontramos até boas aplicação desta metodologia à alguns frameworks conhecidos.

Como aqui no **Tableless** nossa missão é trazer o que há de novo, sigo dizendo que sempre vale a pena testar até mesmo para que em algum momento, você não seja pego de surpresa por classes nomeadas com _underlines_ e _hyphens._

Até a próxima.

😉