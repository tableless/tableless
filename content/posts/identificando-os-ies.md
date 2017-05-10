---
title: Identificando os IEs
author: Diego Eis
type: post
date: 2012-07-10
excerpt: Utilize dois modos simples para identificar os IEs em seus projetos.
url: /identificando-os-ies/
tweetbackscheck:
  - 1356404460
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6404";s:7:"tinyurl";s:26:"http://tinyurl.com/d2dhykv";s:4:"isgd";s:19:"http://is.gd/HZpEUc";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 759056657
categories:
  - Browsers
  - Código
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - 2012
  - Browsers
  - internet explorer
  - JavaScript
  - JQuery

---
Os browsers caminham para um status interessantes. Os usuários estão cada vez mais utilizando browsers mais atuais e espertos. Considere um vencedor se você não precisa mais desenvolver para IE8 e só foca seu esforço para desenvolver acima do IE9. Acontece que uma hora ou outra você vai precisar fixar alguns erros em browsers antigos. Seu cliente vai pedir, seu chefe vai chorar ou qualquer outro motivo vai te fazer resolver um bugzinho no IE7.

Aqui vai uma dica simples que pode salvar seu dia: adicione uma classe na tag HTML identificando o browser, assim você poderá direcionar um código para este browser específico. Fazemos isso com um código simples em Javascript ou JQuery. Veja abaixo:

Versão em Javascript:

<pre class="lang-javascript">&lt;script type="text/javascript"&gt;
if (/MSIE (\d+\.\d+);/.test(navigator.userAgent)) {
 var ieversion=new Number(RegExp.$1)
 if (ieversion&gt;=8)
     // Para IE8
     document.getElementsByTagName('html')[0].className+='ie8';
 else if (ieversion&gt;=7)
     // Para IE7
     document.getElementsByTagName('html')[0].className+='ie7';
 else if (ieversion&gt;=6)
     // Para IE6
     document.getElementsByTagName('html')[0].className+='ie6';
}
&lt;/script&gt;
</pre>

Versão em JQuery:

<pre class="lang-javascript">if ($.browser.msie) {
    if(parseInt($.browser.version) == 8){
         // Para IE8
         $("html").addClass("ie8");
    } else if(parseInt($.browser.version) == 7){
         // Para IE7
         $("html").addClass("ie7");
    } else if(parseInt($.browser.version) == 6){
         // Para IE6
         $("html").addClass("ie6");
    }
}
</pre>

Eu prefiro usar isso a ter que usar CSS Hacks ou ter que usar comentários condicionais para adicionar uma classe na tag HTML. Assim nós precisamos sujar a sintaxe do CSS e quando quisermos retirar esse código adicional e nem sujamos muito no código HTML. Com comentários condicionais ficaria assim:

<pre class="lang-html">&lt;!--[if IE 6]&gt;
&lt;html lang="pt-br" class="ie6"&gt;
&lt;![endif]--&gt;

&lt;!--[if IE 7]&gt;
&lt;html lang="pt-br" class="ie7"&gt;
&lt;![endif]--&gt;

&lt;!--[if IE 8]&gt;
&lt;html lang="pt-br" class="ie8"&gt;
&lt;![endif]--&gt;

&lt;!--[if gte IE 8]&gt;
&lt;html lang="pt-br" class="ie9"&gt;
&lt;![endif]--&gt;

&lt;!--[if !IE]&gt;&lt;!--&gt;
&lt;html lang="pt-br"&gt;
&lt;!--&lt;![endif]--&gt;
</pre>

Eu acho melhor utilizar os comentários condicionais para separar os arquivos de CSS. Assim:

<pre class="lang-html">&lt;!--[if IE 6]&gt;
&lt;link rel="stylesheet" type="text/css" href="ie6.css" /&gt;
&lt;![endif]--&gt;

&lt;!--[if IE 7]&gt;
&lt;link rel="stylesheet" type="text/css" href="ie7.css" /&gt;
&lt;![endif]--&gt;

&lt;!--[if IE 8]&gt;
&lt;link rel="stylesheet" type="text/css" href="ie8.css" /&gt;
&lt;![endif]--&gt;

&lt;!--[if gte IE 8]&gt;
&lt;link rel="stylesheet" type="text/css" href="ie9.css" /&gt;
&lt;![endif]--&gt;

&lt;!--[if !IE]&gt;&lt;!--&gt;
&lt;link rel="stylesheet" type="text/css" href="application.css" /&gt;
&lt;!--&lt;![endif]--&gt;
</pre>

### Guerra contra o Terror

[Preparamos um PDF][1] que te ajuda a convencer clientes e chefes <del>tontos</del> mostrando as deficiencias de suportarmos browsers antigos. [Dá uma olhada aqui][1].

 [1]: http://tableless.com.br/browsers-antigos-guerra-contra-o-terror/