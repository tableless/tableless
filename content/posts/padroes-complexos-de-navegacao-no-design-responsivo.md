---
title: Padrões Complexos de Navegação no Design Responsivo
author: Will Sales
type: post
date: 2013-06-28
excerpt: Como lidar com uma navegação complexa no design responsivo? Nesta tradução, Brad Frost mostra os prós e os contras na utilização de alguns padrões de menus.
url: /padroes-complexos-de-navegacao-no-design-responsivo/
dsq_thread_id: 1458578276
categories:
  - Design
  - Mobile
  - Traduções
tags:
  - 2013
  - CSS
  - Mobile
  - mobile
  - responsive
  - traducoes

---
A pergunta que mais recebo desde que postei meu artigo sobre <a href="http://bradfrostweb.com/blog/web/responsive-nav-patterns/" target="_blank">Modelos responsivos de navegação</a> é: **Como lidar com uma navegação complexa no design responsivo?**

Ótima pergunta, mas antes de entrar nos pormenores, eu vos peço: **Use o celular como uma desculpa para revisitar sua navegação**. Observe suas análises. Quais os pontos chave da sua experiência? Onde as pessoas passam a maior parte do tempo? Você realmente precisa da sua &#8220;política de privacidade&#8221; na navegação principal? <a href="http://futurefriend.ly/thinking.html#laser-focus" target="_blank">Tenha foco</a>. Aproveite a falta de espaço da tela para retirar todo o besteirol político do site etc, e elimine todo o conteúdo inútil. Seus usuários agradecerão.

Mais uma coisa: Se você tem zilhões de seções e páginas, **priorize a busca**. Um formulário de busca é uma maneira eficaz de levar os usuários onde eles desejam ir, sem ter que percorrer vários níveis na navegação.

Ok, agora que definimos algumas coisas, é <a href="http://www.youtube.com/watch?v=cdaAWFoWr2c" target="_blank">hora da verdade</a>. Às vezes não é muito prático reduzir suas milhares de páginas em três pequenos e ordenados links que se ajustem a tela de um dispositivo mobile. Muitas vezes você é um grande varejista, ou uma universidade com um enorme conteúdo para um grande público alvo. Às vezes o cliente que anuncia no seu site vai, **literalmente, te engolir** por remover o seu link da navegação.

**Enfim, às vezes você só precisa de uma navegação mais complexa**. O que você vai fazer? Bem, aí vão alguns padrões para lidarmos com navegações complexas, longas e multi-level.

  * Multi Toggle
  * O bom e velho Right-To-Left
  * Pular a sub-navegação
  * Priority+
  * Off-Canvas Flyout
  * Carousel+

## O MULTI-TOGGLE

<img style="width: 550px;height: 375px" title="Fig: Navegação multi-toggle no redesign do site de Barack Obama" alt="Navegação multi-toggle do site do Barack Obama" src="http://bradfrostweb.com/uploads/2012/08/Screen-Shot-2012-08-27-at-11.43.41-PM-650x443.png" />

O menu multi-toggle é basicamente um acordeão encaixado. Basta dar um _tap_ na categoria para revelar sub-categorias ocultas. Uma vez que a tela tenha largura suficiente, é convertida num menu suspenso <a href="http://devsnippets.com/article/reviews/10-brilliant-multi-level-navigation-menu-techniques.html" target="_blank">dropdown multi-level</a>, como já estamos acostumados a ver.

Dica rápida: Use os ícones + ou ▼ para deixar o usuário saber que há mais conteúdo.

### Prós

  * **Escaneável** &#8211; Os usuários podem rapidamente escanear as categorias principais, antes de tomar qualquer decisão em ir ao próximo nível.
  * **Escalável** &#8211; Seu menu tem 17 níveis? Esta solução pode lidar com isso facilmente (mas, por favor, não faça isso).

### Contras

  * **Não é tão atraente** &#8211; Dar _taps_ ao longo dos vários níveis não é a coisa mais elegante do mundo, mas acho que você poderia acabar dizendo a mesma coisa diante de qualquer solução de navegação multi-level.
  * **Um possível JS é requerido** &#8211; Digo &#8220;possível&#8221; pois a maioria desses estilos de interação usam JavaScript para fazer a coisa acontecer. No entanto, o brilhante <a href="https://twitter.com/aarongustafson" target="_blank">Aaron Gustafson</a> demonstrou que você pode <a href="http://www.netmagazine.com/tutorials/build-smart-mobile-navigation-without-hacks" target="_blank">realizar este efeito</a> usando a pseudo-classe :target na regra CSS. Muito legal! Além disso, a necessidade de JavaScript não é necessariamente um contra. Apenas certifique-se que a navegação não será acessada por usuários sem suporte a esta linguagem.

