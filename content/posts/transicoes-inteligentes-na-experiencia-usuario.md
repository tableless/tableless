---
title: Transições inteligentes na experiência do usuário
author: Raphael Fabeni
type: post
date: 2013-12-16
excerpt: Alguns websites superam outros, seja em seu conteúdo, usabilidade, design, funcionalidades, etc. Detalhes do design de interação e animação fazem uma diferença fundamental em websites modernos. Vamos compartilhar algumas lições tiradas de vários modelos e analisar por que esses simples padrões funcionam tão bem.
url: /transicoes-inteligentes-na-experiencia-usuario/
categories:
  - Artigos
  - Design
  - Traduções
  - UX
tags:
  - experiência do usuário
  - Técnicas e Práticas
  - usabilidade
  - ux

---
As novas propriedades do CSS3 nos surpreendem cada vez mais. Não só pelo fato de terem simplificado muitas coisas (só quem lembra do trabalho para se fazer uma borda arredondada ou sombra em um elemento entende o quão úteis são algumas propriedades), mas também pelo poder que nos deu de enriquecermos a experiência do usuário. Se você ainda não está por dentro dessa maravilha, [confira mais artigos sobre CSS3][1].

Um dia, navegando pela _interwebs_, achei esse [artigo][2] do [Adrian Zumbrunnen][3] no site da Smashing Magazine. Gostei bastante do conteúdo e resolvi traduzi-lo pra gente.

A idéia era a tradução ao pé da letra, mas em alguns casos de expressões que ficariam estranhas no português, deixei em inglês mesmo (algumas que inclusive estamos mais acostumados a usar). Vamos lá&#8230;

—

Alguns websites superam outros, seja em seu conteúdo, usabilidade, design, funcionalidades, etc. Detalhes do design de interação e animação fazem uma diferença fundamental em websites modernos. Vamos compartilhar algumas lições tiradas de vários modelos e analisar por que esses simples padrões funcionam tão bem.

Quando desenhamos/projetamos produtos digitais, nós frequentemente utilizamos aplicações digitais como Photoshop e Sketch. A maioria das pessoas que já estão no mercado por alguns anos, obviamente sabem que design é muito mais que apenas apresentação visual. Ainda assim, muitos continuam a criar interfaces com design estático. [Steve Jobs uma vez disse][4] sobre design:

> &#8220;Design não é apenas o que parece e o que se sente. Design é como funciona.&#8221;

Nossa experiência e impressão de um produto são formadas por uma combinação de fatores, com a interação desempenhando um papel fundamental. Não podemos mais pensar em interfaces de usuário com design estático e adicionar a mágica da interação depois. Em vez disso, precisamos abraçar a natureza interativa da web desde o início e pensar na interação como componente natural.

Vejamos alguns exemplos em que a interação inteligente, definida pela animação sutil, melhora suavemente a experiência do usuário.

## Scroll Animado

A benção e a maldição da web são os hiperlinks. Quando você clica em um link, isso pode levá-lo a qualquer lugar, da página de um produto para o site da loja do velho e assustador fantoche no fim da rua. O resultado é a perda de contexto.

Uma das grandes características sobre a experiência do usuário de livros é a linearidade. Cada capítulo em um livro baseia-se no anterior. Você deve ler o capítulo um para poder entender o capítulo dois. Quando você pula um capítulo, você está ciente de que pode perder algo e, assim não obter algum conhecimento sobre o conteúdo subseqüente. Na web, e principalmente em websites longos, isso muitas vezes acontece inconscientemente. Ao adicionar um scroll animado, podemos consertar isso:

<img class="alignnone size-full wp-image-39940" alt="scroll-animado" src="http://tableless.com.br/uploads/2013/12/scroll-animado.gif" width="500" height="580" />

Compare a imagem anterior com essa:

<img class="alignnone size-full wp-image-39943" alt="scroll-sem-animacao" src="http://tableless.com.br/uploads/2013/12/scroll-sem-animacao.gif" width="500" height="580" />

Compare o comportamento padrão dos links (âncoras) com o comportamento animado. Pular conteúdo não é mais uma ação inconsciente; é uma decisão. O site [Hope Lies at 24 Frames Per Second][5] tem um botão de menu para a sua versão móvel que envia o usuário para o topo da página, sem qualquer animação. Levei mais de um minuto para descobrir o que realmente tinha acontecido.

