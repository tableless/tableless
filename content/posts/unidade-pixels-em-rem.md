---
title: Qual unidade utilizar – Pixel, EM ou REM
author: Diego Eis
type: post
date: 2012-09-03
excerpt: Entenda mais sobre as duas unidades prediletas pelos desenvolvedores.
url: /unidade-pixels-em-rem/
tweetbackscheck:
  - 1356407674
shorturls:
  - 'a:3:{s:9:"permalink";s:46:"http://tableless.com.br/unidade-pixels-em-rem/";s:7:"tinyurl";s:26:"http://tinyurl.com/8avfmy2";s:4:"isgd";s:19:"http://is.gd/wRR0fw";}'
twittercomments:
  - 'a:23:{i:242997199330484224;s:7:"retweet";i:242993549665251329;s:7:"retweet";i:242992576305709056;s:7:"retweet";i:242947055188844544;s:7:"retweet";i:242697395291422720;s:7:"retweet";i:242670468509859841;s:7:"retweet";i:242617665645076482;s:7:"retweet";i:242608049058111488;s:7:"retweet";i:242598525987332098;s:7:"retweet";i:242593610242088960;s:7:"retweet";i:242593520597209089;s:7:"retweet";i:246256474366562304;s:7:"retweet";i:254233108935761920;s:7:"retweet";i:254231218747490304;s:7:"retweet";i:261120526372708353;s:7:"retweet";i:261104544061222912;s:7:"retweet";i:261097112446578688;s:7:"retweet";i:261096998118240256;s:7:"retweet";i:264720202397278208;s:7:"retweet";i:264705361062273024;s:7:"retweet";i:264703111594139648;s:7:"retweet";i:267988526686150656;s:7:"retweet";i:267986395740647425;s:7:"retweet";}'
tweetcount:
  - 58
dsq_thread_id: 829044237
categories:
  - Acessibilidade
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2012
  - CSS
  - em
  - pixels
  - px
  - unidades

---
Aqui no Brasil é muito comum usarmos pixels para definição de tamanho de textos. Lá fora a galera gosta muito de usar EM. Mas qual a diferença? Por que usar um ou outro? 

### Pixels

Unidade em pixels é mais velho que andar para trás. Você utiliza pixels para definir a largura de um elemento, o tamanho do texto, a espessura da borda e outras coisas.

Os pixels são utilizados para definir o tamanho dos textos por que é a medida mais exata que você pode encontrar. Por não ser uma medida variável, Pixels são fáceis de controlar. Fáceis de usar. Você abre seu Photoshop, mede e pronto, passa os valores para CSS facilmente. É tudo muito eficiente. É por isso que todo mundo prefere utilizar pixels nos projetos, principalmente aqui no Brasil onde a preguiça impera.

Antigamente definir unidades de texto em pixels trazia uma desvantagem por causa do Internet Explorer. Quando o usuário tentava mudar o tamanho do texto pelo browser, por algum motivo bizarro o IE não aumentava esse texto pelo simples motivo de que o texto estava definido em pixels. Um problema sério de acessibilidade. É por isso que muitos devs preferiram durante um tempo definir o tamanho do texto utilizando % (porcentagem) em vez de trabalhar com pixels. O problema é que trabalhar com porcentagem é algo muito instável. Havia diferenças de tamanhos de textos entre os browsers e por causa disso o layout nunca ficava igual. 

<pre class="lang-css">body {
  font: normal 16px verdana, arial, tahoma, sans-serif;
}
</pre>

Agora, definindo a mesma font com um tamanho variável em porcentagem:

<pre class="lang-css">body {
  font: normal 100% verdana, arial, tahoma, sans-serif;
}
</pre>

A diferença de um e para outro é um pouco óbvia. O tamanho padrão das font dos browsers geralmente é de 16px. Logo, se você define que a fonte terá 100% do seu tamanho, você está dizendo que a font terá 16px. Claro, se algum dia o browser mudar o tamanho padrão de sua font, ela terá um novo fator de base.

### Unidades em EM

EM é uma unidade de medida tipográfica. Seu nome está relacionada com a letra “M”, onde o tamanho base dessa unidade deriva da largura da letra M em maiúscula. Dizem que 1em equivale aproximadamente 16 pontos.

Não sou eu que estou falando isso, <a href=“http://en.wikipedia.org/wiki/Em_(typography)”>é a Wikipedia</a>. 😉

O problema de utilizar fonts em EM é que elas são variáveis como a porcentagem. Diferentemente da utilização de pixels, temos que fazer um pouco de matemática para planejar nossas unidades no projeto. Não é nada de outro mundo, então pare de preguiça.

