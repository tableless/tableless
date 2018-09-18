+++
authors = "Igor Octaviano"
categories = ["javascript"]
date = "2018-08-23T04:02:00-03:00"
excerpt = "Entenda como surgiram os bundlers no Javascript"
image = "https://i.imgur.com/GIzEFch.jpg"
publishdate = "2018-08-23T04:02:00-03:00"
tags = ["bundlers"]
title = "Uma História Web: A Origem dos Bundlers"
type = "post"

+++
Você é um aspirante JavaScript ou está confuso sobre módulos? Já viu vários termos como module loaders e module bundlers e está querendo saber o que é?! Ou você tem escrito JavaScript por um tempo mas não está muito confiante para falar sobre módulos? Ouviu falar sobre [webpack](https://webpack.js.org/), [Browserify](https://browserify.org/), [CommonJS](https://www.commonjs.org/), [AMD](https://www.requirejs.org/docs/whyamd.html) e não entendeu porquê utilizamos essas coisas?

Nesse artigo vamos entender qual foi a necessidade dos módulos e o porque do surgimento de tantas ferramentas para trabalhar com eles.

Já pegou sua caneca de café? então vamos lá! **Vai ser uma longa história**.

## Preâmbulo: Script em linha ou Inline Script

Nada melhor que começar com esse termo! Inline Script me traz boas lembranças de como eu escrevia as minhas primeiras páginas web. É quando se adiciona scripts diretamente em sua página, dentro de uma tag HTML chamada **script**. Foi assim que eu comecei e acredito que a maioria dos desenvolvedores começara por ai também.

É uma boa maneira de começar de forma rápida para ser sincero. Não há arquivos ou dependências externas para se preocupar nesse momento. Porém… é uma receita perfeita para código difícil de se manter ao longo do tempo, e existem alguns motivos para isso!

* **Falta de reusabilidade de código**: Se você precisar adicionar outra página ao seu website que também vai precisar de alguma função ou recurso dessa outra página que você já possui, será necessário copiar e colar esse código.
* **Falta da resolução de dependência**: Dependendo do jeito que você escreve o seu script, você será responsável em organizar as funções em uma ordem específica, de forma que elas já existam quando forem utilizadas.
* **Poluição do escopo global**: Todas as funções e variáveis vão morar no escopo global de sua aplicação. Mais para frente você vai entender o problema disso.

Essa parte, essa não pude deixar de lado, não entra com detalhes na história a seguir. Vamos já deixar nivelado aqui as razões pelas quais o uso do Inline Script traz certos problemas, e isso vale também para [Inline Style](https://www.w3schools.com/html/html_css.asp).

## Capítulo I: A Origem

Um jovem programador detentor de um único script de 500 linhas de código e seu script escrito com muita dedicação para uma página web cuja estava trabalhando em dado momento. Tal script fora escrito em uma linguagem épica de capacidades inimagináveis (e cuja as bruxarias são incríveis) chamada JavaScript. Diêiés é o seu nome e a sua vida é uma vida muito boa, o seu script é, até então, manuseável e de tamanho razoável. Mas o tempo é dito ser cruel com alguns e não foi diferente com ele, com o passar dos dias, o projeto em que Diêiés trabalhava no seu dia-a-dia, cresceu, e nesse fluxo de crescimento ele começou a adicionar mais funcionalidades em sua página. E não só isso, ele se tornou um membro de equipe, pois sua empresa contratou novos desenvolvedores para trabalhar em conjunto nessa página web.

Se Diêiés continuar com sua configuração atual (um único arquivo de script cuja ele e possivelmente 'outros' podem começar a adicionar novas funcionalidades), ele estará fadado a encontrar 2 problemas em seu caminho:

* O seu arquivo de script vai crescer. Vai crescer igual [Chuchu](https://pt.wikipedia.org/wiki/Sechium_edule) na cerca (quem é interior conhece essa expressão), ou seja, vai crescer muito rápido a cada nova funcionalidade. Isso é ruim porque arquivos grandes são difíceis de manter e sabemos que é complicado encontrar seções específicas. Tirando o fato que é difícil ter vários desenvolvedores trabalhando no mesmo arquivo, ao mesmo tempo.
* Ele talvez queira utilizar algumas bibliotecas externas. Isso não é um problema propriamente, mas logo ele irá vai entender porque isso complica ainda mais toda a situação.

## Capitulo II: Quebrando o Código

Com esse problema na cabeça, Diêiés e sua perspicácia incrível, obviamente decidiu quebrar esse arquivo script enorme em vários arquivos menores. Isso não só porque o arquivo é grande, como também é uma boa prática separar as coisas em partes independentes para manter seu código organizado e limpo. Isso é até justificável, pois podemos querer separar as funções que lidam com manipulação da DOM de outras funções que lidam com requisições http ou processamento de dados, etc.

Digamos que originalmente ele tinha um arquivo de tamanho 10KLOCs e nessa vibe de mudança, rapidamente quebrou o arquivo em partes menores, ficando com 20 arquivos script menores, de tamanho 500LOC. Não é ótimo e maravilhoso porém é definitivamente melhor.

* KLOC = 1,000 linhas de código (k = 1,000, LOC = lines of code)
* LOC = linhas de código (lines of code)

Mas como Diêiés vai gerenciar esses arquivos? ele chegou a conclusão que a forma mais simples de se fazer isso é simplesmente colocando 20 tags **script** em sua página. Bom, ou talvez mais 20 outras tags para suas bibliotecas que tinha adicionado durante todo esse processo, como [lodash](https://lodash.com/), [jQuery](https://jquery.com/) (só para dar um drama) e outros plug-ins.

Tem uma coisa que Diêiés tem que levar em consideração, e essa coisa se chama ordem. Ele tem que tomar o devido cuidado ao inserir essas tags pois elas precisam estar em uma certa ordem. Ele tem que se garantir que as coisas (como as funções utilitárias) estarão disponíveis antes que outras partes as utilize. Isso até parece uma missão, acredite, agora é uma missão para ele.

A vida de Diêiés deu uma melhorada em alguns aspectos. Ele agora possui arquivos menores, o que já ajuda muito no seu dia a dia. Mas nem tudo são flores para ele. Esse pobre rapaz adicionou algumas preocupações, essas que ele tem que cuidar nesse momento. Não só a ordem das tags **script** como também tem o fato de que quando os outros membros de equipe adicionarem novas funções, eles tem que pensar onde vão colocar essas funções. Em qual arquivo eles devem colocar de forma que elas estarão disponíveis quando elas forem utilizadas? Será melhor adicionar um novo arquivo e uma nova tag **script**?

Diêiés se questiona profundamente enquanto abre um pacote de Doritos…

Também, agora que ele entendeu sobre a importância da separação das responsabilidades, sendo o primeiro dos princípios [SOLID](https://cleancoders.com/videos/clean-code/solid-principles) que ele tinha estudado na época da faculdade. Porém agora ele está produzindo um numero maior de pequenos arquivos e ele provavelmente vai precisar mante-los bem organizados em pastas.

Rapidamente ele alcançou 50 ,80… 100 arquivos JavaScript. Ele pode ver que o seu código está muito melhor agora, igualmente nós, expectadores, podemos ver novos problemas surgindo da superfície.

## Capítulo III: Surgem Novos Problemas

Mais problemas aparecem… Diêiés está preocupado com problema da quantidade de tags **script** e com a ordem que ele tem que manter… e agora algo novo apareceu. Esses arquivos definem vários nomes. Como nomes de funções, nomes de variáveis, nome de várias coisas. E toda vez que bate a vontade de alterar algum arquivo ele não tem ideia de quais nomes os outros arquivos já declararam. Colisões podem acontecer! O desenvolvimento se torna uma tarefa tediosa, ele tem que se lembrar de vários nomes que já foram utilizados antes ou ficar procurando alguma convenção, ou… bom, deu para ter uma ideia. Agora ele vai tentar resolver isso.

Procurando a sabedoria para resolver esse problema, buscando desesperadamente por tutoriais, livros, reddit e tudo mais, Diêiés acabou descobrindo os chamados Padrões de Módulos, mais conhecidos na lingua inglesa como **Module Patterns**.

<script src="https://gist.github.com/igoroctaviano/19cb06ab4323e521470841120e22d148.js"></script>     

Basicamente, esse padrão lhe permite, através de [clausuras](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures), o encapsulamento de código. A coisa retornada e atribuída a algumaCoisaInteressante acima tem métodos e propriedades visíveis e esses métodos tem acesso as coisas locais definidas dentro da expressão da função, na qual ninguém fora da mesma tem acesso. Então, de certa forma, é essa estrutura que vai permitir Diêiés escrever blocos encapsulados com visibilidade privada. Mas porque isso é relevante para ele?

Isso evita o problema dele com as colisões de nomes.

O que ele vai fazer é criar essa estrutura em cada um desses 80, 100… arquivos que ele tem, engolindo todo o conteúdo de cada arquivo. E no final de contas, essa estrutura vai retornar apenas as coisas que ele realmente quer que sejam visíveis.

Isso é um ganho e tanto, agora ele pode quebrar os arquivos em arquivos menores sem se preocupar com colisões de nomes. Por outro lado ele tem 180 tags **script** ou até mais que isso em sua página. E aquela coisa sobre a ordem dos arquivos ainda está valendo para ele, e ele ainda não solucionou esse problema.

## Capítulo IV: O seu Primeiro Script

**Vamos recapitular!**

1. Diêiés resolveu o problema do arquivo de script único e possivelmente monstruoso com sucesso. Isso era um grande problema para ele, de fato o arquivo era grande e difícil de se manter, e se tornava cada vez mais complicado gerenciar alterações com uma equipe de desenvolvimento trabalhando nesse mesmo arquivo com ele.
2. Mas agora ele tem os seguintes problemas:

* Ele tem um monte de tags **script** em sua página.
* Ele tem que manter uma certa ordem para tudo funcionar.
* Algumas pessoas de seu projeto tem reclamado que leva muito tempo para carregar 200 ou mais arquivos. Ele vai ter que lidar com isso uma hora ou outra, e esperamos que ele tenha isso em mente.

Querendo fazer algum progresso, ele segue no primeiro passo para tentar resolver esses novos problemas.

Bom, devido aos problemas enfrentados por Diêiés, posso dizer que existe uma solução simples. Não vai resolver todos os problemas, mas é simples e vai ajudar esse pobre desenvolvedor em alguma coisa. Bom, ele poderia ter um script shell ou outra ferramenta similar que simplesmente iria concatenar todos os seus arquivos de script em uma certa ordem. Assim, o primeiro problema dele seria resolvido (sendo que ele tem 274 ou mais arquivos até então). O script que foi incluído em sua página voltaria a ser apenas um único arquivo de script. Ele conseguiria voltar a ter uma única tag **script** em sua página.

— Que grande progresso! disse Diêiés após uma risada espalhafatosa ao ler sobre essa possível solução que mencionei, em um post na internet. Porém ainda ele tem o segundo problema em mãos. Para o script shell concatenar corretamente todos os arquivos JavaScript, ele tem que dizer qual é a ordem correta.

Ele pode encontrar várias soluções cabeludas e talvez alguma delas pode, de certa forma, resolver o seu problema.

Em uma situação fictícia, durante um período de insight da luz radiante da sabedoria eterna, ele então pensou… Talvez eu possa nomear os meus arquivos seguindo um padrão como 00001-algumArquivo.js, 00002-outroArquivo.js… e depois ir concatenando seguindo essa ordem. Isso iria funcionar, claro! bom… manter isso vai seria um pouco caótico, mas iria funcionar. E foi isso o que ele fez. A princípio ele iria usar uma sequência numérica mas depois de ter que renomear cerca de 80 arquivos em um dia nublado terrível, ele deixou alguns espaços vazios para serem preenchidos quando necessário, para não acontecer novamente, certo? (mas que sacada em Diêiés!).

Ou talvez ele iria manter em seu script shell, de alguma forma, a lista ordenada de arquivos, ou outras ideias desse tipo.

Bom, como podemos ver, qualquer solução que segue essa linha de pensamento é complicada ou se torna complicada muito rapidamente, e também não resolve o problema de Diêiés de forma prática. É uma tentativa válida de resolver? sim, mas acaba se tornando apenas um analgésico, só alivia a dor momentaneamente.

Dado a situação atual, Diêiés recorre novamente ao oráculo web, buscando novos tutoriais, novas ideias, pois ele sabe que há de existir padrões mais sofisticados do que os Padrões de Módulos.

![](https://cdn-images-1.medium.com/max/600/1\*mqkBUzVriASwAFBP-ynPbA.png)


## Capítulo V: Uma Primeira Aproximação aos Módulos

Refletindo sobre isso durante um tempo, Diêiés chegou ao ponto que seria muito legal se ele pudesse adicionar alguma forma de seu próprio arquivo script, disponibilizar a sua própria ordem, ou melhor dizendo, disponibilizar quais são as suas dependências explicitamente.

Para não perdermos o foco da história no meio de um monte de código, você pode dar uma pesquisada rápida sobre [RequireJS](https://requirejs.org/), pois essa é a implementação que mais se aproxima com a ideia de Diêiés nesse momento.

Em resumo, o RequireJS é o que muitos dizem, um Carregador de Módulos. Esse termo é mais conhecido na linha inglesa como **Loader**. Ele implementa uma definição chamada **Asynchronous Module Definition**. **Ele ajuda a carregar módulos de forma assíncrona.**
                                                                                                       <script src="https://gist.github.com/igoroctaviano/ec6f1a4a027fb6a2d47ef3733e5cb041.js"></script>

Novamente, enquanto ele estava fazendo uso do RequireJS, vivendo alegremente imerso no conforto desse mundo, alguns caras publicam na web uma coisa chamada [Node.js](https://nodejs.org/en/), e essa coisa se torna extremamente popular!

Isso é relevante porque o Node.js incluiu um mecanismo para fazer exatamente o que Diêiés queria fazer: definir módulos que possam ter partes locais e privadas, que possam exportar (**export**) algumas partes públicas e que também podem requisitar (**require**) outros módulos/dependências.

O mecanismo do Node.js surgiu com todo o poder da sintaxe de uma especificação conhecida na época como [CommonJS](https://www.commonjs.org/). Bom, se tornou algo muito popular. _Observe que depois de um tempo, o padrão ECMAScript decide fazer uso de um outro mecanismo e uma nova sintaxe extensível. Isso não importa muito agora, a parte importante é que algumas sintaxes se tornaram populares e é uma boa ideia seguir as que são populares, as que tem grandes chances de serem mantidas pela comunidade._

Claro, a sintaxe no Node.js funciona muito bem para Node.js. E enquanto o ECMAScript não tinha padronizado essa sintaxe, o suporte de módulos ainda não estava totalmente disponível em todos os navegadores, e esses sistemas são desenhados com a intenção de ter vários arquivos independentes e você não iria querer servir esses arquivos separadamente.

De qualquer forma, essa sintaxe livraria Diêiés de todo o mal daquele código esquisito sobre clausuras e simplesmente iria lhe permitir escrever seus módulos em uma maneira bem mais limpa e uniforme.

Então ele decidiu que essa é uma boa maneira de se fazer as coisas, decidiu que iria seguir esse caminho de agora em diante.

<script src="https://gist.github.com/igoroctaviano/1b429bd18f4776f7aba17d02a08a8c06.js"></script>

## Capítulo VI: O Segundo Script

Como ainda ele precisava empacotar todos os arquivos em um único arquivo apenas, e também precisava fazer esse arquivo funcionar em seu browser (não no Node.js), ele tinha que revisar aquele seu script shell, aquele que apenas concatenava todos os seus arquivos JavaScript. Ele precisava torna-lo em algo mais sofisticado.

Observe que ele poderia optar por várias formas aqui.

Uma forma que ele poderia tentar é:

1. Antes de cada um de seus arquivos de script, o script shell iria inserir um número de funções genéricas utilitárias. Isso principalmente porque, como mencionado, no navegador ele não tem suporte daquela sintaxe do Node.js `(require, module.exports)`, então ele precisa garantir que isso esteja disponível.
2. O conteúdo de cada arquivo será abraçado com um pouco de 'boilerplate' ou código de configuração. Pensa nisso da seguinte forma, é tipo aquele código que ele eliminou quando mudou da maneira escrever do RequireJS para maneira de escrever do Node.js (reveja os exemplos anteriores). Não é exatamente igual… mas é a mesma ideia. O que que esse código 'boilerplate' vai fazer? ele vai colocar o código de Diêiés dentro de uma função, e ao invés de chama-la diretamente, vai passar essa função, com o seu código do arquivo, para dentro de uma das funções genéricas utilitárias que ele adicionou no início de cada arquivo com o seu script shell.

O que vai resultar de disso tudo? o código de módulos vai ser escrito de uma maneira bem mais confortável agora, de uma forma que agora ele possa de fato apreciar. Porém quando chega o momento de executar isso, ele vai ter que gerenciar **como** e **quando** isso vai ser executado. Quando o seu código chamar `require("algumaCoisa.js")`, suas funções genéricas utilitárias adicionadas com o script shell, irão disponibilizar o código daquele módulo, ou se caso o arquivo ainda não estiver carregado, irá aguardar a execução desse módulo enquanto esse arquivo **algumaCoisa.js** ainda não estiver disponível (carregamento assíncrono).

_\*Geralmente isso é feito através do uso de registros ou identificadores que permitem o sistema referenciar os módulos corretamente, como se estivessem referenciando arquivos comuns ou coisas similares._

## Capítulo VII: O seu Próprio Empacotador \*Bundler

**Vamos recapitular novamente!**

1. Diêiés tem uma base de código manuseavel, onde o seu código fonte é dividido funcionalmente em pequenos módulos. Isso é uma coisa muito boa de ter.
2. Ele tem agora um processo ou uma ferramenta que:

* Coloca todos os seus pequenos arquivos em um arquivo único.
* Adiciona suas funções genéricas utilitárias que: **1.** Toma conta de disponibilizar cada módulo juntamente com outros módulos exigidos. **2.**Resolve o seu problema da ordenação.

> **Como é que o problema de ordenação foi resolvido? eu perdi essa parte?!**

> Como eu mencionei anteriormente, a execução dos módulos do Diêiés agora é gerenciada! agora ele tem a capacidade de atrasar a execução de módulos se caso alguma de suas dependências ainda não tiver sido carregada (carregamento assíncrono). Dessa forma ele não precisa mais se preocupar com a ordenação. Simplesmente carrega todos os módulos e então executa aquilo que ele queria executar.

Observe que não é só isso. O sistema de dependência pode trabalhar com o código dele, seja encapsulado ou agrupado em um único arquivo. Ou até mesmo, se for o caso, um arquivo separado e então esse fosse carregado sob demanda `require/import`. Contanto que o sistema ou a ferramenta disponibilize os mecanismos e entenda a mesma sintaxe, Diêiés ganha essa capacidade sob o seu código, sem que o seu código saiba disso (olha a inversão de dependência ai, lembra do [SOLID](https://en.wikipedia.org/wiki/SOLID)? pois é, o último dos princípios).

Agora, essa ferramenta do caso de Diêiés é algo que podemos fazer nós mesmos, igual como imaginamos aqui nessa história. Mas seria bem melhor se várias pessoas fazendo ferramentas similares, fizessem elas de uma forma que funcionasse da mesma maneira, ou utilizasse da mesma ferramenta que nós. Assim iriamos poder tratar bibliotecas externas da mesma forma que nós tratamos nosso próprio código, como um contrato, uma interface em comum.

Então, ao invés de construirmos nós mesmos essa ferramenta, você pode utilizar uma já existente. Essas ferramentas são [Browserify](https://browserify.org/), [webpack](https://webpack.js.org/), [Parcel](https://parceljs.org/), etc.

Algumas dessas ferramentas tem a tendência de tirar vantagem do fato que nós já estamos fazendo todas essas transformações de código, como também esses processos de empacotamento, para então, fornecer outras tarefas! Tarefas como minificar o nosso código (comprimir ele para que fique menor e leve menos tempo para ser carregado). Ou talvez algumas ferramentas são sofisticadas o suficiente que elas podem até evitar a inclusão de arquivos (ou partes de arquivos) cuja não estão sendo realmente utilizados (técnica conhecida como [tree-shaking](https://webpack.js.org/guides/tree-shaking/)). Ou eles também podem processar nossos assets como CSS e imagens. Uma vez que nós concordamos em ter essa ferramenta ou processo como um passo no nosso fluxo de trabalho, bom, por que não fazer uso de tudo isso?!

## Detalhes Adicionais

A partir daqui tudo é opcional, é uma extensão da explicação anterior. Não vai lhe passar mais nenhum tipo de insight em como utilizamos os bundlers, os problemas que eles resolvem ou como chegamos até eles.

## Apêndice: Código Gerado

O que se segue é apenas uma parte mais detalhada do 'como é realmente feito'. A ferramenta utilizada será o Browserify por ser uma ferramenta mais simples. Todo bundler funciona de uma maneira similar e produz resultados similares. A ideia aqui não é ver o código de forma detalhada, "a ideia aqui é ter uma ideia mesmo".

Digamos que um dos arquivos de Diêiés (algo chamado carregadorDeLink.js), possui o seguinte código:

<script src="https://gist.github.com/igoroctaviano/714bc433e78255ade5b11dfad91c3c9b.js"></script>

A maior parte do código foi tirado do exemplo, mas a parte interessante ainda está ali, a parte da importação e exportação de módulos. Então, executamos o Browserify nesse código e ele cospe um arquivo empacotado, um bundle, um pacote. Novamente, a ideia não é mostrar todo o resultado! Isso seria algo grande e visualmente poluído. Arquivo após simplificado, pós transformação:

<script src="https://gist.github.com/igoroctaviano/3debfa7bf26d23d15c54c9180e340350.js"></script>

Então isso é jogado em um objeto. Esse objeto vai ser passado para a função mencionada acima, essa cuja vai executar cada um dos módulos/expressões de função. A transformação é basicamente o ato de abraçar o código original do script e extrair as dependências que cada módulo requer nesse código. Ler cada linha onde há um **require** e colocar todos os nomes coletados em uma coleção de dependências, para mais tarde gerenciar esses módulos de forma correta.

É interessante notar que esse código é executado em um ambiente onde se tem acesso a três coisas:

1. uma função **require**.
2. uma referência **module**.
3. uma referência **exports**.

Isso é basicamente tudo que se precisa para que o código possa funcionar corretamente, de forma gerenciada, e é interessante que não importa muito o que são essas coisas e como elas funcionam em baixo nível. Precisamos apenas entender que elas fazem aquilo que você espera que elas fazem, e é isso. O carregamento pode acontecer como é feito aqui nesse exemplo, em um único arquivo empacotado/bundled, como também pode acontecer de forma diferente, carregando sob demanda através de uma requisição http ou em um sistema de arquivo (de forma assíncrona).

![](https://cdn-images-1.medium.com/max/600/1\*Tfa5Fuid6Vz6oByiBvlXsQ.png)

Imagem [Pixabay](https://pixabay.com/pt/users/bartek001-592579/)

## Uma curiosidade: webpack

> O webpack é um empacotador de módulos (bundler) para aplicações JavaScript modernas. Quando o webpack processa seu aplicativo, ele **cria recursivamente um grafo de dependência que inclui todos os módulos que sua aplicação precisa** e, em seguida, **empacota todos esses módulos em um pequeno número de pacotes** — muitas vezes apenas um — para ser carregado pelo navegador.

Para uma linguagem dinâmica, o JavaScript tem um sistema de módulo bem estático e isso vem com algumas regras limitantes.

* Todos os tipos de importação e exportação (import, export) são permitidos apenas no nível superior em um módulo (no topo de um arquivo). Não há importações ou exportações condicionais e você não pode usar a importação no escopo de uma função qualquer, por exemplo.
* Todas as coisas exportadas devem ser explicitamente exportadas por nome em seu script. Não é possível fazer um loop e exportar vários nomes de acordo com alguma lista de nomes ou algum outro dado.
* Os objetos de módulo (module/exports) estão petrificados. Não há como sair adicionando recursos em um objeto de módulo, tipo um [polyfill](https://developer.mozilla.org/pt-BR/docs/Glossario/Polyfill).
* Todas as dependências de um módulo devem ser carregadas, analisadas e vinculadas antes que qualquer código de algum módulo seja executado. Não há sintaxe própria para uma importação que possa ser carregada de forma [lazy](https://pt.wikipedia.org/wiki/Lazy_loading), sob demanda.
* Não tem jeito de tratar erros de importação. Um aplicativo pode ter vários módulos nele e, se algo não conseguir ser carregado ou vinculado no caminho, basicamente nada será executado. Você não pode importar dentro de um bloco try / catch, por exemplo.
* Não há algum tipo de gancho que permita que um módulo execute algum código antes que suas dependências sejam carregadas, ou seja, os módulos não têm controle sobre como suas dependências são carregadas.

Enfim, o sistema de modulos do JavaScript é muito legal desde que suas necessidades sejam estáticas. Mas você pode precisar de um pouco mais que isso, certo?

> A coisa toda aqui é que, como o sistema puro do ES6 é estático, ferramentas como **_webpack e outros_** bundlers parrudos possibilitam o dinamismo, como a execução de c**_ódigos_** antes de que suas dependências sejam carregadas e a detecção de erros em tempo de compilação.

> A sintaxe estática de módulos do JavaScript foi projetada para funcionar em conjunto com alguma API dinâmica e programática de um Module Loader.

> [Jason Orendorff](https://blog.mozilla.org/jorendorff/)

Por isso, o sistema de carregamento de módulos que você usa terá uma API programável para andar junto com essa sintaxe estática de importação / exportação do ES6. Por exemplo, o **webpack** inclui uma API que você pode usar para “quebrar o código” e carregar alguns pacotes de módulos sob demanda (lazy). **_A mesma API pode te ajudar a matar a maioria das outras regras limitantes que foram listadas acima_**.

A sintaxe de módulo do ES6 é muito estática, e isso de certa forma nos tem ajudado. Com a entrada dessas regras limitantes no advento dessa sintaxe estática de módulos, surgiu trabalho a ser feito no mundo web, e agora temos ferramentas poderosas que trabalham em tempo de compilação, como o **webpack** _e demais bundlers/compiladores parrudos_.

O **webpack** faz um monte de coisas, como a minificação de arquivos, gerenciamento de assets (css), em conjunto com scripts JavaScript. Ele roda [transcompiladores](https://en.wikipedia.org/wiki/Source-to-source_compiler) para transformar códigos em outros, como transformar o seu TypeScript em JavaScript, etc. E uma das coisas que é bem comum, eque podemos tirar dessa história toda, é que existe duas sintaxes ou duas formas de escrever código para importação e exportação de módulos, sendo a especificação CommonJS `require("algumaCoisa")` que o Node.js faz uso e o padrão [ESM](https://nodejs.org/api/esm.html) que está padronizado no ECMAScript (`import from "algumaCoisa"`). O webpack suporta as duas formas, transformando em tempo de empacotamento esses **imports** em **require**. Isso não é tudo que o webpack faz, existem diversas configurações e recursos como [caching](https://webpack.js.org/guides/caching/). Enfim, é uma ferramenta poderosa que disponibiliza várias configurações!

## É o tal de Module Bundlers e é o tal de Module Loaders…

Ah, só para deixar mais explicito ainda, o webpack, além de ser um bundler também é um module loader. Ele também é dito ser um compilador por alguns. O objetivo da galera ao utilizar o webpack é ter todos os assets do projeto colocados como responsabilidade do webpack e não do navegador (embora isso não significa que eles tenham que ser empacotados juntos). O webpack trata todo arquivo (.css, .html, .scss, .jpg, .etc.) como um módulo, mesmo que o webpack **entenda apenas JavaScript**. Então os Loaders (carregadores) que são utilizados no webpack, transformam os arquivos tratados como módulos, assim então eles vão sendo adicionados ao grafo de dependências.

O tempo voou em! chegamos no fim!

Espero que tenha pegado alguma coisa desse post, alguma ideia de como tudo isso surgiu, de qual foi a necessidade. Sei que é bem complicado começar um projeto web hoje em dia, tipo [Vue.js](https://vuejs.org/) ou [React](https://react.js/), eles vão exigir essas ferramentas. Ainda bem que alguns geradores de projeto já faz toda a configuração dessas ferramentas para nós. Muitas vezes é complicado entender todo esse ecosistema web, não se sinta só, é complicado mesmo, mas não é difícil, é possível entender e nada melhor do que uma história para começar o aprendizado!