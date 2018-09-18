---
title: Posts Formats do WordPress
authors: Paulo Rodrigues
type: post
date: 2011-05-18
excerpt: O WordPress teve sua última atualização para a versão 3.1, dentre as novidades, está a inclusão de post formats em tipos de conteúdo. Com essa função, você pode deixar o WordPress com um toque de Tumblr.
url: /posts-formats-do-wordpress/
tweetbackscheck:
  - 1356467878
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"https://tableless.com.br/posts-formats-do-wordpress";s:7:"tinyurl";s:26:"https://tinyurl.com/3d9lq9s";s:4:"isgd";s:19:"https://is.gd/wf5EOR";}'
twittercomments:
  - 'a:1:{i:162738452469780480;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503040240
categories:
  - Wordpress
tags:
  - 2011
  - tumblr
  - Wordpress

---
O WordPress depois de sua atualização para versão 3.1, trouxe uma função de Formato nos Posts, que consiste em personalizar a visualização do post. É uma funcionalidade para temas, que oferece uma lista de formatos que estão disponíveis. São suportados os seguintes formatos:

  * aside
  * gallery
  * link
  * image
  * quote
  * status
  * video
  * audio
  * chat

Esses formatos são padrões, até hoje não se tem maneiras para criar um novo tipo de formato. 

### Ativando o suporte aos Posts Formats

Para ativar o suporte, adicione este seguinte código no arquivo **functions.php** do seu tema:

[cc lang=&#8221;php&#8221;]<?php add_theme_support('post-formats', array('aside', 'gallery','link','image')); ?>[/cc]

Não é obrigatório usar todos os formatos, e sim os quais você achar necessário. Caso queria adicionar mais formatos, adicione dentro do array os formatos disponíveis na lista acima.

Com este código, só é adicionado o suporte para o conteúdo de Posts, caso queria adicionar em outros tipos de conteúdo, adicione o seguinte código:

[cc lang=&#8221;php&#8221;]<?php add_post_type_support( 'page', 'post-formats' ); ?>[/cc]

Essa função habilita o suporte para outros tipos de conteúdo, no primeiro parâmetro defini-se o nome do conteúdo e no segundo, o tipo de suporte. 

Após ativar o suporte, terás dentro da edição do seus posts, um espaço feito esse para edição dos Posts Formats.

<img src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2011/04/edicao.jpg" alt="" width="281" height="130" class="alignnone size-full wp-image-3669" />

### Personalizando o retorno dos formatos

Para especificar o suporte, utilizamos formatos padrões. Mas como ele vai ser visualizado, como ele vai ser interpretado, é você quem vai definir.

Um exemplo simples de manipulação dos formatos (como isso é um post, este código deve ser adicionado no loop) :

[cc lang=&#8221;php&#8221;]
  
<?php if ( has_post_format( 'link' )) : ?>


     
<a href="<?php echo get_the_content(); ?>&#8221; title=&#8221;

<?php the_title(); ?>&#8220;>

<?php the_title(); ?></a>


  
<?php elseif(has_post_format( 'image' )) : ?>


     
<img src="<?php echo get_the_content(); ?>&#8221; title=&#8221;

<?php the_title(); ?>&#8221; alt=&#8221;

<?php the_title(); ?>&#8221; />


  
<?php endif; ?>


  
[/cc]

A função **has\_post\_format**, é um tipo de [tag condicional][1] que verifica qual o tipo formato visualizado.

No exemplo acima, utilizei os dados enviados pelo content como um link para algum site ou link para leitura de imagem.

**Dica:** Se for usar este exemplo, antes de postar, utilize a aba de editor HTML para evitar qualquer tipo de formatação, e use **get\_the\_content** para retornar o que foi enviado pelo editor, para também evitar qualquer tipo de formatação e retornar somente a informação enviada.

Você pode personalizar este retorno das maneiras que quiser. Se for usar esta função, seja mais criativo possível, explorando o máximo que essa função tem para oferecer.

Caso tenha maiores dúvidas, consulte o [codex de Posts Formats][2]

 [1]: https://tableless.com.br/tags-condicionais-do-wordpress "Guia de Referência de Tags Condicionais | Tableless"
 [2]: https://codex.wordpress.org/Post_Formats "Codex de Posts Formats"