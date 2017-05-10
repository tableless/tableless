---
title: Redução Progressiva
author: Dani Guerrato
type: post
date: 2013-09-11
excerpt: 'Entenda como criar interfaces que se adaptam automaticamente de acordo com o perfil de uso do usuário. '
url: /reducao-progressiva/
dsq_thread_id: 1742636788
categories:
  - Artigos
  - UX

---
## O Problema

<p dir="ltr">
  Quando apresentamos uma interface nova, principalmente quando este processo envolve uma experiência ou forma de interação diferente do usual, é normal guiarmos o usuário pela mão com dicas, tutoriais e legendas óbvias. Embora, dependendo do público alvo, este processo seja útil no início, com o passar do tempo e ganho óbvio de proficiência todas aquelas informações acabam se tornando, no mínimo, desnecessárias e na maior parte do tempo irritantes.
</p>

<p dir="ltr">
  Um bom exemplo são os tutoriais de videogames. Quem curte jogos provavelmente já passou pela experiência de querer começar a história sem ter como pular os tutoriais. A maior parte dos jogos compartilha os mesmos controles, ou seja, você já sabe como andar, mudar o ângulo da câmera, pular, conversar… tudo o que você quer é que o tutorial acabe logo para poder salvar o mundo (ou destrui-lo) sozinho. E parte desta experiência as vezes inclui descobrir as coisas por conta própria. O mesmo acontece com interfaces de sites, softwares ou aplicativos. As vezes ajuda demais pode ser inconveniente. Aqueles que são mais velhos certamente vão se lembrar dos assistentes do pacote Office entre 1997/2007.   Não sei quem foi o designer que decidiu que um clipe de papel deveria fornecer ajuda o tempo todo para os usuários. O que ele conseguiu na prática foi criar um dos mascotes mais odiados da era digital. A maior parte das dicas eram óbvias e irrelevantes.
</p>

<p dir="ltr">
  <img class="alignnone size-full wp-image-38918" alt="clippy" src="http://tableless.com.br/uploads/2013/09/clippy.jpg" width="660" height="400" srcset="uploads/2013/09/clippy.jpg 660w, uploads/2013/09/clippy-277x168.jpg 277w, uploads/2013/09/clippy-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />
</p>

<p dir="ltr">
  O exemplo é antigo, mas o problema de ajuste de dificuldade não foi resolvido. É só ver a evolução dos softwares da própria Microsoft. Ao modificar radicalmente a interface padrão do Windows na versão 8 a empresa conquistou os corações dos usuários mais experientes… Mas minha tia me liga desesperada cada vez que não consegue encontrar o botão iniciar no layout novo. E ela não foi a única. Tanto que na versão 8.1 o botão iniciar estará de volta ao sistema. A pergunta central aqui é: considerando que cada usuário tem sua própria velocidade de aprendizado como determinar qual é a quantidade de ajuda necessária?  E se este nível de proficiência evolui com o tempo, uso e interesse individual por que a experiência de navegação permanece igual o tempo todo?
</p>

## Redução Progressiva

<p dir="ltr">
  Bem, foi pensando nestas questões que o pessoal da <a title="Progressive Reduction" href="http://layervault.tumblr.com/post/42361566927/progressive-reduction">Layer Vault</a> criou o conceito de Progressive Reduction, ou Redução Progressiva. A ideia principal do artigo é que usabilidade não é um conceito estático. Da mesma forma que o design responsivo otimiza o layout para diferentes tipos de mídia, interfaces também deveriam se adequar as necessidades de cada usuário. E isto pode ser feito reduzindo o ênfase ou espaço de alguns elementos conforme o uso. Um botão composto de ícone + legenda com o tempo poderia ganhar um destaque menor com cores mais discretas até se transformar em apenas um ícone.
</p>

