---
title: ECMAScript 6, uma breve introdução à POO
author: Lenilson Nascimento
type: post
date: 2014-12-15
excerpt: 'Veja como ficou a programação orientada à objetos na nova especificação do JavaScript. Construiremos uma mini loja virtual  usando classes com ECMAScript 6!'
url: /ecmascript-6-uma-breve-introducao-a-poo/
categories:
  - Geral
  - JavaScript
tags:
  - ecmascript
  - JavaScript
  - poo

---
Bom galera, já falei aqui no tableless, sobre o uso de classes na ECMAScript 6, porém, foram exemplos bem superficiais. Então decidi criar um exemplo mais prático de como utilizá-la. Você pode encontrar o artigo que estou falando [aqui][1].

## Entendendo o projeto

A ideia inicial foi criar uma mini (e põe mini nisso) loja virtual, utilizando dados em JSON.

O que teremos, nada mais é que uma variável contendo dados em JSON e estes dados serão transformados em objetos&#8230; Advinha? Objetos de uma classe da ES6.

### Tá, mas pra quê?

Bem, hoje em dia temos muitas ferramentas no mercado que utilizam dados em JSON o tempo todo para o front-end. O AngularJS, o backbone.js, e vários outros, são frameworks que utilizam de dados JSON parar gerar views.

##  Estrutura dos arquivos

Os arquivos do projeto seguem a seguinte estrutura:

**/**
  
**    -/css**
  
**        bootstrap.min.css**
  
**    -/img**
  
**        01.jpg**
  
**        02.jpg**
  
**        03.jpg**
  
**    -/js**
  
**        script.js**
  
**index.html**

Como você já deve ter percebido, na pasta css temos o bootstrap, na pasta img, temos algumas imagens, temos também o arquivo index.html na raiz do projeto, e por fim, na pasta js temos o arquivo script.js, que é onde acontece a mágica.

No final do artigo deixarei um link com o repositório deste projeto no github.

## Finalmente, mãos à obra 🙂

Vamos começar pelo arquivo index.html, que tem uma estrutura bem simples, veja:

<pre>&lt;html&gt;
&lt;head&gt;
&lt;meta charset="utf-8"&gt;
&lt;title&gt;Teste com ECMAScript 6 classes&lt;/title&gt;
&lt;link rel="stylesheet" href="css/bootstrap.min.css"&gt;
&lt;style type="text/css"&gt;
    .old-price{
        text-decoration: line-through;
    }
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div class="container"&gt;
        &lt;div class="row" id="lista"&gt;
 
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;script type="text/javascript" src="js/script.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Bem simples não?

Vamos usar uma estrutura bem básica, pois a nossa mini loja só vai mostrar alguns produtos e pronto. Como eu já disse, o objetivo é usar a ES6.

No final teremos o seguinte resultado:

<img class="alignnone size-full wp-image-46212" src="http://tableless.com.br/uploads/2014/12/zoa.jpg" alt="zoa" width="1177" height="576" srcset="uploads/2014/12/zoa.jpg 1177w, uploads/2014/12/zoa-265x129.jpg 265w, uploads/2014/12/zoa-400x195.jpg 400w" sizes="(max-width: 1177px) 100vw, 1177px" />

Bem, vamos estudar um pouco o HTML acima.

Nas linhas 6 a 10, apenas criamos um css para &#8220;riscar&#8221; o preço antigo no caso de promoção usando a classe **.old-price**.

Na linha 13 criamos o container e na linha 14 uma div com o atributo id setado como &#8220;lista&#8221;, é nesta div onde carregaremos os produtos.

### Preparado? Vamos ao JavaScript.

O JavaScript será estudado mais a fundo, então não vou simplesmente colar o código e explicar as linhas como fiz com o HTML, vou fazer um passo à passo e no final mostro o resultado do arquivo.

#### Qual o primeiro passo?

Habilitar a ES6 no seu navegador, é claro!

Como a ES6 ainda não está funcionando totalmente nos navegadores e ainda não foi adotada como padrão, ela está por padrão desabilitada.

Neste exemplo utilizei o Google Chrome Canary, indico que você o utilize também, mas nada contra o firefox.

Para habilitar a ES6 no Chrome Canary, basta você abrir uma nova aba e acessar a url: **chrome://flags**

Após acessar esta url, você vai procurar algo parecido com a imagem abaixo, basta apenas habilitar e pronto:

<img class="alignnone size-full wp-image-46218" src="http://tableless.com.br/uploads/2014/12/zoa21.jpg" alt="zoa2" width="830" height="316" srcset="uploads/2014/12/zoa21.jpg 830w, uploads/2014/12/zoa21-265x100.jpg 265w, uploads/2014/12/zoa21-400x152.jpg 400w" sizes="(max-width: 830px) 100vw, 830px" />

Feito isso, podemos começar :).

O primeiro passo, é habilitar o strict mode do JavaScript, pois objetos não podem ser utilizados sem o modo strict. Você pode ver mais sobre o strict mode [Bom galera, já falei aqui no tableless, sobre o uso de classes na ECMAScript 6, porém, foram exemplos bem superficiais. Então decidi criar um exemplo mais prático de como utilizá-la. Você pode encontrar o artigo que estou falando [aqui][1].

## Entendendo o projeto

A ideia inicial foi criar uma mini (e põe mini nisso) loja virtual, utilizando dados em JSON.

O que teremos, nada mais é que uma variável contendo dados em JSON e estes dados serão transformados em objetos&#8230; Advinha? Objetos de uma classe da ES6.

### Tá, mas pra quê?

Bem, hoje em dia temos muitas ferramentas no mercado que utilizam dados em JSON o tempo todo para o front-end. O AngularJS, o backbone.js, e vários outros, são frameworks que utilizam de dados JSON parar gerar views.

##  Estrutura dos arquivos

Os arquivos do projeto seguem a seguinte estrutura:

**/**
  
