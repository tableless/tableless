---
title: Locaweb Style – Como iniciamos
author: Diego Eis
type: post
date: 2013-02-19
excerpt: Como iniciamos e por que resolvemos criar um framework próprio aqui na Locaweb.
url: /locaweb-style-como-iniciamos/
dsq_thread_id: 1092474590
categories:
  - Artigos
  - Código
  - Design
  - HTML
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - 2013
  - CSS
  - framework
  - JavaScript
  - locaweb

---
Se você ainda não conhece o [Locaweb Style][1], vá lá conhecer e continue lendo esse texto. Vai ser interessante se você está querendo usar um framework pronto se quer criar um novo para seus projetos.

Uma das minhas missões aqui na Locaweb em 2012 foi iniciar uma reestruturação na área de front-end. Embora todas as equipes aqui tenham programadores super [talentosos em back-end][2], por incrível que possa parecer, a Locaweb não tinha uma equipe focada para tratar do código front-end de seus produtos. O problema de não ter uma equipe é que cada projeto era escrito de uma maneira diferente. Geralmente as equipes tentavam se virar de alguma maneira. Alguns terceirizavam ou contratavam uma pessoa que suprisse essa demanda. Alguns usavam HAML (arghhh!), outros terceirizavam o desenvolvimento na Índia etc&#8230; A ideia então de ter uma equipe que unificasse o código front-end, facilitando principalmente o entrosamento da equipe de back-end com a equipe de UX, foi tirada do papel e foi aí que eu entrei para fazer minha bagunça.

Fazia um tempo que a equipe de UX estava planejando um redesign completo dos produtos da Locaweb, unificando todo o visual e padronizando os elementos de interação elementos. Quando começamos a estruturar a área, eles já estavam com o novo design pronto para ser aplicado em um projeto pequeno. Aproveitamos isso e começamos a produzir um padrão de código em cima dessa nova linha visual.

## Escolhendo a base

Utilizar o [Bootstrap][3] foi nossa primeira decisão. Nós não queríamos e nem podíamos iniciar um projeto do zero. O Bootstrap já tinha todos os elementos e comportamentos que precisávamos. Logo, seria burrice iniciar uma nova biblioteca, que faria a mesma coisa.

> Escolha um framework em que confia para ser sua base.

O próximo passo foi convencer os designers a utilizarem os elementos que já existiam no Bootstrap. A vantagem é que os elementos e os comportamentos prontos do Bootstrap são lindões e bem simples, logo, convencer os designers não foi difícil. Mas como nem tudo são flores, nos novos layouts produzidos pela Locaweb existem elementos e estruturas que demandariam a produção de customizações em cima do que já existia no Bootstrap. Por exemplo: cada produto tem uma cor diferente e por causa disso a cor dos botões primários de confirmação seriam da cor do produto. Logo, teríamos que sobreescrever o visual dos botões do Bootstrap com o nosso código. Além disso, como queríamos realinhar o visual dos serviços da Locaweb, elementos estruturais como header, footer, sidebar e etc teriam que ser produzidos do zero.

Existiam outros pontos onde não queríamos esperar o Bootstrap resolver, por exemplo a forma com que o Boostrap usava ícones. Haviam dois problemas:

**1. Para manter a compatibilidade com browsers antigos, o Booststrap insere um elemento extra vazio no HTML para colocar o ícone.**
  
Nós não queríamos deixar um elemento vazio no HTML simplesmente para suprir uma necessidade visual. O elemento não traz semântica nenhuma e nem ajuda na estruturação da página.

A solução foi reescrever o código para que os ícones fossem inseridos via pseudo-elementos :after ou :before, assim o elemento extra no HTML não seria mais necessário e nós teríamos a mesma liberdade de customização.

**2. Os ícones originais do Bootstrap são feitos como imagem.** 
  
Isso trazia vários problemas: como cada serviço tem uma cor específica, teríamos que converter para cada cor os stripes dos ícones do Bootstrap. Outro problema é que os ícones são utilizados em diversos tamanhos, isso já significava que teríamos que reproduzir os ícones do Bootstrap para diversos tamanhos de acordo com o layout.

Logo a decisão foi utilizar os ícones em formato de fonts. Para tanto usamos os serviços como [Fontello][4] e [IcoMoon][5]. Dessa forma conseguímos ter os ícones do Bootstrap em formato de font e também demos mais liberdade para os designers escolherem uma cartilha maior de ícones.

Parece que na versão 3.0 eles substituirão os ícones de imagem por fonts&#8230; Mas aí já fizemos nossa parte aqui! 😉

## Javascript

