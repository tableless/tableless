---
title: Testando sua app do Firefox OS em seu device
author: Willem Allan
type: post
date: 2013-11-13
excerpt: Como testar sua aplicação em um celular com Firefox OS.
url: /testando-sua-app-firefox-os-em-seu-device/
dsq_thread_id: 1961091541
categories:
  - Técnicas e Práticas
tags:
  - Firefox OS

---
## Configurando Aparelho

Para habilitar Depuração em seu celular é preciso ir em Configurações, Informações > Mais informações > Desenvolvedor, marque a opção Depuração Remota.

## Configurando seu Mac OS X

Após habilitar opção no celular é preciso configurar e baixar adt-bundle no site do Android.

  * <a href="http://developer.android.com/sdk/index.html" target="_blank">Download</a></p> 

Caso queria instalar em um Windows ou Linux segue o link da <a href="https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Debugging/Connecting_a_Firefox_OS_device_to_the_desktop" target="_blank">Mozilla</a>.

  * <a href="https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Debugging/Connecting_a_Firefox_OS_device_to_the_desktop" target="_blank">Windows e Linux</a>

No meu caso baixei o arquivo adt-bundle-mac-x86_64-20130522.zip, extraia em algum diretório de sua preferência. Lembre-se que o caminho desta pasta é importante no passo seguinte.

Agora é preciso editar seu arquivo .bashrc ou .profile, depende do seu sistema:

<pre class="lang-html">nano ~/.profile
</pre>

No meu caso editei o arquivo .profile e adicionei a linha abaixo:

<pre class="lang-html">export PATH="/Applications/adt-bundle-mac-x86_64-20130522/sdk/platform-tools:$PATH"
</pre>

Após a alteração execute o comando para atualizar o seu console, dessa forma ele irá reconhecer o comando **adb devices** que será usado para reconhecer seu smartphone:

<pre class="lang-html">source ~/.profile
</pre>

Plug o cabo usb no Macbook e em seu celular, execute o comando para verificar se o seu aparelho é reconhecido:

<pre class="lang-html">adb devices
</pre>

Retorno será algo parecido com isso:

<pre class="lang-html">List of devices attached
AA:BB:A5:B5:AA:BB    device
</pre>

Pronto, seu device foi reconhecido em seu computador.

## Instalando sua app no device com Firefox OS

Agora abra seu Firefox e no menu vá até Ferramentas > Desenvolvedor web > Firefox Os Simulator.

Se você não adicionou sua aplicação, adicione agora apontado o caminho até o arquivo manifest.webapp da sua aplicação.

Após adicionado basta clicar em Push e aparecerá uma mensagem em seu aparelho perguntando se você aceita instalação do aplicativo, basta clicar ok e o aplicativo será instalado no seu smartphone.

## Saiba mais

  * <a href="https://developer.mozilla.org/en-US/docs/Mozilla/Firefox_OS/Debugging" target="_blank">Mozilla</a>