### Recursos

  * <a href="http://www.netmagazine.com/tutorials/build-smart-mobile-navigation-without-hacks" target="_blank">Construa um smart mobile navigation sem hacks</a>
  * <a href="http://jsfiddle.net/leaverou/zwvNY/" target="_blank">Anime usando min-height</a> por <a href="https://twitter.com/leaverou" target="_blank">Lea Verou</a> – Esta técnica é insanamente incrível. Eu a utilizo em todas as minhas necessidades de height-animating, Inclusive em accordions.
  * <a href="http://jqueryui.com/accordion/" target="_blank">jQuery Accordion</a>

### Na web

O redesign do site do <a href="http://www.barackobama.com/" target="_blank">Barack Obama</a> em conjunto com o padrão <a href="http://bradfrostweb.com/blog/web/responsive-nav-patterns/#footer-anchor" target="_blank">footer anchor</a>.

## O BOM E VELHO RIGHT-TO-LEFT

<img style="width: 475px;height: 427px" title="Navegaçao em tela pequena da Sony" alt="Sony" src="http://bradfrostweb.com/uploads/2012/08/sony.gif" />

Em vez de itens de sub-navegação aparecendo por baixo da categoria, como no multi-toggle, o nível seguinte da navegação fica à direita (fora da tela) e é animado quando requisitado.

### Prós

  * **Muito atraente** &#8211; Não é sempre que um menu de navegação te surpreende, mas a navegação right-to-left sem dúvida é muito elegante;
  * **Segue as convenções do mobile** &#8211; A maioria das principais plataformas de smartphones tem algum padrão de animação right-to-left para potencializar sua experiência
  * **Escalável** &#8211; É bom para uma navegação com muitos níveis.

### Contras

  * Complexo &#8211; Isto não é necessariamente um contra, mas este padrão tem &#8211; literalmente &#8211; um monte de peças móveis. Por isso, certifique-se de deixá-las todas acessíveis, garanta-se e teste no maior número de dispositivos possível;
  * **Desempenho da animação** &#8211; O desempenho varia bastante entre os diversos dispositivos e plataformas. Algumas plataformas mobile o animam muito bem, enquanto em outras é uma droga. Também esteja ciente de que algumas plataformas não suportam esta animação, e uma mudança repentina na navegação pode ser um choque ao usuário.

### Na web

  * <a href="http://www.sony.com/index.php" target="_blank">Sony</a>
  * <a href="http://www.currys.co.uk/gbuk/index.html" target="_blank">Currys</a>

## PULAR A SUB-NAVEGAÇÃO

<a href="http://bradfrostweb.com/uploads/2012/08/wwf.png" target="_blank"><img style="width: 550px;height: 128px" title="A navegação responsiva da WWF ignora a sub-navegação em telas menores, fazendo com que os usuários sejam levados direto à página de destino da categoria." alt="World Wildlife Fund Navigation" src="http://bradfrostweb.com/uploads/2012/08/wwf-650x151.png" /></a>

A sub-navegação normalmente inclui itens que também são inclusos na página principal da categoria. Pelo fato do conteúdo ser acessível desta página, é perfeitamente viável simplesmente levar os usuários de small screens direto à página principal e deixá-lo tomar sua próxima decisão de lá.

### Prós

  * **Evita ter que lidar com sub-navegações** &#8211; Simplesmente levar o usuário a uma nova página elimina a dor de cabeça resultante de uma sub-navegação. Embora ele possa se sentir enganado, lembre-se que o _tap_ é utilizado em dispositivos sem um estado _hover_. Assim, quando o usuário dá um _tap_ em &#8220;clothing&#8221; e então é levado à página principal de roupas, ele já está atingindo o seu objetivo.
  * **Simples** – Links para outras páginas.

