---
title: Usando Meta Box em seu tema WordPress
author: Giovanni Keppelen
type: post
date: 2012-03-20
excerpt: Entenda como funcionam o Meta Box do Wordpress.
url: /usando-meta-box-em-seu-tema-wordpress/
tweetbackscheck:
  - 1356424670
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5161";s:7:"tinyurl";s:26:"http://tinyurl.com/6soofob";s:4:"isgd";s:19:"http://is.gd/CLTCQt";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 617871152
categories:
  - Wordpress
tags:
  - desenvolvimento
  - Meta Box
  - Wordpress

---
## O que são Meta Boxes?

Os Meta Boxes (Caixas de informações) foi implementado a partir da versão 2.5 do CMS, os Meta Boxes são aquelas caixas arrastáveis que estão presente na Dashboard, edição de um post, páginas, além de outros locais na área administrativa do WordPress.

Os Meta Boxes é uma maneira atraente para a tela do editor de post e evita forçar os usuários a confiar em <a title="Custom Post Type" href="http://tableless.com.br/custom-post-types-wordpress/" target="_blank">campos personalizados</a>. Se você já criou algum tipo de campo personalizado no WordPress, você provavelmente gostaria de adicionar algum campo.

Com os Meta Box e mais fácil. Imagine que você esteja criando um tema para um cliente que precise catalogar sua coleção de vinil. Você começa imediatamente olhar para o WordPress para ver como isso pode ser feito. Cada Post representa um Vinil, que é perfeito para adicionar imagem, titulo e descrição. Podemos usar também as categorias e marcar dentro do WordPress para que os organize. Mas vamos supor que o cara queira acrescentar mais um dado para catalogação? O WordPress não te dar essa opção por padrão a não ser que usemos o grande Meta Box.

## Usando o Meta boxes

Neste tutorial não iremos trabalhar em um arquivo functions.php. Que não é o lugar correto para ele. Se você está adicionando dados a uma mensagem, é provável que você quer que ele exista independentemente do seu projeto de front end. Como tal, você deve colocar esse código em algum lugar que não é dependente do seu design. Ex: Um arquivo de plugin.

Convenientemente o WordPress oferece uma função para adicionar os Meta Boxes a uma tela de administração, usando o seguinte &#8220;add\_meta\_box&#8221;. Abaixo um exemplo.

<pre class="lang-php">&lt;?php add_meta_box( $id, $title, $callback, $page, $context, $priority, $callback_args ); ?&gt;

</pre>

### Parâmetros

  * $id &#8211; (<a title="String" href="http://codex.wordpress.org/How_to_Pass_Tag_Parameters#String" target="_blank">String</a>) Identificador único (Obrigatório)
  * $title &#8211; (<a title="String" href="http://codex.wordpress.org/How_to_Pass_Tag_Parameters#String" target="_blank">String</a>) Titulo a ser exibido (Obrigatório)
  * $callback &#8211; (<a title="Callback" href="http://codex.wordpress.org/How_to_Pass_Tag_Parameters#Callback" target="_blank">Callback</a>) Função para exibir o conteúdo do Meta Boxes (Obrigatório) <a title="Exemplo Callback" href="http://codex.wordpress.org/Function_Reference/add_meta_box#Example" target="_blank">Exemplo</a>
  * $page &#8211; (<a title="String" href="http://codex.wordpress.org/How_to_Pass_Tag_Parameters#String" target="_blank">String</a>) Onde será exibido o Meta Boxes. Exemplos (<tt>'post'</tt>, <tt>'page'</tt>, <tt>'link'</tt>, or<tt>'custom_post_type' )</tt>
  * $context (<a title="String" href="http://codex.wordpress.org/How_to_Pass_Tag_Parameters#String" target="_blank">String</a>) Tela onde o box vai ser inserido.
  * $priority (<a title="String" href="http://codex.wordpress.org/How_to_Pass_Tag_Parameters#String" target="_blank">String</a>) Prioridade de inserção da caixa em relação as demais.
  * $callback_args (<a title="Array" href="http://codex.wordpress.org/How_to_Pass_Tag_Parameters#Array" target="_blank">array</a>) Determina a passagem de parâmetros a função callback.

Então, nosso **add\_meta\_box** será parecido com esse.

<pre class="lang-php">&lt;?php add_meta_box ( 'my-meta-box-id', 'Meu primeiro Meta Box', 'vinil_meta_box_vinil', 'post', 'normal', 'high' ); ?&gt;

</pre>

