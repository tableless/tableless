---
title: O fim da profissão front-end
author: Diego Eis
type: post
aliases:
  - /?p=57364
image: uploads/2017/03/pexels-photo-296983-2.jpg
date: 2017-03-20
excerpt: O front-end como você conhece vai morrer.
categories:
  - Artigos
  - Opinião
  - Código
  - JavaScript
  - ReactJS
  - Tecnologia e Tendências
---

O processo de desenvolvimento web pode se dividir em três categorias: design, front-end e back-end. Na minha opinião, a categoria que tem mais processos manuais e repetitivos é sem duvida o front-end.

Pare pra pensar: o core do trabalho do front-end se resume em duas partes:

  * **implementação do layout**: produção da primeira camada de código, onde replicamos o layout criado em algum programa gráfico, para código estático em HTML, CSS e JS.
  * **integração com API**: depois (ou junto, tanto faz) de feito o código estático, a interface é integrada com a API, que geralmente carrega boa parte da lógica, já que essa mesma API é usada para alimentar outras plataformas como mobile, robôs etc.

As outras &#8220;responsabilidades&#8221; que orbitam em volta do front-end como acessibilidade, SEO, performance, compatibilidade entre browsers, código semântico, entre outras coisas que você pode julgar serem de responsabilidade de um front-end **são um mero apetrecho**. Elas podem existir ou não em um projeto. Mas um projeto não sobrevive sem o código front-end do layout e sem o conteúdo integrado à interface.

_Um observação: acessibilidade é algo que as máquinas podem fazer muito melhor que um ser humano. Embora eu tenha colocado como algo que possa existir ou não em um projeto, é importante demais que você faça um esforço para que todos os seus projetos sejam acessíveis. Eu sei que isso não é a realidade até hoje no mercado e provavelmente nunca será até que esse processo seja automatizado._

Existem uma série de tarefas manuais que nós delegamos para ferramentas criadas afim de economizar parte do nosso tempo evitando a execução de tarefas repetitivas, automatizando o workflow do front-end. Só para citar algumas:

  * **Pre-processadores CSS:** Sass, Less, Stylus
  * **Task runners:** Gulp, Grunt , Make, NPM Scripts
  * **Scaffolding:** Yeoman, Slush
  * **Dependências/Module Bundles:** Bower, NPM, Yarn, Webpack, Duo, RequireJS, Browserify, JSPM, Rollup
  * **SPA/Libraries/Frameworks:** React, Angular, Vue.js, Backbone, EmberJS, todomvc, Polymer, Lodash, Aurelia, MeteorJS
  * **CSS Frameworks/Libraries:** SemanticUI, Bootstrap, Foundation, UiKit, YUI, Susy
  * **JS Test**: Mocha, Jasmine, QUnit, Ava, Tape, Jest
  * **JS Templates:** Underscore, Mustache, Handlebars, DoT, Dust, EJS

Mas mesmo com todas essas ferramentas, o core da responsabilidade de um front-end ainda continua sendo **implementar layout original** e **integrar a interface com o back-end**. Você ainda continua **replicando** o layout que alguém passou dias desenhando e integra o conteúdo que está numa API, que outra pessoa criou. Seu dia se resume em alternar entre as janelas do Sublime / Sketch / Browser / Sublime / API / Browser / Sublime.

> &#8220;Automation isn&#8217;t about being lazy. It&#8217;s about being efficient.&#8221; &#8212; Addy Osmani

Esse processo se torna tedioso e a lista de requisitos para tentar tornar o trabalho de front-end eficiente só aumenta. Toda tarefa mecânica, repetitiva e manual tende a ser automatizada e na minha opinião, em pouco tempo, **não vamos precisar de alguém executando o trabalho de front-end de ponta a ponta**.

Okay, respira. Isso é a minha opinião. Dado que o front-end é a parte mais operacional de todo o processo, mais cedo ou mais tarde todo o trabalho executado no front-end vai ser automatizado. A parte mais difícil são essas duas tarefas que nós fazemos desde os primórdios. Contudo, elas já podem estar com seus dias contados.

## Trabalhando com dados reais direto no Design

Você pode não ser designer, mas há uma premissa no mundo dos designers que diz que **você deve trabalhar sempre com conteúdo real**. Isso quer dizer que entregar um layout com texto em _Lorem Ipsum Dolor_ é coisa de designer júnior.

> &#8220;If your site or application requires data input, enter real and relevant words and type the text, don’t just paste it in from another source.&#8221; &#8212; Jason Fried

