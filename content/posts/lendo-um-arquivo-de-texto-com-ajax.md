---
title: Lendo um arquivo de texto com AJAX
author: Moacyr Minéro
type: post
date: 2011-09-14
url: /lendo-um-arquivo-de-texto-com-ajax/
tweetbackscheck:
  - 1356446444
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4131";s:7:"tinyurl";s:26:"http://tinyurl.com/3p8mgj6";s:4:"isgd";s:19:"http://is.gd/2cNhT3";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503012620
categories:
  - AJAX
  - Código
tags:
  - 2011
  - AJAX
  - JavaScript
  - Na Prática

---
Inicio mostrando como realizar uma requisição de arquivos de texto com AJAX.
  
Em tempos de Web 2.0, não podemos pensar mais em sites que usem requisições síncronas para rotinas de interação com o usuário.
  
Uma das técnicas mais utilizadas para esse fim é o AJAX &#8211; Assynchronous Javascript and XML.
  
De uma forma resumida e sem muito &#8220;tecniquês&#8221;, AJAX é a captura de informações sem a necessidade de recarregamento da estrutura do documento HTML a cada requisição ao servidor web.

E para poder fazer conexão assíncrona com o servidor web temos que criar um objeto com as propriedades e métodos AJAX .
  
Porém, como a web não é um ambiente perfeito, temos que criar um objeto AJAX para os browsers Firefox, Chrome, Opera, Safari, chamado de XMLHttpRequest. E para o IE um objeto ActiveX que faça referencia ao objeto XMLHTTP.

Como padrão de desenvolvimento, vamos criar um arquivo que faça essa identificação e criação chamado de xhr.js.
  
Para a criação desse arquivo, abra o editor de código de sua preferência e digite o seguinte código:

**Arquivo xhr.js**&#8230;

<pre class="lang-javascript">//Declarando variaveis globais
var xhr;
var txt ;

function ajax(){
//Verificando se os browsers aceitam o objeto XMLHttpRequest
if(window.XMLHttpRequest){
xhr  = new XMLHttpRequest();
}
//Verificando se o browser IE versão &gt; 6
else if(window.ActiveXObject){
try{
xhr = new ActiveXObject(Msxml2.XMLHTTP);
}
catch(e){
try{
xhr =  new ActiveXObject(Microsoft.XMLHTTP);
}
catch(er){
txt = "Seu browser não aceita AJAX!";
alert(txt);
}
}
}
return xhr;
}
...
</pre>

Em seguida, vamos criar o arquivo HTML e fazer referência ao objeto AJAX criado pelo arquivo **xhr.js**.
  
Para isso use a  tag script no head da página html. Exemplo: **<script type=&#8221;text/javascript&#8221; src=&#8221;caminho/xhr.js&#8221;></script>**

**Arquivo ajax_txt.html**

<pre class="lang-javascript">//Declarando variáveis globais
var xhr;
var valor;

//Função para pegar os arquivos de texto
function pegaTextos{
//Instancia o objeto ajax e guarda na var xhr
xhr = ajax();
//Captura o elemento select  via DOM
var txt = document.getElementById("textos");
//Pega o valor da opção escolhida na lista do campo select
valor = txt.options[txt.selectedIndex].value;
//Monta a url da chamada AJAX
var url = "texto"+valor+".txt";
//Abre a conexão com o servidor web via AJAX
xhr.open("GET",url,false);
//Confirma o envio dos dados
xhr.send(null);
//Verifica a mudança de estado do servidor web e dispara a função para mostrar os textos
xhr.onreadystatechange = mostraTextos;
}

//Função para mostras os textos
function mostraTextos(){
//Verifica o status do retorno do servidor web
if(xhr.readyState == 4 && xhr.status == 200){
//Pega a resposta do servidor web
var resposta = xhr.responseText;
//Captura a div Box para mostrar os textos
var box  = document.getElementById("box");
//Escreve os textos na div Box
box.innerHTML = resposta;
//Aplica um estilo de borda na div Box
box.style.border = "1px dotted #333";
}
}

</pre>

Aplicando um estilo CSS na div Box

<pre class="lang-css">#box{
width: 450px;
height: auto;
padding: 10px;
margin-top: 25px;
}

</pre>

Montamos agora o HTML com o combo dos textos.

<pre class="lang-html">&lt;body&gt;
&lt;p&gt;Selecionando textos com AJAX&lt;/p&gt;&lt;br/&gt;
&lt;select id="textos" onchange="pegaTextos()"&gt;
&lt;option value="" selected="selected"&gt;selecione&lt;/option&gt;
&lt;option value="1"&gt;Texto 1&lt;/option&gt;
&lt;option value="2"&gt;Texto 2&lt;/option&gt;
&lt;option value="3"&gt;Texto 3&lt;/option&gt;
&lt;/select&gt;
&lt;div id="box"&gt;&lt;/div&gt;
&lt;/body&gt;
</pre>

Para que a chamada AJAX funcione, temos que criar os arquivos de textos com os respectivos nomes: texto1.txt,texto2.txt e texto3.txt.
  
Em seguida salve os arquivos na mesma pasta onde se encontram os **arquivos xhr.js** e **ajax_txt.html**.

Agora é so testar!

Lembrando que para uma requisição AJAX funcionar, ela tem que passar por um servidor. No nosso caso o **localhost**.