Não podemos simplesmente colocar em nosso arquivo plugin sozinho, se não vamos acabar na tela branca da morte ou o erro fatal PHP. Chamada para a função indefinida, por quê? Porque chamamos a função add\_meta\_box antes do WordPress ser carregado. Com isso precisamos fazer um gancho no WordPress, que faz parte da api de um plugin. Basicamente, as funções começam enganchando em uma ação do WordPress. Então vamos fazer nosso gancho add\_meta\_box em uma função, então conectar essa função ao add\_meta\_boxes, evitando o erro fatal. Nosso código para o Meta Boxes para tela de postagem ficará assim:

<pre class="lang-php">&lt;?php add_action( 'add_meta_boxes', 'vinil_meta_box_add' );

function vinil_meta_box_add() {

add_meta_box( 'my-meta-box-id', 'Meu primeiro Meta Box', 'vinil_meta_box_vinil', 'post', 'normal', 'high' ); }

?&gt;

</pre>

## Renderizando o Meta Box

O código acima é o suficiente para adicionar o Meta Box, mas agora temos que tornar a coisa mais legal. Vamos adicionar campos, apenas um formulário HTML misturado com um pouco de PHP para exibir os dados salvos. Não precisamos incluir as tags de formulário pois o WordPress já faz isso para a gente. 🙂 Lembre que a string passada como o $callback em add\_meta\_box? Agora vamos criar um função com o mesmo nome.

<pre class="lang-php">&lt;?php function vinil_meta_box_vinil() {

echo 'Conteúdo do meu primeiro Meta Box.'; }

?&gt;

</pre>

Agora vamos fazer o formulário, vamos adicionar vários campos para este Meta Box, 1 input, 1 select, 1 checkbox. Vamos começar com o input.

Na função

<pre class="lang-php">function vinil_meta_box_vinil() {

echo 'Conteúdo do meu primeiro Meta Box.'; }

?&gt;

</pre>

Vamos retirar o

<pre class="lang-php">echo 'Conteúdo do meu primeiro Meta Box';

</pre>

Para começar a fazer o formulario do Meta Box, ficando da seguinte forma:

<pre class="lang-php">function vinil_meta_box_vinil()
{
?&gt;
&lt;p&gt;
&lt;label for="texto_meta_box"&gt;Text Label&lt;/label&gt;
&lt;input type="text" name="texto_meta_box" id="texto_meta_box" /&gt;
&lt;/p&gt;
&lt;?php
}

?&gt;

</pre>

Mas e quanto a exibir os dados? Bem você verá a seguinte, vamos armazenar esses dados na tabela usando a função wp\_postmeta update\_post\_meta. Essas funções tem duas irmãs chamada get\_post\_meta e get\_post\_custom, que pega os dados de wp\_postmeta. O get\_post\_meta só peega dados de uma chave, enquanto get\_post\_custom pega tudo. Como estamos usando realmente apenas um campo, neste ponto, vamos usar o get\_post\_meta.

<pre class="lang-php">function vinil_meta_box_vinil()
{
$values = get_post_custom( $post-&gt;ID );
$text = isset( $values['texto_meta_box'] ) ? esc_attr( $values['texto_meta_box'][0] ) : '';
$selected = isset( $values['meta_box_select'] ) ? esc_attr( $values['meta_box_select'][0] ) : '';
$check = isset( $values['meta_box_check'] ) ? esc_attr( $values['meta_box_check'][0] ) : '';
wp_nonce_field( 'my_meta_box_nonce', 'meta_box_nonce' );
?&gt;
&lt;p&gt;
&lt;label for="texto_meta_box"&gt;Text Label&lt;/label&gt;
&lt;input type="text" name="texto_meta_box" id="texto_meta_box" /&gt;
&lt;/p&gt;

&lt;?php
}

?&gt;

</pre>

Agora vamos adicionar o DropDow em nosso Meta Box.

No drop-dow iremos usar uma das funções mais úteis no WordPress, o selected(). Ele compara o primeiro valor, os dados que salva, com o segundo atributo de valor, <option>. Se eles são os mesmos a função selected=&#8221;selected&#8221; que faz com o que o valor do drop down seja gravado. Mas você também pode usar o selected com botões de radio.

Ficando da seguinte forma:

