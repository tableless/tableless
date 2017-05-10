---
title: Design para telas sensíveis ao toque
author: Dani Guerrato
type: post
date: 2013-08-05
excerpt: Conheça quais são as técnicas, padrões e principais desafios para o desenvolvimento de aplicativos nativos e interfaces web touch screen.
url: /design-para-telas-sensiveis-ao-toque/
dsq_thread_id: 1572169895
categories:
  - Artigos
  - Design
  - Mobile
tags:
  - 2013
  - design
  - tablets
  - toque
  - touchscreen

---
A popularização das telas sensíveis ao toque adicionou uma esfera completamente nova ao design de interfaces: a experiência tátil. Este é um trabalho bem diferente do que nós designers e desenvolvedores estávamos acostumados até então, já que a possibilidade de utilizar esta nova forma de toque permite ao usuário interagir diretamente com a informação como se estivesse manipulando dados com propriedades físicas. Este novo universo de possibilidades, embora fascinante, também trouxe novos desafios.

## Um novo conjunto de metáforas

Todo o webdesign como conhecemos hoje é baseado em metáforas. Utilizamos botões por que são a coisa do mundo real mais próxima de algo que &#8220;ativa&#8221;. Chamamos links de âncoras. E browsers de janelas. Com o advento de dispositivos capazes de responder ao toque as metáforas de interface mudam. Botões, menus e abas tradicionais se tornam secundários, dando lugar a formas de navegação muitas vezes mais físicas do que visuais. Um vocabulário de gestos foi criado para lidar com este novo paradigma. Mas ainda faltam padrões claros para lidarmos com estas novas situações. Para criar novas metáforas precisamos observar como os usuários interagem com seus brinquedos eletrônicos para assim determinar o melhor caminho para a criação de layouts, tanto para aplicativos nativos quanto para a internet. No fim são as pessoas &#8211; e sua maneiras preferidas de engajar ações &#8211; que ditam as regras, não os designers.

## Smartphones

Cada pessoa segura seu celular de maneira única. Mas, para generalizar, existem três grupos de pegadas básicas: segurar o celular com uma mão e tocar a tela com a outra, segurar o telefone com as duas mãos e usar a ponta dos dedões para teclar e &#8211; a pegada Mestra &#8211; segurar e teclar com uma mesma mão. Esta última é a mais comum. [Segundo uma pesquisa realizada por profissionais de UX][1] 49% das pessoas segura o telefone desta maneira. E não é a toa. É libertador utilizar apenas uma mão pois você pode fazer outras coisas com a outra&#8230; Por outro lado isto também é limitador pois boa parte da tela fica coberta. A dica que fica para os designers é utilizar controles primários no arco formado a partir do canto inferior, já que a área superior é mais difícil de alcançar.

<img class="alignnone size-full wp-image-38273" alt="area-segura-iphone" src="http://tableless.com.br/uploads/2013/07/area-segura-iphone.jpg" width="660" height="600" srcset="uploads/2013/07/area-segura-iphone.jpg 660w, uploads/2013/07/area-segura-iphone-184x168.jpg 184w, uploads/2013/07/area-segura-iphone-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Já reparou que a maior parte da navegação de aplicativos nativos fica justamente na parte de inferior da tela? Está aí a explicação!

<img class="alignnone size-full wp-image-38277" alt="android-home" src="http://tableless.com.br/uploads/2013/07/android-home.jpg" width="660" height="600" srcset="uploads/2013/07/android-home.jpg 660w, uploads/2013/07/android-home-184x168.jpg 184w, uploads/2013/07/android-home-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Alias este tipo de diagramação conteúdo no topo, controles embaixo não é comum apenas em aplicativos de smartphones. Diversos outros aparelhos como calculadoras, balanças e iPods também partem deste mesmo princípio de design.

Quanto a direção &#8211; direita ou esquerda &#8211; não é algo que possa ser previsto com precisão. Existe uma grande variação na pegada, inclusive entre pessoas canhotas e destras. Na dúvida: coloque a navegação em uma posição que favoreça as duas mãos. Deixar o botão principal na posição central ou utilizar inputs com 100% de largura para formulário de login são boas práticas.

O Aplicativo do Instagram, por exemplo, deixa a função principal &#8211; tirar fotos &#8211; no centro.

<img class="alignnone size-full wp-image-38270" alt="instagram" src="http://tableless.com.br/uploads/2013/07/instagram.jpg" width="660" height="600" srcset="uploads/2013/07/instagram.jpg 660w, uploads/2013/07/instagram-184x168.jpg 184w, uploads/2013/07/instagram-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

De posse destes dados fica muito mais fácil hierarquizar informações. Deixe os botões mais importantes embaixo e as opções menos frequentes no topo. Alias, a parte de cima da tela é uma área ótima para opções que podem alterar significativamente os dados como editar ou deletar. Já que é uma região mais difícil de alcançar você evita que o usuário encoste acidentalmente e apague algo importante.

A tela de configurações do iPhone, por exemplo, deixa as opções editáveis no canto superior direito.

### E para sites?

