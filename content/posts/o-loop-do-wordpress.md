---
title: O LOOP do WordPress
author: Diego Eis
type: post
date: 2008-04-28
url: /o-loop-do-wordpress/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356410277
shorturls:
  - 'a:3:{s:9:"permalink";s:43:"http://tableless.com.br/o-loop-do-wordpress";s:7:"tinyurl";s:26:"http://tinyurl.com/3pnfjl3";s:4:"isgd";s:19:"http://is.gd/4R1Scy";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038097
categories:
  - Técnicas e Práticas
  - Wordpress
tags:
  - padroes web
  - serverside
  - Wordpress

---
O WordPress tem vários segredos&#8230; um dos segredos mais interessantes é o [Loop][1].

O Loop é usado no WordPress para mostrar os posts e páginas do site. O WordPress procura pelas páginas ou posts publicados no sistema e exibe seu conteúdo na página de acordo com os critérios que especificamos com as [Template Tags][2]. Qualquer código HTML ou PHP colocado no Loop será repetido em cada um dos posts exibidos. 

O loop deve ser colocado no index.php e em qualquer outro arquivo do template que é utilizado para exibir informações de páginas ou posts.

<pre class="lang-html">&lt;php while (have_posts()) : the_post(); ?&gt;
   &lt;!-- Template Tags e conte&uacute;do --&gt;
&lt;php endwhile; ?&gt;
</pre>

Os passos são os seguintes:

  1. Primeiro o have_posts() checa se há posts para serem exibidos.
  2. Se houverem posts, o Loop começa. Enquanto o loop continuar a executar, tudo o que você colocar dentro dele será repetido para cada um dos posts exibidos. Por exemplo: links de comentários, data, autor, e etc.
  3. Se não houverem mais posts, a função have_posts() retorna false e então o loop pára de ser executado.

Dentro deste while vai sua estrutura com as Template Tags. Fica mais ou menos assim:

<pre class="lang-html">&lt;php while (have_posts()) : the_post(); ?&gt;
    &lt;?php the_content(); ?&gt;
&lt;?php endwhile; ?&gt;
</pre>

A Template Tag [the_content()][3] exibe o conteúdo do post. Vamos rechear mais este código:

<pre class="lang-html">&lt;php while (have_posts()) : the_post(); ?&gt;
    &lt;h1&gt;&lt;?php the_title(); ?&gt;&lt;/h1&gt;
    &lt;div id="texto"&gt;
        &lt;?php the_content(); ?&gt;
    &lt;/div&gt;
&lt;?php endwhile; ?&gt;
</pre>

Agora o conteúdo fica dentro de um div específico chamado #texto. E o Título do post foi colocado dentro de uma tag apropriada, H1.

Dentro deste loop você coloca tudo quanto é objeto que você queira que se repita em cada um dos posts que forem exibidos. Normalmente: data, autor, número de comentários, links para feeds ou qualquer outro elemento normal em blogs.

<pre class="lang-html">&lt;php while (have_posts()) : the_post(); ?&gt;
    &lt;h1&gt;&lt;?php the_title(); ?&gt;&lt;/h1&gt;
    &lt;div id="texto"&gt;
        &lt;?php the_content(); ?&gt;
       &lt;small&gt;&lt;?php the_time('F jS, Y') ?&gt; por &lt;?php the_author() ?&gt; &lt;/small&gt;
    &lt;/div&gt;
&lt;?php endwhile; ?&gt;
</pre>

Esse código puxa do banco: título do post, o conteúdo do post, o dia que foi publicado e o nome do autor. Recheando com mais códigos para inserir uma sidebar, cabeçalho e rodapé, já começamos a montar a estrutura de um site de verdade. Mesmo assim, o principal da informação do site, foi feito nestas poucas linhas.

[Se quiser, pegue o arquivo de exemplo aqui][4].

 [1]: http://codex.wordpress.org/The_Loop
 [2]: http://codex.wordpress.org/Template_Tags
 [3]: http://codex.wordpress.org/Template_Tags/the_content
 [4]: http://tableless.com.br/uploads/2008/04/exemplo-loop-wordpressphp.zip