**    -/css**
  
**        bootstrap.min.css**
  
**    -/img**
  
**        01.jpg**
  
**        02.jpg**
  
**        03.jpg**
  
**    -/js**
  
**        script.js**
  
**index.html**

Como você já deve ter percebido, na pasta css temos o bootstrap, na pasta img, temos algumas imagens, temos também o arquivo index.html na raiz do projeto, e por fim, na pasta js temos o arquivo script.js, que é onde acontece a mágica.

No final do artigo deixarei um link com o repositório deste projeto no github.

## Finalmente, mãos à obra 🙂

Vamos começar pelo arquivo index.html, que tem uma estrutura bem simples, veja:

<pre>&lt;html&gt;
&lt;head&gt;
&lt;meta charset="utf-8"&gt;
&lt;title&gt;Teste com ECMAScript 6 classes&lt;/title&gt;
&lt;link rel="stylesheet" href="css/bootstrap.min.css"&gt;
&lt;style type="text/css"&gt;
    .old-price{
        text-decoration: line-through;
    }
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div class="container"&gt;
        &lt;div class="row" id="lista"&gt;
 
        &lt;/div&gt;
    &lt;/div&gt;
    &lt;script type="text/javascript" src="js/script.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Bem simples não?

Vamos usar uma estrutura bem básica, pois a nossa mini loja só vai mostrar alguns produtos e pronto. Como eu já disse, o objetivo é usar a ES6.

No final teremos o seguinte resultado:

<img class="alignnone size-full wp-image-46212" src="http://tableless.com.br/uploads/2014/12/zoa.jpg" alt="zoa" width="1177" height="576" srcset="uploads/2014/12/zoa.jpg 1177w, uploads/2014/12/zoa-265x129.jpg 265w, uploads/2014/12/zoa-400x195.jpg 400w" sizes="(max-width: 1177px) 100vw, 1177px" />

Bem, vamos estudar um pouco o HTML acima.

Nas linhas 6 a 10, apenas criamos um css para &#8220;riscar&#8221; o preço antigo no caso de promoção usando a classe **.old-price**.

Na linha 13 criamos o container e na linha 14 uma div com o atributo id setado como &#8220;lista&#8221;, é nesta div onde carregaremos os produtos.

### Preparado? Vamos ao JavaScript.

O JavaScript será estudado mais a fundo, então não vou simplesmente colar o código e explicar as linhas como fiz com o HTML, vou fazer um passo à passo e no final mostro o resultado do arquivo.

#### Qual o primeiro passo?

Habilitar a ES6 no seu navegador, é claro!

