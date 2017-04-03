---
title: JavaScript e CSS no WordPress
author: Breno Alves
type: post
date: 2015-12-02
url: /javascript-e-css-no-wordpress/
categories:
  - Artigos
  - Wordpress

---
Você faz um front-end impecável, mas ao transformá-lo em um tema WordPress, o carregamento fica lento, os plugins não funcionam e ocorrem milhares de outros problemas? Saiba que você pode não estar utilizando seus scripts corretamente no WordPress.

Não se prenda ao termo! Neste post vamos usar &#8220;scripts&#8221; para qualquer JavaScript ou CSS que você queira adicionar ao seu tema ou plugin.

Ao adicionar um novo script na sua aplicação, você deve fazê-lo da forma adequada para que o WordPress cuide de todo o processo, não usando código desnecessário e impedindo conflitos entre sua aplicação e de terceiros (plugins).

## O problema

Imagine que você está desenvolvendo um tema usando jQuery. Mas ao mesmo tempo você vai usar alguns plugins que também usam o jQuery. Se você simplesmente adicionar diretamente o jQuery na sua página, sua aplicação vai estar carregando o jQuery que você adicionou e o dos plugins.

Nada bom, né? Sem contar que cada um pode estar usando uma versão diferente, gerar conflitos e aí o buraco fica mais fundo.

## A solução

O WordPress possui uma série de funções que permitem a você controlar o enfileiramento (enqueue) de scripts da sua aplicação. Com elas você pode adicionar, remover ou até mesmo registrar um script para uso posterior.

Ao desenvolver um tema, você precisa adicionar a função `<a href="https://codex.wordpress.org/Function_Reference/wp_head">wp_head()</a>` antes da tag `</head>` do seu tema e a função `<a href="https://codex.wordpress.org/Plugin_API/Action_Reference/wp_footer">wp_footer()</a>` antes da `</body>`. Dentro dessas funções é que a mágica acontece, como veremos mais a frente.

Como de costume no WordPress, as funções são simples e bastante auto-explicativas:
  
Acompanhe todos os comentários do código para não ter dúvidas. 😉

<pre class="prettyprint lang-php">// Identificador para o script
$handle = &#039;my-script&#039;;

// Caminho para o arquivo
$src = get_template_directory_uri() . &#039;/js/my-script.js&#039;;

// Array com os identificadores das dependências deste arquivo
$deps = array();

// Versão do arquivo
$ver = &#039;1.0.0&#039;;

// Imprimir no footer? Caso seja false, imprime no head.
$in_footer = true;


// Enfileira um script
wp_enqueue_script( $handle, $src, $deps, $ver, $in_footer );

// Desenfileira um script
wp_dequeue_script( $handle );
</pre>

Para CSS é tudo bem parecido e mudam apenas o sufixo das funções e uma opção.

<pre class="prettyprint lang-php">// Identificador para o script
$handle = &#039;my-style&#039;;

// Caminho para o arquivo
$src = get_template_directory_uri() . &#039;/css/my-style.css&#039;;

// Array de identificadores das dependências deste arquivo
$deps = array();

// Versão do arquivo
$ver = &#039;1.0.0&#039;;

// Atributo media da folha de estilos. Ex.: screen, print, all
$media = &#039;screen&#039;;


// Enfileira um style
wp_enqueue_style( $handle, $src, $deps, $ver, $media );

// Desenfileira um style
wp_dequeue_style( $handle );
</pre>

Você deverá usar estas funções no hook `wp_enqueue_scripts`, que é responsável por todo gerenciamentos de scripts públicos do seu WordPress (os que aparecem no front-end).

<pre class="prettyprint lang-php">&lt;?php

/*
 * Insira no functions.php ou em um arquivo separado.
 *
 * Não existe uma action específica para styles (wp_enqueue_styles).
 * Você deverá adicionar todas as funções aqui mesmo.
 */
