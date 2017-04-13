---
title: Angular 2, vale a pena?
author: Daniel Campos
type: post
date: 2016-12-02
excerpt: O Angular é hoje uma das ferramentas mais largamente utilizada para desenvolvimento front end. Vale a pena migrar para a nova versão?
url: /angular-2-vale-pena/
categories:
  - AngularJS
  - JavaScript
tags:
  - angular2
  - JavaScript
  - typescript

---
Ultimamente, com o boom do JavaScript, os desenvolvedores front end se depararam com a difícil questão: qual framework e/ou biblioteca usar em meu projeto? A resposta é: depende do que você está procurando. Construir uma SPA completa? Uma aplicação híbrida? Ou apenas um simples formulário? O objetivo aqui não é enumerar as diferenças entre todas as várias ferramentas existentes no mercado, e sim focar no Angular, a que considero mais completa e que pode atender a todos os objetivos de um projeto.

O Angular, apesar de ter sido pensado inicialmente para lidar apenas com formulários, é hoje uma das ferramentas mais largamente utilizada para desenvolvimento front end, porém, sempre teve seus problemas, dentre eles, os problemas de performance. E é esse um dos principais motivos que levou a equipe do Angular a desenvolver, do zero, a sua versão 2.

O <a href="https://angular-2-training-book.rangle.io/handout/why_angular_2.html" target="_blank">rangle.io</a> listou as principais diferenças entre o Angular 1 e o 2:

> “_Transitional Architecture_” se refere ao estilo de programação no Angular 1 de forma a se aproximar o máximo possível do Angular 2, mas com _Controllers_ e _Diretivas,_ ao invés de classes TypeScript.

<img class="alignnone wp-image-56319 size-full" src="http://tableless.com.br/uploads/2016/10/Captura-de-Tela-2016-10-27-às-10.28.09.png" alt="Comparação Angular 1 e 2 do rangle.io" width="718" height="274" />

## Mas e aí, vale ou não a pena?

### Adoção

A preocupação da maioria das pessoas é simplesmente não saber se Angular 2 vai realmente “vingar”, e acabam ficando com receio de migrar. Fazendo uma simples pesquisa no Google Trends, é possível comparar a popularidade do termo Angular 2, comparado a VueJS e ReactJS, as ferramentas que estão mais em alta atualmente.

<img class="alignnone wp-image-56321 size-full" src="http://tableless.com.br/uploads/2016/10/trends.jpg" alt="Comparação entre AngularJS, VueJS e ReactJS" width="1118" height="357" />

### Mobile

Se você pretende desenvolver aplicativos híbridos, cá está mais um excelente motivo para usar Angular 2, a equipe do Ionic está finalizando o desenvolvimento da sua segunda versão, que é totalmente escrita em Angular 2.

### TypeScript

Uma vez que a maioria dos navegadores não estão habilitados para rodar ES6 e ES7, surgiram alguns pré-compiladores, que geram todo o código para o JavaScript “entendível” pelo navegador. Mas o Typescript vai um pouco mais longe.

<img class="alignnone wp-image-56324 size-full" src="http://tableless.com.br/uploads/2016/10/v94tyy.jpg" alt="Meme TypeScript" width="512" height="358" />

O TypeScript, criado pela Microsoft (isso mesmo), é um “_superset_” do JavaScript, que, além de implementar as funcionalidades do ES6+, traz uma série de “poderes” no desenvolvimento. Uma das coisas que eu gosto bastante, é a capacidade de _autocomplete_ nas IDEs (se você tiver uma que suporte, como o Sublime Text ou VSCode). Mas acredito que o mais interessante é a parte de organização do código. O TypeScript tem uma sintaxe muito mais clara e fácil de entender. Abaixo um mesmo código escrito em TypeScript e JavaScript:

TypeScript:

<pre class="lang-javascript">class HelloWorld {
  text: string;
  constructor(text: string) {
    this.text = text;
  }
}
let txt = new HelloWorld("Olá mundo!");
console.log(txt);
</pre>

JavaScript:

<pre class="lang-javascript">var HelloWorld = (function () {
  function HelloWorld(text) {
    this.text = text;
  }
return HelloWorld;
}());
var txt = new HelloWorld("Olá mundo!");
console.log(txt);</pre>

### Performance

Um ponto muito importante de destaque é a performance. O Angular 1, de fato, oferece uma experiência de baixa performance devido a excessivas interações com a DOM. O Angular 2 vem pra resolver esse problema de uma vez por todas. O gráfico abaixo, feito pela <a href="https://auth0.com/blog/more-benchmarks-virtual-dom-vs-angular-12-vs-mithril-js-vs-the-rest/" target="_blank">auth0</a>, mostra, na prática o resultado do _benchmark_ que eles realizaram:

<img class="alignnone wp-image-56328 size-full" src="http://tableless.com.br/uploads/2016/10/angular2-grafico.png" alt="angular2 grafico por auth0" width="615" height="338" />

## Conclusão

O Angular 2 veio pra ficar, além de ser uma ferramenta que evoluiu, ter uma grande empresa como o Google por trás só ajuda. A adoção deste framework só tende a crescer mais, e, sim, vale muito a pena usar em seus projetos.