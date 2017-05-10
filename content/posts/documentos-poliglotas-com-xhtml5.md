---
title: Documentos poliglotas com XHTML5
author: Talita Pagani
type: post
date: 2012-05-16
excerpt: O XHTML5 permite utilizar a sintaxe do XML/XHTML em documentos HTML5
url: /documentos-poliglotas-com-xhtml5/
tweetbackscheck:
  - 1356460265
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6057";s:7:"tinyurl";s:26:"http://tinyurl.com/7n8yd6c";s:4:"isgd";s:19:"http://is.gd/3YuL59";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 691953873
categories:
  - HTML
  - HTML5
  - Mercado e Comportamento
  - Tecnologia e Tendências
tags:
  - html5
  - marcação poliglota
  - padroes web
  - xhtml5
  - xml

---
Quando se começou a falar massivamente a respeito do HTML5, em 2009, muitos desenvolvedores (inclusive eu) torceram o nariz para o fato de poder voltar a utilizar a sintaxe tolerante do HTML, ou seja, tags em uppercase ou sem fechamento, valores de atributos sem aspas, fechar tags em ordem incorreta, entre outros. Inclusive, [comentei especificamente sobre isso em um outro artigo][1].

Grande parte dos desenvolvedores aprenderam  e se habituaram a utilizar a sintaxe do XHTML, que segue as diretrizes do XML para documentos bem formados e que apresentariam erros de renderização caso essas diretrizes são fossem seguidas. Isto nos permitia códigos mais limpos e bem estruturados. Porém, no HTML5, a escolha é sua e você não será punido por não fechar tags.

Com toda essa preocupação, no mesmo ano começou a ideia do XHTML5, uma tentativa de contornar o problema, adicionando as restrições de marcação do XML a documentos escritos em HTML5. Podemos dizer que seria uma tentativa de unir o melhor de cada especificação. O [artigo escrito por Bruce Lawson para o HTML5 Doctor][2] (com [versão traduzida no Pinceladas da Web][3]) foi um dos primeiros a comentar sobre o tema.

Durante cerca de 1 ano isto era uma forma, digamos, marginalizada de tratar essa questão, por não ser algo reconhecido pelo  <a title="Web Hypertext Application Technology Working Group" href="http://www.whatwg.org/" target="_blank">WHATWG</a> / <a title="W3C HTML Working Group" href="http://www.w3.org/html/wg/" target="_blank">HTML WG</a>. Mas em 2010 surgiu o primeiro draft com a proposta de nortear o uso do HTML5 com a sintaxe do XML/XHTML. O W3C denominou essa metodologia de [marcação poliglota][4].

### O que é um documento com marcação poliglota?

Um documento com marcação poliglota é um documento escrito em HTML5 que pode ser processado tanto como HTML quanto como XML dentro de um conjunto de restrições definidas, porém, ainda seguindo a especificação do HTML5. Eles são compatíveis com o HTML e XHTML.

Significa que você pode utilizar todo o poder do HTML5 dentro do padrão de marcação bem formada do XML. É importante ressaltar que isto não afeta as tags que você pode utilizar. Por exemplo, elementos que são considerados _deprecated_ em XHTML mas válidos no HTML5 continuam a ser válidos. Uma exceção é com relação a algumas tags que são excluídas de documentos poliglotas por não serem possível de serem replicadas em um _parser_ XML (como é o caso da tag _<noscript>_).

Mas em linhas gerais, esta “fusão” não altera a especificação, mas sim as regras de sintaxe para processamento e há influência no DOM também (ex.: _document.write_ não é permitido, mas sim _innerHTML_).

Segundo o W3C, um documento poliglota resulta em:

  * Um documento HTML5 válido;
  * Um documento XML bem formado (mas não significa um documento XML válido);
  * DOM idêntico quando processado tanto como HTML quanto como XML, isto porque os parsers geram diferentes DOMs para determinados atributos relativos ao XML.

### Como escrever um documento poliglota

Um dos principais requisitos para escrever um documento em XHTML5 é o MIME-type utilizado. Isto vai definir se o navegador irá interpretar o documento como HTML ou XHTML. Segundo o WHATWG, um documento HTML5 se torna um documento poliglota se for provido o MIME-type application/xhtml+xml.

[cc lang=&#8221;html&#8221;]

<meta http-equiv="Content-Type" content="application/xhtml+xml; charset=utf-8" />
[/cc]

Até algum tempo atrás, o IE não suportava este MIME-type. Para isso, você pode indicar que o MIME-type é o usual _text/html_. Ele pode ser utilizado junto com o primeiro (separando por vírgula), ou pode ser feita uma validação do navegador para decidir qual o MIME-type a ser utilizado.

O doctype passa a ser opcional, mas ainda é recomendável utilizar para prevenir o [quirks mode][5] dos navegadores. Se utilizado, a palavra doctype deve ser escrito adequadamente em uppercase, ex.: _<!DOCTYPE html>_. A meta-tag que especifica o charset e a declaração _<?xml version=”1.0” encoding=”UTF-8”?>_ (herdada do XHTML 1.1) também passam a ser opcionais se o charset desejado para o documento é UTF-8 (padrão do XML).

Além disso é preciso definir também o namespace do XHTML na tag _<html>_:

[cc lang=&#8221;html&#8221;][/cc]</p> 

Ao utilizar recursos como SVG e MathML, é preciso especificar também o atributo xml para a tag raiz correspondente de cada um.

Outras recomendações são:

  * Usar tanto o atributo lang quanto xml:lang na tag _<html>_;
  * Usar _tbody_ / _thead_ / _tfoot_ em _<table>_s;
  * Quando o elemento _<col>_ é utilizado em tabelas, utilizar também o elemento _<colgroup>_;
  * Não utilizar o elemento _<noscript>_;
  * Não iniciar as tags _<pre>_ e _<textarea>_ com linha em branco;
  * Utilizar _innerHTML_ ao invés de _documento.write_;
  * Para scripts embutidos na página, escreva o código entre uma seção CDATA com os delimitadores comentados. É uma forma de fazer com que o parser do XML (que analisa apenas a marcação) não acuse erros ao utilizar < ou & no script;
  * Os atributos _xml:space_ e _xml:base_ são permitidos apenas nos elementos relativos a SVG e MathML;
  * Elementos que podem ter conteúdo mas estão vazios não devem ser minimizados para o formato de tag órfã. Ex.: _<p />_ não deve ser utilizado, mas sim _<p></p>_.

Ao escrever documentos poliglotas, é possível utilizar todas as funcionalidades do HTML5 com uma garantia de código bem formado de acordo com as restrições do XHTML. Com isso, é possível ter um código mais organizado e consistente que seja mais fácil de produzir, manter e reutilizar a longo prazo, principalmente quando este trabalho é realizado em equipe.

### Referências

[Polyglot Markup: HTML-Compatible XHTML Documents][4]
  
[XHTML5 in a nutshell][6]
  
[Benefits of polyglot XHTML5][7]
  
[HTML 5 + XML = XHTML 5][2]

 [1]: http://tableless.com.br/o-dilema-da-sintaxe-no-html5/
 [2]: http://html5doctor.com/html-5-xml-xhtml-5/
 [3]: http://www.pinceladasdaweb.com.br/blog/2009/12/10/html-5-xml-xhtml-5/
 [4]: http://dev.w3.org/html5/html-xhtml-author-guide/
 [5]: http://en.wikipedia.org/wiki/Quirks_mode
 [6]: http://blog.whatwg.org/xhtml5-in-a-nutshell
 [7]: http://www.xmlplease.com/xhtml/xhtml5polyglot/