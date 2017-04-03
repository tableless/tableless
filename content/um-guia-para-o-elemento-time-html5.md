---
title: Um guia para o elemento ‘time’ do HTML5
author: Raphael Fabeni
type: post
date: 2014-09-29
excerpt: Conheça mais detalhes sobre a tag Time. Ela parece inocente, mas guarda vários segredos.
url: /um-guia-para-o-elemento-time-html5/
categories:
  - Artigos
  - Geral
  - Traduções
tags:
  - datetime
  - elemento
  - html5
  - time

---
O HTML5 trouxe diversas coisas bacanas pra nós desenvolvedores. Uma das mais simples e que eu acho que são uma das mais legais é a questão da semântica com os novos elementos. O surgimento dessas _tags_ deixaram nossos códigos mais semânticos e legíveis, tanto por nós como pelas máquinas.

Um desses elementos é o `time`. Já havia lido sobre ele, mas nunca tinha ido muito a fundo. Esses dias encontrei um texto do <a href="https://twitter.com/AurelioDeRosa" target="_blank">Aurelio De Rosa</a> no <a href="http://www.sitepoint.com/" target="_blank">SitePoint</a> que <a href="http://www.sitepoint.com/html5-time-element-guide/" target="_blank">explica bastante coisa</a> sobre este elemento e resolvi traduzir pra gente.

&#8212;

Tempo &#8211; uma das poucas coisas que sabemos que é infinita. Os seres humanos, bem como animais e plantas, têm lidado com o tempo desde o início de sua existência.

Na web essa necessidade não é diferente. Mesmo nesse meio, precisamos nos comunicar com outras pessoas de que alguma coisa aconteceu em um determinado ponto, em uma data específica, ou em relação a um outro tempo definido.

Antes do HTML5 não tivemos nenhum elemento para marcar semanticamente uma data ou hora. Nos últimos anos, outras soluções, como os <a href="http://microformats.org/" target="_blank">Microformats</a> e <a href="http://en.wikipedia.org/wiki/Microdata_%28HTML%29" target="_blank">Microdata</a>, tentaram preencher esta lacuna para situações específicas (data de nascimento, a publicação de um livro, e assim por diante).

Nesse artigo eu irei cobrir o elemento `time` do HTML5, o que ajuda a responder à necessidade de que acabamos de discutir.

## O que é o elemento `time`?

O elemento `time` foi introduzido na especificação do HTML5 em 2009. Então, em 2011 foi trocado  em favor do `data`. Então, em seguida, o elemento foi reintroduzido e melhorado para permitir novos formatos de data/hora. A partir deste ponto você pode ver que as especificações podem ser bastante controversas.

O elemento `time` representa uma data e/ou um tempo no <a href="http://en.wikipedia.org/wiki/Gregorian_calendar" target="_blank">calendário gregoriano</a>. É um elemento inline (como `<span>` e `<a>`) e deve ter uma tag de fechamento (como `<div>` e `<span>`). Quando usado na sua forma mais simples, o conteúdo do elemento deve ser uma string <a href="http://www.w3.org/TR/html5/text-level-semantics.html#the-time-element" target="_blank">de data e/ou tempo válidas</a>.

Um exemplo abaixo:

<pre class="lang-html">&lt;!-- 1º Fevereiro 2009 --&gt;
&lt;time&gt;2009-02-01&lt;/time&gt;
</pre>

No código acima, eu estou definindo uma data, especificamente 1º de fevereiro de 2009. O formato utilizado no código (aaaa-mm-dd) deve ser familiar para você se você já mexeu algum tempo com Linux, mas, como veremos mais adiante neste artigo, este não é o único formato válido.

No primeiro esboço das especificações, datas precisas eram um dos poucos formatos que você podia escrever. Por exemplo, você não podia especificar uma data como &#8220;Novembro 2014&#8221; ou &#8220;476&#8221; (o início da Idade Média). Isso foi um grande problema para vários casos, como a datação de uma pintura ou de um acontecimento histórico pois não havia uma data precisa.

Felizmente, esse tipo de data agora é permitida na especificação. Então, hoje nós podemos descrever um determinado mês de um ano sem um dia:

<pre class="lang-html">&lt;!-- Janeiro 2014 --&gt;
&lt;time&gt;2014-01&lt;/time&gt;
</pre>

## O atributo `datetime`