Websites são aplicativos que funcionam dentro de outro aplicativo: o navegador. Posicionar a navegação de sites no canto inferior pode ser um problema, pois a localização pode conflitar com a barra do browser (pelo menos no caso do Safari e IE, por exemplo) criando uma pilha enorme de controles. Isto é o pesadelo dos dedos gordinhos! Outro fator que conta pontos contra colocar navegação embaixo para sites é: nem todos os navegadores aceitam position: fixed. Ou seja, &#8220;sticky-footers&#8221; estão fora de questão por enquanto&#8230;

Deixar a lista de links aberta no topo também pode ser uma estratégia perigosa. Dependendo da quantidade de opções da sua página isto pode ofuscar completamente o conteúdo. A melhor prática de navegação, neste caso, é colapsar o menu em apenas uma âncora. Este tipo de abordagem pode ser facilmente criada utilizando JavaScript ou CSS3. Se você precisa de uma ajudinha o plugin [Responsive Nav][2] dá conta do recado.

<img class="alignnone size-full wp-image-38271" alt="responsive-nav" src="http://tableless.com.br/uploads/2013/07/responsive-nav.jpg" width="660" height="600" srcset="uploads/2013/07/responsive-nav.jpg 660w, uploads/2013/07/responsive-nav-184x168.jpg 184w, uploads/2013/07/responsive-nav-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Uma outra abordagem, ainda mais simples, é deixar a navegação no rodapé da página (sem ser fixa). Assim você dá ao usuário o que ele quer ver primeiro: o conteúdo.

## Tablets

Lembra das três pegadas básicas de smartphones? Esqueça elas por aqui! A ergonomia de um tablet é completamente diferente&#8230; O modo de segurar vai depender de outros fatores, incluindo a postura. A mesma pessoa pode segurar um tablet de uma maneira completamente diferente se estiver sentada, deitada ou de pé. Os tamanhos dos dispositivos também variam muito (iPad mini estou falando com você) e isto também vai influenciar a pegada. Mas a tendência é segurarmos o aparelho sempre pelas laterais e obedecermos a sequência de leitura tradicional no ocidente. Ou seja, da esquerda para a direita de cima para baixo. Podemos ainda apoiar o tablet em um suporte próprio ou até mesmo no próprio corpo ao deitar. Isto significa que, ao contrário dos smartphones, a parte de baixo é a área menos favorecida para controles. Ela pode ser obscurecida por cobertores ou pelas barrigas de nossos amigos leitores.

A posição mais confortável para menus acaba sendo nos cantos superiores, já que ficam próximos aos dedões. A área do meio neste caso deve ser evitada já que para alcança-la é necessário cobrir a tela com o braço, ofuscando o conteúdo.

<img class="alignnone size-full wp-image-38272" alt="area-segura-ipad" src="http://tableless.com.br/uploads/2013/07/area-segura-ipad.jpg" width="660" height="600" srcset="uploads/2013/07/area-segura-ipad.jpg 660w, uploads/2013/07/area-segura-ipad-184x168.jpg 184w, uploads/2013/07/area-segura-ipad-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Para outros tipos de controles (principalmente os que afetam o conteúdo a ser exibido imediantamente no canvas) o ideal é que fiquem mesmo na parte de baixo. Isto vale para o caso de navegação por thumbnails, por exemplo.

## Aparelhos Híbridos

Com a evolução da tecnologia já é comum aparelhos que misturam funcionalidades de tablets e notebooks. Neste caso a preferência do usuário vai ser utilizar os tradicionais teclado e mouse na maior parte do tempo, certo? Errado! [Segundo um estudo realizado pela Intel][3] quando oferecidas as duas opções de inputs os usuários preferem utilizar o toque. A idéia desta pesquisa era observar pessoas realizando tarefas corriqueiras como criar um arquivo de PowerPoint, escrever um e-mail, realizar uma compra online, etc e o toque foi a maneira preferida de interação em 77% dos casos. Isto acontece por que o toque é algo natural, orgânico mesmo. E, segundo os entrevistados, mais divertido!

A tendência, nestes casos, é segurar o aparelho pelas laterais. Isto evita o cansaço dos braços, já que assim eles descansam na superfície do dispositivo. A melhor localização para a navegação, para o caso de aparelhos híbridos, é na área próxima aos cantos inferiores e lados da tela. É por conta disto que a interface touch do Windows 8, por exemplo, possui tantos gestos ativados pelas laterais.

## Teste teste teste!

Lembre-se que estas regras são linhas gerais e não devem ser tomadas como verdades imutáveis. Mesmo dentro de uma mesma &#8220;pegada&#8221; existem formas diferentes e dificuldades individuais de acordo com o tamanho, forma e alcance dos dedos (e do aparelho). A Apple foi uma que errou por generalizar. A antena do iPhone 4 foi alvo de critícas pois sofria interferência se acordo com a maneira que o usuário segurava o aparelho. A resposta do então CEO da empresa Steve Jobs foi bem clara: &#8220;Não segure desta maneira&#8221;. É difícil agradar todos, mas nem todas as empresas possuem fãs suficientes para dar este tipo de resposta&#8230; Então, na dúvida, teste a navegação em diferentes pegadas. Ou melhor, recrute algumas pessoas para realizar uma experiência rápida e observe como cada um interage com a interface. É nesta hora que você vai descobrir o que funciona e o que pode ser melhorado.

## E o design responsivo?

