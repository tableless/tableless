---
title: Criando facebook reactions com css
authors: Deivid Marques
type: post
date: 2016-03-07
excerpt: Criando novos botões de comportamento do Facebook usando apenas CSS e HTML.
url: /criando-facebook-reactions-com-css/
categories:
  - CSS
  - CSS3
  - HTML

---
## Introdução

No dia 24 de fevereiro de 2016, o Facebook liberou seus novos botões de curtir, chamado de &#8220;Facebook Reactions&#8221;, a função foi liberada para todos os usuários, já que estava em fase de testes em alguns países.

São eles: Curtir, Amei, Haha, Uau, Triste, Grr.

Essa novidade é uma ótima maneira de saber como seus contatos reagem ao que você compartilha na rede social.
  
Em 2014 o Facebook registrou a patente que previa esses botões com sentimentos, <a href="https://thenextweb.com/facebook/2015/09/18/facebook-patent-reveals-what-its-empathy-button-might-look-like/" target="_blank">leia mais detalhes</a>.

Como sou apaixonado por CSS, resolvi criar essas micro interações ao passar o mouse sobre o elemento, e também caso use o teclado.

Cheguei a olhar como o Facebook criou aquelas animações, e resolvi fazer algo mais simples usando a propriedade translate e não animation conforme eles usaram no deles.

## Veja o HTML

<pre class="lang-html">&lt;div class="box"&gt;
  &lt;input type="checkbox" id="like" class="field-reactions"&gt;
  &lt;span class="text-desc"&gt;Press space and after tab key to navigation&lt;/span&gt;
  &lt;label for="like" class="label-reactions"&gt;Like&lt;/label&gt;
  &lt;div class="toolbox"&gt;&lt;/div&gt;
  &lt;label class="overlay" for="like"&gt;&lt;/label&gt;
  &lt;button class="reaction-like"&gt;&lt;span class="legend-reaction"&gt;Like&lt;/span&gt;&lt;/button&gt;
  &lt;button class="reaction-love"&gt;&lt;span class="legend-reaction"&gt;Love&lt;/span&gt;&lt;/button&gt;
  &lt;button class="reaction-haha"&gt;&lt;span class="legend-reaction"&gt;Haha&lt;/span&gt;&lt;/button&gt;
 &lt;button class="reaction-wow"&gt;&lt;span class="legend-reaction"&gt;Wow&lt;/span&gt;&lt;/button&gt;
 &lt;button class="reaction-sad"&gt;&lt;span class="legend-reaction"&gt;Sad&lt;/span&gt;&lt;/button&gt;
 &lt;button class="reaction-angry"&gt;&lt;span class="legend-reaction"&gt;Angry&lt;/span&gt;&lt;/button&gt;
&lt;/div&gt;</pre>

## o HTML

**Linha 1:** _área geral do elemento que recebe o hover  e com isso inicia as interações utilizando o mouse._

**Linha 2:** _input checkbox utilizado pra iniciar as interações ao ser checado via mouse ou teclado._

**Linha 3**: _mensagem exibida pro usuário assim que ele navegar com o teclado e o input da linha 2 receber o foco._

**Linha 4:** _elemento que recebe o background do like e também ao ser clicado faz o change do input checkbox e iniciando as interações._

**Linha 5:** _caixa branca com borda arredondada que tem uma animação diferente dos reactions, por isso ele não é pai dos elementos._

**Linha 6:** _overlay sem cor alguma que serve pra fechar as interações, caso o usuário clique na área fora do box._

**Linha 7 a 12:** _reactions do Facebook que possui uma animação ao receber o :hover ou :focus.  Adicionei em cada um a propriedade transition-delay com diferença de 0.03s entre eles_

## O CSS

Para exibir os Reactions através do mouse, utilizei o :hover do CSS na classe .box , que é o pai geral dos elementos.

