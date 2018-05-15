---
title: Repaint, Reflow e Layout Thrashing - Performance além do carregamento
authors: Morais Junior
type: post
image: https://csharpcorner-mindcrackerinc.netdna-ssl.com/article/important-steps-to-increasing-web-api-performance/Images/pp.png
date: 2018-05-14
excerpt: Neste artigo falaremos sobre renderização e boas práticas na manipulação do DOM :)
categories:
  - JAVASCRIPT
  - Browsers  
  - HTML
---
A Web tem mudado muito nos últimos anos, temos cada vez mais acessos através de dispositivos móveis é cada vez mais o usuário espera que as páginas sejam simples e interativas, temos vários serviços rodando em paralelo, recursos dinâmicos como players de vídeos ou áudio embutidos, então é imprescindível dedicar nosso tempo  performance de renderização e evitar o Layout Thrashing.

Layout Thrashing é uma falha na renderização que ocorre quando o javascript lê ou escreve no DOM várias vezes, causando reflow na página (travamento), quando alteramos alguma propriedade de uma DIV por exemplo o navegador faz uma invalidação do layout e tem que recalcular toda a página, porém ele espera o próximo frame para fazer o reflow, se nesse intervalo fizermos alguma leitura no DOM o navegador é forçado a recalcular o layout antes, o que é conhecido como forced synchronous layout ou layout síncrono forçado, fazendo com que ocorrem travamentos e quebras de performance.

Atualmente, a maioria dos dispositivos atualiza as telas 60 vezes por segundo, isso quer dizer que o navegador tem que entregar um novo frame a cada 16ms, nesse período o navegador tem que fazer todas as escritas no DOM, leituras e redesenhar o layout, se você tem qualquer script atrasando esse processo temos uma quebra na taxa de 60fps e um caso de Layout Thrashing.

Tendo entendido todo o processo, lhe dou agora a boa notícia, existem várias ferramentas que cuidam de controlar todo esse fluxo, dentre elas a minha preferida [FastDOM](https://github.com/wilsonpage/fastdom "FastDOM") :)---

Você pode instalar pelo NPM:
> $ npm install fastdom --save

A utilização é muito simples segue um exemplo:
```javascript
fastdom.read(function() { //aqui você faz as leituras no DOM
    var h1 = element1.clientHeight;
    fastdom.write(function() { //agora as escritas
        element1.style.height = (h1 * 2) + 'px';
    });
});

```
# Caminho das pedras
O método window.requestAnimationFrame() fala para o navegador que deseja-se realizar uma alteração no DOM e pede que o navegador chame uma função específica para atualizar um quadro de animação antes da próxima repaint (repintura), com ele conseguimos agendar para que a mudança seja executada somente no próximo frame.

Ná prática a implementação é bem simples, se baseia que temos que fazer primeiro todos os cálculos necessários e somente depois de tudo pronto "agendar" a modificação no DOM, segue um ex:

```javascript
var start = null;
var element = document.getElementById("ElementoQueVcQuerAnimar");
element.style.position = 'absolute';

function frame(timestamp) {
  if (!start) start = timestamp;
  var progress = timestamp - start;  
  element.style.left = Math.min(progress/10, 200) + "px";//efetiva a alteração no DOM
  if (progress < 2000) {
    window.requestAnimationFrame(frame);//agenda a próxima alteração
  }
}

//inicia a primeira alteração
window.requestAnimationFrame(frame);
```
Antigamente só tínhamos os métodos de tempo como o setInterval, setTimeOut mais não era a melhor forma de fazer isso.

# Conclusão
Atualmente temos cada vez mais dispositivos acessando a WEB, e muitas vezes com poucos recursos de memória, devemos sempre nos preocupar com a performance de renderização e garantir a melhor performance possível em todos os dispositivos, mesmo que ao preço de uma pequena curva de aprendizado e uso de uma porcentagem maior de código.
