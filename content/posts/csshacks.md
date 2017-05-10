---
title: Css Hacks – Ruim com eles, pior sem eles.
author: Diego Eis
type: post
date: 2005-02-11
url: /csshacks/
tweetbackscheck:
  - 1356447337
shorturls:
  - 'a:3:{s:9:"permalink";s:32:"http://tableless.com.br/csshacks";s:7:"tinyurl";s:26:"http://tinyurl.com/3gyg86r";s:4:"isgd";s:19:"http://is.gd/Qz7edn";}'
twittercomments:
  - 'a:1:{i:22315039234981888;s:6:"136574";}'
tweetcount:
  - 1
dsq_thread_id: 503032373
categories:
  - Artigos
  - Browsers
  - Geral
tags:
  - acessibilidade
  - Técnicas e Práticas

---
### O que são os CSS Hacks?

Css Hacks não são mais do que “gambiarras” no código do css que abusam de erros de renderização dos navegadores.

### Para que serve?!

Talvez você já enfrentou um problema parecido:
  
Quando você está implementando um layout, e compara o resultado em vários navegadores, percebe que ficou certo em dois deles mas exclusivamente em um, ficou totalmente diferente. Você sabe que o defeito é simples de ser resolvido… sabe que é só mudar o tamanho do div, para fazer funcionar, mas se você o fizer, vai dar defeito nos outros dois navegadores que estavam certos. Então, O que fazer?

É exatamente aqui que entra o Css Hack.
  
Você irá usá-lo para fazer funcionar seu layout neste único browser que está errado.

Em suma: Css Hack é um código CSS que faz funcionar ou não, um certo código CSS em um browser.

### Existem quantos tipos?!

Existem várias formas de fazer os Hacks de CSS. Basta procurar no google o tipo de hack que você deseja.

Hacks que escondem código css para Netscape, Opera, Mozilla, IE para Mac, e por aí vai.
  
O fato é que você quase não irá usar hacks para estes browsers, e sim, para o grande venerado Internet Explorer para PC.

Vou ensinar aqui 2 tipos de hack. São os dois que eu mais uso. Como os problemas acontecem na maioria das vezes com o Internet Explorer, você precisa apenas de um hack que esconda o css deste browser ou que faça o código funcionar apenas nele.

### Exemplo 1

Este hack fará com o que certo código CSS funcione apenas nele. Ou seja, apenas o Ie vai reconhecer o hack, os outros browsers vão ignorar.
  
Isso funciona em Internet Explorer 5, e o 6 se estiver funcionando em Quirks Mode (assunto para outro artigo).

<pre>div { width:500px; }</pre>

No código acima fizemos todos os divs terem 500 pixels de largura.
  
Suponha que por alguma razão, com este tamanho de largura, o layout ficou bagunçado apenas no Internet Explorer… no Firefox, Opera, Konqueror, Safari, Galeon, e etc ficou certinho.
  
Você precisa então fazer com que esse tamanho diminua apenas para o Internet Explorer, veja o código abaixo:

<pre>div { width:500px; _width:400px; }</pre>

Note que coloquei um underline na segunda propriedade.
  
Todo browser decente não entenderá essa propriedade e a ignorará, pelo simples motivo de que não existe nada no CSS que tenha um underline na frente da propriedade. Isso é errado, não existe, portanto é ignorado.

Mas por algum motivo obscuro, o Internet Explorer aceita essa propriedade.
  
Logo, no Internet Explorer, a largura dos divs somente no Internet Explorer terão 400 pixels de largura.

**Atenção.**
  
Esse hack deve vir depois da propriedade correta. Se vir antes, o IE aceitará a última propriedade que vier, ela sobrescreverá a propriedade underline e dará prioridade para a propriedade que está sem underline.

Outra coisa: Esse hack faz seu CSS não ser validado pelo W3C.
  
Nesse caso, você decide.

### Exemplo 2

Nesse exemplo, usarei um seletor que irá ser desconhecido de muitos. Não vou entrar em muitos detalhes. Sinta-se à vontade para pesquisar pela internet. Abaixo temos o seguinte seletor

<pre>div>p span { background-color:red; }</pre>

Agora preste atenção no código HTML:

<pre><div>
  Aqui vai o texto.
</div>
O seletor de css acima funciona assim:</pre>

Todo ?span? que estiver dentro de um ?p? que por sua vez seja diretamente filho de um ?div? ter o a cor de fundo vermelha.
  
Então, se tiver algum outro ?span?, dentro de um ?p?, mas que não esteja dentro de um ?div?, não terá o fundo vermelho.

Eu prometo (ai, lá vem) que tentarei fazer um artigo explicando seletores. É um assunto bastante interessante e vale a pena estudar.

Bem… Agora voltemos ao tema do artigo.
  
O Internet Explorer simplesmente não reconhece este seletor, ele não sabe que isso existe, não sabe que faz parte do CSS. Portanto, ele ignora totalmente.

Então, se você quisesse fazer com que os spans tivessem uma cor de fundo diferente de vermelho no Internet Explorer, você faria assim:

<pre>span { background-color:blue; }  div>p span { background-color:red; }</pre>

O Ie, relevaria o primeiro código. Ele não reconhece o segundo seletor, logo ele ignora.

Interessante notar que ele reconhece um código que não existe e não reconhece outro que existe. <img width="18" height="18" title=":-D" class="wp-smiley" alt=":-D" src="http://tableless.com.br/smilies/yahoo_bigsmile.gif" />

Todos os outros navegadores que tem uma melhor abordagem ao css, reconhece este seletor e não ignorará.
  
Uso muito esse hack porque ele não impede que seu CSS valide.

Aqui estão 2 Hacks para você usar abusar. Vai ao seu gosto escolher qual dos dois você usará.
  
O primeiro tem menos código, embora não valide. O segundo valida, mas usa mais linhas de código para ser feito.