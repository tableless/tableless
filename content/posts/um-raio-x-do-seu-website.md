---
title: Um raio-x do seu website
author: Alysson Franklin
type: post
date: 2011-03-03
excerpt: 'Ferramentas e metodologia para entregar mais e com maior qualidade. O Progressive Enhancement pode nos ajudar como mostramos em outros artigos. E hoje vamos mergulhar em um tópico específico da metodologia. '
url: /um-raio-x-do-seu-website/
tweetbackscheck:
  - 1356453572
shorturls:
  - 'a:3:{s:9:"permalink";s:48:"http://tableless.com.br/um-raio-x-do-seu-website";s:7:"tinyurl";s:26:"http://tinyurl.com/4x25fvk";s:4:"isgd";s:19:"http://is.gd/rxsqjn";}'
twittercomments:
  - 'a:9:{i:151327323508064257;s:7:"retweet";i:151236453039489025;s:7:"retweet";i:154255318610755584;s:7:"retweet";i:154254464201670657;s:7:"retweet";i:154253700964167680;s:7:"retweet";i:169584844064571392;s:7:"retweet";i:181826903370514433;s:7:"retweet";i:181824512231346176;s:7:"retweet";i:181822569626861570;s:7:"retweet";}'
tweetcount:
  - 13
dsq_thread_id: 503040040
categories:
  - Artigos
  - CSS
  - HTML
  - HTML5
  - JavaScript
  - JQuery
tags:
  - desenvolvimento web
  - Na Prática
  - padroes web
  - Semântica

---
A criacão de aplicações web evolui ao longo dos anos. A interação front-end/aplicação também segue esta evolução e é previsivel que a complexidade e a integração de funcionalidades com a interface web deva evoluir tambem. Só que para devs front-end, essa complexidade não está em novas linguagens ou tecnologias, e sim em como embarcar todas elas em um HTML semântico, limpo e de acordo com os requisitos. Tudo isso no menor tempo possível. Tempos ágeis, esses. As necessidades do cliente sempre não são compatíveis com nossos relógios e cada segundo vale nesse cenário.

Não é dificil abracarmos ferramentas que podem otimizar o nosso tempo. Fazer um mockup ou mesmo os primeiros protótipos sem usar Zen Coding podem ser tarefas demoradas. O Diego [já mencionou isso][1] aqui no Tableless há quase um ano e não é dificil vermos o pessoal maravilhado quando clicamos no tab e de repente a &#8220;mágica&#8221; acontece, montando um HTML inteiro. Não usar boilerplates ou grids pode ser fator determinante na demora no período de homologação. Mas até aí estamos falando apenas das ferramentas, e elas não são nada sem o conhecimento do desenvolvedor, somado a suas metodologias de trabalho. Nesta fase inicial de projeto, enviar uma arte para aprovação do cliente e algumas horas depois de aprovado já apresentar um modelo funcional básico, HTML/CSS com certeza pode garantir que o relacionamento cliente/desenvolvedor possa ser mais &#8220;tranquilo&#8221;, com uma pressão bem diferente se entre aprovação e o primeiro mockup tivermos um intervalo de um dia, por exemplo.

Só que isso não é tudo, é apenas a ponta do iceberg. Montar um mockup é o início do trabalho para garantir que esse design e as funcionalidades pedidas pelo cliente funcionem da mesma maneira, na maior gama de navegadores e dispositivos possível, e mesmo com suas limitações, oferecer a mesma experiência para os usuários. E isso é doloroso e nos toma muitas noites de sono que a gente teima em descontar xingando um ou outro navegador.

O Progressive Enhancement pode nos ajudar como mostramos em outros artigos. E hoje vamos mergulhar em um tópico específico da metodologia: iremos aprender como usar a perspectiva Raio-X para desconstruir uma página, separando o conteúdo do markup, usando abordagens top-bottom e bottom-up respectivamente. Dito isso vamos em frente que atras vem gente &#8211; e prazos cada vez mais apertados!

A Perspectiva Raio-X é baseada no princípio de que mesmo o mais complexo design – mesmo que seja algo dinâmico, como aplicações com AJAX com comportamentos estilo desktop – conteúdo e funcionalidade possam ser expressados com um simples HTML semântico, oferecendo uma experiencia acessivel e com Usabilidade para toda audiência.

