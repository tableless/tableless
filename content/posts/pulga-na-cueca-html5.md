---
title: Pulga na cueca e experimentando o HTML5
author: Diego Eis
type: post
date: 2009-04-07
excerpt: Tenho pulga na cueca. Não no sentido literal. Claro. Eu não agüentei e mudei novamente o Tableless, por fora e por dentro. Por fora ele ficou mais bonito. Por dentro, ele está implementado com as novas tags de estrutura do HTML5.
url: /pulga-na-cueca-html5/
aktt_notify_twitter:
  - no
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356440352
shorturls:
  - 'a:3:{s:9:"permalink";s:44:"http://tableless.com.br/pulga-na-cueca-html5";s:7:"tinyurl";s:26:"http://tinyurl.com/3ny8bla";s:4:"isgd";s:19:"http://is.gd/VasxeW";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038968
categories:
  - Artigos
  - HTML
  - Tecnologia e Tendências
tags:
  - CSS
  - html5
  - padroesweb
  - tableless

---
Tenho pulga na cueca. Não no sentido literal. Claro. Eu não diria a você esse tipo de intimidade (nojenta). Tenho pulga na cueca no sentido didático da história. Sendo sincero contigo, eu não gostei do design antigo do Tableless. Sério. Não fiz planejamento nenhum, o design ficou de mal gosto. Eu não gostei do fundo colorido que nem porpurina e nem da diagramação do layout como um todo. Por isso, resolvi mudar. 

### Sobre a compatibilidade entre os browsers

Nessa mudança eu aproveitei para estudar alguma coisa sobre CSS e HTML5, e me adiantando um pouco, resolvi implementar o site com as novas tags de estrutura propostas nas [recomendações do WHATWG][1]. Mesmo assim, se você está usando **Internet Explorer 6, 7 e provavelmente até o 8, talvez esse site não é para você**. Quer dizer, é para você, mas só se você utilizar outro browser, caso contrário, siga-o pelo [Twitter][2] ou pelo [FEED][3]. Nem preciso dizer que o [Internet Explorer 6 é ultrapassado][4] e muita coisa que utilizei no CSS aqui não vai funcionar nele. O IE7 já é muito melhor, mas há algumas coisas que não funcionam nele, apesar de todo o esforço do pessoal da Microsoft. Eu não testei o site no IE8 para saber se há uma renderização consistente. Se você utiliza esses (menos IE6) ou qualquer outro browser e perceber algum erro grotesco, por favor, me diga.

Eu posso abusar com o Tableless porque ele é um site feito para um público muito, mas muito específico. Não são clientes que utilizando 800&#215;600 nem Netscape 4. Por isso eu posso fazer muita coisa fora do escopo normal de desenvolvimento de sites.
  
Na vida real, temos que nivelar tudo por baixo. Temos que entender e estudar os clientes do cliente para saber se você pode ou não ignorar usuários de browsers antigos. Por isso, relaxe, não sou tão rebelde quanto parece.

Mesmo assim, estou utilizando um script que faz os IEs entenderem as tags para que o CSS possa atuar sem grandes problemas. A estrutura aparecerá perfeitamente. A única cois que não vai funcionar são algumas das funcionalidades do CSS, como os seletores complexos. Eu também não coloquei o PNGFix para o IE6. Realmente, quero ignorar essa versão do IE e tentar melhorar a experiência a partir do IE7.

### Sobre o HTML5

O **[HTML5][5] levará algum tempo para que esteja totalmente completo** e maduro para a utilização. Mas como tenho pulga na cueca (lembra?), por pura experimentação, eu apliquei as novas tags de estrutura do HTML5 para montar essa nova versão do site. Eu não sei qual será o impacto disso nos buscadores. Vou descobrir daqui um tempo. Mas o fato é que o HTML5 ainda não está pronto para que você utilize nos seus projetos diários. O [Google][6], Firefox, Safari, Opera e até o IE8 andam implementando partes específicas das recomendações do HTML5. São coisas como o [módulo Offline][7], [implementações de tags de vídeo e áudio][8] e [outras coisas][9].
  
Eu já vi alguns erros de estrutura neste novo código aqui do Tableless. Irei arrumar brevemente. Há ainda muitos conceitos novos que devemos pensar e analisar. É uma nova maneira de estruturar um site. Há **uma dose muito de grande de semântica** envolvida, e por isso, o cuidado deve ser maior, já que os buscadores e elementos de acessibilidades usarão seu código como nunca para prover conteúdo.

### Sobre o CSS

Eu utilizei um bocado de [seletores complexos][10] e [pseudo-classes][11] que normalmente não funcionam no IE6. Utilizei também PNG e não coloquei um pngfix para contornar o bug do IE6.
  
O CSS é outra linguagem que está se atualizando muito rápido. Os browsers tem se prontificado implementando atualizações de características que podem ser salvar a nossa vida durante o desenvolvimento. Daqui pra frente, ouviremos muito sobre CSS Animations e CSS 3. As coisas estão andando depressa.

 [1]: http://www.whatwg.org/specs/web-apps/current-work/multipage/index.html#contents
 [2]: http://twitter.com/tableless/
 [3]: http://feeds2.feedburner.com/tableless
 [4]: http://search.twitter.com/search?q=%23semie6
 [5]: http://tableless.com.br/html5-estrutura-semantica
 [6]: http://www.engadget.com/2009/02/18/google-demos-html5-based-maps-on-the-palm-pre/
 [7]: http://www.whatwg.org/specs/web-apps/current-work/#offline
 [8]: http://www.whatwg.org/specs/web-apps/current-work/#video-and-audio-codecs-for-video-elements
 [9]: http://whatwg.org/html5
 [10]: http://tableless.com.br/seletores-complexos-do-css
 [11]: http://tableless.com.br/pseudo-classes-css