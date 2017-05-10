---
title: Doctype e Browsers Modes
author: Diego Eis
type: post
date: 2005-03-07
url: /doctype/
tweetbackscheck:
  - 1356466139
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/doctype";s:7:"tinyurl";s:26:"http://tinyurl.com/3dqsc4n";s:4:"isgd";s:19:"http://is.gd/KgSdAz";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503032423
categories:
  - Browsers
  - Geral
tags:
  - acessibilidade

---
Um assunto meio complexo e interessante que muita gente se confundi na hora de entender. Doctypes e os modes dos browsers. 

Acho que todos já ouviram falar em Box Model, não é?
              
Pois então&#8230; Alguns browsers calculam as medidas no CSS de um jeito particular, calculam do jeito antigo, errado, causando esse tipo de problema.
              
Muitos fizeram sites enquantos os browsers calculavam do jeito errado. Logo, os desenvolvedores dos browsers ficaram num dilema: Se eles resolvessem o &#8220;bug&#8221; de cálculo, muitos sites iriam parar de funcionar corretamente&#8230;
              
Resolveram criar um tipo de chaveamento para os browsers. 

Hoje, os browsers atuais, funcionam do jeito antigo e do jeito certo, tudo depende do Doctype.
              
O jeito antigo é chamado de &#8220;Quirks Mode&#8221; e o jeito novo chama-se &#8220;Strict Mode&#8221; ou &#8220;Standard Mode&#8221;.
              
Para começar, se os browsers não encontram nenhum tipo de Doctype na página, o Internet Explorer e o Opera funcionam em &#8220;Quirks Mode&#8221;. Mas o Mozilla (e genéricos) funcionam em &#8220;Strict Mode&#8221;.
              
Se os browsers encontram um Doctype, como por exemplo, de HTML 3.0, eles funcionam &#8220;Quirks Mode&#8221;. Se encontram um Doctype mais novo, como XHTML ou até mesmo o HTML 4, eles funcionam em &#8220;Strict Mode&#8221;. 

Abaixo, segue uma tabelinha para facilitar as coisas. 

<table class="dadoscomp">
  <tr>
    <th>
      Navegador
    </th>
    
    <th>
      S / DOCTYPE
    </th>
    
    <th>
      C / DOCTYPE
    </th>
    
    <th>
      C / prolog
    </th>
  </tr>
  
  <tr>
    <th>
      IE 6
    </th>
    
    <td>
      Quirks
    </td>
    
    <td>
      Strict
    </td>
    
    <td>
      Quirks
    </td>
  </tr>
  
  <tr>
    <th>
      IE 5
    </th>
    
    <td>
      Quirks
    </td>
    
    <td>
      Quirks
    </td>
    
    <td>
      Quirks
    </td>
  </tr>
  
  <tr>
    <th>
      Opera
    </th>
    
    <td>
      Quirks
    </td>
    
    <td>
      Strict
    </td>
    
    <td>
      Strict
    </td>
  </tr>
  
  <tr>
    <th>
      Mozilla
    </th>
    
    <td>
      Quirks
    </td>
    
    <td>
      Strict
    </td>
    
    <td>
      Strict
    </td>
  </tr>
  
  <tr>
    <th>
      IE 5 Mac
    </th>
    
    <td>
      Quirks
    </td>
    
    <td>
      Strict
    </td>
    
    <td>
      Strict
    </td>
  </tr>
</table>

### Alguns &#8220;poréns&#8221;:

Embora o Mozilla funcione em &#8220;Quirks Mode&#8221; sem o Doctype, ele calcula o Box Model da maneira correta.
              
Lembrando que há mais diferenças entre o &#8220;Quirks Mode&#8221; e o &#8220;Strict Mode&#8221;. 

O Ie5, **sempre** se comportará do jeito antigo. O Ie6, se colocarmos o Prolog XML, ignora o Doctype (não importa qual seja) e passa a se comportar em &#8220;Quirks Mode&#8221;. 

Eu, particularmente, recomendo colocar o Prolog XML, para fazer o Ie6 se comportar em Quirks Mode. Se eu precisar ajeitar o layout nos Ie&#8217;s, eu coloco um CSS Hack e resolve o problema. 

Mais sobre esse assunto: 

  * <http://www.quirksmode.org/>
  * <http://www.mozilla.org/docs/web-developer/quirks/>
  * <http://www.webmasterworld.com/forum21/7975.htm>
  * [http://www.w3.org/QA/2002/04/valid-dtd-list.htm][1]
  * [Differences between the modes][2]

 [1]: http://www.w3.org/QA/2002/04/valid-dtd-list.html
 [2]: http://www.mozilla.org/docs/web-developer/quirks/quirklist.html