A ideia é que você crie um layout da forma mais fiel possível usando os termos, palavras, nomes, datas etc, afim de chegar mais perto da experiência do usuário.

Atualmente a maioria dos programas visuais utilizados para criar layouts para web tem alguma feature ou plugin que permite a integração com alguma fonte de dados que contenha o conteúdo real.

Por exemplo o Sketch, que é o programa de criação visual mais querido do momento, conta com plugins que permitem a integração direta entre API e layout. Veja por exemplo o vídeo abaixo demonstrando a utilização do plugin Craft (também disponível para Photoshop):



Ou essa demonstração que usa a API do Stackoverflow:



> Em pouco tempo, não vamos precisar de alguém executando o trabalho de front-end de ponta a ponta.

O ponto aqui é: nós só precisamos criar o layout uma vez, usando o programa desejado (Sketch/Photoshop/Figma/Adobe XD etc) e pronto. Não precisamos de uma pessoa para refazer esse layout com HTML/CSS/JS de forma alguma. Isso nos leva para uma segunda discussão: mesmo com o design pronto, usando dados reais de uma API, nós ainda precisamos que ele seja acessível pelos browsers. Como resolvemos isso?

_Obs.: E aquele movimento do &#8220;Design in the Browser&#8221;? Esse é um movimento criado exatamente para evitar o trabalho de produzir duas vezes o mesmo layout. Mas é MUITO melhor fazer um design usando um programa visual do que escrever direto no código. IMHO._

## Código bonito não é importante

Desde sempre os front-ends escrotizavam o código que era gerado automaticamente por programas como o Dreamweaver. Eles tinham uma razão pra isso: o código era completamente horrível. Era um tempo onde a conexão com a internet era precária e tudo o que pudéssemos fazer para melhorar o carregamento do site, nós fazíamos. O código gerado por programas Wysiwyg tinha vários problemas: era difícil de ler, não havia semântica alguma, continha código inútil e muitas vezes não era compatível com todos os browsers. Tudo isso fazia com que o código limpo, semântico, enxuto e acessível tivesse um valor inestimável.

Código limpo era sinônimo de bom ranking no Google, boa compatibilidade entre os browsers, performance de carregamento garantida, produtividade entre os membros do time por causa da legibilidade do código, facilidade de manutenção etc etc etc.

Hoje, boa parte desses problemas foram resolvidos:

  * os browsers tem uma ótima complacência com os padrões web, extinguindo a maioria dos problemas de compatibilidade de layout;
  * a performance é atacada em várias frentes: processo de build dos assets, tecnologias como HTTP/2 e até a evolução da conexão que fica mais rápida a cada ano;
  * a manutenção e a legibilidade do código HTML/CSS não é mais um problema sério, já que o HTML é facilmente escrito usando poucas tags e o CSS tem os pré-processadores, que auxiliam muito na hora de definir padrões, além das boas práticas;
  * o JS está bem assessorado por frameworks, libraries e uma série de boas práticas que se responsabilizam pela parte pesada do trabalho, deixando pouca margem de erro para os devs;
  * e o mais importante para mim é que a semântica não está mais no HTML. Desde a vinda de tecnologias com o JSON-LD, a semântica não está mais atrelada ao código HTML e isso é ótimo;

Eu sei que mesmo que grande parte da responsabilidade fique na mão dos frameworks, bibliotecas e ferramentas, o dev tem grandes chances de fazer merda com o pedaço de código que ele cuida. Não olha pro seu amiguinho do lado, coitado&#8230; Todos nós cometemos erros&#8230; uns mais, outros menos.

Mas entenda uma coisa: **código bonito, não é mais algo importante**. As ferramentas que nos auxiliam hoje para buildar os assets podem ser usadas por programas/robôs ao criar automaticamente código HTML/CSS/JS a partir de layouts produzidos em programas como Sketch. Veja por exemplo [esse plugin][1] que não é mais atualizado desde 2015 já tentava automatizar a exportação de código no Sketch. O cara estava tentando fazer código HTML a partir do layout desenhado no Sketch versão 3. Hoje o Sketch está na versão 42. E sabe de uma coisa: na versão 43 o Sketch está abrindo o código dos seus arquivos em formato JSON. O que nos leva para o próximo assunto.

### Automatização do Design

_We have a new file format which is more compact, and enables more powerful integrations for third-party developers. &#8212; [Sketch Team][2]_

