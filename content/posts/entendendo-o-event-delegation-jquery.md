---
title: Entendendo o Event Delegation da função on() no jQuery
author: Diego Eis
type: post
date: 2015-02-02
excerpt: 'Um pouco sobre event delegation com a função <code>on()</code> do jQuery.'
url: /entendendo-o-event-delegation-jquery/
categories:
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - event delegation
  - JQuery
  - performance

---
Geralmente uma &#8220;delegação&#8221;, que seria a uma tradução livre para **delegation**, significa definir um evento para um elemento pai, que será disparado para todos os seus filhos. O evento vai funcionar para qualquer elemento filho que já existir e também para os que forem adicionados posteriormente na árvore do DOM.

Para exemplificar, entenda o código abaixo. Ele apenas muda o texto do parágrafo quando clicamos em alguma opção do menu. É um uso simples da função `on('click')` do jQuery:



Para entender como isso funciona, você precisa saber o que é o `event propagation` (ou `event bubbling`): toda vez que você clica em um elemento, esse clique é propagado para toda a árvore do DOM, iniciando pelo elemento onde o evento aconteceu e chegando até o root do documento, que no nosso caso é a tag HTML. 

Além disso, você faz seu browser ouvir o click em todos os elementos desse nosso menu, se considerarmos o exemplo acima. Nesse nosso caso, não chega a ser um problema, mas imagine em uma tabela que tem muitas células e que você precisa executar alguma coisa quando alguma das `td` é clicada. A performance começa a ser prejudicada.

Quando usamos o **event delegation** ao nosso favor, podemos definir o evento no elemento pai e então, quando esse evento acontecer, delegamos para o seu filho. No nosso exemplo acima, nós vamos atrelar o evento de click no `ul.menu`, mas delegando esse evento para os links. A função em si nem muda tanto, ela fica assim:

<pre class="lang-javascript">$('.menu').on('click', 'a', function(evt){
        // Seu código...
    });
</pre>

Perceba que a função `on()` recebe dois parâmetros: o primeiro é o evento e o segundo é o elemento filho que esse evento deve ser aplicado. 



Suponha que você tenha alguma função que adiciona mais filhos ao seu elemento pai. A propagação continua funcionando, já que o evento está atrelado ao pai e não aos seus filhos. 

Lembrando que a função `on()` foi adicionada no jQuery 1.7, para juntar as vantagens das funções `delegate()` e `live()`. 

Há uma [análise de performance no JSPerf][1] comparando o várias maneiras para você delegar os eventos aos filhos de um elemento. O `delegate()` tem quase a mesma performance que o `on()`, mesmo assim é melhor usar o `on()`, já que ele tem mais vantagens.

 [1]: http://jsperf.com/jquery-event-delegation/5