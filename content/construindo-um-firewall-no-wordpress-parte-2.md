---
title: Construindo um firewall no WordPress – Parte 2
author: Morais Júnior
type: post
date: 2016-09-26
url: /construindo-um-firewall-no-wordpress-parte-2/
categories:
  - CMS
  - Geral
  - Wordpress

---
Neste artigo de hoje iremos dar continuar com a série onde construímos um plugin de controle e monitoramento de acessos no WordPress, para controlarmos e impedirmos tentativas de login, ataques DDOS e outros eventos que possam vir a prejudicar nosso ambiente WordPress.

Para quem ainda não leu o primeiro artigo comece pela [parte 1][1] onde criamos a base do plugin e uma notificação por e-mail quando tivermos uma tentativa de login fracassada, nessa segunda parte iremos implementar um contador dessas tentativas e junto dele um bloqueio quando atingirmos um limite previamente configurado, para isso utilizaremos as funções: get\_transient, set\_transient e delete_transient&#8230;

Transitents no WordPress é um recurso muito interessante para guardarmos pares de chaves/valor que possam ser consultados posteriormente, não é o objetivo desse recurso o controle que iremos implementar, o correto seria fazer estes registros diretamente nos logs do servidor, porem para fins didáticos (e por muita gente utilizar cPanel e não ter acesso a escrita dos logs) iremos utilizar assim por hora 🙂

nosso plugin atualizado fica assim:

<pre class="lang-html"> &lt;?php
/*
Plugin Name: WP Firewall
Description: Controle de segurança do WordPress
Version: 1.0
Author: Tableless
Author URI: http://tableless.com.br
*/
if (!class_exists('WP_Firewall')) { //caso a classe já não exista
 class WP_Firewall{ // declara o plugin WP_Firewall
 function WP_Firewall (){ //inicialização da classe: Declara uma ação apara quando tiver uma falha de login
 add_action('init', array($this, 'init'));
 add_action('admin_init', array( $this , 'register_fields' ) );

 add_action('wp_login', array($this, 'log'));
 add_action('wp_login_failed', array($this, 'log_failed'));
 }
 
 public function init( ) {
 $_LIMIT = get_option( 'firewall_login_limit', 10); //recebe a configuração
 $_COUNT = get_transient( 'log_failed_'.$_SERVER['REMOTE_ADDR'] ); //recebe o contador

 //faz o bloqueio
 if($_COUNT &gt;= $_LIMIT):
 echo "Ops!!! voce excedeu o limite de tentativas :(";
 exit;
 endif;
 }

 public function log( ) {
 //exclui o transient
 delete_transient( 'log_failed_'.$_SERVER['REMOTE_ADDR'] );
 }

 public function log_failed( $username ) {
 //recebe o número atual de tentativas do ip
 $_COUNT = get_transient( 'log_failed_'.$_SERVER['REMOTE_ADDR'] );

 //Ops.. Login falhou 🙂 o que fazer agora? 
 set_transient('log_failed_'.$_SERVER['REMOTE_ADDR'], $_COUNT + 1, 12 * HOUR_IN_SECONDS );

 //avisa por e-mail da tentativa de login
 @mail(get_option('admin_email'), 'Login falhou :'.$username, json_encode($_SERVER)); 
 }

 public function register_fields() {
 //registra o campo nas configurações gerais
 register_setting( 'general', 'firewall_login_limit', 'esc_attr' );
 add_settings_field(
 'firewall_login_limit',
 '&lt;label for="extra_blog_desc_id"&gt;Limite de tentativas no login&lt;/label&gt;',
 array( $this, 'fields_html' ),
 'general'
 );
 } 
 public function fields_html() {
 $value = get_option( 'firewall_login_limit', 10);
 //imprime o campo nas configurações gerais
 echo '&lt;input type="number" id="firewall_login_limit" name="firewall_login_limit" value="' . esc_attr( $value ) . '" /&gt;';
 } 
 }
 
 $WP_Firewall = new WP_Firewall();
}</pre>

Contador, bloqueio e notificação implementados, na parte 3  iremos fazer uso do [Google reCAPTCHA][2] para melhorar nosso firewall&#8230;

até a próxima!

 [1]: http://tableless.com.br/construindo-um-firewall-no-wordpress-parte-1/
 [2]: https://www.google.com/recaptcha/intro/index.html