### Contras

  * **Requer a atualização de uma página inteira para acessar os itens de sub-navegação** &#8211; Este é um grande contra. Ter que ir a uma outra página não é tão eficiente para uma navegação rápida.
  * **Usuários de _small screens_ ainda fazem download do conteúdo da sub-navegação** &#8211; Também é um grande contra. É um caso clássico de usuários mobile fazer download de elementos que nunca irão usar. No entanto, não precisa ser assim. Sub-navegações, especialmente mega menus monstruosos, daqueles cheios de tranqueiras que ninguém nunca irá usar e&#8230; onde eu estava? Ah sim&#8230; eles podem (e devem) ser <a href="http://24ways.org/2011/conditional-loading-for-responsive-designs/" target="_blank">condicionalmente carregados</a> para que usuários de small screens não tenham que baixar um conteúdo inútil.

### Recursos

  * <a href="http://24ways.org/2011/conditional-loading-for-responsive-designs/" target="_blank">Carregamento condicional para design responsivo</a>
  * <a href="http://filamentgroup.com/lab/ajax_includes_modular_content/" target="_blank">Padrão Ajax-Include para conteúdo modular</a>

### Na web

  * <a href="http://worldwildlife.org/" target="_blank">World Wildlife Fund (WWF)</a>
  * <a href="http://www.wvu.edu/" target="_blank">West Virginia University</a>
  * <a href="http://www.bostonglobe.com/" target="_blank">Boston Globe</a> AJAXifies é uma sub-navegação feita do jeito certo.
  * <a href="http://www.chapman.edu/arts/index.aspx" target="_blank">Chapman University</a>
  * <a href="http://uca.edu/" target="_blank">University of Central Arkansas</a>
  * <a href="http://www.southwales.ac.uk/" target="_blank">University of Glamorgan</a>

## PRIORITY+

<a href="http://bradfrostweb.com/uploads/2012/08/priority2.gif" target="_blank"><img style="width: 550px;height: 467px" title="Padrão Priority+ " alt="Padrão Priority+" src="http://bradfrostweb.com/uploads/2012/08/priority2.gif" /></a>

O <a href="http://justmarkup.com/log/2012/06/19/responsive-multi-level-navigation/" target="_blank">padrão Priority+</a> foi cunhado por <a href="http://justmarkup.com/" target="_blank">Michael Scharnagl</a> (<a href="http://twitter.com/justmarkup" target="_blank">@justmarkup</a>) para descrever uma navegação que exibe os elementos considerados &#8220;mais importantes&#8221; na navegação, ocultando os itens menos relevantes por trás de um link &#8220;more&#8221;. Esses itens somente são revelados quando o usuário clicar neste link.

### Prós

  * **Relativamente simples de implementar** &#8211; A lógica requerida para executar esta técnica não é tão complicada. Basta um comando show/hide para revelar e esconder os itens de navegação.
  * **Expõe as características mais acessadas (é o que a gente acredita)** &#8211; Com isto, esperamos revelar três ou quatro itens que a maioria dos usuários acessam com frequência.

### Contras

  * **Oculta potencialmente importantes itens da navegação** &#8211; o que você julga mais importante pode não ser a opinião do seu usuário. Enterrar itens de navegação significa ter que fazer suposições, e ao mesmo tempo que esperamos ser útil para a maior parte dos usuários, pode irritar a outros.
  * **Não funciona muito bem com a navegação multi-level** &#8211; O modelo priority+ parece bom para navegações que tem muitos itens num mesmo nível de hierarquia, mas infelizmente parece ainda não resolver o dilema da sub-navegação.

### Recursos

<a href="http://justmarkup.com/log/2012/06/19/responsive-multi-level-navigation/" target="_blank">Navegação Responsiva Multi Level – Vamos tentar!</a>

<a href="http://justmarkup.com/lab/juma/nav/example2/" target="_blank">Priority+ Demo</a>

### Na web

<a href="http://www.wm.edu/" target="_blank">William and Mary</a>

As <a href="http://m.usatoday.com/sports" target="_blank">section pages do site mobile do USA Today</a> não seguem exatamente esta proposta, mas exibem as categorias mais importantes por padrão, e uma seta revela os itens de navegação restantes. Bastante atrativo.

## OFF-CANVAS FLYOUT

<a href="http://bradfrostweb.com/uploads/2012/08/nav-obama.png" target="_blank"><img title="Navegação Left Flyout do site do Barack Obama" alt="nav-obama" src="http://bradfrostweb.com/uploads/2012/08/nav-obama-650x295.png" width="573" height="260" /></a>

