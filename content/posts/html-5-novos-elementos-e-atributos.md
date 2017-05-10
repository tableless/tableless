---
title: HTML 5, novos elementos e atributos.
author: Thaiana Poplade
type: post
date: 2011-02-28
excerpt: Em meio à tutoriais e artigos a respeito, em alguns minutos consegue-se perceber algumas das novas possibilidades que o HTML 5 proporcionará, mas na prática da construção de códigos para interfaces, o que será possível além de secções, barras de menu, barras laterais, etc?
url: /html-5-novos-elementos-e-atributos/
tweetbackscheck:
  - 1356406153
shorturls:
  - 'a:3:{s:9:"permalink";s:58:"http://tableless.com.br/html-5-novos-elementos-e-atributos";s:7:"tinyurl";s:26:"http://tinyurl.com/44csu7o";s:4:"isgd";s:19:"http://is.gd/yPaxFt";}'
twittercomments:
  - 'a:29:{i:146002622099361792;s:7:"retweet";i:146007777561686016;s:7:"retweet";i:146004868266598400;s:7:"retweet";i:146047292032552960;s:7:"retweet";i:146035921626726400;s:7:"retweet";i:146236502991572993;s:7:"retweet";i:146002646728323072;s:7:"retweet";i:146002618949443584;s:7:"retweet";i:146002443887587329;s:7:"retweet";i:146190325055107072;s:7:"retweet";i:146373501362765824;s:7:"retweet";i:146024481096335362;s:7:"retweet";i:149922062180421632;s:7:"retweet";i:149914968345673728;s:7:"retweet";i:149913941391323136;s:7:"retweet";i:149907759360520193;s:7:"retweet";i:149907241661775872;s:7:"retweet";i:149906548494307328;s:7:"retweet";i:149906160680579072;s:7:"retweet";i:149906156117164032;s:7:"retweet";i:149905957894361089;s:7:"retweet";i:149905818697998336;s:7:"retweet";i:149905761751937025;s:7:"retweet";i:149905732224032768;s:7:"retweet";i:149905547196502017;s:7:"retweet";i:149905525780389888;s:7:"retweet";i:149905287069966336;s:7:"retweet";i:264256999271845888;s:7:"retweet";i:264233722675605504;s:7:"retweet";}'
tweetcount:
  - 43
dsq_thread_id: 503029323
categories:
  - Artigos
  - HTML
  - HTML5
  - Técnicas e Práticas
tags:
  - 2011
  - html5
  - padroes web
  - Semântica
  - tableless

---
Tags, mídia, interação usuário x website, relevância nos resultados de busca, usabilidade e acessibilidade são as grandes definições do poder de transformação que o HTML 5 promete estabelecer quando desenvolvedores web puderem utilizá-lo e <a href="http://tableless.com.br/afinal-o-que-muda-com-o-html-5" target="_blank" rel="external">como já mencionado em outro artigo</a>, especializações na área devem surgir com esta nova versão, ou seja, você terá a possibilidade de escolher em qual das vertentes citadas acima vai deter maior conhecimento. Ainda assim, é fato que a construção de códigos para interfaces continuará sendo tarefa geral do desenvolvedor Front-End e saber quais tags utilizar e de que forma as utilizar continuará sendo conhecimento básico no desenvolvimento de códigos de marcação.

Determinar como distribuir informação será o grande objetivo no planejamento de construção de seu código html na versão 5. Esta hoje, acaba sendo uma das tarefas de um profissional SEO, mas acredita-se que com uso das novas tags desenvolvedores Front-End terão conhecimento e possibilidades de participar deste planejamento.
  
Desta forma, o conselho é: você desenvolvedor não familiarizado com algumas destas técnicas de construção semântica de códigos html priorizando informação, pode fazer algumas leituras complementares a respeito, como por exemplo, <a href="http://tableless.com.br/introducao-a-microdata-no-html5" target="_blank">o uso de Microdata no HTML 5 &#8211; explanado pela Talita Pagani</a>. Este com certeza, será um diferencial no perfil de um profissional Front-End.