**Leve em conta:** Mudanças bruscas em uma interface são difíceis para os usuários entenderem. Não deixe-os no escuro, sempre mostre o que está acontecendo.

## Alternância de estados

Como vimos no último exemplo, transições ajudam os usuários a entender o ritmo e o fluxo de uma interface. Nada parece mais artificial do que uma mudança brusca, pois **mudanças bruscas simplesmente não existem no mundo real**. Vamos olhar outro exemplo: _menus que se alternam (toggle menus)_. Usuários associam o ícone de &#8220;_mais_&#8221; (+) com a ação de adicionar conteúdo ou expandir um elemento. Girando o ícone em 45°, o &#8220;_mais_&#8221; (+) torna-se uma &#8220;_xis_&#8221; (x), um elemento de interface amplamente entendido como _fechar_.

<img class="alignnone size-full wp-image-39944" alt="Stateful-toggle" src="http://tableless.com.br/uploads/2013/12/Stateful-toggle.gif" width="500" height="580" />

Essa simples transição muda completamente o significado do ícone. Esse pequeno detalhe faz a diferença entre ter que adivinhar o que vai acontecer a seguir e saber o que o ícone significa em cada estado. Se você me perguntar, essa alternância é bastante _&#8220;amigável&#8221; (user-friendly_). Além disso, observe que o ícone de &#8220;_mais_&#8221; sempre gira na mesma direção que o conteúdo, reforçando o fluxo de informações.

**Leve em conta:** Faça os elementos de interface do seu website compreensíveis em cada estado.

## Formulários e comentários recolhidos (_collapsed_)

Os formulários de comentários em vários blogs e sites de notícias não são os elementos mais bonitos de um website. Por que? Bem, a maioria deles não são um tanto amigáveis, certo? Quando você está prestes a postar um comentário, você só quer começar a escrever o comentário em si e nada mais. Ao invés disso, um formulário padrão de comentários lhe pede todos os tipos de outras coisas primeiro. É irritante.

Para motivarmos as pessoas a comentarem mais, nós podemos _recolher_ (_collapse_) o formulário e **só mostrarmos o elemento mais crucial: o campo de comentário**. Quando o usuário clica no campo, você pode expandir o formulário. Um exemplo no mundo real dessa revelação progressiva pode ser encontrado na versão beta do site do New York Times:

<img class="alignnone size-full wp-image-39945" alt="NY-Times" src="http://tableless.com.br/uploads/2013/12/NY-Times.gif" width="530" height="592" />

Você pode ir até mais longe, definindo o foco do cursor no campo de comentario quando o formulário se expandir. Porém, essa abordagem tem um problema: um princípio fundamental do design de interação é que **uma ação deve acontecer próxima ao local da onde a interação ocorre** (próximo ao local de atenção). Podemos então ir um passo além, e animar o campo de comentário para orientar o usuário:

<img class="alignnone size-full wp-image-39946" alt="ExpandingComments" src="http://tableless.com.br/uploads/2013/12/ExpandingComments.gif" width="500" height="580" />

Você pode até fixar o campo de comentário no topo, expandi-lo nesse sentido e exibir os campos adicionais abaixo dele.

Como você pode ver, isso reduz a desordem e faz com que o formulário de comentário seja mais convidativo. Mas, e se _&#8220;recolhermos&#8221; (collapsing)_ todo os comentários anteriores também?

Recolhendo os comentários, nós temos a barra de rolagem para representar o comprimento do artigo (conteúdo) em si, ao invés da página inteira (com os comentários expandidos). Uma prática comum é a de carregar automaticamente os comentários quando o usuário chega ao fim de uma página. Devemos evitar forçar o usuário a clicar a menos que haja uma boa razão para isso.

**Leve em conta:** Exibição progressiva a fim de reduzir os componentes de interface do usuário à sua essência. Revele funcionalidades de acordo com que os usuários precisem delas.

## Puxe para atualizar

Uma das interações mais interessantes a surgir logo após a introdução do iPhone foi o &#8220;_puxar para atualizar (pull to refresh)_&#8220;, iniciada por Loren Brichter. Ela permite ao usuário atualizar o conteúdo de rolagem que esteja disposto numa ordem cronológica reversa. Você pode ver esse conceito em ação no aplicativo do Twitter. Uma vez que você deslizou para o topo da lista de tweets, deslize um pouco mais para atualizar a _timeline_.

