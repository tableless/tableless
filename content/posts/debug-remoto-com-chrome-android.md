---
title: Debug Remoto com Chrome no Android
author: George Moura
type: post
date: 2014-02-22
url: /debug-remoto-com-chrome-android/
dsq_thread_id: 2302801964
categories:
  - Browsers
  - Mobile
tags:
  - android
  - chrome
  - mobile
  - tooling

---
Vasculhando a web me deparei com uma coisa muito interessante: a Google criou uma forma de nós, desenvolvedores, usarmos nossas máquinas e o Google Chrome DevTools para inspecionar, debugar e analizar páginas em nossos dispositivos móveis.

Como isso funciona? O &#8220;_RemoteDebugging_&#8221; ocorre pela porta USB, a partir do momento que você conecta seu celular no computador, você pode inspecionar páginas html, css, javascript, rodar scripts no console, visualizar o comportamento de uma página nem precisar realizar deploy, testar web apps, outra coisa interessante é que você pode até inspecionar Webviews.

Para iniciar debug remoto você precisará de:

  * Um celular ou tablet Android com Chrome for Android na versão 31 ou maior instalado via Google Play. (O Chrome for Android beta já esta na versão 32 &#8211; é uma boa opção para sempre testar as novidades &#8211; requer ADB-free para conectar)
  * Um cabo usb para plugar o seu dispositivo. (Para usuários windows instalar um <a title="OEM USB Android" href="http://developer.android.com/tools/extras/oem-usb.html" target="_blank">driver USB apropriado</a>)
  * Google Chrome na versão 31 ou maior em sua máquina

Vamos agora às configurações:

## 1 &#8211; Configurando seus dispositivos

**Configurando o Android**

Caso as opções de desenvolvedor não estejam habilitadas, será necessário fazê-las. A partir da versão 4.2 do Android essa funcionalidade vem escondida por default. Para desabilita-la vá até Configurações > Sobre  o telefone e aperte 7 vezes a opção Build number. No Android 4.0 e 4.1 é só ir em Configurações > Opções de Desenvolvedor. Em opções do desenvolvedor basta habilitar a opção Debug USB.

**Configurando o Computador**

Caso tenha um linux será necessário instalar alguns programas para que o celular ou tablet seja reconhecido pelo computador.
  
Utiliza os seguintes comandos:

Para instalar os drivers para reconhecimento do dispositivo:

<pre class="lang-bash">$  sudo apt-get -y install mtp-tools mtpfs gmtp
</pre>

Para instalar o Chromium Browser &#8211; a versão open source do Google Chrome:

<pre class="lang-bash">$  sudo apt-get install chromium-browser
</pre>

Caso esteja em Windows será necessário ir no site do android e instalar o <a title="OEM USB Android" href="http://developer.android.com/tools/extras/oem-usb.html" target="_blank">driver usb</a> do fabricante apropriado.

As versões 32 do Chrome  (as versões beta) tem suporte nativo para Debug Remoto, basta a acessar `about:inspect` e ver a lista de dispositivos.

Para versões m31 e anteriores é necessário instalar a extensão do chrome [ADB Chrome extension][1].  Essa extenção inclui o Android Debug Bridge(ADB) e seguintes benefícios:

  * Inclui ADB se não tiver instalado o pacote total do sdk android.
  * Fornece uma interface de usuário para facilmente ligar e desligar o ADB e listar dispositivos conectados.

Quando a ADB Chrome extension tiver sido instalada um ícone cinza do android aparecerá ao lado do menu do Chrome

1 &#8211; Clique no ícone do android e depois em **Start ADB**

[<img class="alignnone size-full wp-image-40309" alt="tableless-adb-plugin-menu" src="http://tableless.com.br/uploads/2014/01/tableless-adb-plugin-menu.png" width="206" height="141" />][2]

Após iniciado o ícone do android ficará verde e o número de dispositivos ativos será exibido.

2 &#8211; Clique em **View Inspection Targets** para abrir a página **about:inspect**.

[<img class="alignnone size-full wp-image-40310" alt="tableless-adb-plugin-menu-active" src="http://tableless.com.br/uploads/2014/01/tableless-adb-plugin-menu-active.png" width="205" height="144" />][3]

**3 &#8211; Conecte seu celular**

Conecte seu dispositivo a maquina de desenvolvimento via cabo USB. Qdo você plugar o cabo a seguinte mensagem será exibida:

[<img class="alignnone size-full wp-image-40314" alt="usb-debugging-dialog" src="http://tableless.com.br/uploads/2014/01/usb-debugging-dialog.png" width="344" height="292" srcset="uploads/2014/01/usb-debugging-dialog.png 344w, uploads/2014/01/usb-debugging-dialog-197x168.png 197w" sizes="(max-width: 344px) 100vw, 344px" />][4]

Após apertar em OK vá para página `about:inspect`

[<img class="alignnone size-medium wp-image-40316" alt="devices-list" src="http://tableless.com.br/uploads/2014/01/devices-list-588x226.png" width="588" height="226" srcset="uploads/2014/01/devices-list-588x226.png 588w, uploads/2014/01/devices-list-329x126.png 329w, uploads/2014/01/devices-list-660x254.png 660w, uploads/2014/01/devices-list.png 674w" sizes="(max-width: 588px) 100vw, 588px" />][5]

Nessa tela, basta clicar no link &#8220;_inspect_&#8221; e você verá a seguinte tela:

[<img class="alignnone size-medium wp-image-40923" alt="inspect-1" src="http://tableless.com.br/uploads/2014/02/inspect-1-450x310.png" width="450" height="310" srcset="uploads/2014/02/inspect-1-450x310.png 450w, uploads/2014/02/inspect-1-244x168.png 244w, uploads/2014/02/inspect-1.png 973w" sizes="(max-width: 450px) 100vw, 450px" />][6]

Clicando no botão [<img alt="screencast0" src="http://tableless.com.br/uploads/2014/02/screencast0.png" width="25" height="26" />][7] você verá:

[<img alt="inspect2" src="http://tableless.com.br/uploads/2014/02/inspect2-562x310.png" width="562" height="310" />][8]

Com o screencast você pode interagir com a tela do seu device como se fosse um site, usar todas as ferramentas de desenvolvedor do chrome e tudo que é feito no device é repetido no seu pc e vice-versa, veja abaixo um video no youtube demonstrando a interação.

Fonte e mais informações: <a title="Chorme Developer Tools - Remote Debug com Chrome" href="https://developers.google.com/chrome-developer-tools/docs/remote-debugging?hl=pt-BR" target="_blank">https://developers.google.com/chrome-developer-tools/docs/remote-debugging?hl=pt-BR</a>

 [1]: https://developers.google.com/chrome-developer-tools/docs/remote-debugging?hl=pt-br#remote-debugging-chrome-extension
 [2]: http://tableless.com.br/uploads/2014/01/tableless-adb-plugin-menu.png
 [3]: http://tableless.com.br/uploads/2014/01/tableless-adb-plugin-menu-active.png
 [4]: http://tableless.com.br/uploads/2014/01/usb-debugging-dialog.png
 [5]: http://tableless.com.br/uploads/2014/01/devices-list.png
 [6]: http://tableless.com.br/uploads/2014/02/inspect-1.png
 [7]: http://tableless.com.br/uploads/2014/02/screencast0.png
 [8]: http://tableless.com.br/uploads/2014/02/inspect2.png