---
title: Desenvolvendo para Firefox OS
author: Willem Allan
type: post
date: 2013-05-20
excerpt: Introdução para criar aplicativos para FirefoxOS.
url: /desenvolvendo-para-firefox-os/
dsq_thread_id: 1267251416
categories:
  - Técnicas e Práticas
tags:
  - 2013
  - firefox
  - Firefox OS
  - mobile
  - mozilla

---
## Introdução

Firefox OS é novo sistema operacional móvel desenvolvido pela Mozilla. Para nós desenvolvedores web ficou fácil criar aplicativos para aparelhos mobile, pois para desenvolver é utilizado apenas HTM5, CSS e JAVASCRIPT.

Para testar seus aplicativos não precisa ter um smartphone com Firefox OS, basta baixar a extensão (Firefox OS Simulator) do Firefox disponível em Windows, Linux e MAC OS X.

## Colocando em pratica

Primeiro passo é instalar a extensão Firefox OS Simulator em seu Firefox.

Firefox OS Simulator &#8211; links para Download

  * Windows &#8211; <a href="https://addons.mozilla.org/firefox/downloads/file/190978/firefox_os_simulator-2.0-fx-windows.xpi" target="_blank">download</a>
  * Linux &#8211; <a href="https://addons.mozilla.org/firefox/downloads/file/190986/firefox_os_simulator-2.0-fx-linux.xpi" target="_blank">download</a>
  * Mac OS X &#8211; <a href="https://addons.mozilla.org/firefox/downloads/file/190998/firefox_os_simulator-2.0-fx-mac.xpi" target="_blank">download</a>

## Iniciando Firefox OS Simulator

Para abrir o Firefox OS Simulator procure a aba Ferramentas > Desenvolvedor web > Firefox OS Simulator. Uma aba será aberta com as informações do Firefox OS Simulator. Nesta aba você pode desligar e ligar o emulador e nela também são adicionados os aplicativos que serão instalados no emulador assim que iniciado. Para adicionar seus aplicativos, clique em Add diretory e localizar a pasta em que você desenvolveu seu aplicativo.

## Criando uma aplicação para Firefox OS

Para iniciar, crie uma pasta do seu projeto e nela ficarão os arquivos da sua aplicação. No meu caso willemallan. Dentro do diretório crie um arquivo manifest.webapp este arquivo contém as configurações do projeto como: nome, autor, versão, icones e outros dados importantes do aplicativo. Veja abaixo o exemplo do arquivo manifest.webapp.

<pre class="lang-html linenums">{
    "version": "0.1",
    "name": "Willem Allan",
    "description": "Willem Allan - Blog posts",
    "launch_path": "/index.html",
    "icons": {
        "16": "/imgs/icons/wi16.png",
        "48": "/imgs/icons/wi48.png",
        "128": "/imgs/icons/wi128.png"
    },
    "developer": {
        "name": "Willem Allan",
        "url": "http://willemallan.com.br"
    },
    "installs_allowed_from": ["*"],
    "locales": {
        "es": {
            "description": "Willem Allan - Blog posts",
            "developer": {
                "url": "http://willemallan.com.br"
            }
        },
        "it": {
            "description": "Willem Allan - Blog posts",
            "developer": {
                "url": "http://willemallan.com.br"
            }
        }
    },
    "default_locale": "en"
}</pre>

Analisando o código acima, perceba que possuem locais para definir a versão do aplicativo, nome e descrição. Logo após, repare que o launch_path aponta para /index.html, que é o primeiro arquivo a ser carregado quando o aplicativo for iniciado. Pode ser também definido os ícones em diversos tamanhos. Por último temos opções para os dados do desenvolvedor que também podem ser traduzidos em outros idiomas.

## Mão na massa

Para iniciar crie um diretório da sua aplicação e em seguida crie um arquivo index.html e utilize o arquivo citado acima manifest.webapp alterando as configurações do seu projeto.

O resultado final é uma pasta com o nome do projeto e dentro os arquivos index.html e manifest.webapp.

Adicione um texto qualquer no arquivo index.html, pode ser o famoso hello world.

<pre class="lang-html linenums">&lt;html&gt;
&lt;head&gt;
    &lt;title&gt;Primeira aplicação Firefox OS&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;h1&gt;hello world!!! Primeira aplicação Firefox OS&lt;/h1&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

Para testar a aplicação é preciso ir na extensão do Firefox OS Simulator, Bashboard e adicionar a pasta do projeto &#8220;add directory&#8221;, depois inicie o emulador a aplicação será instalada e aparecerá nos aplicativos.

  * github &#8211; exemplo de aplicação do Firefox OS: <a href="https://github.com/willemallan/tableless-firefox-os-example" target="_blank">link</a>
  * github page &#8211; <a href="http://willemallan.github.io/tableless-firefox-os-example/" target="_blank">link</a>

## Saiba mais

  * Firefox OS Quick Start &#8211; <a href="https://marketplace.firefox.com/developers/docs/quick_start" target="_blank">link</a>
  * Desenvolva para Firefox OS sem um smartphone &#8211; <a href="https://marketplace.firefox.com/developers/docs/firefox_os_simulator" target="_blank">link</a>
  * Aplicativos de exemplo &#8211; <a href="https://marketplace.firefox.com/developers/docs/reference_apps" target="_blank">link</a>
  * Disponibilizando um aplicativo no Mozilla Marketplace &#8211; <a href="https://developer.mozilla.org/pt-BR/docs/Apps/Submitting_an_app" target="_blank">link</a>