Para suprir algumas outras necessidades, nós contamos com alguns plugins comuns no mercado. Utilizamos o [jQuery][6], [Modernizr][7], [Select2][8] que é um puxadinho do [Chosen][9], [Masked Input][10] e o módulo de [calendário do JQuery UI][11].

Em nosso roadmap já está previsto a refatoração de todo o Javascript &#8211; na verdade já estamos no final do trabalho &#8211; utilizando as melhores práticas e facilitando o acesso de scripts externos aos scripts do Locaweb Style. Precisamos rever uma série de coisas para que o Javascript fique mais flexível e modulado. Todo o Javascript criado foi pensando em comportamentos específicos que os serviços necessitam e que são misturados com os comportamentos do Bootstrap. Por exemplo: um formulário que é aberto dentro de um collapse, mas que quando o collapse é fechado, limpa todos os campos. O script do collapse é do Bootstrap, mas a ação de limpar os campos não. Veja [um exemplo aqui][12].

Estendemos toda a necessidade de interação e comportamento para nossos produtos, utilizando o que já existia no Bootstrap como padrão e produzindo scripts derivados para complementar a função dos comportamentos.

> A ideia é iniciar da maneira correta. Se isso não for feito, tome uma atitude de mudança o mais rápido possível.

Com a refatoração do nosso Javascript, estamos colocando as boas práticas de codificação em ação. O certo mesmo era começarmos já da maneira correta. Mas como estávamos nos baseando totalmente no Bootstrap, durante algum tempo não havia a necessidade da criação de novos scripts. Isso ajudou no começo, mas o pouco código que havia começou a crescer e aí sim nos incomodou. Nesse tempo a equipe cresceu, então pudemos dar mais atenção a isso.

Meu conselho é começar sempre colocando as boas práticas em ação. Aqui estamos usando [Prototypes][13] do javascript (não o [frameworks][14]), para quem me perguntou. Outra premissa é retirar do Javascript o máximo daquilo que o CSS pode resolver. Aí entra um mesclado de boas práticas trazidas pelo [gracefull degradation e o progressive enhancement][15].

### Escolhendo o que vai pra dentro

Uma das decisões mais difíceis de tomar quando se constrói um framework é decidir o que vai fazer parte do padrão. Se você tem a falsa impressão de que tudo o que é útil será usado no framework, qualquer script bonitinho que o pessoal encontra acaba sendo inserido no framework. Isso infla o código e geralmente não usamos nem metade do que está lá. A ideia é crescer harmoniosamente, tendo features que são realmente usadas pelos projetos. Nada de inserir algo que talvez, um dia, alguém precise. Se não precisa agora, não coloque. Seu framework será sempre um work in progress, lembre-se disso. Se mais pra frente houver a necessidade dessa feature, basta inserí-lo.

Por isso é importante tomar cuidado quando surgir uma funcionalidade nova, que pode ser muito útil em um projeto e que nunca mais será usada em outro. A mesma coisa acontece quando decidimos quais plugins farão parte do pacote. Se determinada funcionalidade for indispensável em vários produtos, ele entra pro framework, caso contrário ele é utilizado especificamente naquele projeto. Se algum dia, talvez, alguns outros projetos forem utilizar aquilo, é relevante repensar a utilidade de colocá-lo no framework para que sua utilização seja unificada.

> Nenhum framework do mundo vai se adequar a 100% da sua necessidade. Isso é mito. 

Geralmente, a gente adiciona coisas de acordo com a necessidade. Se ainda não precisamos de collapses, não vamos adicionar um script de collpase. Se não existem ainda um carousel no sistema, não vamos adicionar o script de carousel ainda. Uma boa ideia também é discutirmos com a equipe inteira se vale a pena ou não termos determinado plugin no sistema. 

No Locaweb Style temos alguns plugins inclusos: jQuery, Masked Input, Select2 e [Modernizr][16].
  
De cara eu já tiraria o Select2. Eu acho pecado customizar combobox/selects, mas os designers acham bonitinho&#8230; E realmente dependendo do contexto pode ser muito útil.
  
O Masked Input serve para criar máscaras em campos de formulário. Não vale a pena fazer um do zero por isso adicionamos no pacote.
  
Já o jQuery e a [Modernizr][16] nem preciso descrever que são indispensáveis no pacote.

### Mantendo tudo em ordem

Outro ponto crítico é ajudar os designers não caírem na tentação de criar novas soluções para problemas que já foram resolvidos. Quando a equipe de UX é grande e os integrantes cuidam de projetos diferentes com necessidades similares, é normal que pessoas diferentes criem soluções parecidas para resolver um mesmo problema. Nesse caso a obrigação do front-end é proteger o framework, fazendo com que os designers utilizem as soluções já existentes no pacote. Assim evitamos que a inserção de soluções redundantes. Por isso, é muito interessante que todos da equipe tenham em mente quais as soluções já foram criadas no framework. Isso é facilmente resolvido tendo um manual completo de todos os elementos e suas respectivas funcionalidades. 

