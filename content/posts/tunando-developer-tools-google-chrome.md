---
title: Tunando o Developer Tools do Google Chrome
author: Zeno Rocha
type: post
date: 2012-10-16
excerpt: Já imaginou poder trocar o CSS da sua ferramenta de Inspecionar Elementos? Pois é, você pode!
url: /tunando-developer-tools-google-chrome/
tweetbackscheck:
  - 1356420068
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7107";s:7:"tinyurl";s:26:"http://tinyurl.com/cdo3gd4";s:4:"isgd";s:19:"http://is.gd/DcwTze";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 887942514
categories:
  - Browsers
  - Código
  - Técnicas e Práticas
tags:
  - 2012
  - chrome
  - developer tools
  - ferramentas

---
Uma coisa muito comum entre os programadores é a vontade de customizar as coisas. Trocar o _syntax highlight_ do seu editor de código preferido é uma coisa muito comum e legal de se fazer, já que você passa o dia inteiro olhando para aquilo, é bom ver algo que goste.

Só que outra coisa que também passamos muito tempo do nosso dia é o Developer Tools dos nossos navegadores, seja o Firebug no Firefox, Dragonfly no Opera ou o do próprio Chrome. Já pensou se pudéssemos bagunçar eles também?

Hoje vou ensinar como fazer isso muito rapidamente no Developer Tools do Google Chrome!

[youtube http://www.youtube.com/watch?v=Mu6nnPN7W_s&w=560&h=420]

## 1 &#8211; Escolha o tema que mais lhe agrada:

  * Monokai Dark: <https://github.com/simonowendesign/SO-Dark-Monokai-v3>
  * MNML Theme: <https://github.com/frontdevDE/mnml-devtools-theme>
  * Tomorrow Theme: <https://gist.github.com/1163300>
  * IR_Black Theme: <https://gist.github.com/1150520>
  * Solarized Dark <https://gist.github.com/2174604>
  * Ruby Blue: <https://github.com/chrisbateman/ChromeDevToolsTheme-RubyBlue/>
  * Expresso: <https://gist.github.com/1207219>
  * Inversion: <https://github.com/mohsen1/Chrome-Dev-tools-dark-theme>
  * Dark Theme: <https://github.com/xajler/chrome-devtools-dark-theme>
  * Dark Dev: <https://github.com/simonsmith/DarkDev>
  * WebLight Theme: <https://gist.github.com/1325072>

Você também pode criar seu próprio tema, para isso na cole essa URL na barra de endereço: _**chrome-devtools://devtools/devTools.css**_.

Esse é o CSS padrão, modifique-o à vontade!

## 2 &#8211; Depois vá até o seguinte diretório:

Windows: &#8220;C:\Users\**\*\*SeuUsuario\*\***\AppData\Local\Google\Chrome\User Data\Default\User StyleSheets\&#8221;
  
Mac: &#8220;~/Library/Application Support/Google/Chrome/Default/User StyleSheets/&#8221;
  
Linux: &#8220;~/.config/chrome/Default/User StyleSheets/&#8221;

## 3 &#8211; E modifique o **Custom.css!**

Copiando e colando o conteúdo do CSS escolhido nesse arquivo. Depois é só voltar para seu navegador e ser feliz!

_Referência: [Addy Osmani no Google+][1]_

 [1]: https://plus.google.com/115133653231679625609/posts