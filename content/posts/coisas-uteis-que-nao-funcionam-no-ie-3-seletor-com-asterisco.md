---
title: 'Coisas úteis que não funcionam no IE #3 – Seletor com asterísco'
author: Diego Eis
type: post
date: 2006-12-04
url: /coisas-uteis-que-nao-funcionam-no-ie-3-seletor-com-asterisco/
tweetbackscheck:
  - 1355864726
shorturls:
  - 'a:3:{s:9:"permalink";s:84:"http://tableless.com.br/coisas-uteis-que-nao-funcionam-no-ie-3-seletor-com-asterisco";s:7:"tinyurl";s:26:"http://tinyurl.com/3f3yepg";s:4:"isgd";s:19:"http://is.gd/aZ8f8d";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036377
categories:
  - Browsers
tags:
  - Técnicas e Práticas

---
Alguns elementos do HTML tem valores padrões de Margem ou Padding ou outros valores de outras propriedades. Estes valores, normalmente são totalmente diferentes dos valores que os designers aplicam para seus layouts. Se você não for regrado, pode fazer confusão com esses valores e causar alguns transtornos na hora da implementação porque esqueceu de zerar os valores padrões dos elementos.

Portanto, sempre que eu começo um CSS, eu me preocupo em zerar todos os valores que possam me atrapalhar futuramente. Me deixando livre para colocar os valores personalizados nestes elementos. Algumas pessoas fazem isso também, mas fazem desta maneira:

 `body, h1, h2, h3, h4, h5, h6, p, form, ul, ol, fieldset {<br />
margin:0;<br />
padding:0;<br />
}`Acontece que esta maneira não é a mais elegante e você pode esquecer de mencionar um objeto. Há outra maneira muito mais fácil e mais elegante para fazer isso, é usando o *. Veja como fica:

`* {<br />
margin:0;<br />
padding:0;<br />
}`O * quer dizer TUDO. Então ele seleciona todos os objetos do HTML, e aplica as características que você quiser. Interessante, huh?

Até aqui isso funciona perfeitamente em tudo quanto é browser e até no IE. Só que você pode utilizar este * de diversas outras formas úteis, e claro, que não funcionam no IE. Por exemplo: Você tem um div #conteudo, e dentro deste div existem diversos outros objetos. Deu na telha de você querer colocar para todos estes objetos uma mesma característica, como por exemplo, borda. Normalmente você faria assim:

`#conteudo div, #conteudo form, #conteudo p, #conteudo fieldset {<br />
border:1px solid black;<br />
}`E daria certo. O ruim é que a cada objeto novo inserido dentro do div#conteudo, você teria que abrir o CSS e editar este seletor mencionando o objeto novo.
  
O jeito bonito de se fazer e que não funciona no IE é este:

`#conteudo * {<br />
border:1px solid black;<br />
}`

Ou seja: tudo que estiver dentro de #conteudo, vai ter uma borda (ou qualquer outra característica que queira).

Mais fácil, bem simples e dá menos, muito menos trabalho. Mas, só funciona em browsers.