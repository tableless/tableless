---
title: Conheça de verdade o Boot2Gecko (ou FirefoxOS)
author: Zeno Rocha
type: post
date: 2012-01-29
excerpt: Não seria lindo se pudéssemos criar apps nativas para um sistema operacional mobile totalmente open source e feito em HTML, CSS e JavaScript? Bom, agora você já pode.
url: /conheca-de-verdade-o-boot2gecko-ou-firefoxos/
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6544";s:4:"isgd";s:19:"http://is.gd/xFnVGy";s:7:"tinyurl";s:26:"http://tinyurl.com/d7485xc";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 783970492
categories:
  - Mobile
  - Tecnologia e Tendências

---
Uma das coisas que eu tenho notado nos últimos tempos é o volume de desenvolvedores web com interesse no mundo mobile. Não é por menos, esse é um dos mercados de desenvolvimento que mais crescem no mundo.

Com essa onda, muitos curiosos começam a investir um pouco do seu tempo para criar apps de iPhone ou Android. Só que, logo de cara, esbarram com uma tremenda barreira, as diferentes linguagens de programação. Para criar apps nativas no iOS (sistema operacional do iPhone) você precisa aprender Objective-C. Para criar apps nativas no Android você precisa aprender Java.

Aí você pensa: &#8220;Linguagem de programação é tudo igual, o que importa é a lógica&#8221;. E realmente, migrar de uma linguagem para outra não é algo que deva assustar um programador. Porém muito tempo é perdido nesse processo, ainda mais quando você precisa lidar com cenários como tamanho grande de equipe ou curto prazo de projeto.

Essa frustração pode ser contornada através do uso de ferramentas como PhoneGap ou Titanium. O que elas fazem é prover um conjunto de APIs, possibilitando que você crie seus apps usando as linguagens que já está acostumado na web e que, quando finalizados, são empacotados para as linguagens nativas destes dispositivos.

Beleza, já não é a pior coisa do mundo, mas e se pudéssemos criar apps para um sistema operacional mobile totalmente open source e feito em HTML, CSS e JavaScript? Esse, senhoras e senhores, é o Boot2Gecko (ou Firefox OS), o sistema operacional que está sendo desenvolvido pela Mozilla.

Hoje escrevo direto do [FISL (Fórum Internacional do Software Livre)][1] em Porto Alegre. Nesses últimos dias estive em contato direto com os caras da Mozilla que estão desenvolvendo essa plataforma e por isso resolvi compartilhar com vocês o que tem rolado por aqui.

Antes de ontem (dia 26/07/12), Christian Heilmann ([@codepo8][2]) e John Hammink ([@rijksband][3]) deram uma palestra introdutória sobre esse assunto. Para quem não conhece, o Chris é o principal e mais popular evangelista da Mozilla no mundo. E se você nunca tinha ouvido falar sobre esse sistema operacional, recomendo muito assisti-lá. 

[youtube http://www.youtube.com/watch?v=ukjXZvfvSUs&w=560&h=420]

Já ontem (dia 27/07/12) passei o dia inteiro no Hackathon na MozillaHQ. O objetivo era criar uma app e submeter para a [Mozilla Marketplace][4].

<img style="margin-left: 78px" src="http://tableless.com.br/uploads/2012/07/abb.jpg" alt="" width="560" height="420" />

Infelizmente não consegui terminar e submeter a tempo, até porque aproveitei o dia para trocar muitas ideias com esses caras e gravar um vídeo com o Chris mostrando um celular rodando o Boot2Gecko \o/.

[youtube http://www.youtube.com/watch?v=Lu77uPgrgx0&w=560&h=420]

E no momento em que escrevo (dia 28/07/12) passei boa parte do dia contribuindo para o Boot2Gecko na [tradução da documentação][5].

## Afinal, como funciona?

A plataforma do Boot2Gecko consiste em três camadas principais. A camada de mais baixo nível é chamada de Gonk, na qual inclui o kernel do Linux e toda camada de abstração com o hardware. A camada do meio é o motor de renderização Gecko, muito semelhante ao usado no Firefox. E a camada de mais alto nível é o Gaia, responsável pela interface do usuário, sendo escrita completamente em HTML, CSS e JavaScript.

## E eu já posso usar?

Pode! Hoje já é possível instalar o Boot2Gecko em alguns smartphones, mas isso não é nada aconselhável por enquanto. O projeto encontra-se em contínuo desenvolvimento e falta bastante coisa para fazer. A boa notícia é que já você pode desenvolver apps para a Mozilla Marketplace.

## Mas como eu posso desenvolver apps se eu não tenho um celular rodando ele?

Pra isso existem os emuladores, tem um projeto chamado [Gaia Rocking][6] onde lhe instrui como rodar o emulador. Por agora não vou perder muito tempo mostrando como rodar, já que esse não é o foco do artigo, mas para provar que o negócio funciona mesmo, aproveitei para gravar um vídeo emulando o Boot2Gecko na minha máquina. Saca só o bicho!

[youtube http://www.youtube.com/watch?v=tigdi6EwSgs&w=560&h=420]

## Quando eu vou poder usar?

A previsão é que em 2013 sejam lançados comercialmente os primeiros celulares rodando o Boot2Gecko. E adivinha em qual país essa brincadeira vai começar? Brasil! Isso mesmo, após um acordo entre a Mozilla e a Telefônica, foi definido que a venda dos primeiros aparelhos no mundo será no Brasil. Um dos motivos disso acontecer é por conta da ideia da Mozilla em abordar o mercado de smartphones com preços populares.

## Concluindo

A ideia não é convencer ninguém que esse novo sistema operacional é melhor do que o iOS ou Android. O projeto está em desenvolvimento e falta muito chão para percorrer ainda. 

O que vale ressaltar aqui é a incrível oportunidade de mercado para nós brasileiros. Podemos lançar os primeiros apps da Mozilla Marketplace e sair na frente comparado ao resto do mundo.

 [1]: http://softwarelivre.org/fisl13
 [2]: https://twitter.com/codepo8
 [3]: http://twitter.com/rijksband
 [4]: https://marketplace.mozilla.org/
 [5]: https://developer-new.mozilla.org/pt-BR/docs/Apps
 [6]: https://github.com/canuckistani/gaia-rocking