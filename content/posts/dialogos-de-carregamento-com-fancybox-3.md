Ei! Você aí que vem usando o [**fancyBox**][1] já faz anos (ou não) e nunca reparou que a biblioteca tem um diálogo de carregamento super útil, bem, esse post é pra você!

Na verdade, é bem simples utilizar o **fancyBox 3** como um diálogo de carregamento, ainda mais que a versão recém chegada da biblioteca tá de cara nova ~(é pra glorificar de pé)~ e o diálogo de carregamento ficou a coisa mais querida!

Após ter instalado e configurado o **fancyBox** em seu site, você só precisa o seguinte código para abrir o famoso plugin **jQuery** como o tal diálogo de carregamento:

```javascript
// Abre o fancyBox!
var activityIndicator = $.fancybox.open('', {
    protect: true, // Desabilita clique direito e cria uma proteção simples
    keyboard: false, // Desabilita o teclado
    touch : {
        vertical: false,  // Impede o diálogo de ser arrastado verticalmente
        momentum: false   // Desabilita animações contínuas para "drag"s
    },
    clickContent: function (current, event) { return false }, // Desabilita o clique no geral
    mobile: { clickContent: function (current, event) { return false } }, // Desabilita o clique no geral
});

// A seguir é exibido o spinner!
activityIndicator.showLoading();
```

Pô! Massa! Agora que tenho o diálogo, como fecha?!

É muuuuito simples:

```javascript
// Fecha o diálogo!
activityIndicator.close();
```

---
title: Diálogos de carregamento com o fancyBox 3
author: Luiz Barni
type: post
date: 2017-09-24
excerpt: Este artigo ensina você a utilizar os diálogos do fancyBox 3 como diálogos de carregamento!
categories:
  - Browsers
  - Destaques
  - jQuery
  - fancyBox
---

[1]: http://fancyapps.com/fancybox/3/
