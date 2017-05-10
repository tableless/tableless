---
title: HTML5 Diff
author: Diego Eis
type: post
date: 2010-07-13
excerpt: Um resumo do que mudou no HTML5 em comparação com o HTML4.
url: /html5-diff/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356394075
shorturls:
  - 'a:3:{s:9:"permalink";s:34:"http://tableless.com.br/html5-diff";s:7:"tinyurl";s:26:"http://tinyurl.com/42765j2";s:4:"isgd";s:19:"http://is.gd/Oz7CKE";}'
twittercomments:
  - 'a:2:{i:35357237505425408;s:7:"retweet";i:35352685414711296;s:7:"retweet";}'
tweetcount:
  - 2
dsq_thread_id: 503039462
categories:
  - Artigos
  - Código
  - HTML
  - HTML5
  - Tecnologia e Tendências
tags:
  - 2010
  - desenvolvimento web
  - html5
  - Na Prática
  - padroesweb
  - tableless
  - web standards
  - xhtml

---
O [W3C][1] mantém um documento que compara o HTML4 com as novidades do HTML5. São inúmeras mudanças em elementos mais conhecidos e também em outros elementos mais específicos, utilizados em aplicações e sistemas mais complexos. Sugiro que você leia [este documento][2] e o guarde como referência.

O HTML5 ainda é um rascunho. Ele está sendo discutido entre o WHATWG e o W3C. Diversos pontos podem ser modificados ainda, por isso é interessante que você entenda e fique por dentro das discussões para que você atualize seu código quando necessário.

Um dos grandes objetivos do HTML5 é que ele seja retrocompatível. Isso evita o retrabalho de código e faz com que a web retome o rumo da semântica e do código enxuto. Vamos às mudanças:

O elemento B passa a ter o mesmo nível semântico que um SPAN, mas ainda mantém o estilo de negrito no texto. Contudo, ele não dá nenhuma importância para o text marcado com ele.

O elemento I também passa a ser um SPAN. O texto continua sendo itálico e para usuários de leitores de tela, a voz utilizada é modificada para indicar ênfase. Isso pode ser útil para marcar frases em outros idiomas, termos técnicos e etc.

O interessante é que nestes dois casos houve apenas uma mudança semântica. Provavelmente você não precisará modificar códigos onde estes dois elementos são utilizados.

Voce utilizará o SMALL para fazer literalmente os &#8220;letras miúdas&#8221; de um documento legal, comentários gerais ou até mesmo aqueles pequenos comentários e dicas que colocamos em campos de formulários e etc.

O HR virou um parágrafo de quebra. Ou seja, ele passa a ter a mesma importância do parágrafo, mas em um nível temático para quebra de linha.

Os elementos abaixo foram descontinuados por que seus efeitos são apenas visuais:

  * basefont
  * big
  * center
  * font
  * s
  * strike
  * tt
  * u

Como já era conhecido por alguns, os inputs ganharam novos valores no atributo TYPE. Estes novos valores permitem que browsers e outros user-agents melhorem a experiência do usuário, mostrando calendários e permitindo integração com agenda de contatos e etc. Permite também que os dados possam ser submetidos para o servidor com um formato específico. Valores como TEL, URL e EMAIL já tem efeitos em smartphones como iPhone:

  * tel
  * search
  * url
  * email
  * datetime
  * date
  * month
  * week
  * time
  * datetime-local
  * number
  * range
  * color