### Novos elementos

Além das tags de mídia (`audio` e `vídeo`), a incansavelmente comentada `canvas` e das novas tags de estrutura: `section`, `article`, `nav`, `aside`, `header` e `footer`, teremos também, de acordo com a W3C, ainda outras novas tags que determinarão o tipo de informação que estará sendo exibida na tela. Um exemplo são as tags: `embed` que será usada para pluggins e a tag `progress` que representará dados em progresso como o download de um arquivo.
  
Outro exemplo de novos elementos, será a tag `time` utilizada para informações de dia e hora que poderão situar o usuário quanto ao horário e data de navegação ou apenas quanto a periodicidade de um novo post em um blog ou de um novo comentário. Abaixo, 3 exemplos de como aplicar esta tag:

Para determinar hora:

<pre lang="html" class="1"><p>
  Postado às &lt;time>09:00hs&lt;/time>
</p>
</pre>

Para determinar a data [ através do uso do atributo datetime]:

<pre lang="html" class="1"><p>
  Postado em &lt;time datetime=”2011-02-13”> 13 de fevereiro de 2011&lt;/time>
</p>
</pre>

Ou para determinar data e hora de um local específico:

<pre lang="html" class="1"><p>
  Postado em &lt;time datetime=”2011-02-13”> 13 de fevereiro de 2011 às 09:00hs&lt;/time>
</p>
</pre>

Neste último exemplo, a informação referente ao horário é separada da informação de data através do separador “T” (obrigatório caso ambas as informações sejam declaradas). Logo após é possível adicionar a informação de fuso horário `[+03:00]` &#8211; declarada para situar o local onde este horário está sendo determinado &#8211; em nosso exemplo: regiões Nordeste / Sul e Sudeste do Brasil, de acordo com o ponto referencial &#8211; Meridiano de Greenwich.

### Novos atributos

Com o HTML 5, novos atributos à elementos que já existentes também foram criados.
  
Uma das possibilidades que está entusiasmando desenvolvedores é quanto a criação de formulários sem a necessidade de scripts externos para validação das informação que serão “inputadas” pelos usuários.
  
Por exemplo, o elemento `input` poderá receber atributos como `tel` [para número de telefones], `search` [para campos de busca], `month`, `date`, `time` [para informações referentes a tempo e data], `email` [para endereços eletrônicos], entre outros. <a href="http://tableless.com.br/html5/?chapter=7" target="_blank">Saiba mais sobre a construção de formulários em HTML 5.</a>
  
Outros novos atributos que também prometem revolucionar são: `placeholder` que poderá ser declarado nos elementos `input` e `textarea`, utilizado para validar o tipo de informação a ser inserida. Por exemplo: `<input type=”email” placeholder=”a@b.com.br” />`
  
E o atributo `required` que poderá ser declarado aos campos de um formulário exigindo preenchimento. 

### Elementos Alterados

Alguns elementos terão sua significancia alterada no HTML 5. Como por exemplo, o elemento `b` que não representará nada além de uma informação em negrito na tela e o elemento `i` que representará informações em outras línguas ou um novo tom de voz para leitores de tela. 

### Elementos eliminados

E como não poderia deixar de ser, alguns elementos não deverão mais ser utilizados, como por exemplo os elementos `center`, `u`, `tt`, `frame` e `noframes`. Inevitavelmente, algumas das técnicas de acessibilidade que utilizamos hoje, deverão ser revistas bem como a busca por novas alternativas para esta nova versão.

Muito do que foi descrito acima, ainda está em estudo e aprendizado. Alguns testes já podem ser feitos em navegadores como o Chrome e Opera e, em algumas semanas, Firefox 4, e são essenciais para um entendimento mais direto das limitações e possibilidades que teremos. Sem descartar claro, que a troca de informações entre profissionais do desenvolvimento web será essencial, portanto comente, observe e sugira maneiras de utilização e saiba, este é só o começo do quanto o HTML 5 pretende revolucionar o que conhecemos por “construção de websites”.