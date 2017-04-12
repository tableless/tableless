---
title: Formulário responsivo com MailChimp
author: Palloi Hofmann
type: post
date: 2015-02-06
excerpt: Cada dia mais estamos utilizando serviços disponíveis na web, principalmente aqueles que tem um plano básico gratuito que permite integrações.
url: /formulario-responsivo-com-mailchimp/
categories:
  - Adaptive Web Design (AWD)
  - AJAX
  - Código
  - CSS
  - HTML
  - JavaScript
  - JQuery
  - Responsive Web Design (RWD)
tags:
  - AJAX
  - CSS
  - formularios
  - html
  - JQuery
  - mailchimp
  - responsivo

---
Há cada dia mais utilizamos serviços disponíveis na web que tem um plano básico e gratuito que permite integrações. Nos últimos meses tenho feito formulários com frequência usando uma abordagem bem simples. Vou mostrar agora como criar um formulário responsivo, integrando com MailChimp e usando jQuery Validate.

## O HTML

Vamos criar o formulário da seguinte maneira:

<pre class="lang-html">&lt;section&gt;
  &lt;h1&gt;CREATE RESPONSIVE FORM WITH INTEGRATE MAILCHIMP&lt;/h1&gt;
  &lt;form id="form-contact" method="POST" action="mailchimp-contact.php"&gt;
    &lt;div class="input"&gt;
      &lt;label for="name"&gt;Name&lt;/label&gt;
      &lt;input type="text" id="name" name="name" placeholder="Your name" required&gt;
    &lt;/div&gt;

    ...
    
    &lt;div class="input txt"&gt;
      &lt;label for="message"&gt;Message&lt;/label&gt;
      &lt;textarea id="message" name="message" cols="10" rows="5" placeholder="Its message leaves" required&gt;&lt;/textarea&gt;
    &lt;/div&gt;
    &lt;div class="buttons"&gt;
      &lt;span class="form-message"&gt;&lt;/span&gt;
      &lt;input type="submit" value="SEND" /&gt;
    &lt;/div&gt;
  &lt;/form&gt;
&lt;/section&gt;</pre>

<a href="http://palloi.github.io/responsive-form-mailchimp/demo-only-elements.html" target="_blank" title="Ver demo sem style.">Ver demo sem style.</a>

## O CSS

Para cada label e input foi adicionado uma `div.input` para inserir uma formatação por grupo.

### O form está centralizado com max-width:

Por ser um elemento &#8216;block&#8217;, vamos definir o tamanho máximo que ele pode ter.

<pre class="lang-css">form {
&nbsp; margin: 0 auto;
&nbsp; max-width: 850px;
&nbsp; padding: 20px 10px;
&nbsp; background-color: rgba(255,255,255,0.4)
}
</pre>

### O grupo div.input com 50% em &#8216;width&#8217; do form:

<pre class="lang-css">.input {
  float: left;
  width: 48%;
  padding: 0 1% 20px;
  position: relative;
}

.input.txt { width: 98%; } /*textarea 100%*/
</pre>

### Os labels:

<pre class="lang-css">.input label {
  display: block;
  padding-bottom: 5px;
  color: #666;
}
</pre>

<pre class="lang-css">.input label.error {
  position: absolute;
  right: 18px;
  top: 35px;
  color: #f00;
}</pre>

O label.error é gerado pelo jQuery validate e adicionado seguido dos campos.

### Os campos:

<pre class="lang-css">.input input,
.input textarea {
  padding-top: 10px;
  padding-bottom: 9px;
  border: none;
  font-size: 16px;
  font-weight: 100;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}

.input input {
  width: 94%;
  padding-left: 3%;
  padding-right: 3%;
}

.input textarea {
  width: 97%;
  padding-left: 1.5%;
  padding-right: 1.5%;
}</pre>

Formatamos os campos para ter 100% de tamanho do elemento pai &#8216;div.input&#8217;.
  
Sempre que redimensionar não haverá quebras, portanto, responsivo meu amigo.

### Agora um capricho para resoluções pequenas.

<pre class="lang-css">@media screen and (max-width: 520px) {
  .input {
    width: 98%;
  }
}</pre>

<a href="http://palloi.github.io/responsive-form-mailchimp/demo-style-elements.html" target="_blank" title="Ver demo com style.">Ver demo com style.</a>

## O jQuery + MailChimp

Com o HTML e CSS prontos, vamos adicionar o JavaScript que é fácil. Como dependemos do jQuery e não podemos iniciar de qualquer forma, segue uma estrutura bem legal:

