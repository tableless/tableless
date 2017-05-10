---
title: 'Introdução: diversidade dos meios acesso'
author: Diego Eis
type: post
date: 2009-09-28
excerpt: Lidar com a quantidade de meios de acesso é e será um grande desafio no desenvolvimento para web. E não estou falando apenas sobre mobiles. O negócio é mais amplo e complexo. Há mobiles, desktops, consoles e uma pancada de outos dispositivos que ainda não são populares, mas serão um dia.
url: /diversidade-dos-meios-acesso/
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356452857
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/diversidade-dos-meios-acesso";s:7:"tinyurl";s:26:"http://tinyurl.com/3sjagje";s:4:"isgd";s:19:"http://is.gd/Mqc5VK";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039255
categories:
  - Artigos
  - Browsers
  - Código
tags:
  - Browsers
  - clientside
  - CSS3
  - frontend
  - html5
  - mobile

---
Estive no mês de Setembro/2009 fazendo uma [consultoria][1] para a Globo.com. Nesta consultoria, dentre muitas coisas, conversamos sobre a diversidade de aparelhos móveis utilizados para acessar os sites da Globo. Este problema está se tornando cada vez mais recorrente em grandes e pequenos sites. A quantidade de aparelhos que são lançados, não apenas celulares e smartphones, mas também outros aparelhos que permitem o usuário acessar a internet, cresce a cada ano. Isso faz com que tenhamos uma preocupação excessiva em como poderemos apresentar o conteúdo da melhor forma os diversos dispositivos. Mesmo assim, o problema não é tão grande. O desenvolvimento web para os dispositivos móveis, hoje, é o melhor dos mundos. Temos browsers com suporte total dos Padrões Web, rápidos e que fornecem uma experiência excelente de uso e navegação.

### Graceful Degradation e Progressive Enhanced

Procurar querer dar uma boa experiência para todos os dispositivos utilizados pode se tornar um problema, já que a variação de aparelhos e hardware é muito maior quando comparado com o mundo dos desktops.
  
Sabemos que, para um site normal, é seguro ter uma largura de 990px. Sabemos que com essa largura, o site vai ficar bem diagramado em diversas resoluções, começando em 1024.
  
Mas nos aparelhos móveis não temos essa métrica. A variação dos tamanhos das telas é muito maior. Os aparelhos e a forma de uso de cada um são muito diferentes.

Eu não gosto de nivelar os sites por baixo. Pelo menos não hoje. Há muitas possibilidades de fazermos um bom trabalho de user experience, mas não o fazemos, porque há alguns perfis de usuário, que infelizmente temos que prever no escopo. Por isso sou a favor do [Graceful Degradation][2] e do Progressive Enhanced.

Fornecer a melhor experiência possível para todas as camadas de usuários. Esse é o alvo para a utilização do Graceful Degradation e do Progressive Enhanced.  Se nivelarmos o visual e as funcionalidades do site/sistema por baixo, iremos prejudicar demais os usuário “de alto escalão”. Para entender melhor, imagine um usuário de Safari Mobile acessando um site customizado para Internet Explorer Mobile.

### Versionamento Especifico

Já é prática antiga criar versões dos sites para um sistema, aplicação ou dispositivo específico. Fazíamos isso na guerra dos browsers e fazemos isso hoje para alguns browsers antigos. Versionar um site é uma das saídas mais simples para resolver um grande problema. Como a quantidade de dispositivos de acesso está crescendo, a necessidade de haver uma versão do site para estes dispositivos é mais que normal. O HTML é uma linguagem feita para que seja acessada por diversos meios. Hoje, os meios de acesso são bem escassos, consigo pensar apenas em Desktops e Aparelhos de mão (celulares e smartphones). Você consegue pensar em mais alguns outros?
  