Bem, a tendência para o futuro é que mais e mais aparelhos desktop ofereçam telas sensíveis ao toque. Não podemos mais cair na armadilha de acreditar automaticamente que, se alguém está utilizando uma tela grande, ela não é touch. A formulinha desktop = mouse, smartphone = touch não se aplica mais. Felizmente em breve teremos Media Queries especificamente para solucionar este problema&#8230; O que fazer até lá?

Bem, na dúvida, parta do pressuposto que sim, o seu usuário está navegando de uma tela sensível ao toque. Uma boa prática é não deixar nenhuma função fundamental depender de ações do tipo hover, já que este tipo de comportamento não existe em touch screens. Trate todas a partir de agora como um aprimoramento progressivo&#8230; Outra dica é manter a navegação nos cantos superiores. Desta maneira o seu site fica optimizado para desktops, tablets e hibridos. No caso de smartphones, utilize menus colapsados. E tenha certeza que todos os objetos tocáveis são largos o suficiente para acomodar dedos&#8230;

## Qual é o tamanho de item ideal para o toque?

O tamanho médio das telas pode variar muito, mas o tamanho médio da ponta de um dedo é relativamente o mesmo. [Um estudo realizado no MIT][4] concluiu que a largura média da ponta dos dedos de um ser humano é de 1.6 a 2 cm. Tendo isto em mente algumas empresas fabricantes de sistemas operacionais tentaram estabelecer um valor mínimo para toque. Segundo o [Guia de Interface da Apple][5] 44 pixels é o tamanho mínimo para elementos da interface tocáveis. Isto significa navegação, inputs, botões, enfim&#8230; O guia de estilo do Windows 8 vai um pouco além: 50 pixels. Acha que é grande demais? Segundo a Microsoft corrigir um um erro demora mais de dois gestos ou cinco segundos. É melhor garantir que as pessoas acertem da primeira vez já que erros sucessivos são uma verdadeira receita para frustração&#8230;

O fato de precisarmos colocar botões grandes nos leva a uma questão: como colocar mais botões em um menor espaço? A verdade é: você não pode! Mas tente encarar isto pelo lado bom&#8230; Ter menos espaço significa ser obrigado a repensar alguns conceitos para criar interfaces mais objetivas. As vezes a alternativa mais simples pode ser a mais efetiva.

Mas se você absolutamente precisa de objetos menores tente manter uma das dimensões (altura ou largura) em 44 pixels. A própria Apple faz isto em seus teclados, já que seria impossível inserir toda a sequência QUERTY no tamanho ideal. A dimensão efetiva das teclas, neste caso, fica em 44 x 30 pixels.

Para games a coisa é um pouco diferente. Como alguns controles são utilizados especificamente pelos dedões o ideal é ter uma área de toque maior. Algo por volta de 72 pixels é suficiente.

Outro fator importante é a densidade de pixels. As medidas aqui apresentadas são apenas uma base para você ter em mente ao projetar layouts. Pixels só existem, bem, dentro de uma tela. E são valores relativos a cada aparelho&#8230; Para telas em HD lembre-se de ajustar o tamanho dos elementos já que o que importa neste caso é o espaço físico ocupado pelo dedo e não a resolução da tela&#8230; A calculadora [T+L Density Converter][6] pode ajudar na matemática.

Pixels podem ajudar na hora de criar e desenvolver layouts, mas é importante ter como referência medidas do mundo real. Certifique-se de testar se o tamanho do seu botão, ícone, elemento, etc tem pelo menos 1.6 a 2 cm quadrados.

## Crie alvos perceptíveis

Não basta apenas criar um botões gigantes, o seu usuário precisa entender de alguma forma que aqueles elementos podem ser tocados. Para isto é importante utilizar uma tipografia legível e desenvolver elementos que apresentem algum tipo de contraste como cor, traçado, forma, etc com relação ao restante da interface.

Outra boa prática é desenvolver algum comportamento para ser aplicado no momento de ativação. Isto pode variar entre uma sombra interna em um botão ou até mesmo um movimento ou animação leve. Desta maneira seu usuário sabe que sua ação teve resultado e &#8220;alguma coisa está prestes a acontecer&#8221;. Você pode fazer isto facilmente através de CSS com a pseudo-classe :active.

Lembre-se também de cuidar do espaço entre os elementos da interface. Uma regra boa para se ter em mente é: quanto mais elementos mais espaço você vai precisar entre eles. Assim você evita criar layous visualmente poluídos, ou pior, difíceis de utilizar.

## Utilize gestos

A lei de Fitts é um modelo do movimento humano utilizado em ergonomia para prever o tempo necessário para mover-se rapidamente de uma posição até a outra. E o que esta lei diz basicamente é algo que você pode já ter concluido sozinho: quanto menor e mais longe estiver um objeto, mais dificil vai ser de atingi-lo. É por isto que o centro de um alvo de arco-e-flecha vale 100 pontos. É fisicamente mais dificil de atingir&#8230; E isto também vale para itens clicáveis em um browser ou a serem tocados em uma tela. E, seguindo esta lógica, é mais fácil e requer menos coordenação motora fazer gestos como varrer a tela completa com os dedos do que tocar em botões pequenos. Uma boa prática portanto é oferecer alterativas gestuais para controles. No iPad você pode puxar a interface para baixo para carregar mais tweets no aplicativo do Twitter ou juntar os cinco dedos para deixar o aplicativo. Pense em gestos como o equivalente a atalhos de teclado&#8230; Lembre-se, no entanto, de não depender exclusivamente de gestos para realizar todas as ações. Um usuário com alguma dificuldade visual ou motora pode preferir utilizar comandos de voz, por exemplo. Em aplicativos nativo os gestos mais comuns são: toque, toque longo, toque duplo, varrer e pinçar.

