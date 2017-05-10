---
title: Schema – Marcação de dados estruturados
author: thiago-pacheco
type: post
date: 2012-04-02
excerpt: Entenda como o Schema pode ajudar a auxiliar o vocabulário de marcação de dados em páginas web.
url: /schema-marcacao-de-dados-estruturados/
tweetbackscheck:
  - 1356388657
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5762";s:7:"tinyurl";s:26:"http://tinyurl.com/7fklmwl";s:4:"isgd";s:19:"http://is.gd/efgqTs";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 633477884
categories:
  - Acessibilidade
  - Artigos
  - Código
  - SEO
tags:
  - 2012
  - acessibilidade
  - Browsers
  - buscadores
  - google
  - internet
  - schema

---
Há cerca de cinco anos atrás os principais buscadores se uniram para definir uma nova estrutura que pode ser chamado de “mapa de um site”, um documento onde tem uma única função que é informar aos buscadores a estrutura de um site, vídeos ou imagens. Essa estrutura é utilizada até hoje pelos desenvolvedores permitindo assim que todas as áreas ou páginas sejam facilmente “descobertas” pelos crawlers dos buscadores, foi assim que surgiu o <a href="http://sitemap.org/" target="_blank">sitemap.org</a>.

![Logo Buscadores][1]

Recentemente os principais buscadores se reuniram novamente, só que agora com a participação do Yandex um novo buscador russo que <a href="http://exame.abril.com.br/tecnologia/noticias/buscador-russo-yandex-afirma-ser-melhor-que-o-google" target="_blank">afirma ser melhor que o Google</a>. Os buscadores se uniram para definir uma nova marcação de dados estruturados, trata-se do <a href="http://schema.org/" target="_blank">Schema</a>.

Historicamente, o Google tem apoiado três padrões diferentes para dados estruturados, (microdados, microformat e RDFa) com a vinda do Schema as coisas irão mudar já que é proposto por três dos mais influentes players da web.

O projeto Schema vem basicamente para ser uma central de recursos para desenvolvedores, para auxiliar e apoiar o vocabulário de marcação de dados estruturados nas páginas web. Para conferir o novo projeto ele está disponível no endereço <a href="http://schema.org/" target="_blank">schema.org</a>.

Navegando na web você já deve ter visto em um resultado de busca algumas snippets mais interessantes, que mostram reviews de usuários, preços de produtos.

![Snippet][2]

Com uma snippet assim você acaba chamando mais atenção na SERP do Google conseguindo assim mais cliques e consequentemente mais visitantes, essa é uma das vantagens de utilizar a marcação de dados estruturados mais conhecida como <a href="http://www.seomonkey.com.br/rich-snippets/conheca-rich-snippets?utm_source=Tableless&utm_medium=GuestPost&utm_campaign=divulgacao-schema-rich-snippets" target="_blank">Rich Snippets</a> (Trechos ricos de informação).

### Introdução de como implementar

Para implementar o Schema em seu site é muito simples, em uma marcação HTML adicione a tag **itemscope** essa tag é responsável por identificar a seção da página que é sobre um determinado “assunto”, após especificar o itemscope é necessário atribuir o tipo desse “assunto”, para tal utilize a tag **itemtype**.

No Schema para determinados assuntos temos várias propriedades, por exemplo em um filme temos atores, diretor, preço, trailer, avaliações. Para atribuir essas informações para os motores de buscas utilize a tag **itemprop**, veja um exemplo:

<pre class="lang-html">&lt;div itemscope itemtype = "http://schema.org/Movie"&gt;
&lt;h1 itemprop=&rdquo;name&rdquo;&gt; Como &Aacute;gua - Anderson Silva &lt;/ h1&gt;
&lt;span itemprop=&rdquo;director&rdquo;&gt; Diretor: Pablo Croce&lt;/ span&gt;
&lt;a itemprop=&rdquo;url&rdquo; href="../movies/anderson-silva-como-agua.html"&gt;Trailer&lt;/ a&gt;
&lt;/div&gt;
</pre>

No código acima o “assunto” é o novo filme do Anderson Silva (Como Água) dirigido pelo diretor Pablo Croce com um link para um trailer do filme, por isso foi utilizado o itemtype “Movie”.

Desde 2004 o Google vem dando fortes sinais em relação a semântica e trechos ricos de informação, em meados de 2009 lançou uma ferramenta chamada [Rich Snippets Testing Tool][3] que tem como finalidade trazer uma amostra de como os Rich Snippets aparecereia nos resultados das buscas do Google.

Recentemente um executivo do Google anunciou uma das maiores renovações em seu algoritmo de busca, a ideia dessa atualização é que o buscador entenda da mesma forma que nós humanos entendemos o mundo, mais uma vez ressalto a importância de se ter um site semântico e bem estruturado.

 [1]: http://www.seomonkey.com.br/img/logos-buscadores.jpg
 [2]: http://www.seomonkey.com.br/img/snippets.jpg
 [3]: http://www.google.com/webmasters/tools/richsnippets