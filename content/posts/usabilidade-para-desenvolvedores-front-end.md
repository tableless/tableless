---
title: Usabilidade para desenvolvedores front-end
author: Talita Pagani
type: post
date: 2010-10-13
excerpt: A usabilidade possui diversos critérios a serem trabalhados durante todo o processo de desenvolvimento de uma interface, mas no dia-a-dia podemos melhorar a experiência do usuário através de pequenos detalhes.
url: /usabilidade-para-desenvolvedores-front-end/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356448998
shorturls:
  - 'a:3:{s:9:"permalink";s:66:"http://tableless.com.br/usabilidade-para-desenvolvedores-front-end";s:7:"tinyurl";s:26:"http://tinyurl.com/43gcmkw";s:4:"isgd";s:19:"http://is.gd/b2cSi2";}'
twittercomments:
  - 'a:52:{i:17071444512997377;s:7:"retweet";i:19789065083682818;s:6:"136511";i:19743952437518337;s:7:"retweet";i:22258700492218368;s:6:"136569";i:37598206179151872;s:7:"retweet";i:42265201931853825;s:6:"137107";i:42266147596402688;s:6:"137108";i:42296883959439360;s:6:"137113";i:42296123104309248;s:6:"137114";i:42303711535562752;s:7:"retweet";i:42300035144228864;s:7:"retweet";i:42299633099210752;s:7:"retweet";i:42249192369963008;s:7:"retweet";i:42249171100639232;s:7:"retweet";i:42248958248108032;s:7:"retweet";i:42248524770967553;s:7:"retweet";i:51300383242465280;s:6:"137371";i:51304794647834624;s:6:"137372";i:51308419847688193;s:6:"137373";i:51310294676414464;s:6:"137375";i:51316675190079488;s:6:"137377";i:51321768891260929;s:6:"137379";i:52698687058624512;s:6:"137419";i:52698121905512449;s:6:"137420";i:52697302883774464;s:6:"137421";i:52697268838608896;s:6:"137422";i:110795222484647936;s:7:"retweet";i:110694587114340352;s:7:"retweet";i:110138295639486464;s:7:"retweet";i:109637381732306945;s:7:"retweet";i:109636845251469312;s:7:"retweet";i:109635701745786881;s:7:"retweet";i:109633752208113664;s:7:"retweet";i:109631493772550144;s:7:"retweet";i:109628333590978560;s:7:"retweet";i:109626218969706496;s:7:"retweet";i:109624801693417472;s:7:"retweet";i:109624135830863873;s:7:"retweet";i:109624114603499520;s:7:"retweet";i:109623896780701696;s:7:"retweet";i:109623527325446144;s:7:"retweet";i:109622614938497024;s:7:"retweet";i:109622432096198656;s:7:"retweet";i:109621150732124160;s:7:"retweet";i:109621126812016640;s:7:"retweet";i:109620991654760448;s:7:"retweet";i:109620815405912064;s:7:"retweet";i:109620799442395137;s:7:"retweet";i:109620528867840000;s:7:"retweet";i:109620506055020544;s:7:"retweet";i:109620387486244866;s:7:"retweet";i:117262506954719232;s:7:"retweet";}'
tweetcount:
  - 212
dsq_thread_id: 503039634
categories:
  - Artigos
  - CSS
  - HTML
tags:
  - clientside
  - CSS
  - padroes web
  - usabilidade

---
A usabilidade é uma qualidade das interfaces que caracteriza a facilidade de uso. Várias diretrizes sobre usabilidade de interfaces web foram desenvolvidas ao longo dos últimos 15 anos e o interesse em proporcionar interfaces de fácil utilização tem crescido entre designers e desenvolvedores.
  
Entre as várias diretrizes de usabilidade, os princípios convergem para a seguinte tríade:

  * **Fácil de usar:** o uso da interface deve ser intuitivo, com recursos de fácil reconhecimento e elementos que não dificultem a navegação, leitura, interpretação, clique, etc.
  * **Fácil de aprender:** uso de termos, ícones, padrões de interface e recursos de ajuda que possibilitem novos usuários reconhecer e facilmente aprender como utilizar a interface. Consistência é fundamental neste quesito.
  * **Fazer com que o usuário não cometa erros:** neste quesito entram entram dicas, ajuda, validação, boas mensagens de erro e outros recursos que possam prevenir a ocorrência de erros e ajudar o usuário na correção dos mesmos.

Mas, na prática, como podemos implementar estes princípios? Neste artigo apresento algumas dicas simples de usabilidade que podemos praticar efetivamente durante o rotina de desenvolvimento do HTML e do CSS.

### Facilitando a leitura com line-height