function theme_scripts() {
	// Suas funções de enqueue vão aqui.
}
add_action( &#039;wp_enqueue_scripts&#039;, &#039;theme_scripts&#039; );
</pre>

Você também tem o `<a href="https://codex.wordpress.org/Plugin_API/Action_Reference/admin_enqueue_scripts">admin_enqueue_scripts</a>` e `<a href="https://codex.wordpress.org/Plugin_API/Action_Reference/login_enqueue_scripts">login_enqueue_scripts</a>` caso queira adicionar scripts ao admin e a tela de login respectivamente.

O WordPress já possui também vários [scripts embutidos por padrão][1] e para usar qualquer um deles, basta usar a função adequada com o identificador do script.

Uma das recomendações é sempre dar prioridade ao uso desses scripts que já vêm embutidos (sem colocar jQuery no braço, hein galera!) pois assim garantimos que não teremos problemas com a maior parte dos plugins do repositório do WordPress.

Poderíamos, por exemplo, adicionar o jQuery como dependência de `my-script`.

<pre class="prettyprint lang-php">&lt;?php

// Identificador
$handle = &#039;my-script&#039;;

// Caminho para o arquivo
$src = get_template_directory_uri() . &#039;/js/my-script.js&#039;;

// Array com o identificador do jQuery embutido por padrão
$deps = array( &#039;jquery&#039; );

// Versão
$ver = &#039;1.0.0&#039;;

// Imprime no footer (boa prática)
$in_footer = true;


// Enfileira o script
wp_enqueue_script( $handle, $src, $deps, $ver, $in_footer );
</pre>

Ou até mesmo enfileirarmos os dois (seguirá sempre a ordem de chamada das funções).

<pre class="prettyprint lang-php">&lt;?php

// Um plugin já registrado pode ser enfileirado, usando apenas o seu identificador
wp_enqueue_script( 'jquery' );
wp_enqueue_script( $handle, $src, $deps, $ver, $in_footer );
</pre>

Ambos os casos farão com que o WordPress adicione uma tag `<script>` para o jQuery e outra para `my-script`. E caso algum outro plugin já esteja usando o jQuery, o WordPress cuidará de adicioná-lo apenas uma vez.

Você também pode [registrar][2] ou [desregistrar][3] um script ou folha de estilo que ficará disponível para ser usado a qualquer momento por qualquer plugin ou tema.

Os parâmetros são os mesmos da função de enqueue:

<pre class="prettyprint lang-php">&lt;?php

/*
 * Ao registrar um script, você poderá
 * enfileirá-lo usando apenas o seu identificador.
 */
wp_register_script( $handle, $src, $deps, $ver, $in_footer );
wp_enqueue_script( 'my-script' );

// Desregistra o script
wp_deregister_script( 'my-script' );
</pre>

E combinando o uso dessas funções com as [tags condicionais][4] do WordPress, você pode melhorar muito a performance das suas páginas. Você pode criar folhas de estilo específicas para cada template e carregá-las somente quando for necessário.

<pre class="prettyprint lang-php">&lt;?php

if ( is_page() ) {
	// Essa folha de estilos será carregada apenas nos templates de páginas
	wp_enqueue_style( 'my-page-style' );
}
</pre>

Bem tranquilo, né?
  
Apenas tome cuidado para não exagerar! Não saia criando uma folha de estilos para cada página. Lembre-se que usar o cache dos navegadores é sempre muito importante, além de ajudar a reduzir custos em alguns casos.

Também vale fazer uma análise da aplicação e pensar um pouquinho em [Atomic Design][5] para componentizar melhor seu CSS.

 [1]: https://codex.wordpress.org/Function_Reference/wp_enqueue_script#Default_Scripts_Included_and_Registered_by_WordPress
 [2]: https://codex.wordpress.org/Function_Reference/wp_register_script
 [3]: https://codex.wordpress.org/Function_Reference/wp_deregister_script
 [4]: https://codex.wordpress.org/Conditional_Tags
 [5]: http://tableless.com.br/o-que-e-design-atomic/