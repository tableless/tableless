---
title: Personalizando o painel de administração do WordPress
author: Dani Guerrato
type: post
date: 2013-07-03
excerpt: Aprenda a modificar o layout da dashboard de maneira simples para facilitar a navegação, personalizar a experiência do usuário e reforçar o branding.
url: /customizando-o-painel-de-administracao-do-wordpress/
dsq_thread_id: 1458641418
categories:
  - Artigos
  - Wordpress
tags:
  - 2013
  - dashboard wordpress
  - temas em wordpress
  - Wordpress

---
Você provavelmente já [conhece o WordPress][1] e já sabe [como criar seus próprios temas][2]. Mas isto não significa que o trabalho acabou. É possível &#8211; e extremamente recomendável &#8211; personalizar os elementos da interface do Painel de Administração para que ele se adeque as necessidades de cada marca.

#### Layouts únicos

Muitas vezes ao fazer a escolha entre utilizar um sistema de administração de conteúdo padrão ou projetar o seu próprio do zero o critério de desempate é a capacidade de personalização. Quando você cria um CMS, seja para um blog, um site ou uma loja, você está levando em conta todas as necessidades específicas daquele cliente. O mesmo não acontece com um sistema pronto. Mas muitas vezes não é preciso reinventar a roda. Com alguns recursos simples você pode transformar o layout de um administrador padrão como o WordPress em algo consistente com a identidade visual do seu projeto.

#### Melhor usabilidade

Muitas vezes nossos clientes não possuem um conhecimento muito grande em administração de conteúdo para a web e a visão do painel de controle pode ser meio intimidadora. O que parece simples e fácil para você na maioria das vezes é bem complicado para pessoas que não estão habituadas com ambiente de desenvolvimento. Criar elementos que facilitem o uso, adaptando a interface para a cultura / nível de conhecimento de cada empresa é fazer com que o usuário se sinta em casa.

#### Branding

Sua dashboard também pode ser uma extensão da sua marca. Logotipo, cores, tipografia, iconografia&#8230; Estes são alguns dos elementos que podem ser inseridos dentro do painel para criar uma experiência verdadeiramente única &#8211; mesmo dentro de um CMS padrão.

#### Menos dor de cabeça

Se nada disto te convenceu pense nos motivos egoístas. Se o seu administrador for mais simples de usar você vai receber menos e-mails / ligações / chamadas no Skype com reclamações, certo? O ganho de produtividade (e horas de sono) não tem preço.

Bem, vamos por a mão na massa!

## Um endereço para chamar de seu

Se você está habituado a utilizar o WordPress provavelmente já digita &#8220;/wp-login&#8221; ou &#8220;/wp-admin&#8221; após o endereço de qualquer site que utilize a plataforma para entrar na sua conta. Mas talvez para o seu cliente seria mais fácil de lembrar do endereço se a url tivesse um nome mais amigável como &#8220;/administrador&#8221; ou até mesmo apenas &#8220;/login&#8221;, certo?

