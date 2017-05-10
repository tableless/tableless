---
title: Sites para Dispositivos Móveis – MediaType
author: Diego Eis
type: post
date: 2007-12-06
url: /sites-para-dispositivos-moveis-mediatype/
tweetbackscheck:
  - 1356439238
shorturls:
  - 'a:3:{s:9:"permalink";s:64:"http://tableless.com.br/sites-para-dispositivos-moveis-mediatype";s:7:"tinyurl";s:26:"http://tinyurl.com/3wtrl9k";s:4:"isgd";s:19:"http://is.gd/D4Y2kX";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037689
categories:
  - Artigos
  - Mobile
  - Técnicas e Práticas
tags:
  - 2007
  - acessibilidade
  - Browsers
  - CSS
  - desenvolvimento
  - design
  - dispositivos moveis
  - html
  - internetmovel
  - mediatype
  - mobilidade
  - opera
  - web standards
  - xhtml

---
Felizmente, com a ajuda dos Web Standards, o trabalho para criar um site ficou muito mais fácil, rápida e o mais importante, divertida.
  
Hoje, você troca de layout a hora que quiser, sem se preocupar em ter que refazer todo o código e programação. Eles já estão feitos, por que ter que recriá-los? Então, você troca apenas 1 arquivo CSS, e seu site muda completamente, sem dor de cabeça, apenas mudando a lente de formatação.

E com as qualidades do <acronym title="Cascading Style Sheets - Folhas de Estilo em Cascata">CSS</acronym>, também se tornou fácil fazer várias vesões de um mesmo site para diversas medias. O que eu quero dizer com isso? Muito simples&#8230; Antes, se você quisesse prover para seu visitante uma versão do seu site para imprimir, você faria uma versão do seu layout mais enxuta, sem as informações que se tornariam desnecessárias uma vez impressas. Teria que refazer o HTML, tirar partes de código e etc&#8230; Hoje, você simplesmente cria um CSS para a media de impressão, e pelo CSS oculta os objetos que você quiser. Muito mais fácil, muito mais prático.

Do mesmo jeito que você faz uma versão do CSS para site ser impresso, você fará uma folha de estilo para os HandHelds. Ou seja, o camarada que entrar usando um dispositivo móvel, terá uma versão totalmente compatível, e sem informações que não lhe é interessante quando está usando esse dispositivo.
  
A mecanica é mesma. Com CSS você oculta as informações não são interessantes para o usuário de mobiles. Por exemplo, se o cidadão acessar o site da [UOL][1] com um mobile, não é interessante para ele, ver boa parte de cabeçalho do UOL. Como por exemplo os links de ASSINE UOL ou links para o BATE-PAPO. Essas informações seriam facilmente ocultadas.

Você fará então, várias versões de CSS para vários tipos de Medias. Usará o mesmo XHTML, sem tocar em nenhum código de programação, manipulando totalmente o site para se adequarem às Medias desejáveis.
  
Suas tags para linkar os arquivos CSS ficarão desta maneira:

Screen: Para Desktops
:   <link rel=&#8221;stylesheet&#8221; type=&#8221;text/css&#8221; href=&#8221;screen.css&#8221; media=&#8221;screen&#8221; />

Print: Para Impressão
:   <link rel=&#8221;stylesheet&#8221; type=&#8221;text/css&#8221; href=&#8221;print.css&#8221; media=&#8221;print&#8221; /> 

HandHelds: Para HandHelds, PDA´s, etc
:   <link rel=&#8221;stylesheet&#8221; type=&#8221;text/css&#8221; href=&#8221;handheld.css&#8221; media=&#8221;handheld&#8221; /> 

Perceba que em todas as linhas, há um atributo MEDIA. É com esse atributo que diremos ao navegar onde ele deve aplicar o CSS. Se o camarada visita o site com um dispositivo móvel, com um navegador que seja de acordo com os Padrões (óbvio), vai usar automáticamente para renderizar o site, o CSS de HandHelds, em vez de Screen. Você não terá trabalho para fazer um script que chaveia nem nada parecido, como fazem alguns sites hoje em dia. Esse chaveamento será feito automáticamente, pelo navegador.

