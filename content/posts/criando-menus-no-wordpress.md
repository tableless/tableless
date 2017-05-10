---
title: Criando Menus no WordPress
author: Paulo Rodrigues
type: post
date: 2011-03-02
excerpt: Aprenda a adicionar menus e edite no seu próprio painel de administração com as páginas ou links que você quer
url: /criando-menus-no-wordpress/
tweetbackscheck:
  - 1356403209
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/criando-menus-no-wordpress";s:7:"tinyurl";s:26:"http://tinyurl.com/3sj7gkg";s:4:"isgd";s:19:"http://is.gd/AiwIyM";}'
twittercomments:
  - 'a:6:{i:144482084331847683;s:7:"retweet";i:145087211413569536;s:7:"retweet";i:153796274972393472;s:7:"retweet";i:164006827166670849;s:7:"retweet";i:164005868462030848;s:7:"retweet";i:164005767307997185;s:7:"retweet";}'
tweetcount:
  - 8
dsq_thread_id: 503040032
categories:
  - Artigos
  - Técnicas e Práticas
  - Wordpress
tags:
  - 2011
  - descrição
  - menu
  - Na Prática
  - registrando menus
  - Wordpress

---
Depois da versão 3.0, a criação de menus no WordPress tornou-se muito importante, pois se utiliza um gerenciador para reproduzir as informações do menu. No menu, pode-se criar links, integrar páginas e páginas de arquivo.

### Habilitando e registrando o menu

Em functions.php do seu tema, adicione: 

