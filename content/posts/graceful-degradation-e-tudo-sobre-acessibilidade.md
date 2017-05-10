---
title: Graceful degradation é tudo sobre Acessibilidade
author: Diego Eis
type: post
date: 2009-04-12
excerpt: Cada tipo de dispositivo e perfil de usuário tem um nível de experiência. Você precisa dar a melhor experiência possível para cada um destes perfis. Isso se chama Graceful Degradation.
url: /graceful-degradation-e-tudo-sobre-acessibilidade/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356439968
shorturls:
  - 'a:3:{s:9:"permalink";s:72:"http://tableless.com.br/graceful-degradation-e-tudo-sobre-acessibilidade";s:7:"tinyurl";s:26:"http://tinyurl.com/3suom8q";s:4:"isgd";s:19:"http://is.gd/uSyvhG";}'
twittercomments:
  - 'a:1:{i:174582502474788864;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503039037
categories:
  - Browsers
  - CSS
  - Mobile
tags:
  - Browsers
  - clientside
  - CSS
  - html
  - Mobile

---
Não há uma tradução literal para Graceful Degradation. O mais próximo seria Degradação Harmoniosa. Não é um termo muito bonito de ficar dizendo por aí. Por isso, vamos utilizar o termo original inglês durante todo o artigo.

Graceful Degradation é algo que vemos todos os dias. Trata-se de um método comum em dias onde a Internet é muito mais que um simples computador ligado no telefone. Acho que resumidamente, podemos dizer o que exatamente é Graceful Degradation com a frase: 

> Graceful degradation means that your Web site continues to operate even when viewed with less-than-optimal software in which advanced effects don’t work.

<cite><a href="http://www.digital-web.com/about/contributors/peterpaul_koch">Peter-Paul Koch</a> em <a href="http://www.digital-web.com/articles/fluid_thinking/">Fluid Thinking</a></cite>

Esse assunto é bastante velho, mas que volta à tona nestes dias de [campanhas contra o IE6][1] e outros browsers antigos. Eu mesmo já falei para ignorar totalmente o Internet Explorer 6, mas não é tão fácil assim. Eu posso ignorar aqui no Tableless, onde os usuários são de um nicho específico, mas eu não posso ignorar esse público quando se trata de um produto que é feito para o meu cliente. O cliente do meu cliente utiliza IE6. E ignorá-los significa fazer meu cliente perder dinheiro. Isso está fora de questão.
  
Então, se seguirmos este raciocínio, pense bem: podemos cometer este erro com outros tipos de usuários. Por exemplo, se seu site não pode ser bem visto em dispositivos móveis ou se não é bem acessado por leitores de tela. 

### É tudo sobre acessibilidade

Engana-se aquele que acha que acessibilidade é apenas sobre cegos e outras pessoas com alguma necessidade fisica. É claro que esse público merece uma atenção especial, que muitas vezes é tristemente ignorada. Mas quando falamos sobre acessibilidade, temos que entender que há outros grupos que se encaixam nesse assunto.
  
Quando um visitante não consegue acessar seu site por causa da resolução, ou por meio de algum dispositvo, ou por algum sistema de voz etc, estamos falando de acessibilidade.

Temos que prever visitantes com necessidades diversas. Há pessoas que passam a maior parte do tempo viajando. Por isso é muito difícil ler emails ou trabalhar conectado por notebook ou computador decente. Por isso ela passa a maior parte do tempo utilizando aparelhos móveis. Não por que ela queira, mas por causa da sua necessidade.
  
Se negligenciarmos o acesso desse tipo de público, cometemos um erro grave de acessibilidade. O mesmo para um simples visitante que não consegue acessar seu website por causa da sua resolução. Ele usa 800&#215;600 porque precisa e não porque quer. Embora haja alguns que nem sabem o que é resolução.
  
Necessidade. Acessibilidade é tudo sobre a necessidade das pessoas. 

### Meios de acesso a Internet

Se as pessoas acessam a Internet, elas acessam por meio de um dispositivo especifico. Se ela é cega ou tem algum ou outro problema de visão, ela acessa o site por um leitor de tela. Se ela viaja muito ou fica muito tempo presa no trânsito, utililza dispositivos móveis.
  
Hoje em dia não existem muitos meios de acesso a Web. Se não acessamos por um computador ou um dispositivo móvel, acessamos com o que?
  
Outros meios de acesso a Internet estão nascendo. Na verdade novos usos para o acesso a Internet estamos surgindo e com estes novos usos, surgem novos meios de acesso. Vide o Surface da Microsof. É um meio totalmente diferente de interagir com a Web. Mas é um novo meio.

### Mas e o Graceful Degradation?

Problemas com compatibilidades sempre existiram e creio que nunca deixarão de existir. Pelo contrário. Esses problemas serão mais comuns embora fiquem mais fáceis de resolver. Não serão apenas probleminhas entre browsers (os browsers existirão em tempos futuros?), mas também entre dispositivos.