Os elementos abaixo não foram incluídos na especificação porque não tiveram uso entre os desenvolvedores ou porque sua função foi substituída por outro elemento:

  * `acronym` não foi incluído porque criou um bocado de confusão entre os desenvolvedores que preferiram utilizar a tag `abbr`. 
      * `applet` ficou obsoleto em favor da tag `object`. 
          * `isindex` foi substituído pelo uso de form controls. 
              * `dir` ficou obsoleto em favor da tag `ul`. </ul> 
                Este atributos foram descontinuados porque modificam a formatação do elemento e suas funções são melhores controladas pelo CSS:
                
                  * `align` como atributo da tag `caption`,
	      
                    `iframe`, `img`, `input`,
	      
                    `object`, `legend`, `table`,
	      
                    `hr`, `div`, `h1`, `h2`,
	      
                    `h3`, `h4`, `h5`, `h6`,
	      
                    `p`, `col`, `colgroup`,
	      
                    `tbody`, `td`, `tfoot`, `th`,
	      
                    `thead` e `tr`.</p> 
                  * `alink`, `link`, `text` e
	      
                    `vlink` como atributos da tag `body`.</p> 
                  * `background` como atributo da tag `body`. 
                  * `bgcolor` como atributo da tag `table`, `tr`,
	      
                    `td`, `th` e `body`.</p> 
                  * `border` como atributo da tag `table` e
	      
                    `object`.</p> 
                  * `cellpadding` e `cellspacing` como atributos da tag
	      
                    `table`.</p> 
                  * `char` e `charoff` como atributos da tag
	      
                    `col`, `colgroup`, `tbody`,
	      
                    `td`, `tfoot`, `th`, `thead`</p> 
                    e `tr`.
                
                  * `clear` como atributo da tag `br`. 
                  * `compact` como atributo da tag `dl`, `menu`,
	      
                    `ol` e `ul`.</p> 
                  * `frame` como atributo da tag `table`. 
                  * `frameborder` como atributo da tag `iframe`. 
                  * `height` como atributo da tag `td` e `th`. 
                  * `hspace` e `vspace` como atributos da tag
	      
                    `img` e `object`.</p> 
                  * `marginheight` e `marginwidth` como atributos da tag
	      
                    `iframe`.</p> 
                  * `noshade` como atributo da tag `hr`. 
                  * `nowrap` como atributo da tag `td` e `th`. 
                  * `rules` como atributo da tag `table`. 
                  * `scrolling` como atributo da tag `iframe`. 
                  * `size` como atributo da tag `hr`. 
                  * `type` como atributo da tag `li`, `ol` e
	      
                    `ul`.</p> 
                  * `valign` como atributo da tag `col`,
	      
                    `colgroup`, `tbody`, `td`,
	      
                    `tfoot`, `th`, `thead` e
	      
                    `tr`.</p> 
                  * `width` como atributo da tag `hr`, `table`,
	      
                    `td`, `th`, `col`, `colgroup`</p> 
                    e `pre`. </li> </ul> 
                    
                    Alguns atributos do HTML4 não são mais permitidos no HTML5. Se eles tiverem algum impacto negativo na compatibilidade de algum user-agent eles serão discutidos. 
                    
                      * `rev` e `charset` como atributos da tag
      
                        `link` e `a`.</p> 
                      * `shape` e `coords` como atributos da tag
      
                        `a`.</p> 
                      * `longdesc` como atributo da tag `img` and
      
                        `iframe`.</p> 
                      * `target` como atributo da tag `link`. 
                      * `nohref` como atributo da tag `area`. 
                      * `profile` como atributo da tag `head`. 
                      * `version` como atributo da tag `html`. 
                      * `name` como atributo da tag `img` (use `id` 
                        instead).
                    
                      * `scheme` como atributo da tag `meta`. 
                      * `archive`, `classid`, `codebase`,
      
                        `codetype`, `declare` e `standby`</p> 
                        como atributos da tag `object`.
                    
                      * `valuetype` e `type` como atributos da tag
      
                        `param`.</p> 
                      * `axis` e `abbr` como atributos da tag `td` 
                        e `th`.
                    
                      * `scope` como atributo da tag `td`. 
                    
                    Há outras mudanças mais profundas, por isso sugiro que você leia esse documento inteiro: [W3C HTML5 Diff][2].
                    
                    Estes artigos também podem ajudar:
                    
                      * [Conteúdo, Flash e HTML][3]
                      * [Processos de Adoção e Padrões][4]
                      * [HTML5 &#8211; Mudanças na estrutura e Semântica][5]
                      * [Ah! O maravilhoso mundo real][6]

 [1]: http://w3c.org/
 [2]: http://www.w3.org/TR/2010/WD-html5-diff-20100624 "mundanças no html5"
 [3]: http://tableless.com.br/contedo-flash-e-html
 [4]: http://tableless.com.br/processos-adocao-padroes
 [5]: http://tableless.com.br/html5-estrutura-semantica
 [6]: http://tableless.com.br/ah-o-maravilhoso-mundo-real