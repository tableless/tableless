---
title: Moment.js para trabalhar com datas no JavaScript
authors: Breno Panzolini
type: post
date: 2018-02-25
excerpt: Como utilizar o pacote Moment.js para trabalhar de maneira mais eficiente com datas no JavaScript.
categories:
  - NodeJS
  - JavaScript
tags:
  - NodeJS
  - JavaScript
image:  https://imasters.com.br/wp-content/uploads/2014/02/moment-js.jpg
---

Trabalhar com datas no JavaScript utilizando a biblioteca padrão pode ser muito complicado e "chato" em diversos cenários e situações do dia a dia, por isso nesse post vou mostrar como utilizar algumas das principais funções do [**Moment.js**](http://momentjs.com/) para facilitar nosso desenvolvimento.

## Sobre o Moment.js

O Moment.js é um pacote open source que pode ser utilizado para validar, manipular e fazer o parse de datas no JavaScript de uma maneira muito poderosa (para os que já utilizam JavaScript há algum tempo, sabem muito bem que em certos cenários utilizar a biblioteca padrão pode ser bem chatinho).

O repositório oficial do Moment.js pode ser encontrado no [GitHub](https://github.com/moment/moment) e a documentação oficial no [site](http://momentjs.com/docs/).

## Instalando o pacote

O Moment.js foi desenvolvido para funcionar tanto no browser como no Node.js e por isso ele pode ser instalado através de diversos gerenciadores de pacotes, como por exemplo: npm, bower, nuget, etc.

Para instalar o moment utilizando o npm, basta utilizar o comando:

```sh
$ npm install moment
```

*Obs: as demais formas de instalação e instruções podem ser lidas na [doc oficial](http://momentjs.com/docs/#/use-it/)*
