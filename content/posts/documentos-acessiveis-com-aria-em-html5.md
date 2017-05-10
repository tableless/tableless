---
title: Documentos acessíveis com WAI-ARIA em HTML5
author: Talita Pagani
type: post
date: 2011-04-14
excerpt: 'A preocupação com acessibilidade tem aumentado gradativamente a cada nova versão do HTML e CSS, em vista de atender cada vez mais os usuários que possuem alguma deficiência. '
url: /documentos-acessiveis-com-aria-em-html5/
tweetbackscheck:
  - 1356393835
shorturls:
  - 'a:3:{s:9:"permalink";s:63:"http://tableless.com.br/documentos-acessiveis-com-aria-em-html5";s:7:"tinyurl";s:26:"http://tinyurl.com/42gy56b";s:4:"isgd";s:19:"http://is.gd/87CvGn";}'
twittercomments:
  - 'a:3:{i:144892320020570112;s:7:"retweet";i:145509722383056896;s:7:"retweet";i:144902451965870080;s:7:"retweet";}'
tweetcount:
  - 3
dsq_thread_id: 503040088
categories:
  - Acessibilidade
  - Artigos
  - HTML5
tags:
  - acessibilidade
  - aria
  - html5

---
A reestruturação do HTML para sua versão 5 propõem elementos mais semânticos. Porém, as novas tags do HTML5 não são suficientes para permitir que os documentos sejam corretamente acessíveis a softwares leitores de tela. 

O comportamento dos novos elementos ainda não é reconhecido por estes programas e o conteúdo da página pode não ser interpretado de forma correta. Em alguns testes que fiz com o conhecido leitor de telas [JAWS][1], ele para de interpretar o conteúdo da página logo após o título.

O HTML continua a possui limitações de acessibilidade e, como é cada vez mais utilização para construir aplicações web, é cada vez mais necessária a supressão destas dificuldades para adequar o reconhecimento do conteúdo à tecnologias assistivas.

Para atender esta demanda de acessibilidade e tecnologias assistivas, o grupo [_Web Accessibility Initiative_ (WAI)][2] do W3C tem desenvolvido uma tecnologia complementar para o HTML5 chamada [_Accessible Rich Internet Application_][3] ou simplesmente **ARIA**.

O ARIA provê uma ontologia de funções, estados e propriedades que definem elementos acessíveis de interface. Ele estende a semântica do HTML provendo informações sobre _widgets_, estruturas e comportamentos, de modo a permitir que tecnologias assistivas reconheçam e transmitam informações adequadas.
  
Neste artigo abordaremos um dos conceitos básicos do ARIA: **roles**.

### Roles

Como os leitores de tela não reconhecem novas tags do HTML5, é preciso informar qual o papel de cada tag, ou seja, qual o tipo de informação que ela estará representando. E para isso, o ARIA possui o atributo `role`, que possui um conjunto definido de valores para representar cada tipo de informação. O ARIA define `roles` abstratas (apenas para definição de conceitos gerais, não devem ser utilizadas), de _widget_ (elementos de formulário, em sua maioria), de estrutura de documento e de _landmark_ (áreas onde o usuário pode encontrar acesso rápido, como navegação, busca, etc.)

### Exemplo

O exemplo abaixo mostra o fragmento de uma página em HTML5 utilizando uma estrutura trivial de um blog. Com este código, se a página fosse acessada por um leitor de tela, o conteúdo não seria interpretado.

<pre class="lang-html">&lt;header&gt;  
    &lt;div&gt;Nome do Site&lt;/div&gt;
    &lt;nav&gt;
        &lt;ul&gt;...&lt;/ul&gt;
    &lt;/nav&gt;
&lt;/header&gt;
 
