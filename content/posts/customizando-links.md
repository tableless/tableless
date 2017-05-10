---
title: Customizando links
author: Diego Eis
type: post
date: 2011-02-18
excerpt: Customizar links do site pode ser algo rápido e útil para o seu visitante. Fazemos essa customização com a ajuda dos seletores complexos, onde conseguimos filtrar e selecionar links específicos de acordo com o valor do HREF.
url: /customizando-links/
tweetbackscheck:
  - 1356452857
shorturls:
  - 'a:3:{s:9:"permalink";s:42:"http://tableless.com.br/customizando-links";s:7:"tinyurl";s:26:"http://tinyurl.com/3sw9q65";s:4:"isgd";s:19:"http://is.gd/hXTCcv";}'
twittercomments:
  - 'a:18:{i:42633642580783105;s:7:"retweet";i:41117832653701120;s:7:"retweet";i:146373153311047680;s:7:"retweet";i:146251519275184130;s:7:"retweet";i:145626988575604736;s:7:"retweet";i:153903265577312257;s:7:"retweet";i:152768280539561984;s:7:"retweet";i:158757967867559936;s:7:"retweet";i:158752497245241345;s:7:"retweet";i:158712122237390848;s:7:"retweet";i:158710177950990337;s:7:"retweet";i:157796844854980608;s:7:"retweet";i:157787377409077248;s:7:"retweet";i:157257757794377728;s:7:"retweet";i:157238523362156544;s:7:"retweet";i:161443978548482048;s:7:"retweet";i:161443358257053696;s:7:"retweet";i:169588987638448129;s:7:"retweet";}'
tweetcount:
  - 45
dsq_thread_id: 503040023
categories:
  - Acessibilidade
  - CSS
  - Técnicas e Práticas

---
Além do aspecto visual, customizar links é importante por causa da Acessibilidade. Não estou falando aqui da acessibilidade para pessoas cegas e etc, estou falando de acessibilidade para pessoas que enxergam também. Eu gosto muito de usar o browser sem a barra de status. O problema de se fazer isso é que eu nunca sei para onde um link vai. Quando estou lendo um texto e há um link interessante, quase nunca tenho a indicação de que aquele link vai me levar para fora do site, ou vai me levar para o download arquivo e etc&#8230; Por isso é interessante que você, se puder, indique ao leitor qual o tipo de link ele está prestes a clicar. Abaixo dou algumas dicas de [seletores complexos][1] que podem te ajudar com este trabalho.

Os seletores complexos são uma ferramenta fascinante. Os seletores complexos pinçam aqueles elementos difíceis, no meio da estrutura HTML, sem identificação de classes ou IDs. 

O nosso problema aqui é selecionar links cujo os endereços podem variar, levando o usuário para uma página externa ou um arquivo. Os seletores complexos ajudarão a selecionar estes links sem a ajuda de classes ou IDs extras. Veja os exemplos abaixo e divirta-se:

Para formatar um link que leva para um PDF, por exemplo veja o HTML:

<pre lang="HTML" class="1"><a href="arquivo.pdf">Arquivo PDF</a>
</pre>

O CSS ficaria assim:

<pre lang="HTML" line="1">a[href $='.pdf'] { 
   padding-left: 18px;
   background: transparent url(icopdf.gif) no-repeat center left;
}
</pre>

O resultado: [link de arquivo PDF][2]

O código acima aplica o estilo nos links onde o valor do HREF terminam com .PDF.
  
Seguindo a mesma dinâmica:

<pre lang="HTML" line="1">a[href ^="mailto:"] {
   padding-left: 18px;
   background: transparent url(icomailto.gif) no-repeat center left;
}
</pre>

Neste exemplo customizamos os links cujo valor do HREF comece com MAILTO.

Exemplo: [Contato do Tableless][3]

Veja uma [lista de alguns seletores complexos][4] e como eles podem te ajudar com outros elementos.

 [1]: http://migre.me/3Tqgs "Seletores complexos"
 [2]: #arquivo.pdf "Link de Teste - Icone de PDF"
 [3]: mailto: tableless@tableless.com.br
 [4]: http://migre.me/3Tqgs "Artigo sobre Seletores Complexos no CSS"