A especificação para o elemento também padronizou um atributo chamado de `datetime`.

Ao escrevermos datas como nos formatos discutidos na seção anterior, pode funciona em alguns países/culturas, como pode não atender outros. Por exemplo, os italianos (e nós brasileiros) escrevem datas usando o formato _dd/mm/aaaa_. Portanto, mostrar uma data em outro formato pode gerar confusão.

Este problema pode ser facilmente resolvido usando o atributo `datetime` do elemento `time`. É um atributo opcional que contém as informações em um formato legível por uma máquina, como os observados nos exemplos anteriores, o que nos permite que possamos escrever o conteúdo do elemento da qualquer maneira que nós quisermos.

Na verdade, se o atributo `datetime` não for especificado, o conteúdo deve estar em um dos formatos de data/hora válidos, caso contrário, podemos usá-lo como quisermos. Isso é ótimo porque nos permite escrever um código assim:

<pre class="lang-html">A próxima reunião está agendada para &lt;time datetime="2014-10"&gt;Outubro&lt;/time&gt;.
</pre>

Ou assim:

<pre class="lang-html">A próxima reunião está agendada para o &lt;time datetime="2014-10"&gt;próximo mês&lt;/time&gt;.
</pre>

Ambos exemplos possuem um conteúdo de data que não é legível por uma máquina de acordo com a especificação, mas são aceitáveis​​, por causa da presença do atributo `datetime`, que _faz uso_ de um formato válido.

À primeira vista, isso pode parecer estranho. Mas o conteúdo do elemento foi concebido para servir os seres humanos, não máquinas. Além disso, esse fato permite a internacionalização das datas. Por exemplo:

<pre class="lang-html">&lt;!-- Mesma mensagem anterior, só que em italiano --&gt;
Il prossimo incontro è programmato per &lt;time datetime="2014-10"&gt;il mese prossimo&lt;/time&gt;.
</pre>

No código acima temos a mesma mensagem anterior, só que em Italiano.

## O atributo `pubdate`

Os primeiros rascunhos da especificação definiam um atributo `pubdate` para o elemento `time`. Este atributo era um _booleano_ que indicava que uma determinada data era a data de publicação do elemento pai `article` ou, em caso de ausência de elemento `article` pai, de todo o documento.

Você poderia escrever por exemplo:

<pre class="lang-html">&lt;article&gt;
    &lt;h1&gt;Um título&lt;/h1&gt;
    &lt;p&gt;Esse é o conteúdo do article.&lt;/p&gt;
    &lt;footer&gt;
        &lt;p&gt;Artigo publicado em &lt;time datetime="2014-09-05" pubdate&gt;05 de setembro de 2014&lt;/time&gt;
    &lt;/footer&gt;
&lt;/article&gt;
</pre>

Nesse caso, 05 de setembro de 2014 seria a data de publicação desse `article`.

Eu fui um grande fã deste atributo desde que aprendi bastante sobre isso, mas, infelizmente, ele foi removido da especificação. Essa decisão criou um grande problema, porque um grande número de pessoas (inclusive eu) usam a data de publicação para julgar o frescor e a relevância de um artigo ou notícia. Embora seja verdade que você ainda possa acessar a página de um artigo e ver a data de publicação, precisamos de uma forma padrão para uma máquina de ler a data.

No atual momento não existe um atributo que substitua `pubdate`, mas você pode empregar o <a href="http://schema.org/BlogPosting" target="_blank">BlogPosting schema</a>, e especificamente o valor `datePublished` como mostrado abaixo:

<pre class="lang-html">&lt;article itemscope itemType="http://schema.org/BlogPosting"&gt;
        &lt;h1 itemprop="headline"&gt;Um título&lt;/h1&gt;
        &lt;p itemprop="articleBody"&gt;Conteúdo do article.&lt;/p&gt;
 
        &lt;footer&gt;
            &lt;p&gt;Artigo publicado em &lt;time datetime="2014-09-05" itemprop="datePublished"&gt;05 de setembro de 2014&lt;/time&gt;
        &lt;/footer&gt;
&lt;/article&gt;
</pre>

Agora que você tem um _overview_ completo do elemento `time`, vamos ver os diversos formatos permitidos.

Os formatos validos para o conteúdo do elemento `time` na ausência do atributo `datetime` e para esse atributo em si são descritos nos itens seguintes.

## Um mês válido

