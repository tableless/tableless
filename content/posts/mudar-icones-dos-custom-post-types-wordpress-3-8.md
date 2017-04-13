---
title: Mudar ícones dos Custom Post Types no WordPress 3.8
author: Julian Leno
type: post
date: 2014-01-13
excerpt: Como atualizar os ícones do Custom Post Types do novo Wordpress.
url: /mudar-icones-dos-custom-post-types-wordpress-3-8/
categories:
  - Wordpress
tags:
  - aprenda
  - desenvolvimento
  - desenvolvimento web
  - Na Prática
  - Técnicas e Práticas
  - tutorial
  - Wordpress

---
No dia 12 de Dezembro a Equipe do WordPress liberou a sua mais nova versão, o **WordPress 3.8 Parker**, que é uma referência ao **Charlie Parker**, grande saxofonista de Jazz. Visualmente a versão 3.8 do WordPress foi a que trouxe mais mudanças, a começar pela belíssima renovação de design do painel que também passou a ser responsivo e acessível por todos os dispositivos móveis, o que é um grande avanço, já que não será mais preciso usar os aplicativos móveis para fazer moderação e criação de posts.

[<img class="size-full wp-image-40235 aligncenter" alt="overview" src="http://tableless.com.br/uploads/2014/01/overview.jpg" srcset="uploads/2014/01/overview.jpg 623w, uploads/2014/01/overview-329x101.jpg 329w, uploads/2014/01/overview-588x182.jpg 588w" sizes="(max-width: 623px) 100vw, 623px" />][1]

A fonte do Painel agora é a **Open Sans** importada do <a title="Open Sans" href="http://www.google.com/fonts/specimen/Open+Sans" target="_blank">Google Web Fonts</a> e foram criados 8 novos temas super coloridos e vibrantes (em um próximo artigo iremos ver como mudar a cor desses temas) para deixar a sua experiencia de uso mais agradável e única e como de costume foi lançado um novo tema padrão: <a title="Novo tema padrão do WordPress 3.8" href="http://twentyfourteendemo.wordpress.com/" target="_blank"><strong>Twenty Fourteen</strong></a> além de novos ícones no menu.

<p class="aligncenter">
  <a href="http://tableless.com.br/uploads/2014/01/colors1.png"><img class=" wp-image-40238 aligncenter" alt="colors" src="http://tableless.com.br/uploads/2014/01/colors1.png" width="559" height="398" srcset="uploads/2014/01/colors1.png 932w, uploads/2014/01/colors1-235x168.png 235w, uploads/2014/01/colors1-435x310.png 435w" sizes="(max-width: 559px) 100vw, 559px" /></a>
</p>

Esses novos ícones são do pacote **Dashicons**, um pacote de [font para ícones][2] que foi incorporada ao WordPress. Sua vantagem é a responsividade, já que o ícone se adapta a todo tamanho de tela sem serrilhar, é mais fácil de manipular a cor, posição e tamanho via CSS, o que torna sua aparência mais agradável. quem já acompanha o **[Tableless][3]** e lê os artigos do Mestre Jedi **[Diego Eis][4]** sabe bem disso, não é?

E para quem usa [Custom Post Types][5] no WordPress pode ter notado o sumiço dos ícones (ou quer atualizá-los), pois os Custom Post Types manipulam o conteúdo do WordPress possibilitando que você personalize-o a partir da sua necessidade em um projeto, criando por exemplo um Portfólio personalizado em seu site, um Cadastro de Clientes e etc, as possibilidades são infinitas. Sabendo disso o nome Custom Post Types passa até a ficar estranho, pois o WordPress quebrou esse limite de somente paginas e posts e agora manipula todo tipo de conteúdo, é Você quem manda! Se Você quiser saber mais sobre o assunto, leia esse excelente artigo aqui do Tableless: [Custom Post Types no WordPress][6].

## Vamos à Prática

E agora Como adicionar esses novos ícones ao meu Custom Post Types? Eu já vi algumas poucas <del datetime="2014-01-07">gambiarras</del> soluções na internet e não achei nada conveniente. Logo descobri que era mais fácil do que eu imaginava e resolvi escrever este pequeno tutorial para mostrar o quão fácil é trocar o ícone de seu Custom Post Type por um novo e lindo ícone.

A Primeira coisa que se deve fazer é acessar seu arquivo _functions.php_ e editar uma linha da função que cria o Custom Post Types (Nesse momento você deve ter plena certeza do que está fazendo, pois qualquer movimento errado em seu arquivo functions.php pode fazer seu site <del datetime="2014-01-07">explodir</del> sair do ar).

Nesse exemplo é a linha 7, onde está escrito: **menu_icon**

<pre class="lang-php">$args = array(
		'labels' =&gt; $labels,
		'public' =&gt; true,
		'publicly_queryable' =&gt; true,
		'show_ui' =&gt; true,
		'query_var' =&gt; true,
		'menu_icon' =&gt; '<!--?php bloginfo('template_url'); ?-->/images/meu-icone.png',
		'rewrite' =&gt; true,
		'capability_type' =&gt; 'post',
		'hierarchical' =&gt; false,
		'menu_position' =&gt; null,
		'supports' =&gt; array('title','editor','thumbnail')
	  );</pre>

Se seu Custom Post Types está com algo assim: ** &#8216;menu_icon&#8217; => null** , ou **não tem esse campo**, basta você adicionar dentro do array que está guardado na variável **$args** a linha** &#8216;menu_icon&#8217; => &#8221;** e agora vem a parte fácil. Você vai escolher seu novo ícone nesse site: <http://melchoyce.github.io/dashicons/> e copiar seu nome, por exemplo: **dashicons-wordpress** e coloca-lo entre aspas simples depois de** =>** ficando assim: **&#8216;menu_icon&#8217; => &#8216;dashicons-wordpress&#8217;.**

[<img class="size-full wp-image-40240 aligncenter" alt="dashicons" src="http://tableless.com.br/uploads/2014/01/dash.png" width="159" height="257" />][7]

Nessa imagem troquei o ícone padrão de posts e dos Custom Post Types (Projetos e Destaque) para o **dashicons-wordpress**.

Feito isto, basta conferir no seu painel seu novo ícone.

 [1]: http://tableless.com.br/uploads/2014/01/overview.jpg
 [2]: http://tableless.com.br/utilizando-icones-formato-font/ "Font icons – Utilizando ícones em formato de font"
 [3]: http://tableless.com.br/
 [4]: http://tableless.com.br/author/diego-eis/
 [5]: http://tableless.com.br/custom-post-types-wordpress
 [6]: http://tableless.com.br/custom-post-types-wordpress/
 [7]: http://tableless.com.br/uploads/2014/01/dash.png