<pre class="lang-php">function vinil_meta_box_vinil()
{
$values = get_post_custom( $post-&gt;ID );
$text = isset( $values['texto_meta_box'] ) ? esc_attr( $values['texto_meta_box'][0] ) : '';
$selected = isset( $values['meta_box_select'] ) ? esc_attr( $values['meta_box_select'][0] ) : '';
$check = isset( $values['meta_box_check'] ) ? esc_attr( $values['meta_box_check'][0] ) : '';
wp_nonce_field( 'my_meta_box_nonce', 'meta_box_nonce' );
?&gt;
&lt;p&gt;
&lt;label for="texto_meta_box"&gt;Text Label&lt;/label&gt;
&lt;input type="text" name="texto_meta_box" id="texto_meta_box" /&gt;
&lt;/p&gt;
&lt;p&gt;
&lt;label for="meta_box_select"&gt;Color&lt;/label&gt;
&lt;select name="meta_box_select" id="meta_box_select"&gt;
&lt;option value="red" &lt;?php selected( $selected, 'red' ); ?&gt;&gt;Vermelho&lt;/option&gt;
&lt;option value="blue" &lt;?php selected( $selected, 'blue' ); ?&gt;&gt;Azul&lt;/option&gt;
&lt;/select&gt;
&lt;/p&gt;
&lt;?php
}

?&gt;

</pre>

### Adicionando o Check box

<pre class="lang-php">function vinil_meta_box_vinil()
{
$values = get_post_custom( $post-&gt;ID );
$text = isset( $values['texto_meta_box'] ) ? esc_attr( $values['texto_meta_box'][0] ) : '';
$selected = isset( $values['meta_box_select'] ) ? esc_attr( $values['meta_box_select'][0] ) : '';
$check = isset( $values['meta_box_check'] ) ? esc_attr( $values['meta_box_check'][0] ) : '';
wp_nonce_field( 'my_meta_box_nonce', 'meta_box_nonce' );
?&gt;
&lt;p&gt;
&lt;label for="texto_meta_box"&gt;Text Label&lt;/label&gt;
&lt;input type="text" name="texto_meta_box" id="texto_meta_box" /&gt;
&lt;/p&gt;
&lt;p&gt;
&lt;label for="meta_box_select"&gt;Color&lt;/label&gt;
&lt;select name="meta_box_select" id="meta_box_select"&gt;
&lt;option value="red" &lt;?php selected( $selected, 'red' ); ?&gt;&gt;Vermelho&lt;/option&gt;
&lt;option value="blue" &lt;?php selected( $selected, 'blue' ); ?&gt;&gt;Azul&lt;/option&gt;
&lt;/select&gt;
&lt;/p&gt;
&lt;p&gt;
&lt;input type="checkbox" name="meta_box_check" id="meta_box_check" &lt;?php checked( $check, 'on' ); ?&gt; /&gt;
&lt;label for="meta_box_check"&gt;Don't Check This.&lt;/label&gt;
&lt;/p&gt;
&lt;?php
}

?&gt;

</pre>

Novamente o WordPress fornece a função checked(). Ela funciona exatamente como selected() comparando o primeiro valor com o segundo valor e repetindo para checked=&#8221;checked&#8221; se eles são o mesmo.

## Para finalizar vamos salvar nosso Meta Box

Para salvar nossos dados, vamos confiar em outro gancho: save_post. Isso funciona como o nosso gancho na ação acima:

<pre class="lang-php">&lt;?php add_action( 'save_post', 'vinil_meta_box_save' ); ?&gt;

</pre>

A função vinil\_meta\_box receberá um argumento, a ID do Post, e vai cuidar da limpeza e salvar todos os nossos dados.

Antes de podermos fazer qualquer coisa, no entanto, que temos que fazer 3 coisas: verificar se o Post esta auto salvando, verificar o valor único que criamos anteriormente, e verificar se o usuário atual pode realmente editar o post.

<pre class="lang-php">add_action( 'save_post', 'vinil_meta_box_save' );
function vinil_meta_box_save( $post_id )
{
if( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) return;

if( !isset( $_POST['meta_box_nonce'] ) || !wp_verify_nonce( $_POST['meta_box_nonce'], 'my_meta_box_nonce' ) ) return;

if( !current_user_can( 'edit_post' ) ) return;

}

</pre>

Agora as coisas divertidas: na verdade, salvar nossos dados. A regra número um, ao colocar qualquer coisa em seu banco de dados ou em seu site é não confiar no usuário. Mesmo se esse usuário é você. Para o efeito, antes de salvar os dados, queremos ter certeza de que não há nada malicioso lá. Felizmente WordPress fornece um monte de funções para validação de dados. Para isso vamos utilizar o esc\_attr(). E também vamos usar a função update\_post_meta para salvar os nossos dados. Leva três argumentos: a ID post, a chave de meta, e o valor.

