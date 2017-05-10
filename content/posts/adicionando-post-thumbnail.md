---
title: Adicionando Post Thumbnail
author: Paulo Rodrigues
type: post
date: 2011-01-17
excerpt: O WordPress depois de sua versão 2.9 disponibilizou uma funcionalidade de Post Thumbnails. Essa funcionalidade é uma característica do tema que é uma miniatura da imagem de determinado post, pode ser usado em Páginas, Posts ou até Custom Post Types.
url: /adicionando-post-thumbnail/
tweetbackscheck:
  - 1356447903
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/adicionando-post-thumbnail";s:7:"tinyurl";s:26:"http://tinyurl.com/3tbd7fv";s:4:"isgd";s:19:"http://is.gd/Fxkxey";}'
twittercomments:
  - 'a:3:{i:35055199420809216;s:7:"retweet";i:35050134052151296;s:7:"retweet";i:35049122742411265;s:7:"retweet";}'
tweetcount:
  - 6
dsq_thread_id: 503039918
categories:
  - Wordpress
tags:
  - 2011
  - custom post types
  - post thumbnail
  - posts
  - thumb
  - Wordpress

---
### Ativando o suporte ao Post Thumbnails em seu tema

Antes de qualquer coisa, volto a lembrar que essa característica é do tema. Pode ser que alguns autores não ativem esse suporte. Para iniciar, adicione este seguinte código no arquivo functions.php:

[cc lang=&#8221;php&#8221;]

[/cc] 

Para ativar o suporte só é necessário este código. Bacana, né? O WordPress faz com que em poucas linhas de código possamos obter soluções significantes.

A condição verifica se a função &#8216;add\_theme\_support&#8217; existe, caso ela exista, adicionamos um suporte ao nosso tema, que é o Post Thumbnails.

Você pode adicionar esse suporte para outros tipos de posts ou até especificar aonde quer adicionar esse suporte:

[cc lang=&#8221;php&#8221;]
   
[/cc] 

No código fizemos o mesmo processo do início, porém especificamos tipos de posts diferentes. Ao contrário do post de cima, que só adicionaria em um tipo de post.

### Customizando as Thumbnails

Esse suporte trouxe várias funções para que possamos personalizar ainda mais o nosso Post Thumbnail. Você pode estipular um valor padrão para todas as imagens, como também pode criar um novo &#8220;estilo&#8221; para as imagens, vejamos:

[cc lang=&#8221;php&#8221;]
   
[/cc] 

Neste código personalizamos as nossas Thumbnails, com a função `set_post_thumbnail_size()` definimos um valor padrão para todas elas, os valores estipulados na função representa a largura e altura respectivamente e o valor TRUE, é destinado para o corte da imagem (crop), caso seja ativado sua imagem será cortada sem distorcê-la e você não precisará usar scripts para isso.

Com a função `add_image_size`, definimos um valor personalizado, os valores representam o nome do campo personalizado, largura, altura e o TRUE significa o crop. Lembrando, com essa função você apenas está definindo as caracteristicas de uma imagem personalizada.

### Adicionando o Thumbnail

Por fim vamos adicionar o Thumbnail em nosso post, adicione o seguinte código na página onde está seu Post, Loop ou aonde queria botar a imagem:

[cc lang=&#8221;php&#8221;]
	  
<?php
		  
//verifica se existe alguma thumbnail para o post
		  
if(has\_post\_thumbnail()){
			  
the\_post\_thumbnail(); //retorna o thumbnail para página
		  
}else{
			  
//caso não tenha nenhuma thumbnail, retorna uma imagem padrão
			  
echo '<img alt="Sem Thumbnail" />&#8216;;
		  
}
	  
?>
			  
[/cc]

Caso você queria adicionar o valor que definimos em algum add\_image\_size, faça isso:

[cc lang=&#8221;php&#8221;]
	  
<?php
		  
//verifica se existe alguma thumbnail para o post
		  
if(has\_post\_thumbnail()){
			  
the\_post\_thumbnail('thumb-post'); //retorna o thumbnail para página especificando o nome do campo personalizado
		  
}else{
			  
//caso não tenha nenhum thumbnail, retorna uma imagem padrão
			  
echo '<img alt="Sem Thumbnail" />&#8216;;
		  
}

//caso não queria que retorne nenhuma imagem padrão, retire o ELSE da condição
	  
?>
			  
[/cc]

Nos códigos acima adicionamos o thumbnail na página, a condição verifica se existe algum thumbnail, se existir, ele retorna a imagem. Quando você não define nenhum valor personalizado com o `add_image_size` ou até dentro da função, ele retorna com o valor que está definido `set_post_thumbnail_size`.

Ainda no código acima, adicionei um ELSE, para caso não tenha nenhuma imagem no Post Thumbnail, ele retorne com uma imagem padrão, que vai ficar ao seu critério.

### Código Final

#### functions.php

[cc lang=&#8221;php&#8221;]

[/cc] 

#### pagina-onde-vai-aparecer-o-thumb.php

[cc lang=&#8221;php&#8221;]
	  
<?php
		  
//verifica se existe algum thumbnail para o post
		  
if(has\_post\_thumbnail()){
			  
the\_post\_thumbnail('thumb-post'); //retorna o thumbnail para página especificando o tipo da imagem
		  
}else{
			  
//caso não tenha nenhuma thumbnail, retorna uma imagem padrão
			  
echo '<img alt="Sem Thumbnail" />&#8216;;
		  
}

//caso não queria que retorne nenhuma imagem padrão, retire o ELSE da condição
	  
?>
			  
[/cc]