Como a ES6 ainda não está funcionando totalmente nos navegadores e ainda não foi adotada como padrão, ela está por padrão desabilitada.

Neste exemplo utilizei o Google Chrome Canary, indico que você o utilize também, mas nada contra o firefox.

Para habilitar a ES6 no Chrome Canary, basta você abrir uma nova aba e acessar a url: **chrome://flags**

Após acessar esta url, você vai procurar algo parecido com a imagem abaixo, basta apenas habilitar e pronto:

<img class="alignnone size-full wp-image-46218" src="http://tableless.com.br/uploads/2014/12/zoa21.jpg" alt="zoa2" width="830" height="316" srcset="uploads/2014/12/zoa21.jpg 830w, uploads/2014/12/zoa21-265x100.jpg 265w, uploads/2014/12/zoa21-400x152.jpg 400w" sizes="(max-width: 830px) 100vw, 830px" />

Feito isso, podemos começar :).

O primeiro passo, é habilitar o strict mode do JavaScript, pois objetos não podem ser utilizados sem o modo strict. Você pode ver mais sobre o strict mode][2] do Fabiano de Lima Abreu.

Para fazer isto é simples, vamos inserir na primeira linha do arquivo o seguinte:

<pre>"use strict";</pre>

Simples, não?

Agora vamos criar a nossa classe Produto e seu método construtor, veja abaixo:

<pre>class Produto{
    constructor(codigo,nome,imagem,promocao,preco,desconto){
        this.codigo = codigo;
        this.nome = nome;
        this.imagem = imagem;
        this.promocao = promocao;
        this.preco = preco;
        this.desconto = desconto;
    }
}</pre>

Não precisa ser um gênio para entender esta parte, e se você chegou a ler o artigo que deixei no início deste, já estará familiarizado com o assunto.

Criamos uma classe com seu método construtor, que possui os atributos, código, nome, imagem, promocao, preco e desconto.

Bacana, e agora?

Vamos criar um método para listagem de produtos, que receberá uma variável em JSON e organizará os produto no HTML.

Criaremos o método lista, que receberá como parâmetro uma variável contendo o JSON:

<pre>lista(products){
}
</pre>

Em seguida criaremos uma variável lista pegando a div onde a lista será inserida pelo id:

<pre>lista(products){
    var lista = document.getElementById("lista");
}</pre>

Agora, vamos criar um laço de repetição que percorrerá nossa lista em JSON e criará seus elementos:

<pre>lista(products){
    var lista = document.getElementById("lista");
    for(var i=0; i &lt; products.length; i++){
        //conteúdo do loop
    }
}</pre>

Dentro deste laço, criaremos e preencheremos os elementos HTML de cada produto, utilizaremos os thumbnails do bootstrap, como você pôde ver na foto com o resultado final.

A estrutura básica será a seguinte:

<pre>&lt;div class="col-xs-12 col-sm-6 col-md-4 col-lg-4"&gt;
    &lt;div class="thumbnail"&gt;
        &lt;h1 class="text-center"&gt;Sapatênis Puma Preto&lt;/h1&gt;
        &lt;img src="img/01.jpg"&gt;
        &lt;small class="old-price"&gt;R$ 250&lt;/small&gt;
        &lt;p class="price"&gt;R$ 200&lt;/p&gt;
        &lt;a class="btn btn-primary"&gt;Comprar&lt;/a&gt;
    &lt;/div&gt;
&lt;/div&gt;</pre>

Para cada produto lido através do JSON, teremos esta estrutura para exibi-lo.

Primeiramente vamos instanciar a classe produto a cada repetição deste laço, utilizando o método construtor para atribuir às suas propriedades:

<pre>let produto = new Produto(products[i].codigo,products[i].nome,products[i].imagem,products[i].promocao,products[i].preco,products[i].desconto);</pre>

Quando criamos um objeto à partir de uma classe, é necessário a utilização da palavra reservada **let**.

Em seguida, vamos criar os elementos HTML dos produtos, começando pelas variáveis:

<pre>var column, thumbnail, title, image, old_price, price, btn;</pre>

Em seguida, atribuímos o HTML nessas variáveis:

<pre>column = document.createElement("div");
thumbnail = document.createElement("div");
title = document.createElement("h1");
image = document.createElement("img");
old_price = document.createElement("small");
price = document.createElement("p");
btn = document.createElement("a");</pre>

