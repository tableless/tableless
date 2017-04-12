---
title: Utilizando Mixins em pré-processadores CSS
author: João Felix
type: post
date: 2014-01-13
excerpt: Entendendo o básico de mixins do SASS.
url: /utilizando-mixins-em-css-preprocessors/
categories:
  - Pré-processadores
  - SASS
tags:
  - CSS
  - mixins
  - pre-processadores
  - SASS

---
Recentemente respondi à uma enquete (não me perguntem aonde, eu esqueci! :-() onde era perguntado sobre como lidávamos com prefixos proprietários em nossos códigos CSS. Até aquele momento apenas cerca de 9% dos participantes usavam Pré-processadores e cerca de 26% escreviam os [prefixos do browsers][1] “na unha”.

Pré-processadores de CSS ainda não são um comum para algumas pessoas, mas eu, particularmente, defendo o uso devido à organização e redução de trabalho na escrita de folhas de estilo, proporcionado entre outros, pelo encadeamento e os “mixins”, algo como “associação interna”, que funcionam melhores que muitos analgésicos para dores de cabeça causadas pelo retrabalho.

Considero o dilema dos prefixos proprietários como o maior motivo para utilizarmos mixins, já que eles estão em processo de adaptação, sofrem recorrentes mudanças e em um curto prazo (<span style="text-decoration: line-through">com um pouco de fé</span>) serão removidos para dar lugar à normalização (se quiser entender mais, recomendo o artigo <a title="Prefixos dos browsers: A web precisa de você" href="http://tableless.com.br/prefixos-dos-browsers-a-web-precisa-de-voce/" target="_blank">&#8220;Prefixos dos browsers: A web precisa de você&#8221;</a>). Para você que só acredita vendo, prefixos proprietários são mais ou menos assim:

<pre class="lang-css">.elemento1 {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  -o-border-radius: 10px;
  border-radius: 10px;
}
.elemento2 {
  -webkit-border-radius: 12px;
  -moz-border-radius: 12px;
  -ms-border-radius: 12px;
  -o-border-radius: 12px;
  border-radius: 12px;
}
</pre>

A grande dificuldade surge na manutenção de extensos arquivos CSS, com inúmeras referências à estes prefixos e que precisam ser alterados. No caso de um CSS puro, a melhor alternativa é abrir um editor de texto e procurar todas as ocorrências para altera-las uma a uma, agora, considerando a utilização de pré-processadores, como o <a title="LESS CSS" href="http://lesscss.org/" target="_blank">LESS</a> e o <a title="SASS LANG" href="http://sass-lang.com/" target="_blank">SASS</a> (de certa forma maduros), o uso de mixins pode ser adotado para concentrar a necessidade de mudança em apenas um trecho do código.

<span style="line-height: 1.5em">Exemplo LESS:</span>

<pre class="lang-css">.border-radius (@radius) {
  -webkit-border-radius: @radius;
  -moz-border-radius: @radius;
  -ms-border-radius: @radius;
  -o-border-radius: @radius;
  border-radius: @radius;
}
.elemento1 {
 .border-radius(10px);
}
.elemento2 {
 .border-radius(12px);
}</pre>

Exemplo SASS:

<pre class="lang-css">@mixin border-radius ($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  -ms-border-radius: $radius;
  -o-border-radius: $radius;
  border-radius: $radius;
}
.elemento1 {
 @include border-radius(10px);
}
.elemento2 {
 @include border-radius(12px);
}
</pre>

Este é um exemplo simples de mixins, em uma utilização mais aprofundada é possível trabalhar mais variáveis, valores padrões e até mesmo sobrecarga.

Deixando de lado o padrão de escrita de cada pré-processador, ambos resultam no seguinte código CSS:

<pre class="lang-css">.elemento1 {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  -o-border-radius: 10px;
  border-radius: 10px;
}
.elemento2 {
  -webkit-border-radius: 12px;
  -moz-border-radius: 12px;
  -ms-border-radius: 12px;
  -o-border-radius: 12px;
  border-radius: 12px;
}
</pre>

Os mixins podem ser reutilizados e reescritos, deixando um código organizado e de fácil manutenção, no entanto, eu não seria imprudente a ponto de recomendar a utilização de pré-processadores aos sete ventos. É extremamente necessário uma avaliação do projeto e suas reais necessidades da utilização de uma ferramenta dessas, que, dependendo das proporções e finalidades do CSS, acabam apenas por aumentar a complexidade do desenvolvimento.

 [1]: http://tableless.com.br/prefixos-dos-browsers-a-web-precisa-de-voce/ "Prefixos dos browsers: A web precisa de você"