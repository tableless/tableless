---
title: Introdução à Programação Funcional (Functional Programming) em Javascript
author: maufarinelli
type: post
date: 2016-06-28
url: /introducao-programacao-funcional-functional-programming-em-javascript/
categories:
  - JavaScript
tags:
  - JavaScript
  - js
  - programação funcional

---
Eu venho estudando functional programming já faz um tempo, e decidi colocar no papel o que aprendi, pois para mim essa é a melhor forma de reter o que se aprendeu. Além disso, será um prazer se esse post ajudar outros programadores.

> “Em ciência da computação, **programação funcional** é um paradigma de programação que trata a computação como uma avaliação de funções matemáticas e que evita estados ou dados mutáveis. Ela enfatiza a aplicação de funções, em contraste da programação imperativa, que enfatiza mudanças no estado do programa” <a href="https://pt.wikipedia.org/wiki/Programa%C3%A7%C3%A3o_funcional" target="_blank">https://pt.wikipedia.org/wiki/Programa%C3%A7%C3%A3o_funcional</a>

A princípio, isso pode parecer algo de outro mundo, mas com calma você também entenderá.

Basicamente, em programação funcional:

  * Dados são imutáveis, ou seja, uma vez atribuídos os valores de uma variável, não devemos nunca alterá-los (parece bizarro, mas fará sentido logo logo)
  * As funções devem ser sem estado (stateless), ou seja, elas devem sempre agir e retornar algo como se fosse a primeira vez que elas fossem utilizadas no programa. Para uma função neste paradigma, o que aconteceu antes de ser chamada não lhe interessa e não deve influenciar em nada a sua resposta

Por isso, a principal característica da programação funcional é a ausência de efeitos secundários. Como uma função não altera nenhum dado externo e não depende de nenhum dado externo para fazer o seu trabalho, teoricamente não existe efeitos secundários causados por ela no programa.

**Como programar utilizando o paradigma da Programação Funcional**

