---
title: Javascript Observe
author: João Felix
type: post
date: 2014-02-20
excerpt: A futura implementação do Javascript Harmony capaz de observar e notificar aplicações sobre as mudanças ocorridas em objetos Javascript.
url: /javascript-observe/
dsq_thread_id: 2277082767
categories:
  - Código
  - JavaScript
  - Técnicas e Práticas

---
O [ECMAScript 6][1] (codinome Harmony ou ES.next) já não é novidade para quem acompanha de perto os avanços do desenvolvimento web, e suas especificações já bem avançadas causam um certo alvoroço a respeito de como vais ser o futuro do Javascript.

Uma das esperadas especificações é o Object.observe, que documenta a capacidade de observar e notificar aplicações sobre as mudanças ocorridas em objetos Javascript, recurso bastante requisitado em aplicações funcionais.

O uso de funcionalidades similares já é possível com algumas bibliotecas como o [Watch.js][2] e também por frameworks como o [Backbone][3] (além de outros), permitindo a criação de mecanismos declarativos e independentes das demais implementações da aplicação.

Para começar, precisamos entender o que esta funcionalidade é capaz de observar um objeto:

  * As mudanças no valor das propriedades;
  * A adição, exclusão e reconfiguração de todas as propriedades visíveis através das APIs de reflexão;
  * Mudanças no protótipo e extensibilidade do próprio objeto.

A [API pública][4] atual disponibiliza as seguintes métodos:

##  Object.observe(Object, callback[, accepts])

Trata-se do método principal da API que é responsável pela funcionalidade de observar um objeto e sua assinatura é bastante simples, sendo necessário apenas informar o objeto a ser observado, a função a ser executada quando alguma notificação for disparada e opcionalmente um vetor de tipos de notificações a serem manipuladas (os tipos de notificações permitidas são: ”add”, “update”, “delete”, “reconfigure”, “setPrototype” e “preventExtensions”); Esta chamada pode ser executada quantas vezes for necessário (você pode querer executar callbacks distintos).

Sua utilização segue o seguinte exemplo:

<pre class="lang-javascript">function observer(regs) { 
   console.log(regs); 
} 
var obj = { id: 1 }; 
Object.observe(obj, observer); 
obj.a = 'b'; 
obj.id++;</pre>

A saída desta rotina, desconsiderando as propriedades herdadas pelo argumento regs, <span style="line-height: 1.5em">seria uma lista de objetos de notificações:</span>

<pre class="lang-console">&gt; [{
     name: "a",
     object: {id: 2, a: "b"},
     oldValue: "b", 
     type: "updated" 
  },{ 
     name: "id", 
     object: {id: 2, a: "b"}, 
     type: "new"
  }]</pre>

## Object.unobserve(Object, callback)

Eventualmente, poderá ser necessário não acompanhar mais as notificações de um determinado objeto, ou apenas interromper a execução de um callback especifico; Para isso, basta executar conforme o exemplo, especificando o objeto observado e o callback a ser removido:

<pre class="lang-javascript">function updateObserver(regs) { 
   regs.forEach(function(notification){
      if(notification.type === "updated"){
         console.log(notification);
      }
   });
}
function deleteObserver(regs) { 
   regs.forEach(function(notification){
      if(notification.type === "deleted"){
         console.log(notification);
      }
   });
} 
var obj = { id: 1 }; 
Object.observe(obj, updateObserver); 
Object.observe(obj, deleteObserver); 
obj.id++; 
Object.unobserve(obj, deleteObserver); 
delete obj.id;</pre>

A saída desta rotina, também seria uma lista de objetos de notificações:

<pre class="lang-console">&gt; [{
     name: "id",
     object: {},
     oldValue: 1, 
     type: "updated" 
  }]</pre>

## Array.observe(Object, callback)

É apenas um atalho, equivalente a:

<pre class="lang-javascript">function(obj, callback) {
    return Object.observe(obj, callback, ["add", "update", "delete", "splice"]);
}</pre>

## Array.unobserve(Object, callback)

Outro atalho, equivalente a:

<pre class="lang-javascript">function(obj, callback) {
    return Object.unobserve(obj, callback);
}</pre>

## Object.deliverChangeRecords

Se notarmos o primeiro exemplo utilizado no método Object.observe, é possível perceber que a lista de notificações foi entregue de forma acumulada em um vetor, ou seja, no final de todas as alterações. Caso seja necessário intervir de forma antecipada o método Object.deliverChangeRecords garante uma chamada imediata do callback especificado (necessita ser um callback já aplicado) com uma lista das notificações pendentes:

<pre class="lang-javascript">function observer(regs) { 
   console.log(regs); 
} 
var obj = { id: 1 }; 
Object.observe(obj, observer); 
obj.a = 'b'; 
obj.id++;
console.log('Primeira chamada');
Object.deliverChangeRecords(observer);
obj.b = 'c'; 
console.log('Segunda chamada');
Object.deliverChangeRecords(observer);</pre>

Esta execução revelaria duas pilhas de notificações:

<pre class="lang-console">&gt; Primeira chamada
&gt; [{
     name: "a",
     object: { a: "b", b: "c", id: 2 },
     type: "new"
  },{
     name: "id"
     object: { a: "b", b: "c", id: 2 }
     oldValue: 1
     type: "updated"
  }]
&gt; Segunda chamada
&gt; [{
     name: "b",
     object: {a: "b", b: "c"},
     id: 2,
     type: "new"
  }]</pre>

## Object.getNotifier

Permite recuperar o objeto notificador e forçar uma notificação através do método notify():

<pre class="lang-javascript">var obj = { id: 1 };
function basicObserver(changeList){
   changeList.forEach(function(change){
      console.log(change);
   });
}
Object.observe(obj,basicObserver); 
Object.getNotifier(obj).notify({ type: "new", name: "id" });</pre>

É importante observarmos que implementações nativas tendem a ter um desempenho superior às implementações customizadas (ex. frameworks), e considerando este como apenas um dos aspectos das futuras implementações do ECMAScript 6 já podemos afirmar que elas representam um passo importante para a maturidade do desenvolvimento web.

Caso você não queira aguardar sentado o Javascript Harmony existem algumas alternativas como o [Object.observe][5] (polyfill/shim) ou a utilização do [Chrome Canary][6] com a flag &#8220;Enable Experimental JS APIs&#8221; ativada.

 [1]: http://wiki.ecmascript.org/doku.php
 [2]: https://github.com/melanke/Watch.JS
 [3]: http://backbonejs.org/#Events-listenTo
 [4]: http://wiki.ecmascript.org/doku.php?id=harmony:observe_public_api
 [5]: https://github.com/jdarling/Object.observe
 [6]: https://www.google.com/intl/pt-BR/chrome/browser/canary.html "Chrome Canary"