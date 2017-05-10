---
title: CSS3 com PIE – bordas, sombras e gradiente
author: Thaiana Poplade
type: post
date: 2011-04-04
excerpt: Utilizar CSS3 no front-end de websites ainda parece uma realidade um pouco distante devido a incompatibilidade de renderização entre os browsers, mas com o lançamento final dos navegadores IE9 e Firefox 4, esta realidade fica ainda mais próxima da prática efetiva que vai criar a nova etapa do desenvolvimento tableless.
url: /css3-bordas-arredondadas-sombras-e-gradiente/
tweetbackscheck:
  - 1356388523
shorturls:
  - 'a:3:{s:9:"permalink";s:68:"http://tableless.com.br/css3-bordas-arredondadas-sombras-e-gradiente";s:7:"tinyurl";s:26:"http://tinyurl.com/3nord3g";s:4:"isgd";s:19:"http://is.gd/VyaV3J";}'
twittercomments:
  - 'a:18:{i:145818679395876865;s:7:"retweet";i:158902711121739779;s:7:"retweet";i:159975179081105408;s:7:"retweet";i:159973521357934592;s:7:"retweet";i:159970928644718592;s:7:"retweet";i:158934121794637824;s:7:"retweet";i:158884186449649664;s:7:"retweet";i:158884011903692800;s:7:"retweet";i:158883560827256832;s:7:"retweet";i:158882895291875328;s:7:"retweet";i:172351941018521600;s:7:"retweet";i:169920036667011072;s:7:"retweet";i:183232806904803328;s:7:"retweet";i:183212236377034753;s:7:"retweet";i:183206276455596034;s:7:"retweet";i:183204339731533825;s:7:"retweet";i:183201892657152001;s:7:"retweet";i:183200564946010113;s:7:"retweet";}'
tweetcount:
  - 49
dsq_thread_id: 503040181
categories:
  - Artigos
  - CSS
  - CSS3
  - Geral
  - HTML
tags:
  - 2011
  - bibliotecas
  - CSS3
  - Na Prática
  - tecnicascss

---
Apesar das incompatibilidades entre browsers, utilizar as novas ou modificadas propriedades em folhas de estilo na versão 3 virou motivo de testes e de implementação das modificações que tanto almejamos no desenvolvimento web. Junto como HTML 5, o uso de CSS3 resultará em facilidades na criação de estruturas semânticas e válidas bem como melhor planejadas visualmente e com velocidade de carregamento reduzida, mas enquanto ainda não o colocamos em prática com HTML5, neste processo de transição em que nos encontramos já podemos utilizar algumas propriedades de CSS3 com os navegadores de mercado, ainda que com o uso de scripts externos para tanto.
  
Abaixo um breve tutorial de como criar boxes com degradês, sombras e bordas arredondadas, apenas utilizando propriedades de css.

### CSS3 PIE

Aplicar propriedades CSS3 é bastante simples e nenhum segredo para desenvolvedores experientes, porém fazer com que estes atributos sejam aplicados aos novos e aos atuais browsers de mercado pode representar uma tarefa um pouco mais trabalhosa.

O browser IE (sempre ele) é um dos responsáveis por esse trabalho. Nas versões 7 e 8, não interpreta as propriedades que vamos demonstrar em nosso tutorial, desta forma, a renderização deverá acontecer através do uso de javascript (neste caso PIE) e mesmo que você não tenha familiaridade com a linguagem, não se preocupe, pois a aplicação deste é simples e baseada apenas na hospedagem de alguns arquivo no servidor e a chamada destes na classe ou ID correspondente no css.

<a href="http://css3pie.com/download-latest" rel="external" target="_blank">Para iniciar, clique aqui e baixe os arquivos CSS3 PIE.</a>

Após, descompacte os arquivos e os hospede no diretório raiz de seu site (seja online ou local) e pronto! Já podemos começar a utilizar bordas arredondadas, gradientes e sombras no IE 7 e 8.

### Firefox, Chrome, Safari e Opera.

Todos os browsers acima citados, em suas versões de mercado, renderizam as propriedades que vamos aplicar neste tutorial, porém o Opera 10 não identifica o atributo que cria gradientes de background e desta forma, utilizaremos valores diferenciados para esta exceção.

### Bordas arredondadas

Para inserirmos bordas arredondadas utilizando CSS3, basta inserirmos a propriedade border-radius e atribuir um valor para tanto, porém devido as diferenças entre browsers e considerando que suas versões de mercado ainda não suportam completamente o parâmetros, distribuimos esta declaração para cada navegador.

