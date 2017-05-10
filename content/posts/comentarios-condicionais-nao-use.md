---
title: Comentários Condicionais – Não use
author: Diego Eis
type: post
date: 2007-12-18
url: /comentarios-condicionais-nao-use/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356244941
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/comentarios-condicionais-nao-use";s:7:"tinyurl";s:26:"http://tinyurl.com/3ckl47a";s:4:"isgd";s:19:"http://is.gd/MWEVke";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503016721
categories:
  - Artigos
  - HTML
  - Técnicas e Práticas
tags:
  - 2007
  - aprenda
  - Browsers
  - CSS
  - csshacks
  - internet explorer
  - Na Prática

---
A utilização de comentários condicionais não é uma excelente maneira de contornar bugs. Os comentários condicionais são comentários incluídos no código HTML escritos exclusivamente para fazer uma parte do código funcionar no Internet Explorer.

Normalmente o uso dos [comentários condicionais][1] servem para especificar uma parte do código para a interpretação exclusiva pelo Internet Explorer. Alguns desenvolvedores criam um CSS exclusivo para o IE e utilizam os comentários condicionais para que apenas o Internet Explorer entenda este CSS. Assim é possível corrigir bugs que acontecem apenas no Internet Explorer.<!--more-->

Esta prática faz com que o desenvolvedor tenha duas versões do CSS para fazer manutenção, corrigir falhas, implementar novas mudanças etc, etc, etc.

A sintaxe é a seguinte:

<pre>&lt;!--[if IE]&gt;
&lt;link href="estilos/estilos_ie.css" rel="stylesheet" type="text/css" /&gt;
&lt;![endif]--&gt;</pre>

Se quiser, você pode fazer um comentário condicional para separar um código específico para cada versão do internet explorer:

<pre>&lt;!--[if IE]&gt;
     Para todas as versões
&lt;![endif]--&gt;

&lt;!--[if IE 5]&gt;
     Apenas para o Internet Explorer 5
&lt;![endif]--&gt;

&lt;!--[if IE 5.0]&gt;
     Apenas para o Internet Explorer 5
&lt;![endif]--&gt;

&lt;!--[if IE 5.5]&gt;
     Apenas para o Internet Explorer 5.5
&lt;![endif]--&gt;

&lt;!--[if IE 6]&gt;
     Apenas para o Internet Explorer 6
&lt;![endif]--&gt;

&lt;!--[if gte IE 5]&gt;
     Para o Internet Explorer 5 e versões superior
&lt;![endif]--&gt;

&lt;!--[if lt IE 6]&gt;
     Para versões anteriores ao Internet Explorer 6
&lt;![endif]--&gt;

&lt;!--[if lte IE 5.5]&gt;
     Para o Internet Explorer 5.5 e versão inferior
&lt;![endif]--&gt;</pre>

A idéia parece ser interessante. Mas eu não aconselho seu uso.
  
Antigamente, por volta de 1997, todos os sites usavam uma &#8220;<span title="Página de apresentação">splash page</span>&#8221; com dois logos: um logo do Netscape Navigator e outro do Internet Explorer. Naquele tempo, em plena guerra dos browsers, era necessário haver uma versão do site para cada navegador por conta da compatibilidade. Os browsers lutavam por adeptos e uma maneira de conseguir isso era criando códigos proprietários que não funcionassem em nenhum outro browser. Por causa disso, o desenvolvedor tinha um dilema: ou sacrificava uma parte do seu público e se dedicava a um único browser, ou ele trabalhava em dobro para suprir as necessidades de todos os browsers da época.

Ter o dobro do trabalho foi um dos motivos pelo qual o pessoal começou a divulgar os Padrões Web com mais força.
  
Trabalhar com Comentários Condicionais faz com que o desenvolvimento web volte para o ano de 1997. Se você utiliza os comentários condicionais para separar um CSS exclusivo para o IE, geramos trabalho desnecessário. Vai ser preciso replicar as modificações em duas versões. É complicado, leva tempo e é muito, mas muito passível de erros.

Hoje é perfeitamente possível fazer um site sem a utilização de Comentários Condicionais ou CSS HACKS. Claro, há horas que é impossível criar soluções para contornar um bug de compatibilidade sem o usar maneiras alternativas. Mesmo assim, é preferível utilizar os CSS HACKS em vez dos Comentários Condicionais pelo simples motivo de que: 1) eles serão poucos ou quase nenhum, se você fizer um código legível e semântico. 2) se tiver que usá-los, eles estarão no mesmo CSS, não precisará manter dois códigos para duas versões de sites. Você vai resolver os erros de compatibilidade isoladamente.

As dicas são: Mantenha o código o mais simples possível. O código deve ser tratado como o seu lar. Mantenha-o organizado e limpo e você viverá bem ali.
  
Se você for designer, não faça layouts bizarros, com montes e montes de bordas arredondadas, formas que ficam sobrepostas, sombrinhas aqui e ali.

 [1]: http://msdn2.microsoft.com/en-us/library/ms537512.aspx