Para isto vamos precisar editar o arquivo .htaccess. Este arquivo fica geralmente na pasta raíz do seu diretorio do WordPress. Dependendo das configurações do seu servidor ele pode estar oculto. Para modificar a url do seu painel de administração basta inserir esta linha no topo do seu arquivo (substituindo &#8220;seu-site&#8221; pela sua url):

<pre class="lang-php">RewriteRule ^login$ http://seu-site.com.br/wp-login.php [NC,L]</pre>

Agora basta acessar http://seu-site.com.br/login para entrar na sua conta WordPress.

## Acessando o functions.php

Grande parte do código que eu vou apresentar para vocês funciona a partir de mudanças no arquivo de funções do WordPress, o functions.php. Para acessar este arquivo em seu painel do WordPress clique no menu **Aparência**, **Editor** e em seguida **Funções do Tema** na barra lateral da direita. Pronto! Outra alternativa é localizar o arquivo no seu servidor através de FTP. O caminho até o arquivo normalmente é _/wp-content/themes/nome-do-tema/functions.php_ (Obviamente substituindo nome-do-tema pelo&#8230; bem, você já entendeu.) Lembre-se de sempre colocar as linhas de código entre as tags `<?php>`.

## A Tela de Login

A primeira impressão é a que fica. Ter um layout bacana para a tela de login é garantir que seu usuário fique impressionado desde o inicio.

### Inserindo seu logotipo

Um logotipo é uma parte fundamental de uma marca. Quanto maior a visibilidade que ele tiver, mais fixado ficará na mente das pessoas. Na página inicial do painel de administração acima do formulário de login temos o logo do WordPress.

<img class="alignnone size-full wp-image-37926" alt="wp-login" src="http://tableless.com.br/uploads/2013/06/wp-login.jpg" width="660" height="400" srcset="uploads/2013/06/wp-login.jpg 660w, uploads/2013/06/wp-login-277x168.jpg 277w, uploads/2013/06/wp-login-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Para deixar o sistema com a identidade visual da sua empresa o primeiro passo é substituir esta imagem pelo seu próprio logo. Crie um arquivo de imagem com o tamanho máximo de 323 pixels de largura por 67 pixels de altura.

<img class="alignnone size-full wp-image-37925" alt="wp-login-tableless" src="http://tableless.com.br/uploads/2013/06/wp-login-tableless.jpg" width="660" height="400" srcset="uploads/2013/06/wp-login-tableless.jpg 660w, uploads/2013/06/wp-login-tableless-277x168.jpg 277w, uploads/2013/06/wp-login-tableless-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

O logo do WordPress está como background de uma classe de CSS. Adicione a seguinte classe na sua folha de estilos e substitua o endereço pelo nome e caminho correto da imagem.

<pre class="lang-css">body.login div#login h1 a {
    background-image: url(/wp-content/themes/nome-do-tema/img/site-logo.png);
}</pre>

Opcionalmente é possível realizar esta modificação através do functions.php. Lembre-se de alterar o valor de padding-bottom para o que funcionar melhor no seu caso e modificar o nome e caminho da imagem.

<pre class="lang-php">// Custom WordPress Login Logo
function my_login_logo() { ?&gt;
   body.login div#login h1 a {
        background-image: url(/img/site-login-logo.png);
        padding-bottom: 30px;
   }

&lt;?php }
add_action( 'login_enqueue_scripts', 'my_login_logo' );</pre>

### Alterando o link do logotipo

Por padrão o logotipo da tela de login aponta para WordPress.org. Seria interessante trocar o link para seu próprio endereço. O snippet abaixo cuida desta tarefa. Você deve colar esta função no arquivo &#8211; você adivinhou &#8211; functions.php.

<pre class="lang-php">//Link na tela de login para a página inicial 
function my_login_logo_url() {
    return get_bloginfo( 'url' );
}
add_filter( 'login_headerurl', 'my_login_logo_url' );

function my_login_logo_url_title() {
    return 'Your Site Name and Info';
}
add_filter( 'login_headertitle', 'my_login_logo_url_title' );</pre>

### Criando seus próprios estilos

Não é possível editar o arquivo HTML core do WordPress, mas podemos modifica-lo completamente através de CSS. Existem duas opções: utilizar sua folha de estilos padrão ou criar uma especificamente para o seu tema. Dá para realizar diversas modificações nesta tela como mudança de background, tipografia, trocar as dimensões do logo, etc. Para isto cole este código no functions.php e altere para o caminho e nome da sua folha de estilos. No caso o arquivo se chama style-login.css

<pre class="lang-php">//Login Stylesheet
function my_login_stylesheet() { ?&gt;
    &lt;link rel="stylesheet" id="custom_wp_admin_css"  href="" type="text/css" media="all" /&gt;
&lt;?php }
add_action( 'login_enqueue_scripts', 'my_login_stylesheet' );</pre>

Segue uma lista de classes úteis para a personalização desta tela.

<pre class="lang-css">body.login {}
body.login div#login {}
body.login div#login h1 {}
body.login div#login h1 a {}
body.login div#login form#loginform {}
body.login div#login form#loginform p {}
body.login div#login form#loginform p label {}
body.login div#login form#loginform input {}
body.login div#login form#loginform input#user_login {}
body.login div#login form#loginform input#user_pass {}
body.login div#login form#loginform p.forgetmenot {}
body.login div#login form#loginform p.forgetmenot input#rememberme {}
body.login div#login form#loginform p.submit {}
body.login div#login form#loginform p.submit input#wp-submit {}
body.login div#login p#nav {}
body.login div#login p#nav a {}
body.login div#login p#backtoblog {}
body.login div#login p#backtoblog a {}</pre>

## Alterando o ícone da Dashboard

