---
title: Use as facilidades do CSS 4 hoje
author: Mateus Ortiz
type: post
date: 2015-10-26
excerpt: |
  |
    Conheça algumas das features do CSS 4 e como você pode  usa-las hoje.
url: /use-as-facilidades-do-css-4-hoje/
categories:
  - CSS
tags:
  - CSS
  - cssnext
  - pre-processadores

---
Se CSS 3 trouxe muitas animações e transições, CSS 4 por sua vez traz muitos seletores novos que facilitam e muito a resolver problemas recorrentes em projetos complexos e grandes. E a maioria ou quase todas você já pode usar hoje com ajuda de alguns transpilers de CSS. Você consegue ter variáveis sem precisar usar pre processadores como Sass ou Less. A spec de CSS nível 4 ainda está em desenvolvimento, mas com transpilers como [CSSNext][1] e [Rework][2], você já pode começar a usar essas features hoje.

A maioria dos seletores da especificação do CSS 4 são pseudo-classes. Os seletores sempre estiveram presentes desde o início da CSS, mas agora eles estão no nível 4 e tem um monte de adições incríveis. Vamos ver apenas as mais interessantes e ver como podemos fazer elas funcionarem hoje com a ajuda dos transpilers.

### O que é o CSSNext?

CSSNext é um transpiler que permite que você use as mais recentes features do CSS. Ele transforma as novas especificações CSS em CSS compatível com os navegadores hoje. E em um futuro proxímo, os navegadores irão implementar as novas especificações CSS. E com o tempo, poderemos ir removendo algumas transformações do cssnext que não será mais necessário.

Ele é muito rápido, cssnext usa [PostCSS][3] que tem parser CSS de forma mais rápida. É um bom concorrente para libsass, e um pouco mais rápido que o Less por exemplo.

### Como começar com o cssnext?

Para começarmos a brincar com o cssnext precisamos instalar ele, e pode ser feito de duas maneiras com Git ou NPM, que é o mais fácil.

`$ npm install cssnext`

Você pode instalá-lo local (&#8211;save ou &#8211;save-dev), ou instalar globalmente (-g) que não é muito recomendado.

Podemos usar cssnext via CLI, com alguma lib JavaScript, algum plugin PostCSS ou através do Gulp, Grunt, broccoli e outros.

E para você compilar um arquivo com as novas features CSS 4 para CSS compatível, basta você executar o arquivo de CSS 4 e o arquivo de saida:

`$ cssnext index.css output.css`

### Vamos as features!

#### 1. custom properties & var()

A especificação de CSS 4 dá a possibilidade de poder usar variáveis sem a necessidade de pré-processadores, hoje apenas o Chrome tem suporte a essa feature. E então o cssnext nós ajuda com isso.

<pre class="lang-css">:root {
  --mainBgColor: blue;
}

body {
  color: var(--mainBgColor);
}
</pre>

[<img class="alignnone size-full wp-image-51818" src="http://tableless.com.br/uploads/2015/10/variables.gif" alt="variables" width="1145" height="433" />][4]

#### 2. gray()

Permite que você use mais de 50 tons de cinza (transpilado para rgba()). No primeiro argumento, você pode usar um número entre 0 e 255 ou uma porcentagem.

<pre class="lang-css">.foo {
  color: gray(85%);
}

.bar {
  color: gray(10%, 50%);
}
</pre>

[<img class="alignnone size-full wp-image-51819" src="http://tableless.com.br/uploads/2015/10/gray.gif" alt="gray" width="1145" height="433" />][5]

#### 3. any-link

any-link simplifica os seletores de target de links. Como :link, :visited, :actived, para somente :any-link.

<pre class="lang-css">nav :any-link {
  background-color: yellow;
}
</pre>

[<img class="alignnone size-full wp-image-51820" src="http://tableless.com.br/uploads/2015/10/any-link.gif" alt="any-link" width="1145" height="433" />][6]

E tem muitas outras features incríveis que vem com o CSS 4, e se você quiser saber mais recomendo você ver esse artigo do [Diego Eis][7].

## Conclusão

CSS 4 está trazendo muitas features interessantes para seletores inteligentes, por enquanto só podemos brincar e experimentar as novidades do CSS 4 com a ajuda desses transpilers. Isso também mostra o quanto a W3C está interessada em solucionar os problemas dos devs sem a necessidade de usar um pre-processor.

## Links

  * [CSSNext][8]
  * [Rework][2]
  * [CSS4 Rocks][9]
  * [PostCSS][10]

 [1]: http://cssnext.io/features/
 [2]: https://github.com/reworkcss/rework
 [3]: https://github.com/postcss/postcss
 [4]: http://tableless.com.br/uploads/2015/10/variables.gif
 [5]: http://tableless.com.br/uploads/2015/10/gray.gif
 [6]: http://tableless.com.br/uploads/2015/10/any-link.gif
 [7]: http://tableless.com.br/seletores-css-nivel-4-o-que-vem-por-ai/
 [8]: http://cssnext.io/
 [9]: http://css4.rocks/
 [10]: https://github.com/postcss/