> Um framework é como um quebra-cabeças onde você junta as peças para criar novas formas de layout e estrutura.

Aqui na Locaweb a equipe de UX faz uma reunião diária para discutir soluções e a verdadeira utilidade de alguns elementos que compoe o layout. Isso é muito bom por que a reciclagem de novos elementos é feita com frequencia e soluções são transformadas para terem um comportamento melhor.

O framework precisa servir como um quebra-cabeças. Todas as peças precisam se encaixar a qualquer momento. Isso facilita a criação de novas estruturas e variações de layouts.
  
Se tudo der certo o trabalho de produção de views e páginas estáticas se resume a praticamente copy and paste do código pronto do framework. Na verdade não é tão fácil assim, mas esse é o objetivo. =^D

### Fluxo de atualização

Como o Locaweb Style é um framework feito primeiramente para suprir as necessidades dos produtos da Locaweb, a frequencia de atualização precisa acompanhar os deploys dos produtos. Descobrimos que aqui dentro podemos fazer uma atualização pequena a cada 15 dias. No primeiro ano de desenvolvimento fazíamos uma atualização por semana. Resolvíamos bugs e inseríamos novas features.

> Seu framework será sempre um work in progress.

Hoje só fazemos atualizações fora da janela de 15 dias se tivermos algum pequeno bug que precisa ser resolvido em algum dos serviços. Se não tivermos atualizações relevantes, não fazemos uma major update.

Atualizações onde mudamos versões de plugins, como jQuery ou Bootstrap, fazemos um deploy individual, marcando bem aquela versão para que quem acompanha possa controlar melhor suas versões.

### Concluindo

Nenhum framework do mundo vai se adequar a 100% da sua necessidade. Isso é mito. Invariavelmente, se você quiser algo bem feito e que você vai ter um trabalho para adequar esse framework às suas necessidades. O pulo do gato é você fazer isso sem produzir código conflitante com o código do framework base.

Fazer um framework que funcione e que tenha uma continuidade saudável é difícil. Mesmo assim vale a pena pela experiência e pela força de produção que a equipe ganha em novos produtos e na manutenção dos que já existem. Por conta dessa facilidade, conseguimos manter com uma equipe de 3 pessoas algo em torno de 10 produtos simultaneos.

Se quiser saber mais sobre o Locaweb Style: <http://developer.locaweb.com.br/locawebstyle/>

Há também dois artigos que escrevi falando um pouco sobre estruturação front-end. Talvez valha a pena ler.

  * [Estruturação de front-end – Parte 1: Préprocessadores, Framewoks e Bibliotecas][17]
  * [Estruturação de front-end – Parte 2: Designers e Programadores][18]

Há outro artigo bem interessante sobre a [criação de seu próprio framework][19] que o [Bernard de Luna][20] escreveu.

 [1]: http://developer.locaweb.com.br/locawebstyle/ "Locaweb Style - O Framework da Locaweb"
 [2]: https://github.com/locaweb/
 [3]: http://twitter.github.com/bootstrap/
 [4]: http://fontello.com/
 [5]: http://icomoon.io/
 [6]: http://jquery.com/
 [7]: http://modernizr.com/
 [8]: http://ivaynberg.github.com/select2/
 [9]: http://harvesthq.github.com/chosen/
 [10]: http://digitalbush.com/projects/masked-input-plugin/
 [11]: http://jqueryui.com/datepicker/
 [12]: http://developer.locaweb.com.br/locawebstyle/conteudo/busca-avancada/
 [13]: http://net.tutsplus.com/tutorials/javascript-ajax/prototypes-in-javascript-what-you-need-to-know/
 [14]: http://prototypejs.org/
 [15]: http://tableless.com.br/bem-vindo-a-xangrila-parte-1/ "Bem vindo a Xangri-lá – Parte 1"
 [16]: http://tableless.com.br/utilizando-a-biblioteca-modernizr/
 [17]: http://tableless.com.br/estruturacao-de-client-side-preprocessadores-framewoks-e-bibliotecas-parte-1/ "Estruturação de front-end – Parte 1: Préprocessadores, Framewoks e Bibliotecas"
 [18]: http://tableless.com.br/estruturacao-de-client-side-designers-e-programadores-parte-2/ "Estruturação de front-end – Parte 2: Designers e Programadores"
 [19]: http://tableless.com.br/criando-seu-framework-html-css/ "Criando seu próprio Framework HTML CSS"
 [20]: http://bernarddeluna.com/