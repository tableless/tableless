---
title: Como usar variáveis no CSS de forma nativa
author: Afonso Pacifer
type: post
date: 2015-11-17
excerpt: Como utilizar o conceito de variáveis nativas do CSS3.
url: /como-usar-variaveis-no-css-de-forma-nativa/
categories:
  - CSS
  - CSS3
tags:
  - CSS
  - CSS3
  - postCSS
  - variaveis

---
<p class="p3">
  <span class="s1">Olá pessoal, neste artigo irei abordar o básico sobre variáveis nativas com CSS, e como você pode usar essa tecnologia hoje e sem medo de ser feliz.</span>
</p>

## **<span class="s1"><a href="http://www.w3.org/TR/css-variables/" target="_blank">CSS Custom Properties for Cascading Variables Module Level 1</a></span>** {.p4}

<p class="p3">
  <span class="s1">Esta especificação ainda em fase de <em>Last Call Working Draft</em>, traz um novo módulo de CSS3 que permite a criação de varáveis de forma nativa, de uma forma simples e rápida como veremos a seguir.</span>
</p>

## <span class="s1">Como declarar uma variável?</span> {.p5}

<p class="p3">
  <span class="s1">Para declarar uma variável utilizamos as chamadas <em>Custom Properties</em>, uma nova forma de declarar uma propriedade utilizando a seguinte sintaxe:</span>
</p>

<pre class="lang-css">.exemplo {
  --destaque: #660066;
}
</pre>

<p class="p3">
  <span class="s1">Por definição uma <em>Custom Property</em> é qualquer propriedade que inicie com dois hífens, como ‘—foo’. </span>
</p>

## <span class="s1">Como utilizar uma variável?</span> {.p5}

<p class="p3">
  <span class="s1">Para utilizar uma variável utilizamos a função var(), passando a variável criada como parâmetro,  assim ela irá retornar o valor da variável, veja o exemplo a seguir:</span>
</p>

<pre class="lang-css">.exemplo {
  --destaque: #660066;
  background-color: var(--destaque);
}
</pre>

<p class="p3">
  <span class="s1">O que equivale diretamente a:</span>
</p>

<pre class="lang-css">.exemplo {
  background-color: #660066;
}
</pre>

## <span class="s1">A notícia ruim 🙁</span> {.p5}

<p class="p3">
  <span class="s1">As variáveis tem um escopo a ser seguido, logo uma variável não pode ser usada fora de seu escopo.</span>
</p>

<p class="p3">
  <span class="s1">Exemplos de utilização correta do escopo:</span>
</p>

<pre class="lang-css">.menu {
  --tamanho: 20px;
}
.menu ul li {
  padding: var(--tamanho); // retorna 20px
}
</pre>

<p class="p3">
  <span class="s1">Exemplo de utilização incorreta do escopo:</span>
</p>

<pre class="lang-css">.menu {
  --tamanho: 20px;
}
.footer {
  padding: var(--tamanho); // não retorna nada
}
</pre>

## <span class="s1">A notícia boa 🙂</span> {.p5}

<p class="p3">
  <span class="s1">Podemos declarar variáveis em um tipo de &#8220;escopo global”, que nada mais é do que a raiz do documento,<span class="Apple-converted-space">  </span>para isso utilizamos o seletor :root.</span>
</p>

<p class="p3">
  <span class="s1">Exemplo de variáveis declaradas na raiz do documento.</span>
</p>

<pre class="lang-css">:root {
  --tamanho: 50%;
  --cor: #660066;
}

.exemplo-1 {
  margin: var(--tamanho); // retorna 50%
}

.exemplo-2 {
  color: var(--cor); // retorna #660066
}
</pre>

## <span class="s1">Até aqui legal, mas e o suporte?</span> {.p5}

<p class="p3">
  <span class="s1">Nem tudo são flores amigos, até o momento o suporte é apenas para Firefox. Vejam a tabela completa no <a href="http://caniuse.com/#feat=css-variables" target="_blank">Can i use</a>.</span>
</p>

## <span class="s1">Como usar hoje!</span> {.p5}

<p class="p3">
  <span class="s1">Não teria graça se eu trouxesse aqui uma coisa tão divertida e ninguém pudesse usar, e com um suporte tão ruim, só nos resta apelar para o<span class="Apple-converted-space"> </span>maravilhoso <a href="https://github.com/MadLittleMods/postcss-css-variables" target="_blank">postcss-css-variables</a>, que é um plugin para <a href="https://github.com/postcss/postcss" target="_blank">Post CSS</a>.</span>
</p>

### **<span class="s1">Mas o que é mesmo esse Post CSS?</span>** {.p3}

<p class="p3">
  <span class="s1">Esse cara é um pós-processador de CSS que possuí vários <a href="https://github.com/postcss/postcss#plugins" target="_blank">plugins</a>, sendo o mais famoso o <a href="https://github.com/postcss/autoprefixer" target="_blank">Autoprefixer</a>, quer por sua vez pega seu código e aplica os <em>vendors prefixes</em> conforme a necessidade, e é exatamente isso que o postcss-css-variables faz, ele pega suas variáveis e as poem em seu devido lugar, compilando seu &#8220;CSS do futuro&#8221;, para um CSS nativo e suportado por todos.</span>
</p>

<p class="p3">
  <span class="s1">Você pode ver exatamente como o plugin funciona no <a href="https://madlittlemods.github.io/postcss-css-variables/playground/" target="_blank">postcss-css-variables Playground</a>.</span>
</p>

### **<span class="s1">Quais as vantagens de utilizar o postcss-css-variables?</span>** {.p3}

<p class="p3">
  <span class="s1">1 &#8211; Você vai <strong>escrever o CSS de forma nativa</strong>, e usar o pós-processador como um tipo de &#8220;polyfill&#8221;, que no futuro,  caso outros navegares além do firefox adotem a especificação, pode ser retirado e seu código já estará pronto, mais ou menos como ocorre com o JavaScript e o <a href="https://babeljs.io/" target="_blank">Babel</a>.</span>
</p>

<p class="p3">
  <span class="s1">2 &#8211; Usar uma coisa nova em seu <em>workflow</em>. Isso faz bem, principalmente quando abre um leque de novas possibilidades como aprender outras várias funções incríveis que o Post CSS trás.</span>
</p>

## <span class="s1">Conclusão</span> {.p5}

<p class="p3">
  <span class="s1">Caso alguém me pergunte se <strong>v</strong></span><strong><span class="s1">ale a pena mudar o <em>workflow</em> apenas para escrever variáveis de forma nativa?</span></strong>
</p>

<p class="p3">
  <span class="s1">Talvez a resposta seja <strong>não</strong>.</span>
</p>

<p class="p3">
  <span class="s1">Agora, se alguém perguntasse se <strong>v</strong></span><span class="s1"><strong>ale a pena brincar com uma coisa nova</strong>, que no fim das contas vai me <strong>ensinar sobre pós-processadores</strong>, me apresentar uma especificação que pode <strong>virar padrão no futuro</strong> e me fazer <strong>refletir sobre formas diferentes de fazer a mesma coisa?</strong></span>
</p>

<p class="p3">
  <span class="s1">Nesse caso a resposta é um imenso <strong>SIM</strong>.</span>
</p>