#### Calculando o EM

A fórmula é fácil de entender. Vou manter os termos em inglês para você entender melhor quando for procurar mais informações sobre este assunto: 

**target ÷ context = result**

Um exemplo: imagine um título, H1, cujo seu tamanho de texto seja 20px. 

<pre class="lang-css">h1 {
  font: 20px verdana, arial, tahoma, sans-serif;
}
</pre>

Então o target (que é o elemento que queremos modificar) é 20px. Nesse caso o BODY é o pai do nosso H1. Logo, valor da font do body é o context (contexto), que como já dissemos tem o valor padrão de 16px. Logo 20 ÷ 16 = 1.25.

<pre class="lang-css">h1 {
  font: 1.25em verdana, arial, tahoma, sans-serif;
}
</pre>

Se este H1 estiver dentro de um outro elemento, tipo um div, o valor de context agora é o tamanho da font do div. Tenha como exemplo esse HTML:

<pre class="lang-html">&lt;div&gt;
    &lt;h1&gt;Um t&iacute;tulo bacana&lt;/h1&gt;
    &lt;p&gt;Um texto grande e bacana para fazermos par&aacute;grafos.&lt;/p&gt;
&lt;/div&gt;
</pre>

O CSS:

<pre class="lang-css">div {
    font: 30px verdana, arial, tahoma, sans-serif;
}

h1 {
    font-size: 20px;
}

p {
    font-size: 12px;
}

</pre>

Vamos passar tudo isso para EM. Primeiro o parágrafo:
  
12px (target) ÷ 30px (context [div]) = 0.4em

Título:
  
20px (target) ÷ 30px (context [div]) = 0.67em

Div:
  
30px (target) ÷ 16px (context [body]) = 1.88em

Simples, ahn?

Isso é útil por quê?
  
Imagine que você faça um site mobile ou um site para grandes telas. Em vez de você mudar as fonts de cada elemento, você pode simplesmente muda o valor da font do target, ou seja, do body!

<pre class="lang-css">body {font: 100% verdana, arial, tahoma, sans-serif;}

div {
    font-size: 1.88em;
}

h1 {
    font-size: 0.67em;
}

p {
    font-size: 0.4em;
}
</pre>

Mudando o valor de porcentagem da font do body, você consegue mudar proporcionalmente a font de todos os outros elementos.

### Mas dá trabalho

Realmente… ficar calculando target e context para cada um dos elementos é muito chato. Seria interessante se o valor do context fosse sempre o mesmo, não é? Pois é… Já pensaram nisso e fizeram uma unidade chamada REM. 

A REM sempre terá o valor de contexto do ROOT (é isso que significa o R do REM), ou seja, sempre o body… Os valores do nosso exemplo acima ficaria assim se referenciando pelo body e não pelo DIV. Logo os valores ficam como abaixo:

<pre class="lang-css">body {font: 100% verdana, arial, tahoma, sans-serif;}

div {
    font-size: 1.88rem;
}

h1 {
    font-size: 1.25rem;
}

p {
    font-size: 0.75rem;
}
</pre>

Infelizmente isso não é para todos os browsers… Firefox 3.6+, Chrome, Safari 5, e IE9 suportam a unidade REM. Mas e os caras que não suportam? Bom, use a font em PX. Cá entre nós, dessa lista de browsers só faltou o IE8, já que o IE7 e 6 já foram embora. Se você não suportar em seus projetos o IE8, pode ignorar essa técnica. 

Basta definir os dois valores, tanto em REM quanto em PIXELS. Lembre-se de sempre colocar a linha de PIXELS antes da REM. Assim, os browsers que entendem REM vão sobreescrever o valor em PIXELS e os browsers que não conhecem REM vão ignorar essa linha.

<pre class="lang-css">body {font: 100% verdana, arial, tahoma, sans-serif;}

div {
    font-size: 30px;
    font-size: 1.88rem;
}

h1 {
    font-size: 20px;
    font-size: 1.25rem;
}

p {
    font-size: 12px;
    font-size: 0.75rem;
}
</pre>

Decidir qual dessas unidades usar não pode ser caso de dúvidas e atrasos. Saiba que pixels são mais precisos entre os browsers, mas menos flexíveis. Enquanto o REM/EM são mais flexíveis, nos dá a vantagem da acessibilidade, mas envolve um pouco de matemática. Mesmo assim utilizar REM tem sido uma ótima prática e não está trazendo tantos problemas crossbrowser.