Trabalho? Quase zero. Você teve apenas que criar um novo CSS, escondendo objetos, diminuindo e modificando outros. Alguns mais ousados, farão uma versão que segue o estilo do site visto por desktops, mas mais direcionado a usuários de Mobiles, deixando mais confortáveis.

Compare as duas imagens abaixo. Usei como modelo o site do Opera, eles fizeram um belo trabalho. Primeiro, um screeshot do site visto de um monitor, com MediaType Screen.

[<img src="/artigos/sites-mobiles/opera-screen.jpg" alt="Opera visto pelo Desktop" width="530" />][2]

Agora, confira o mesmo site, só que visto com o CSS destinado a HandHelds. Perceba as diferenças e veja que eles ocultaram boa parte das informações, como por exemplo, aquela chamada enorme sobre o download do Opera 8.5, que é interessante apenas para os usuários de Desktop, não para usuários de Mobiles.

[![Opera visto em um HandHeld][3]][4]

Eles aproveitaram também para rebuscar o design para esses dispositivos. A experiência do usuário, com certeza será satisfatória. É confortável de navegar. Você pode trabalhar melhor outras partes do desenvolvimento, como por exemplo, estudos de usabilidade. Você tem toda liberdade que o CSS pode lhe dar.

### Propriedades CSS mais usadas

Todas as propriedades do CSS estarão disposníveis para o uso na manipulação para qualquer media. Claro, na media screen é que você usará mais largamente os mais variados tipos de propriedades que o CSS concede. Na media screen, as propriedades que você mais usará será a WIDTH, HEIGHT e DISPLAY.

**Width** e **Height** são propriedades que serve para definir largura e altura, respectivamente. Elas tem duas variação, onde você define qual largura/altura máxima que dado objeto pode ter. São elas **max-width** e **max-hight**.
  
Então, você definirá no CSS de handheld, qual a largura máxima, que por exemplo, o body deverá ter.

<pre>body {max-width: 240px;}</pre>

Já a propriedade **display**, será muito usada para ocultar os objetos. Muitas informações que aparecem em alguma parte do layout, muitas vezes não são úteis para os usuários de mobiles, portanto, ocultar essas informações é um favor que você faz para os usuários.

Há algo sobre o assunto no site do Opera, não custa nada dar uma olhada&#8230; [Visite e leia][5].

### Testando

Você não precisa ter um dispositivo móvel para conseguir saber como seu site se comportará. Basta simplesmente usar o sistema de SSR do Opera, ele é ativado apertando a combinação de teclado <kbd>SHIFT + F11</kbd>.
  
Se você já tem um CSS para media de HandHeld, ele ativará automáticamente esse CSS no SSR.

Meu conselho é você primeiro tudo testar o site sem CSS para HandHeld para ter uma noção de como ele será exibido sem formatação específica. Depois, aplique um CSS para HandHelds, e compare a diferença. Veja como você tem mais controle sobre o layout.

E atenção&#8230; Não são todos os browsers que tem um sistema tão bom quanto o Opera. E, hoje em dia, apenas o Opera e o [MiniMo][6] (uma versão do Mozilla para mobiles) tem amplo suporte de CSS. O resto dos browsers tem pouca ou quase nenhum suporte. O IE para HandHeld por exemplo, não tem tanto suporte quanto os outros dois, por exemplo, ele não reconhece MediaTypes.

Vamos nos dar mais atenção a esse mercado. Ele está crescendo e a cada ano surgem novas possibilidades. É um ramo que cresce rápido, e não vai demorar muito você ver qualquer pessoa na rua visitando algum site para consultar um mapa ou procurar qualquer tipo de informação. É muito importante que os desenvolvedores atentem para esse grande caminho.

 [1]: http://www.uol.com.br/
 [2]: /artigos/sites-mobiles/opera-screen.jpg
 [3]: /artigos/sites-mobiles/opera-handheld-preview.jpg
 [4]: /artigos/sites-mobiles/opera-handheld.jpg
 [5]: http://www.opera.com/products/mobile/dev/multiple/
 [6]: http://www.mozilla.org/projects/minimo/