---
title: O que é Tableless?
author: Diego Eis
type: post
date: 2005-08-09
url: /o-que-etableless/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356466248
shorturls:
  - 'a:3:{s:9:"permalink";s:40:"http://tableless.com.br/o-que-etableless";s:7:"tinyurl";s:26:"http://tinyurl.com/3tz22up";s:4:"isgd";s:19:"http://is.gd/4idbWy";}'
twittercomments:
  - 'a:3:{i:196954586181939200;s:7:"retweet";i:196954585913491456;s:7:"retweet";i:196954585854779393;s:7:"retweet";}'
tweetcount:
  - 3
dsq_thread_id: 503033293
categories:
  - Artigos
  - Geral
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - Browsers
  - CSS
  - desenvolvimento web
  - html
  - internet
  - internet explorer
  - netscape
  - o que e tableless
  - padroes web
  - tableless
  - web standards
  - xhtml
  - xml

---
A Web foi criada para ser um ambiente onde fosse possível trocar informações livremente, e que essas informações pudessem ser acessadas ao redor do planeta por qualquer pessoa. Em 1994, foi criado o W3C (World Wide Web Consortium): um consórcio internacional, onde são desenvolvidas os padrões para a web (Web Standards) tais como: HTML, CSS, XML, XSLT, entre outros.

Naquela época, no mercado de browsers, as opções ainda eram poucas: consistiam apenas em Lynx, Mozaic e Netscape Navigator, da Netscape Communications, então liderada por James Clark. A Microsoft, de Bill Gates, resolveu entrar nesse mercado lançando o Internet Explorer. A partir daí, o Netscape e o Internet Explorer começaram a travar uma guerra atrás de adeptos. A concorrência entre os dois browsers é chamada até hoje de Guerra dos Browsers. Durante essa &#8220;guerra&#8221;, os padrões do W3C ainda eram meros rascunhos. Por conta disso, as duas empresas que não podiam esperar que esses rascunhos ficassem prontos começaram a lançar seus browsers com padrões proprietários.

Agora o impasse: Os browsers tinham seus próprios padrões… Já os desenvolvedores não conseguiam criar um único código que funcionasse nos dois navegadores. Por este motivo, eles eram obrigados a desenvolver, na maioria das vezes, para apenas um browser.
  
Isso trouxe mais um problema, agora para os usuários. O usuário que usava Netscape, não conseguia acessar sites que eram feitos para Internet Explorer, e vice-versa.

Como a web não tinha sido projetada para desenvolver os criativos ambientes gráficos que temos atualmente, naturalmente, os recursos de desenvolvimento eram limitados e os criadores faziam das tripas coração para criar seus sites. Entre as muitas idéias que surgiram para ultrapassar ao ambiente de &#8220;apenas texto&#8221; da internet, estava aquela de utilizar tabelas de HTML para posicionar os elementos no layout, utilizando slices de imagem, gifs transparentes e a técnica de aninhamento de tabelas para contornar os problemas que os padrões proprietários traziam. A esse tipo de técnica, que foi usadapela maior parte dos websites, chamamos de layout com tabelas.

Os sites que seguem os Padrões Web utilizam uma metodologia de desenvolvimento baseado em 3 camadas, são elas:

  1. **Informação** &#8211; A informação do site é exibida utilizando código XHTML ou HTML.
  2. **Formatação** &#8211; O XHTML que exibe a informação é formatada com CSS (Folhas de Estilo). É com CSS que comandamos todo o visual do site. Tudo que é visual e decorativo deve ser feito por CSS.
  3. **Comportamento** &#8211; Definida por Javascript e AJAX. É a camada que define como os elementos irão se comportar de acordo com as ações do usuário.

Em poucas palavras: um site tableless é um site que não utiliza tables para a estruturação do Layout. É um site que segue os Padrões Web.
  
O termo &#8220;tableless&#8221; é usado mais largamente aqui no Brasil. Em outros países outros foram mais difundidos, por exemplo: CSS Layouts.

Um site tabeless segue obrigatoriamente regras de semântica. Cada tag tem sua função própria. Por exemplo, para criar um parágrafo de texto, usamos a tag <p></p>. A tag Table e suas filhas são utilizados para exibir dados tabulados, por exemplo, uma listagem de produtos, onde são mostrados algumas informações sobre o produto como tamanho, preço, cor, material, disponibilidade, etc&#8230;

<table style="margin:0 0 15px;">
  <tr>
    <th>
      Tênis
    </th>
    
    <th>
      Cor
    </th>
    
    <th>
      Tamanho
    </th>
    
    <th>
      Preço
    </th>
    
    <th>
      Disponibilidade
    </th>
  </tr>
  
  <tr>
    <td>
      Nike
    </td>
    
    <td>
      Preto
    </td>
    
    <td>
      38-39
    </td>
    
    <td>
      R$ 100,00
    </td>
    
    <td>
      Em Estoque
    </td>
  </tr>
  
  <tr>
    <td>
      Adidas
    </td>
    
    <td>
      Branco
    </td>
    
    <td>
      40-41
    </td>
    
    <td>
      R$ 120,00
    </td>
    
    <td>
      Esgotado
    </td>
  </tr>
</table>

Formatar informações dos sites não é algo novo. Por volta de 1970, no começo da tragetória do SGML, vários browsers já personalizavam as aparências dos documentos, cada um com seu estilo próprio.

Håkon Wium Lie, estudava e percebia as dificuldades que se tinham ao desenvolver um site, e resolveu criar uma maneira fácil para formatar a informação do HTML. Foi aí que ele propôs a criação do CSS ou Cascading Style Sheets. Esse era o ano de 1994.

Em 1995 eles apresentaram sua proposta e finalmente, o W3C &#8211; World Wide Web Consortium &#8211; que estava acabando de nascer, se interessou pelo projeto e resolveu criar uma equipe, obviamente liderada por Håkon e Bert Bos. O resultado apareceu logo, em 1996, eles lançaram a recomendação oficial pelo W3C do CSS Level 1 (CSS 1).

Dois anos depois, no dia 12 de Maio de 1998, eles lançaram a recomendação do CSS de nível 2. A segunda versão das Folhas de Estilo para web.

Hoje em dia, o nível de compatibilidade entre os browsers é muito parecido, de forma que se você implementar algo específico em um browser, é muito provável que em outro browser esteja igual.

Portanto, o desenvolvedor pode ficar tranqüilo quanto a maioria dos problemas causados por diferenças entre browsers.