Abaixo eu coloquei 3 regras básicas para transformar seu código em Programação Funcional (tirado deste ótimo artigo <a href="http://www.smashingmagazine.com/2014/07/dont-be-scared-of-functional-programming/" target="_blank">http://www.smashingmagazine.com/2014/07/dont-be-scared-of-functional-programming/</a>)

  * A função deve conter pelo menos 1 argumento
  * A função deve retornar algum dado ou outra função (isso será visto mais pra frente)
  * Sem loops (este ponto é controverso, pois a biblioteca Lodash foi otimizada usando loops internamente nas funções. Gostaria de ouvir comentários e mais informações a respeito)

Utilizaremos uma pequena aplicação, uma página para uma agência de turismo virtual, e  transformaremos tudo o que for possível em seu código seguindo os conceitos de programação funcional.

<a href="http://farinelliwebdevelopment.com/demo/functional-programming" target="_blank">Demo Page</a>

(se quiser pegar o código para acompanhar e testar você mesmo, <a href="https://github.com/maufarinelli/tutorial-functional-programming/tree/functional-part1" target="_blank">pegue o código no github</a>)

Começaremos pela parte dos dados:

<pre class="lang-javasript">(function(_) {
    // Data
    var cities = [
        {name: 'Nova York', passagem: 1550.00, hotel: 1800.00, category: 'north-america'},
        {name: 'Paris',     passagem: 1720.00, hotel: 2100.00, category: 'europe'},
        {name: 'Londres',   passagem: 1630.00, hotel: 2500.00, category: 'europe'},
        {name: 'Amsterdam', passagem: 1430.00, hotel: 1750.00, category: 'europe'},
        {name: 'Santiago',  passagem: 600.00,  hotel: 1150.00, category: 'south-america'},
        {name: 'Buenos Aires', passagem: 520.00, hotel: 950.00, category: 'south-america'},
        {name: 'Barcelona', passagem: 1390.00, hotel: 1670.00, category: 'europe'},
        {name: 'Lisboa',    passagem: 1280.00, hotel: 1450.00, category: 'europe'},
        {name: 'Vancouver', passagem: 1590.00, hotel: 320.00, category: 'north-america'},
        {name: 'Roma',      passagem: 1400.00, hotel: 1950.00, category: 'europe'},
    ];
    function createPackages() {
        for(var i = 0; i &lt; cities.length; i++) {
            cities[i].pacote = (cities[i].passagem + cities[i].hotel) * 0.8;
        }
}
});
</pre>

A função `createPackages()` não tem nada de programação funcional. Ela depende da variável _cities_ e ela altera os dados dessa variável, uma vez chamada.

Vamos transformá-la em uma função pura, como dizem na programação funcional, onde ela não dependerá de uma variável externa e não irá alterar nada exterior a ela.

<pre class="lang-javascript">(function(_) {
  // Data
  var cities = [
    {name: 'Nova York', passagem: 1550.00, hotel: 1800.00, category: 'north-america'},
    {name: 'Paris',     passagem: 1720.00, hotel: 2100.00, category: 'europe'},
    {name: 'Londres',   passagem: 1630.00, hotel: 2500.00, category: 'europe'},
    {name: 'Amsterdam', passagem: 1430.00, hotel: 1750.00, category: 'europe'},
    {name: 'Santiago',  passagem: 600.00,  hotel: 1150.00, category: 'south-america'},
    {name: 'Buenos Aires', passagem: 520.00, hotel: 950.00, category: 'south-america'},
    {name: 'Barcelona', passagem: 1390.00, hotel: 1670.00, category: 'europe'},
    {name: 'Lisboa',    passagem: 1280.00, hotel: 1450.00, category: 'europe'},
    {name: 'Vancouver', passagem: 1590.00, hotel: 320.00, category: 'north-america'},
    {name: 'Roma',      passagem: 1400.00, hotel: 1950.00, category: 'europe'},
  ];
  function setPackages(collection) {
    var result = [];
    for(var i = 0; i &lt; collection.length; i++) {
        collection[i].pacote = (collection[i].passagem + collection[i].hotel) * 0.8;
        result.push(collection[i]);
    }
    return result;
  }

  var citiesWithPackages = setPackages(cities);
});
</pre>

A função setPackages pega qualquer coleção e, para cada objeto dessa coleção, insere mais uma propriedade chamada _pacote_.

Alterei o nome da função, pois além de fazer mais sentido, fica claro para o leitor que na verdade, é uma nova função. Ela é pura, ou seja, não depende mais de dados externos e não alterará nada fora do seu escopo.

Opps, quase pura. O leitor mais atento já pode ter percebido que, na verdade, ela alterou sim a variável _cities_ também. Isso porque em JavaScript, assim como Java e outros linguagens, no momento em que fizemos : `collection[i].pacote = alguma coisa`, esta alterando o objeto que esta alocado na referência _collection[i]._

<img class="alignnone size-full wp-image-53585" src="http://tableless.com.br/uploads/2016/04/tuto3.png" alt="tuto3" width="867" height="138" />

Para que essa função seja realmente pura, teremos que clonar o objeto para somente após inserirmos essa nova propriedade. Para isso, vou criar um objecto chamado utilities, que conterá funções utilitárias para nossa aplicação, e a primeira será o método `cloneObject`.

<pre class="lang-javascript">(function(_) {
  var utilities = {};

  utilities.cloneObject = function(obj) {
    if(typeof obj === "object") {
      var clone = {};
      for (var prop in obj)
        if (obj.hasOwnProperty(prop))
          clone[prop] = obj[prop];
      return clone;
    }
  };

  // Data
  var cities = [
    {name: 'Nova York', passagem: 1550.00, hotel: 1800.00, category: 'north-america'},
    {name: 'Paris',     passagem: 1720.00, hotel: 2100.00, category: 'europe'},
    {name: 'Londres',   passagem: 1630.00, hotel: 2500.00, category: 'europe'},
    {name: 'Amsterdam', passagem: 1430.00, hotel: 1750.00, category: 'europe'},
    {name: 'Santiago',  passagem: 600.00,  hotel: 1150.00, category: 'south-america'},
    {name: 'Buenos Aires', passagem: 520.00, hotel: 950.00, category: 'south-america'},
    {name: 'Barcelona', passagem: 1390.00, hotel: 1670.00, category: 'europe'},
    {name: 'Lisboa',    passagem: 1280.00, hotel: 1450.00, category: 'europe'},
    {name: 'Vancouver', passagem: 1590.00, hotel: 320.00, category: 'north-america'},
    {name: 'Roma',      passagem: 1400.00, hotel: 1950.00, category: 'europe'},
  ];
  function setPackages(collection) {
    var result = [];
    for(var i = 0; i &lt; collection.length; i++) {
      if(typeof collection[i].passagem !== 'undefined' && typeof collection[i].hotel !== 'undefined') {
        var cloned = utilities.cloneObject(collection[i]);
        cloned.pacote = (cloned.passagem + cloned.hotel) * 0.8;
        result.push(cloned);
      }
    }
    return result;
  }

  var citiesWithPackages = setPackages(cities);
});
</pre>

<img class="alignnone size-full wp-image-53587" src="http://tableless.com.br/uploads/2016/04/tuto5.png" alt="tuto5" width="872" height="138" />

Agora sim, temos uma função realmente pura, que não altera nenhum dado externo. Como calculamos os pacotes a partir do preço da passagem e do hotel, devemos checar se o objeto em questão contém essas duas propriedades para evitarmos erros, pois agora essa função é mais abstrata e pode receber qualquer tipo de coleção.

Contudo, se queremos uma função abstrata, que pode aceitar qualquer tipo de coleção, por que não criarmos um método de utilities que fará esse papel.

<pre class="lang-javascript">(function(_) {
  var utilities = {};

  utilities.map = function(list, callback) {
    var resultList = [];
    for(var i = 0; i &lt; list.length; i++) {
      resultList.push(callback(list[i]));
    }
    return resultList;
  }

  utilities.cloneObject = function(obj) {
    if(typeof obj === "object") {
      var clone = {};
      for (var prop in obj)
        if (obj.hasOwnProperty(prop))
          clone[prop] = obj[prop];
      return clone;
    }
  };

  // Data
  var cities = [
    {name: 'Nova York', passagem: 1550.00, hotel: 1800.00, category: 'north-america'},
    {name: 'Paris',     passagem: 1720.00, hotel: 2100.00, category: 'europe'},
    {name: 'Londres',   passagem: 1630.00, hotel: 2500.00, category: 'europe'},
    {name: 'Amsterdam', passagem: 1430.00, hotel: 1750.00, category: 'europe'},
    {name: 'Santiago',  passagem: 600.00,  hotel: 1150.00, category: 'south-america'},
    {name: 'Buenos Aires', passagem: 520.00, hotel: 950.00, category: 'south-america'},
    {name: 'Barcelona', passagem: 1390.00, hotel: 1670.00, category: 'europe'},
    {name: 'Lisboa',    passagem: 1280.00, hotel: 1450.00, category: 'europe'},
    {name: 'Vancouver', passagem: 1590.00, hotel: 320.00, category: 'north-america'},
    {name: 'Roma',      passagem: 1400.00, hotel: 1950.00, category: 'europe'},
  ];
  var citiesWithPackages = utilities.map(cities, function(city){
    if(typeof collection[i].passagem !== 'undefined' && typeof collection[i].hotel !== 'undefined') {
      var city = utilities.cloneObject(city);
      city.pacote = (city.passagem + city.hotel) * 0.8;
    }
    return city;
  });
});

</pre>

O método map, existente em diversas linguagens de programação, percorre nossa coleção e retornará uma nova coleção com os dados alterados da forma que a função callback quiser. Ou seja, agora temos toda flexibilidade para inserirmos ou retirarmos dados dos objetos de uma coleção sem afetar a coleção original.

Pode parecer estranho para alguns que não estão habituados a javascript, mais funções callback são tão comuns nessa linguagem que, as vezes, nem me dou conta.

Em javascript, funções podem receber outras funções como argumento e funções podem retornar outras funções.

Vamos a explicação do que fizemos no método map: primeiramente ele aceita uma função como argumento. O que essa função retorna é que realmente será inserido na array resultList.

Funções que podem receber outras funções como argumento ou que retornar outras funções são chamadas funções de ordem superior (higher-order functions).

Vamos supor que eu precise clonar uma array e não mais um objeto. O método cloneObjects como próprio nome já diz, não irá ajudar. Então preciso criar outro método mais eficiente.

<pre class="lang-javascript">(function(_) {
  var utilities = {};

  utilities.map = function(list, callback) {
    var resultList = [];
    for(var i = 0; i &lt; list.length; i++) {
      resultList.push(callback(list[i]));
    }
    return resultList;
  }

  utilities.toClone = function() {
    if(arguments[0] === "object") {
      return function(obj) {
        var clone = {};
        for(var prop in obj)
          if (obj.hasOwnProperty(prop))
            clone[prop] = obj[prop];
        return clone;
      }
    }
    if (arguments[0]==="array"){
      return function(obj) {
        var arrayClone = [];
        for (var i=0; i &lt; obj.length; i++) {
          arrayClone.push(obj);
        }
        return arrayClone;
      };
    }
  };

  utilities.cloneObject = function(obj) {
    if(typeof obj === "object") {
      var clone = {};
      for (var prop in obj)
        if (obj.hasOwnProperty(prop))
          clone[prop] = obj[prop];
      return clone;
    }
  };

  // Data
  var cities = [
    {name: 'Nova York', passagem: 1550.00, hotel: 1800.00, category: 'north-america'},
    {name: 'Paris',     passagem: 1720.00, hotel: 2100.00, category: 'europe'},
    {name: 'Londres',   passagem: 1630.00, hotel: 2500.00, category: 'europe'},
    {name: 'Amsterdam', passagem: 1430.00, hotel: 1750.00, category: 'europe'},
    {name: 'Santiago',  passagem: 600.00,  hotel: 1150.00, category: 'south-america'},
    {name: 'Buenos Aires', passagem: 520.00, hotel: 950.00, category: 'south-america'},
    {name: 'Barcelona', passagem: 1390.00, hotel: 1670.00, category: 'europe'},
    {name: 'Lisboa',    passagem: 1280.00, hotel: 1450.00, category: 'europe'},
    {name: 'Vancouver', passagem: 1590.00, hotel: 320.00, category: 'north-america'},
    {name: 'Roma',      passagem: 1400.00, hotel: 1950.00, category: 'europe'},
  ];
  var citiesWithPackages = utilities.map(cities, function(city){
    if(typeof city.passagem !== 'undefined' && typeof city.hotel !== 'undefined') {
      var clone = utilities.toClone("object");
      var city = clone(city);
      city.pacote = (city.passagem + city.hotel) * 0.8;
    }
    return city;
  });
});
</pre>

O método toClone é muito mais eficiente. Ele recebe como argumento a string “object” ou “array” e retorna a função correta para clonar esse tipo de objeto. E foi isso que utilizei na linha 58, dentro da função callback para a variável citiesWithPackages.

O método toClone é uma função de ordem superior que retorna outra função para ser utilizada futuramente.

Bom, é isso. Uma introdução à programação funcional. Por fim, se quiser continuar seu aprendizado em programação funcional, recomendo as video aulas da [webschool.io][1], do Suissa. O cara disponibiliza gratuitamente um material muito bom e abrengente.

Grande abraço.

 [1]: http://webschool.io/jsfuncional/