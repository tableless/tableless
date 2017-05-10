---
title: Shortcodes
author: Paulo Rodrigues
type: post
date: 2011-01-18
excerpt: Um dos API’s mais importantes do WordPress, fácil de usar e customizar.
url: /shortcodes/
tweetbackscheck:
  - 1356394912
shorturls:
  - 'a:3:{s:9:"permalink";s:34:"http://tableless.com.br/shortcodes";s:7:"tinyurl";s:26:"http://tinyurl.com/3j9t5ok";s:4:"isgd";s:19:"http://is.gd/afFxDc";}'
twittercomments:
  - 'a:4:{i:154148694344728576;s:7:"retweet";i:153211795207757824;s:7:"retweet";i:153200260695605248;s:7:"retweet";i:153199207430373376;s:7:"retweet";}'
tweetcount:
  - 9
dsq_thread_id: 503039923
categories:
  - Wordpress
tags:
  - api
  - encurtador
  - shortcodes
  - Wordpress

---
Os shortcodes são abreviaturas no intuito de retornar o código desejado em uma única linha.

### Exemplos de Shortcodes

Um exemplo de shortcode: 

`[botao]Meu primeiro botão[/botao]`

Um exemplo de shortcode com parâmetros: 

`[botao cor=”vermelho” url=”http://tableless.com.br”]Site do Tableless[/botao]`

Essa é a melhor solução para quem desenvolve sites para terceiros e deseja criar elementos com rapidez.

### Criando um Shortcode

Para criar um shortcode, adicione o seguinte código em **functions.php**:

[cce lang=&#8221;php&#8221;]
  
<?php
  
add\_shortcode(&#8216;botao&#8217;, &#8216;botao\_shortcode&#8217;);

function botao_shortcode( $atts, $content = null ) {

extract(shortcode_atts(array(
        
&#8216;cor&#8217; => &#8216;verde&#8217;,
        
&#8216;url&#8217; => &#8221;,
     
), $atts ) );

return &#8216;[&#8216;.$content.&#8217;][1]{.botao'.esc_attr($cor).'}&#8216;;
  
}
  
?>
  
[/cce]

No código, a função **add_shortcode** registrar o shortcode e abriga dois parâmetros, o nome do shortcode (tag) e a função que vai manipular o shortcode respectivamente.

Após isso, criei a função que vai abrigar os parâmetros e retornar todo o shortcode. Analise bem esta parte, pois são elas que vão abrigar os parâmetros: 

[cce lang=&#8221;php&#8221;]
     
extract(shortcode_atts(array(
        
&#8216;cor&#8217; => &#8216;verde&#8217;,
        
&#8216;url&#8217; => &#8221;,
     
), $atts ) );
  
[/cce]

Nesta parte, a função shortcode_atts significa os atributos do shortcode, logo abaixo em um array, criaremos quais vão ser os parâmetros disponíveis. Por exemplo, criei um parâmetro de cor e outro de url, o valor que está atribuído ao parâmetro pode ser vazio ou um valor padrão, caso o parâmetro esteja vazio quando aplicarmos o shortcode.

[cce lang=&#8221;php&#8221;]
        
return &#8216;[&#8216;.$content.&#8217;][1]{.botao'.esc_attr($cor).'}&#8216;;
  
[/cce]

Este código retorna o shortcode, cada parâmetro é uma variável dentro da função, para retorná-las use, $nomedoparametro, a função esc_attr é própria do WordPress e serve para codificar um texto. 

Por último a variável $content, que serve para retornar o que está dentro da tag do shortcode, por exemplo:
  
\[cce lang=&#8221;html&#8221;\]\[botao\]Isso é o content\[/botao\]\[/cce\] 

### Retornando um Shortcode

Por fim, vamos retornar o shortcode: 

\[cce lang=&#8221;html&#8221;\]\[botao cor=”azul” url=”http://tableless.com.br”\]Site Tableless\[/botao\]\[/cce\]

Para adicionar esse código você precisa está no editor Visual, caso contrário ele não irá funcionar.

Caso você queria usar o shortcode em algum outro lugar diferente do post, é necessário usar uma função chamada do_shortcode, por exemplo: 

[cce lang=&#8221;php&#8221;]
  
<?php echo do_shortcode(‘[botao cor=”azul” url=”http://tableless.com.br”]Site Tableless [/botao]’); ?>
  
[/cce]

De brinde, vou disponibilizar o código em CSS, somente para que vocês tenham uma noção, caso precisem

[cc lang=&#8221;css&#8221;]
  
.botaoverde{
	  
background-color: green;
	  
text-decoration: none;
	  
color: #FFF;
	  
padding: 5px;
	  
margin: 0px 10px;
  
}

.botaoazul{
	  
background-color: blue;
	  
text-decoration: none;
	  
color: #FFF;
	  
padding: 5px;
	  
margin: 0px 10px;
  
}

[/cc]

 [1]: '.esc_attr($url).' "'.$content.'"