Embora não sejam maioria, os consoles estão aumentando sua presença online. Aparelhos como XBOX e Playstation estão se tornando cada vez menos restritos para jogos, e estão indo muito além do que poderíamos imaginar um dia. O XBOX já anunciou sua integração com [Facebook][3] e [Twitter][4]. Embora este tipo de acesso seja ainda muito limitado e controlado pelas fabricantes dos consoles, imagine, como seria a experiência de acessar a internet que temos hoje por um Playstation ou XBOX. Eu acharia sem graça. É uma interface totalmente diferente da comum. Mesmo se tentássemos levar a mesma experiência atual com os desktops para estes dispositivos, na minha opinião, estaríamos subutilizando-os.
  
A mesma coisa pode acontecer com aparelhos como o Surface da Microsft. Eu não imagino um usuário abrindo um navegador como o Firefox, IE ou Opera no Surface e utilizando-o para navegar na internet como fazemos hoje. Não encaixa. É algo diferente, mais interativo, divertido. E atenção aqui: quando digo interativo, não estou querendo dizer que tudo deverá ser feito com Silverlight ou Flash, pelo contrário. O [HTML 5][5] e o [CSS 3][6] estão vindo para acabar com esse mito.

Também não estou dizendo que talvez você fará uma versão dos seus sites para cada novo dispositivo que aparecer. Pelo contrário. Estou dizendo que eles serão necessários de acordo com o público de cada site, e de cada negócio.

Até hoje os desenvolvedores e também os donos de sites, tem uma dificuldade muito grande em criar ou decidir se é útil ou não desenvolver uma versão dos sites para mobiles. Imagine quando a cartilha de meios de acesso aumentar.

A [Globo.com][7] e também outros grandes sites enfrentam o mesmo problema: decidir quem vai e quem fica. Decidir qual aparelho será priorizado e qual receberá apenas uma versão de texto. Claro que com o tempo, as limitações de cada aparelho serão mínimas e as características de cada um serão bem parecidas. Isso diminuiria muito o trabalho de desenvolvimento e aumentaríamos a quantidade de acesso, pelo simples fato de que estaríamos dando quase que a mesma experiência para uma quantidade maior de dispositivos.

Outro ponto importante, mas consolador, é que há motores de renderização muito bons hoje em dia. Vide Gecko e Webkit. Ambos de código livre e que recebem sugestões e modificações do mundo inteiro. Por exemplo, os aparelhos da Nokia e também o Chrome utilizam o Webkit como base para seus softwares de acesso. Isso faz com que consigamos manter o controle de nosso desenvolvimento e nos dá uma visão melhor de todo o horizonte de possibilidades.

Você, como desenvolvedor, tem a obrigação de viver um pouco mais além. Não pense que iremos escrever HTML e CSS para todo o sempre. E mesmo que for, serão linguagens totalmente diferentes de como as conhecemos hoje.

### Conhecendo os browsers e seus motores

Os browsers estão ainda muito longe de melhorar a forma com que lidamos e navegamos com a web. Nenhum deles trouxe nos últimos anos uma inovação capaz de fazer com que melhoremos nossa experiência online. Eles ainda estão engatinhando muito e parte da culpa não é deles. O W3C se mostrou muito lerdo nos últimos 11 anos. Eles acordaram muito tarde para as reais necessidades dos desenvolvedores. A comunidade por sua vez, sacudiu todo o W3C, tomando a iniciativa e começando um novo evanlegismo em pról do HTML 5 e do CSS 3. Isso fez com que o W3C entendesse melhor o que os desenvolvedores precisavam para que a web inteira fosse privilegiada.
  
Os browsers por sua vez, aproveitaram toda essa mudança, e começaram uma nova guerra, em silêncio. O suporte aos Padrões dos principais browsers do mercado está invejavelmente avançada. Há browsers como o Internet Explorer que sempre serão atrasados, mas que felizmente estão acordados também para as novas atualizações do mercado.

