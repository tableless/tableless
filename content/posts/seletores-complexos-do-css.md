---
title: Seletores Complexos do CSS
author: Diego Eis
type: post
date: 2009-03-11
excerpt: Os seletores complexos mostram como a CSS pode ser dinâmica e direta.
url: /seletores-complexos-do-css/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356457389
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/seletores-complexos-do-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3vyqkk8";s:4:"isgd";s:19:"http://is.gd/VKl143";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038919
categories:
  - Artigos
  - CSS
  - Técnicas e Práticas
tags:
  - Código
  - CSS
  - CSS3
  - serie-seletores
  - tecnicascss

---
Os seletores complexos foram feitos para suprir necessidades muito específicas do layout. Por exemplo: Imagine uma página de cadastro, essa página há um formulário enorme, com campos de todos os tipos: radio, checkbox, text, submit etc&#8230; 

Um HTML de exemplo:

<pre class="lang-html">&lt;form action=""&gt;
	&lt;fieldset&gt;
		&lt;label&gt;Nome: &lt;input type="text" class="input-text" /&gt;&lt;/label&gt;
		&lt;label&gt;&lt;input type="checkbox" class="input-checkbox" /&gt; Desejo receber newsletters&lt;/label&gt;
	&lt;/fieldset&gt;
&lt;/form&gt;
</pre>

Agora imagine que você tenha a necessidade de definir a largura somente dos campos de texto, você não poderá colocar a linha como a de baixo:

<pre class="lang-css">input {
	width: 200px;
}
</pre>

Se você utilizar a linha acima, você selecionará todos os **input**, inclusive os de tipo **checkbox**, **radio**, **submit**, etc&#8230; Você gostaria apenas que os inputs de texto, ficassem com o estilo indicado. A saída mais &#8220;inteligente&#8221; até hoje é usando Javascript para encontrar esses elementos, para então atribuirmos uma classe para eles e depois formatarmos essa classe via CSS. Não é uma boa maneira. É aqui que entram os **seletores complexos**. Veja um exemplo abaixo de como resolveríamos o problema acima via CSS:

<pre class="lang-css">input[type="text"] {
	width: 200px;
}
</pre>

Este seletor significa que você encontrará os **inputs** que contenham o atributo **type** cujo valor seja exatamente **text**. Aqui vão alguns outros exemplos de como os seletores podem ser úteis no dia a dia:

<table summary="lista de seletores complexos">
  <tr>
    <th>
      Seletor
    </th>
    
    <th>
      Descrição
    </th>
  </tr>
  
  <tr>
    <td>
      input[type=&#8221;text&#8221;]
    </td>
    
    <td>
      Seleciona o elemento INPUT com o atributo TYPE cujo valor seja exatamente o valor TEXT
    </td>
  </tr>
  
  <tr>
    <td>
      a[title]
    </td>
    
    <td>
      Seleciona o elemento <strong>a</strong> que contenha o atributo <strong>type</strong>não importando o valor.
    </td>
  </tr>
  
  <tr>
    <td>
      a[href$=html]
    </td>
    
    <td>
      Seleciona elementos com atributos cujo seu valor temine com&#8230; Por exemplo, você poderia querer selecionar todos os links que apotam para um arquivo .pdf, ou .php etc.
    </td>
  </tr>
  
  <tr>
    <td>
      a[href^=&#8221;http://tableless.com.br/&#8221;]
    </td>
    
    <td>
      Seleciona elementos com o atributos que comecem com&#8230; Você pode querer selecionar apenas os links que apontem para um site específico, por exemplo.
    </td>
  </tr>
  
  <tr>
    <td>
      a[title~=&#8221;tableless&#8221;]
    </td>
    
    <td>
      Seleciona os elementos cujo o atributo tenha um valor que seja separado por espaços. No exemplo acima ele seleciona um link que contenha o atributo title e que em seu valor tenha a palavra &#8220;tableless&#8221; no meio.
    </td>
  </tr>
  
  <tr>
    <td>
      a[hreflang|=&#8221;pt&#8221;]
    </td>
    
    <td>
      Seleciona o elemento <strong>a</strong> cujo o valor do atributo <strong>hreflang</strong> comece com PT. Ou seja valores como &#8220;pt-br&#8221; serão encontrados.
    </td>
  </tr>
  
  <tr>
    <td>
      a[href=&#8221;http://tableless.com.br/&#8221;]
    </td>
    
    <td>
      Seleciona o elemento <strong>a</strong> cujo o valor do atributo <strong>href</strong> seja exatamente <b>http://tableless.com.br/</b>.
    </td>
  </tr>
  
  <tr>
    <td>
      a[title*=&#8221;artigo&#8221;]
    </td>
    
    <td>
      Seleciona os elementos <strong>a</strong> cujo o valor tenha pelo menos uma ocorrência com a palavra &#8220;artigo&#8221;.
    </td>
  </tr>
  
  <tr>
    <td>
      input:checked
    </td>
    
    <td>
      Um radio button ou um checkbox que esteja marcado
    </td>
  </tr>
</table>

Há uma [lista inteira de seletores aqui][1].

 [1]: http://www.w3.org/TR/css3-selectors/#selectors "Link externo: Lista de seletores do W3C"