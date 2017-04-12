---
title: Anotações sobre Progressive Web Apps
author: Everton de Paula
type: post
date: 2017-01-24
url: /anotacoes-sobre-progressive-web-apps/
categories:
  - Artigos
  - Código

---
A idéia de escrever sobre Progressive Web Apps surgiu quando estudava para apresentar uma talk sobre o conceito ao pessoal do trabalho, percebi durante o processo que existe muito conteúdo bom pela internet afora, porém senti que alguns conceitos estavam separados uns dos outros, então decidi escrever um documento agrupando todos estes dados que encontrei espalhados por aí para facilitar a compreensão e a forma que iria passar isto para minha equipe. Depois de todo trabalho de pesquisa tive a idéia, porque não compartilhar isto com as pessoas? Altamente incentivado pelos colegas de trabalho, resolvi revisar o documento e postar para os leitores do tableless, acredito que vai ser uma boa base para iniciantes no assunto. Fica aqui uma observação antes de começarmos, não tenho nenhuma intenção e escrever um documento canônico sobre Progressive Web Apps, como verão a seguir é um assunto em construção e em constante evolução, muitas coisas que gostaríamos de usar ainda estão sendo definidas pela comunidade. Agora estamos prontos para começar, espero que gostem 🙂 .  

## Conceitos e motivações

  Pesquisando sobre Progressive Web Apps &#8211; (PWA) percebemos que não é um conceito ou uma especificação única, são na verdade um conjunto de idéias que foram agrupadas com com o intuito de promover uma melhor experiência para o usuário mobile para os usuários, resolvendo alguns problemas que um “simples” site responsivo não poderia resolver. PWAs criam uma aproximação dos usuários já fidelizados, aqueles usuários assíduos que já acompanham seu conteúdo, e aprimoram a experiência mobile desses usuários de forma progressiva (não confundir com “progressive enhancement”, veremos ele a seguir), promovendo uma imersão muito próxima do que seria um app nativo, porém não coerciva ou intrusiva, pois não obriga que usuários corriqueiros ou na primeiro visita ao seu site, tenham que baixar um App para ter acesso ao seu conteúdo. Isto garante que qualquer usuário possa acessar os recursos de sua aplicação web de uma forma tão simples quanto acessa a própria web. Todos estes conceitos envolvidos em PWA tentam resolver um dos grandes problemas mobile de hoje, nós temos millhões de aplicativos disponíveis para serem baixados e temos umas dezenas deles instalados em nosso aparelho que fazem nada de relevante e que muitas vezes fomos obrigados a instalar para ter acesso a algo temporário, quando na verdade precisamos de só uma meia dúzia deles. Por outro lado nós temos um numero muito maior de websites disponíveis na internet, mas que mesmo com as iniciativas para web responsiva a usabilidade, ainda não conseguem entender as espectativas dos usuarios. PWAs são caras legais pois eles são uma iniciativa em direção a um lugar comum onde todos queremos chegar para “Tornar a web um lugar melhor”.  

### WebMobile ou App Nativo?<figure>

![][1]<figcaption>“Porque não los dos?”</figcaption></figure> 

  Muito se discute ainda sobre estratégia mobile e os argumentos de hardware, performance geralmente são postos à mesa, porém como Sergio Lopes cita no livro, A Web Mobile, A Web é boa o suficiente para a maioria dos cenário possível, portanto no momento de tomar a decisão de qual estratégia mobile seguir, o que importa mais é o foco no usuário e as expectativas que ele possui com sua marca, produto ou empresa. Existem também aqueles que apelam para os numeros alegando que os usuarios mobile passam 80% do seu tempo utilizando aplicativos e eles estão certos, pena, que não serão os seus aplicativos. Basta darmos uma olhada em nossos celulares, quantos de nós utiliza mais que os aplicativos criados pelas gigantes do mercado já consolidadas e estabilizadas?

#### Estretégia Web Fisrt

Web é uma solução muito interessante para aqueles que já possuem uma marca ou produto web e estão pensando em iniciar um projeto mobile, no entanto para aqueles que vão iniciar um novo produto, um produto inovador que não possua concorrentes e expectativas por parte dos usuários, uma estratégia baseada diretamente em apps pode ser a melhor saída. O que nós entendemos até aqui é que se um produto novo que não tem um público já atingido, seja por você ou por algum concorrente que já lançou um app para o mesmo nicho de mercado, ele não é capaz de gerar expectativas por parte dos usuários, porém quando já existe uma estratégia online estes usuários já possuem esta expectativa com a marca, assim sendo uma estratégia Web Pode ser mais interessante. Em muitos casos pode-se assumir uma estratégia “Web First”, onde nós podemos lançar a marca ou produto no mercado sempre primeiramente pela versão web onde todos os usuários terão acesso, então depois de consolidados no mercado podemos partir para uma estratégia diferente e é exatamente ai que as PWAS irão aparecer.

