---
title: Seletores de CSS - Guia de Referência
authors: Diego Eis
type: post
image: https://imgur.com/1kk8yVW.png
date: 2019-05-05
excerpt: Referência atualizada de seletores de CSS
categories:
- CSS
tags:
- referencia
- css
---

Essa é uma tabela de referência sobre os diferentes tipos de Seletores de CSS. Para facilitar seus testes, use o [CSS Selector Test do W3Schools](https://www.w3schools.com/cssref/trysel.asp).

<table>
  <tbody><tr>
    <th style="width:20%">Seletor</th>
    <th style="width:20%">Exemplo</th>
    <th>Descrição</th>
  </tr>
  <tr>
    <td><a href="sel_class.asp">.<i>class</i></a></td>
    <td class="notranslate">.intro</td>
    <td>Seleciona todos os elementos com class="intro"</td>
  </tr>
  <tr>
    <td><a href="sel_id.asp">#<i>id</i></a></td>
    <td class="notranslate">#firstname</td>
    <td>Seleciona o elemento com id="firstname"</td>
  </tr>  <tr>
    <td><a href="sel_all.asp">*</a></td>
    <td class="notranslate">*</td>
    <td>Seleciona todos os elementos</td>
  </tr>
  <tr>
    <td><i><a href="sel_elemento.asp">elemento</a></i></td>
    <td class="notranslate">p</td>
    <td>Seleciona todos &lt;p&gt;</td>
  </tr>
  <tr>
    <td><i><a href="sel_elemento_comma.asp">elemento,elemento</a></i></td>
    <td class="notranslate">div, p</td>
    <td>Seleciona todos &lt;div&gt; e todos elementos &lt;p&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_elemento_elemento.asp"><i>elemento</i> <i>elemento</i></a></td>
    <td class="notranslate">div p</td>
    <td>Seleciona todos elementos &lt;p&gt; dentro de elementos &lt;div&gt; </td>
  </tr>
  <tr>
    <td><a href="sel_elemento_gt.asp"><i>elemento</i>&gt;<i>elemento</i></a></td>
    <td class="notranslate">div &gt; p</td>
    <td>Seleciona todos &lt;p&gt; onde o pai é um elemento &lt;div&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_elemento_pluss.asp"><i>elemento</i>+<i>elemento</i></a></td>
    <td class="notranslate">div + p</td>
    <td>Seleciona todos &lt;p&gt; que estão imediatamente depois de um elemento &lt;div&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_gen_sibling.asp"><i>elemento1</i>~<i>elemento2</i></a></td>
    <td>p ~ ul</td>
    <td>Seleciona todo elemento &lt;ul&gt; que precede um elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_attribute.asp">[<i>attribute</i>]</a></td>
    <td class="notranslate">[target]</td>
    <td>Seleciona todos os elementos com um atributo target</td>
  </tr>
  <tr>
    <td><a href="sel_attribute_value.asp">[<i>attribute</i>=<i>value</i>]</a></td>
    <td class="notranslate">[target=_blank]</td>
    <td>Seleciona todos os elementos com target="_blank"</td>
  </tr>
  <tr>
    <td><a href="sel_attribute_value_contains.asp">[<i>attribute</i>~=<i>value</i>]</a></td>
    <td class="notranslate">[title~=flower]</td>
    <td>Seleciona todos os elementos com um atributo title contendo a palavra "flower"</td>
  </tr>
  <tr>
    <td><a href="sel_attribute_value_lang.asp">[<i>attribute</i>|=<i>value</i>]</a></td>
    <td class="notranslate">[lang|=pt-br]</td>
    <td>Seleciona todos os elementos com um atributo lang, cujo o atributo valor comece com "pt-br"</td>
  </tr>
  <tr>
    <td><a href="sel_attr_begin.asp">[<i>attribute</i>^=<i>value</i>]</a></td>
    <td>a[href^="https"]</td>
    <td>Seleciona todo elemento &lt;a&gt; que tem um atributo href com o valor começando com "https"</td>
  </tr>
  <tr>
    <td><a href="sel_attr_end.asp">[<i>attribute</i>$=<i>value</i>]</a></td>
    <td>a[href$=".pdf"]</td>
    <td>Seleciona todo elemento &lt;a&gt; que tem um atributo href com o valor termina com ".pdf"</td>
  </tr>
  <tr>
    <td><a href="sel_attr_contain.asp">[<i>attribute</i>*=<i>value</i>]</a></td>
    <td>a[href*="tableless"]</td>
    <td>Seleciona todo elemento &lt;a&gt; que tem um atributo href com o valor contém "tableless"</td>
  </tr>
  <tr>
    <td><a href="sel_active.asp">:active</a></td>
    <td class="notranslate">a:active</td>
    <td>Seleciona o link ativo</td>
  </tr>
  <tr>
    <td><a href="sel_after.asp">::after</a></td>
    <td class="notranslate">p::after</td>
    <td>Insere conteúdo depois de cada elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_before.asp">::before</a></td>
    <td class="notranslate">p::before</td>
    <td>Insere conteúdo antes de cada elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_checked.asp">:checked</a></td>
    <td>input:checked</td>
    <td>Seleciona todo elemento &lt;input&gt; checked </td>
  </tr>
  <tr>
    <td><a href="sel_default.asp">:default</a></td>
    <td>input:default</td>
    <td>Seleciona os &lt;input&gt; padrão</td>
  </tr>
  <tr>
    <td><a href="sel_disabled.asp">:disabled</a></td>
    <td>input:disabled</td>
    <td>Seleciona todo &lt;input&gt; desabilitado</td>
  </tr>
  <tr>
    <td><a href="sel_empty.asp">:empty</a></td>
    <td>p:empty</td>
    <td>Seleciona todo elemento &lt;p&gt; que não tem filhos, incluindo texto</td>
  </tr>
  <tr>
    <td><a href="sel_enabled.asp">:enabled</a></td>
    <td>input:enabled</td>
    <td>Seleciona todo &lt;input&gt; habilitado</td>
  </tr>
  <tr>
    <td><a href="sel_firstchild.asp">:first-child</a></td>
    <td class="notranslate">p:first-child</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o primeiro filho do seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_firstletter.asp">::first-letter</a></td>
    <td class="notranslate">p::first-letter</td>
    <td>Seleciona a primeira letra de todo elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_firstline.asp">::first-line</a></td>
    <td class="notranslate">p::first-line</td>
    <td>Seleciona a primeira linha de todo elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_first-of-type.asp">:first-of-type</a></td>
    <td>p:first-of-type</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o primeiro filho do seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_focus.asp">:focus</a></td>
    <td class="notranslate">input:focus</td>
    <td>Seleciona o &lt;input&gt; que tem focus</td>
  </tr>
  <tr>
    <td><a href="sel_hover.asp">:hover</a></td>
    <td class="notranslate">a:hover</td>
    <td>Seleciona links quando o mouse passa por cima</td>
  </tr>
  <tr>
    <td><a href="sel_in-range.asp">:in-range</a></td>
    <td class="notranslate">input:in-range</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo value dentro de um range especificado</td>
  </tr>
  <tr>
    <td><a href="sel_indeterminate.asp">:indeterminate</a></td>
    <td class="notranslate">input:indeterminate</td>
    <td>Seleciona o elemento &lt;input&gt; tem um estado indeterminado</td>
  </tr>
  <tr>
    <td><a href="sel_invalid.asp">:invalid</a></td>
    <td class="notranslate">input:invalid</td>
    <td>Seleciona todos &lt;input&gt; elementos com um valor inválido</td>
  </tr>
  <tr>
    <td><a href="sel_lang.asp">:lang(<i>language</i>)</a></td>
    <td class="notranslate">p:lang(pt-br)</td>
    <td>Seleciona todo elemento &lt;p&gt; com a atributo lang igual a "pt-br"</td>
  </tr>
  <tr>
    <td><a href="sel_last-child.asp">:last-child</a></td>
    <td>p:last-child</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o último filho de seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_last-of-type.asp">:last-of-type</a></td>
    <td>p:last-of-type</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o último elemento do tipo &lt;p&gt; do seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_link.asp">:link</a></td>
    <td class="notranslate">a:link</td>
    <td>Seleciona todos  links não visitados</td>
  </tr>
  <tr>
    <td><a href="sel_not.asp">:not(<i>Seletor</i>)</a></td>
    <td>:not(p)</td>
    <td>Seleciona todo elemento elemento que não é um elemento &lt;p&gt;</td>
  </tr>
  <tr>
    <td><a href="sel_nth-child.asp">:nth-child(<i>n</i>)</a></td>
    <td>p:nth-child(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo filho do seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_nth-last-child.asp">:nth-last-child(<i>n</i>)</a></td>
    <td>p:nth-last-child(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo filho do seu pai, contando com o último filho</td>
  </tr>
  <tr>
    <td><a href="sel_nth-last-of-type.asp">:nth-last-of-type(<i>n</i>)</a></td>
    <td>p:nth-last-of-type(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo &lt;p&gt; of its parent, contando com o último filho</td>
  </tr>
  <tr>
    <td><a href="sel_nth-of-type.asp">:nth-of-type(<i>n</i>)</a></td>
    <td>p:nth-of-type(2)</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o segundo &lt;p&gt; do seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_only-of-type.asp">:only-of-type</a></td>
    <td>p:only-of-type</td>
    <td>Seleciona todo elemento &lt;p&gt; that is the only &lt;p&gt; do seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_only-child.asp">:only-child</a></td>
    <td>p:only-child</td>
    <td>Seleciona todo elemento &lt;p&gt; que é o único filho do seu pai</td>
  </tr>
  <tr>
    <td><a href="sel_optional.asp">:optional</a></td>
    <td class="notranslate">input:optional</td>
    <td>Seleciona o elemento &lt;input&gt; com sem o atributo "required"</td>
  </tr>
  <tr>
    <td><a href="sel_out-of-range.asp">:out-of-range</a></td>
    <td class="notranslate">input:out-of-range</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo value fora do range especificado</td>
  </tr>
  <tr>
    <td><a href="sel_placeholder.asp">::placeholder</a></td>
    <td class="notranslate">input::placeholder</td>
    <td>Seleciona o elemento &lt;input&gt; com texto placeholder </td>
  </tr>
  <tr>
    <td><a href="sel_read-only.asp">:read-only</a></td>
    <td class="notranslate">input:read-only</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo "readonly" especificado</td>
  </tr>
  <tr>
    <td><a href="sel_read-write.asp">:read-write</a></td>
    <td class="notranslate">input:read-write</td>
    <td>Seleciona o elemento &lt;input&gt; com o atributo "readonly" não especificado</td>
  </tr>
  <tr>
    <td><a href="sel_required.asp">:required</a></td>
    <td class="notranslate">input:required</td>
    <td>Seleciona o elemento &lt;input&gt; com the "required" atributo especificado</td>
  </tr>
  <tr>
    <td><a href="sel_root.asp">:root</a></td>
    <td>:root</td>
    <td>Seleciona o elemento root</td>
  </tr>
  <tr>
    <td><a href="sel_selection.asp">::selection</a></td>
    <td>::selection</td>
    <td>Seleciona a porção de um elemento que está selecionado pelo usuário</td>
  </tr>
  <tr>
    <td><a href="sel_target.asp">:target</a></td>
    <td>#news:target </td>
    <td>Seleciona o elemento atual ativo #news (clicado pelo usuário na URL contendo o nome ancora)</td>
  </tr>
  <tr>
    <td><a href="sel_valid.asp">:valid</a></td>
    <td class="notranslate">input:valid</td>
    <td>Seleciona todos &lt;input&gt; elementos com um valor válido</td>
  </tr>
  <tr>
    <td><a href="sel_visited.asp">:visited</a></td>
    <td class="notranslate">a:visited</td>
    <td>Seleciona todos links já visitados</td>
  </tr>
</tbody></table>