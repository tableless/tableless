---
title: Custom Post Types no WordPress
author: Paulo Rodrigues
type: post
date: 2011-03-29
excerpt: Crie tipos de conteúdo diferentes, agregue taxonomias e adicione campos personalizados. Deixe o seu site cada vez mais personalizado, trabalhando a fundo com o WordPress como CMS.
url: /custom-post-types-wordpress/
tweetbackscheck:
  - 1356387863
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/custom-post-types-wordpress";s:7:"tinyurl";s:26:"http://tinyurl.com/4xnag2m";s:4:"isgd";s:19:"http://is.gd/XyqpeE";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503026190
categories:
  - Wordpress
tags:
  - 2011
  - custom post types
  - Wordpress

---
Custom Post Types é a função que manipula os tipos de conteúdo no WordPress, ou seja, pode-se criar conteúdos personalizados a partir da sua demanda. Isso é uma das provas mais concretas que temos hoje um CMS muito forte que não serve apenas para criar blog e/ou sites de pequeno porte.

### Criando Custom Post Types

Como o assunto é muito amplo, criarei com vocês um exemplo de Notícias. 

Em functions.php, adicione:

<pre class="lang-php">&lt;?php
	add_action('init', 'type_post_noticias');
 
	function type_post_noticias() { 
		$labels = array(
			'name' =&gt; _x('Not&iacute;cias', 'post type general name'),
			'singular_name' =&gt; _x('Not&iacute;cia', 'post type singular name'),
			'add_new' =&gt; _x('Adicionar Novo', 'Novo item'),
			'add_new_item' =&gt; __('Novo Item'),
			'edit_item' =&gt; __('Editar Item'),
			'new_item' =&gt; __('Novo Item'),
			'view_item' =&gt; __('Ver Item'),
			'search_items' =&gt; __('Procurar Itens'),
			'not_found' =&gt;  __('Nenhum registro encontrado'),
			'not_found_in_trash' =&gt; __('Nenhum registro encontrado na lixeira'),
			'parent_item_colon' =&gt; '',
			'menu_name' =&gt; 'Not&iacute;cias'
		);

		$args = array(
			'labels' =&gt; $labels,
			'public' =&gt; true,
			'public_queryable' =&gt; true,
			'show_ui' =&gt; true,			
			'query_var' =&gt; true,
			'rewrite' =&gt; true,
			'capability_type' =&gt; 'post',
			'has_archive' =&gt; true,
			'hierarchical' =&gt; false,
			'menu_position' =&gt; null,
'register_meta_box_cb' =&gt; 'noticias_meta_box',		
			'supports' =&gt; array('title','editor','thumbnail','comments', 'excerpt', 'custom-fields', 'revisions', 'trackbacks')
          );
 
register_post_type( 'noticias' , $args );
flush_rewrite_rules();
}
?&gt;
</pre>

Primeiro adicionamos a função **add_action**, que vai abrigar dois parâmetros, o gancho (aonde vai rodar a função) e a função callback (a função que vai ser chamada com as informações). É função **type\_post\_noticias** que vai armazenar as informações do post. A variável **$labels**, está indicando os valores para cada título.