Utilizar características físicas do mundo real como inercia e gravidade transformam a interface em algo tangível, dando um senso maior de realidade para objetos virtuais. Quando usados de maneira inteligente os gestos podem criar uma experiência verdadeiramente imersiva. No aplicativo de desenho Paper 53 é possível apagar itens realizando movimentos circulares anti-horários e refazer ações em movimentos circulares horários. A impressão é que podemos controlar o tempo, avançando e voltando sem precisar procurar uma borracha e interromper o ato de desenhar. O aplicativo nem é dos mais completos em termos de paleta de opções, mas seu fluxo de trabalho é tão gostoso que Paper 53 acabou sendo um grande sucesso.

<img class="alignnone size-full wp-image-38276" alt="paper53" src="http://tableless.com.br/uploads/2013/07/paper53.jpg" width="660" height="495" srcset="uploads/2013/07/paper53.jpg 660w, uploads/2013/07/paper53-224x168.jpg 224w, uploads/2013/07/paper53-413x310.jpg 413w" sizes="(max-width: 660px) 100vw, 660px" />

### A busca por um padrão

Alguns gestos já são bem estabelecidos. Por repetição frequente, em diversos aplicativos os movimentos de pinça já estão associados inconscientemente a opção de zoom, por exemplo. Mas isto não é uma regra fixa. Não existe nenhum tipo de padronização entre gestos e funções. Cada desenvolvedor faz o que quer, utilizando os mesmos movimentos com objetivos diferentes em cada aplicativo e isto pode acabar gerando uma super confusão. Para piorar a situação outro problema é a falta de padronização entre as referências visuais de gestos. Para interfaces &#8220;classicas&#8221; o usuário padrão sabe que ao clicar em um ícone de casinha você irá para a página inicial ou que um xis representa fechar uma janela. Mas, até hoje, não existe nenhum padrão universal coerente de representação de gestos. Algumas iniciativas como [A popularização das telas sensíveis ao toque adicionou uma esfera completamente nova ao design de interfaces: a experiência tátil. Este é um trabalho bem diferente do que nós designers e desenvolvedores estávamos acostumados até então, já que a possibilidade de utilizar esta nova forma de toque permite ao usuário interagir diretamente com a informação como se estivesse manipulando dados com propriedades físicas. Este novo universo de possibilidades, embora fascinante, também trouxe novos desafios.

## Um novo conjunto de metáforas

Todo o webdesign como conhecemos hoje é baseado em metáforas. Utilizamos botões por que são a coisa do mundo real mais próxima de algo que &#8220;ativa&#8221;. Chamamos links de âncoras. E browsers de janelas. Com o advento de dispositivos capazes de responder ao toque as metáforas de interface mudam. Botões, menus e abas tradicionais se tornam secundários, dando lugar a formas de navegação muitas vezes mais físicas do que visuais. Um vocabulário de gestos foi criado para lidar com este novo paradigma. Mas ainda faltam padrões claros para lidarmos com estas novas situações. Para criar novas metáforas precisamos observar como os usuários interagem com seus brinquedos eletrônicos para assim determinar o melhor caminho para a criação de layouts, tanto para aplicativos nativos quanto para a internet. No fim são as pessoas &#8211; e sua maneiras preferidas de engajar ações &#8211; que ditam as regras, não os designers.

## Smartphones

Cada pessoa segura seu celular de maneira única. Mas, para generalizar, existem três grupos de pegadas básicas: segurar o celular com uma mão e tocar a tela com a outra, segurar o telefone com as duas mãos e usar a ponta dos dedões para teclar e &#8211; a pegada Mestra &#8211; segurar e teclar com uma mesma mão. Esta última é a mais comum. [Segundo uma pesquisa realizada por profissionais de UX][1] 49% das pessoas segura o telefone desta maneira. E não é a toa. É libertador utilizar apenas uma mão pois você pode fazer outras coisas com a outra&#8230; Por outro lado isto também é limitador pois boa parte da tela fica coberta. A dica que fica para os designers é utilizar controles primários no arco formado a partir do canto inferior, já que a área superior é mais difícil de alcançar.

<img class="alignnone size-full wp-image-38273" alt="area-segura-iphone" src="http://tableless.com.br/uploads/2013/07/area-segura-iphone.jpg" width="660" height="600" srcset="uploads/2013/07/area-segura-iphone.jpg 660w, uploads/2013/07/area-segura-iphone-184x168.jpg 184w, uploads/2013/07/area-segura-iphone-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Já reparou que a maior parte da navegação de aplicativos nativos fica justamente na parte de inferior da tela? Está aí a explicação!

