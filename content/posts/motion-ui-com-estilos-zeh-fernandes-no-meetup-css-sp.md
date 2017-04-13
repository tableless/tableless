---
title: 'Motion UI com estilos: Zeh Fernandes no Meetup CSS SP'
author: Danilo Vitoriano
type: post
date: 2015-06-23
excerpt: A experiência em participar de um Meetup sobre Motion UI.
url: /motion-ui-com-estilos-zeh-fernandes-no-meetup-css-sp/
categories:
  - CSS
  - CSS3
  - Design
  - UX
tags:
  - animações css3
  - CSS
  - motion UI

---
Reunir a galera em eventos talvez seja a melhor maneira de manter-se atualizado e trocar conhecimento: você conhece pessoas que fazem a mesma coisa que a gente, soluciona dúvidas, pode discutir novas abordagens em torno de um tema e ainda reforça o _network_.

Neste artigo no Tableless, quero compartilhar a experiência de participar de um **Meetup** e comentar sobre a palestra do **Zeh Fernandes** sobre **Motion UI**.

## Meetup CSS SP

<img class="aligncenter size-full wp-image-49710" src="http://tableless.com.br/uploads/2015/06/logos-meetup-css-sp.jpg" alt="Logos Meetup e Meetup CSS SP" width="474" height="200" />

Excelente ferramenta para manter-se informado sobre os eventos que acontecem perto da sua cidade e com temas relacionados ao seu interesse, o **<a href="http://www.meetup.com/pt/" target="_blank">Meetup</a>** mescla site e aplicativo, permitindo a qualquer pessoa organizar e divulgar eventos e encontros em torno de qualquer tema. Eu já conhecia o site, mas só recentemente passei a acessá-lo com frequência. Foi quando descobri o **<a href="http://www.meetup.com/pt/CSS-SP/" target="_blank">Meetup CSS SP</a>**, comunidade organizada por **<a href="http://twitter.com/raphaelfabeni" target="_blank">Raphael Fabeni</a>** e **<a href="http://twitter.com/lfeh" target="_blank">Felipe Fialho</a>** que promove encontros para discutir assuntos do mundo front-end, com foco principalmente na linguagem de marcação CSS.

## Zeh Fernandes

Na 8ª edição do **Meetup CSS SP**, realizada no começo de junho de 2015, o tema foi a palestra do **<a href="https://twitter.com/zehf" target="_blank">Zeh Fernandes</a>** sobre **_Motion UI_ com estilos**. O Zeh pode ser definido, segundo ele mesmo, como um designer zen. Seus trabalhos podem ser vistos na <a href="https://www.behance.net/gallery/Project-Cliche/12708243" target="_blank">revista Cliche</a>, na rede colaborativa de troca de tempo <a href="http://www.bliive.com/" target="_blank">Blive</a> e nas criações da produtora digital **<a href="http://d3.do/" target="_blank">D3.do</a>, **que cedeu o local para que o encontro acontecesse. O Zeh já havia apresentado a mesma _talk_ na **<a href="http://www.conferenciacssbrasil.com.br/" target="_blank">Conferência CSS Brasil</a>** realizada em São Paulo, mas a experiência em um _Meetup_ é mais interessante, pois só quem se interessa especificamente pelo assunto participa do encontro, e ainda rolam conversas e debates após a apresentação (o que é muito produtivo para trocar experiências).

## _Motion UI_ com estilos

No fim deste artigo, você pode conferir os slides da apresentação feita pelo Zeh, além do vídeo com a gravação realizada pelo <a href="http://twitter.com/matmarsiglio" target="_blank">Matheus Marsiglio</a> e algumas fotos do encontro. O propósito deste texto não é transcrever a palestra, mas apenas reforçar os pontos principais apresentados.

### A morte do Flash e o nascimento do _Flat Design_

Desde que os sites feitos em Flash desapareceram, a web carecia de animação. Seu fim parecia estático, salvo pelos efeitos _mouseovers_ que provocavam certo tipo de resposta para a interação, ou pelos _gifs_ animados e vídeos, estes últimos, com sua utilização limitada.

O surgimento do _flat design,_ em contrapartida com a era do <a href="https://pt.wikipedia.org/wiki/Esqueumorfismo" target="_blank">esqueumorfismo</a>, reforçava ainda mais a simplicidade da web. Eis que surge o HTML5 e o CSS3, trazendo novos recursos, dentre eles, as animações feitas principalmente com os elementos _transform_, _transition_ e _animation_ (confira este <a href="http://tableless.com.br/transition-e-animation/" target="_blank">post</a> do Rapahel Fabeni sobre _transition_ e _animation_ para saber mais).

