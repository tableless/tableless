---
title: Criando efeito de fadeIn e fadeOut com javascript puro
author: Clovis Neto
type: post
date: 2014-01-29
excerpt: Veja como criar um efeito semelhante ao fadeIn e fadeOut da famosa biblioteca Jquery apenas com javascript
url: /criando-efeito-de-fadein-e-fadeout-com-javascript-puro/
dsq_thread_id: 2170230371
categories:
  - Código
  - JavaScript
  - Técnicas e Práticas
tags:
  - efeitos javascript
  - fadein
  - fadeout
  - html5
  - JavaScript
  - javascript ninja
  - javascript puro

---
O uso de bibliotecas JavaScript vem crescendo muito atualmente, mas às vezes utilizamos certas bibliotecas (como a jQuery) para simples tarefas, que poderíamos fazer apenas com JavaScript.

Vejamos na **Listagem 1** o que acontece muito nas páginas da web de hoje.

**Listagem 1:** Pegando o atributo src de uma imagem com jQuery

<pre class="lang-javascript">$("#imagem").attr("src");</pre>

Poderíamos usar simplesmente o JavaScript para ter o mesmo resultado usando o código da **Listagem 2**.

**Listagem 2:** Pegando o atributo src de uma imagem com JavaScript

<pre class="lang-javascript">document.getElementById("imagem").src;</pre>

A intenção do artigo não é desencorajar ninguém a deixar de usar jQuery, mas para quem quer ser um bom front end, um ninja front end, é bom começar a estudar o JavaScript puro. Muitos desanimam ao estudar essa tecnologia por causa da maneira um pouco &#8220;diferente&#8221; de obter um efeito legal e com um código curto, como acontece com o jQuery, mas com o JavaScript puro dá para se ter efeitos, digamos “muito show”.

Muito bem, chega de conversa, vamos dar inicio ao nosso treinamento “ninja”&#8230;

## Estrutura HTML e CSS

Vamos criar um pequeno exemplo para mostrar os efeitos fadeIn e fadeOut. Primeiro vamos elaborar nossa estrutura HTML, criando uma div que irá sofrer o efeitos através de dois botões.

**dica:** _Antes de criar algum efeito com javascript ou qualquer outra biblioteca javascript, sempre seguimos estas três ordens: Primeiro construimos a estrutura html, depois elaboramos o nosso estilo com o css, e por último, começamos a brincar com as nossas linhas de códigos javascript_

Observe a **Listagem 3**.

**Listagem 3:** Estrutura html5 simples

<pre class="lang-html">&lt;!doctype html&gt;
&lt;html lang="pr-br"&gt;
 &lt;head&gt;
   &lt;meta charset="UTF-8"&gt;
   &lt;title&gt;Meu primeiro efeito ninja em js&lt;/title&gt;
 &lt;/head&gt;
&lt;body&gt;
    &lt;section id="objeto"&gt;&lt;/section&gt;
    &lt;button id="fadeIn"&gt;&lt;/button&gt;
    &lt;button id="fadeOut"&gt;&lt;/button&gt;
 &lt;/body&gt;
&lt;/html&gt;</pre>

A marcação html é simples, temos uma tag section, que sofrerá as mudanças de opacidade, determinadas como fadeIn e fadeOut. Temos também dois botões qualquer, que serão responsáveis por chamar as funções de acordo com seu “id”.

Em seguida, aplicamos nosso style,conforme a **Listagem 4**.

**Listagem 4:** Estilo CSS

<pre class="lang-css">&lt;style type="text/css"&gt;
   section {
      width: 150px;
      height: 100px;
      background: red;
   }
&lt;/style&gt;</pre>

Note que só estilizamos a tag section, pois o estilo do botão não é relevante neste exemplo, só é necessário uma cor de fundo na section para que possamos visualizar ela sumindo e aparecendo.

agora iremos aplicar a função dos botões quando o documento for carregado. Observe a **Listagem 5**.

**Listagem 5:** Anexando a função de clique nos botões quando o documento for lido

<pre class="lang-javascript">&lt;script type="text/javascript"&gt;
 window.onload = function(){
	var objeto = document.getElementById('objeto');
    document.getElementById("fadeIn").onclick = function(){
  	fadeIn(objeto,1);
    }
   document.getElementById("fadeOut").onclick = function(){
 	fadeOut(objeto,1);
   }
 }
&lt;/script&gt;</pre>

Nestas linhas de códigos acima, anexamos a função de clique para os botões e, de acordo com seu “id”, chamamos a função de fadeIn e/ou fadeOut

Em seguida, criaremos as funções fadeIn (que servirá para determinar quando elemento irá aparecer) e fadeOut (para determinar quando o elemento irá sumir), conforme as **Listagens 6** e **7**.

**Listagem 6:** Função  fadeIn

<pre class="lang-javascript">function fadeIn(element,time){
   processa(element,time,0,100);
 }</pre>

**Listagem 7: **Função fadeOut

<pre class="lang-javascript">function fadeOut(element,time){
  processa(element,time,100,0);
 }</pre>

