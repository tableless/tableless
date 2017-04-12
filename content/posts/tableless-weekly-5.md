---
title: 'Tableless Weekly #5'
author: Lenilson Nascimento
type: post
date: 2014-10-09
excerpt: Seleção semanal do tableless que reúne links úteis, novidades no mercado front end e alguns sites bem legais.
url: /tableless-weekly-5/
categories:
  - Weekly
tags:
  - Digest
  - tablelessweekly
  - weekly

---
Mais um artigo da série Tableless Weekly. Quero me desculpar por ter ficado algumas semanas sem escrever, mas creio que isto não se repetirá e estarei aqui com vocês todas as semanas. 🙂

Antes de ir aos links e tudo mais, quero discutir um assunto com vocês. No último artigo, falei sobre a nova especificação ECMAScript 6, que foi adotada parcialmente em alguns navegadores.

Uma das partes que ainda não foi adotada, é a nova especificação de orientação a objetos que a ES6 traz consigo. Vou dar alguns exemplos aqui e falar um pouco sobre este novo modelo de OO para que possamos discutir sobre o assunto. Não deixem de comentar 🙂

Uma das coisas mais interessantes, foi a questão das classes, que deixarão de ser &#8220;funções&#8221;.

Para quem se recorda, no modelo antigo, faríamos algo mais ou menos assim:

<pre>function Car(){
    //e aqui iriam os métodos e atributos desta classe.
}
</pre>

No novo modelo de OO será escrito da seguinte forma:

<pre>class Car{
    //e aqui iriam os métodos e atributos desta classe.
}
</pre>

Outro aspecto interessante que foi a adoção de métodos construtores para a classe, o que torna nosso código padronizado e mais bem estruturado. Os construtores da ES6, são bem similares aos métodos construtores do PHP. No PHP usamos construtores através da palavra reservada **__constructor()**, e na ES6 usaremos a palavra reservada apenas como **constructor()**.

Vamos recordar mais uma vez o modelo antigo e o novo modelo. Utilizaremos a mesma classe acima.

<pre>function Car(marca, modelo){
    this.marca = marca; //atribuímos o valor da variável passada ao instanciar a classe à uma de suas propriedades
    this.modelo = modelo; //atribuímos o valor da variável passada ao instanciar a classe à uma de suas propriedades
}
//Instanciamos a classe
var car = new Car('Ford','Mustang GT');
console.log('Seu carro é um '+car.marca+' modelo: '+car.modelo);
</pre>

No novo modelo:

<pre>class Car{
    constructor(marca, modelo){//Criamos o método construtor para atribuir variáveis para as propriedades
        this.marca = marca;
        this.modelo = modelo;
    }
}
let car = new Car('Chevrolet','Camaro SS');
console.log('Seu carro é um '+car.marca+' modelo: '+car.modelo);</pre>

Mais um ponto que merece destaque é a construção de métodos de uma classe. Se tornou mais simples e objetiva. Continuando a mesma classe acima:

<pre>function Car(marca, modelo){
    this.marca = marca;
    this.modelo = modelo;

    //Criamos um método para escrever a marca e o modelo do carro
    this.mostraInfo = function(){
        console.log('Seu carro é um '+this.marca+' modelo: '+this.modelo);
    }
}
var car = new Car('Ford','Mustang GT');
car.mostraInfo();</pre>

No novo Padrão seria:

<pre>class Car{
    constructor(marca, modelo){
        this.marca = marca;
        this.modelo = modelo;
    }
    // Podemos notar como é mais simples cria o método
    mostraInfo(){
        console.log('Seu carro é um '+this.marca+' modelo: '+this.modelo);
    }
}
let car = new Car('Chevrolet','Camaro SS');
car.mostraInfo();</pre>

Com apenas essas pequenas mudanças já podemos ter uma OO bem mais simples de entender que o modelo OO tradicional do JavaScript. Mas, e se eu disser que ainda tem mais?

No novo modelo de OO da ES6, podemos estender classes, assim como fazemos nas demais linguagens orientadas à objetos.

Imagine que tivéssemos propriedades no Camaro SS, que não são comuns ao Mustang GT. Poderíamos criar uma classe para cada um que tivesse suas propriedades e métodos próprios:

<pre>class Car{
    constructor(marca, modelo){
        this.marca = marca;
        this.modelo = modelo;
    }
}
class MustangGT extends Car{
    constructor(marca, modelo, historia){
        super.constructor(marca,modelo); //Utilizamos a palavra reservada super para chamar um método da classe pai
        this.historia = historia;
    }
}
class Camaro extends Car{
    constructor(marca, modelo, musica){
        super.constructor(marca,modelo);
        this.musica = musica;
    }
}</pre>

Veja que estendemos as classes para herdarmos as propriedades **marca** e **modelo** da classe pai para as classes filhas, e então criamos as propriedades distintas em cada uma das classes, como a propriedade música, que pertence somente ao Camaro, e a propriedade história, que pertence somente ao Mustang.

Bom, espero que tenham gostado da nova especificação de OO da ES6. Como todas as mudanças, tem seus prós e contras e quero que deixem suas opiniões à respeito nos comentários.

## Sites Legais

Vamos aos sites legais desta edição.

[The Building of  Memories][1] &#8211; Site feito pela Coca-Cola, para mostrar sua presença em alguns momentos marcantes na história. Achei bem legal o design flat e as animações do site.

[DemiCreative][2] &#8211; Site de uma agência de design e criação, muito interessante também.

[Burnkit][3] &#8211; Outra agência de design bem bacana.

## Links Úteis

[CSS3 Flags][4] &#8211; Uma página feita pelo nosso amigo Raphael Fabeni, onde ele criou bandeiras de diversos países utilizando apenas CSS3. O mais bacana é que se você analisar o código, poderá aprender bastante as aplicações do CSS Animation.

## Conclusão

Não quis ser muito extenso com os links neste artigo devido ao texto inicial ser bem grande, para não ficar cansativo.

Espero que tenham gostado e estarei de volta na próxima semana com mais um Tableless Weekly. Até a próxima.

 [1]: http://www.thebuildingofmemories.com/
 [2]: http://demicreative.com/
 [3]: http://www.burnkit.com/
 [4]: http://www.raphaelfabeni.com.br/flags-css3/