&lt;section&gt;  
 
    &lt;h1&gt;T&iacute;tulo 1&lt;/h1&gt;
 
    &lt;div&gt;&lt;p&gt;Neste espa&ccedil;o pode ser inserido um formul&aacute;rio.&lt;/p&gt;&lt;/div&gt;
 
    &lt;article&gt;             
            &lt;h2&gt;Um post do blog&lt;/h2&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit...&lt;/p&gt;
    &lt;/article&gt;
 
    &lt;article&gt;
            &lt;h2&gt;Outro post do blog&lt;/h2&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit...&lt;/p&gt;
    &lt;/article&gt;
 
&lt;/section&gt; 
 
&lt;aside&gt;  
    &lt;h2&gt;Sidebar&lt;/h2&gt;
    &lt;ul&gt;...&lt;/ul&gt;
&lt;/aside&gt;
 
&lt;footer&gt;Informa&ccedil;&otilde;es do footer.&lt;/footer&gt;
</pre>

Fazemos, então, a aplicação das `roles` nos seguintes elementos:

  * **header**: _role=&#8221;banner&#8221;_. Define uma região que possui, principalmente, conteúdo de orientação do site e não conteúdo específico da página.
  * **nav**: _role=&#8221;navigation&#8221;_. Define uma coleção de elementos de navegação (geralmente links) para navegar no documento ou em documentos relacionados.
  * **section**: _role=&#8221;main&#8221;_. Define o conteúdo principal do documento.
  * **div**: _role=&#8221;application&#8221;_. Declara uma região para uma aplicação web, geralmente contendo formulários, em oposição a um simples documento.
  * **article**: _role=&#8221;article&#8221;_. Define uma seção de uma página que consiste em uma composição que forma uma parte independente do documento.
  * **aside**: _role=&#8221;complementary&#8221;_. Define uma seção de suporte do documento para complementar o conteúdo principal.
  * **footer**: _role=&#8221;contentinfo&#8221;_. Define uma região que contém informações sobre o documento.

Com isso, nosso exemplo fica dessa forma:

<pre class="lang-html">&lt;header&gt;  
    &lt;div&gt;Nome do Site&lt;/div&gt;
    &lt;nav&gt;
        &lt;ul&gt;...&lt;/ul&gt;
    &lt;/nav&gt;
&lt;/header&gt;
 
&lt;section&gt;  
 
    &lt;h1&gt;T&iacute;tulo 1&lt;/h1&gt;
 
    &lt;div&gt;&lt;p&gt;Neste espa&ccedil;o pode ser inserido um formul&aacute;rio.&lt;/p&gt;&lt;/div&gt;
 
    &lt;article&gt;             
            &lt;h2&gt;Um post do blog&lt;/h2&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit...&lt;/p&gt;
    &lt;/article&gt;
 
    &lt;article&gt;
            &lt;h2&gt;Outro post do blog&lt;/h2&gt;
            &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit...&lt;/p&gt;
    &lt;/article&gt;
 
&lt;/section&gt; 
 
&lt;aside&gt;  
    &lt;h2&gt;Sidebar&lt;/h2&gt;
    &lt;ul&gt;...&lt;/ul&gt;
&lt;/aside&gt;
 
&lt;footer&gt;Informa&ccedil;&otilde;es do footer.&lt;/footer&gt;
</pre>

Com estas marcações, os leitores de tela poderão informar o conteúdo que o usuário irá encontrar em cada seção do código. Esta é apenas uma das aplicações do ARIA, que possui outras propriedades para permitir que elementos interativos sejam acessíveis e interoperáveis.

### Para saber mais

  * [Accessible Rich Internet Applications (WAI-ARIA) 1.0][3]
  * [How screen readers speak a page with HTML5 and ARIA][4]
  * [Introduction to WAI ARIA][5]

 [1]: http://www.freedomscientific.com/products/fs/jaws-product-page.asp "JAWS - Screen Reader for Windows"
 [2]: http://www.w3.org/WAI/ "W3C-WAI"
 [3]: http://www.w3.org/WAI/PF/aria/
 [4]: http://cssgallery.info/how-screen-readers-speak-a-page-with-html5-and-aria/
 [5]: http://dev.opera.com/articles/view/introduction-to-wai-aria/