Como utilizar a propriedade?
  
_border-radius &#8211; declaração integral para todas as bordas do box_

Na prática:
  
[cc lang=&#8221;css&#8221; line=&#8221;1&#8243;].boxBorda{
  
border-radius: 15px; /\* Implementação W3C \*/
  
-moz-border-radius: 15px /\* Implementação Mozilla \*/
  
-webkit-border-radius: 15px; /\* Implementação para browsers que renderizam via webkit \*/
  
behavior: url(PIE.htc); /\* Comportamento adicionado para renderização das propriedades acima no IE 7 e IE 8 \*/
  
}[/cc]

E pronto! A borda arrendonda dos elementos será renderizada.
  
Outras possibilidades de valores ainda são permitidas, por exemplo quando pretendemos atribuir um valor diferenciado entre a distância do centro do círculo imaginário ao topo ou à lateral.

Como utilizar a propriedade?
  
_border-[top/bottom]-[left/right]-radius &#8211; declaração segmentada para cada uma das bordas do box_

Na prática:
  
[cc lang=&#8221;css&#8221; line=&#8221;1&#8243;].boxBorda{
  
border-top-left-radius: 15px 20px; /\* Implementação W3C \*/
  
-moz-border-radius-topleft: 15px 20px; /\* Implementação Mozilla \*/
  
-webkit-border-top-left-radius: 15px 20px; /\* Implementação para browsers que renderizam via webkit \*/
  
behavior: url(PIE.htc); /\* Comportamento adicionado para renderização das propriedades acima no IE 7 e IE 8 \*/
  
}[/cc]

### Sombras

A propriedade que define sombra à um box, no CSS3, pode criar diversas possibilidades visuais desde que os atributos sejam declarados. Na totalidade da propriedade, o que podemos declarar é:

Como utilizar a propriedade?
  
_box-shadow: [inset (declaração opcional e referente a shadow interna), posição X, posição Y, blur, largura, cor ]_

Abaixo, as declarações para nosso exemplo:

[cc lang=&#8221;css&#8221; line=&#8221;1&#8243;].boxSombra{
  
box-shadow: 0 0 .25em #CCC; /\* Implementação W3C \*/
  
-moz-box-shadow: 0 0 .25em #CCC; /\* Implementação Mozilla \*/
  
-webkit-box-shadow: 0 0 .25em #CCC; /\* Implementação para browsers que renderizam via webkit \*/
  
behavior: url(PIE.htc); /\* Comportamento adicionado para renderização das propriedades acima no IE 7 e IE 8 \*/
  
}[/cc]

**Background: linear-gradient ou radial-gradient**
  
Para definir um degradê de fundo à um box utilizando CSS3, basta inserir a propriedade background: linear-gradient ou radial-gradient e declarar os devidos valores, porém esta propriedade ainda pode ser renderizada de forma diferente entre os browsers, inclusive nas porcentagens que saem de uma cor migrando para outra. De qualquer forma, dependendo do resultado que você pretende obter em tela é perfeitamente aplicável.

Como utilizar a propriedade?
  
_background: linear-gradient{posição, cor (from), cor(to) porcentagem};_

Segue o exemplo:
  
[cc lang=&#8221;css&#8221; line=&#8221;1&#8243;].boxGradiente{
  
background: linear-gradient(#EEF, #FFF 70%); /\* Implementação W3C \*/
  
background: -moz-linear-gradient(#EEF, #FFF 70%); /\* Implementação Mozilla \*/
  
background: -webkit-gradient(linear, 0 0, 0 70%, from(#EEF), to(#FFF));/\* Implementação para browsers que renderizam via webkit \*/
  
-pie-background: linear-gradient(#EEF, #FFF 70%); Propriedade adicionada para renderização das propriedades acima no IE 7 e IE 8 */
  
background: url (image.png) repeat-x 0px 0px; /\* Background com imagem para degradê para o Opera 10 \*/
  
}[/cc]

<a href="http://tableless.com.br/gradientes-em-css" target="_blank" rel="external">Leia mais sobre gradientes em css, clicando aqui.</a>

<a href="http://tableless.github.com/exemplos/css3-pie/index.html" target="_blank" rel="external">Veja um exemplo, clicando aqui.</a> E [baixe o código pelo nosso GitHub aqui][1].

Até a próxima.

😉

 [1]: https://github.com/tableless/exemplos/