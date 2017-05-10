---
title: Bloginfo Template Tag
author: Diego Eis
type: post
date: 2008-08-21
url: /bloginfo-template-tag/
aktt_tweeted:
  - 1
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356393982
shorturls:
  - 'a:3:{s:9:"permalink";s:45:"http://tableless.com.br/bloginfo-template-tag";s:7:"tinyurl";s:26:"http://tinyurl.com/3tfdmyq";s:4:"isgd";s:19:"http://is.gd/lUTYev";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038409
categories:
  - Técnicas e Práticas
  - Wordpress
tags:
  - desenvolvimento web
  - php
  - Wordpress
  - xhtml

---
A [Template Tag Bloginfo][1] mostra informações sobre o blog. A maioria dessas informações são modificadas diretamente no painel de controle da sua instalação do WordPress. Isso pode ser utilizado em qualquer lugar do seu site. A Template Tag é a **get_bloginfo()**.

Por exempo, se você precisa do nome do site para colocar em algum lugar do site, como o Logo, a sintaxe seria:

<pre lang="php" line="1"><h1>
  <?php bloginfo('name'); ?>
</h1></pre>

<!--more-->


  
Os valores possíveis:

  * **&#8216;name&#8217;** &#8211; Nome do site. Valor padrão.
  * **&#8216;description&#8217;** &#8211; Descrição do site.
  * **&#8216;url&#8217;** &#8211; O endereço do site.
  * **&#8216;rdf_url&#8217;** &#8211; Endereço do RDF/RSS 1.0.
  * **&#8216;rss_url&#8217;** &#8211; Endereço do RSS 0.92.
  * **&#8216;rss2_url&#8217;** &#8211; Endereço para RSS 2.0.
  * **&#8216;atom_url&#8217;** &#8211; URL Feed Atom.
  * **&#8216;comments\_rss2\_url&#8217;** &#8211; Url para acesso do RSS 2.0 dos comentários.
  * **&#8216;pingback_url&#8217;** &#8211; Url dos Pingbacks Pingback (XML-RPC file).
  * **&#8216;admin_email&#8217;** &#8211; Endereço de email do administrador do WordPress.
  * **&#8216;charset&#8217;** &#8211; Tabela de caractéres utilizada no Worpdress; Você define isso na Opções de Leitura no Admin.
  * **&#8216;version&#8217;** &#8211; Mostra a versão do WordPress que você utiliza..
  * **&#8216;text_direction&#8217;** &#8211; Retorna &#8216;rtl&#8217; leitura da direita para esquerda ou &#8216;ltr&#8217; para leitura da esquerda para direita, que é o padrão.

Se você quer ler mais sobre WordPress, experimente visitar a [parte exclusiva sobre WordPress no Tableless][2].

[Mais sobre Bloginfo no site do WordPress][3].

 [1]: http://tableless.com.br/bloginfo-template-tag/
 [2]: http://tableless.com.br/wordpress/
 [3]: http://codex.wordpress.org/Template_Tags/bloginfo