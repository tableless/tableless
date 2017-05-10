---
title: Lojas virtuais com WooCommerce II – Criando temas personalizados
author: Dani Guerrato
type: post
date: 2013-11-04
excerpt: Conheça o front-end do WooCommerce, aprenda a utilizar ganchos de ação e filtros, organize seu CSS e crie seu próprio layout de loja virtual.
url: /lojas-virtuais-com-woocommerce-ii-criando-temas-personalizados/
dsq_thread_id: 1926835656
categories:
  - Wordpress
tags:
  - temas em woocommerce
  - WooCommerce
  - Wordpress

---
O [WooCommerce][1] é um plugin capaz de transformar qualquer site desenvolvido em WordPress em uma loja virtual super potente. Mas para adaptar o seu tema para o sistema e garantir que o seu layout seja visualizado corretamente existem alguns truques, funções e ações fundamentais para que tudo funcione direitinho. A documentação oficial, embora bem completa, pode ser um pouco confusa pois não está organizada em uma ordem cronológica.  Pensando nisto preparei este artigo recheado de dicas úteis para que você possa criar temas em WooCommerce facilmente. Vamos a ele!

#### Aviso aos navegantes!

Para compreender este artigo você precisará de dois requisitos básicos:
  
1. Saber [criar temas para WordPress][2].
  
2. Conhecer as [funções básicas do WooCommerce][3].

### Utilizando seu próprio tema

Existem duas opções básicas para ter um tema personalizado: baixar um tema padrão do WooCommerce e realizar modificações na estrutura ou instalar o plugin em um tema comum de WordPress. Vamos trabalhar com a segunda opção por fins didáticos. Mas eu recomendo experimentar as duas possibilidades para que você possa escolher a sua favorita.

O WooCommerce teoricamente é desenvolvido para funcionar corretamente com qualquer tema de WordPress. Tudo que você precisa fazer, teoricamente, é instalar o plugin e copiar os arquivos da pasta **wp-content/plugins/woocommerce/templates/ **para **/wp-content/themes/nomedoseutema**.

Mas é claro. Se fosse simples assim não iríamos precisar deste artigo, certo?  É bem provável que o seu tema fique um Frankenstein desconfigurado, o layout quebre ou até mesmo simplesmente não funcione. Mas, para tudo tem uma solução! Hoje vamos aprender como modificar a estrutura do WooCommerce para que você possa ter uma loja virtual customizada para chamar de sua.

## O meu tema não oferece suporte ao WooCommerce. E agora?

Se você acabou de instalar o WooCommerce em um tema não-padrão é provável que aparece uma a mensagem em roxo como &#8220;_Seu tema não oferece suporte ao WooCommerce – Se você encontrar problemas de design, por favor, leia o guia de integração ou escolha um tema do WooCommerce 🙂_&#8220;. Isto acontece pois seu tema pode estar utilizando uma estrutura muito diferente e o plugin não tem como adivinhar que página é o que&#8230; Não entre em pânico. Existem duas maneiras para solucionar este problema: substituir a estrutura do seu tema e/ou utilizar hooks.

### Substituindo o loop

1. Duplique o arquivo **page.php** do tema (ou o tipo de página personalizada que você deseja utilizar) e renomeio o arquivo para **woocommerce.php**. A localização dele deve ser a seguinte **wp-content/themes/nomedoseutema/woocommerce.php**.

2. Procure pelo loop do seu post. Normalmente é algo parecido com:

<pre>&lt;?php if ( have_posts() ) :
...
&lt;?php endif; ?&gt;</pre>

&nbsp;

3. Substitua este código por:

<pre>&lt;?php woocommerce_content(); ?&gt;</pre>

&nbsp;

4. Pronto! Sua loja já deve estar funcionando. Por padrão, utilizando o WooCommerce em português, a url ficará em www.seudominio.com.br/loja.

Substituir o loop é rápido e fácil. O ponto contra desta saída é que todos os tipos de post e taxonomias do WooCommerce ficarão com o mesmo layout&#8230; Se você quiser criar templates diferentes para cada seção será necessário partir para a próxima etapa.

## Utilizando Hooks