Isso quer dizer que o Sketch se transformará em uma plataforma de desenvolvimento. Abrindo o código dos seus arquivos, qualquer um conseguirá ler esses arquivos e partir daí criar **qualquer coisa**. Quanto tempo para alguém criar um plugin que lê o arquivo do Sketch em formato JSON e **gera automaticamente HTML/CSS/JS** a partir de um layout Sketch?

> Computadores evoluem. Se os princípios mudassem não haveria base para a evolução. &#8211; Caio Vaccaro

Okay, mas espera aí: mesmo antes desse formato novo de arquivo do Sketch, já existia algumas ferramentas que talvez você não conhecia como o [Teleport][3], que converte **qualquer website** em um artboard do Sketch. E também o [UIPad][4], que converte layout do Sketch em HTML/CSS e React! Se liga:



Essa tendência já estava sendo desenhada há tempos. É a coisa mais inteligente de se fazer. Você pode fazer coisas mais importantes do que ficar sentado na frente do computador alternando entre browser, layout, browser, layout.

Okay: nós temos um design que se integra com a API, puxando dados reais do sistema. Nós temos um programa que design que exporta o layout para código HTML/CSS/JS pronto para ser usado. Mas ainda estamos usando código HTML/CSS/JS como antigamente. Há mais um passo que pode ser melhorado.

### WebAssembly (Wasm)

Outro ponto importante, que não tem nada definido ainda, mas que pode começar a fazer todo sentido é toda aquela [história do WebAssembly][5], que é um novo formato binário criado pelo Google Microsoft, Mozilla e vários outros.

O formato de código binário do WebAssembly pode ser decodificado muito mais rápido do que o JavaScript é parseado. Isso realmente traz para a Web a experiência de programas nativos, principalmente no mobile.

O legal é que outras linguagens podem ser compiladas para WebAssembly. Hoje o projeto está um pouco mais focado em C/C++, mas com certeza outras linguagens serão abrangidas. O objetivo principal do WebAssembly é a performance.

Uma preocupação que surge no ar é que isso cheira monopólio. Lembra do Flash? Querendo ou não ele era uma alternativa de criar algo nativo na Web. Mas a graça é que:

  1. WebAssembly não substitui o JavaScript. Tudo tem retrocompatibilidade, tudo será executado no mesmo universo que o JS e a segurança terá as mesmas restrições que o JS;
  2. Não é só uma empresa ou grupo que está por trás do Wasm, mas várias como Firefox, Chromium, Edge e Webkit;
  3. Para rodar WebAssembly não será necessário rodar plugins de terceiros, já que os motores dos browsers serão totalmente compatíveis;

Está entendendo por que buscar por um código limpo (como conhecemos hoje) não faz mais tanto sentido?

## Conclusão

Mais cedo ou mais tarde a profissão de front-end como nós conhecemos até hoje **vai deixar de existir**. Você que já é velho na área, talvez nem precise se preocupar, porque eu não acho que isso vai acontecer agora, mas você que acabou de começar, é melhor pensar duas vezes no futuro da sua carreira.

Eu tenho certeza que a área de back-end também pode passar por esse processo, embora seja muito mais difícil de acontecer. E eu também acho que vai demorar muito (se chegar a acontecer) a automatização da parte criativa responsável pelo design dos layouts de produtos e websites.

Eu não chuto em quanto tempo isso pode acontecer ou se vai acontecer. É mais um chute meu do que qualquer outra. Quero só abrir para discussão esse assunto. Mas até ontem [carros e caminhões autônomos][6] eram coisa de filme.

Mas com certeza existem vários pontos ainda a serem resolvidos:

  * A automatização de sites gigantes de conteúdo vai ocorrer?
  * E sistemas/produtos, como vamos fazer?
  * Coloque aqui sua dúvida maluca&#8230;

Minha outra aposta é sobre a profissão de UX, que vai desaparecer não porque suas responsabilidades serão automatizadas, mas por se tornar obsoleto mesmo. Esse é assunto para um outro artigo, mas se quiser pensar sobre isso agora, comece ouvindo [esse capítulo do podcast do Movimento UX][7] com o [Felipe Memória][8].

## Para ler mais

**Dados reais no design**

  * [3 Easy Steps for Working with Realistic Data in Sketch Using JSON][9]
  * [Designing with Data][10]
  * [Prototype with real data in Framer, from JSON to multi-device and internet of things][11]
  * [Adobe XD: Designing with Real Data][12]