<p dir="ltr">
  <a href="http://layervault.tumblr.com/post/42361566927/progressive-reduction"><img class="alignnone size-full wp-image-38916" alt="progressive-reduction" src="http://tableless.com.br/uploads/2013/09/progressive-reduction.jpg" width="660" height="400" srcset="uploads/2013/09/progressive-reduction.jpg 660w, uploads/2013/09/progressive-reduction-277x168.jpg 277w, uploads/2013/09/progressive-reduction-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" /></a>
</p>

## O estado atual do design digital

<p dir="ltr">
  Com o crescente uso de dispositivos móveis é cada vez mais importante decidir qual conteúdo merece ou não espaço. O mesmo acontece com elementos de design. As tendências minimalistas e flat estão em super alta. E com elas vieram a cultura de redução. As interfaces estão mais objetivas, sem esqueumorfismos ou floreios desnecessários.
</p>

<p dir="ltr">
  Um bom termômetro para mudanças de design são os blogs. Estes micro-sites carregam sempre um aspecto mais pessoal e experimental que os grandes sites corporativos e, portanto, são ótimos laboratórios de observação de tendências. Anos atrás os usuários lotavam blogs com todo tipo de informações. Sidebars gigantes com mais widgets, banners e elementos aleatórios do que conteúdo propriamente dito. A grande tendência do momento são blogs de uma única coluna de texto. Mais um reflexo da cultura de redução. Mas decidir o quanto reduzir ainda causa dúvida. O ícone de três linhas tipo sanduíche que ganhou fama em interfaces móveis aos poucos vem surgindo como um padrão também para navegação desktop. Será que os usuários de maneira geral estão preparados para isto? Eu, você, e outras pessoas que usam constantemente smartphones não vão sentir dificuldade alguma. Mas quem não usa? Tentar adivinhar o público alvo com base em dados demográficos é o melhor que temos até agora. Mas a redução progressiva pode ser o equilibrio entre entregar a clareza e objetividade que os usuários mais avançados precisam, sem perder a visita do pessoal menos experiente. O ícone poderia vir acompanhado de uma label &#8220;menu&#8221; e a partir de um certo ponto (determinado pelo número de cliques) o rótulo sumir e apenas o ícone permanecer. Desta forma presenteamos os usuários experientes com uma navegação mais objetiva, sem punir quem está procurando pelo menu pela primeira vez.
</p>

## Na prática

<p dir="ltr">
  O ícone é um exemplo claro, mas em teoria a Redução Progressiva pode ser aplicada a qualquer elemento da user interface. Podemos projetar variações de tamanho, cor, forma, contraste, rótulo, enfim, são inúmeras as possibilidades de modificação. Eventualmente poderemos criar interfaces mais avançadas, focadas no usuário &#8220;profissional&#8221; sem se preocupar tanto com a curva de aprendizado dos iniciantes.
</p>

<p dir="ltr">
  Os <a title="Implementing progressive reduction" href="http://layervault.tumblr.com/post/42442865260/implementing-progressive-reduction">exemplos práticos da Layer Vault</a>  estão estruturados em Ruby on Rails, mas não seria difícil adaptar o conceito para outras linguagens de programação. Já a variação de layouts em si é facilmente criada através de folhas de estilo com uma ajudinha de pré-processadores.
</p>

## Declínio de Experiência

<p dir="ltr">
  Dizem que ninguém esquece como andar de bicicleta, mas infelizmente esta regra não vale para tudo. Em algumas situações a proficiência de uso pode diminuir ao invés de aumentar. Isto acontece, por exemplo, quando você faz um curso de línguas e não tem com quem praticar. O mesmo vale para interfaces. Se você passa muitos anos sem entrar em um determinado site ou abrir aquele aplicativo, é natural demorar um tempinho a mais para se situar e se acostumar com o posicionamento e diagramação dos elementos. É como se fosse a primeira vez que você estivesse utilizando aquele serviço. É importante, portanto, nos casos de redução progressiva se preocupar com estes usuários que perderam experiência. Isto pode ser feito a partir de estágios diferentes de user interface. Da mesma forma que com o uso frequente você passa da interface nível 1 para a nível 2, se não utiliza o serviço por algumas semanas o layout deverá regredir para o nível 1 novamente. O eixo de complexidade sempre se modifica de acordo com as necessidades do usuário partindo para uma interface mais assistida conforme o declínio de experiência. Em resumo: se você usa muito o aplicativo a UI saí da frente do seu caminho, se você usa pouco recebe mais ajuda. Desta maneira você cria interfaces efetivas para usuários iniciantes e avançados, frequentes e não frequentes.