O WooCommerce (assim como o próprio WordPress) trabalha utilizando uma estrutura de hooks ou, em português, ganchos. A idéia aqui é chamar um determinado elemento de forma rápida através de uma função. Desta maneira você pode manipular o código (e criar suas próprias páginas), sem necessariamente modificar os arquivos do core. Esta solução é mais complexa e flexível do que simplesmente substituir o loop, mas também pode ser um pouco mais complicada se você for um iniciante.

Primeiro é necessário desconectar os ganchos padrões do WooCommerce. Para isto basta acrescentar estas linhas no arquivo **functions.php**

<pre>remove_action( 'woocommerce_before_main_content', 'woocommerce_output_content_wrapper', 10);
remove_action( 'woocommerce_after_main_content', 'woocommerce_output_content_wrapper_end', 10);</pre>

&nbsp;

Depois conecte suas próprias funções para mostrar o conteúdo do seu tema. Por exemplo:

&nbsp;

<pre>add_action('woocommerce_before_main_content', 'my_theme_wrapper_start', 10);
add_action('woocommerce_after_main_content', 'my_theme_wrapper_end', 10);

function my_theme_wrapper_start() {
  echo '&lt;section id="main"&gt;';
}

function my_theme_wrapper_end() {
  echo '&lt;/section&gt;';
}</pre>

&nbsp;

Não esqueça de substituir as classes e IDs pelas seções do seu tema.

### Criando hooks personalizados

O WooCommerce é um plugin bem completo. Mas as vezes você deseja inserir alguma funcionalidade diferente da do tema padrão. Você pode fazer isto criando novos hooks personalizados através do arquivo **functions.php**.

Existem dois tipos de hooks: ganchos de ações e ganchos de filtros.

#### Action hooks

Permite que você insira um código customizado. Você pode criar os seus próprios ganchos de ação através do arquivo **functions.php**. Para isto basta seguir esta estrutura:

<pre>add_action('action_name', 'your_function_name');
function your_function_name() {
// Seu código
}</pre>

&nbsp;

Então chame a função no seu layout obedecendo a seguinte sintaxe:

<pre>do_action(‘action_name’);</pre>

#### Filter Hooks

Os ganchos de filtros servem para retornar e/ou manipular uma determinada variável, como por exemplo o preço de um produto. De maneira bem semalhante a ações, você pode criar seus próprios filtros através do nosso bom e velho amigo **functios.php**

<pre>add_filter('filter_name', 'your_function_name');
function your_function_name( $variable ) {
// Seu código
return $variable;
}</pre>

E para chamar a função no seu layout:

<pre>apply_filter(‘filter_name’, $variable);</pre>

Mas nem sempre é preciso reinventar a roda. O WooCommerce possui uma [lista bem grande de hooks][4] para diversas situações. A seção [snippets][5] da documentação do WooCommerce também possui hooks que podem ser úteis para o seu tema. Vale a pena favoritar e consultar antes de criar uma nova função.

## Estrutura básica de um Template

