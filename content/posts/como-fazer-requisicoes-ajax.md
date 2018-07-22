---
title: Como fazer requisições ajax
authors: Tailo Mateus Gonsalves
type: post
image: https://cdn-images-1.medium.com/max/1200/1*X4f9MUJG2O2ufvjW2tSjlg.png
date: 2018-02-18
excerpt: Requisições ajax com Fetch API e Axios
categories:
  - Front-end
  - Javascript
  - Ajax
tags:
  - Javascript
  - Requisições ajax
  - Fetch api
  - Axios
---

Há algum tempo (não muito distante), pessoas comuns adicionavam em seus projetos a biblioteca JQuery.
Em alguns casos (ainda frequentes), apenas para usarem a função ajax().

```
$.ajax({
    url:"https://api.github.com/users/tailomateus/repos",
    dataType: 'json',
    success: function(response){
		console.log(response);
    }
});
```

Além dessa função, o JavaScript possui um método, 
[XMLHttpRequest](https://developer.mozilla.org/pt-BR/docs/Web/API/XMLHttpRequest) também faz requisições.
Porém para conseguir o esperado é necessário muitos passos. 
Com isso foi criado a Fetch API com recursos mais flexíveis e conceitos de request e response, 
isso cabe em novas tecnologias que estão surgindo, como Service Workers e Cache API.

A Fetch API e o Axios API utilizam o conceito de promessas, você pode ler mais sobre nos links abaixo:

[Promises no JavaScript] (https://braziljs.org/blog/promises-no-javascript/)

[Promessas em JavaScript: uma introdução] (https://developers.google.com/web/fundamentals/primers/promises?hl=pt-br)

[Using promises] (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

## Fetch API - Como funciona

Abaixo, como exemplo é utilizado a API do Github. 

```
fetch('https://api.github.com/users/tailomateus/repos')
  .then(response => response.json())
  .then(data => console.log('data is', data))
  .catch(error => console.log('error is', error));
```
Além da url, existem outros parâmetros,caso queira se aprofundar mais no assunto, sugiro:

[Introduction to fetch] (https://developers.google.com/web/updates/2015/03/introduction-to-fetch)

[Using fetch - CSS Tricks] (https://css-tricks.com/using-fetch/)

[Using fetch - Mozilla] (https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API/Using_Fetch)


### SUPORTE 

O maior problema para mim é não possuir suporte no IE 11.

![Support Fetch API](https://tailomateus.github.io/images/support_fetch.png)


## Axios - Como usar

A API é basicamente um cliente http, funciona em browsers e em servidores nodejs. 

Se quiser usar no browser, importe a cdn:

```
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

Ou instale utilizando o npm: 

```
npm install axios
```

Importe o pacote: 

```
ES5: var axios = require('axios'); 
ES6: import axios from 'axios';
```


Após instalar, o código abaixo simula uma requisição get na API do Github


```

axios.get('https://api.github.com/users/tailomateus/repos').then(function(response){
    console.log(response.data); 
}); 

```

Para utilizar o método post, possui um parâmetro a mais, indicando o que está sendo enviado para o servidor: 

```
axios.post('/save', { firstName: 'Teste', lastName: 'Testes' })
  .then(function(response){
    console.log('salvo com sucesso')
});
```

### SUPORTE

É suportado pelos browsers mais usados.

![Support Fetch API](https://tailomateus.github.io/images/support_axios.png)

Para saber mais sobre Axios API:

[Axios NPM](https://www.npmjs.com/package/axios)

[Getting Started With Axios](https://medium.com/codingthesmartway-com-blog/getting-started-with-axios-166cb0035237)

## CONCLUSÃO

Neste artigo foi demonstrado formas para fazer requisições (JQuey, Fetch API, Axios), além dessas, existem outras formas. Porém, 
cabe a você a melhor opção para usar nos projetos.
