---
title: Firefox Quantum
authors: Diego Eis
type: post
date: 2017-11-13
excerpt: Novo Firefox, duas vezes mais rápido para renderizar páginas, consumindo 30% menos memória que o Chrome.
image: https://i.imgur.com/UNUpGn4.png
categories:
  - Browsers
  - Firefox
  - Chrome
  - Opera
---

E o novo Firefox está na área. Depois de um ano sendo desenvolvido, esta é o maior update feito no código do browser mais open source e independente do mundo. Eles dizem que 75% do código foi impactado de alguma forma para deixar o Firefox mais rápido e moderno, não apenas no Desktop, mas também nos outros dispositivos.

A interface mudou um pouco, mas nada de outro mundo. Foram pequenas mudanças, mas que deixaram a interface do Firefox bem mais minimalista do que suas versões anteriores. 
A barra de endereço agora é declaradamente uma barra única, com busca embutida, como os outros browsers.

<iframe width="560" height="315" src="https://www.youtube.com/embed/n6wiRyKkmKc" frameborder="0" allowfullscreen></iframe>

Como dissemos anteriormente, o design mudou um pouco, mas o suficiente para diferenciar das versões anteriores. Para mim o Firefox sempre teve a interface mais feia do pedaço dos browsers, mas agora ele está bem agradável. O Time de designers da Mozilla trabalhou no que eles chamam de Photon Project.

<iframe width="560" height="315" src="https://www.youtube.com/embed/7MiKf8Rqf5w" frameborder="0" allowfullscreen></iframe>

Eles deixam claro que o Firefox ficou duas vezes mais rápido do que as versões anteriores por causa das melhorias de performance que fizeram. Uma das mudanças foi fazer o Firefox rodar usando múltiplus processos, além de lançarem o suporte a WebAssembly e WebVR.

O Firefox sempre rodou usando apenas um core do CPU, mas com essa versão, ele usa múltiplos cors do CPU, tanto no desktop quanto nos Mobiles. Por exemplo: o motor de renderização de CSS monta as páginas de forma paralela, usando múltiplos cores, em vez de rodar sequencialmente usando apenas um core de CPU. Parece que atualmente nenhum browser faz isso.

<iframe width="560" height="315" src="https://www.youtube.com/embed/tJG278nX6dM" frameborder="0" allowfullscreen></iframe>

[Nesse artigo](https://hacks.mozilla.org/2017/08/inside-a-super-fast-css-engine-quantum-css-aka-stylo/), [Lin Clark](https://code-cartoons.com/) explica que eles pegaram vários truques de versões antigas do Firefox, mais algumas coisas de browsers como Chrome e Safari, para remodelarem o motor de renderização de CSS do Firefox Quantum. É interessante você ler [esse artigo](https://hacks.mozilla.org/2017/08/inside-a-super-fast-css-engine-quantum-css-aka-stylo/), pois ele explica como o processo multi core foi pensado e realizado.

Para quem não sabe, o motor de renderização faz com que o código HTML e CSS se transformem em pixels na tela. Cada browser tem um motor desses, com seus respectivos truques: o Chrome tem o Blink, o Edge tem o EdgeHTML, o Safari tem o WebKit, o Firefox tem o Gecko. Toda regra de cascata, herança, layout, posicionamento, painting e etc fica sendo responsabilidade desse motor. Muitos dos truques que o novo Firefox usou, foi pensando em como melhorar a fase de "restyle" da página, onde o estilo dos elementos precisa ser recalculados ou até mesmo suas posições precisam ser recalculadas por conta de uma interação do usuário.

![](https://i.imgur.com/zTBxKKS.png)

> Quantum CSS makes use of this recent feature of computers by splitting up style computation for the different DOM nodes across the different cores.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YIywpvHewc0" frameborder="0" allowfullscreen></iframe>

Durante muito tempo, meu browser padrão foi o Safari, muito por conta da sua velocidade, interface mínima, renderização de tipografia e velocidade principalmente de carregamento de páginas. Embora eu gostasse muito, vira e mexe alguns sites não funcionavam direito, tanto por causa de quebra na renderização quanto por conta do JS que acaba quebrando por algum motivo. Sempre que me frustrava com o Safari, voltava para o Firefox que sempre foi o browser do coração, tanto por causa do saudosismo quanto pela cultura Open Source, anonimato, privacidade de dados e etc... Mas minha estada não durava nem 2 semanas e acabava voltando para o Safari, exatamente por causa dos problemas de performance que foram resolvidos nessa versão. Fiquei assim uns anos até estacionar de vez no Opera. Hoje, sou muito mais feliz com Opera, até agora com o lançamento do Quantum. Com certeza ficarei uns dias usando a nova versão. Quem sabe não volto direto para ele?! ;-)

![](https://i.imgur.com/dDCfoCW.png)

Leia mais direto da fonte:
- [The New Firefox Is Here!](https://blog.mozilla.org/firefox/the-new-firefox-is-here/)
- [Start Your Engines – Firefox Quantum Lands in Beta, Developer Edition](https://blog.mozilla.org/blog/2017/09/26/firefox-quantum-beta-developer-edition/)
- [Quantum CSS makes use of this recent feature of computers by splitting up style computation for the different DOM nodes across the different cores.](https://hacks.mozilla.org/2017/08/inside-a-super-fast-css-engine-quantum-css-aka-stylo/)