Mesmo assim, acho que o foco não se deve dar em browsers específicos, acho que nossa atenção deve ser voltada para os Motores de Renderização. Hoje, os principais são:

  * **Gecko**
  
    Motor com código aberto. É utilizado nas aplicações da Mozilla: SeaMonkey, Camino, Firefox, Thunderbird etc. Gecko é um motor herdado do antigo Netscape, baseado no Mosaic. Depois da Guerra dos Browsers, a Netscape doou o motor de renderização para a comunidade, que culminou na criação da Mozilla.
  
     ****
  * **Presto**
  
    Motor proprietário da Opera Software. A Opera é uma das empresas que mais inovam no mercado de browsers. Embora eles tenham tecnicamente um dos melhores browsers para desktops, a versão mobile é a mais utilizada. Eles tem duas versões: Opera Mobile, para smartphones e Opera Mini, para celulares mais básicos. A Opera também está muito presentes em outros mercados fora da web.
  * **Webkit** 
  
    Motor com código aberto, é utilizado hoje em aplicações como Safari, Safari Mobile e Chrome, browser do Google. É o mais novo motor de renderização do mercado. Foi criado pela Apple, baseando-se no motor de renderização KHTML, que estava só presente em browsers para Linux, como o Konqueror. Aproveitando que o KHTML é um sistema OpenSource, a Apple modificou todo o seu código, fazendo melhorias e aperfeiçoando-o para criar seu browser o Safari.  A Apple fez várias outras modificações posteriores em cima desta primeira versão. Deu o nome de Webkit, e hoje, conduz o desenvolvimento dessa plataforma.
  * **Trident** 
  
    É o motor proprietário da Microsoft. É utilizado em aplicações como Outlook e claro, no Internet Explorer. Eles estão criando um novo motor, que é utilizado no Internet Explorer 8 e posteriores. Embora o Trident fora o primeiro a suportar completamente a primeira versão do CSS, atualmente ele é o motor de renderização mais atrasado. A Microsoft vem fazendo um bom trabalho para tentar recuperar essa má fama, mas mesmo assim, os outros motores do mercado estão muito além.

Quando conhecemos o motor de renderização dos browsers, e sabemos quais suas limitações, não precisamos nos preocupar com a quantidade de browsers criados. O Google lançou o seu browser chamado Chrome, baseado em Webkit. Embora fosse um novo browser, isso não deveria assustar os desenvolvedores, já que é o mesmo motor utilizado no Safari. Logo, a renderização dos dois é muito parecida. Não é uma preocupação a mais, pelo contrário.
  
A mesma coisa se aplica aos browsers para mobiles dos sistemas da Nokia e também do iPhone. Ambos utilizam Webkit para renderizar as páginas. Isso dá liberdade para a criação de interfaces mais elaboradas, tornando a experiência de usuário mais interessante em dispositivos móveis.

Já o Internet Explorer, com seu motor de renderização se mostra um inimigo dos desenvolvedores. Embora a Microsoft esteja trabalhando arduamente em um novo código, as versões antigas deste motor ainda assombra a muitos desenvolvedores. E infelizemente, em alguns projetos, precisamos dar um passo para trás por conta da massa de acessos feitos por este motor.
  
A mesma história se aplica para a versão do Internet Explorer Mobile. O suporte crítico aos Padrões Web faz com que os aparelhos com este sistema se tornem obsoletos quando se trata de experiência online.

Entenda a importância dos motores de renderização. Eles tem um papel fundamental no comportamento do mercado e faz com que avancemos no desenvolvimento web.

### No final tudo dá certo. Ou não.

A web está passando por uma transação infinita. A cada dia ela ganha mais foco na mídia, mais atenção das empresas, tanto grandes, quanto pequenas. Sempre que um novo dispositivo é criado, um novo nicho de usuários surge, com novas maneiras e costumes de navegação. É impossível agradar a todos. Por isso é importante estabelecer prioridades. Um bom caminho é ajudar no desenvolvimento e compartilhamento de sistemas que ajudam a web a avançar. “Muda, porque quando a gente muda, o mundo muda com a gente.” Gabriel O Pensador.

 [1]: http://visie.com.br/treinamento/treinamento-in-company/
 [2]: http://tableless.com.br/graceful-degradation-e-tudo-sobre-acessibilidade
 [3]: http://facebook.com/
 [4]: http://twitter.com/tableless/
 [5]: http://tableless.com.br/html-5-semantica-e-o-que-e-importante-na-web
 [6]: http://tableless.com.br/efeito-cascata-e-especificidade-do-css
 [7]: http://globo.com