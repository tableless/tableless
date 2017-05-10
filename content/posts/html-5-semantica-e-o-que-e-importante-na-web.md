---
title: HTML 5 – Semântica e o que é importante na web
author: Diego Eis
type: post
date: 2009-01-26
excerpt: 'Bem como o CSS3 o HTML 5 vem para mudar totalmente a forma que a web é construída. '
url: /html-5-semantica-e-o-que-e-importante-na-web/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356460497
shorturls:
  - 'a:3:{s:9:"permalink";s:68:"http://tableless.com.br/html-5-semantica-e-o-que-e-importante-na-web";s:7:"tinyurl";s:26:"http://tinyurl.com/3tqpyj6";s:4:"isgd";s:19:"http://is.gd/vKQ3wd";}'
twittercomments:
  - 'a:1:{i:19730620334743552;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503038772
categories:
  - Artigos
  - Código
  - HTML
  - Tecnologia e Tendências
tags:
  - CSS
  - html5
  - Semântica
  - w3c
  - xhtml

---
O HTML é a primeira camada do desenvolvimento client-side. Como você sabe, existem 3: a primeira que é a informação, que é o HTML que vai exibi-la na página. A segunda é o CSS, que vai formatar esse HTML de forma que fique legível, usável, bonito. E a terceira que vai definir o comportamento desses elementos, que é o Javascript e Ajax.<!--more-->


  
Deles o HTML é mais importante. É o HTML que cuida da exibição da formatação. É ele que serve os buscadores e leitores de tela. É ele que serve a informação para aplicações e te dão toda a informação que você busca na web todos os dias.

Hoje em dia, a maioria dessa informação tem significado. Leitores de tela e o Google conseguem distinguir o que é um título, parágrafo, ênfase, listas, etc&#8230; Mas como eles sabem o que é um telefone? Ah, sim, fazendo microformatos. Mas microformatos é uma tecnologia que veio para tapar um buraco de semântica do HTML. E esse é um assunto interessante.

Na nova versão do HTML, a 5, o pessoal do W3C está estudando novas formas de inserir significado no HTML. Hoje, só o básico é feito. Você define o que é título, parágrafo, links, endereços, e só. Com algum microformato, você consegue definir um contato, localização e outras informações.

Abaixo, segue uma lista de alguns elementos que podemos utilizar no nosso dia-a-dia para trazer mais significado para a informação dos seus sites:

[a][1]
:   Define a ancora de um elemento.

[abbr][2]
:   Define uma abreviação.

[acronym][3]
:   Indica um acrônimo.

[address][4]
:   A tag address é utilizada para conter informações de endereço e contatos.

[blockquote][5]
:   Blockquote define longos blocos de citação.

[cite][6]
:   Define uma citação ou referência a outra fonte

[code][7]
:   Define que aquele texto é um código.

[dfn][8]
:   Define que certo texto é a definição de um termo.

[div, span][9]
:   Div e Span definem a estrutura dos elementos. Div é um elemento de bloco e Span um elemento de linha.

[dl, dd, dt][10]
:   Listas de definição são feitas para criar um grupo de termos e definições. Muito usada para fazer glossários, dicionários ou entrevistas textuais.

[del, ins][11]
:   INS é utilizado para mostrar que certo texto foi inserido e DEL define o texto que foi deletado da redação. Isso é bastante utilizado para corrigir artigos, textos e etc.

[em][12]
:   Como o strong, indica uma ênfase no texto.

[h1 .. h6][13]
:   Grupo de títulos definidos por importância, onde o H1 é o mais importante e o H6 o menos importante.

[ul, ol, li][14]
:   Listas ordenadas (OL) e listas não ordenadas (UL) são utilizadas para definir e criar listas de itens.

[p][15]
:   Define um parágrafo.

[q][16]
:   Define uma citação ou reposta que não necessita de quebra de linha ou marcação de um parágrafo.

[strong][17]
:   Define uma ênfase, como o EM.

[var][18]
:   Indica uma instância de uma variavel ou argumento de programa.

Além dessas tags, podemos também trabalhar com a semântica com atributos. Alguns deles: Alt, Title, classe, cite, id, lang, longdesc, rev, rel.
  
Tudo isso traz mais significado ao HTML. Mas ainda não é o bastante.

Como o [John Allsopp][19] disse em seu [artigo no A List a Part][20]. Nós precisamos de tipos de mecanismos no HTML, que solucionem a necessidade dos desenvolvedores de enriquecer as informações exibidas no HTML dando significado inteligentes para os elementos. Essa é a verdadeira meta do HTML 5.

Infelizmente a adoção do HTML 5 não é tão simples assim. Temos que lembrar da regra Don´t Break the Web. Esse suporte deve ser leve, caso contrários, browsers como o Internet Explorer 6 ou 7 podem sofrer com a falta de compatibilidade com as novas características.

 [1]: http://www.w3.org/TR/html4/struct/links.html#edef-A
 [2]: http://www.w3.org/TR/html4/struct/text.html#edef-ABBR
 [3]: http://www.w3.org/TR/html4/struct/text.html#edef-ACRONYM
 [4]: http://www.w3.org/TR/html4/struct/global.html#edef-ADDRESS
 [5]: http://www.w3.org/TR/html4/struct/text.html#edef-BLOCKQUOTE
 [6]: http://www.w3.org/TR/html4/struct/text.html#edef-CITE
 [7]: http://www.w3.org/TR/html4/struct/text.html#edef-CODE
 [8]: http://www.w3.org/TR/html4/struct/text.html#edef-DFN
 [9]: http://www.w3.org/TR/html4/struct/global.html#edef-SPAN
 [10]: http://www.w3.org/TR/html4/struct/lists.html#edef-DL
 [11]: http://www.w3.org/TR/html4/struct/text.html#edef-ins
 [12]: http://www.w3.org/TR/html4/struct/text.html#edef-EM
 [13]: http://www.w3.org/TR/html4/struct/global.html#edef-H1
 [14]: http://www.w3.org/TR/html4/struct/lists.html#edef-LI
 [15]: http://www.w3.org/TR/html4/struct/text.html#edef-P
 [16]: http://www.w3.org/TR/html4/struct/text.html#edef-Q
 [17]: http://www.w3.org/TR/html4/struct/text.html#edef-STRONG
 [18]: http://www.w3.org/TR/html4/struct/text.html#edef-VAR
 [19]: http://www.alistapart.com/authors/a/johnallsopp "John Allsopp"
 [20]: http://www.alistapart.com/articles/semanticsinhtml5 "Sematics in HTML 5"