Para exibir via teclado, ou click do mouse, existe um input[type=&#8221;checked&#8221;], que manipula seus irmãos (os Reactions e o background branco com borda arredondada).

O elemento branco com borda arredondada, mesmo que visualmente ele esteja atrás como background dos Reactions, no html ele é irmão, com isso foi feito uma outra animação específica pra ele, algo bem simples, apenas dando um show.

#### Os Reactions

Conforme se vê abaixo, é chamado o sprite dos Reactions e seus elementos de exibição (width, height, position, top, etc). Os reactions inicia com opacidade, 0 scale 10%, e o transform-origin. Lembrando que eles serão exibidos quando o elemento pai (.box) receber o hover do mouse e/ou quando o input for checado.

<pre class="lang-css">[class*="reaction-"] {
border: none;
background-image: url(https://fbstatic-a.akamaihd.net/rsrc.php/v2/yh/r/sqhTN9lgaYm.png);
background-color: transparent;
display: block;
cursor: pointer;
height: 48px;
position: absolute;
width: 48px;
z-index: 11;
top: -28;
transform-origin: 50% 100%;
transform: scale(0.1);
transition: all 0.3s;
outline: none;
will-change: transform;
opacity: 0;
}
</pre>

#### Animando

Como temos aquele input[type=&#8221;checked], citado anteriormente, através do CSS, podemos usar o :hover, e o :checked desse input e gerar nossas interações mais fáceis em seus irmãos, ou seja, manipulado a opacidade e o scale dos Reactions, ao passar o mouse, ou clicar no like, ou navegar com o teclado checando o input escondido.

Se vocês repararem existe uma diferença de animação entre o primeiro Reactions e o último e isso foi resolvido bem simples, aplicando um delay pra cada um. (veja abaixo)

<pre class="lang-css">.box:hover .reaction-love {
 transition-delay: 0.03s;
}
.box:hover .reaction-haha {
 transition-delay: 0.09s;
}
.box:hover .reaction-wow {
 transition-delay: 0.12s;
}
.box:hover .reaction-sad {
 transition-delay: 0.15s;
}
.box:hover .reaction-angry {
 transition-delay: 0.18s;
}</pre>

Pra finalizar, existe um outro comportamento aplicado em cada Reactions que exibe a legenda (inicia com opacidade 0), e muda no :hover e o :focus de cada Reaction para 1 na opacidade.
  
Inicialmemte eles estão escondidos e pequenos e ao passar o mouse ou receber o foco, são exibidos.

<pre class="lang-css">.box:hover [class*="reaction-"]:hover .legend-reaction, 
.box:hover [class*="reaction-"]:focus .legend-reaction {
 opacity: 1;
}</pre>

#### Bônus

A propriedade  will-change  otimiza animações, permitindo que o navegador sabe quais propriedades e elementos estão prestes a ser manipulados, aumentando potencialmente o desempenho dessa operação específica.

O will-change é uma recomentação do W3C, desde dezembro de 2015, e seu suporte aos navegadores atuais são bons, segundo o <a href="https://caniuse.com/#search=will-change" target="_blank">caninuse</a> somente os IEs e o Edge não dão suporte atualmente.

Para saber mais sobre will change <a href="https://www.w3.org/TR/css-will-change-1/" target="_blank">veja a documentação do W3C</a>

<pre class="lang-css">[class*="reaction-"] {
  transform-origin: 50% 100%;
  transform: scale(0.1);
  transition: all 0.3s;
  will-change: transform, opacity;
}</pre>

## Em resumo

O grande segredo então seria conhecer algumas propriedades de animação como, translate, transform, opacity, visibility, e lembrar que podemos manipular elementos irmãos com :checked ou :hover do pai e manipular seus elementos filhos.

## Veja o demo {.codepen}

{{< codepen 
  hash="wGvbwY"
  user="deividmarques"
  author="Deivid Marques"
>}}

## Conclusão

Inicialmente criei as interações acontecendo apenas no click do elemento, porém no resultado final mudei para o hover do mouse, e também deixei funcionando ao usar a tecla TAB, sendo foi possível navegar pelos &#8220;Reactions&#8221; com o teclado também.

Utilizei HTML e SASS, claro que daria pra fazer de outras maneiras, escrever menos códigos, até mesmo usando funções do sass em alguns lugares, mas isso ficará pra próxima versão.

O intuito de criar esse pequeno exemplo foi me divertir e também em mostrar os poderes que o CSS têm ao se criar essas micro interações.

<div style="overflow: hidden">
  <p>
    <a style="float: left;margin: 0 15px 15px 0" href="https://deividmarques.github.io/facebook-reactions-css/"><img class="alignleft size-full wp-image-53344" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2016/02/print-cel.png" alt="facebook reactions com css by Deivid Marques" width="300" height="533" /></a>
  </p>
  
  <p>
    O resultado por ser <a href="https://deividmarques.github.io/facebook-reactions-css/" target="_blank">conferido aqui</a><br /> Gostou? Dê um click nas estrelinhas do projeto lá no <a href="https://github.com/deividmarques/facebook-reactions-css" target="_blank">github</a>
  </p>
</div>