<img class="alignnone size-full wp-image-39947" alt="Twitter" src="http://tableless.com.br/uploads/2013/12/Twitter.gif" width="240" height="360" />

Por que isso funciona tão bem? Antes do &#8220;_puxar para atualizar_&#8221; existir, os usuários tinham que apertar o botão de atualizar nos navegadores para carregar mais conteúdo. Ao juntar o desejo do usuário de encontrar mais conteúdo com a ação de atualizar, a necessidade de uma ação explícita tornou-se obsoleta.

**Leve em conta:** Ao ligar inteção com ação, a experiência torna-se mais transparente.

## Sticky Labels

_Sticky labels_ são uma outra sutil, mas útil combinação de um componente de interface e uma transição significativa. Confira o uso desta técnica no [portfólio][6] da Edenspiekermann.

<img class="alignnone size-full wp-image-39948" alt="Sticky-Label" src="http://tableless.com.br/uploads/2013/12/Sticky-Label.gif" width="500" height="580" />

As _labels_ de projeto deslizam juntamente com o conteúdo, proporcionando assim contexto para as imagens à direita, até o próximo projeto aparecer. Este comportamento é semelhante ao livro de endereços no iOS e é especialmente útil para fornecer contextos em seções longas. A transição oferece uma melhor orientação e descrições fáceis baseadas no contexto.

**Leve em conta:** Use _sticky labels_ para seções longas em que as descrições ou títulos adicionam informações valiosas ao conteúdo que não cabe na _viewport_.

## Affordance transition

O conceito de _affordance_ deriva da psicologia cognitiva e refere-se às características particulares de um objeto que guia o espectador.

No contexto de UI design, o [glossário de usabilidade][7] (PDF) do website da EU, define-o assim:

> &#8220;_Affordance_ é uma propriedade desejável de uma interface de usuário &#8211; software que, naturalmente, leva as pessoas a tomarem as medidas corretas para realizarem seus objetivos.&#8221;

_Ridges (detalhes?)_ são muitas vezes utilizados para melhorar a _affordance_. _Ridges_ em torno de um botão sugerem que este pode ser manipulado. Esta técnica de UX foi amplamente popularizada pelo aplicativo da câmera no iOS.

<img class="alignnone size-full wp-image-39949" alt="iOS_Lockscreen-500-final" src="http://tableless.com.br/uploads/2013/12/iOS_Lockscreen-500-final.jpg" width="500" height="750" srcset="uploads/2013/12/iOS_Lockscreen-500-final.jpg 500w, uploads/2013/12/iOS_Lockscreen-500-final-112x168.jpg 112w, uploads/2013/12/iOS_Lockscreen-500-final-206x310.jpg 206w" sizes="(max-width: 500px) 100vw, 500px" />

Os traços (_ripples_) em torno do botão de câmera na tela de bloqueio do iOS 6, sugerem a idéia do botão ser arrastável. A Apple removeu-os no iOS 7, aparentemente porque os usuários se acostumaram a isso, tornando o ícone mais parecido com um botão independente. Porém, o que acontece é ainda a mesma coisa: quando você arrasta o botão, a tela de bloqueio revela a câmera por baixo. Essa é uma grande técnica para apontar os usuários para os recursos em uma interface.

**Leve em conta:** Dê aos elementos uma alta _affordance_ para apontar os usuários para os recursos em uma interface.

## Ocultar com base no contexto

O Google Chrome no iOS teve o a ação de ocultar baseada no contexto desde que foi lançado. Veja na imagem a seguir:

<img class="alignnone size-full wp-image-39950" alt="CBH" src="http://tableless.com.br/uploads/2013/12/CBH.gif" width="500" height="580" />

A idéia básica é que os controles de navegação se escondam automaticamente uma vez que o usuário rolar a página para baixo. Assim que o usuário rolar a página para cima novamente, os controles reaparecem. Essa abordagem tanto melhora a experiência contextual (com foco no conteúdo em si) como aumenta o espaço da tela. Esse último, claro, particularmente importante em dispositivos móveis.

A premissa é que os **usuários vão fluir com o conteúdo que estão consumindo**. Logo que eles pararem esse fluxo, uma mudança de contexto provavelmente seja necessária; assim, os controles de navegação reaparecem. Embora essa técnica economize espaço de tela, verifique se essa premissa é válida no seu caso.

