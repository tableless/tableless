---
title: 'jQuery: seletores personalizados'
author: Davi Ferreira
type: post
date: 2011-03-30
excerpt: Como se não bastasse ser altamente personalizável através de plugins, o framework jQuery também é bastante flexível com seus seletores. Além de poder localizar objetos e elementos por ID, classe, nome do elemento, expressões e atributos também é possível criar o seu próprio seletor.
url: /jquery-seletores-personalizados/
tweetbackscheck:
  - 1356388603
shorturls:
  - 'a:3:{s:9:"permalink";s:55:"http://tableless.com.br/jquery-seletores-personalizados";s:7:"tinyurl";s:26:"http://tinyurl.com/3sb6kfq";s:4:"isgd";s:19:"http://is.gd/5mjCy6";}'
twittercomments:
  - 'a:13:{i:103555847107526656;s:7:"retweet";i:146373488519811074;s:7:"retweet";i:146184692197105664;s:7:"retweet";i:146180775170146306;s:7:"retweet";i:146176533936091136;s:7:"retweet";i:146138959989325825;s:7:"retweet";i:154680583711232000;s:7:"retweet";i:154669817062895616;s:7:"retweet";i:154666532734107648;s:7:"retweet";i:152898003080982529;s:7:"retweet";i:152877171252273152;s:7:"retweet";i:152858986104893440;s:7:"retweet";i:169589285626970113;s:7:"retweet";}'
tweetcount:
  - 33
dsq_thread_id: 503040176
categories:
  - JQuery
  - Técnicas e Práticas
tags:
  - 2011
  - JavaScript
  - JQuery

---
Um seletor pode ser composto de uma ou mais classes, atributos ou expressões e sua chamada retorna um conjunto de objetos que atendem suas regras.