<pre class="lang-javascript">function(){
  var contact = function(){
    var init = function() {
      //initialize code
    };
    
&nbsp;   //more functions

    return {init: init};
  }();

  //jQuery loaded
  $(document).ready(contact.init);
})();</pre>

Como sabemos exatamente qual função vai executar quando a jQuery carregar, adicionaremos o jQuery Validate no init:

<pre class="lang-javascript">var init = function() {
  $(&#039;#form-contact&#039;).validate({
    rules : {
      name: "required",
      email: { required: true, email: true },
      phone: { required: true, minlength: 14 },
      company: "required",
      message: "required"
    },
    messages: {
      name: "*",
      email: { required: "*", email: "*" },
      phone: { required: "*", minlength: "*" },
      company: "*",
      message: "*"
    }
  });
};</pre>

Agora que estamos validando todos os campos, que tal adicionar um ajax para deixar nosso formulário bem suave e uma função para exibir mensagens de sucesso ou erro, veja:

<pre class="lang-javascript">var init = function() {
  $(&#039;#form-contact&#039;).validate({
    rules : {
      ...
    },
    messages: {
      ...
    },
    submitHandler: function(form) {
      var $form = $(form);

      var params = {
        name: $form.find(&#039;#name&#039;).val(),
        email: $form.find(&#039;#email&#039;).val(),
        phone: $form.find(&#039;#phone&#039;).val(),
        company: $form.find(&#039;#company&#039;).val(),
        message: $form.find(&#039;#message&#039;).val()
      };

      $.ajax({
        type: $form.attr(&#039;method&#039;),
        url: $form.attr(&#039;action&#039;),
        data: params,
        success: function( data ) {
          if(data == "true") {
            $form.find(&#039;.input input&#039;).val("");
            $form.find(&#039;.input textarea&#039;).val("");
            setMessage("Mission accomplished. &lt;strong&gt;"+ params.email +"&lt;/strong&gt; was successfully added to list.", "success");
          } else {
            setMessage("Mission failed. &lt;strong&gt;"+ params.email +"&lt;/strong&gt; not was added to list.", "error");
          }
        },
        error: function( data ) {
          setMessage("Mission failed in connection. Try again.", "error");
        }
      });

      return false;
    }
  });
};

var setMessage = function($message, $type) {
  $(&#039;.form-message&#039;).html($message).addClass($type);

  setTimeout(function(){
    $(&#039;.form-message&#039;).removeClass($type);
  }, 6000);
};
</pre>

Via &#8216;submitHandler&#8217; do <a href="http://jQueryvalidation.org/" target="_blank">jQuery Validate</a>, vamos disparar por ajax todos os dados preenchidos e travar o post do form com &#8216;return false&#8217; no final da função. Assim evitamos aquele redirecionamento de post.

### O PHP

Como definimos com &#8216;method&#8217; e &#8216;action&#8217; para o nosso formulário, segue o código para resgatar os dados:

<pre class="lang-php">&lt;?php
    require_once &#039;MCAPI.class.php&#039;;
    $api = new MCAPI(&#039;casiuach1293kajsc912319203cja23s-us9&#039;);
    $merge_vars = array(&#039;NAME&#039;=&gt;$_POST["name"], 'PHONE'=&gt;$_POST["phone"], 'COMPANY'=&gt;$_POST["company"], 'MESSAGE'=&gt;$_POST["message"]);
    
    // Submit subscriber data to MailChimp
    // For parameters doc, refer to: http://apidocs.mailchimp.com/api/1.3/listsubscribe.func.php
    $retval = $api-&gt;listSubscribe( &#039;12938asd98&#039;, $_POST["email"], $merge_vars, &#039;html&#039;, false, true );
    
    if ($api-&gt;errorCode){
        echo "false";
    } else {
        echo "true";
    }
?&gt;
</pre>

Dependemos da MCAPI.class que você pode verificar na <a href="https://apidocs.mailchimp.com/api/example-code/" target="_blank">documentação</a> ou baixar <a href="https://codeload.github.com/sunarlim/mailchimp-subscribe/zip/master" target="_blank">aqui</a>, só lembrando que precisa adicionar sua API Key e List ID.

## PRONTO

Nosso formulário é responsivo e integrado ao mailchimp.

<a href="http://css4html.com.br/demos/responsive-form-mailchimp/" target="_blank" title="Veja como ficou o resultado final">Veja como ficou o resultado final</a>
  
<a href="https://github.com/palloi/responsive-form-mailchimp/" target="_blank" title="Veja o código completo no github">Veja o c&oacute;digo completo no github</a>

É isso ae pessoal, obrigado.