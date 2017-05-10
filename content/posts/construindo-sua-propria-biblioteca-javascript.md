---
title: Construindo sua própria biblioteca javascript
author: Clovis Neto
type: post
date: 2014-07-07
excerpt: E se um dia você criasse sua própria biblioteca JavaScript, no estilo da jQuery?
url: /construindo-sua-propria-biblioteca-javascript/
dsq_thread_id: 2825600760
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - bibliotecas javascript
  - criando sua própia biblioteca javascript
  - JavaScript
  - JQuery

---
Pois bem, meu amigo ninja, está na hora de melhorar um pouco mais seus conhecimentos e quem sabe embarcar em uma nova ideia: a criação da sua própria biblioteca javascript!

# Introdução

Antes de você pensar: “Ah, mas eu já sei como é. Basta estender o objeto HTMLElement por meio da prototype…”. Digo-lhes que felizmente não é assim. Imagine o peso que seria colocar um novo método em todos os elementos HTML. Impraticável.

Bem, meu amigo, se você não compreende minhas palavras, segue um exemplo de como podemos anexar um novo método aos elementos HTML por meio do prototype:

<pre class="lang-javascript">HTMLElement.prototype.esconde = function(){
 this.setAttribute(“style”,”display:none”)
}
</pre>

Logo poderíamos esconder qualquer elemento HTML através da chamada:

<pre class="lang-javascript">document.querySelector(“div”).esconde();</pre>

Então vamos fazer isto da maneira correta, usando um alias ($) para selecionar nossos elementos mais ou menos igual ao jQuery, o resultado final será este:

<pre class="lang-javascript">$(“div”).esconde();</pre>

> Note que a sintaxe ficará igual a biblioteca jQuery. Veremos como obter este resultado passo-a-passo.

# Passo 1 &#8211; A função imediata

Criaremos uma função imediata, incrivelmente versátil e que tornará a linguagem javascript mais poderosa. Esta função imediata, que veremos aqui, criará um escopo temporário e algumas váriaveis “particulares”

**Listagem 1 — Começando com uma função imediata**

<pre class="lang-javascript">(function(){ var blJs= function(arg){ }
})();
</pre>

Note que criei uma função anônima, cujo o nome é: **blJs**.

Este será o nome da nossa biblioteca

# Passo 2 &#8211; Entendendo a blJs

Agora que a brincadeira começa a ficar boa. Primeiro iremos programar nossa função anônima (blJs), para que, sempre que ela for chamada, retorne ela mesmo como um construtor, para podermos ter acesso ao tão poderoso “**this**”:

**Listagem 2 — A função blJs**

<pre class="lang-javascript">var blJs= function(arg){ 
 if(!(this instanceof blJs)){ 
  return new blJs(arg); 
 }
 this.myArg = arg;
}
</pre>

Note que verifiquei se o nosso objeto foi declarado como um construtor. Claro que na chamada inicial ele não será. Por isso invocamos novamente nossa função **blJs**, mas desta vez como um construtor, para podermos utilizar o &#8216;**this**&#8216;. Observe que salvei o argumento da função blJs no objeto **myArg**.

Lembra desta linha de código: $(“div”)…? Isto é o mesmo que: blJs(“div”). Podemos perceber que estamos passando o “**div**” como parâmetro da nossa função. Logo: **this.myArg = “div”**

# Passo 3 &#8211; Estendendo nossa biblioteca: inserindo métodos☺

Se prepare, amigo ninja, pois a mágica funciona justamente nas próximas linhas de códigos a seguir.

Iremos estender nossa função ( blJs ), por meio da propriedade prototype e fn. Veja a seguir:

<pre class="lang-javascript">blJs.fn = blJs.prototype = { 
 esconde: function(){ 
  document.querySelector(this.myArg).setAttribute(“style”,”display:none”); 
 }
}
window.blJs= blJs, window.$ = blJs;
</pre>

Logo definimos que **blJs.fn** é igual a **blJs.prototype**, onde declaramos nosso novo método. O método esconde, que seleciona a div por meio de querySelector(this.myArg) e esconde o elemento alvo por meio de um display:none.

Ao final da nossa função imediata, definimos que window.blJs será igual a nossa função “blJs”, para podermos chamar nossa biblioteca fora do escopo da função imediata. Veja como é simples definir um alias para nossa biblioteca: é só referenciar o window.$ à nossa função blJs.

# Finalizando

Agora é só sorrir e correr para o abraço ☺. Sua biblioteca javascript já está pronta para ser usada. É só utilizar a chamada do inicio:

<pre class="lang-javascript">$(“div”).esconde() ou blJs(“div”).esconde()</pre>

Visualize o código completo no <a title="clique para visualizar o código completo" href="https://github.com/clovisdasilvaneto/blJs" target="_blank">github</a>

Bem, amigos ninjas, por hoje é só. Caso tenha alguma dúvida, deixem seu comentário.

Espero que tenham curtido o artigo. Compartilhem e até a próxima!