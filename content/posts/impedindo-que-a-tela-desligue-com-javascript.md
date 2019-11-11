---
title: Impedindo que a tela desligue com JavaScript
authors: Matheus Alves
type: post
image: https://source.unsplash.com/mqyMjCTWJyQ/748x500
date: 2019-05-07
excerpt: Como podemos impedir que a tela do usuário entre no modo de descanso
categories:
  - JavaScript
  - Mobile
tags:
  - Acessibilidade
---

Recentemente o *power button* do meu *smartphone* estragou e eu tive que começar a me virar sem ele. A princípio, naturalmente, eu não conseguia desligar a tela e o tempo de inatividade antes do seu desligamento era de 5 minutos - o que é muito tempo para se esperar antes de colocá-lo no bolso. Desse modo, antes de eu querer concertar o dispositivo, procurar um aplicativo ou qualquer coisa que seja para resolver o meu problema, decidi configurar o tempo máximo de inatividade para somente 15 segundos.

Ou seja: se eu não tocar a tela em 15 segundos, ela desliga. Bem simples!

## Problemas

No entanto, notei alguns problemas ao fazer isso logo após tentar ler alguns artigos longos na *internet* pelo *browser*, pois a tela sempre desligava durante a leitura, porque nesses casos o tempo sem tocar a tela do dispositivo aumenta - principalmente se você está lendo algum artigo onde há muitas ilustrações, fórmulas ou códigos que devem ser analisados por um tempinho um pouco maior.
Até que eu notei algo bem interessante que ocorria no aplicativo do [Instapaper](https://www.instapaper.com/), que além de lhe oferecer um vasto número de utilitários e personalização durante a leitura de um texto, também impede que a tela desligue enquanto você está a lê-lo, assim como quando você assiste um video.

> Obs.: O Instapaper é um aplicativo que lhe permite salvar o texto principal de um site, aplicativo ou qualquer coisa do gênero para ler mais tarde, quando estiver desconectado da internet por exemplo.

## Soluções

Depois de ver essa funcionalidade, fiquei me questionando se haveria alguma forma de impedir que a tela desligue utilizando JavaScript dentro de um *browser*. Fiz algumas pesquisas no Google e as duas primeiras coisas relevantes que encontrei foram: *Wake Lock API* e *NoSleep.js*.

A primeira, *Wake Lock API*, eu encontrei no artigo [*I’m Awake! Stay Awake with the WakeLock API*](https://developers.google.com/web/updates/2018/12/wakelock), do Pete LePage no Google Developers, que é uma API para os navegadores que basicamente permite manter o "dispositivo acordado", só que ela ainda está em progresso e aparentemente funciona apenas no Google Chrome e com a *flag* `#enable-experimental-web-platform-features` habilitada nele, portanto, isso ainda não é ainda nem um pouco útil para os dias de hoje.

A segunda, [*NoSleep.js*](https://github.com/richtr/NoSleep.js), é uma biblioteca criada pelo Rich Tibbett que eu encontrei no GitHub e que lhe permite fazer algo bem semelhante ao *Wake Lock API*, no entanto, com algo que alguns podem chamar de gambiarra. O fato é que uma tela não descansa se o usuário estiver assistindo um vídeo, certo?! Desse modo, o *NoSleep.js*, enquanto estiver ativado, apenas dá *play* num video em segundo plano fazendo o navegador entender que o usuário está assistindo algo e evitando assim o desligamento dela. O video em questão não apresenta nenhum vestígio de seu comportamento para o usuário, pois além de ser mudo nem chega a ser inserido na `<body>` do HTML, além de ser muitíssimo leve.

## Uso do NoSleep.js

Usar essa biblioteca é extremamente simples, onde você possui apenas dois modos: ativado e desativado. O primeiro faz com que a tela não descanse e o segundo, obviamente, deixa a tela no modo normal.

É possível obter o NoSleep.js pelo [NPM](https://www.npmjs.com/), [Bower](https://bower.io/) (que já [foi descontinuado](https://snyk.io/blog/bower-is-dead/)) ou diretamente pelo *download* do código-fonte no GitHub.

Depois de tê-lo instalado, antes de usá-lo você deve instanciar um objeto a partir da classe  `NoSleep`.

```javascript
var noSleep = new NoSleep();
```

Após isso, a variável `noSleep` armazenará um objeto com dois métodos: `enable` (para ativar) e `disable` (para desativar). Algo curioso e que certamente é um ponto negativo dessa biblioteca é a obrigatoriedade do método `enable` ser chamado dentro de um [evento](https://www.w3schools.com/jsref/dom_obj_event.asp) de entrada do usuário, como um `click`. Por exemplo, supondo que `button` é o elemento de um botão qualquer da sua página então você deve fazer isso para ativar o NoSleep.js:

```javascript
button.addEventListener('click', () => {
  noSleep.enable();
});
```

Já para desativá-lo, basta usar `noSleep.disable()` em qualquer lugar do código, não havendo a necessidade de estar encapsulado em um evento do usuário.

## Conclusão

Você pode experimentar um [exemplo aqui](https://theuves-demos.github.io/no-sleep-demo/), observando que é extremamente aconselhável que seu dispositivo esteja com um tempo limite de tela baixo, caso contrário você poderá perder muito tempo esperando até cair a fixa de que a demonstração está funcionando.

Esse é um utilitário simples e que em alguns casos para determinados usuários pode não fazer absolutamente nenhuma diferença, mas que para outros, como foi o meu, pode fazer uma falta gigantesca, não somente para leitura dum texto (que talvez seja um caso mais incomum), mas também para jogos, páginas com animações ou simples aplicativos como o de um cronômetro.