Em seguida, vamos adicionar as classes aos elementos para receberem a formatação do bootstrap:

<pre>column.classList.add("col-xs-12");
column.classList.add("col-sm-6");
column.classList.add("col-md-4");
column.classList.add("col-lg-4");

thumbnail.classList.add("thumbnail");

title.classList.add("text-center");

old_price.classList.add("old-price");

price.classList.add("price");

btn.classList.add("btn");
btn.classList.add("btn-primary");
btn.innerHTML = "Comprar";</pre>

Para adiantar, já colocamos o innerHTML do botão com o texto &#8220;Comprar&#8221;.

Agora o que temos que fazer é inserir nos elementos os seus valores:

<pre>title.innerHTML = produto.nome;

image.setAttribute("src",produto.imagem);</pre>

Eu coloquei por enquanto, apenas o nome do produto, e sua imagem. Pois precisamos pensar na promoção.

O atributo promocao, é um valor booleano, que nos mostrará se o produto vai ou não ter desconto.

Caso promocao seja verdadeiro, colocaremos o preço normal do produto com a classe **.old-price** que criamos lá em cima para que ele fique &#8220;riscado&#8221;, e o preço real será um cálculo do valor do produto subtraído do desconto. Caso ocorra o contrário, o elemento **old_price** receberá um **display:none** e o preço não sofrerá alteração:

<pre>if(produto.promocao == true){
    old_price.innerHTML = "R$ "+ produto.preco;
    price.innerHTML = "R$ "+ (produto.preco - produto.desconto);
}else{
    old_price.setAttribute("display","none");
    price.innerHTML = "R$ "+ produto.preco;
 }</pre>

E por fim, para finalizarmos o nosso laço de repetição, iremos dar um **appendChild()** onde for necessário, criando a hierarquia do HTML:

<pre>thumbnail.appendChild(title);
thumbnail.appendChild(image);
thumbnail.appendChild(old_price);
thumbnail.appendChild(price);
thumbnail.appendChild(btn);

column.appendChild(thumbnail);

lista.appendChild(column);</pre>

Não vou postar o código final do nosso método, pois o artigo já está bem grande. Basta dar uma olhadinha no repositório no final do artigo e você verá a estrutura completa.

### Beleza, mas e agora?

Bom, criei uma variável após o final de nossa classe Produto, com os dados em formato JSON para testarmos os produtos. Em um sistema real, estes dados viriam de fontes externas.

Abaixo o código:

<pre>var products = [
 {
 codigo: 1,
 nome: "Sapatênis Puma Preto",
 imagem: "img/01.jpg",
 promocao: true,
 preco: 250.00,
 desconto: 50.00
 },
 {
 codigo: 2,
 nome: "Sapatênis Preto Linha Vermelha",
 imagem: "img/02.jpg",
 promocao: false,
 preco: 250.00,
 desconto: null
 },
 {
 codigo: 3,
 nome: "Sapatênis Bege c/ Branco",
 imagem: "img/03.jpg",
 promocao: false,
 preco: 250.00,
 desconto: null
 },
]</pre>

Por fim, basta apenas instanciar a classe Produto e chamarmos o método lista, passando como parâmetro nossa variável contendo os dados em JSON:

<pre>let produto = new Produto();
produto.lista(products);</pre>

## Conclusão

Bom galera, o artigo ficou um pouco longo, pois tentei ser o mais específico possível.

Este foi só um exemplo do que podemos fazer com as novas features da ECMAScript 6 e as mudanças (pra melhor) que ela nos proporciona.

Aguardamos ansiosamente que ela comece à ser suportada pelos browsers por completo, pois além de tanta coisa que se pode fazer com ela, o Angular 2.0 está sendo escrito nela também.

Pra quem quiser dar um olhada no repositório com o código deste artigo basta seguir este [link][3].

Por hoje é só 🙂 até mais galera!

 [1]: http://tableless.com.br/tableless-weekly-5/ "Tableless Weekly 5"
 [2]: http://tableless.com.br/javascript-strict-mode/ "JavaScript Strict Mode"
 [3]: https://github.com/lnlwd/ECMAScript6-loja "Repositório"