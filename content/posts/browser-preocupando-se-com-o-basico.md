---
title: Browser – Preocupando-se com o básico
author: Diego Eis
type: post
date: 2006-05-17
url: /browser-preocupando-se-com-o-basico/
tweetbackscheck:
  - 1356140086
shorturls:
  - 'a:3:{s:9:"permalink";s:59:"http://tableless.com.br/browser-preocupando-se-com-o-basico";s:7:"tinyurl";s:26:"http://tinyurl.com/3k46gk8";s:4:"isgd";s:19:"http://is.gd/3n9Nwz";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503035357
categories:
  - Browsers
  - Geral
tags:
  - Técnicas e Práticas

---
Já vi muita gente preocupada em fazer o site funcionar em uma centena de browsers. Não seria perda de tempo se a maioria dos browsers não fossem dispensáveis.

Conto esta história toda vez que vou falar deste assunto para algum aluno: Quando comecei a seguir os padrões na criação de sites, uma das grandes dificuldades iniciais era a falta de compatibilidade entre os browsers. Era uma época que o Opera e o Firefox (que antes tinha outro nome: Firebird e Phoenix, algo assim) estavam começando a surgir. Por isso, era normal que ao implementar algum site, eu testasse o resultado em pelo menos 6 browsers: IE 5, IE 5.5, IE 6, Firefox, e Opera 3 e Opera 3.5.
  
O tempo passou e os browsers ficaram melhores. Hoje em dia, browsers como [Firefox][1], [Opera][2] e [Safari][3] tem um ótimo suporte a CSS, o que os tornam previsíveis e muito estáveis na hora de desenvolver sites baseados nos padrões.

Por isso, hoje eu testo meus sites em apenas 2 browsers: no Firefox e no Internet Explorer 6.
  
Não  me preocupo mais com o IE 5.x, pois ele já não é muito mais usado. Hoje, quem não usa WinXP, usa qualquer outro Windows (no mínimo Win98) atualizado com o IE 6. Logo o IE 5 deixou de ser um problema. Ainda testo no Internet Explorer 6, por que infelizmente ele não tem um suporte bom para CSS. Ainda existem muitos problemas que na maioria das vezes não sabemos a causa.

Esqueça por enquanto o IE 7. Ele é um browser beta, ainda está em testes e por isso não se baseie nele. Pense nele daqui 1 ou 2 anos. Ele será um browser voltado ao novo sistema da Microsoft, então, usuários comuns não terão muito acesso a ele. Por isso, não se desespere por causa dele. Mas apesar disso, é possível fazer sites sem usar uma gota de css hack.
  
Vá com calma. Na hora da implementação teste apenas em Firefox e Internet Explorer 6. Se funcionar nestes dois browsers, você tem 99% de chance de funcionar nos outros. Os browsers bons, que seguem os padrões, normalmente costumam dar os mesmos resultados, por isso, testar apenas no Firefox (digo o Firefox porque ele é o browser &#8220;alternativo&#8221; mais conhecido) é muito seguro.

A uma extensão para Firefox chamada [IETab][4] que abre apenas o Viewport do IE em uma tab do Firefox&#8230; Muito interessante, porque você não precisa ficar gerenciando duas janelas, só duas tabs.

 [1]: http://getfirefox.com/
 [2]: http://opera.com/
 [3]: http://www.apple.com/macosx/features/safari/
 [4]: https://addons.mozilla.org/firefox/1419/