Surgiram botões animados, sites com efeitos _<a href="http://tableless.com.br/parallax-simples-com-jquery-e-css/" target="_blank">parallax</a>_, caixas animadas, animações de SVG, e tudo tomou vida novamente. Porém, assim como aconteceu com o Flash, alguns sites perderam o bom senso, usando os novos recursos apenas por usar, ou seja, apenas para dar aquela &#8220;animada&#8221; na página, muitas vezes, apenas cumprindo a demanda do cliente.

### Animações com significado

> A animação é uma camada que ajuda a interface a comunicar-se com o usuário.

Ela ajuda o cérebro a compreender como a informação deve ser entendida. Deve ser utilizada com cautela, com propósito e com significado. Alguns itens interessantes levantados pelo Zeh para o uso consciente de animações podem ser listados a seguir:

  * Antecipar a ocorrência de determinado comportamento
  * Chamar a atenção para conteúdo específico
  * Oferecer contexto sobre o que está acontecendo
  * Oferecer _feedback_ sobre algo
  * Reforçar a identidade da marca (_branding_)

### Código e propriedades

Como dito anteriormente, os principais elementos utilizados pelo CSS3 para criar animações são as propriedades _transform_, _transition_ e _animation_ do CSS, com uso adicional dos _keyframes_. Javascript ou jQuery podem ser utilizados ocasionalmente, mas não são obrigatórios.

Para saber mais sobre o que faz cada uma destas propriedades, o Raphael Fabeni criou uma <a href="http://www.raphaelfabeni.com.br/lab-css3/" target="_blank">lista</a> resumindo as possibilidade de animações do CSS3:

<a href="http://www.raphaelfabeni.com.br/lab-css3/" target="_blank"><img class="alignnone wp-image-49698 size-full" src="http://tableless.com.br/uploads/2015/06/lab-css3-raphael-fabeni.png" alt="Lab CSS3 Raphael Fabeni" width="1085" height="710" /></a>

Já as principais propriedades de um elemento a serem modificadas por uma animação são _Position_, _Transform_, _Opacity_ e _Color_.

<img class="aligncenter wp-image-49699 size-full" src="http://tableless.com.br/uploads/2015/06/propriedades-alteradas-por-animacoes.png" alt="Propriedades alteradas por animações" width="610" height="162" />

Uma dica valiosa dada por <a href="https://twitter.com/aprilzero" target="_blank">A</a><a href="https://twitter.com/aprilzero" target="_blank">nand</a> <a href="https://twitter.com/aprilzero" target="_blank">Sharma</a> é:

> Se você precisa utilizar mais elementos do que apenas opacidade e transformação, repense sua animação.

### Performance

Outro fator importante a ser considerado ao utilizar animações é performance, e por isto a última dica é tão importante. Alterar propriedades como posição, cores e determinados efeitos dos elementos de uma página requer alto processamento e uso de memória animando as camadas _Layout,_ _Paint_ ou _Paint Setup_. Para isso, recomenda-se priorizar a utilização da camada _Composite Layers_. Ela é uma abstração das demais camadas do DOM, utilizada principalmente pelas propriedades _transform_ e _opacity, _e não interfere nas demais, usando poucos processamento ao modificar os elementos da página.

As camadas e suas respectivas propriedades:

<img class="alignnone wp-image-49700 size-full" src="http://tableless.com.br/uploads/2015/06/camadas-e-propriedades-animcao.png" alt="Camadas e suas respectivas propriedades" width="804" height="505" />

Este comparativo retirado da apresentação **<a href="http://pt.slideshare.net/hugobessaa/performance-em-animacoes" target="_blank">Performance em Animações</a>** do **Hugo Bessa** mostra o processamento exigido por cada cada camada alterada nas animações:

<a href="http://pt.slideshare.net/hugobessaa/performance-em-animacoes" target="_blank"><img class="alignnone wp-image-49701 size-full" src="http://tableless.com.br/uploads/2015/06/composite-layers-hugo-bessa.png" alt="Comparativo de performance nas camadas de animação por Hugo Bessa" width="1007" height="703" /></a>

### _Easing_ e _Timing_

Duas variáveis importantes em qualquer animação são os efeitos da gravidade e suavidade (_easing_) e o tempo de duração das animações (_timing_).

