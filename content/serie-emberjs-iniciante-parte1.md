---
title: EmberJS para iniciantes – Parte 1
author: Anderson de Castro
type: post
date: 2014-10-29
excerpt: Iniciando com Ember.JS
url: /serie-emberjs-iniciante-parte1/
categories:
  - JavaScript
tags:
  - Ember
  - ember.js
  - Frameworks Javascript
  - JavaScript

---
É com muito prazer que começo a escrever aqui no Tableless para ajudá-lo a utilizar um dos melhores frameworks (IMHO) JavaScript atualmente: o EmberJS.

A ideia é ter uma série de artigos sobre EmberJS, visando atender aos que estão começando agora. Por isso, se você já é um cara avançado, não se empolgue, quero fazer algo bem light, certo? Vamos lá então!

Nesta primeira parte começaremos uma aplicação. Faremos com que o resultado seja mostrar uma mensagem de boas vindas ao usuário.

Lápis e caneta na mão&#8230; Oops, melhor: teclados a postos, vamos codar.

## 1. O Download

Primeiramente, vá até o site do nosso querido framework Ember (www.emberjs.com) e faça seu download. Esse passo é simples: basta apenas clicar no link &#8220;Download Starter Kit&#8221; e pronto.

## 2. Descompactar o Arquivo

Parece óbvio, mas como dito no início, vamos devagar: vá até onde você salvou o arquivo do Ember e descompacte-o. Depois disso, caso prefira, mude o nome da pasta para um nome mais sugestivo. Feito isso abra a pasta e veja seus diretórios e arquivos responsáveis pelo funcionamento do framework. Não vou me ater a isso aqui pois você pode encontrar detalhes <a title="Ember JS ... Do Zero!" href="http://emberjs.com.br/blog/?p=14" target="_blank">aqui neste post</a>.

## 3. Abrindo os arquivos!

Os arquivos que você trabalhará para alcançar nosso objetivo (neste artigo) serão o **index.html **e o **app.js. **Este último localizado na pasta &#8220;**js**&#8220;. Então, usando seu editor favorito (o meu é o Sublime!) abra estes dois arquivos para manipulá-los.

## 4. Criar a aplicação

No Ember, para que uma aplicação possa existir e funcionar, é necessário que se declare uma variável que crie uma Application. O arquivo **app.js** é o responsável por ter esta chamada. O código é simples e ocupa 1 linha apenas:

<pre class="lang-javascript">var App = Ember.Application.create();</pre>

Sugiro que você não apenas mantenha o código que já vem escrito, mas apague e faça do zero mesmo. Assim poderá entender como as coisas vão acontecendo ao longo desta série.

## 5. Criar a Rota 

A próxima coisa que temos a fazer é criar uma rota no nosso arquivo **app.js.** As rotas são muito importantes, pois são por onde chamaremos a aplicação (pela URL) e ela nos dirá quais dados carregar e em qual template. Todas as rotas ficarão mapeadas dessa forma:

<pre class="lang-javascript">App.Router.map(function(){

this.route('index');

this.route('hello',{path : '/bem-vindo'});

});
</pre>

Note que temos 2 rotas mapeadas: uma chamada **index** e outra **hello.** A conclusão é de que se digitarmos no URL, por exemplo, _www.meuapp.com/index_ então a rota index chamará o template de mesmo nome para ser carregado para o usuário. Uma atenção para o segundo parâmetro do route é um objeto que contem a propriedade &#8220;**path**&#8220;. Neste caso, o que está escrito como valor de path pode ser digitado pelo usuário no URL e o template acionado será o **hello. **Maneiro, né?

## 6. Criar os templates

Agora que temos as rotas devidamente criadas e configuradas, podemos criar no arquivo **index.html** os nossos templates. Aqui vale lembrar que você verá um monte de coisas entre tags <script>, certo? Pois bem. O Ember utiliza como engine de template padrão o <a title="Handlebars" href="http://handlebarsjs.com" target="_blank">Handlebars</a>, e então essas tags são necessárias para que tudo rode nos conformes!

Pode apagar tudo (ou quase tudo). Tenha atenção na chamada dos scripts, pois há uma ordem devido as suas dependências. Jquery vem primeiro, depois Handlebars e por fim o EmberJS. Daí sim, você pode chamar seu app.js (aquele que estava mexendo até agorinha, não esqueceu né?!).

Para criar um novo template é simples, veja:

<pre class="lang-html">&lt;script type="<strong>text/x-handlebars</strong>" id="<strong>nomedotemplate</strong>"&gt;

// aqui o conteúdo do meu template!

&lt;/script&gt;
</pre>

Como queremos o template **hello**, basta colocar o nome dele ali na propriedade **id **da tag script, certo? E mais uma coisa, note que o atributo **type** não é _text/script,_ mas sim **text/x-handlebars, **por causa da engine que estamos usando.

Adicione algum conteúdo dentro do template, como por exemplo o tão clichê &#8220;Olá Mundo!&#8221;, para que seja visto na tela.

## 7. Testando&#8230;

Bem, por fim criamos os 2 templates que queríamos e a aplicação já pode ser vista, no navegador!

Sua URL será algo parecido com isso: **http://localdasuaaplicacao/#bem-vindo** e **http://localdasuaaplicacao/#index**

Missão cumprida por aqui, bons estudos e até o próximo!