<img class="alignnone size-full wp-image-38277" alt="android-home" src="http://tableless.com.br/uploads/2013/07/android-home.jpg" width="660" height="600" srcset="uploads/2013/07/android-home.jpg 660w, uploads/2013/07/android-home-184x168.jpg 184w, uploads/2013/07/android-home-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Alias este tipo de diagramação conteúdo no topo, controles embaixo não é comum apenas em aplicativos de smartphones. Diversos outros aparelhos como calculadoras, balanças e iPods também partem deste mesmo princípio de design.

Quanto a direção &#8211; direita ou esquerda &#8211; não é algo que possa ser previsto com precisão. Existe uma grande variação na pegada, inclusive entre pessoas canhotas e destras. Na dúvida: coloque a navegação em uma posição que favoreça as duas mãos. Deixar o botão principal na posição central ou utilizar inputs com 100% de largura para formulário de login são boas práticas.

O Aplicativo do Instagram, por exemplo, deixa a função principal &#8211; tirar fotos &#8211; no centro.

<img class="alignnone size-full wp-image-38270" alt="instagram" src="http://tableless.com.br/uploads/2013/07/instagram.jpg" width="660" height="600" srcset="uploads/2013/07/instagram.jpg 660w, uploads/2013/07/instagram-184x168.jpg 184w, uploads/2013/07/instagram-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

De posse destes dados fica muito mais fácil hierarquizar informações. Deixe os botões mais importantes embaixo e as opções menos frequentes no topo. Alias, a parte de cima da tela é uma área ótima para opções que podem alterar significativamente os dados como editar ou deletar. Já que é uma região mais difícil de alcançar você evita que o usuário encoste acidentalmente e apague algo importante.

A tela de configurações do iPhone, por exemplo, deixa as opções editáveis no canto superior direito.

### E para sites?

Websites são aplicativos que funcionam dentro de outro aplicativo: o navegador. Posicionar a navegação de sites no canto inferior pode ser um problema, pois a localização pode conflitar com a barra do browser (pelo menos no caso do Safari e IE, por exemplo) criando uma pilha enorme de controles. Isto é o pesadelo dos dedos gordinhos! Outro fator que conta pontos contra colocar navegação embaixo para sites é: nem todos os navegadores aceitam position: fixed. Ou seja, &#8220;sticky-footers&#8221; estão fora de questão por enquanto&#8230;

Deixar a lista de links aberta no topo também pode ser uma estratégia perigosa. Dependendo da quantidade de opções da sua página isto pode ofuscar completamente o conteúdo. A melhor prática de navegação, neste caso, é colapsar o menu em apenas uma âncora. Este tipo de abordagem pode ser facilmente criada utilizando JavaScript ou CSS3. Se você precisa de uma ajudinha o plugin [Responsive Nav][2] dá conta do recado.

<img class="alignnone size-full wp-image-38271" alt="responsive-nav" src="http://tableless.com.br/uploads/2013/07/responsive-nav.jpg" width="660" height="600" srcset="uploads/2013/07/responsive-nav.jpg 660w, uploads/2013/07/responsive-nav-184x168.jpg 184w, uploads/2013/07/responsive-nav-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Uma outra abordagem, ainda mais simples, é deixar a navegação no rodapé da página (sem ser fixa). Assim você dá ao usuário o que ele quer ver primeiro: o conteúdo.

## Tablets

Lembra das três pegadas básicas de smartphones? Esqueça elas por aqui! A ergonomia de um tablet é completamente diferente&#8230; O modo de segurar vai depender de outros fatores, incluindo a postura. A mesma pessoa pode segurar um tablet de uma maneira completamente diferente se estiver sentada, deitada ou de pé. Os tamanhos dos dispositivos também variam muito (iPad mini estou falando com você) e isto também vai influenciar a pegada. Mas a tendência é segurarmos o aparelho sempre pelas laterais e obedecermos a sequência de leitura tradicional no ocidente. Ou seja, da esquerda para a direita de cima para baixo. Podemos ainda apoiar o tablet em um suporte próprio ou até mesmo no próprio corpo ao deitar. Isto significa que, ao contrário dos smartphones, a parte de baixo é a área menos favorecida para controles. Ela pode ser obscurecida por cobertores ou pelas barrigas de nossos amigos leitores.

A posição mais confortável para menus acaba sendo nos cantos superiores, já que ficam próximos aos dedões. A área do meio neste caso deve ser evitada já que para alcança-la é necessário cobrir a tela com o braço, ofuscando o conteúdo.

<img class="alignnone size-full wp-image-38272" alt="area-segura-ipad" src="http://tableless.com.br/uploads/2013/07/area-segura-ipad.jpg" width="660" height="600" srcset="uploads/2013/07/area-segura-ipad.jpg 660w, uploads/2013/07/area-segura-ipad-184x168.jpg 184w, uploads/2013/07/area-segura-ipad-341x310.jpg 341w" sizes="(max-width: 660px) 100vw, 660px" />

Para outros tipos de controles (principalmente os que afetam o conteúdo a ser exibido imediantamente no canvas) o ideal é que fiquem mesmo na parte de baixo. Isto vale para o caso de navegação por thumbnails, por exemplo.

## Aparelhos Híbridos