Deve ser uma _string_ especificando um mês específico de um ano no formato **aaaa-mm**. Por exemplo:

<pre class="lang-html">&lt;!-- Setembro 2014 --&gt;
&lt;time&gt;2014-09&lt;/time&gt;  
</pre>

## Uma data válida (dia do mês)

Deve ser uma _string_ especificando uma data precisa no formato **aaaa-mm-dd**.

Por exemplo:

<pre class="lang-html">&lt;!-- 16 de setembro de 2014 --&gt;
&lt;time&gt;2014-09-16&lt;/time&gt;
</pre>

## Uma data válida sem ano

Deve ser uma _string_ especificando um mês e um dia sem um ano no formato **mm-dd**.

Por exemplo:

<pre class="lang-html">&lt;!-- 29 de Junho --&gt;
&lt;time&gt;06-29&lt;/time&gt;
</pre>

## Um tempo válido

Deve ser uma _string_ especificando um tempo sem uma data e usando o formato 24 horas, da seguinte maneira **HH:MM[:SS[.mm]]** onde:

  * **H** são horas
  * **M** são minutos
  * **S** são segundos
  * **m** são milisegundos
  * Os _brackets_ indicam partes que são opcionais.

Um exemplo desse formato mostrado abaixo:

<pre class="lang-html">&lt;!-- 16 horas e 10 minutos (ou 4 horas e 10 minutos pm) --&gt;
&lt;time datetime="16:10"&gt;afternoon&lt;/time&gt;
</pre>

## Uma data e hora _flutuante_ válida

Esse formato é apresentado na especificação do W3C, mas não na versão WHATWG. Deve ser uma data e um tempo precisos no formato **aaaa-mm-ddTHH:MM[:SS[.mm]]** ou **aaaa-mm-dd HH:MM[:SS[.mmm]]**. Por exemplo:

<pre class="lang-html">&lt;!-- 16 de Setembro de 2014 às 18 horas, 20 minutos, e 30 segundos --&gt;
&lt;time datetime="2014-09-16T18:20:30"&gt;Terça-feira às 18:20&lt;/time&gt;
</pre>

## Um fuso horário válido

Deve ser uma _string_ representando um fuso horário. Por exemplo:

<pre class="lang-html">&lt;!-- GMT+1 (Itália) --&gt;
&lt;time&gt;+01:00&lt;/time&gt;
</pre>

## Uma data e tempo global válidos

Deve ser uma _string_ representando uma data completa, incluindo tempo e fuso horário. Por exemplo:

<pre class="lang-html">&lt;!-- 16 de Setembro de 2014 às 18 horas, 20 minutos, e 30 segundos um um fuso horário de GMT+1 (como a Itália) --&gt;
&lt;time&gt;2014-09-16&lt;/time&gt;
</pre>

## Uma semana válida

Deve ser uma _string_ representando uma semana do ano. Por exemplo:

<pre class="lang-html">&lt;!-- A 18ª semana de 2014 --&gt;
&lt;time&gt;2014-W18&lt;/time&gt;
</pre>

## Um ano válido

Deve ser uma _string_ representando um ano. Por exemplo:

<pre class="lang-html">&lt;!-- 2014 --&gt;
&lt;time datetime="2014"&gt;Esse ano&lt;/time&gt;  
</pre>

## Uma _string_ válida de duração

Deve ser uma _string_ representando uma duração. Uma duração pode começar com o prefixo _&#8220;P&#8221;_ (para _período_) e usa _&#8220;D&#8221;_ para marcar os _dias_. Por exemplo:

<pre class="lang-html">&lt;!-- Uma duração de 4 dias --&gt;
&lt;time datetime="P4D"&gt;quatro dias&lt;/time&gt;
</pre>

Em caso da necessidade de especificar melhor o período, após o _&#8220;D&#8221;_, você pode adicionar um _&#8220;T&#8221;_, que significa _tempo_, e usar _&#8220;H&#8221;_ para _horas_, _&#8220;M&#8221;_ para _minutos_ e _&#8220;S&#8221;_ para _segundos_. Assim:

<pre class="lang-html">&lt;!-- Uma duração de quatro dias, quatro horas e três minutos --&gt;
&lt;time datetime="P4DT4H3M"&gt;quatro dias&lt;/time&gt;
</pre>