O menu off-canvas flyout revela uma coluna de navegação. Os itens do sub-menu podem ser tantos quanto o comprimento da própria página, por isso há espaço de sobra para uma longa e/ou complexa navegação. Como já escrevi sobre o <a href="http://bradfrostweb.com/blog/web/responsive-nav-patterns/#left" target="_blank">modelo flyout left</a> antes, vou poupá-los da análise de prós e contras. Em vez disso, estou disponibilizando uma lista de referências para modelos off-canvas.

### Recursos para off-canvas

  * <a href="http://www.lukew.com/ff/entry.asp?1517" target="_blank">Off Canvas Multi-Device Layout</a>
  * <a href="http://www.lukew.com/ff/entry.asp?1569" target="_blank">Off Canvas Multi-Device Layouts</a>
  * <a href="http://jasonweaver.name/lab/offcanvas/" target="_blank">Off-Canvas demo por Jason Weaver</a>
  * <a href="http://zurb.com/playground/off-canvas-layouts" target="_blank">Off Canvas Layouts na Zurb Foundation</a>

### Na web

  * <a href="https://www.facebook.com/" target="_blank">Facebook’s mobile site</a>

## CAROUSEL+

<img style="width: 494px;height: 523px" alt="Carousel+ Pattern" src="http://bradfrostweb.com/uploads/2012/08/Screen-shot-2012-08-27-at-12.47.20-PM.png" />

Este é o menu da moda. O padrão Carousel+ é um carrossel contendo uma categoria principal com opções de sub-navegação exibidas na parte inferior. O usuário pode deslizar horizontalmente pelas opções de navegação ou usar as setas (direita/esquerda) para mover-se pelo carrosel.

### Prós

  * **Relativamente atraente** &#8211; Esta é certamente uma solução única e elegante para navegações mais complexas.
  * **Funciona bem com touch screens** &#8211; A capacidade de deslizar por um pequeno carrossel é uma interação muito legal, e é eficiente no sentido de conseguir &#8216;chegar aonde você quer&#8217;.

### Contras

  * **Não exibe todas as categorias** &#8211; Assim como o modelo Priority+, o modelo Carousel+ requer uma interação antes de o usuário poder compreender todas as opções disponíveis.
  * **Pesado em dispositivos non-touch** &#8211; Ter um carrossel deslizante é ótimo, mas ainda existem muitos ambientes e dispositivos que não suportam eventos touch JavaScript. Para esses ambientes, o usuário terá que recorrer a setas que avançam uma categoria de cada vez, o que pode ser bem entendiante.
  * **Não é recomendado para navegação multi-level** &#8211; Este padrão funciona bem quando a sub-navegação tem apenas um nível. Mas, não é escalável além disso.
  * **Questões de proximidade entre a navegação principal e a sub-navegação** &#8211; A distância entre os itens do primeiro nível da navegação e da sub-navegação é muito pequena. Não fica muito legal. Sei lá, talvez seja só pra mim.

### Na web

  * <a href="http://m.intel.com/us/en/home.html" target="_blank">Site mobile da Intel</a> &#8211; Sim, sei que não é responsivo, mas não significa que este padrão não possa ser usado em um ambiente responsivo<a id="anchornota1" href="#nota1" name="achornota1"><sup>1</sup></a>.

## ADIANTE!

Não importa o que você faça, ajustar uma navegação complexa e multi-level para small screens é algo difícil. Lembre-se de priorizar a busca, e de subtrair o que for possível antes de embarcar na implementação de uma navegação complexa. Essa coleção de padrões de navegação não está tão abrangente, por isso fique a vontade para sugerir outras soluções interessantes que você já viu.

<a id="nota1" name="nota1"></a>1 &#8211; Nota do tradutor: O site da Intel agora é responsivo, e utiliza um outro padrão de menu. Mantive este link apenas para ser fiel a tradução. Vocês podem observar este padrão de menu pela imagem que abre a seção _Carousel+_. [voltar ao texto][1]

&#8212;

_Artigo traduzido com autorização de <a href="http://bradfrostweb.com/" target="_blank">Brad Frost</a>._

_Artigo original escrito por <a href="http://bradfrostweb.com/" target="_blank">Brad Frost</a>._

_Acesse o artigo original em <a href="http://bradfrostweb.com/blog/web/complex-navigation-patterns-for-responsive-design/" target="_blank">Brad Frost Web &#8211; &#8220;Complex Navigation Pattern for Responsive Design&#8221; &#8211; 27 de agosto de 2012</a>._

&#8212;

&nbsp;

 [1]: #anchornota1