A variável **$args** é onde vamos colocar as informações do post. Explico com mais detalhes abaixo.

  * **labels:** Indica a variável que contém as informações do label
  * **public:** determina se o conteúdo pode ser visto no painel de administração, por padrão é falso.
  * **publicly_queryable:** determina se a consulta pode ser realizada usando o argumento post_type, por padrão ele herda o valor do public.
  * **show_ui:** determina se telas de adicionar e editar o post devem ser adicionadas esse tipo de post, por padrão ele herda o valor do public.
  * **query_var:** evita consultas ou valores de sequência, por padrão é falso.
  * **rewrite:** reescrita do link, por padrão é verdadeiro.
  * **capability_type:** define o tipo de conteúdo que o tipo de post personalizado vai seguir, por padrão é post.
  * **has_archive:** permite os arquivos do tipo do post, por padrão é falso.
  * **hierarchial:** determina que o tipo do post é hierárquico (igual o das páginas), por padrão o valor é falso
  * **menu_position:** determina a ordem do menu, por padrão é null (ele ficará em baixo do menu dos comentários), mas pode receber esses seguintes valores 
      * **5** – Em baixo do menu Post;
      * **10** – Em baixo do menu mídia;
      * **20** – Em baixo do menu páginas;
      * **60** – Em baixo do primeiro separador;
      * **100** – Em baixo do segundo separador.
  * **register\_meta\_box_cb:** Retorna a função que chamará as caixas de meta para o formulário (irei explicar à frente).
  
    supports: determina os recursos aceitos para esse tipo de post, por padrão é vazio, por isso tem que definir, ele recebe esses valores:</p> 
      * **author:** o autor por uma área personalizada
      * **title:** inclui o título ao tipo do post
      * **editor:** inclui a área de conteúdo do post (VISUAL ou HTML) e uploader de mídia
      * **excerpts:** inclui o campo de resumo
      * **thumbnail:** determina se o tipo de post pode inlcuir miniatura de post (http://tableless.com.br/adicionando-post-thumbnail)
      * **comments:** inclui os comentários
      * **trackbacks:** inclui os trackbacks
      * **custom-fields:** inclui a baixa de Custom Fields e se os campos serão automaticamente salvos
      * **revisions:** inclui revisões (armazenadas ou exibidas)
      * **page-attributes:** inclui a caixa Page Attributes (são encontradas na inserção de páginas), contendo as opções de parent, template e menu order.

Para o registro do post, é necessário a função **register\_post\_type**, que abrigará dois parâmetros. No primeiro é definido o nome do post (de preferência coloque em letras minúsculas e sem espaço, uma slug) e o outro agregará as demais informações do post, neste caso, a variável $args.

### Criando Taxonomias

A taxonomia é uma forma de criar um tipo de categoria para o tipo de conteúdo.

Adicione em functions.php: 

<pre class="lang-php">&lt;?php
register_taxonomy(
"categorias", 
      "noticias", 
      array(            
      	"label" =&gt; "Categorias", 
            "singular_label" =&gt; "Categoria", 
            "rewrite" =&gt; true,
            "hierarchical" =&gt; true
)
);
?&gt;
</pre>

Com a função **register_taxonomy**, registramos uma nova taxonomia. O primeiro valor aonde será definido o nome da taxonomia (de preferência de letras minúsculas e sem espaço), o segundo valor é definido o nome do tipo de conteúdo registrado, onde essa taxonomia se agregará. No array, é definido informações já explicadas acima.

### Criando campos personalizados

Vamos trabalhar com a variável **register\_meta\_box** na criação de campos personalizados. Para essa variável, foi definido o valor **noticias\_meta\_box**, que será a nossa função callback, a função que vai ser chamada para a criação da meta. 

Em functions.php adicione:

<pre class="lang-php">&lt;?php
function noticias_meta_box(){        
        add_meta_box('meta_box_test', __('Meta Box'), 'meta_box_meta_test', 'noticias', 'side', 'high');
}
?&gt;
</pre>

Retornamos a função definida para a criação de meta box, dentro dela definimos na função add\_meta\_box, os argumentos respectivamente, são:

  * **$id:** o nome para o meta box, destinado para uso interno
  * **$title:** o título da caixa
  * **$callback:** a função que irá ser chamada para imprimir o conteúdo da caixa
  * **$page:** o tipo de post que vão existir esse meta, para aparecer em mais de um, coloque dentro de um array, ex: array(‘noticias’, ‘post’)
  * **$context:** em qual parte da página de edição ela vai está (normal, advanced ou side [lateral])
  * **$priority:** em qual altura a caixa deve aparecer dentro da seção (high [alta], normal, low[baixa), a depender do valor, caixas com prioridade maior ficará encima

Depois que definimos a meta, vamos agora retornar a função que vai imprimir o conteúdo da caixa:

<pre class="lang-php">&lt;?php
function meta_box_meta_test(){
      global $post;
      $metaBoxValor = get_post_meta($post-&gt;ID, 'valor_meta', true); 
?&gt;        
    &lt;label for="inputValorMeta"&gt;Valor: &lt;/label&gt;
    &lt;input type="text" name="valor_meta" id="inputValorMeta" value="&lt;?php echo $metaBoxValor; ?&gt;" /&gt;
&lt;?php
    }
?&gt;
</pre>

A função foi criada, dentro dela imprimi-se o que o Box vai conter. Para garantir que o campo retornado é necessário usar a função **get\_post\_meta**. Ela requer três argumentos: o ID do post, o nome do campo (se possível sem acentos e nem espaços) e um valor true/false determinando se a função deve retornar um valor individual ou não.

Por fim criaremos a função que vai salvar as alterações dos campos personalizados:

<pre class="lang-php">&lt;?php
    add_action('save_post', 'save_noticias_post');
    
    function save_noticias_post(){
        global $post;        
        	update_post_meta($post-&gt;ID, 'valor_meta', $_POST['valor_meta']);
    }
?&gt; 
</pre>

Inicialmente adicionamos a ação no gancho **save_post** com o retorno da função **save\_noticias\_post**. A função **update\_post\_meta** vai receber três argumentos, os dois primeiros serão iguais aos explicados na função **get\_post\_meta**, a única diferença que o ultimo argumento vai receber o valor alterado, caso seja alterado manualmente colocamos uma simples string com o outro valor. Neste caso a alteração será feita após o envio do formulário.

### Criando um LOOP personalizado

Vamos criar o LOOP personalizado de acordo com o tipo de post, caso ainda não tenha visto o que seja um LOOP, [veja][1]

Aonde queria que aparecesse a repetição, adicione:

<pre class="lang-php">&lt;?php 
$newsArgs = array( 'post_type' =&gt; 'noticias', 'posts_per_page' =&gt; 4);                   
                        
      $newsLoop = new WP_Query( $newsArgs );                  
                        
      while ( $newsLoop-&gt;have_posts() ) : $newsLoop-&gt;the_post();              ?&gt;
&lt;div class="news"&gt;                                
      	&lt;h1&gt;&lt;a href="&lt;?php the_permalink(); ?&gt;" title="&lt;?php the_title(); ?&gt;"&gt;&lt;?php the_title(); ?&gt;&lt;/a&gt;&lt;/h1&gt;
            &lt;p&gt;&lt;strong&gt;&lt;?php the_time('F jS, Y') ?&gt;&lt;/strong&gt; by &lt;?php the_author_posts_link() ?&gt;&lt;/p&gt;
           	&lt;p&gt;&lt;?php the_content(); ?&gt;&lt;/p&gt;
&lt;p&gt;&lt;?php echo get_the_term_list( $post-&gt;ID, 'categorias', 'Categorias: ', ' '); ?&gt;&lt;/p&gt;
            &lt;p&gt;Retornando o campo personalizado: &lt;?php echo get_post_meta($post-&gt;ID, 'valor_meta', true); ?&gt;&lt;/p&gt;
&lt;/div&gt;
&lt;?php endwhile; ?&gt;

</pre>

O único termo desconhecido no Loop é a função **get\_the\_term_list**, que vai retornar a taxonomia para o post. O primeiro argumento é o valor do ID do post, o segundo valor é o nome definido da taxonomia, o terceiro valor é o que vai retonar antes de retornar as taxonomias e o último o separador.

Não há dificuldade, o segredo está na variável **$newsArgs**, que é aonde você vai definir as opções da repetição, ele pode receber mais argumentos, que você pode ver em: http://codex.wordpress.org/Function\_Reference/WP\_Query

Para visualizar um post, editamos as informações no arquivo **single.php** do nosso tema, quando temos um Custom Post Type, por padrão ele lê com essa página, caso queria ter uma pagina só para o tipo de post, você pode uma nova página chamada **single-{slug}.php**, ou seja, essa slug seria trocada pelo nome do Custom Post Type, no nosso caso, **single-noticias.php**.

### Feeds para tipos de post personalizado

Se seu site existe muitos leitores via feed e você quer mostrar o conteúdo personalizado, como fazer? Lendo um livro, WordPress 3 Básico (livro que indico para iniciantes ou desenvolvedores natos), achei essa solução, muito simples. 

Em functions.php, adicione:

<pre class="lang-php">&lt;?php
add_filter('pre_get_posts', 'postsfeed');
    
    function postsfeed($query){
        if( is_feed() ){
            $query-&gt;set('post_type', array('post', 'noticias'));
        }
        return $query;
    }
?&gt;

</pre>

No código vamos adicionar o filtro para a consulta de conteúdo para o Feed, você pode adicionar inúmeros conteúdos personalizados.

### Reduzindo o código

Existe mesmo a necessidade para registrar o Custom Post Type a quantidade de argumentos que foi mostrado? Não.

Neste artigo fez questão de mostrar a maioria das variáveis, mas você pode reduzir o código ainda mais em futuras alterações. Em vez de registrar o seu conteúdo com aquele código enorme, pode-se substituir por:

<pre class="lang-php">&lt;?php
add_action('init', 'type_post_noticias');
 
	function type_post_noticias() { 
		$labels = array(
			'name' =&gt; _x('Not&iacute;cias', 'post type general name'),
			'singular_name' =&gt; _x(Not&iacute;cia', 'post type singular name')
		);

		$args = array(
			'labels' =&gt; $labels,
			'public' =&gt; true,			
			'register_meta_box_cb' =&gt; 'noticias_meta_box',
			'supports' =&gt; array('title','editor','thumbnail','comments', 'excerpt', 'custom-fields', 'revisions', 'trackbacks')
          );
 
	register_post_type( 'noticias' , $args );
	flush_rewrite_rules();  
?&gt; 
</pre>

Ambas as formas estão corretas.

 [1]: http://tableless.com.br/o-loop-do-wordpress "O Loop do WordPress - Tableless"