Esse formato também permite a você especificar um ou mais <a href="http://www.w3.org/TR/html5/infrastructure.html#duration-time-component" target="_blank">componentes de duração de tempo</a>.

## Limitações

A especificação atual tem algumas limitações no que você pode definir com o elemento `time`. Uma dessas limitações é que você não pode indicar intervalos de datas. Então, se você estiver escrevendo um post sobre uma conferência que dura mais de um dia, por exemplo a partir de 26 de junho de 2014 a 28 de junho de 2014, você terá que usar dois elementos `time`. Um bom exemplo pode ser encontrado na <a href="http://aurelio.audero.it/speaking" target="_blank">página sobre palestras do meu website</a>, onde eu uso o elemento `time`, como mostrado abaixo:

<pre class="lang-html">&lt;time datetime="2014-06-28"&gt;26&lt;span class="hidden"&gt;de Junho de 2014&lt;/span&gt;&lt;/time&gt;-&lt;time datetime="2014-06-28"&gt;28 Junho 2014&lt;/time&gt;
</pre>

Outra limitação é que você não pode usar o elemento `time` para representar datas antes da <a href="http://en.wikipedia.org/wiki/Common_Era" target="_blank">Era Comum</a>.

## Suporte

Baseado no <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time" target="_blank">artigo no MDN</a>, o suporte do elemento `time` é:

  * Chrome 33+
  * Firefox 22+
  * Internet Explorer 9+
  * Opera 22+
  * Safari 7+

No entanto, não há muito o que se preocupar sobre navegadores antigos. Na verdade, em caso do navegador não oferecer suporte para o elemento, ele será renderizado como um elemento _inline_ desconhecido.

## Conclusão

Se você ainda não começou a usar o elemento `time` nas suas páginas, eu espero que esse guia lhe inspire a começar.

Para mais informações, aqui vão alguns links relevantes:

  * [`<time>` Element on W3C][1]
  * [`<time>` Element on WHATWG][2]
  * [`<time>` Element on MDN][3]
  * [`<time>` Element Wiki on WHATWG][4]

—