Essa perspectiva nada mais é do que um metodo para planejarmos o design (sim, podemos usá-la para o design também) e desenvolvimento de modo a garantir, antes mesmo de começar, premissas que vão ser MUITO mais fáceis de seguir ao longo do desenvolvimento do projeto, afinal garantir acessibilidade e usabilidade desde o inicio é muito mais facil do que lá na frente, com tudo pronto, abracar o Graceful Degradation e um bom tempo brigando com javascripts que teimam em funcionar em um navegador e outro não. Você ainda terá que fazer isso, é fato. Mas é muito melhor trabalhar em um pequeno pedaço de código lá na frente do que descobrir que alterar um método desencadeará um efeito dominó que vai fazer você perder muito tempo entendendo o comportamento do script atraves da funcionalidades de uma aplicação.

Como o foco aqui é o desenvolvimento e não o design, partimos da premissa que já temos um design com funcionalidades e uma experiência que o visitante vai ter caso use o _navegador do momento_. Com esse design em mãos, antes de começar a codificar, planejamos um processo de desenvolvimento dividido em 3 partes:

  1. Definir a hierarquia do conteúdo e sua prioridade, mapeando componentes para encontrarmos elementos básicos no HTML equivalentes a esta componentização.
  2. Criar um markup de fundação, oferecendo todo o conteúdo essencial e funcionalidade com o mínimo de CSS(garantindo que o usado sejam &#8220;atributos seguros&#8221;) e ZERO de javascript.
  3. Escrever o markup avançado, com CSS e javascript para cuidar da camada visual e funcional de acordo com as funcionalidades que cada navegador suporta.

Vale lembrar que essa experiencia é interativa, e mudanças no markup de fundação podem acontecer a medida que limitações no código são encontradas de acordo com os navegadores ou dispositivos testados. Mas estas mudanças serão pequenas e de fácil implementação, uma vez que todo o desenvolvimento foi planejado para minimizar este tipo de impacto.

### **Definindo Hierarquia de Conteúdo e mapeando componentes para o HTML**

Algumas perguntas podem ser feitas para ordenar o fluxo de trabalho nesta fase do processo, elas vão ajudar a estabelecer regras e normas de inteface, centralizando estilo e regras de comportamento funcional no processo de desenvolvimento. Analisando o design, vamos aprofundar a analise pelos componentes visuais no trabalho. A partir da sala, comecamos nosso top-down:

  * Quais são as partes mais importantes da página?
  * O quanto de conhecimento sobre o assunto a audiência precisa para entender a informação da página? Há informação suficiente para este entendimento?
  * Existe uma ordem literal ou implícita para ordenar este conteúdo?
  * Olhando o site como um todo, existem partes em comum, com funcionalidades ou padrões de comportamento que podem ser reutilizados com templates?
  * Existe alguma tarefa que precisa ser feita na página? Se sim, quais são os passos que a audiência deve seguir e quais ferramentas ou plugins ela deve usar até completar estes requisitos? Existem passos adicionais/opcionais/mandatórios?
  * Existe conteúdo ou fluxo de pagina/formulários que dependam de opções previamente inputadas pela audiência?

Até aí estamos olhando apenas a sala. O código também precisa de uma abordagem parecida. É hora de olharmos a cozinha da aplicação e fazermos nosso bottom-up:

  * Existe algo que é inserido dinamicamente via AJAX? Se sim, temos que oferecer uma opção acessível, com conteúdo similar inserido na página ou em um HTML em separado;
  * Existem partes na interface que dependem de um workflow de escolhas aonde uma escolha determina opções em outra, ou ainda dependa de conexões já feitas em um servidor para validar o fluxo? Se sim, temos que ter certeza que estas experiências estao devidamente segregadas na versão básica da pagina, ajudando usuários a serem mais eficientes na tarefa da cognição, minimizando erros e complicações.
  * Existem partes na interface que são complicadores devido a alto grau de consumo de banda ou dificuldade de uso para uma experiência básica que são construidas apenas com markup HTML? Se sim, podemos oferecer componentes simplificados no markup de fundação ou ainda encorajar usuários básicos a viver a experiência através de uma alternativa offline.

Com estas duas análises da sua aplicação, fica fácil fazer o mapeamento dos componentes na página e quais elementos básicos do HTML melhor suportam a causa-fim. Ao mesmo tempo, analisamos como implementar o CSS e o Javascript a este markup. Se é necessário algum trabalho adicional para garantir a acessibilidade, é o momento de analisar a abordagem a ser usada. Com isso temos definido a hierarquia de conteúdo e seus agrupamentos, funcionalidade de todos os elementos de página associados a elementos básicos HTML, garantindo markups e estilos mínimos para uma expêriencia básica que todos os usuários &#8211; independentes de navegador ou dispositivo possam ter. A partir daí trabalhamos estilos e scripts a serem incorporados a experiência básica, tratados como um expansão que o usuário pode viver dependendo do seu navegador.

### **HTML4 x HTML5 – Ganhando tempo**

O W3C ainda esta incorporando funcionalidades ao HTML, mas isso não significa que você não pode usar o HTML5 dependendo dos requisitos do projeto. De fato o HTML5 melhora e muito a produtividade, incorporando melhorias na linguagem que salvam tempo na criacao de componentes (como placeholders no input, datepickers avançados, players de áudio e vídeo, para mencionar alguns), porém com o foco em Progressive Enhancements, é necessario manter o foco na usabilidade &#8211; um player de vídeo por exemplo precisa de um plano de fallback para navegadores que não suportam o HTML5, como o IE6 (na ausência do suporte, um player flash pode ser carregado).

Pesquisas com desenvolvedores indicando o que tem sido codificado e colocado em produção mostram que as implementações estão a todo vapor. Por ordem de popularidade e facilidade na implementação:

  1. Semântica
  2. Melhorias de formulário
  3. Áudio / Vídeo
  4. Canvas
  5. Outros
  6. Drag and Drop
  7. Microdata
  8. Geolocation
  9. Offline Storage
 10. Cross Document Messaging

O uso depende de estudo. Quanto mais direcionado for o escopo do projeto, mais você poderá tirar vantagem do HTML5. Separando o HTML5 em 3 partes distintas, teriamos:

  * **Nível 1:** elementos que ganharam nova semântica, a maior parte deles sem nenhuma mudançaa drástica &#8211; exceção ao elemento deâncora <a>, que agora permite nao apenas links inline (no contexto linear, uma frase por exemplo), mas tambem links em bloco. Fazendo com que em determinadas situações <a> possa ter o mesmo comportamento de um <div> por exemplo. Estas melhorias são amplamente suportadas pelos browsers e não tem porque não utilizarmos as mesmas. Podemos mencionar a sintaxe simplificada, redução nas chamadas de DOCTYPE, charset, <script> e <style> e os atributos type, alem da não necessidade de fechar tags para elementos self-closing (/>) 
  * **Nível 2:** Alguns extras que já não são garantidos em todos os navegadores. Algumas intervenções serão necessárias para implementar este nível, mas nada muito complicado que possa oferecer riscos de impacto ao design. Por default, estas funcionalidades são atingidas pelo Graceful Degradation (ex.: uma caixa <input type=&#8221;range&#8221;> em navegadores sem suporte se transformam em caixas comum de texto. Nada que não possa ser resolvido com um pouco de javascript.
  * **Nível 3:** Tudo o que não foi mencionado antes. Infelizmente são solucoes que ainda precisam de intervenções para termos escalabilidade. Alguns deles possuem já soluções consagradas (como os já mencionados Boilerplates e Grids) e garantem escalabilidade em navegadores que não oferecem suporte. Tags para diagramação de conteúdo como <section>, <article>, <nav>, <aside>, <header>, <footer> ; tags para elementos inline <mark>, <time> ; tags para elementos dinamicos como <audio>, <video>, <details>, <canvas> são suportadas via document.createElement ou boilerplate. As APIs tambem chegam para oferecer possibilidades infindáveis mas novamente, cuidado e análise neste nivel são coisas fundamentais.

Combinar o HTML5 com metodologias como o Progressive Enhancement é um grande diferencial, e, dominando as ferramentas, fica facil entregar mais com menos &#8211; e com maior qualidade. Pronto para tirar uma _chapa_ de suas páginas e começar a analisar o que pode ser otimizado?

### Referências

  * [Tableless &#8211; Editores e Snippets][1]
  * [zen coding][2]
  * [html5 boilerplate][3]
  * [960 grid][4]
  * [Designing w/ Progressive Enhancement][5] (esse ja é um clássico)
  * [HTML5 Features in use on Production Sites][6]
  * [A Form of Madness][7]
  * [3 levels of HTML usage][8]

 [1]: http://tableless.com.br/produtividade-editores-e-snippets
 [2]: http://code.google.com/p/zen-coding/
 [3]: http://br.html5boilerplate.com/
 [4]: http://sixrevisions.com/web_design/the-960-grid-system-made-easy/
 [5]: http://filamentgroup.com/dwpe/
 [6]: http://css-tricks.com/poll-results-html5-features-in-use-on-production-sites/
 [7]: http://diveintohtml5.org/forms.html
 [8]: http://mathiasbynens.be/notes/html5-levels