Acontece muito hoje: tentamos acessar um serviço por um determinado browser, e somos aconselhados a utilizar outro browser porque o serviço não é compativel ou não funciona bem no nosso browser predileto.
  
Isso tira qualquer um do sério. O site deveria funcionar em qualquer browser. Para exemplificar: se em um meio de acesso eu não consigo utilizar bordas arredondadas nos elementos, os elementos apareceriam sem as bordas arredondadas. Isso não deveria prejudicar minha experiência de uso. Eu perderia um pouco no Design, mas conseguiria utilizar o serviço sem problemas. 

A idéia do Graceful Degradation é exatamente essa: dar a melhor experiência possível ao dispositivo/meio que o usuário estiver utilizando sem prejudicar a acessibilidade.

Os usuários do IE6 por exemplo podem ficar sem bordas arredondas, position fixed, sombras e pngs semi-transparentes, mas eles precisam acessar e utilizar perfeitamente o site, com a melhor experiência que é possivel dar a este browser.

Mesma coisa é aplicada aos dispositivos móveis. Estes dispositivos normalmente não tem os mesmos recursos de um desktop. É tudo diferente, desde o poder de processamente até o tamanho das coisas. Então imaginar que o uso do sistema/site será parecido como se fosse acessado por PC, é um erro.

É um erro também se fizermos um site pensando em dispositivos menos capazes mas não nós lembrarmos do grupo de usuarios que acessam seu site com dispositivos mais completos e modernos. É engraçado porque pensamos sempre no usuário que está no pior cenário. Mas aquele usuário que não seria um problema pra nós, pode se tornar o pior deles.

Um exemplo disso é quando usuários de iphone acessam sites inteiros feitos em Flash. Sabemos que é uma limitação do aparelho. Mas estes usuários estão crescendo e seu cliente pode estar ali. Normalmente ninuem coloca uma versão diferente da do Flash. Logo, estes usuários simplesmente são ignorados. Imagine a frustação.

Resumidamente, Graceful Degradation é dar a melhor experiência que você conseguir para o usuário.
  
Se ele utiliza o último lançamento da Apple ou se ele utiliza um Nokia 6111 com Opera Mini. Ele precisa ter a melhor experiência que é possível dar dentro dos limites de cada dispositivo.
  
Obviamente que vice não vai prever todos os tipos de usuário. Mesmo porque seria impossível fazer isso. Novamente eu digo o óbvio: faça um estudo de público-alvo é importante.