O **_easing_** pode ser entendido como a aceleração ou desaceleração inicial ou final, comumente observada pela física nos movimentos tradicionais do nosso dia-a-dia. Por exemplo, os automóveis, ao saírem do lugar, começam a movimentar-se lentamente, e adquirem velocidade progressiva até que esta torne-se constante, para depois reduzirem o movimento de forma mais lenta ao frear. As bolas de futebol, por exemplo, não quicam no chão com a mesma velocidade que voltam para a mão de quem as lançou, sendo possível observar leve achatamento causado pela física ao chocarem-se com o chão. A aplicação deste conceito faz grande diferença na suavização dos movimentos das animações, tornando-as mais próximas do real, e comunicando melhor ao usuário o que a interface quer dizer.

O site <a href="http://easings.net/pt-br" target="_blank">easings.net</a> oferece referências sobre os diversos tipos de efeitos de suavização:

<a href="http://easings.net/pt-br" target="_blank"><img class="alignnone wp-image-49697 size-full" src="http://tableless.com.br/uploads/2015/06/easing.png" alt="Exemplos de easings" width="878" height="622" /></a>

Já o **_timing_** está relacionado ao tempo de duração das animações. Animações muito longas não provocam a sensação de realidade, por isso, prefira efeitos com pouco milissegundos, algo entre 0,2 e 0,6 segundos.

### Ferramentas para trabalhar com animações

O **Chrome** e o **Firefox** já possuem ferramentas que permitem controlar as animações, depurar e mensurar a performance através do processamento gasto ao movimentar os elementos da página. Em breve, o **<a href="https://developer.chrome.com/devtools" target="_blank">Chrome DevTools</a>** promete disponibilizar uma ferramenta capaz de controlar a linha do tempo (_timeline_) igual a existente no Flash.

Aqui tem os slides da palestra do Zeh Fernandes:



E aqui a gravação no Meetup:



## O que rolou após a palestra

O encontro contou com aproximadamente 25 profissionais entre designers, desenvolvedores front-end, back-end e UXs. Após a palestra, a discussão entre os participantes girou em torno das seguintes questões: **as animações, devem ser pensadas antes, durante ou depois do processo de desenvolvimento? Quem deve ser o responsável por pensar seus significados e propósitos?**

Vários pontos de vista foram levantados, e o que tornou o debate mais interessante foi a diversidade de profissionais presentes. As conclusões, resumidamente, podem ser enumeradas a seguir:

  * Pensar as animações é atividade do UX, mas nem sempre este profissional está presente na equipe (principalmente em empresas pequenas). Desta forma, a responsabilidade é igualmente do designer web e do front-end, que devem trabalhar juntos com o objetivo de encontrar a melhor solução: a que comunica melhor o significado e propósito da animação, e a que oferece melhor performance (esta última, uma responsabilidade maior do front-end).
  * Pensar as animações antes de desenvolver o código é mais produtivo, pois elas terão propósito semântico e comunicacional, informando o usuário sobre o que esperar da interface e como interagir com a mesma. Isto não exclui que, após a definição dos _sketchs_ ou layouts, quaisquer dos profissionais envolvidos sugiram melhorias. Como dito anteriormente, a responsabilidade é de todos.
  * Use animações com moderação. A atitude de criar a interface e somente depois de pronta receber resolver &#8220;dar uma animada&#8221; pode ser o maior dos erros. Interface não é circo, e a intenção é comunicar com propósito e significância. Planeje, pesquise, busque referências no mundo _online_ e _offline_.

<img class="aligncenter size-full wp-image-49709" src="http://tableless.com.br/uploads/2015/06/fotos-meetup-css-sp-8.jpg" alt="Fotos Meetup CSS SP 8" width="695" height="520" />

Em suma, os _Meetups_ são excelentes oportunidades para conhecer profissionais que lidam com assuntos do seu interesse, aprender novas abordagens, solucionar problemas ou aumentar a rede de contatos.

Para quem achou interessante a proposta, <a href="http://www.meetup.com/CSS-SP/" target="_blank">cadastre-se aqui</a> e fique ligado nos próximos encontros. Sugira temas, problemas do seu dia-a-dia e fomente discussões. Ofereça lugares na sua empresa para que as reuniões aconteçam. Crie _Meetups_ na sua cidade. Esta é ferramenta de colaboração pode contribuir com o desenvolvimento da comunidade trazendo benefícios a todos.