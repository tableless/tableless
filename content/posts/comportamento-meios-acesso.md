---
title: Comportamento e meios de acesso
author: Diego Eis
type: post
date: 2011-03-18
url: /comportamento-meios-acesso/
tweetbackscheck:
  - 1356399543
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/comportamento-meios-acesso";s:7:"tinyurl";s:26:"http://tinyurl.com/3b857et";s:4:"isgd";s:19:"http://is.gd/Wy5r0S";}'
twittercomments:
  - 'a:7:{i:129903788499795968;s:7:"retweet";i:129898026578886656;s:7:"retweet";i:129896422169518080;s:7:"retweet";i:129895281268490240;s:7:"retweet";i:129893074926178304;s:7:"retweet";i:154867152074178560;s:7:"retweet";i:154860994290659328;s:7:"retweet";}'
tweetcount:
  - 12
dsq_thread_id: 503040102
categories:
  - Acessibilidade
  - Artigos
  - Código
tags:
  - 2011
  - acessibilidade
  - Browsers
  - facebook
  - smartphones
  - twitter
  - usabilidade

---
Ainda lembro quando comprei meu primeiro smartphone. Odiava navegar naquilo. Eu estava acostumado a utilizer a internet em desktops, com telas grandes e confortáveis. Os sites também não ajudavam. Praticamente nenhum site tinha versão mobile ou uma que funcionasse direito. O Opera tentava fazer a parte dos desenvolvedores, tentando manipular o site para que ele fosse melhor visto em telas menores. Era bom, mas não o ideal.
  
Hoje o cenário é diferente. Antes usávamos o celular para no máximo procurar um endereço. Hoje lemos feeds, twitter, facebook, enviamos, recebemos e arquivamos emails. Dependendo do aparelho é possível criar planilhas, documentos, pastas e tudo mais. Já perdi a conta de quantos artigos comecei no smartphone e terminei no notebook.

Sistemas baseados em web, teoricamente, já funcionam em qualquer aparelho móvel. Do ponto de vista de desenvolvimento, não é preciso reprogramar o sistema. Mas o design para mobiles é diferente do design para desktops. E é aí que as mudanças são necessárias.

O comportamento, respostas cognitivas e a forma de uso dos mobiles é totalmente diferente do que estamos acostumados em desktops. Isso afeta totalmente a acessibilidade e a usabilidade do sistema/site. Temos muitas indicações das ações feitas com o mouse. Por exemplo, quando clicamos em algum botão ou link, muda-se as cores, sublinhado, background, bordas e etc. Tudo isso nos dá uma resposta de que acionamos algum mecanismo. Nos mobiles isso é diferente. Normalmente, como utilizamos nosso dedo, a área visível do botão praticamente some. Logo, indicações de cor, fundo, sublinhado e etc não são tão efetivas. Como indicação de comportamento podemos fazer o aparelho vibrar, fazendo com que o usuário saiba que ele executou uma ação.
  
É por conta destas diferenças &#8211; que parecem simples em uma primeira análise &#8211; que a ideia de ampliar as possibilidade das linguagens client-side pode ajudar. Imagine controlar via CSS a força, quantidade de vezes e tempo de vibração do aparelho. Em desktops isso não afetará em nada, mas para mobiles e outros tipos de aparelhos – touchs, principalmente &#8211; trariam uma grande vantagem de acessibilidade e usabilidade.

Você já deve saber que o desenvolvimento com padrões web é dividido em 3 camadas: informação, formatação e comportamento. O HTML é responsável pela informação. O CSS é responsável pela formatação e o Javascript é responsável pelo comportamento.
  
Isso mudou um pouco nos últimos tempos. O Javascript controlava o CSS para manipular o comportamento dos elementos HTML. Para fazermos tabelas zebradas (tabelas com linhas de cores alternados), animações, menu com submenus e etc utilizávamos Javascript. Hoje, uma boa quantidade destas necessidades já podemos fazer com CSS, como é o caso das tabelas zebradas. Com as inovações do CSS3 e do HTML5, a terceira camada de comportamento não depende mais apenas do Javascript. Logo o comportamento (do ponto de vista visual e cognitivo e não funcional) que os celulares deveriam ter quando determinado botão é selecionado ou clicado, também será responsabilidade do CSS.

Para que você entenda melhor, sugiro que leia a a especificação do W3C sobre CSS Aural. Eu já aviso que é coisa do tinhoso.
  
Imagine que um internauta cego visite um site. Por causa do problema de visão, ele utiliza um leitor de tela ligado ao sistema de som do computador ou a um sistema de som de multi-canais, como um Home Theater. Ao visitar o site, o leitor de tela leria seu HTML e interpretaria o CSS Aural escrito para o site. Com o CSS Aural, o desenvolvedor controla, por exemplo, se a voz que o usuário ouvirá é feminina ou masculina. Controla de onde o som sairá, se é da caixa da esquerda ou da direita. Será possível escolher em qual das caixas de som a voz do leitor de tela sairá. Controlaremos a pausa da fala, volume, força da voz e etc&#8230; Você praticamente “formata” a voz ouvida pelo visitante. Isso tudo com CSS! Genial!

Entenda que a web é mais do que conhecemos. Hoje você assiste vídeos, vê imagens e lê blogs, notícias e etc. Você escreve, compartilha e produz conteúdo. Todas essas características devem estar disponíveis **não importa qual meio de acesso** o visitante utiliza. Não deve importar também qual o nível de acessibilidade o visitante necessita. CSS Aural é útil para pessoas com problema de visão. Há outros tipos de problemas, muitas vezes nem são problemas físicos. Entenda também que os dispositivos não se limitam a notebooks, desktops e smartphones. A moda agora são as tablets e não vai demorar muito para surgirem outros dispositivos. Não estou me referindo sobre a criação de novos dispositivos. Pode ser que a próxima moda seja uma geladeira ou um microondas que acessa a internet. Pode ser que o Surface da Microsoft passe a custar barato&#8230; Abra sua cabeça. Saia da caixa.
  
Para o desenvolvimento web, o termo “dispositivo” não pode mais existir. O que existe são meios de acesso. O Google é um meio de acesso assim como o smartphone, o browser, o leitor de feed, etc etc etc.

Toda **a informação publicada na web é reutilizável**. É reutilizada por seus usuários ao compartilharem, é reutilizada pelos buscadores, por outros sites e etc. Por isso a informação precisa estar disponível em qualquer lugar, a qualquer hora, não importando o meio que pela qual ela é acessada.