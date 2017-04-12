---
title: Fluxo de execução assíncrono em JavaScript – Callbacks
author: Jean Carlo Emer
type: post
date: 2015-07-27
excerpt: Este é o primeiro artigo de uma pequena série a respeito de execução de código assíncrono. Definiremos o que é fluxo de execução e veremos o que é e quão importante é dominar as callbacks na escrita de código JavaScript.
url: /fluxo-de-execucao-assincrono-em-javascript-callbacks/
categories:
  - Código
  - JavaScript
  - Técnicas e Práticas

---
O fluxo de execução de um programa é determinado pela ordem em que suas instruções são executadas. Tradicionalmente a execução é sequencial e segue a ordem em que as instruções aparecem no código fonte do programa.

Existem instruções especiais que podem guiar o fluxo de execução, seja pela imposição de uma decisão, repetição ou pulo. No JavaScript, temos como exemplo `if`, `for`, `while`, `try catch`, `return`, dentre outros (como `break` e `continue` que podem ser usados de um [jeito peculiar][1]).

Como a maioria das linguagens de programação, o JavaScript foi projetado para funcionar com um único fluxo de execução. Apenas uma instrução do seu código será processada em um determinado instante. No ambiente do navegador, seu código JavaScript ainda terá que disputar vaga com o [_rendering_][2] (_layout_ e _paint_) da página. **Isto significa que o navegador não conseguirá posicionar ou desenhar um elemento na tela ao mesmo tempo que executa JavaScript e vice-versa**.

## Fluxos assíncronos

Mesmo que projetado para ter um único fluxo de execução, algumas tarefas do seu programa JavaScript poderão ser executadas sem interferir em nada o fluxo principal de execução de código. Essas tarefas são conhecidas como fluxos assíncronos. **Você pode disparar uma série dessas tarefas sem precisar esperar que cada uma se complete para prosseguir**. Nos computadores atuais, que possuem mais de um núcleo de processamento, algumas tarefas do escopo do seu programa poderão inclusive ser executadas no mesmo instante do seu código.

Isso pode parecer um pouco complicado e um exemplo pode ajudar. Toda vez que você dispara uma [requisição Ajax][3], a comunicação com o servidor e o recebimento dos dados ocorre em paralelo a execução de outras linhas do seu programa. **Quando tudo estiver pronto, você será avisado no mesmo fluxo de execução que disparou a requisição, e então poderá usar sua resposta**.

Os navegadores possuem uma série de APIs e funções que executam em fluxos assíncronos. Abaixo a lista das mais relevantes:

### Timers

As funções `setTimeout` e `setInterval` criam contadores que irão avisar seu programa que determinado período de tempo se passou de forma assíncrona.

### Comunicação com servidor

As APIs para comunicação Ajax e outras que implementam os vários [protocolos de comunicação que fazem parte da Web][4] são assíncronas.  Web Sockets e Server Sent Events criam conexões permanentes com o servidor no navegador, retornando dados ao longo do tempo para nosso código.

### Eventos do DOM

Através dos eventos do DOM é possível perceber interações do usuário e monitorar mudanças de estado do documento. Como o usuário pode reagir a qualquer instante, o tratamento obrigatoriamente precisa se dar de forma assíncrona. Não é viável bloquear o fluxo de execução principal a espera de um clique.

### Mensagens

A função `window.postMessage` e o tratador de evento de recebimento de mensagem, permitem, respectivamente, enviar e receber mensagens de forma assíncrona entre diferentes páginas (ou _iframes_) abertas no navegador.

### Mutation Observers

Os Mutation Observers permitem assistir a mudanças no documento. Através destes, é possível ser avisado a cada alteração de atributo, criação, remoção ou alteração de elementos da página. Seu comportamento e justificativa de existência é a mesma dos eventos do DOM.

## Callbacks e closures

As chamadas de função que executam em um fluxo assíncrono fazem uso de _callbacks_. _Callbacks_ são porções de código que serão executados no futuro, em um tempo conveniente.

O JavaScript interage com os fluxos assíncronos através de troca de mensagens. Sempre que uma tarefa assíncrona entra em ação, a _callback_ é registrada e fica a espera de uma mensagem para ser executada. **Existe então um loop de eventos que aguarda por mensagens** emitidas por _timers_, requisições, eventos do DOM e outras chamadas assíncronas.

As mensagens, quando recebidas, são mantidas em uma fila e disparam a execução da _callback_, uma por vez. É importante notar que duas _callbacks_ não são disparadas no mesmo instante. Existe um único fluxo de execução JavaScript nos navegadores e as _callbacks_ são executadas nele também.

> Tudo é executado em paralelo, exceto o seu código &#8211; Mikito Takada

As _callbacks_ **possuem acesso às variáveis do escopo em que foram definidas**, por isto são chamadas _closures_. Apesar disto, _callbacks_ não são executadas no mesmo escopo em que definidas.

## Quebrando o fluxo de execução