Texto traduzido e adaptado do [O HTML5 trouxe diversas coisas bacanas pra nós desenvolvedores. Uma das mais simples e que eu acho que são uma das mais legais é a questão da semântica com os novos elementos. O surgimento dessas _tags_ deixaram nossos códigos mais semânticos e legíveis, tanto por nós como pelas máquinas.

Um desses elementos é o `time`. Já havia lido sobre ele, mas nunca tinha ido muito a fundo. Esses dias encontrei um texto do <a href="https://twitter.com/AurelioDeRosa" target="_blank">Aurelio De Rosa</a> no <a href="http://www.sitepoint.com/" target="_blank">SitePoint</a> que <a href="http://www.sitepoint.com/html5-time-element-guide/" target="_blank">explica bastante coisa</a> sobre este elemento e resolvi traduzir pra gente.

&#8212;

Tempo &#8211; uma das poucas coisas que sabemos que é infinita. Os seres humanos, bem como animais e plantas, têm lidado com o tempo desde o início de sua existência.

Na web essa necessidade não é diferente. Mesmo nesse meio, precisamos nos comunicar com outras pessoas de que alguma coisa aconteceu em um determinado ponto, em uma data específica, ou em relação a um outro tempo definido.

Antes do HTML5 não tivemos nenhum elemento para marcar semanticamente uma data ou hora. Nos últimos anos, outras soluções, como os <a href="http://microformats.org/" target="_blank">Microformats</a> e <a href="http://en.wikipedia.org/wiki/Microdata_%28HTML%29" target="_blank">Microdata</a>, tentaram preencher esta lacuna para situações específicas (data de nascimento, a publicação de um livro, e assim por diante).

Nesse artigo eu irei cobrir o elemento `time` do HTML5, o que ajuda a responder à necessidade de que acabamos de discutir.

## O que é o elemento `time`?

O elemento `time` foi introduzido na especificação do HTML5 em 2009. Então, em 2011 foi trocado  em favor do `data`. Então, em seguida, o elemento foi reintroduzido e melhorado para permitir novos formatos de data/hora. A partir deste ponto você pode ver que as especificações podem ser bastante controversas.

O elemento `time` representa uma data e/ou um tempo no <a href="http://en.wikipedia.org/wiki/Gregorian_calendar" target="_blank">calendário gregoriano</a>. É um elemento inline (como `<span>` e `<a>`) e deve ter uma tag de fechamento (como `<div>` e `<span>`). Quando usado na sua forma mais simples, o conteúdo do elemento deve ser uma string <a href="http://www.w3.org/TR/html5/text-level-semantics.html#the-time-element" target="_blank">de data e/ou tempo válidas</a>.

Um exemplo abaixo:

<pre class="lang-html">&lt;!-- 1º Fevereiro 2009 --&gt;
&lt;time&gt;2009-02-01&lt;/time&gt;
</pre>

No código acima, eu estou definindo uma data, especificamente 1º de fevereiro de 2009. O formato utilizado no código (aaaa-mm-dd) deve ser familiar para você se você já mexeu algum tempo com Linux, mas, como veremos mais adiante neste artigo, este não é o único formato válido.

No primeiro esboço das especificações, datas precisas eram um dos poucos formatos que você podia escrever. Por exemplo, você não podia especificar uma data como &#8220;Novembro 2014&#8221; ou &#8220;476&#8221; (o início da Idade Média). Isso foi um grande problema para vários casos, como a datação de uma pintura ou de um acontecimento histórico pois não havia uma data precisa.

Felizmente, esse tipo de data agora é permitida na especificação. Então, hoje nós podemos descrever um determinado mês de um ano sem um dia:

<pre class="lang-html">&lt;!-- Janeiro 2014 --&gt;
&lt;time&gt;2014-01&lt;/time&gt;
</pre>

## O atributo `datetime`

A especificação para o elemento também padronizou um atributo chamado de `datetime`.

Ao escrevermos datas como nos formatos discutidos na seção anterior, pode funciona em alguns países/culturas, como pode não atender outros. Por exemplo, os italianos (e nós brasileiros) escrevem datas usando o formato _dd/mm/aaaa_. Portanto, mostrar uma data em outro formato pode gerar confusão.

Este problema pode ser facilmente resolvido usando o atributo `datetime` do elemento `time`. É um atributo opcional que contém as informações em um formato legível por uma máquina, como os observados nos exemplos anteriores, o que nos permite que possamos escrever o conteúdo do elemento da qualquer maneira que nós quisermos.

Na verdade, se o atributo `datetime` não for especificado, o conteúdo deve estar em um dos formatos de data/hora válidos, caso contrário, podemos usá-lo como quisermos. Isso é ótimo porque nos permite escrever um código assim:

<pre class="lang-html">A próxima reunião está agendada para &lt;time datetime="2014-10"&gt;Outubro&lt;/time&gt;.
</pre>

Ou assim:

<pre class="lang-html">A próxima reunião está agendada para o &lt;time datetime="2014-10"&gt;próximo mês&lt;/time&gt;.
</pre>

Ambos exemplos possuem um conteúdo de data que não é legível por uma máquina de acordo com a especificação, mas são aceitáveis​​, por causa da presença do atributo `datetime`, que _faz uso_ de um formato válido.

À primeira vista, isso pode parecer estranho. Mas o conteúdo do elemento foi concebido para servir os seres humanos, não máquinas. Além disso, esse fato permite a internacionalização das datas. Por exemplo:

<pre class="lang-html">&lt;!-- Mesma mensagem anterior, só que em italiano --&gt;
Il prossimo incontro è programmato per &lt;time datetime="2014-10"&gt;il mese prossimo&lt;/time&gt;.
</pre>

No código acima temos a mesma mensagem anterior, só que em Italiano.

## O atributo `pubdate`

Os primeiros rascunhos da especificação definiam um atributo `pubdate` para o elemento `time`. Este atributo era um _booleano_ que indicava que uma determinada data era a data de publicação do elemento pai `article` ou, em caso de ausência de elemento `article` pai, de todo o documento.

Você poderia escrever por exemplo:

<pre class="lang-html">&lt;article&gt;
    &lt;h1&gt;Um título&lt;/h1&gt;
    &lt;p&gt;Esse é o conteúdo do article.&lt;/p&gt;
    &lt;footer&gt;
        &lt;p&gt;Artigo publicado em &lt;time datetime="2014-09-05" pubdate&gt;05 de setembro de 2014&lt;/time&gt;
    &lt;/footer&gt;
&lt;/article&gt;
</pre>

Nesse caso, 05 de setembro de 2014 seria a data de publicação desse `article`.

Eu fui um grande fã deste atributo desde que aprendi bastante sobre isso, mas, infelizmente, ele foi removido da especificação. Essa decisão criou um grande problema, porque um grande número de pessoas (inclusive eu) usam a data de publicação para julgar o frescor e a relevância de um artigo ou notícia. Embora seja verdade que você ainda possa acessar a página de um artigo e ver a data de publicação, precisamos de uma forma padrão para uma máquina de ler a data.

No atual momento não existe um atributo que substitua `pubdate`, mas você pode empregar o <a href="http://schema.org/BlogPosting" target="_blank">BlogPosting schema</a>, e especificamente o valor `datePublished` como mostrado abaixo:

<pre class="lang-html">&lt;article itemscope itemType="http://schema.org/BlogPosting"&gt;
        &lt;h1 itemprop="headline"&gt;Um título&lt;/h1&gt;
        &lt;p itemprop="articleBody"&gt;Conteúdo do article.&lt;/p&gt;
 
        &lt;footer&gt;
            &lt;p&gt;Artigo publicado em &lt;time datetime="2014-09-05" itemprop="datePublished"&gt;05 de setembro de 2014&lt;/time&gt;
        &lt;/footer&gt;
&lt;/article&gt;
</pre>

Agora que você tem um _overview_ completo do elemento `time`, vamos ver os diversos formatos permitidos.

Os formatos validos para o conteúdo do elemento `time` na ausência do atributo `datetime` e para esse atributo em si são descritos nos itens seguintes.

## Um mês válido

Deve ser uma _string_ especificando um mês específico de um ano no formato **aaaa-mm**. Por exemplo:

<pre class="lang-html">&lt;!-- Setembro 2014 --&gt;
&lt;time&gt;2014-09&lt;/time&gt;  
</pre>

## Uma data válida (dia do mês)

Deve ser uma _string_ especificando uma data precisa no formato **aaaa-mm-dd**.

Por exemplo:

<pre class="lang-html">&lt;!-- 16 de setembro de 2014 --&gt;
&lt;time&gt;2014-09-16&lt;/time&gt;
</pre>

## Uma data válida sem ano

Deve ser uma _string_ especificando um mês e um dia sem um ano no formato **mm-dd**.

Por exemplo:

<pre class="lang-html">&lt;!-- 29 de Junho --&gt;
&lt;time&gt;06-29&lt;/time&gt;
</pre>

## Um tempo válido

Deve ser uma _string_ especificando um tempo sem uma data e usando o formato 24 horas, da seguinte maneira **HH:MM[:SS[.mm]]** onde:

  * **H** são horas
  * **M** são minutos
  * **S** são segundos
  * **m** são milisegundos
  * Os _brackets_ indicam partes que são opcionais.

Um exemplo desse formato mostrado abaixo:

<pre class="lang-html">&lt;!-- 16 horas e 10 minutos (ou 4 horas e 10 minutos pm) --&gt;
&lt;time datetime="16:10"&gt;afternoon&lt;/time&gt;
</pre>

## Uma data e hora _flutuante_ válida

Esse formato é apresentado na especificação do W3C, mas não na versão WHATWG. Deve ser uma data e um tempo precisos no formato **aaaa-mm-ddTHH:MM[:SS[.mm]]** ou **aaaa-mm-dd HH:MM[:SS[.mmm]]**. Por exemplo:

<pre class="lang-html">&lt;!-- 16 de Setembro de 2014 às 18 horas, 20 minutos, e 30 segundos --&gt;
&lt;time datetime="2014-09-16T18:20:30"&gt;Terça-feira às 18:20&lt;/time&gt;
</pre>

## Um fuso horário válido

Deve ser uma _string_ representando um fuso horário. Por exemplo:

<pre class="lang-html">&lt;!-- GMT+1 (Itália) --&gt;
&lt;time&gt;+01:00&lt;/time&gt;
</pre>

## Uma data e tempo global válidos

Deve ser uma _string_ representando uma data completa, incluindo tempo e fuso horário. Por exemplo:

<pre class="lang-html">&lt;!-- 16 de Setembro de 2014 às 18 horas, 20 minutos, e 30 segundos um um fuso horário de GMT+1 (como a Itália) --&gt;
&lt;time&gt;2014-09-16&lt;/time&gt;
</pre>

## Uma semana válida

Deve ser uma _string_ representando uma semana do ano. Por exemplo:

<pre class="lang-html">&lt;!-- A 18ª semana de 2014 --&gt;
&lt;time&gt;2014-W18&lt;/time&gt;
</pre>

## Um ano válido

Deve ser uma _string_ representando um ano. Por exemplo:

<pre class="lang-html">&lt;!-- 2014 --&gt;
&lt;time datetime="2014"&gt;Esse ano&lt;/time&gt;  
</pre>

## Uma _string_ válida de duração

Deve ser uma _string_ representando uma duração. Uma duração pode começar com o prefixo _&#8220;P&#8221;_ (para _período_) e usa _&#8220;D&#8221;_ para marcar os _dias_. Por exemplo:

<pre class="lang-html">&lt;!-- Uma duração de 4 dias --&gt;
&lt;time datetime="P4D"&gt;quatro dias&lt;/time&gt;
</pre>

Em caso da necessidade de especificar melhor o período, após o _&#8220;D&#8221;_, você pode adicionar um _&#8220;T&#8221;_, que significa _tempo_, e usar _&#8220;H&#8221;_ para _horas_, _&#8220;M&#8221;_ para _minutos_ e _&#8220;S&#8221;_ para _segundos_. Assim:

<pre class="lang-html">&lt;!-- Uma duração de quatro dias, quatro horas e três minutos --&gt;
&lt;time datetime="P4DT4H3M"&gt;quatro dias&lt;/time&gt;
</pre>

Esse formato também permite a você especificar um ou mais <a href="http://www.w3.org/TR/html5/infrastructure.html#duration-time-component" target="_blank">componentes de duração de tempo</a>.

## Limitações

A especificação atual tem algumas limitações no que você pode definir com o elemento `time`. Uma dessas limitações é que você não pode indicar intervalos de datas. Então, se você estiver escrevendo um post sobre uma conferência que dura mais de um dia, por exemplo a partir de 26 de junho de 2014 a 28 de junho de 2014, você terá que usar dois elementos `time`. Um bom exemplo pode ser encontrado na <a href="http://aurelio.audero.it/speaking" target="_blank">página sobre palestras do meu website</a>, onde eu uso o elemento `time`, como mostrado abaixo:

<pre class="lang-html">&lt;time datetime="2014-06-28"&gt;26&lt;span class="hidden"&gt;de Junho de 2014&lt;/span&gt;&lt;/time&gt;-&lt;time datetime="2014-06-28"&gt;28 Junho 2014&lt;/time&gt;
</pre>

Outra limitação é que você não pode usar o elemento `time` para representar datas antes da <a href="http://en.wikipedia.org/wiki/Common_Era" target="_blank">Era Comum</a>.

## Suporte

Baseado no <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time" target="_blank">artigo no MDN</a>, o suporte do elemento `time` é:

  * Chrome 33+
  * Firefox 22+
  * Internet Explorer 9+
  * Opera 22+
  * Safari 7+

No entanto, não há muito o que se preocupar sobre navegadores antigos. Na verdade, em caso do navegador não oferecer suporte para o elemento, ele será renderizado como um elemento _inline_ desconhecido.

## Conclusão

Se você ainda não começou a usar o elemento `time` nas suas páginas, eu espero que esse guia lhe inspire a começar.

Para mais informações, aqui vão alguns links relevantes:

  * [`<time>` Element on W3C][1]
  * [`<time>` Element on WHATWG][2]
  * [`<time>` Element on MDN][3]
  * [`<time>` Element Wiki on WHATWG][4]

—

Texto traduzido e adaptado do][5] escrito pelo [Aurelio De Rosa][6] em 16 de setembro de 2014.

Tradução autorizada pelo [SitePoint][7].

Qualquer erro ou sugestão de melhoria na tradução, é bem vinda! <img class="wp-smiley" src="http://tableless.com.br/wp-includes/images/smilies/icon_smile.gif" alt=":)" />

 [1]: http://www.w3.org/html/wg/drafts/html/master/text-level-semantics.html#the-time-element
 [2]: https://html.spec.whatwg.org/multipage/semantics.html#the-time-element
 [3]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time
 [4]: https://wiki.whatwg.org/wiki/Time_element
 [5]: http://www.sitepoint.com/html5-time-element-guide/
 [6]: https://twitter.com/AurelioDeRosa "Perfil do twitter"
 [7]: http://www.sitepoint.com/