### Porque usar Progressive Web App?

Segue abaixo uma lista de motivos que eu encontrei para justificar o uso de PWAs como primiera estratégia em relação a Apps nativos:

#### Porque é Web:

PWAs terão o comportamento e imersão de um App nativo, com toda a acessibilidade e recursos que um website, isto quer dizer que seu conteúdo estará disponível a todos em todos os dispositivos, seja mobile, desktop, na tv da sala ou em seu tamagotchi.

#### Apps são inconvenientes:

Como já citado acima, para um usuário que visita sua página pela primeira vez, que talvez nem conheça o seu serviço ou produto, pode não ser muito confortável(e não será) ter que baixar um app, muitas vezes grande, muitas vezes em uma conexão ruim e muitas vezes conflitante com o pouco espaço de armazenamento do aparelho, somente porque você não proveu uma solução online para o problema dele.

#### “UsuarioFirst”, Porque relacionamentos possessivos acabam cedo:

Todas as estratégias das PWAs baseiam-se fortemente nas expectativas do usuário, suas experiências e necessidades, em momento algum você deve obrigá-lo a fazer algo ou a tomar uma decisão por ele, você deve prover a melhor experiência possível sempre. Acredito que de todos os conceitos que vi sobre PWAs este foi um dos mais repetidos e se mostrou para mim o mais importante dos conceitos, foco 100% no usuário.

#### Porque você não quer perder público:

para cada etapa que você obriga seus usuários a enfrentarem até chegar a seu conteúdo, você irá perder em torno de 20% do seu público, como explicado por [Alex Russell em sua palestra sobre Progressive Web Apps em 2015][2]. Isto que dizer que entre entrar na loja, baixar e instalar seu aplicativo, você está deixando usuários preciosos insatisfeitos.

#### Progressivamente aprimorado (Progressive Enhancement):

Tão importante que faz parte do nome que define o conceito, isto que dizer que sua aplicação funciona para todos os usuários, independentemente da escolha de navegador, pois são criados com aprimoramento progressivo como princípio central.

#### Progressivamente instalado:

Porque Você irá prover toda a solução online para seu usuário, então conforme ele torna-se assíduo consumidor do seu conteúdo você poderá oferecer a ele, o direito de escolha para que tenha uma experiência mais próxima da marca em sua home screen, permitir que ele escolha entre continuar acessando normalmente pelo browser ou ainda baixar um aplicativo que pode lhe possibilitar mais recursos.

#### Engajamento:

Uma vez que você promove uma aproximação progressiva e totalmente acessível com os usuários, você naturalmente conseguirá uma proximidade maior com os mesmo, e agora com PWA podemos fazer com que esta aproximação seja facilitada pois o acesso ao seu conteúdo estará a um click de distância, mesmo antes dele ter decidido por baixar o seu App(supondo que você tenha optado por fazer um), isto irá gerar um engajamento muito maior do público.

#### Reengajáveis:

Facilitam o reengajamento por meio de recursos como notificações push.

#### Compartilhamento de conteúdo:

Permite que os usuários compartilhem seu conteúdo com outras pessoas de maneira fácil a partir de hiperlinks assim como seria em um site convencional.

#### Funcionam Offline e são constantemente Atualizados:

Todo o conteúdo será guardado em cache e estará disponibilizado para o seu usuário mesmo que ele não tenha acesso a internet. Sempre que for possível e houver conexão o Service Worker pode solicitar a versão mais atualizada do se WebApp e gerenciar de acordo com a estratégia escolhida pela equipe, para que ele seja salvo e o cache antigo será deletado.

#### Seguros:

Toda informação será veiculada por HTTPS para impedir o rastreamento e assegurar que o conteúdo não foi adulterado.

### Próximos passos com PWAs

Bem, este foi um pedaço do conteúdo com uma pequena introdução sobre PWAs, espero que tenham gostado. Eu achei que o conteúdo estava ficando muito grande então decidi dividir em dois artigos para a leitura não fica maçante, então no próximo teremos os principais aspectos de **como iniciar com Progressive Web Apps?**

Web content composed with the [online wysiwyg editor][3]. Please subscribe for a membership to remove promotional messages like the above.

 [1]: uploads/2016/12/c7NJRa2.gif
 [2]: https://www.youtube.com/watch?v=MyQ8mtR9WxI
 [3]: https://html-online.com/editor/