[cce lang=&#8221;php&#8221;]
  
if ( function\_exists( &#8216;register\_nav_menu&#8217; ) ) {
	  
register\_nav\_menu( &#8216;meu_menu&#8217;, &#8216;Este é meu primeiro menu&#8217; );
	  
register\_nav\_menu( &#8216;segundo_menu&#8217;, &#8216;Este é meu segundo menu&#8217; );
  
}
  
[/cce]

De início, verificamos a função register\_nav\_menu. Dentro da função, abrigamos dois parâmetros, que são: nome do menu (de preferência sem espaços e letras minusculas) e a descrição do menu. Ambos são obrigatórios nesta função. 

Essa função já habilita o suporte para os menus.

### Retornando o menu

Adicione o seguinte código onde queira que o retornasse o menu:

[cce lang=&#8221;php&#8221;]
  
wp\_nav\_menu( array(
	  
&#8216;menu&#8217; => &#8216;meu_menu&#8217;,
	  
&#8216;theme\_location&#8217; => &#8216;meu\_menu&#8217;,
	  
&#8216;container&#8217; => &#8216;div&#8217;,
	  
&#8216;container\_class&#8217; => &#8216;classe\_do_container&#8217;,
	  
&#8216;container\_id&#8217; => &#8216;id\_do_container&#8217;,
	  
&#8216;menu\_class&#8217; => &#8216;classe\_do_menu&#8217;,
	  
&#8216;echo&#8217; => true,
	  
&#8216;menu\_id&#8217; => &#8216;id\_do_menu&#8217;,
	  
&#8216;before&#8217; => &#8221;,
	  
&#8216;after&#8217; => &#8221;,
	  
&#8216;link_before&#8217; => &#8221;,
	  
&#8216;link_after&#8217; => &#8221;,
	  
&#8216;depth&#8217; => 0,
	  
&#8216;walker&#8217; => &#8221;,
  
) );
  
[/cce]

Como perceberam, a função **wp\_nav\_menu** recebe alguns parâmetros, para não haver dúvidas, explico melhor abaixo. 

  * **menu:** O nome do menu em que deseja retornar (valor determinado na função register_menu)
  * **theme_location:** Onde vai está localizado o menu (valor determinado na função register_menu)
  * **container:** Se alguma tag irá envolver a lista do menu
  * **container_class:** Classes do container 
  * **container_id:** O ID do container
  * **menu_class:** Classes da lista do menu
  * **menu_id:** O ID da lista do menu
  * **echo:** Usado para retorno do menu, em uma vez que seu valor seja falso, o menu não será retornado ou visível.
  * **before:** Se algum elemento entrará antes do menu
  * **after:** Se algum elemento entrará depois do menu
  * **link_before:** Se algum elemento entrará antes do link
  * **link_after:** Se alguém elementro entrará depois do menu
  * **depth:** Quantos níveis de hierarquia devem ser incluídos
  * **walker:** Objeto para personalização do menu

### Habilitando descrição

Para terminar a explicação, os Menus do WordPress contém uma opção para descrição nos menus. É uma forma melhor de explorar o conteúdo e também explicar um pouco mais o parâmetro walker, que ficou um pouco difícil de se entender.

Primeiro, ative a opção de descrição desta forma: Abra a seção de menus no painel de administração e vá a Screen Options (Opções de tela) e ative a opção Description (Descrição)

[<img src="http://tableless.com.br/uploads/2011/02/ativando-descricao-300x80.png" alt="" width="300" height="80" class="alignnone size-medium wp-image-3099" srcset="uploads/2011/02/ativando-descricao-300x80.png 300w, uploads/2011/02/ativando-descricao.png 324w" sizes="(max-width: 300px) 100vw, 300px" />][1]

Vamos personalizar o menu para receber as informações de descrição, adicione em functions.php: 

[cce lang=&#8221;php&#8221;]
      
/\* Código por: http://www.kriesi.at/archives/improve-your-wordpress-navigation-menu-output \*/
      
class descricao\_walker extends Walker\_Nav_Menu
  
{
        
function start_el(&$output, $item, $depth, $args)
        
{
             
global $wp_query;
             
$indent = ( $depth ) ? str_repeat( &#8220;\t&#8221;, $depth ) : &#8221;;

$class_names = $value = &#8221;;

$classes = empty( $item->classes ) ? array() : (array) $item->classes;

$class\_names = join( &#8216; &#8216;, apply\_filters( &#8216;nav\_menu\_css\_class&#8217;, array\_filter( $classes ), $item ) );
             
$class\_names = &#8216; class=&#8221;&#8216;. esc\_attr( $class_names ) . &#8216;&#8221;&#8216;;

$output .= $indent . &#8216;

  * ID . &#8216;&#8221;&#8216; . $value . $class_names .&#8217;>&#8217;; 
    $attributes = ! empty( $item->attr\_title ) ? &#8216; title=&#8221;&#8216; . esc\_attr( $item->attr_title ) .'&#8221;&#8216; : &#8221;;
             
    $attributes .= ! empty( $item->target ) ? &#8216; target=&#8221;&#8216; . esc_attr( $item->target ) .'&#8221;&#8216; : &#8221;;
             
    $attributes .= ! empty( $item->xfn ) ? &#8216; rel=&#8221;&#8216; . esc_attr( $item->xfn ) .'&#8221;&#8216; : &#8221;;
             
    $attributes .= ! empty( $item->url ) ? &#8216; href=&#8221;&#8216; . esc_attr( $item->url ) .'&#8221;&#8216; : &#8221;;
    
    $prepend = &#8216;**&#8216;;
             
    $append = &#8216;**&#8216;;
             
    $description = ! empty( $item->description ) ? &#8216;
    
    &#8216;.esc_attr( $item->description ).&#8217;
    
    &#8216; : &#8221;; // aqui é aonde a informação está a descrição
    
    if($depth != 0)
             
    {
                       
    $description = $append = $prepend = &#8220;&#8221;;
             
    }
    
    $item_output = $args->before;
              
    $item_output .= &#8216;<a>&#8216;;<br /> $item_output .= $args->link_before .$prepend.apply_filters( &#8216;the_title&#8217;, $item->title, $item->ID ).$append;<br /> $item_output .= $description.$args->link_after; //aqui aonde a descrição estará sendo retornada<br /> $item_output .= &#8216;</a>&#8216;;
              
    $item_output .= $args->after;
    
    $output .= apply\_filters( &#8216;walker\_nav\_menu\_start\_el&#8217;, $item\_output, $item, $depth, $args );
              
    }
  
    }
  
    [/cce]
    
    No código, foi criado uma classe retorna todo o item do menu, ou seja, a <li>. Está comentado no código onde você vai encontrar os códigos da descrição. É necessário entender um pouco de PHP para alterar esse código e personalizar ainda mais o seu menu.
    
    Para retornar essa classe, vamos usar o walker do menu, altere o valor, assim:
    
    [cce lang=&#8221;php&#8221;]&#8217;walker&#8217; => new descricao_walker() [/cce]
    
    Você pode determinar o valor da descrição no mesmo lugar aonde você altere as informações do menu.
    
    [<img src="http://tableless.com.br/uploads/2011/02/adicionando-descricao-300x242.png" alt="" width="300" height="242" class="alignnone size-medium wp-image-3098" srcset="uploads/2011/02/adicionando-descricao-300x242.png 300w, uploads/2011/02/adicionando-descricao.png 418w" sizes="(max-width: 300px) 100vw, 300px" />][2]
    
    Fonte da descrição: [http://www.kriesi.at/archives/improve-your-wordpress-navigation-menu-output][3]

 [1]: http://tableless.com.br/uploads/2011/02/ativando-descricao.png
 [2]: http://tableless.com.br/uploads/2011/02/adicionando-descricao.png
 [3]: http://www.kriesi.at/archives/improve-your-wordpress-navigation-menu-output "Fonte da descrição"