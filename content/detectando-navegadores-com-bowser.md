---
title: Detectando navegadores com Bowser
author: Raphael Guastaferro
type: post
date: 2015-11-24
excerpt: Projeto hospedado no GitHub ajuda a detectar versões e detalhes do navegador utilizado
url: /detectando-navegadores-com-bowser/
categories:
  - Browsers
  - JavaScript
  - Técnicas e Práticas
tags:
  - bowser
  - browser detection
  - internet explorer
  - navegadores

---
## Uma ajuda para detectar e dar suporte a diferentes navegadores

### O Bowser

Em muitos projetos, precisamos dar uma atenção especial para alguns navegadores (nosso querido IE, por exemplo). A proposta do **Bowser** é facilitar a detecção de navegadores e suas versões, minimizando os erros de detecção, e facilitando sua vida.

### Mãos à obra

Para começar, você precisa fazer o download do arquivo JavaScript do **Bowser** no <a href="https://github.com/ded/bowser" target="_blank">GitHub oficial do projeto</a>, e inclui-lo no seu HTML. Depois, basta fazer suas condicionais utilizando o objeto Javascript Bowser, que contém várias informações sobre seu navegador.

Podemos facilmente detectar se o navegador é IE, na versão menor ou igual a 8, como a seguir:

<pre class="lang-javascript,">if (bowser.msie && bowser.version &lt;= 8) {
  alert('Atualize seu browser!');
};
</pre>

Ou você pode detectar a _engine_ do navegador:

<pre class="lang-javascript,">if (bowser.webkit) {
  alert('A engine do seu navegador é Webkit!');
};
</pre>

E também pode fazer um tratamento específico pra mobile:

<pre class="lang-javascript,">if (bowser.mobile && bowser.ios) {
  alert('Você está num dispositivo mobile da Apple!');
};
</pre>

Agora você não precisa mais gastar seu tempo escrevendo muitas linhas de JavaScript com _regex_ para todos os lados, tentando detectar navegadores, versões, se é mobile ou desktop&#8230; O Bowser te entrega tudo isso.

O projeto está disponível no <a href="https://github.com/ded/bowser" target="_blank">GitHub</a>.