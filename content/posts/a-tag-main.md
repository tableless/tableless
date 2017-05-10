---
title: A tag MAIN
author: Diego Eis
type: post
date: 2013-01-14
excerpt: Conheça a nova tag MAIN do HTML.
url: /a-tag-main/
dsq_thread_id: 1025167062
categories:
  - Código
  - HTML
  - HTML5
tags:
  - 2013
  - html5
  - tags

---
E finalmente, depois muita discussão, a nova tag **<main>** do HTML foi lançada. A discussão envolvia o real motivo de ter ou não uma nova tag para definir o conteúdo principal do documento. O [Ian Hickson][1] &#8211; mestre dos mestres do HTML &#8211; era contra essa nova tag. Aqui [tem uma entrevista com ele][2], muito interessante, onde há uma parte que ele explica o motivo de não querer essa nova tag. 

A tag **MAIN** tem uma única função semântica: definir o conteúdo principal da página ou da aplicação. Ele representa o conteúdo mais importante da página, que está diretamente relacionado ao tópico central do documento ou a funcionalidade principal de uma aplicação.

> The main element represents the main content section of the body of a document or application. The main content section consists of content that is directly related to or expands upon the central topic of a document or central functionality of an application.

Por exemplo:

<pre class="lang-html">&lt;main&gt;

  &lt;h1&gt;Skateboards&lt;/h1&gt;
  &lt;p&gt;The skateboard is the way cool kids get around&lt;/p&gt;
  
  &lt;article&gt;
  &lt;h2&gt;Longboards&lt;/h2&gt;
  &lt;p&gt;Longboards are a type of skateboard with a longer 
  wheelbase and larger, softer wheels.&lt;/p&gt;
  &lt;p&gt;... &lt;/p&gt;
  &lt;p&gt;... &lt;/p&gt;

  &lt;h2&gt;Electric Skateboards&lt;/h2&gt;
  &lt;p&gt;These no longer require the propelling of the skateboard
  by means of the feet; rather an electric motor propels the board, 
  fed by an electric battery.&lt;/p&gt;
  &lt;p&gt;... &lt;/p&gt;
  &lt;p&gt;... &lt;/p&gt;
  &lt;/article&gt;

&lt;/main&gt;
</pre>

O MAIN não pode ser filho de elementos como aside, article, footer, header ou nav. A tag MAIN não é um elemento de seção de conteúdo e ele não afeta o fluxo do documento. Ou seja, ele não tem margin, padding, borda ou qualquer outro valor padrão.

É muito recomendado que utilizemos o ARIA **role=&#8221;main&#8221;** para que usar agents implementem esse mapeamento.

Um detalhe importante: você **não pode** colocar mais do que UMA tag **main** no seu documento. Claro, por motivos óbvios.

## Já vale a pena usar

Já. Embora nenhum navegador ainda tenha suporte oficial, o elemento não provoca nenhum problema no layout. Então eu aconselho atualizar seu código assim que puder. Quando os browsers suportarem, seu código já estará atualizado. Outra motivo é a adesão.

Se acontecer alguma coisa e a galera voltar atrás, é simples de arracar o elemento de lá. Sem chororo. 😉

Link para a [documentação oficial][3].

 [1]: https://plus.google.com/107429617152575897589/posts
 [2]: http://html5doctor.com/interview-with-ian-hickson-html-editor/
 [3]: http://www.w3.org/html/wg/drafts/html/master/grouping-content.html#the-main-element