O iOS levou isso a um passo adiante. Quando você chega ao fim de uma página, os controles de navegação se expandem novamente. Isso é um bom exemplo de incorporação dinâmica das necessidades do usuário em uma interface.

**Leve em conta:** Use a ação de ocultar baseada no contexto para melhorar o foco do usuário e economizar espaço na tela.

## Transição do foco

Há cerca de uma semana atrás, Nikita Vasilyev, uma UI designer de Toronto, teve uma idéia bem legal. Ela desenvolveu um script que anima elementos que recebem foco. Embora ainda seja um projeto experimental, o conceito é bastante interessante. Dê uma olhada no [vídeo][8]. (E por favor, coloque seus fones de ouvido &#8211; a música é épica).

Ao navegar pelo teclado, muitas vezes não fica claro pro usuário para onde o foco mudou após pressionar a tecla Tab. A animação aponta-os para o lugar certo na página. A transição é sútil mas tem um grande impacto em orientar o usuário.

**Leve em conta:** Oriente o usuário, independentemente de como eles navegam.

## Conclusão

Esses são apenas alguns exemplos, entre muitos outros por aí. A questão não é mostrar as mais recentes e extravagantes técnicas de interação, mas sim destacar como pequenos detalhes de interação podem melhorar significativamente a experiência do usuário.

Se nós estamos a projetar melhores produtos digitais, então **temos que desafiar nossas crenças atuais** e ver como padrões de interação podem, potencialmente, facilitar a vida do usuário. Eu não estou dizendo que devemos reinventar a roda, mas seria muito ingênuo pararmos de explorar. Então, saia da sua zona de conforto. Continue explorando e testando.

Se você gostou desse artigo, você pode [me seguir][9] no Twitter ou se juntar a mim para comer uma barra de chocolate suiço na Suíça.

Que padrões de transição você achou especialmente útil nos seus projetos?

—

Texto traduzido e adaptado do [As novas propriedades do CSS3 nos surpreendem cada vez mais. Não só pelo fato de terem simplificado muitas coisas (só quem lembra do trabalho para se fazer uma borda arredondada ou sombra em um elemento entende o quão úteis são algumas propriedades), mas também pelo poder que nos deu de enriquecermos a experiência do usuário. Se você ainda não está por dentro dessa maravilha, [confira mais artigos sobre CSS3][1].

Um dia, navegando pela _interwebs_, achei esse [artigo][2] do [Adrian Zumbrunnen][3] no site da Smashing Magazine. Gostei bastante do conteúdo e resolvi traduzi-lo pra gente.

A idéia era a tradução ao pé da letra, mas em alguns casos de expressões que ficariam estranhas no português, deixei em inglês mesmo (algumas que inclusive estamos mais acostumados a usar). Vamos lá&#8230;

—

Alguns websites superam outros, seja em seu conteúdo, usabilidade, design, funcionalidades, etc. Detalhes do design de interação e animação fazem uma diferença fundamental em websites modernos. Vamos compartilhar algumas lições tiradas de vários modelos e analisar por que esses simples padrões funcionam tão bem.

Quando desenhamos/projetamos produtos digitais, nós frequentemente utilizamos aplicações digitais como Photoshop e Sketch. A maioria das pessoas que já estão no mercado por alguns anos, obviamente sabem que design é muito mais que apenas apresentação visual. Ainda assim, muitos continuam a criar interfaces com design estático. [Steve Jobs uma vez disse][4] sobre design:

> &#8220;Design não é apenas o que parece e o que se sente. Design é como funciona.&#8221;

Nossa experiência e impressão de um produto são formadas por uma combinação de fatores, com a interação desempenhando um papel fundamental. Não podemos mais pensar em interfaces de usuário com design estático e adicionar a mágica da interação depois. Em vez disso, precisamos abraçar a natureza interativa da web desde o início e pensar na interação como componente natural.

Vejamos alguns exemplos em que a interação inteligente, definida pela animação sutil, melhora suavemente a experiência do usuário.

## Scroll Animado

A benção e a maldição da web são os hiperlinks. Quando você clica em um link, isso pode levá-lo a qualquer lugar, da página de um produto para o site da loja do velho e assustador fantoche no fim da rua. O resultado é a perda de contexto.

Uma das grandes características sobre a experiência do usuário de livros é a linearidade. Cada capítulo em um livro baseia-se no anterior. Você deve ler o capítulo um para poder entender o capítulo dois. Quando você pula um capítulo, você está ciente de que pode perder algo e, assim não obter algum conhecimento sobre o conteúdo subseqüente. Na web, e principalmente em websites longos, isso muitas vezes acontece inconscientemente. Ao adicionar um scroll animado, podemos consertar isso:

<img class="alignnone size-full wp-image-39940" alt="scroll-animado" src="http://tableless.com.br/uploads/2013/12/scroll-animado.gif" width="500" height="580" />

Compare a imagem anterior com essa:

<img class="alignnone size-full wp-image-39943" alt="scroll-sem-animacao" src="http://tableless.com.br/uploads/2013/12/scroll-sem-animacao.gif" width="500" height="580" />

Compare o comportamento padrão dos links (âncoras) com o comportamento animado. Pular conteúdo não é mais uma ação inconsciente; é uma decisão. O site [Hope Lies at 24 Frames Per Second][5] tem um botão de menu para a sua versão móvel que envia o usuário para o topo da página, sem qualquer animação. Levei mais de um minuto para descobrir o que realmente tinha acontecido.

**Leve em conta:** Mudanças bruscas em uma interface são difíceis para os usuários entenderem. Não deixe-os no escuro, sempre mostre o que está acontecendo.

## Alternância de estados

Como vimos no último exemplo, transições ajudam os usuários a entender o ritmo e o fluxo de uma interface. Nada parece mais artificial do que uma mudança brusca, pois **mudanças bruscas simplesmente não existem no mundo real**. Vamos olhar outro exemplo: _menus que se alternam (toggle menus)_. Usuários associam o ícone de &#8220;_mais_&#8221; (+) com a ação de adicionar conteúdo ou expandir um elemento. Girando o ícone em 45°, o &#8220;_mais_&#8221; (+) torna-se uma &#8220;_xis_&#8221; (x), um elemento de interface amplamente entendido como _fechar_.

<img class="alignnone size-full wp-image-39944" alt="Stateful-toggle" src="http://tableless.com.br/uploads/2013/12/Stateful-toggle.gif" width="500" height="580" />

Essa simples transição muda completamente o significado do ícone. Esse pequeno detalhe faz a diferença entre ter que adivinhar o que vai acontecer a seguir e saber o que o ícone significa em cada estado. Se você me perguntar, essa alternância é bastante _&#8220;amigável&#8221; (user-friendly_). Além disso, observe que o ícone de &#8220;_mais_&#8221; sempre gira na mesma direção que o conteúdo, reforçando o fluxo de informações.

**Leve em conta:** Faça os elementos de interface do seu website compreensíveis em cada estado.

## Formulários e comentários recolhidos (_collapsed_)

Os formulários de comentários em vários blogs e sites de notícias não são os elementos mais bonitos de um website. Por que? Bem, a maioria deles não são um tanto amigáveis, certo? Quando você está prestes a postar um comentário, você só quer começar a escrever o comentário em si e nada mais. Ao invés disso, um formulário padrão de comentários lhe pede todos os tipos de outras coisas primeiro. É irritante.

Para motivarmos as pessoas a comentarem mais, nós podemos _recolher_ (_collapse_) o formulário e **só mostrarmos o elemento mais crucial: o campo de comentário**. Quando o usuário clica no campo, você pode expandir o formulário. Um exemplo no mundo real dessa revelação progressiva pode ser encontrado na versão beta do site do New York Times:

<img class="alignnone size-full wp-image-39945" alt="NY-Times" src="http://tableless.com.br/uploads/2013/12/NY-Times.gif" width="530" height="592" />

Você pode ir até mais longe, definindo o foco do cursor no campo de comentario quando o formulário se expandir. Porém, essa abordagem tem um problema: um princípio fundamental do design de interação é que **uma ação deve acontecer próxima ao local da onde a interação ocorre** (próximo ao local de atenção). Podemos então ir um passo além, e animar o campo de comentário para orientar o usuário:

<img class="alignnone size-full wp-image-39946" alt="ExpandingComments" src="http://tableless.com.br/uploads/2013/12/ExpandingComments.gif" width="500" height="580" />

Você pode até fixar o campo de comentário no topo, expandi-lo nesse sentido e exibir os campos adicionais abaixo dele.

Como você pode ver, isso reduz a desordem e faz com que o formulário de comentário seja mais convidativo. Mas, e se _&#8220;recolhermos&#8221; (collapsing)_ todo os comentários anteriores também?

Recolhendo os comentários, nós temos a barra de rolagem para representar o comprimento do artigo (conteúdo) em si, ao invés da página inteira (com os comentários expandidos). Uma prática comum é a de carregar automaticamente os comentários quando o usuário chega ao fim de uma página. Devemos evitar forçar o usuário a clicar a menos que haja uma boa razão para isso.

**Leve em conta:** Exibição progressiva a fim de reduzir os componentes de interface do usuário à sua essência. Revele funcionalidades de acordo com que os usuários precisem delas.

## Puxe para atualizar

Uma das interações mais interessantes a surgir logo após a introdução do iPhone foi o &#8220;_puxar para atualizar (pull to refresh)_&#8220;, iniciada por Loren Brichter. Ela permite ao usuário atualizar o conteúdo de rolagem que esteja disposto numa ordem cronológica reversa. Você pode ver esse conceito em ação no aplicativo do Twitter. Uma vez que você deslizou para o topo da lista de tweets, deslize um pouco mais para atualizar a _timeline_.

<img class="alignnone size-full wp-image-39947" alt="Twitter" src="http://tableless.com.br/uploads/2013/12/Twitter.gif" width="240" height="360" />

Por que isso funciona tão bem? Antes do &#8220;_puxar para atualizar_&#8221; existir, os usuários tinham que apertar o botão de atualizar nos navegadores para carregar mais conteúdo. Ao juntar o desejo do usuário de encontrar mais conteúdo com a ação de atualizar, a necessidade de uma ação explícita tornou-se obsoleta.

**Leve em conta:** Ao ligar inteção com ação, a experiência torna-se mais transparente.

## Sticky Labels

_Sticky labels_ são uma outra sutil, mas útil combinação de um componente de interface e uma transição significativa. Confira o uso desta técnica no [portfólio][6] da Edenspiekermann.

<img class="alignnone size-full wp-image-39948" alt="Sticky-Label" src="http://tableless.com.br/uploads/2013/12/Sticky-Label.gif" width="500" height="580" />

As _labels_ de projeto deslizam juntamente com o conteúdo, proporcionando assim contexto para as imagens à direita, até o próximo projeto aparecer. Este comportamento é semelhante ao livro de endereços no iOS e é especialmente útil para fornecer contextos em seções longas. A transição oferece uma melhor orientação e descrições fáceis baseadas no contexto.

**Leve em conta:** Use _sticky labels_ para seções longas em que as descrições ou títulos adicionam informações valiosas ao conteúdo que não cabe na _viewport_.

## Affordance transition

O conceito de _affordance_ deriva da psicologia cognitiva e refere-se às características particulares de um objeto que guia o espectador.

No contexto de UI design, o [glossário de usabilidade][7] (PDF) do website da EU, define-o assim:

> &#8220;_Affordance_ é uma propriedade desejável de uma interface de usuário &#8211; software que, naturalmente, leva as pessoas a tomarem as medidas corretas para realizarem seus objetivos.&#8221;

_Ridges (detalhes?)_ são muitas vezes utilizados para melhorar a _affordance_. _Ridges_ em torno de um botão sugerem que este pode ser manipulado. Esta técnica de UX foi amplamente popularizada pelo aplicativo da câmera no iOS.

<img class="alignnone size-full wp-image-39949" alt="iOS_Lockscreen-500-final" src="http://tableless.com.br/uploads/2013/12/iOS_Lockscreen-500-final.jpg" width="500" height="750" srcset="uploads/2013/12/iOS_Lockscreen-500-final.jpg 500w, uploads/2013/12/iOS_Lockscreen-500-final-112x168.jpg 112w, uploads/2013/12/iOS_Lockscreen-500-final-206x310.jpg 206w" sizes="(max-width: 500px) 100vw, 500px" />

Os traços (_ripples_) em torno do botão de câmera na tela de bloqueio do iOS 6, sugerem a idéia do botão ser arrastável. A Apple removeu-os no iOS 7, aparentemente porque os usuários se acostumaram a isso, tornando o ícone mais parecido com um botão independente. Porém, o que acontece é ainda a mesma coisa: quando você arrasta o botão, a tela de bloqueio revela a câmera por baixo. Essa é uma grande técnica para apontar os usuários para os recursos em uma interface.

**Leve em conta:** Dê aos elementos uma alta _affordance_ para apontar os usuários para os recursos em uma interface.

## Ocultar com base no contexto

O Google Chrome no iOS teve o a ação de ocultar baseada no contexto desde que foi lançado. Veja na imagem a seguir:

<img class="alignnone size-full wp-image-39950" alt="CBH" src="http://tableless.com.br/uploads/2013/12/CBH.gif" width="500" height="580" />

A idéia básica é que os controles de navegação se escondam automaticamente uma vez que o usuário rolar a página para baixo. Assim que o usuário rolar a página para cima novamente, os controles reaparecem. Essa abordagem tanto melhora a experiência contextual (com foco no conteúdo em si) como aumenta o espaço da tela. Esse último, claro, particularmente importante em dispositivos móveis.

A premissa é que os **usuários vão fluir com o conteúdo que estão consumindo**. Logo que eles pararem esse fluxo, uma mudança de contexto provavelmente seja necessária; assim, os controles de navegação reaparecem. Embora essa técnica economize espaço de tela, verifique se essa premissa é válida no seu caso.

O iOS levou isso a um passo adiante. Quando você chega ao fim de uma página, os controles de navegação se expandem novamente. Isso é um bom exemplo de incorporação dinâmica das necessidades do usuário em uma interface.

**Leve em conta:** Use a ação de ocultar baseada no contexto para melhorar o foco do usuário e economizar espaço na tela.

## Transição do foco

Há cerca de uma semana atrás, Nikita Vasilyev, uma UI designer de Toronto, teve uma idéia bem legal. Ela desenvolveu um script que anima elementos que recebem foco. Embora ainda seja um projeto experimental, o conceito é bastante interessante. Dê uma olhada no [vídeo][8]. (E por favor, coloque seus fones de ouvido &#8211; a música é épica).

Ao navegar pelo teclado, muitas vezes não fica claro pro usuário para onde o foco mudou após pressionar a tecla Tab. A animação aponta-os para o lugar certo na página. A transição é sútil mas tem um grande impacto em orientar o usuário.

**Leve em conta:** Oriente o usuário, independentemente de como eles navegam.

## Conclusão

Esses são apenas alguns exemplos, entre muitos outros por aí. A questão não é mostrar as mais recentes e extravagantes técnicas de interação, mas sim destacar como pequenos detalhes de interação podem melhorar significativamente a experiência do usuário.

Se nós estamos a projetar melhores produtos digitais, então **temos que desafiar nossas crenças atuais** e ver como padrões de interação podem, potencialmente, facilitar a vida do usuário. Eu não estou dizendo que devemos reinventar a roda, mas seria muito ingênuo pararmos de explorar. Então, saia da sua zona de conforto. Continue explorando e testando.

Se você gostou desse artigo, você pode [me seguir][9] no Twitter ou se juntar a mim para comer uma barra de chocolate suiço na Suíça.

Que padrões de transição você achou especialmente útil nos seus projetos?

—

Texto traduzido e adaptado do][10] escrito pelo [Adrian Zumbrunnen][3] em 23 de outubro de 2013.

Tradução autorizada pela [Smashing Magazine][11].

Qualquer erro ou sugestão de melhoria na tradução, é bem vinda! 🙂

 [1]: http://tableless.com.br/?s=css3
 [2]: http://uxdesign.smashingmagazine.com/2013/10/23/smart-transitions-in-user-experience-design/ "Smart transitions in user experience design"
 [3]: https://twitter.com/webchaeschtli "Perfil do twitter"
 [4]: http://www.nytimes.com/2003/11/30/magazine/30IPOD.html?pagewanted=all
 [5]: http://hopelies.com/
 [6]: http://edenspiekermann.com/projects
 [7]: http://ec.europa.eu/regional_policy/archive/country/commu/docevent/26112008/5_doulgerof_glossary.pdf
 [8]: http://www.youtube.com/watch?v=MyIE9vjy8Zo
 [9]: https://twitter.com/webchaeschtli
 [10]: http://uxdesign.smashingmagazine.com/2013/10/23/smart-transitions-in-user-experience-design/
 [11]: http://www.smashingmagazine.com/