Quando escrevemos código para adicionar interatividade a uma página, existem algumas situações que pode ser interessante que o fluxo de execução não seja contínuo. Como vimos anteriormente, a execução de nosso código é compartilhada com o _rendering_ da página. Qualquer execução que tome um pouco mais de tempo, irá bloquear a interface e transmitir uma impressão de lentidão para o usuário.

Um artifício que pode ser usado para permitir que o _rendering_ não seja prejudicado é quebrar a execução de uma tarefa em fatias. Para isto, será preciso dividir a tarefa em _callbacks_ e fazer uso de recursos que criem fluxos assíncronos. A mais simples das funções que conhecemos já pode ajudar: `setTimeout(callback, 0)`.

A cada chamada de `setTimeout` um fluxo assíncrono será criado para gerenciar um temporizador. Assim que as demais instruções forem executadas, o fluxo principal será interrompido. O navegador poderá então utilizar seus recursos para fazer tarefas relacionadas ao _rendering_, garantindo assim uma interface fluída para o usuário. Quando tais tarefas terminarem, o temporizador de zero segundos já deverá ter disparado uma mensagem a ser atendida pelo _loop_ de eventos do JavaScript. A _callback_ será disparada.

Usar `setTimout`, apesar de ser um truque baixo, irá funcionar bem para tarefas simples. Porém, existe uma limitação em sua especificação. Sempre que _callbacks_ disparadas por um temporizador criarem outro temporizador, este terá tempo mínimo de 4 milissegundos. Existe uma [especificação em andamento para definir a função `setImmediate`][5]. E para jogos e animações, melhor mesmo é usar a [função `requestAnimationFrame`][6] que cria um novo fluxo de execução logo após o _rendering_.

## Problemas das callbacks

O único mecanismo que o JavaScript oferece para gerenciar fluxos de execução assíncronos são as _callbacks_. É provável que no futuro tenhamos os [Generators][7] e [Async Functions][8]. Mas por enquanto todas as APIs recebem apenas _callbacks_.

O problema é que alguns códigos que utilizam _callbacks_ são frequentemente mal compreendidos. O código abaixo, apesar de parecer, não irá mostrar um contador regressivo para o usuário. Como já mencionado, o que as _closures_ enxergam são variáveis e não valores.

    for (var i=0; i<4; i++) {
        setTimeout(function () {
            alert(4-i)
        }, i*100)  
    }
    

A solução para o código acima é utilizar o `.bind` para armazenar os diferentes valores de `i`. Uma solução melhor ainda é reescrever este algoritmo seguindo um estilo mais funcional:

    Array.apply(null, Array(4)).forEach(function (undef, index) {
        setTimeout(function () {
            alert(4-index)
        }, index*100)  
    })
    

Outra confusão comum envolve excessões. Observe o código a seguir e tente prever seu comportamento:

    try {
        setTimeout(function () {
            throw "Exception"
        }, 100)
    }
    catch (e) {}
    

A exceção emitida pela _callback_ não será coletada e explodirá direto para o usuário. A _callback_, quando executada, não estará mais sendo assistida pelo bloco de tratamento de exceção. Um novo bloco de tratamento deve ser criado no interior da função.

O valor que o `this` irá representar no interior da _callback_ algumas vezes gera dúvidas. Esqueça! Geralmente é uma má ideia utilizar o `this` nestes casos. Se for preciso, é bom recorrer ao `.bind` da _callback_ com o valor que se espera que o `this` represente. Logo será possível utilizar também [Arrow Functions][9] para contornar este problema.

Por fim, há desenvolvedores que argumentam contra _callbacks_ pelo uso destas resultar em um código confuso e com alto acoplamento. O site [Callback Hell][10] ensina de forma prática como evitar o temido _callback hell_ (sic).

Apesar de todos estes problemas e confusões, as _callbacks_ são simples e poderosas.

<p style="text-align: center;">
  ***
</p>

Espero que tenha aproveitado a leitura. <span style="text-decoration: line-through;">No próximo artigo da série, veremos algumas limitações reais das <em>callbacks</em>. Seremos apresentados às <em>promises</em>, que irão garantir uma escrita de código melhor em determinadas circunstâncias. Até lá.</span> [O próximo artigo da série que fala sobre _promises _já saiu][11].

 [1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label#Using_a_labeled_continue_with_for_loops
 [2]: https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction
 [3]: https://en.wikipedia.org/wiki/Ajax_(programming
 [4]: https://speakerdeck.com/jcemer/protocolos-de-comunicacao-que-fazem-parte-da-web
 [5]: https://github.com/YuzuJS/setImmediate
 [6]: https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame
 [7]: http://www.2ality.com/2015/03/no-promises.html
 [8]: http://jakearchibald.com/2014/es7-async-functions/
 [9]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
 [10]: http://callbackhell.com
 [11]: http://tableless.com.br/fluxo-de-execucao-assincrono-em-javascript-promises/