</p>

## O outro lado da moeda

<p dir="ltr">
  O conceito central da Redução Progressiva é auxiliar o usuário, &#8220;profissional&#8221; ou não, a chegar até o seu objetivo de maneira rápida e eficiente. É importante, no entanto, que as mudanças sejam sutis o suficiente para não causar mais problemas do que melhorias. No caso do Layer Vault as mudanças ocorrem automaticamente, sem qualquer tipo de notificação ou aviso. Existe um certo debate quanto a eficacia deste método do ponto de vista da psicologia. Para reduzir a probabilidade de aversão a mudança uma possível solução seria prover ao usuário uma maneira de voltar atrás. Isto pode ser feito através de um painel de controle onde ele pode escolher voltar para o início, reverter os estágios da interface ou até travar o layout em um determinado estágio, por exemplo. Isto colocaria o usuário que porventura sentisse dificuldade com o novo estágio de volta no controle.
</p>

## Conclusão

O conceito de Regressão Progressiva tem gerado tanto buzz que dividiu opiniões de designers, desenvolvedores e profissionais de UX sendo alvo de [críticas alarmistas][1] e [elogios empolgados][2]. A idéia não é exatamente inédita. Existe até mesmo uma tentativa de registro de [patente da Samsung][3] de dezembro de 2011 relatando um conceito parecido.

[<img class="alignnone size-full wp-image-38915" alt="patente-samsung" src="http://tableless.com.br/uploads/2013/09/patente-samsung.jpg" width="660" height="727" srcset="uploads/2013/09/patente-samsung.jpg 660w, uploads/2013/09/patente-samsung-152x168.jpg 152w, uploads/2013/09/patente-samsung-281x310.jpg 281w" sizes="(max-width: 660px) 100vw, 660px" />][4]

Esta documentação versa especificamente sobre ícones de interfaces gráficas que mudam de tamanho conforme frequência de uso. A patente está em contestação por que, bem, existem registros mais antigos de interfaces adaptáveis neste sentido&#8230; Não é exatamente uma idéia nova. Mas o artigo do Layer Vault foi o primeiro a descrever o conceito, apresentar bons argumentos e até mesmo alguns exemplos de implementação. O interessante do método é que pela primeira vez o usuário está no centro da mudança. O timing não poderia ser melhor. Em teoria isto pode ser algo tão revolucionário quanto o design responsivo foi para dispositivos móveis ou apenas tempestade em copo d&#8217;agua. A efetividade em si só poderá ser posta a prova empiricamente: implementando a Regressão Progressiva em projetos e testando extensivamente. Por maior que seja o debate entre desenvolvedores, designers e psicólogos quem vai dizer se a idéia funciona na prática ou não, como sempre, são os próprios usuários.

 [1]: http://azumbrunnen.me/blog/progressive-reduction-just-another-buzzword/ "Progressive reduction just another buzzword"
 [2]: http://alistapart.com/blog/post/progressive-reductionmodify-your-ui-over-time "Progressive reductionmodify your ui over time"
 [3]: http://patents.stackexchange.com/questions/4233/user-interface-changing-icon-appearance-based-on-frequency-of-use-samsung "User interface changing icon appearance based on frequency of use samsung"
 [4]: http://patents.stackexchange.com/questions/4233/user-interface-changing-icon-appearance-based-on-frequency-of-use-samsung