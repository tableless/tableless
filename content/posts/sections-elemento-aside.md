---
title: 'Sections: elemento aside – Parte 3'
author: Diego Eis
type: post
date: 2010-10-13
excerpt: O elemento ASIDE agrupa informações relacionadas ao conteúdo principal. São informações desde publicidades, menus laterais, blogos de navegação e etc.
url: /sections-elemento-aside/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356394697
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/sections-elemento-aside";s:7:"tinyurl";s:26:"http://tinyurl.com/3oo3wnw";s:4:"isgd";s:19:"http://is.gd/hG1dD8";}'
twittercomments:
  - 'a:1:{i:12674862111789056;s:6:"136330";}'
tweetcount:
  - 1
dsq_thread_id: 503039590
categories:
  - Código
  - HTML5
  - SEO
tags:
  - 2010
  - aprenda
  - desenvolvimento
  - desenvolvimento web
  - html5
  - padroes web

---
Engana-se se o você acha que o `aside` serve apenas para fazer &#8220;sidebars&#8221;. Lembre-se de outros blocos para utilizamos para expor algum tipo de informação referente ao assunto principal. Isso acontece muito em livros: dependendo do livro que você estiver lendo, como um livro técnico, ele pode ter caixas de informação durante todo o fluxo de texto do livro. Essas caixas normalmente servem para chamar sua atenção para alguma informação importante ou outras informações que agregarão mais ao conteúdo principal. O elemento `aside` fará esse papel quando se tratar de websites. Logo, tenha em mente: o elemento `aside` agrega mais informação ao conteúdo principal.

Algumas utilidades do `aside`: citações ou sidebars, agrupamento de publicidade, grupos e blocos de navegação e para qualquer outro conteúdo que é separado do conteúdo principal.

Dentro do `aside` você pode agregar por exemplo grupos de elementos nav, headers, sections e etc. Isso te permite fazer um menu lateral separando os grupos de informações:

<pre lang="html" line="1">&lt;aside id="menulateral">
   &lt;nav>
       

<h3>
  Esportes
</h3>
       

<ul>
  <li>
    <a href="#">Fórmula 1</a>
  </li>
            
  
  <li>
    <a href="#">Futebol</a>
  </li>
            
  
  <li>
    <a href="#">Baskete</a>
  </li>
            
  
  <li>
    <a href="#">Voley</a>
  </li>
         
</ul>
   &lt;/nav>

   &lt;nav>
       

<h3>
  Política
</h3>
       

<ul>
  <li>
    <a href="#">Eleições 2010</a>
  </li>
            
  
  <li>
    <a href="#">Urna eletrônica</a>
  </li>
            
  
  <li>
    <a href="#">Candidatos</a>
  </li>
         
</ul>
   &lt;/nav>
&lt;/aside>
</pre>

Note que não utilizamos nenhum `div`, pelo contrário, utilizamos apenas tags que trazem algum tipo de significado semântico. Neste exemplo, indicamos para o navegador, aplicação, sistema de busca &#8211; qualquer outra coisa que acessará nosso código &#8211; que aquele é bloco lateral, e que cada grupo de `nav` é referente um assunto.

O elemento `aside` pode ir também dentro de um elemento `article` como uma caixa de notação ou algo do genêro. Nesse caso, quando o usuário imprimir, você pode dar ênfase a esta caixa como se fosse um box de informação, como nos livros.