[cce lang=&#8221;javascript&#8221;]
  
// seleciona todos os elementos <a><br /> $(&#8216;a&#8217;)<br /> // seleciona todas as células com a classe projeto<br /> $(&#8216;td.projeto&#8217;)<br /> // seleciona todas as imagens com o source &#8220;default.jpg&#8221;<br /> $(&#8216;img[src=&#8221;default.jpg&#8221;]&#8217;)<br /> // seleciona todas as linhas diretamente filhas de uma table/tbody<br /> $(&#8216;table > tbody > tr&#8217;)<br /> // seleciona o primeiro parágrafo da página<br /> $(&#8216;p:first&#8217;)<br /> // os elementos com id &#8220;projeto-1&#8221; e &#8220;projeto-2&#8221; e todos os elementos com a classe &#8220;projeto&#8221;<br /> $(&#8216;#projeto-1, #projeto-2, .projeto&#8217;)<br /> [/cce]</p> 

<p>
  No entanto, em momentos bem específicos, para evitar a repetição de código, pode ser necessário desenvolver o seu próprio seletor.
</p>

<h3>
  As propriedades de um seletor
</h3>

<p>
  O cabeçalho básico de um seletor personalizado segue o modelo abaixo:
</p>

<p>
  [cce lang=&#8221;javascript&#8221;]<br /> $.expr[&#8216;:&#8217;].seletor = function(objNode, intStackIndex, arrProperties, arrNodeStack){<br /> // código que deve retornar true para incluir o objeto ou false<br /> };<br /> [/cce]
</p>

<p>
  Através da alta flexibilidade do jQuery estamos estendendo o funcionamento da expressão &#8220;:&#8221; adicionando uma função própria, desenvolvida sob medida para nosso site ou aplicação web.
</p>

<p>
  Um seletor personalizado nada mais é do que uma função que retorna true para incluir o elemento na lista ou false para não incluí-lo. Essa função pode receber até quatro parâmetros:
</p>

<ul>
  <li>
    <strong>objNode</strong> &#8211; o objeto atual (referente ao elemento no DOM, ou seja, NÃO é um clone);
  </li>
  <li>
    <strong>intStackIndex</strong> &#8211; o índice do objeto no conjunto de elementos do seletor. Vamos supor que nosso seletor busque ítens (<li>) de uma lista (<ul>). O primeiro ítem da lista terá o índice 0, o segundo o índice 1 e por aí vai;
  </li>
  <li>
    <strong>arrProperties</strong> &#8211; esse parâmetro contém informações sobre nosso objeto atual no seletor. Só lidaremos mesmo com a posição 3, que representa o parâmetro passado no seletor, mas vejamos o que cada um representa:<br /> [cce lang=&#8221;javascript&#8221;]meta = [<br /> &#8216;:seletor(argumento)&#8217;, // o seletor completo<br /> &#8216;seletor&#8217;, // apenas o seletor<br /> &#8221;, // aspas utilizadas nos parâmetros<br /> &#8216;argumento&#8217; // parâmetros<br /> ][/cce]
  </li>
  <li>
    <strong>arrNodeStack</strong> &#8211; o array completo, com todos os objetos capturados pelo nosso seletor.
  </li>
</ul>

<h3>
  Nosso primeiro seletor
</h3>

<p>
  Hora de colocar a mão na massa. Vamos começar com um seletor bem simples que buscará todos os links da nossa aplicação que possuam &#8220;#&#8221; como atributo href:
</p>

<p>
  [cce lang=&#8221;javascript&#8221;]$.expr[&#8216;:&#8217;].sem_link = function(obj){<br /> return ($(obj).attr(&#8216;href&#8217;) == &#8220;#&#8221;);<br /> };[/cce]
</p>

<p>
  Reparem que só utilizamos o primeiro parâmetro: o próprio objeto. A função compara o atributo href do elemento com o link &#8220;#&#8221; e automaticamente retorna true ou false. Como exemplo de uso do nosso seletor vamos fazer com que todos os links com a tralha no href percam sua ação padrão:
</p>

<p>
  [cce lang=&#8221;javascript&#8221;]$(&#8216;a:sem_link&#8217;).click(function(e){<br /> e.preventDefault();<br /> });[/cce]
</p>

<p>
  É claro que a mesma coisa poderia ter sido obtido com o seguinte seletor nativo:
</p>

<p>
  [cce lang=&#8221;javascript&#8221;]$(&#8216;a[href=&#8221;#&#8221;]&#8217;).click(function(e){<br /> e.preventDefault();<br /> });[/cce]
</p>

<p>
  Esse é o grande lance dos seletores personalizados: saber a hora de usá-los. Dificilmente uma expressão ou um seletor já existente não vai atender à sua necessidade. O que você precisa pesar é se o seletor novo vai facilitar a implementação e manutenção do seu código jQuery. O seletor :sem_link, por exemplo, poderia retornar true também para elementos com o href &#8220;javascript:;&#8221; ou vazio.
</p>

<h3>
  Seletores com parâmetros
</h3>

<p>
  <a href="http://tableless.com.br/melhorando-exibicao-tabelas-jquery" target="_blank">Seguindo a onda das tabelas</a> vamos utilizar como exemplo para nossos próximos seletores uma tabela com os principais jogadores do Mengão. O código completo você encontra lá no <a href="https://github.com/tableless-site/tableless-site.github.com/tree/master/seletores-personalizados" target="_blank">GitHub</a>.
</p>

<p>
  [cce lang=&#8221;html&#8221;]<br /> &#8230;
</p>

<tr>
  <th>
    apelidos
  </th>
  
  <th>
    nome completo
  </th>
  
  <th>
    jogos
  </th>
  
  <th>
    gols
  </th>
  
  <th>
    posição
  </th>
</tr>

<p>
  &#8230;<br /> <tr class=&#8221;jogador&#8221; data-atividade=&#8221;true&#8221;>
</p>

<td>
  Leonardo Moura
</td>

<td>
  Leonardo da Silva Moura
</td>

<td>
  179
</td>

<td>
  27
</td>

<td>
  Lateral
</td></tr> 

<tr class="jogador">
  <td>
    Andrade
  </td>
  
  <td>
    Jorge Luís Andrade da Silva
  </td>
  
  <td>
    160
  </td>
  
  <td>
    7
  </td>
  
  <td>
    Meia
  </td>
</tr>

<p>
  &#8230;<br /> [/cce]
</p>

<p>
  Nosso objetivo é criar um set de seletores para marcar dados específicos na tabela: jogadores em atividade, jogadores com x ou mais gols, jogadores com x ou mais jogos e jogadores de uma posição específica.
</p>

<p>
  Para selecionar apenas os jogadores em atividade apenas precisamos verificar se o atributo atividade nos dados do elemento (data-atividade, ou $(&#8216;.jogador&#8217;).data(&#8216;atividade&#8217;)) é verdadeiro.
</p>

<p>
  [cce lang=&#8221;javascript&#8221;]$.expr[&#8216;:&#8217;].em_atividade = function(obj){<br /> return $(obj).data(&#8216;atividade&#8217;);<br /> };[/cce]
</p>

<p>
  Já para os próximos filtros precisamos passar um parâmetro: um valor mínimo para a quantidade de gols e jogos ou a posição desejada. Lembra quando falamos lá em cima sobre o array de propriedades dos seletores, mais especificamenteo seu terceiro parâmetro? Ele é a nossa chave para seletores com parâmetros.
</p>

<p>
  [cce lang=&#8221;javascript&#8221;]$.expr[&#8216;:&#8217;].posicao = function(obj, index, meta, stack){<br /> if($(obj).find(&#8216;td:last&#8217;).text() == meta[3]) return true;<br /> else return false;<br /> };
</p>

<p>
  $(&#8216;.jogador:posicao(&#8220;Goleiro&#8221;)&#8217;).addClass(&#8216;selected&#8217;);
</p>

<p>
  $.expr[&#8216;:&#8217;].gols = function(obj, index, meta, stack){<br /> var gols = parseInt($(obj).find(&#8216;td:eq(3)&#8217;).text());<br /> if(gols >= meta[3]) return true;<br /> else return false;<br /> };
</p>

<p>
  $(&#8216;.jogador:gols(43)&#8217;).addClass(&#8216;selected&#8217;);
</p>

<p>
  $.expr[&#8216;:&#8217;].jogos = function(obj, index, meta, stack){<br /> var jogos = parseInt($(obj).find(&#8216;td:eq(2)&#8217;).text());<br /> if(jogos >= meta[3]) return true;<br /> else return false;<br /> };
</p>

<p>
  $(&#8216;.jogador:jogos(137)&#8217;).addClass(&#8216;selected&#8217;);[/cce]
</p>

<p>
  No filtro por posições, comparamos o conteúdo da última célula da linha ($(&#8216;td:last&#8217;)), que armazena a posição do jogador, com o conteúdo passado como parâmetro (&#8220;Goleiro&#8221;).
</p>

<p>
  Os filtros de gols e jogos utilizam um outro seletor especial, o :eq. Ele representa a posição do elemento no array de objetos do seletor. Por exemplo, $(&#8216;tr td:eq(2)&#8217;) localiza a terceira célula de uma linha (começa em 0!).
</p>

<p>
  Legal, né? As possibilidades realmente são infinitas e a flexibilidade do jQuery impressiona. Mas, assim como os plugins, lembre-se que nem sempre um seletor personalizado vai ser a melhor solução.
</p>

<p>
  <a href="https://github.com/tableless-site/tableless-site.github.com/tree/master/seletores-personalizados" target="_blank">Clique aqui para fazer o download do exemplo</a> ou <a href="http://tableless-site.github.com/seletores-personalizados/" target="_blank">aqui para visualizar o exemplo no navegador</a>.
</p>