OK. Agora que você já modificou a aparência externa do seu administrador está na hora de alterar a aparência interna. O primeiro passo é o ícone do cabeçalho do seu painel de controle. Por padrão temos um pequeno W.

<img class="alignnone size-full wp-image-37922" alt="header-dashboard" src="http://tableless.com.br/uploads/2013/06/header-dashboard.jpg" width="660" height="26" srcset="uploads/2013/06/header-dashboard.jpg 660w, uploads/2013/06/header-dashboard-329x12.jpg 329w, uploads/2013/06/header-dashboard-588x23.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

Para adicionar o seu próprio ícone customizado basta criar uma imagem com 20px quadrados. A imagem precisa ser transparente (formato gif ou png).

<img class="alignnone size-full wp-image-37921" alt="header-dashboard-tableless" src="http://tableless.com.br/uploads/2013/06/header-dashboard-tableless.jpg" width="660" height="26" srcset="uploads/2013/06/header-dashboard-tableless.jpg 660w, uploads/2013/06/header-dashboard-tableless-329x12.jpg 329w, uploads/2013/06/header-dashboard-tableless-588x23.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

Você pode modificar o background por CSS da classe #wp-admin-bar-wp-logo .ab-icon ou acrescentar o seguinte código no seu arquivo functions.php.

<pre class="lang-php">//Custom dashboard logo
add_action('admin_head', 'my_custom_logo');
function my_custom_logo() {
echo '
#wp-admin-bar-wp-logo .ab-icon {background: url('.get_bloginfo('template_directory').'/img/admin_logo.png) no-repeat center top !important; }';
}</pre>

## Como modificar o texto do footer

Por padrão o footer do WordPress exibe a mensagem &#8220;Obrigado por criar com o WordPress&#8221;.

<img class="alignnone size-full wp-image-37920" alt="footer" src="http://tableless.com.br/uploads/2013/06/footer.jpg" width="660" height="52" srcset="uploads/2013/06/footer.jpg 660w, uploads/2013/06/footer-329x25.jpg 329w, uploads/2013/06/footer-588x46.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

Ok. Não somos ingratos, mas já que você que criou seu próprio tema seria interessante colocar ali um link para seu portfólio, créditos relativos ao cliente ou a mensagem que você bem entender, certo?

<img class="alignnone size-full wp-image-37919" alt="footer-modificado" src="http://tableless.com.br/uploads/2013/06/footer-modificado.jpg" width="660" height="52" srcset="uploads/2013/06/footer-modificado.jpg 660w, uploads/2013/06/footer-modificado-329x25.jpg 329w, uploads/2013/06/footer-modificado-588x46.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

Para trocar este texto novamente vamos utilizar o nosso grande amigo functions.php. Adicione o seguinte código e mude o texto entre as aspas depois do echo.

<pre class="lang-php">// Customizar o Footer do WordPress
function remove_footer_admin () {
	echo '© &lt;a href="http://tableless.com.br/"&gt;Tableless&lt;/a&gt; - Desenvolvimento inteligente com padrões web e design';
}
add_filter('admin_footer_text', 'remove_footer_admin');</pre>

## Saudações!

O administrador em inglês do WordPress saúda o usuário com um &#8220;Howdy!&#8221;. Embora muita gente ache que a saudação jovem e divertida, talvez um cliente sério e corporativo ficasse mais satisfeito com algo menos &#8220;sou um cowboy do Texas&#8221;. Por sorte o painel em português diz um simples &#8220;olá&#8221;. Mesmo assim você poder querer trocar o texto para algo que combine mais com o seu projeto.

<img class="alignnone size-full wp-image-37924" alt="mensagem-header" src="http://tableless.com.br/uploads/2013/06/mensagem-header.jpg" width="660" height="26" srcset="uploads/2013/06/mensagem-header.jpg 660w, uploads/2013/06/mensagem-header-329x12.jpg 329w, uploads/2013/06/mensagem-header-588x23.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

Para trocar o texto da saudação padrão do WordPress basta adicionar o seguinte snippet no arquivo functions.php.

<img class="alignnone size-full wp-image-37923" alt="mensagem-header-modificada" src="http://tableless.com.br/uploads/2013/06/mensagem-header-modificada.jpg" width="660" height="26" srcset="uploads/2013/06/mensagem-header-modificada.jpg 660w, uploads/2013/06/mensagem-header-modificada-329x12.jpg 329w, uploads/2013/06/mensagem-header-modificada-588x23.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