Estas funções tem como parâmetros element, time, intial, e end, onde:

·        element &#8211; Elemento que sofrerá o fadeIn ou fadeOut;

·        time &#8211; Tempo que o fade acontecerá (neste caso, um segundo);

·        initial &#8211; Estado inicial do elemento;

·        end &#8211; Estado final do elemento.

Agora criaremos uma função que será responsável por processar os efeitos de fadeIn e fadeOut, conforme abaixo:

<pre class="lang-javascript">function processa(element,time,initial,end){
    //cógigo
}</pre>

No escopo da nossa função, declararemos uma variável responsável pelo incremento (no caso do fadeIn) ou decremento (no caso do fadeOut) do efeito. Esta variável será a chave principal para setar o efeito na opacidade do nosso elemento. Observe a **Listagem 8.**

**Listagem 8**. Criação da variável de incremento da função processa

<pre class="lang-javascript">if(initial == 0){
  increment = 2;
   element.style.display = "block";
}else {
  increment = -2;
}</pre>

Se o estado inicial do elemento for igual a zero, declaramos o incremento como positivo para que o elemento possa aparecer, colocando-o com um display:block. Mas se o estado inicial do elemento for diferente de zero, então declaramos o incremento como negativo, assumindo o efeito de fadeOut

Agora iremos declarar a opacidade inicial do nosso elemento, declarando uma variável cujo nome será &#8220;opc&#8221; que irá “sofrer” as mudanças de incremento ou decremento. Observe a **Listagem 9.**

**Listagem 9:** declaração da variável de opacidade

<pre class="lang-javascript">if(initial == 0){
  increment = 2;
   element.style.display = "block";
}else {
  increment = -2;
}
opc = initial;</pre>

_**Obs:** Declaramos a variável “opc”, porque iremos precisar do valor “initial” para fazer uma verificação, em um loop mais na frente, mas também iremos precisar que o valor da variável “initial” também mude para que possamos aplicar as mudanças na tag section_

Agora iremos criar um intervalo para simular o efeito fadeIn / fadeOut no nosso elemento. Este intervalo irá se repetir em um intervalo de 10 milissegundos, pois queremos que aconteça o fade em um segundo (1 \* 10) == (time \* 10), conforme a **Listagem 10.**

**Listagem 10:** Intervalo responsável por aplicar efeito de fadeIn ou fadeOut

<pre class="lang-javascript">intervalo = setInterval(function(){
},time * 10);</pre>

Dentro do nosso intervalo verificaremos se a variável opc chegou ao estado final, ou seja, se o intervalo completar o efeito de fade limpamos o mesmo, pois ele não será mais necessário. Observe a **Listagem 11.**

**Listagem 11:** Verificando se o fade foi completado

<pre class="lang-javascript">intervalo = setInterval(function(){
  if((opc == end)){
	if(end == 0){
  	element.style.display = "none";
	}
	clearInterval(intervalo);
  }
},time * 10);</pre>

Note que foi feita uma nova verificação para ver se o estado final do elemento é zero. Se está em zero, então teremos que esconde-lo para que não ocupe espaço na tela.

Logo após a verificação, setaremos a opacidade do nosso elemento, conforme a **Listagem 12.**

**Listagem 12:** setando a opacidade do elemento

<pre class="lang-javascript">}else {
  opc += increment;
  element.style.opacity = opc/100;
  element.style.filter = "alpha(opacity="+opc+")";
}</pre>

Os comandos dentro deste bloco serão executados a cada 10 milissegundos. Na linha “opc += increment;”, a opacidade incrementa ou decrementa. Por exemplo, se a opacidade for 0, o incremento é positivo e teremos a seguinte repetição:

0 + 2= 2 (na primeira execução do loop);

2 + 2 = 4 (na segunda execução do loop);

(&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;)

98 + 2 = 100 (na ultima execução do loop);

Mas se a variável opc for  maior que  0 (no caso 100), significa que o incremento é positivo, pois no topo do escopo da nossa função processa(), temos uma verificação do parâmetro “initial”, e se initial não for igual a zero (que declaramos a variável opc = initial) a variável increment é negativa. Logo teremos a seguinte função:

100 &#8211; 2= 98 (na primeira execução do loop);

98 &#8211; 2 = 96 (na segunda execução do loop);

(&#8230;&#8230;&#8230;&#8230;&#8230;)

98 &#8211; 2 = 100 (na ultima execução do loop);

Já na linha “element.style.opacity = opc/100;” seta a opacidade no elemento.

E quem disse que o nosso efeito não é cross browser? Esta linha abaixo faz o nosso efeito de opacidade funcionar no ie8 até o ie6,

<pre class="lang-javascript">Element.style.filter = “alpha(opacity=”+opc+”)”;</pre>

O Internet Explorer do 8 abaixo, interpreta a propriedade filter:alpha(opacity=100) como opacity:1;

Disponibilizei o código no github, [clique aqui.][1]

_Um forte abraço e até a próxima._

 [1]: https://github.com/clovisdasilvaneto/fadein-fadeout-com-javascript-puro "código do post"