---
title: Melhores Práticas Web Components
author: Mateus Ortiz
type: post
date: 2014-09-10
excerpt: Conheça práticas simples que podem ajudar na organização do seu web component.
url: /melhores-praticas-web-components/
categories:
  - HTML5
  - JavaScript
tags:
  - JavaScript
  - web component

---
Web Components é um novo conjunto bem recente de recursos da plataforma web que permite aos desenvolvedores criarem componentes de forma declarativa e muito interessante.

Irei apresentar a seguir algumas boas práticas do ecossistema de Web Components.

O guia a seguir contém boas práticas que evoluirão ao longo do tempo, assim como a própria especificação. O guia é um ponto de partida.

## Namespacing

É como você nomeia seu Web Component, ele deve conter um traço no seu nome para diferenciar de outras tags do HTML, você também deve mantê-lo curto, semântico.

<pre class="lang-html">&lt;mark-down&gt;&lt;/mark-down&gt;</pre>

## Definir valores default para Atributos

Definindo valores default nos atributos, mesmo que o usúario não defina um valor para esse atributo ele já vai ter um valor default definido.

<pre class="lang-html">&lt;polymer-element name="button-large" attributes="color"&gt;
	&lt;template&gt;
	&lt;template&gt;
&lt;/polymer-element&gt;
</pre>

<pre class="lang-javascript">Polymer('button-large', {
	color: '#f00'
});
</pre>

Atributos devem usar camel-cased, quando houver uso de mais de uma palavra no Atributo.

## Organizando os Imports

Uma boa prática, é você organizar todos os seus componentes em um único arquivo, e depois chamar apenas esse arquivo na sua index. Isso traz uma ótima organização para seus web components.

arquivo imports.html.

<pre class="lang-html">&lt;link rel="import" href="../src/my-tabs.html"&gt;</pre>

<pre class="lang-html">&lt;link rel="import" href="../src/my-buttons.html"&gt;</pre>

esse arquivo imports está com poucas importações mas em uma grande aplicação isso vai ser bem grande, agora importo apenas o arquivo imports.html na minha index.html.

<pre class="lang-html">&lt;link rel="import" href="../src/imports.html"&gt;</pre>

## Documente seus web components

Documentar seus custom elements é muito importante. Isso ajuda que pessoas usem seu web component; e consiga contribuir com ele; documentar atributos; criar demos do web component; mostrar se ele é feito para ser usado dentro de outro componente; mostrar o contexto; documentar métodos e propriedades do javascript e também listar seus eventos.

## Testes

Uma boa prática para seus Custom Elements é criar testes de unidade para verificar as funcionalidades do seu componente, [<seed-element></seed-element>][1] usa uma configuração usando Mocha e Chai.

## FrontInterior 2014

Final de semana retrasado ocorreu em Bauru a segunda edição do Front In Interior 2014, o evento contou com a presença de palestrantes incríveis e tiver o prazer de palestrar também. Falei sobre melhores práticas web components. Segue os slides a seguir:

[slideshare id=38535624&doc=frontinterior-140831113624-phpapp02]

## Conclusão

Todas essas boas práticas irão evoluir com a especificação, e isso é excelente.

 [1]: https://github.com/PolymerLabs/seed-element