No exemplo a seguir o texto dirá &#8220;Bem vindo&#8221;.

<pre class="lang-php">// Saudação customizada
function replace_howdy( $wp_admin_bar ) {
    $my_account=$wp_admin_bar-&gt;get_node('my-account');
    $newtitle = str_replace( 'Olá', 'Bem vindo', $my_account-&gt;title );            
    $wp_admin_bar-&gt;add_node( array(
        'id' =&gt; 'my-account',
        'title' =&gt; $newtitle,
    ) );
}
add_filter( 'admin_bar_menu', 'replace_howdy',25 );</pre>

Ah, se o seu admin estiver em inglês substitua &#8220;Olá&#8221; por &#8220;Howdy&#8221; ou este snippet não vai funcionar&#8230;

## Temas de administração

Todos estes snippets são bacanas para dar um tapa no visual do WordPress. Mas, se você ainda está insatisfeito com o nível de personalização, pode criar um tema completamente diferente. Para isto basta alterar o CSS do administrador. A folha de estilos padrão (/wp-admin/css) é bem completa e organizadinha. Pode ser que você só precise fazer alguns ajustes.

<img class="alignnone size-full wp-image-37918" alt="admin-css" src="http://tableless.com.br/uploads/2013/06/admin-css.jpg" width="660" height="350" srcset="uploads/2013/06/admin-css.jpg 660w, uploads/2013/06/admin-css-316x168.jpg 316w, uploads/2013/06/admin-css-584x310.jpg 584w" sizes="(max-width: 660px) 100vw, 660px" />

&nbsp;

Aqui estão algumas das classes mais utilizadas:

**#wphead**
  
O cabeçalho do painél contendo o título principal, nome do blog e link para o site.

**#adminmenu ul**
  
A barra de navegação lateral com os links: **Posts**, **Mídia**, **Ferramentas**&#8230;

**#adminmenu2 ul**
  
A subnavegação da barra lateral. Por exemplo &#8220;dentro&#8221; de **Posts** teríamos **Todos os Posts**, **Adicionar Novo**, **Tags** e **Categorias**.

**.wrap**
  
A div que funciona como um container principal do painel de administração.

**#footer**
  
O rodapé do site com logotipo do wordpress, versão e links.

**.wrap h2**
  
Títulos das seções principais como por exemplo **Paine**l.

Posteriormente você pode criar um plugin com o seu tema para instalar/desinstalar quando quiser ou até mesmo e redistribuir para a comunidade.

## Apenas a ponta do iceberg

As dicas que eu mostrei aqui são só o começo. Dominando bem as classes CSS do tema e conhecendo o funcionamento do sistema é possível modificar completamente o layout do WordPress. É possível, por exemplo, criar widgets personalizados, esconder ou modificar itens do menu, ocultar alertas de atualizações, exibir mensagens de ajuda, etc. Além disto existem centenas de plugins a sua disposição para transformar ainda mais o sistema, seja em termos de design, seja acrescentando novas funcionalidades. A principal vantagem de trabalhar com um CMS tão conhecido e respeitado no mercado como o WordPress é justamente essa: poder contar com uma comunidade de desenvolvedores imensa criando e compartilhando conhecimento.

### Saiba mais:

 [Codex &#8211; Customizing the Login Form][3]
  
[Codex &#8211; Creating Admin Themes][4]
  
[WP Snippets][5]
  
[Smashing Magazine &#8211; Customize WordPress Admin Easily ][6]

 [1]: http://tableless.com.br/wordpress-uma-pequena-introducao/#.Uc3zT_bXS5c "WordPress – Uma pequena introdução"
 [2]: http://tableless.com.br/como-se-tornar-um-profissional-top-em-wordpress/#.Uc3zs_bXS5c "http://tableless.com.br/como-se-tornar-um-profissional-top-em-wordpress/#.Uc3zs_bXS5c"
 [3]: http://codex.wordpress.org/Customizing_the_Login_Form "Codex WordPress - Customizing the Login Form"
 [4]: http://codex.wordpress.org/Creating_Admin_Themes "Codex WordPress - Creating Admin Themes"
 [5]: http://wp-snippets.com/ "WP Snippets"
 [6]: http://wp.smashingmagazine.com/2012/05/17/customize-wordpress-admin-easily/ "Customize WordPress Admin Easily"