Para complementar seu estudo:

  * [Fault-tolerant System][2][Não há uma tradução literal para Graceful Degradation. O mais próximo seria Degradação Harmoniosa. Não é um termo muito bonito de ficar dizendo por aí. Por isso, vamos utilizar o termo original inglês durante todo o artigo.

Graceful Degradation é algo que vemos todos os dias. Trata-se de um método comum em dias onde a Internet é muito mais que um simples computador ligado no telefone. Acho que resumidamente, podemos dizer o que exatamente é Graceful Degradation com a frase: 

> Graceful degradation means that your Web site continues to operate even when viewed with less-than-optimal software in which advanced effects don’t work.

<cite><a href="http://www.digital-web.com/about/contributors/peterpaul_koch">Peter-Paul Koch</a> em <a href="http://www.digital-web.com/articles/fluid_thinking/">Fluid Thinking</a></cite>

Esse assunto é bastante velho, mas que volta à tona nestes dias de [campanhas contra o IE6][1] e outros browsers antigos. Eu mesmo já falei para ignorar totalmente o Internet Explorer 6, mas não é tão fácil assim. Eu posso ignorar aqui no Tableless, onde os usuários são de um nicho específico, mas eu não posso ignorar esse público quando se trata de um produto que é feito para o meu cliente. O cliente do meu cliente utiliza IE6. E ignorá-los significa fazer meu cliente perder dinheiro. Isso está fora de questão.
  
Então, se seguirmos este raciocínio, pense bem: podemos cometer este erro com outros tipos de usuários. Por exemplo, se seu site não pode ser bem visto em dispositivos móveis ou se não é bem acessado por leitores de tela. 

### É tudo sobre acessibilidade

Engana-se aquele que acha que acessibilidade é apenas sobre cegos e outras pessoas com alguma necessidade fisica. É claro que esse público merece uma atenção especial, que muitas vezes é tristemente ignorada. Mas quando falamos sobre acessibilidade, temos que entender que há outros grupos que se encaixam nesse assunto.
  
Quando um visitante não consegue acessar seu site por causa da resolução, ou por meio de algum dispositvo, ou por algum sistema de voz etc, estamos falando de acessibilidade.

Temos que prever visitantes com necessidades diversas. Há pessoas que passam a maior parte do tempo viajando. Por isso é muito difícil ler emails ou trabalhar conectado por notebook ou computador decente. Por isso ela passa a maior parte do tempo utilizando aparelhos móveis. Não por que ela queira, mas por causa da sua necessidade.
  
Se negligenciarmos o acesso desse tipo de público, cometemos um erro grave de acessibilidade. O mesmo para um simples visitante que não consegue acessar seu website por causa da sua resolução. Ele usa 800&#215;600 porque precisa e não porque quer. Embora haja alguns que nem sabem o que é resolução.
  
Necessidade. Acessibilidade é tudo sobre a necessidade das pessoas. 

### Meios de acesso a Internet

Se as pessoas acessam a Internet, elas acessam por meio de um dispositivo especifico. Se ela é cega ou tem algum ou outro problema de visão, ela acessa o site por um leitor de tela. Se ela viaja muito ou fica muito tempo presa no trânsito, utililza dispositivos móveis.
  
Hoje em dia não existem muitos meios de acesso a Web. Se não acessamos por um computador ou um dispositivo móvel, acessamos com o que?
  
Outros meios de acesso a Internet estão nascendo. Na verdade novos usos para o acesso a Internet estamos surgindo e com estes novos usos, surgem novos meios de acesso. Vide o Surface da Microsof. É um meio totalmente diferente de interagir com a Web. Mas é um novo meio.

### Mas e o Graceful Degradation?

Problemas com compatibilidades sempre existiram e creio que nunca deixarão de existir. Pelo contrário. Esses problemas serão mais comuns embora fiquem mais fáceis de resolver. Não serão apenas probleminhas entre browsers (os browsers existirão em tempos futuros?), mas também entre dispositivos.

Acontece muito hoje: tentamos acessar um serviço por um determinado browser, e somos aconselhados a utilizar outro browser porque o serviço não é compativel ou não funciona bem no nosso browser predileto.
  
Isso tira qualquer um do sério. O site deveria funcionar em qualquer browser. Para exemplificar: se em um meio de acesso eu não consigo utilizar bordas arredondadas nos elementos, os elementos apareceriam sem as bordas arredondadas. Isso não deveria prejudicar minha experiência de uso. Eu perderia um pouco no Design, mas conseguiria utilizar o serviço sem problemas. 

A idéia do Graceful Degradation é exatamente essa: dar a melhor experiência possível ao dispositivo/meio que o usuário estiver utilizando sem prejudicar a acessibilidade.

Os usuários do IE6 por exemplo podem ficar sem bordas arredondas, position fixed, sombras e pngs semi-transparentes, mas eles precisam acessar e utilizar perfeitamente o site, com a melhor experiência que é possivel dar a este browser.

Mesma coisa é aplicada aos dispositivos móveis. Estes dispositivos normalmente não tem os mesmos recursos de um desktop. É tudo diferente, desde o poder de processamente até o tamanho das coisas. Então imaginar que o uso do sistema/site será parecido como se fosse acessado por PC, é um erro.

É um erro também se fizermos um site pensando em dispositivos menos capazes mas não nós lembrarmos do grupo de usuarios que acessam seu site com dispositivos mais completos e modernos. É engraçado porque pensamos sempre no usuário que está no pior cenário. Mas aquele usuário que não seria um problema pra nós, pode se tornar o pior deles.

Um exemplo disso é quando usuários de iphone acessam sites inteiros feitos em Flash. Sabemos que é uma limitação do aparelho. Mas estes usuários estão crescendo e seu cliente pode estar ali. Normalmente ninuem coloca uma versão diferente da do Flash. Logo, estes usuários simplesmente são ignorados. Imagine a frustação.

Resumidamente, Graceful Degradation é dar a melhor experiência que você conseguir para o usuário.
  
Se ele utiliza o último lançamento da Apple ou se ele utiliza um Nokia 6111 com Opera Mini. Ele precisa ter a melhor experiência que é possível dar dentro dos limites de cada dispositivo.
  
Obviamente que vice não vai prever todos os tipos de usuário. Mesmo porque seria impossível fazer isso. Novamente eu digo o óbvio: faça um estudo de público-alvo é importante.

Para complementar seu estudo:

  * [Fault-tolerant System][2]][2] 
  * [Graceful Degradation Dan&#8217;s Web Tips][3]
  * [Graceful Degradation &#8211; CSS3.info][4]
  * [Graceful Degradation Progressive Enhancement][5]

 [1]: http://tableless.com.br/a-internet-tem-que-avancar-sem-o-ie6
 [2]: http://en.wikipedia.org/wiki/Fault-tolerant_system
 [3]: http://webtips.dan.info/graceful.html
 [4]: http://www.css3.info/graceful-degradation/
 [5]: http://accessites.org/site/2007/02/graceful-degradation-progressive-enhancement/