---
title: 'Parcel Bundler: Criando um projeto React'
authors: Eduardo Rabelo
type: post
publishdate: 2018-02-05
date: 2017-12-07
excerpt: Rápido, sem configurações e prático! É amigos da rede web, temos um bom jogador em campo!
image: https://cdn-images-1.medium.com/max/1000/1*QrdmWMnKnVLsL2_1BiZGFw.png
categories:
  - Javascript
  - front-end
tags:
  - reactjs
---


[Nós temos um novo jogador em
campo](https://hackernoon.com/announcing-parcel-a-blazing-fast-zero-configuration-web-application-bundler-feac43aac0f1?source=search_post---------0)!
[Que promete um projeto “com zero de
configurações”](https://mobile.twitter.com/devongovett/status/938084464743165952).
O conceito do Parcel Bundler é parecido com o do Ruby on Rails.

Assumindo convenções de arquivos e pastas, escondendo boa parte do *tooling,
*deixando o seu foco para, exclusivamente, sua aplicação!

[Como sempre, o Twitter está indo a
loucura!](https://mobile.twitter.com/search?q=Parcel Bundler&src=typed_query)

Fiz o teste em alguns projetos que utilizam ferramentas como Babel,
TypeScript/FlowType, CSS Modules, Styled Components, [React
Material-UI](https://github.com/mui-org/material-ui), e funcionou muito bem!

Para pequenos e médios projetos, é uma solução e tanto! E quais as vantagens que
o [Parcel Bundler](https://parceljs.org/) trás?

* A perforamnce de compilação/build é rápida, **muito rápida!!1 🚀🚀🚀**
* *Code Splitting* com a sintaxe `import()` ✅
* *Hot Module Replacement* já configurado 🔥
* Configuração *dev* e *prod* **out of the box!!1 😎**

### Configurando um projeto React 👾

Abaixo, vamos ver o passo a passo para criar um exemplo para uma aplicação
React.

Vamos criar nossa pasta de exemplo e pedir ao *npm* para criar o *package.json*:

```
mkdir parcel-react-example
cd parcel-react-example
npm init -y
```

Instalando as dependências:

```
mkdir parcel-react-example
cd parcel-react-example
npm init -y
```

Vamos adicionar o nosso arquivo `.babelrc`:

```
{
  "presets": ["react-app"]
}
```


E agora,vamos criar nosso arquivo de entrada.

### A mágica do arquivo de entrada ⭐️

Se assim como eu, você é fã do webpack, (っ◕‿◕)っ, estamos acostumados a criar os
pontos de entrada (*entry points*), utilizando arquivos `.js`.

O Parcel Bundler tem uma outra abordagem. Ele, na verdade, pode **receber
qualquer tipo de arquivo como ponto de entrada**.

E uma mágica bacana, é usar um arquivo `.html`. Vamos supor que você faça o link
do seu arquivo `.js` no HTML:

```
// index.html
<html>
<body>
  <script src="./index.js"></script>
</body>
</html>
```

E no arquivo JavaScript:

```
// index.js
console.log(`Hello ${"World"}`);
```

Parcel Bundler irá processar esse arquivo JavaScript mencionado e, como
configuramos Babel acima, irá utilizar todos os *transforms* e *presets*. Ele
irá gerar os arquivos finais com o caminho relativo ao arquivo HTML.

Por exemplo:

```
<html>
<body>
  <!-- arquivo de imagem -->
  <img src="./images/header.png">
  <a href="./outra-pagina.html">Outra página</a>
  <!-- sua aplicação JavaScript -->
  <script src="./index.js"></script>
</body>
</html>
```

Para cada tipo de *transforms* ou *plugins* (Babel,
[PostCSS](https://postcss.org/),
[PostHTML](https://github.com/posthtml/posthtml), etc) um tipo de *asset* será
transformado. Sem a necessidade de criar nada além de um caminho relativo ao
HTML. É bem incrível!

Você pode saber mais na [documentação oficial de
transforms](https://parceljs.org/transforms.html).

### Voltando ao nosso exemplo 🏠

Continuando de onde paramos, atualmente temos:

```
// ls -la parcel-react-example
.babelrc
node_modules
package-lock.json
package.json
```

Vamos criar nosso ponto de entrada com um arquivo HTML:

```
vim index.html
```

E vamos adicionar:

```
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Parcel React Example</title>
</head>
<body>
  <div id="root"></div>
  <script src="./index.js"></script>
</body>
</html>
```



E agora… tente sair do vim 😂

Como essa é uma aplicação React, vamos criar nosso JavaScript:

```
vim index.js
```

E adicionar:

```
import React from 'react';
import ReactDOM from 'react-dom';
const App = () => <div>Hello Parcel x React</div>;
ReactDOM.render(<App />, document.getElementById('root'));
if (module.hot) {
  module.hot.accept();
}
```

E para finalizar, vamos adicionar ao nosso *package.json* os *scripts* de
desenvolvimento e build:

```
...
"scripts": {
  "start": "NODE_ENV=development parcel index.html",
  "build": "NODE_ENV=production parcel build index.html --no-minify"
},
…
```

E agora, você já sabe o caminho!

```
npm start
```

![](https://cdn-images-1.medium.com/max/1000/1*Nh9ZjMOemGx27hYGPj6o7g.png)
<span class="figcaption_hack">Emojis, boas mensagens de erro, tudo no seu devido lugar!</span>

Ah, cheguei a falar que Parcel já vem com um servidor de desenvolvimento por
padrão? 😉 Não precisa das loucuras do **webpack-dev-server** e etc.

Só abrir o endereço [https://localhost:1234](https://localhost:1234/)** **no seu
navegador!

### Finalizando 

[ Parcel Bundler](https://parceljs.org/) trás muita coisa boa para o
*(não-)*concorrido mundo de empacotadores de projetos. Principalmente hoje em
dia, onde temos N configurações, um projeto que valorize algumas convenções, é
muito bem vindo.

Funciona para todos os projetos? É claro que não! 😁

Ainda vou continuar com meu `webpack.config.{ENV}.js`, até porque, o
[V4](https://medium.com/webpack/webpack-4-changes-part-1-week-24-25-fd4d77674e55)
está quase saindo do forno 🔥

Se você quiser conferir o exemplo completo, pode olhar [nesse
repositório](https://github.com/jaredpalmer/react-parcel-example).

Obrigado! 🙏