Trabalhar com hooks é uma maneira prática de criar suas próprias páginas de template. Mas as vezes você quer simplesmente fazer uma modificação em alguma estrutura já existente. Na pasta **/woocommerce/templates/** você encontrará a estrutura do front-end da loja, bem como os templates para e-mail marketing do seu projeto.

**archive-pro
  
duct.php**

**cart/**
  
cart-empty.php
  
cart.php
  
cross-sells.php
  
mini-cart.php
  
shipping-calculator.php
  
shipping-methods.php
  
totals.php

**checkout/**
  
cart-errors.php
  
form-billing.php
  
form-checkout.php
  
form-coupon.php
  
form-login.php
  
form-pay.php
  
form-shipping.php
  
review-order.php
  
thankyou.php

**content-product_cat.php**
  
**content-product.php**
  
**content-single-product.php**

**emails/**
  
admin-new-order.php
  
customer-completed-order.php
  
customer-invoice.php
  
customer-new_account.php
  
customer-note.php
  
customer-processing-order.php
  
customer-reset-password.php
  
email-addresses.php
  
email-footer.php
  
email-header.php
  
email-order-items.php

**loop/**
  
add-to-cart.php
  
loop-end.php
  
loop-start.php
  
no-products-found.php
  
orderby.php
  
pagination.php
  
price.php
  
rating.php
  
result-count.php
  
sale-flash.php

**myaccount/**
  
form-change-password.php
  
form-edit-address.php
  
form-login.php
  
form-lost-password.php
  
my-account.php
  
my-address.php
  
my-downloads.php
  
my-orders.php

**order/**
  
form-tracking.php
  
order-details.php
  
tracking.php

**shop/**
  
breadcrumb.php
  
errors.php
  
form-login.php
  
messages.php
  
sidebar.php
  
wrapper-end.php
  
wrapper-start.php

**single-product/**
  
add-to-cart/
  
external.php
  
grouped.php
  
quantity.php
  
simple.php
  
variable.php
  
meta.php
  
price.php
  
product-attributes.php
  
product-image.php
  
product-thumbnails.php
  
related.php
  
review.php
  
sale-flash.php
  
share.php
  
short-description.php
  
tabs/
  
additional-information.php
  
description.php
  
tabs.php
  
title.php
  
up-sells.php

**single-product-reviews.php**
  
**single-product.php**
  
**taxonomy-product_cat.php**
  
**taxonomy-product_tag.php**

Em tese basta editar estes arquivos para alterar a estrutura. Mas tome cuidado: se você simplesmente alterar e salvar por cima o seu tema vai funcionar, mas toda vez que o plugin for atualizado suas modificações serão perdidas… Se você quiser fazer alterações de forma segura duplique o arquivo desejado e salve na pasta **nomedoseuthema/woocommerce/**. Desta maneira você não perderá suas modificações em uma atualização futura.

Ex: Vamos supor que você queira modificar o carrinho de compras. Copie o arquivo localizado em **/templates/cart/cart.php** para **nomedoseutema/woocommerce/cart/cart.php**.

## Modificando o CSS

OK. Vamos supor que você já tenha editado todos os arquivos PHP e esteja satisfeito com a estrutura da loja. Mas o visual provavelmente está todo quebrado! É preciso agora modificar o CSS do seu tema para criar estilos de botões, links, texto, etc.

Dentro da pasta **assets/css/** você vai encontrar duas folhas de estilo: woocommerce.less e woocommerce.css A versão .css está minificada, ou seja, o ideal é trabalhar com o arquivo pré-processado (extensão .less) e depois compilar ([saiba mais sobre LESS][6]). Se você não curte muito utilizar LESS não se preocupe! Você pode também descomprimir o css padrão.

Aqui vale o mesmo conselho dos outros arquivos do tema: não sobrescreva os arquivos ou eles irão para o grande limbo da internet na próxima atualização do WooCommerce! Ao invés disto crie seus próprios arquivos CSS e/ou LESS a partir de cópias dos originais e desative as folhas antigas. Como fazer isto? Através do arquivo **functions.php**. Basta inserir a seguinte linha de código:

<pre>define('WOOCOMMERCE_USE_CSS', false);</pre>

&nbsp;

Depois de desativado é só continuar trabalhando com a cópia dentro da pasta do seu tema (que você fez no inicio do parágrafo, lembra?)

## Declararando seu suporte ao WooCommerce

Uma vez que você esteja satisfeito com o visual e as funcionalidades do seu tema, está na hora de remover aquela mensagem chatinha de erro (&#8220;seu tema não é compatível blá blá blá&#8230;&#8221;) e declarar o seu suporte ao WooCommerce. Para isto, basta colar esta linha de código no **functions.php**

<pre>add_theme_support( 'woocommerce' );</pre>

&nbsp;

E pronto! Agora é só realizar as configurações básicas, acrescentar produtos e começar a vender. Boa sorte! 🙂

 [1]: http://www.woothemes.com/woocommerce/ "WooCommerce"
 [2]: http://codex.wordpress.org/Theme_Development "Wordpress Codex - Theme Development"
 [3]: http://tableless.com.br/lojas-virtuais-com-woocommerce/#.UnLaEJTXQv4 "Lojas virtuais com WooCommerce"
 [4]: http://docs.woothemes.com/document/hooks/ "WooThemes Hooks"
 [5]: http://docs.woothemes.com/documentation/plugins/woocommerce/woocommerce-codex/snippets/ "WooCommerce Snippets"
 [6]: http://tableless.com.br/css-dinamico-com-less/#.UnLuApTXQv4 "Css dinamico com less"