Um espaçamento adequado entre linhas permite que as pessoas possam ler um texto com maior facilidade e mais rapidamente. O espaçamento não pode ser muito reduzido, pois pode deixar o texto &#8220;amontoado&#8221;, nem muito extenso, caso contrário as pessoas terão dificuldade de encontrar a próxima linha.
  
Particularmente recomendo utilizar espaçamento de 1.5 relativo ao tamanho da fonte, ou seja, se você utilizar fonte de 12px, o espaçamento entre as linhas será de 18px. No CSS, controlamos o espaçamento entre linhas com o `line-height`.

### Utilize margins e paddings para distinguir itens

Espaços em branco entre os elementos da página podem ser usado a favor da usabilidade e também da arquitetura de informação do seu site. Creio que muitos já devem ter passado pela situação de alguém falar o seguinte a respeito de um site que você fez: &#8220;Ah, mas esse conteúdo X não tem a ver com o Y? É porque estava tudo junto então achei que tinha a ver&#8221;.
  
Os espaços entre itens permite identificar quais elementos estão relacionados e quais são distintos. Portanto, utilize `margin` e/ou `padding` mais generosas para afastar elementos que sejam distintos e aproxime os elementos que estejam relacionados, evitando erros de interpretação e mesmo de utilização de alguns recursos presentes na página. Isto serve principalmente para:

  * Estabelecer relação entre títulos e texto
  * Identificar rótulo de formulário e o campo a qual ele se refere
  * Imagens e o respectivo conteúdo textual
  * Páginas que tenham múltiplos formulários ou outros recursos com botões de ação que possam fazer com que o usuário clique em um determinado botão pensando ser relativo a outro recurso

### O logo deve ser clicável

Por uma convenção que foi sendo consolidada ao longo do anos, os usuários tendem a clicar no logotipo para retornar à página inicial e é frustrante quando isso não ocorre, pois já é uma ação que o usuário espera ao clicar no logo. Independente do logo ser uma imagem ou um background dentro de uma outra tag, deve-se colocar um link para a página inicial do site.

### Textos que não são links não devem ser sublinhados

Atualmente, nem todo link precisa estar sublinhado para transmitir a ideia de link, mas todo texto sublinhado ainda transmite a ideia de link. É intuitivo o usuário clicar em uma palavra sublinhada esperando acessar uma página (imagine então se, além de sublinhado, o texto estiver em azul, como já vi em alguns lugares). Portanto, é aconselhável que, para dar ênfase em palavras nos textos, sejam utilizadas as tags `strong`, `em` que já têm essa função.

### Atributos &#8220;alt&#8221; e &#8220;title&#8221; para imagens

O atributo `alt` para a tag `img` tem a função de fornececer um texto alternativo caso a imagem não seja carregada ou caso um browser leitor de tela esteja analisando o conteúdo da página. Por isso, é importante que este texto tenha uma boa descrição sobre o conteúdo da imagem. Mas em algumas imagens é interessante que ela não somente tenha um texto alternativo, mas que também exiba uma dica descritiva da imagem ao passar o mouse sobre ela. Isto é muito útil, por exemplo, ao utilizar ícones que indiquem ações, status ou representem link para algum conteúdo sem o uso de um texto descritivo junto à imagem. Para isso, podemos utilizar o atributo `title` do HTML.

### Associando label à campos de formulário

A tag `label` serve para associar um rótulo a um campo de formulário. Mas muitos desenvolvedores esquecem de realizar essa associação através do atributo `for`, que deve remeter ao `id` do campo de formulário.
  
A principal vantagem dessa associação é permitir que o usuário selecione o campo do formulário ao clicar no `label`, o que facilita muito especialmente no caso de campos do tipo `checkbox` ou `radio`, pois aumenta a região clicável, ajuda diminuir o tempo e a chance de erros para selecionar estes campos.

### Destaque o campo ativo do formulário com :focus

Quando um usuário estiver preenchendo um formulário, ele deve perceber claramente em qual campo está inserindo os dados, pois somente mostrar o cursor dentro do campo pode não ser suficiente.
  
Para isso, pode-se utilizar a pseudo-classe `:focus` no CSS para o seletor de `input`, que possibilita aplicar um estilo ao elemento quando ele recebe foco para receber dados do teclado, como uma borda mais espessa ou de outra cor e um background diferenciado, como no exemplo abaixo:

<pre lang="css">/* Campos no estado normal possuem um background neutro e uma borda clara */
input.text, select, textarea
{ background: #FFF; border: 1px solid #999; }

/* Campos no estado :focus possuem um background diferenciado e uma borda de maior destaque */
input.text:focus, select:focus, textarea:focus
{ background: #FFC; border: 2px solid #D8A561; }</pre>

A usabilidade possui muitos outros critérios a serem trabalhados durante todo o processo de desenvolvimento de uma interface para a web, mas no dia-a-dia podemos melhorar a experiência do usuário através de pequenos detalhes.