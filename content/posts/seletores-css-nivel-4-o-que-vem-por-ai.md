---
title: Seletores CSS Nível 4 – O que vem por aí
author: Diego Eis
type: post
date: 2015-01-12
excerpt: Saiba quais os seletores que irão salvar sua vida muito em breve.
url: /seletores-css-nivel-4-o-que-vem-por-ai/
categories:
  - CSS
  - HTML
tags:
  - CSS
  - CSS3
  - selectors
  - seletores

---
Os seletores do CSS são a coisa mais importante da linguagem. As propriedades você consegue decorar e aprender de acordo com necessidade. Mas os seletores são a sua ferramenta de trabalho. A falta de um seletor adequado é determinante quando você decide fazer aquela gambiarra nojenta para conseguir formatar um elemento específico. Com seletores mais inteligentes, você também previne a chuva de classes que tem sido comum em projetos alheios. Por isso é importante que você conheça os novos seletores de nível 4 do CSS. Eles trazem uma série de novidades importantes para resolver aqueles problema recorrentes principalmente em projetos complexos. Abaixo, veja alguns exemplos.

Para os mais puristas: quase nenhum destes seletores podem ser usados. A maioria apenas com a ajuda de prefixos e outros com a nomenclatura diferente da do padrão estabelecido. Por isso, não fique esperando que tudo isso poderá ser usado agora. Este é apenas um vislumbre do que você terá como ferramenta nos próximos anos (ou meses?).

## :matcher

É uma pseudo-classe que seleciona como argumento uma lista de elementos. Nesse caso, não é possível fazer um seletor com combinadores. Muito útil, veja o exemplo abaixo:

<pre class="lang-css">section h1, header h1, article h1 {
  color: blue;
}
</pre>

Seria o mesmo que escrever:

<pre class="lang-css">:matches(section, header, article) h1 {
  color: blue;
}
</pre>

Para você testar aí no Firefox ou no WebKit, note que eles estão usando um seletor prefixado chamado **any**. É usado assim: **-moz-any()** e **-webkit-any()**. Alguma hora eles irão mudar para o nome definido pelo W3C.

<pre class="lang-css">:-moz-any(section, article, header) h1,
:-webkit-any(section, article, header) h1 {
  color: red;
}
</pre>

## :not

O **:not** foi apresentado no nível 3 do CSS, mas na versão 4 ele ganha um novo improvement, sendo utilizado assim:

<pre class="lang-css">p:not(.active, .visible) {
   color: red;
}
</pre>

Esse código seleciona todos os parágrafos que não tem a classe ACTIVE ou VISIBLE aplicadas.

## :any-link

Esse é uma pequena adição, mas que ajuda bastante. Veja o exemplo abaixo:

<pre class="lang-css">a:link,
a:visited,
a:actived {
  color: green;
}
</pre>

É substituído por:

<pre class="lang-css">a:any-link {
  color: green;
}
</pre>

## Case-sensitivity

Atributos e Valores geralmente são minúsculos, mas alguns linguagens ou devs desavisados podem colocar letras maiúsculas nos valores dos atributos do HTML. Isto se torna um problema quando fazemos a seleção dos elementos via atributo e valor, como no exemplo abaixo:

<pre class="lang-css">a[href$="PDF"] {
  color: green;
}
</pre>

Para prevenir isso, basta adicionar uma flag **i** ainda dentro dos colchetes para que o browser ignore o case-sensitivity dos valores:

<pre class="lang-css">a[href$="pdf" i] {
  color: green;
}
</pre>

## :dir()

Seleciona elementos com uma direção de leitura específica. Veja o exemplo abaixo:

<pre class="lang-css">// Parágrafos com direção de leitura da esquerda para direita
p:dir(ltr) {
  color: green;
}

// Parágrafos com direção de leitura da direita para esquerda
p:dir(rtl) {
  color: red;
}
</pre>

## :read-only e :read-write

Outra adição bastante simples. Com essas pseudo-classes nós podemos selecionar e formatar os elementos que são read-only ou read-write na página. Geralmente todos os elementos são apenas read-only. Você não interage ou muda um parágrafo, por exemplo. Você vê um exemplo bastante simples pelos formulários:

<pre class="lang-css">input:-moz-read-only {
  border: 1px solid red;
}

input:-moz-read-write {
  border: 1px solid blue;
}
</pre>

## Subject Seletor

Agora você tem a possibilidade de inverter a ordem do seletor. Calma, eu explico: o seletor é lido sempre da direita para a esquerda. Mas agora você pode inverter essa ordem usando a flag **!** no começo do seletor. Assim:

<pre class="lang-css">!ul > li {
  border: 1px solid blue;
}
</pre>

No caso acima, a **UL** ficará com a borda. Bem interessante! Coisa lindíssima.

## Entre outros

Existem uma [listagem completa na documentação do W3C][1] que mostra não apenas os seletores de nível 4, mas também os seletores que entraram nas versões anteriores. Vale a pena dar uma lida na documentação.

[Neste link][2] você encontra uma listagem com exemplos de sintaxe 

Alguns seletores eu queria muito ver funcionando, como é o caso das time-pseudos [:current, :past e :future][3].

 [1]: http://dev.w3.org/csswg/selectors-4/#overview
 [2]: http://css4-selectors.com/selectors/
 [3]: http://dev.w3.org/csswg/selectors-4/#time-pseudos