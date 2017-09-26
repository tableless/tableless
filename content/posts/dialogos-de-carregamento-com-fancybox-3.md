---
title: Diálogos de carregamento com o fancyBox 3
author: Luiz Barni
type: post
date: 2017-09-24
image: https://i.ytimg.com/vi/djlx7xdwlpI/maxresdefault.jpg
excerpt: Como utilizar os diálogos de carregamento do fancyBox 3 para melhorar a UX do seu site!
categories:
  - JavaScript
  - UX e Design
  - jQuery
  - HTML
---

Ei! Você aí que vem usando o [**fancyBox**][1] já faz anos (ou não) e nunca reparou que a biblioteca tem um diálogo de carregamento super útil, bem, esse post é pra você!

# Não sabe o que é o fancyBox?

O fancyBox é um plugin jQuery que fornece uma biblioteca de diálogos, entre eles modais, galerias, exibição única de imagem, incorporação de mídia, como YouTube e Vimeo, entre várias outras coisas.

# Utilizando o fancyBox

Na verdade, é bem simples utilizar o **fancyBox 3** como um diálogo de carregamento, ainda mais que a versão recém chegada da biblioteca tá de cara nova ~(é pra glorificar de pé)~ e o diálogo de carregamento ficou a coisa mais querida!

Após ter instalado e configurado o **fancyBox** em seu site, você só precisa o seguinte código para abrir o famoso plugin **jQuery** como o tal diálogo de carregamento:

```javascript
// Abre o fancyBox!
var activityIndicator = $.fancybox.open('', {
    protect: true, // Desabilita clique direito e cria uma proteção simples
    modal: true, // Desabilita a p* toda!
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

# Exemplo

{{< codepen
  hash="RLKjYL?editors=" 
  user="odahcam"
  author="Luiz Barni"
  title="fancyBox 3 como indicador de atividade!"
  tab="1010"
>}}

[1]: http://fancyapps.com/fancybox/3/