Com a evolução da tecnologia já é comum aparelhos que misturam funcionalidades de tablets e notebooks. Neste caso a preferência do usuário vai ser utilizar os tradicionais teclado e mouse na maior parte do tempo, certo? Errado! [Segundo um estudo realizado pela Intel][3] quando oferecidas as duas opções de inputs os usuários preferem utilizar o toque. A idéia desta pesquisa era observar pessoas realizando tarefas corriqueiras como criar um arquivo de PowerPoint, escrever um e-mail, realizar uma compra online, etc e o toque foi a maneira preferida de interação em 77% dos casos. Isto acontece por que o toque é algo natural, orgânico mesmo. E, segundo os entrevistados, mais divertido!

A tendência, nestes casos, é segurar o aparelho pelas laterais. Isto evita o cansaço dos braços, já que assim eles descansam na superfície do dispositivo. A melhor localização para a navegação, para o caso de aparelhos híbridos, é na área próxima aos cantos inferiores e lados da tela. É por conta disto que a interface touch do Windows 8, por exemplo, possui tantos gestos ativados pelas laterais.

## Teste teste teste!

Lembre-se que estas regras são linhas gerais e não devem ser tomadas como verdades imutáveis. Mesmo dentro de uma mesma &#8220;pegada&#8221; existem formas diferentes e dificuldades individuais de acordo com o tamanho, forma e alcance dos dedos (e do aparelho). A Apple foi uma que errou por generalizar. A antena do iPhone 4 foi alvo de critícas pois sofria interferência se acordo com a maneira que o usuário segurava o aparelho. A resposta do então CEO da empresa Steve Jobs foi bem clara: &#8220;Não segure desta maneira&#8221;. É difícil agradar todos, mas nem todas as empresas possuem fãs suficientes para dar este tipo de resposta&#8230; Então, na dúvida, teste a navegação em diferentes pegadas. Ou melhor, recrute algumas pessoas para realizar uma experiência rápida e observe como cada um interage com a interface. É nesta hora que você vai descobrir o que funciona e o que pode ser melhorado.

## E o design responsivo?

Bem, a tendência para o futuro é que mais e mais aparelhos desktop ofereçam telas sensíveis ao toque. Não podemos mais cair na armadilha de acreditar automaticamente que, se alguém está utilizando uma tela grande, ela não é touch. A formulinha desktop = mouse, smartphone = touch não se aplica mais. Felizmente em breve teremos Media Queries especificamente para solucionar este problema&#8230; O que fazer até lá?

Bem, na dúvida, parta do pressuposto que sim, o seu usuário está navegando de uma tela sensível ao toque. Uma boa prática é não deixar nenhuma função fundamental depender de ações do tipo hover, já que este tipo de comportamento não existe em touch screens. Trate todas a partir de agora como um aprimoramento progressivo&#8230; Outra dica é manter a navegação nos cantos superiores. Desta maneira o seu site fica optimizado para desktops, tablets e hibridos. No caso de smartphones, utilize menus colapsados. E tenha certeza que todos os objetos tocáveis são largos o suficiente para acomodar dedos&#8230;

## Qual é o tamanho de item ideal para o toque?

O tamanho médio das telas pode variar muito, mas o tamanho médio da ponta de um dedo é relativamente o mesmo. [Um estudo realizado no MIT][4] concluiu que a largura média da ponta dos dedos de um ser humano é de 1.6 a 2 cm. Tendo isto em mente algumas empresas fabricantes de sistemas operacionais tentaram estabelecer um valor mínimo para toque. Segundo o [Guia de Interface da Apple][5] 44 pixels é o tamanho mínimo para elementos da interface tocáveis. Isto significa navegação, inputs, botões, enfim&#8230; O guia de estilo do Windows 8 vai um pouco além: 50 pixels. Acha que é grande demais? Segundo a Microsoft corrigir um um erro demora mais de dois gestos ou cinco segundos. É melhor garantir que as pessoas acertem da primeira vez já que erros sucessivos são uma verdadeira receita para frustração&#8230;

O fato de precisarmos colocar botões grandes nos leva a uma questão: como colocar mais botões em um menor espaço? A verdade é: você não pode! Mas tente encarar isto pelo lado bom&#8230; Ter menos espaço significa ser obrigado a repensar alguns conceitos para criar interfaces mais objetivas. As vezes a alternativa mais simples pode ser a mais efetiva.

Mas se você absolutamente precisa de objetos menores tente manter uma das dimensões (altura ou largura) em 44 pixels. A própria Apple faz isto em seus teclados, já que seria impossível inserir toda a sequência QUERTY no tamanho ideal. A dimensão efetiva das teclas, neste caso, fica em 44 x 30 pixels.

Para games a coisa é um pouco diferente. Como alguns controles são utilizados especificamente pelos dedões o ideal é ter uma área de toque maior. Algo por volta de 72 pixels é suficiente.

Outro fator importante é a densidade de pixels. As medidas aqui apresentadas são apenas uma base para você ter em mente ao projetar layouts. Pixels só existem, bem, dentro de uma tela. E são valores relativos a cada aparelho&#8230; Para telas em HD lembre-se de ajustar o tamanho dos elementos já que o que importa neste caso é o espaço físico ocupado pelo dedo e não a resolução da tela&#8230; A calculadora [T+L Density Converter][6] pode ajudar na matemática.

Pixels podem ajudar na hora de criar e desenvolver layouts, mas é importante ter como referência medidas do mundo real. Certifique-se de testar se o tamanho do seu botão, ícone, elemento, etc tem pelo menos 1.6 a 2 cm quadrados.