**Sobre não usar texto fake em layouts**

  * [Lorem Ipsum is Killing Your Designs][13]
  * [Why designers should never use fake text][14]
  * [Stop using Lorem Ipsum!][15]
  * [&#8220;Getting Real&#8221; design tip: Just say no to Lorem Ipsum][16]

**WebAssembly**

  * [FAQ do site WebAssembly][17]
  * [WebAssembly – a web compilada][5]
  * [Google, Microsoft, Mozilla And Others Team Up To Launch WebAssembly, A New Binary Format For The Web][18]
  * [WebAssembly e o futuro da Web][19]
  * [From asm.js to webassembly][20]
  * [The Web is getting its bytecode: WebAssembly][21]

**Sobre o cenário das ferramentas de front-end**

  * [front-end.directory][22]
  * [Using front-end build tools][23]
  * [A Collection Of Best Front End Frameworks][24]
  * [GitHub: Front-end JavaScript frameworks][25]
  * [Front-End Tooling Trends for 2017][26]
  * [Updated List: The 67 Very Best Front End Web Developer Tools][27]
  * [The most popular JavaScript front-end tools][28]
  * [Top 10 Templating Engines for JavaScript To Improve and Simplify Your Workflow 2017][29]
  * [Automating Front-end Workflow][30]
  * [Javascript State of the Union 2015, parte 3][31]
  * [Slides &#8211; Javascript State of the Union 2015][32]
  * [The State of Front-End Tooling 2016 &#8211; Results][33]
  * [Front-end Roles and Responsibilities][34]

 [1]: https://github.com/sskyy/blade
 [2]: https://rink.hockeyapp.net/apps/0172d48cceec171249a8d850fb16276b
 [3]: https://protoship.io/tools/teleport.html
 [4]: https://protoship.io/tools/uipad.html
 [5]: https://tableless.com.br/o-webassembly-vem-ai/
 [6]: https://www.wired.com/2016/10/ubers-self-driving-truck-makes-first-delivery-50000-beers/
 [7]: http://movimentoux.com/work/felipememoria/
 [8]: http://www.fmemoria.com.br/
 [9]: https://www.shopify.com/partners/blog/91010886-3-easy-steps-for-working-with-realistic-data-in-sketch-using-json
 [10]: https://medium.com/@markjenkins/designing-with-data-7f6bcd907f0a#.95haya5yq
 [11]: https://blog.framer.com/prototype-with-real-data-in-framer-from-json-to-multi-device-and-internet-of-things-6eb1ae8b8325#.fo9b8i4gz
 [12]: https://medium.com/@anirudhs/project-comet-designing-with-real-data-959beccb5c1a#.v6khfndrh
 [13]: https://www.smashingmagazine.com/2010/01/lorem-ipsum-killing-designs/
 [14]: https://thenextweb.com/dd/2015/04/09/why-designers-should-never-use-fake-text/#.tnw_zjSSHkxh
 [15]: http://www.creativebloq.com/design/stop-using-lorem-ipsum-7116907
 [16]: https://signalvnoise.com/archives/001083.php
 [17]: http://webassembly.org/docs/faq/
 [18]: https://techcrunch.com/2015/06/17/google-microsoft-mozilla-and-others-team-up-to-launch-webassembly-a-new-binary-format-for-the-web/
 [19]: https://jaydson.com/webassembly-e-o-futuro-da-web/
 [20]: https://brendaneich.com/2015/06/from-asm-js-to-webassembly
 [21]: https://arstechnica.com/information-technology/2015/06/the-web-is-getting-its-bytecode-webassembly/
 [22]: https://frontend.directory/
 [23]: http://radify.io/blog/using-build-tools/
 [24]: http://usablica.github.io/front-end-frameworks/compare.html
 [25]: https://github.com/showcases/front-end-javascript-frameworks?s=stars
 [26]: https://www.sitepoint.com/front-end-tooling-trends-2017/
 [27]: http://blog.debugme.eu/front-end-web-developer-tools/
 [28]: https://techbeacon.com/most-popular-javascript-front-end-tools
 [29]: https://colorlib.com/wp/top-templating-engines-for-javascript/
 [30]: https://speakerdeck.com/addyosmani/automating-front-end-workflow
 [31]: https://medium.com/@caiovaccaro/javascript-state-of-the-union-2015-parte-3-281aa04bece1#.bulta9j6j
 [32]: https://www.slideshare.net/Hugeinc/javascript-state-of-the-union-2015
 [33]: https://ashleynolan.co.uk/blog/frontend-tooling-survey-2016-results
 [34]: https://hackernoon.com/front-end-roles-and-responsibilities-6ee8654f1649#.gsg5zdjtr