<pre class="lang-php">add_action( 'save_post', 'vinil_meta_box_save' );
function vinil_meta_box_save( $post_id )
{
if( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) return;

if( !isset( $_POST['meta_box_nonce'] ) || !wp_verify_nonce( $_POST['meta_box_nonce'], 'my_meta_box_nonce' ) ) return;

if( !current_user_can( 'edit_post' ) ) return;

$allowed = array(
'a' =&gt; array(
'href' =&gt; array()
)
);

if( isset( $_POST['texto_meta_box'] ) )
update_post_meta( $post_id, 'texto_meta_box', wp_kses( $_POST['texto_meta_box'], $allowed ) );

if( isset( $_POST['meta_box_select'] ) )
update_post_meta( $post_id, 'meta_box_select', esc_attr( $_POST['meta_box_select'] ) );

$chk = ( isset( $_POST['meta_box_check'] ) && $_POST['meta_box_check'] ) ? 'on' : 'off';
update_post_meta( $post_id, 'meta_box_check', $chk );
}

?&gt;

</pre>

É isso, agora você deve ter um Meta Boxes funcionando em seu WordPress.

## Nosso arquivo fica assim:

<pre class="lang-php">&lt;?php
/*
Plugin Name: Meta Box
Plugin URI: http://bygiovanni.com.br
Description:
Version: 1.0
Author: Giovanni - Tableless
Author URI: http://bygiovanni.com.br
*/

//ADICIONANDO O META BOX
add_action( 'add_meta_boxes', 'vinil_meta_box_add' );
function vinil_meta_box_add()
{
add_meta_box( 'my-meta-box-id', 'Meu primeiro Meta Box', 'vinil_meta_box_vinil', 'post', 'normal', 'high' );
}

//FORMULARIO PARA SALVAS OS DADOS
function vinil_meta_box_vinil()
{
$values = get_post_custom( $post-&gt;ID );
$text = isset( $values['texto_meta_box'] ) ? esc_attr( $values['texto_meta_box'][0] ) : '';
$selected = isset( $values['meta_box_select'] ) ? esc_attr( $values['meta_box_select'][0] ) : '';
$check = isset( $values['meta_box_check'] ) ? esc_attr( $values['meta_box_check'][0] ) : '';
wp_nonce_field( 'my_meta_box_nonce', 'meta_box_nonce' );
?&gt;
&lt;p&gt;
&lt;label for="texto_meta_box"&gt;Text Label&lt;/label&gt;
&lt;input type="text" name="texto_meta_box" id="texto_meta_box" /&gt;
&lt;/p&gt;
&lt;p&gt;
&lt;label for="meta_box_select"&gt;Color&lt;/label&gt;
&lt;select name="meta_box_select" id="meta_box_select"&gt;
&lt;option value="red" &lt;?php selected( $selected, 'red' ); ?&gt;&gt;Vermelho&lt;/option&gt;
&lt;option value="blue" &lt;?php selected( $selected, 'blue' ); ?&gt;&gt;Azul&lt;/option&gt;
&lt;/select&gt;
&lt;/p&gt;
&lt;p&gt;
&lt;input type="checkbox" name="meta_box_check" id="meta_box_check" &lt;?php checked( $check, 'on' ); ?&gt; /&gt;
&lt;label for="meta_box_check"&gt;Don't Check This.&lt;/label&gt;
&lt;/p&gt;
&lt;?php
}

add_action( 'save_post', 'vinil_meta_box_save' );
function vinil_meta_box_save( $post_id )
{
if( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) return;

if( !isset( $_POST['meta_box_nonce'] ) || !wp_verify_nonce( $_POST['meta_box_nonce'], 'my_meta_box_nonce' ) ) return;

if( !current_user_can( 'edit_post' ) ) return;

$allowed = array(
'a' =&gt; array(
'href' =&gt; array()
)
);

if( isset( $_POST['texto_meta_box'] ) )
update_post_meta( $post_id, 'texto_meta_box', wp_kses( $_POST['texto_meta_box'], $allowed ) );

if( isset( $_POST['meta_box_select'] ) )
update_post_meta( $post_id, 'meta_box_select', esc_attr( $_POST['meta_box_select'] ) );

$chk = ( isset( $_POST['meta_box_check'] ) && $_POST['meta_box_check'] ) ? 'on' : 'off';
update_post_meta( $post_id, 'meta_box_check', $chk );
}

?&gt;

</pre>

Para saber mais sobre os Meta Box podem ver no Codex que também é uma ótima fonte de estudo para o WP. <a href="http://codex.wordpress.org/Function_Reference/add_meta_box" target="_blank">http://codex.wordpress.org/Function_Reference/add_meta_box</a>