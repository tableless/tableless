---
title: Em tempo de transição, quais recursos utilizar?
author: Thaiana Poplade
type: post
date: 2011-05-24
excerpt: Acompanhar todas as mudanças que o desenvolvimento web vem sofrendo é tarefa muito difícil e bastante trabalhosa. Alguns de nós ainda preferem sentir-se mais seguros quanto a regulamentação dessas diretrizes e outros já estão testando e experimentando. Pra onde podemos direcionar nossa postura às evoluções?
url: /em-tempo-de-transicao-quais-recursos-utilizar/
tweetbackscheck:
  - 1356467834
shorturls:
  - 'a:3:{s:9:"permalink";s:69:"http://tableless.com.br/em-tempo-de-transicao-quais-recursos-utilizar";s:7:"tinyurl";s:26:"http://tinyurl.com/43npmp7";s:4:"isgd";s:19:"http://is.gd/VtbBc3";}'
twittercomments:
  - 'a:8:{i:131046860470235136;s:7:"retweet";i:131043403872997379;s:7:"retweet";i:131041448836603905;s:7:"retweet";i:155794218755948544;s:7:"retweet";i:155775409882013696;s:7:"retweet";i:160530631737094144;s:7:"retweet";i:162908909038874625;s:7:"retweet";i:160536516819550208;s:7:"retweet";}'
tweetcount:
  - 12
dsq_thread_id: 503040279
categories:
  - Artigos
  - Browsers
  - CSS
  - CSS3
  - HTML
  - HTML5
  - JavaScript
  - Tecnologia e Tendências
tags:
  - 2011
  - Browsers
  - cotidiano
  - CSS
  - Na Prática

---
HTML 5, CSS3, IE9, Firefox 4&#8230; enfim, siglas, nomes e versões que não param de pipocar nos tweets, posts, artigos, e em todos os lugares dentro do nosso universo do desenvolvimento web e automaticamente nos perguntamos &#8211; como traçar nosso trabalho nesta época de transição? O que é certo? O que é errado?

### Graciosamente retroceder ou progressivamente evoluir?

A melhor análise antes de decidir qual caminho tomar e a qual evolução recorrer vem do planejamento de seu projeto. Estudo de estatísticas de navegadores, perfil do usuário, resolução de tela, dispositivos, etc; são alguns dos pontos a serem levados em consideração, criando material suficiente para você decidir qual caminho seguir: considerar o retrocesso [ por exemplo: desenvolver seu website para IE6 ] ou expor a evolução de forma progressiva [ por exemplo: utilizar bordas arredondadas e novas características via CSS3 ].
  
Determinar os fins do projeto vão estabelecer o melhor caminho a seguir durante toda a sua execução pois, em época de transição, os riscos de utilizar algo que não dê certo e a presença de retrabalho são quase inevitáveis. Assim, considere todas as possibilidades.

### Graciosamente retroceder

Quando pensamos em retrocesso, no caso do desenvolvimento web, o utilizamos para conceituar uma codificação baseada em X-HTML/CSS 2 e Crossbrowser [ com browsers de mercado incluindo o IE6 ], de qualquer forma, a ideia não é pensar que esteja errado ou que seja um método fora de uso, mas sim uma segurança em utilizar o que já está regulamentado, validado pela W3C e igualmente embutido na renderização padrão dos browsers mais utilizados.
  
Inúmeras são as dicas aqui no Tableles relacionadas à esta frente de desenvolvimento, mas o que podemos levar em consideração quando pensamos em desenvolver um website dentro dessas diretrizes é que: IE 6 e IE7 ainda devem fazer parte dos browsers em testes e que ainda utilizaremos imagens para criação de bordas arredondadas e sombras. Além claro, de nos encontrar em momentos que utilizaremos diversos elementos em nosso código html apenas para assegurar que algum efeito visual seja renderizado na tela [ as vezes dependente do uso de Javascript para tanto ]. Considerando estes pontos e pensando nos fins do projeto, basta iniciar o desenvolvimento.
  
Algumas dicas que podem ajudar nesta escolha estão em: <a href="http://tableless.com.br/categoria/client-side/html-css/page/2" target="_blank">http://tableless.com.br/categoria/client-side/html-css/page/2</a>

### Progressivamente evoluir

Como falamos acima, estamos num momento de transição que significa acima de tudo &#8211; escolha. Utilizar novas possibilidades na criação de websites é uma escolha que deve ser igualmente planejada pois, o risco não vem do que já conhecemos e do que já sabemos que vai exigir maior cuidado, mas sim do que desconhecemos &#8211; a renderização de novos parâmetros em folhas de estilo e a interpretação de uma nova tag html, por exemplo.
  
Pouco ainda consegue-se definir a respeito das novas possibilidades, mas é fato que muitos desenvolvedores estão aprendendo como utilizar o novo, testando e reportando erros e acertos e este comportamento deve estender-se por anos, até que as diretrizes sejam regulamentadas pela W3C e os browsers tenham o mesmo número de usuários que suas versões de mercado tem hoje.
  
Com isso, os testes geralmente giram em torno dos novos browsers, mas eventualmente necessitamos também direcionar o desenvolvimento à navegadores mais antigos, encontrando assim, a dificuldade em visualizar a mesma coisa em todos eles. Para ajudar, pensando em HTML 5 e CSS3, abaixo uma lista de algumas ferramentas que podem ajudar na implementação das novas técnicas em browsers e possibilidades atuais:

  * Modernizr: <a href="http://www.modernizr.com/" target="_blank">http://www.modernizr.com/</a> &#8211; uma ferramenta JavaScript que suporta propriedades CSS3 em diferentes navegadores.
  * CSS3 Pie: <a href="http://css3pie.com/" target="_blank">http://css3pie.com/</a> &#8211; <a href="http://tableless.com.br/css3-bordas-arredondadas-sombras-e-gradiente" target="_blank">já comentada em outro artigo</a>, o CSS3 Pie é uma ferramenta JavaScript que permite renderizar bordas arredondadas, background-gradient e box-shadow nas versões anteriores de IE.
  * Selectivizr: <a href="http://selectivizr.com/" target="_blank">http://selectivizr.com/</a> &#8211; ferramenta JavaScript que emula seletores CSS3 e pseudo-classes, como por exemplo :focus em diferentes browsers.

Além das ferramentas, conheça no link ao lado também, algumas das melhorias trazidas para as folhas de estilo em sua nova versão e para a evolução da linguagem de marcação &#8211; o HTML5: <a href="http://tableless.com.br/categoria/client-side/html-css" target="_blank">http://tableless.com.br/categoria/client-side/html-css</a>

Testar o novo ou trabalhar com o conhecido? Esta pergunta não podemos responder, mas analisadas as características do seu projeto, você mesmo poderá tomar esta decisão consciente de um trabalho profissional e determinado ao sucesso.

Boas escolhas e até a próxima.
  
😉