---
title: Requisições AJAX no WordPress
author: Guilherme Brero
type: post
date: 2016-05-20
url: /requisicoes-ajax-no-wordpress/
categories:
  - Wordpress

---
O objetivo deste artigo é tentar mostrar uma forma simples e bem completa (e melhor. Segura!) de trabalhar com requisições AJAX e WordPress.

<blockquote id="2e7e">
  <p>
    Obs. Mostrarei de forma genérica e com exemplos banais, o importante é entender o processo. 🙂
  </p>
</blockquote>

<p id="e69f">
  Como já trabalhei em muitos lugares e peguei muito freela pra fazer nessa vida, acabo esbarrando com códigos no mínimo questionáveis, outros muito bons também. Porém a questão de fazer requisições AJAX no WordPress sempre é um assunto delicado pois várias e várias vezes vi códigos em que a complexidade que o desenvolvedor fez o código não só é desnecessária como também é ineficaz e insegura.
</p>

Vamos ao que interessa!

Quando precisamos realizar uma consulta ao banco do WordPress para trazermos um conteúdo específico sem dar um refresh na página, logo corremos para fazer a tão maravilhosa requisição AJAX.

Já vi isso sendo feito de muitas formas diferentes, desde um arquivo na raiz do projeto com uma “query na mão” e sendo chamada diretamente dentro do código da página específica, já vi uns arquivos nos mais variados diretórios com um require\_once da vida no wp\_load e então fazendo os loops lá dentro e cuspindo o html e etc.

Não digo que a forma que vou mostrar agora seja a única forma correta de fazer, muito menos a melhor, porém é uma forma que está na documentação do WordPress e que fica bem simples de ser entendida e também menos complexa que as invenções que vemos por aí.

Todas as requisições AJAX em WordPress, devem ser feitas num arquivo único, diferenciando-as através de parâmetros. O arquivo correto para enviarmos nossas requisições, é o arquivo “<em class="markup--em markup--p-em">admin-ajax.php</em>” que fica localizado dentro da pasta wp-admin e que no código veremos de que forma chamamos este arquivo dinamicamente sem problemas através de uma função do WordPress.

Primeiro vamos criar um nonce para nossas requisições , jogar este nonce para uma variável global de Javascript para que possamos usá-la no nosso frontend e, após termos nosso nonce criado, vamos criar nossa função para buscar mais notícias. Ela é chamada através de uma action também. Veja como fica o código:

&nbsp;

<pre class="lang-php">//Adiciona um script para o WordPress
add_action( 'wp_enqueue_scripts', 'secure_enqueue_script' );
function secure_enqueue_script() {
  wp_register_script( 'secure-ajax-access', esc_url( add_query_arg( array( 'js_global' =&gt; 1 ), site_url() ) ) );
  wp_enqueue_script( 'secure-ajax-access' );
}

//Joga o nonce e a url para as requisições para dentro do Javascript criado acima
add_action( 'template_redirect', 'javascript_variaveis' );
function javascript_variaveis() {
  if ( !isset( $_GET[ 'js_global' ] ) ) return;

  $nonce = wp_create_nonce('mais_noticias_nonce');

  $variaveis_javascript = array(
    'mais_noticias_nonce' =&gt; $nonce, //Esta função cria um nonce para nossa requisição para buscar mais notícias, por exemplo.
    'xhr_url'             =&gt; admin_url('admin-ajax.php') // Forma para pegar a url para as consultas dinamicamente.
  );

  $new_array = array();
  foreach( $variaveis_javascript as $var =&gt; $value ) $new_array[] = esc_js( $var ) . " : '" . esc_js( $value ) . "'";

  header("Content-type: application/x-javascript");
  printf('var %s = {%s};', 'js_global', implode( ',', $new_array ) );
  exit;
}



add_action('wp_ajax_nopriv_mais_noticias', 'mais_noticias');
add_action('wp_ajax_mais_noticias', 'mais_noticias');

function mais_noticias() {
  if( ! wp_verify_nonce( $_POST['mais_noticias_nonce'], 'mais_noticias_nonce' ) ) {
    echo '401'; // Caso não seja verificado o nonce enviado, a requisição vai retornar 401
    die();
  }
  //Busca os dados que queremos
  $args = array(
    'post_type' =&gt; 'noticias',
    'paged' =&gt; $_POST['paged']
  );
  $wp_query = new WP_Query( $args  );

  //Caso tenha os dados, retorna-os / Caso não tenha retorna 402 para tratarmos no frontend
  if( $wp_query-&gt;have_posts() ) {
    echo json_encode( $wp_query-&gt;posts );
  } else {
    echo 402;
  }
  exit;
}

</pre>

<p id="6b31" class="graf--p graf-after--figure">
  Com isso, se formos no nosso console do navegador e jogarmos js_global.mais_noticias_nonce, ele nos retornará um nonce como este: “<em class="markup--em markup--p-em">85c93a8183</em>”.
</p>

<blockquote id="f227">
  <p>
    Obs. Se ainda não sabe o que é nonce, e como ele funciona no WordPress veja neste link : <a class="markup--anchor markup--blockquote-anchor" href="https://blog.apiki.com/2015/09/21/wordpress-nonces-e-o-que-voce-precisa-saber-sobre-isso/" rel="nofollow">https://blog.apiki.com/2015/09/21/wordpress-nonces-e-o-que-voce-precisa-saber-sobre-isso/</a>
  </p>
</blockquote>

<p id="48b7">
  Note que usamos as actions wp_ajax e wp_ajax_nopriv, que respectivamente autorizam nossa aplicação para acessar a determinada função privadamente e publicamente.
</p>

Agora vamos ao frontend

Temos um botão para buscar mais notícias num archive nosso da vida:

vamos, por exemplo, capturar o click neste botão e a partir disso vamos buscar mais conteúdo via ajax:

<pre class="lang-javascript">jQuery(document).ready(function() {

  jQuery('.mais-noticias').on('click', function(e) {
      e.preventDefault();

      var dados_envio = {
        'mais_noticias_nonce': js_global.mais_noticias_nonce,
          'paged': 2,
          'action': 'mais_noticias'
      }

      jQuery.ajax({
          url: js_global.xhr_url,
          type: 'POST',
          data: dados_envio,
          dataType: 'JSON',
          success: function(response) {
              if (response == '401'  ){
                  console.log('Requisição inválida')
              }
              else if (response == 402) {
                  console.log('Todos os posts já foram mostrados')
              } else {
                  console.log(response)
              }
          }
      });


  });

})


</pre>

<p class="graf--p graf-after--figure">
  Javascript com jQuery (para efeito de exemplo com menos código. Fique a vontade para fazer ~do seu jeito~)
</p>

<p id="46a6" class="graf--p graf-after--figure">
  Desta forma, estamos enviando corretamente uma requisição ao WordPress e ele nos retornando um resultado que precisamos.
</p>

Como disse lá no começo, os exemplos são ‘toscos’ mas o que vale ), é entender como funciona esse fluxo e o que realmente é necessário enviar para podermos fazer de forma segura uma requisição.

Procurei focar realmente no processo.

<

p id=&#8221;f224&#8243; class=&#8221;graf&#8211;p graf-after&#8211;p graf&#8211;last&#8221;>Espero que tenha esclarecido alguma coisa pra você e qualquer dúvida ou sugestão pode postar nos comentários.