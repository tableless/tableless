---
title: CSSDoc – padrão para documentação de folhas de estilo
author: Talita Pagani
type: post
date: 2011-01-02
excerpt: Como padronizar seu código CSS com eficiência com CSSDoc.
url: /cssdoc-documentacao-css/
tweetbackscheck:
  - 1356388603
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/cssdoc-documentacao-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3dujomu";s:4:"isgd";s:19:"http://is.gd/TaGH5b";}'
twittercomments:
  - 'a:4:{i:150188837774176257;s:7:"retweet";i:150156523019055104;s:7:"retweet";i:150099740380495872;s:7:"retweet";i:169578213792681985;s:7:"retweet";}'
tweetcount:
  - 7
dsq_thread_id: 503039857
categories:
  - Artigos
  - CSS
  - Geral
tags:
  - cotidiano
  - CSS
  - cssdoc
  - documentação
  - tecnicascss

---
Cada designer ou desenvolvedor front-end tem o hábito de documentar o código CSS de uma forma diferente através dos comentários. Alguns colocam os nomes das seções, outros inserem uma descrição mais detalhada, alguns utilizam letras maiúsculas e uma sequência de caracteres para formar uma linha.

<pre lang="css" line="1" escaped="true">/* -----------------------------------*/
/* ----------&gt;&gt;&gt; GLOBAL &lt;&lt;&lt;-----------*/
/* -----------------------------------*/

/*
STRUCTURE &gt; HEADER &gt; LOGO
//////////////////////////////////////*/
</pre>

Mas em nenhum destes formatos há uma padronização. Por isto, desde 2007 três desenvolvedores alemães têm desenvolvido a especificação do CSSDoc, que eu já havia mencionado em [outro artigo][1].

O CSSDoc é uma convenção para documentar folhas de estilo herdada do conceito de DocBlock e permite uma forma padronizada de comentar arquivos CSS, facilitando a manutenção e a organização de arquivos compartilhados em uma equipe de desenvolvimento.

O uso desta convenção ajuda a estruturar arquivos CSS adicionando informações relevantes sobre o arquivo e seu respectivo conteúdo (classes, metadata, correção de bugs, etc). Para equipes de desenvolvimento, que necessitam compartilhar um mesmo arquivo com todos os membros da equipe, o uso do CSSDoc oferece de maneira clara e padronizada as especificações técnicas e comentários que clarificam as informações contidas no arquivo.

Para quem trabalha com Java e PHP provavelmente deve conhecer o conceito de DocBlock. Ele se assemelha a um comentário comum de código, entretanto, tem uma organização específica:

<pre lang="css" line="1">/**
* Descrição curta
*
* Exemplo de uma descrição
* longa com quebra de
* linha
*
* @tag valor
*/
</pre>

Todas as especificações baseadas em DocBlock contém _tags_ (identificadas através do @), que são propriedades do trecho de código descrito abaixo do comentário.

### Os tipos de blocos de comentários do CSSDoc

<div id="attachment_2550" style="width: 238px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2010/12/cssdoc-cssfile-structure-00.png"><img src="http://tableless.com.br/uploads/2010/12/cssdoc-cssfile-structure-00-228x300.png" alt="Estrutura do CSSDoc" width="228" height="300" class="size-medium wp-image-2550" srcset="uploads/2010/12/cssdoc-cssfile-structure-00-228x300.png 228w, uploads/2010/12/cssdoc-cssfile-structure-00.png 274w" sizes="(max-width: 228px) 100vw, 228px" /></a>
  
  <p class="wp-caption-text">
    Estrutura do CSSDoc
  </p>
</div>

#### Comentários de Arquivo (File Comments)

O _File Comment_ é utilizado como descrição principal do arquivo CSS, aparece apenas uma vez no arquivo e deve ser escrito no topo. Geralmente nos comentários de arquivo são descritas informações sobre a função do arquivo e alguns metadados como autor, versão, etc.

#### Comentários de Seção (Section Comments)

Abrem seções em arquivos CSS e podem ser utilizados diversas vezes para estruturar o código CSS. O significado de &#8220;seção&#8221; é bastante amplo e depende do designer/desenvolvedor. Algumas seções comuns em CSS são: Reset, Layout, Tipografia, entre outros.

### Principais tags do CSSDoc

Os comentários em CSSDoc podem fornecer diversas informações sobre os arquivos CSS e trechos específicos de código. Algumas tags referem-se apenas a informações do arquivo e são inseridas em _File Comments_, mas a maioria são utilizadas em _Section Comments_. Exemplos de algumas das tags mais utilizadas são:

  * _@autor_: comentário de arquivo, pode conter o nome e/ou o e-mail do autor do documento.
  * _@colordef_: comentário de arquivo, especifica a cor (em hexa ou RGB) e pode também ser fornecido o nome da cor e sua utilização seguido de ponto-e-vírgula.
  * _@bugfix_: comentário de arquivo e de seção, apresenta uma descrição resumida sobre um trecho de código para corrigir alguma incompatibilidade de navegador.
  * _@css-for_: comentário de arquivo e de seção, usado em conjunto com @bugfix para especificar qual browser está relacionado com a correção feita (Ex.: @css-for IE 6).
  * _@section, @subsection e @subsubsection_: comentários de seção, para indicar as seções de um código CSS em até 3 níveis. Quando utilizar @subsection, o bloco de comentário também deve também conter @section, e o mesmo para o @subsubsection, deve conter a @subsection e a @section.

### Porque utilizar CSSDoc

A intenção desta padronização de comentários de código é fornecer uma especificação que possa ser interpretada por aplicações denominadas _parsers_, que geram uma documentação HTML navegável dos blocos de código comentados com CSSDoc.

O _parser_ é uma aplicação responsável por analisar os trechos de comentários, extrair o comentário resumido, comentário longo e as _tags_ para depois formatá-los em documentos HTML.

Esta documentação pode ser disponibilizada online, em uma intranet, extranet ou de outra forma que preferir. E dessa forma há um manual compreensível e de fácil acesso à equipe de desenvolvimento. Em 2009, Thomas Kadauke começou a desenvolver um <a href="https://github.com/imedo/css_doc" target="_blank">parser open source para CSSDoc</a> em Ruby.

E mesmo com o uso do CSSDoc você pode continuar a utilizar o comentário convencional do CSS, ele apenas não será interpretado pelo parser.

### Bônus: Cheat Sheet

Desenvolvi uma Cheat Sheet (guia de referência rápida) não oficial, em inglês, sobre as principais tags do CSSDoc e os comentários de arquivo e de seção. Você pode baixá-la <a href="http://tableless.com.br/uploads/2010/12/cssdoc_cheat_sheet.pdf" target="_blank">aqui</a>.

Para saber mais sobre o projeto e ver outros exemplos de aplicação das _tags_: <a href="http://www.cssdoc.net" target="_blank">CSSDoc.net</a>

 [1]: http://tableless.com.br/6-estrategias-para-melhorar-a-organizacao-do-seu-css-2