## Crie alvos perceptíveis

Não basta apenas criar um botões gigantes, o seu usuário precisa entender de alguma forma que aqueles elementos podem ser tocados. Para isto é importante utilizar uma tipografia legível e desenvolver elementos que apresentem algum tipo de contraste como cor, traçado, forma, etc com relação ao restante da interface.

Outra boa prática é desenvolver algum comportamento para ser aplicado no momento de ativação. Isto pode variar entre uma sombra interna em um botão ou até mesmo um movimento ou animação leve. Desta maneira seu usuário sabe que sua ação teve resultado e &#8220;alguma coisa está prestes a acontecer&#8221;. Você pode fazer isto facilmente através de CSS com a pseudo-classe :active.

Lembre-se também de cuidar do espaço entre os elementos da interface. Uma regra boa para se ter em mente é: quanto mais elementos mais espaço você vai precisar entre eles. Assim você evita criar layous visualmente poluídos, ou pior, difíceis de utilizar.

## Utilize gestos

A lei de Fitts é um modelo do movimento humano utilizado em ergonomia para prever o tempo necessário para mover-se rapidamente de uma posição até a outra. E o que esta lei diz basicamente é algo que você pode já ter concluido sozinho: quanto menor e mais longe estiver um objeto, mais dificil vai ser de atingi-lo. É por isto que o centro de um alvo de arco-e-flecha vale 100 pontos. É fisicamente mais dificil de atingir&#8230; E isto também vale para itens clicáveis em um browser ou a serem tocados em uma tela. E, seguindo esta lógica, é mais fácil e requer menos coordenação motora fazer gestos como varrer a tela completa com os dedos do que tocar em botões pequenos. Uma boa prática portanto é oferecer alterativas gestuais para controles. No iPad você pode puxar a interface para baixo para carregar mais tweets no aplicativo do Twitter ou juntar os cinco dedos para deixar o aplicativo. Pense em gestos como o equivalente a atalhos de teclado&#8230; Lembre-se, no entanto, de não depender exclusivamente de gestos para realizar todas as ações. Um usuário com alguma dificuldade visual ou motora pode preferir utilizar comandos de voz, por exemplo. Em aplicativos nativo os gestos mais comuns são: toque, toque longo, toque duplo, varrer e pinçar.

Utilizar características físicas do mundo real como inercia e gravidade transformam a interface em algo tangível, dando um senso maior de realidade para objetos virtuais. Quando usados de maneira inteligente os gestos podem criar uma experiência verdadeiramente imersiva. No aplicativo de desenho Paper 53 é possível apagar itens realizando movimentos circulares anti-horários e refazer ações em movimentos circulares horários. A impressão é que podemos controlar o tempo, avançando e voltando sem precisar procurar uma borracha e interromper o ato de desenhar. O aplicativo nem é dos mais completos em termos de paleta de opções, mas seu fluxo de trabalho é tão gostoso que Paper 53 acabou sendo um grande sucesso.

<img class="alignnone size-full wp-image-38276" alt="paper53" src="http://tableless.com.br/uploads/2013/07/paper53.jpg" width="660" height="495" srcset="uploads/2013/07/paper53.jpg 660w, uploads/2013/07/paper53-224x168.jpg 224w, uploads/2013/07/paper53-413x310.jpg 413w" sizes="(max-width: 660px) 100vw, 660px" />

### A busca por um padrão

Alguns gestos já são bem estabelecidos. Por repetição frequente, em diversos aplicativos os movimentos de pinça já estão associados inconscientemente a opção de zoom, por exemplo. Mas isto não é uma regra fixa. Não existe nenhum tipo de padronização entre gestos e funções. Cada desenvolvedor faz o que quer, utilizando os mesmos movimentos com objetivos diferentes em cada aplicativo e isto pode acabar gerando uma super confusão. Para piorar a situação outro problema é a falta de padronização entre as referências visuais de gestos. Para interfaces &#8220;classicas&#8221; o usuário padrão sabe que ao clicar em um ícone de casinha você irá para a página inicial ou que um xis representa fechar uma janela. Mas, até hoje, não existe nenhum padrão universal coerente de representação de gestos. Algumas iniciativas como][7] [Gesture Works Flash][8] tentam organizar a bagaça e criar uma iconografia para cada movimento. Trabalhos como este devem ser divulgados. Apenas com a popularização de um padrão visual de representação poderemos de fato facilitar o uso e aprendizagem para que todos os usuários possam explorar o real valor dos gestos. Até lá&#8230;

## Transforme a aprendizagem em algo divertido!

Cabe a cada desenvolvedor demonstrar &#8211; preferencialmente de uma maneira rápida, em pequenos drops e divertida &#8211; as funções do seu aplicativo. Apenas lembre-se que ninguém gosta de tutoriais. Não tente ensinar tudo de uma vez. Ao invés disto plante pequenas pistas para os usuários que gostam de explorar os detalhes. É algo como aprender a jogar um novo game.Você precisa estimular as pessoas a quererem passar de nível&#8230; Isto pode ser feito com uma animação automática sutil ou até mesmo com um sistema de aprendizagem em etapas. Da mesma maneira que um jogador de um game recebe pontos, itens e conquistas por completar níveis, os usuários de aplicativos também gostam de recompensas. A Dropbox, por exemplo, recompensa o usuário com espaço extra se ele completa algumas etapas de introdução como fazer um tour ou compartilhar uma pasta. É uma forma divertida de ensinar a usar o serviço.

