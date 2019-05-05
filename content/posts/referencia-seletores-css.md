---
title: Tabela de Referência de Seletores de CSS
authors: Diego Eis
type: post
image: https://imgur.com/1kk8yVW.png
date: 2019-05-05
excerpt: Tabela de referência para seletores de CSS
categories:
- CSS
tags:
- referencia
- css
---

Essa é uma tabela de referência sobre os diferentes tipos de Seletores de CSS. Para facilitar seus testes, use o [CSS Selector Test do W3Schools](https://www.w3schools.com/cssref/trysel.asp).

<table>
  <thead>
    <tr>
      <th style="width:20%">Seletor</th>
      <th style="width:20%">Exemplo</th>
      <th>Descrição</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>.class</td>
    <td>.intro</td>
    <td>Seleciona todos os elementos com class="intro"</td>
  </tr>
  <tr>
    <td>#id</td>
    <td>#firstname</td>
    <td>Seleciona o elemento com id="firstname"</td>
  </tr>  
  <tr>
    <td>*</td>
    <td>*</td>
    <td>Seleciona todos os elementos</td>
  </tr>
  <tr>
    <td>elemento</td>
    <td>p</td>
    <td>Seleciona todos &lt;p&gt;</td>
  </tr>
  <tr>
    <td>elemento, elemento</td>
    <td>div, p</td>
    <td>Seleciona todos &lt;div&gt; e todos elementos &lt;p&gt;</td>
  </tr>
  <tr>
    <td>elemento elemento</td>
    <td>div p</td>
    <td>Seleciona todos elementos &lt;p&gt; dentro de elementos &lt;div&gt; </td>
  </tr>
  <tr>
    <td>elemento &gt; elemento</td>
    <td>div &gt; p</td>
    <td>Seleciona todos &lt;p&gt; onde o pai é um elemento &lt;div&gt;</td>
  </tr>
  <tr>
    <td>elemento+elemento</td>
    <td>div + p</td>
    <td>Seleciona todos &lt;p&gt; que estão imediatamente depois de um elemento &lt;div&gt;</td>
  </tr>
  <tr>
    <td>elemento1 ~ elemento2</td>
    <td>p ~ ul</td>
    <td>Seleciona todo elemento &lt;ul&gt; que precede um elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td>[attribute]</td>
    <td>[target]</td>
    <td>Seleciona todos os elementos com um atributo target</td>
  </tr>
  <tr>
    <td>[attribute=value]</td>
    <td>[target=_blank]</td>
    <td>Seleciona todos os elementos com target="_blank"</td>
  </tr>
  <tr>
    <td>[attribute~=value]</td>
    <td>[title~=flower]</td>
    <td>Seleciona todos os elementos com um atributo title contendo a palavra "flower"</td>
  </tr>
  <tr>
    <td>[attribute|=value]</td>
    <td>[lang|=pt-br]</td>
    <td>Seleciona todos os elementos com um atributo lang, cujo o atributo valor comece com "pt-br"</td>
  </tr>
  <tr>
    <td>[attribute^=value]</td>
    <td>a[href^="https"]</td>
    <td>Seleciona todo elemento &lt;a&gt; que tem um atributo href com o valor começando com "https"</td>
  </tr>
  <tr>
    <td>[attribute$=value]</td>
    <td>a[href$=".pdf"]</td>
    <td>Seleciona todo elemento &lt;a&gt; que tem um atributo href com o valor termina com ".pdf"</td>
  </tr>
  <tr>
    <td>[attribute*=value]</td>
    <td>a[href*="tableless"]</td>
    <td>Seleciona todo elemento &lt;a&gt; que tem um atributo href com o valor contém "tableless"</td>
  </tr>
  <tr>
    <td>:active</td>
    <td>a:active</td>
    <td>Seleciona o link ativo</td>
  </tr>
  <tr>
    <td>::after</td>
    <td>p::after</td>
    <td>Insere conteúdo depois de cada elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td>::before</td>
    <td>p::before</td>
    <td>Insere conteúdo antes de cada elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td>:checked</td>
    <td>input:checked</td>
    <td>Seleciona todo elemento &lt;input&gt; checked </td>
  </tr>
  <tr>
    <td>:default</td>
    <td>input:default</td>
    <td>Seleciona os &lt;input&gt; padrão</td>
  </tr>
  <tr>
    <td>:disabled</td>
    <td>input:disabled</td>
    <td>Seleciona todo &lt;input&gt; desabilitado</td>
  </tr>
  <tr>
    <td>:empty</td>
    <td>p:empty</td>
    <td>Seleciona todo elemento &lt;p&gt; que não tem filhos, incluindo texto</td>
  </tr>
  <tr>
    <td>:enabled</td>
    <td>input:enabled</td>
    <td>Seleciona todo &lt;input&gt; habilitado</td>
  </tr>
  <tr>
    <td>:first-child</td>
    <td>p:first-child</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o primeiro filho do seu pai</td>
  </tr>
  <tr>
    <td>::first-letter</td>
    <td>p::first-letter</td>
    <td>Seleciona a primeira letra de todo elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td>::first-line</td>
    <td>p::first-line</td>
    <td>Seleciona a primeira linha de todo elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td>ype.asp">:first-of-type</td>
    <td>p:first-of-type</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o primeiro filho do seu pai</td>
  </tr>
  <tr>
    <td>:focus</td>
    <td>input:focus</td>
    <td>Seleciona o &lt;input&gt; que tem focus</td>
  </tr>
  <tr>
    <td>:hover</td>
    <td>a:hover</td>
    <td>Seleciona links quando o mouse passa por cima</td>
  </tr>
  <tr>
    <td>sp">:in-range</td>
    <td>input:in-range</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo value dentro de um range especificado</td>
  </tr>
  <tr>
    <td>:indeterminate</td>
    <td>input:indeterminate</td>
    <td>Seleciona o elemento &lt;input&gt; tem um estado indeterminado</td>
  </tr>
  <tr>
    <td>:invalid</td>
    <td>input:invalid</td>
    <td>Seleciona todos &lt;input&gt; elementos com um valor inválido</td>
  </tr>
  <tr>
    <td>:lang(language)</td>
    <td>p:lang(pt-br)</td>
    <td>Seleciona todo elemento &lt;p&gt; com a atributo lang igual a "pt-br"</td>
  </tr>
  <tr>
    <td>sp">:last-child</td>
    <td>p:last-child</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o último filho de seu pai</td>
  </tr>
  <tr>
    <td>ype.asp">:last-of-type</td>
    <td>p:last-of-type</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o último elemento do tipo &lt;p&gt; do seu pai</td>
  </tr>
  <tr>
    <td>:link</td>
    <td>a:link</td>
    <td>Seleciona todos  links não visitados</td>
  </tr>
  <tr>
    <td>:not(Seletor)</td>
    <td>:not(p)</td>
    <td>Seleciona todo elemento elemento que não é um elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td>sp">:nth-child(n)</td>
    <td>p:nth-child(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo filho do seu pai</td>
  </tr>
  <tr>
    <td>hild.asp">:nth-last-child(n)</td>
    <td>p:nth-last-child(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo filho do seu pai, contando com o último filho</td>
  </tr>
  <tr>
    <td>f-type.asp">:nth-last-of-type(n)</td>
    <td>p:nth-last-of-type(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo &lt;p&gt; of its parent, contando com o último filho</td>
  </tr>
  <tr>
    <td>ype.asp">:nth-of-type(n)</td>
    <td>p:nth-of-type(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo &lt;p&gt; do seu pai</td>
  </tr>
  <tr>
    <td>ype.asp">:only-of-type</td>
    <td>p:only-of-type</td>
    <td>Seleciona todo elemento &lt;p&gt; that is the only &lt;p&gt; do seu pai</td>
  </tr>
  <tr>
    <td>sp">:only-child</td>
    <td>p:only-child</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o único filho do seu pai</td>
  </tr>
  <tr>
    <td>:optional</td>
    <td>input:optional</td>
    <td>Seleciona o elemento &lt;input&gt; com sem o atributo "required"</td>
  </tr>
  <tr>
    <td>ange.asp">:out-of-range</td>
    <td>input:out-of-range</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo value fora do range especificado</td>
  </tr>
  <tr>
    <td>::placeholder</td>
    <td>input::placeholder</td>
    <td>Seleciona o elemento &lt;input&gt; com texto placeholder </td>
  </tr>
  <tr>
    <td>sp">:read-only</td>
    <td>input:read-only</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo "readonly" especificado</td>
  </tr>
  <tr>
    <td>sp">:read-write</td>
    <td>input:read-write</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo "readonly" não especificado</td>
  </tr>
  <tr>
    <td>:required</td>
    <td>input:required</td>
    <td>Seleciona o elemento &lt;input&gt; com the "required" atributo especificado</td>
  </tr>
  <tr>
    <td>:root</td>
    <td>:root</td>
    <td>Seleciona o elemento root</td>
  </tr>
  <tr>
    <td>::selection</td>
    <td>::selection</td>
    <td>Seleciona a porção de um elemento que está selecionado pelo usuário</td>
  </tr>
  <tr>
    <td>:target</td>
    <td>#news:target </td>
    <td>Seleciona o elemento atual ativo #news (clicado pelo usuário na URL contendo o nome ancora)</td>
  </tr>
  <tr>
    <td>:valid</td>
    <td>input:valid</td>
    <td>Seleciona todos &lt;input&gt; elementos com um valor válido</td>
  </tr>
  <tr>
    <td>:visited</td>
    <td>a:visited</td>
    <td>Seleciona todos links já visitados</td>
  </tr>
</tbody></table>