---
title: Construindo um firewall no WordPress – Parte 1
author: Morais Júnior
type: post
date: 2016-09-01
url: /construindo-um-firewall-no-wordpress-parte-1/
categories:
  - CMS
  - Wordpress

---
Quem desenvolve para WEB e nunca passou por um ataque DDoS provavelmente não está fazendo o monitoramento de forma correta, principalmente em plataformas que utilizam WordPress, por ser OpenSorce existe uma infinidade de robores navegando pela internet em busca de brechas para obter acesso administrativo.

Nessa serie de artigos iremos desenvolver um plugin que possa monitorar, identificar e barrar esses acessos e tentativas de invasão, por hoje iremos apenas criar o plugin e implementar uma ação que nos indique por e-mail quando over uma falha de login. _(mas você ja pode ir pesquisando sobre **iptables** e **fail2ban** que serão os recursos que utilizaremos nos próximos artigos para automatizar o bloqueio deses acessos 🙂_

Para começar você precisa criar o arquivo **WP_Firewall.php** na pasta **plugins** e nesse arquivo escrever o seguinte código:

<pre class="lang-html">&lt;?php
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
     add_action('wp_login_failed', array($this, 'log_failed'));
   }

   public function log_failed( $username ) {
     //Ops.. Login falhou 🙂 o que fazer agora?

     //avisa por e-mail da tentativa de login
     mail(get_option('admin_email'), 'Login falhou :'.$username, json_encode($_SERVER)); 
   }
 }

 $WP_Firewall = new WP_Firewall();
}</pre>

Pronto agora é só salvar e ativar o plugin. 🙂

Nos próximos artigos iremos desenvolver este plugin implementando bloqueios, fazendo registro nos logs do servidor e integrando com o firewall nativo do linux. Até a próxima&#8230;