## Não exagere no esqueumorfismo&#8230;

Essa é uma palavra que vem gerando um certo buzz ultimamente. Para quem não sabe, esqueumorfismo é uma técnica de design que copia características necessárias em outros objetos e materiais para fins estéticos.

O aplicativo de calculadora mais antigo do iOS, como demonstrado neste comparativo da revista [Wired][9], é inspirado no visual de um objeto real: a calculadora Braun ET44 de 1977.

<img class="alignnone size-full wp-image-38274" alt="calculator" src="http://tableless.com.br/uploads/2013/07/calculator.jpg" width="660" height="411" srcset="uploads/2013/07/calculator.jpg 660w, uploads/2013/07/calculator-269x168.jpg 269w, uploads/2013/07/calculator-497x310.jpg 497w" sizes="(max-width: 660px) 100vw, 660px" />

Esta é uma técnica que divide opiniões. O iOS usou durante bastante tempo, mas interfaces mais recentes como a do Windows 8 tem optado por elementos sólidos sem texturas. Se você pretende ou não utilizar feltro verde e madeirinha nos seus layouts isto fica a seu critério e eu não vou entrar neste mérito. Só é necessário lembrar de uma coisa: se uma interface lembra um objeto do mundo real ela deve se comportar da mesma maneira. Criou um aplicativo que lembra um livrinho? As pessoas vão querer virar as páginas. Preste bastante atenção neste tipo de comportamento &#8220;intuitivo&#8221; ou você pode acabar frustrando seu usuário mais do que agradando. [E tente não exagerar][10], ok?

As vezes quebrar as barreiras do esqueumorfismo pode dar um ar novo a funções antigas. O aplicativo MyScript Calculator seria uma simples calculadora. A diferença é que você pode escrever os números na tela utilizando a ponta dos dedos ou uma caneta stylus. Através deste mecanismo é muito mais rápido &#8211; e divertido! &#8211; fazer operações matemáticas. O aplicativo ainda utiliza referências do mundo real (papel quadriculado), mas sem ficar preso as limitações de uma calculadora física.

<img class="alignnone size-full wp-image-38275" alt="script-calculator" src="http://tableless.com.br/uploads/2013/07/script-calculator.jpg" width="660" height="495" srcset="uploads/2013/07/script-calculator.jpg 660w, uploads/2013/07/script-calculator-224x168.jpg 224w, uploads/2013/07/script-calculator-413x310.jpg 413w" sizes="(max-width: 660px) 100vw, 660px" />

## Conclusão

Apesar das dicas apresentadas aqui serem um bom caminho inicial, ainda não existem padrões fixos e definitivos para telas sensíveis ao toque. Mas isto é uma coisa boa, certo? Nos dá espaço para criar, testar e desenvolver a desde a fundação nossas próprias regras do jogo. É claro que devemos levar em conta muitos dos aspecto lógicos. Não dá para fugir do que é uma questão de física, matemática e ergonomia&#8230; Mas ainda existe muito espaço para debate e experimentação neste cenário em evolução permanente que é a internet. É necessário constantemente reinventar conceitos e expandir horizontes para criar sempre a melhor experiência para os usuários. E é isto que faz da profissão webdesigner algo tão desafiador. E divertido!

## Saiba mais:

[Designing for Touch &#8211; The Mobile Book &#8211; Josh Clark][11]
  
[Finger-Friendly Design: Ideal Mobile Touchscreen Target Sizes][12]
  
[How Do Users Really Hold Mobile Devices?][1]
  
[Responsive Navigation: Optimizing for Touch Across Devices][13]
  
[Common Misconceptions About Touch][14]

 [1]: http://www.uxmatters.com/mt/archives/2013/02/how-do-users-really-hold-mobile-devices.php
 [2]: http://responsive-nav.com/ "Responsive Nav"
 [3]: http://software.intel.com/en-us/articles/the-human-touch-building-ultrabook-applications-in-a-post-pc-age/
 [4]: http://touchlab.mit.edu/publications/2003_009.pdf
 [5]: https://developer.apple.com/library/ios/#documentation/UserExperience/Conceptual/MobileHIG/UEBestPractices/UEBestPractices.html#//apple_ref/doc/uid/TP40006556-CH20-SW1
 [6]: http://www.teehanlax.com/tools/density/
 [7]: http://www.lukew.com/ff/entry.asp?1071
 [8]: http://gestureworks.com/pages/flash-features-gestures
 [9]: http://www.wired.com/gadgetlab/2007/07/iphones-design/
 [10]: http://skeu.it/
 [11]: https://shop.smashingmagazine.com/the-mobile-book-digital-edition.html
 [12]: http://uxdesign.smashingmagazine.com/2012/02/21/finger-friendly-design-ideal-mobile-touchscreen-target-sizes/
 [13]: http://www.lukew.com/ff/entry.asp?1649
 [14]: http://www.uxmatters.com/mt/archives/2013/03/common-misconceptions-about-touch.php