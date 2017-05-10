---
title: Utilizando Map Structure do Sass
author: Diego Eis
type: post
date: 2014-08-11
excerpt: |
  |
    Estruturando variáveis de forma inteligente com o Maps do SASS.
url: /utilizando-maps-sass/
dsq_thread_id: 2915464932
categories:
  - Código
  - Pré-processadores
  - SASS
tags:
  - CSS
  - pre-processador
  - SASS

---
O Sass é um pré-processador usado para melhorar sua produtividade ao codificar CSS. Dentre as várias funcionalidades, existe uma chamada `maps`.

O `maps` é como um array de variáveis. Ela guarda uma série de chaves com valores. A sintaxe é bastante comum, veja:

<pre class="lang-sass">$map: (
  key1: value1, 
  key2: value2, 
  key3: value3
);
</pre>

A primeira vista se parece com Json, né?
  
A ideia é que você consiga pegar o valor de qualquer chave que está dentro do seu mapa e usar em momentos onde você irá repetir bastante código.

## Demo

No exemplo abaixo, vou mostrar uma situação muito comum ao desenvolvermos um site com variação de temas de cores. Na maneira normal, você faria um código basicamente assim:

<pre class="lang-css">.tema-azul body {
  background-color: #0176bb;
}

.tema-vermelho body {
  background-color: #e3413e;
}

.tema-amarelo body {
  background-color: #f8e042;
}
</pre>

Usando o mapa do SASS, a primeira coisa que faríamos seria separar as cores em variáveis, assim:

<pre class="lang-sass">$cores: (
  azul: #0176bb, 
  vermelho: #e3413e, 
  amarelo: #f8e042
);
</pre>

E faríamos uma função dessa forma:

<pre class="lang-sass">@each $tema, $cor in $cores {
  .tema-#{tema} body {
     background-color: $cor;
  }
}
</pre>

O `$tema` seria cada uma das chaves, no nosso caso `azul`, `vermelho` e `amarelo`. O `$cor` seria cada um dos valores dos temas, ou seja, os valores hexadecimais. A função `@each` está dizendo assim: a cada valor dos temas (azul, vermelho, amarelo) que encontrar no mapa `$cores`, repita o bloco de código.

Isso resultaria no seguinte código:

<pre class="lang-css">.tema-azul body {
  background-color: #0176bb;
}

.tema-vermelho body {
  background-color: #e3413e;
}

.tema-amarelo body {
  background-color: #f8e042;
}
</pre>

Isso salva vidas. Agora vamos complicar mais. Normalmente um tema é composto de mais cores. Para isso o mapa vai ficar parecido isso:

<pre class="lang-sass">$cores: (
  azul: (
    color1: #0176bb, 
    color2: #23aad0,
    color3: #edf7fd
  ),
  vermelho: (
    color1: #e3413e, 
    color2: #1f518c,
    color3: #f8e042
  ),
  amarelo: (
    color1: #4a5269, 
    color2: #fc7d74,
    color3: #4a5269
  )
);
</pre>

O código do `@each` não mudará muito, mas precisaremos guardar cada uma dessas cores dentro de uma variável que será usada no código final. Ficará assim:

<pre class="lang-sass">@each $tema, $cor in $cores {
  $color1: map-get($cor, color1);
  $color2: map-get($cor, color2);
  $color3: map-get($cor, color3);
}
</pre>

Explicando: a cada `$tema` (azul, vermelho e amarelo) que há no mapa `$cores`, ele vai gravar as variáveis `$color1`, `$color2` e `$color3`. A função `map-get` vai pegar o valor específico de cada variável `color1`, `color2` e `color3` de cada tema e irá guardar. O código CSS fica assim:

<pre class="lang-scss">@each $tema, $cor in $cores {
  $color1: map-get($cor, color1);
  $color2: map-get($cor, color2);
  $color3: map-get($cor, color3);

  .color-#{$tema} {
    body {
      background-color: $color1;
    }

    .header {
      background-color: $color2;
    }

    .menu a {
      background-color: $color3;
    }

  }
}
</pre>

Ele vai repetir o bloco acima uma vez para cada tema de cor. No nosso caso, 3 vezes: uma para azul, vermelho e amarelo. 

Novamente: isso salva vidas.
  
A única coisa que você vai gerenciar depois são as variáveis para modificar ou inserir novas cores.

Veja abaixo um exemplo mais completo, mostrando o código final do CSS gerado:

<p class="sassmeister" data-gist-id="9fc788894331313ce485" data-height="480">
  <a href="http://sassmeister.com/gist/9fc788894331313ce485">Play with this gist on SassMeister.</a>
</p>



[O pessoal do Viget explorou outro problema][1] para resolver. Na verdade, as implicações são diversas. A qualquer momento que você tiver um bloco de código repetitivo e que depende de muitas variações, o `maps` é indicado.

 [1]: http://viget.com/extend/sass-maps-are-awesome