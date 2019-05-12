---
title: Configurando React Native no macOS Mojave
excerpt: Como configurar apps feitos com React Native para rodar em simuladores de iOS e Android, assim como aparelhos físicos.
authors: Nando Vieira
image: https://i.imgur.com/cSKMBwP.jpg
type: post
date: 2019-05-12
canonical: https://nandovieira.com.br/configurando-react-native-no-macos-mojave
categories:
  - Javascript
  - Técnicas e Práticas
tags:
  - ReactJS
  - React Native
  - React
---

React Native é a plataforma de escolha para quem conhece [React](https://reactjs.org/) e precisa desenvolver aplicativos mobile. Em vez de usar uma abordagem híbrida como muitos projetos por aí, React Native tem como objetivo criar apps nativos com ferraments que já usamos para desenvolvimento web.

Em grande parte, essa abordagem funciona perfeitamente, especialmente se você faz parte de um time pequeno e não tem todos os recursos necessários para desenvolver código nativo para dispositivos Apple e Android. No entanto, é preciso estar ciente dos prós e contras, assim como qualquer decisão que você precisa tomar. Felizmente, o [Airbnb](https://medium.com/airbnb-engineering/react-native-at-airbnb-f95aa460be1c) public um artigo muito legal que cobre esse assunto, então dê uma lida.

E depois de fazer sua pesquisa, você decidiu que React Native cobre suas necessidades. E agora? Neste artigo irei mostrar como configurar apps feitos com React Native para rodar em simuladores de iOS e Android, assim como aparelhos físicos.

## Instalando Xcode

Você precisará de um Mac para usar o simulador de iOS. Você pode usar serviços como [Appetize](https://appetize.io/) (que eu não testei) para isso, mas já que o meu ambiente de desenvolvimento é o Mac, irei focar nele.

Muitas pessoas desenvolvem aplicações web e instalam apenas o command-line tools sem o Xcode para poder compilar extensões e usar o [homebrew](https://brew.sh/). No entanto, você precisa do Xcode completo para rodar o simulador, então certifique-se de instalá-lo através da [App Store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12).

![App Store: Xcode app page](https://i.imgur.com/fihvj71.png)

A instalação do Xcode vai levar um tempo. Quando terminar, abra o Xcode e instale os componentes extras.

![Xcode: Instalando components adicionais](https://i.imgur.com/ZW1hGAw.png)

Agora você precisa instalar os simuladores de iOS. Vá em “Preferences > Components” e baixe todos os simuladores que você precisar. Eu normalmente instalado apenas a versão mais recente, mas isso vai depender do suporte oficial que você quer dar aos apps.

![Xcode: Instalando os simuladores de iOS](https://imgur.com/dBMk2oU.png)

É isso! Agora vamos ver como instalar o simulador de Android.

## Instalando o Android Studio

O ecossistema de Android é diferente do da Apple. Primeiro, é possível instalar diversos simuladores desenvolvidos por terceiros, com alternativas pagas inclusive. Se você não quer ter que escolher, sugiro que use o [Android Studio](https://developer.android.com/studio), a IDE oficial para desenvolvimento de apps para Android.

![Site do Android Studio](https://imgur.com/isNbwWu.png)

Depois de fazer o download do Android Studio, move o app para o seu diretório `/Applications`.

![Android Studio: Movendo o app para o diretório /Applications](https://imgur.com/188HSmi.png)

Agora, abra o Android Studio e siga as instruções. Se você não instalou o Android SDK, você verá uma tela como esta:

![Android Studio Setup Wizard: detecção de SDK](https://imgur.com/vhiritj.png)

Click em “Next” e o Android Studio irá instalar o SDK para você.

![Android Studio Setup Wizard: Configuração de componentes](https://imgur.com/vAcli44.png)

Assim que a instalação terminar, você a tela de boas-vindas.

![Android Studio: tela de boas-vindas](https://imgur.com/MdPbuEn.png)

Vá em “Configure > SDK Manager”, e então “SDK Tools”. Clique no checkbox para selecionar o Build Tools, que serão usados pela command-line do React Native. Clique em “Apply” para iniciar a instalação.

![Android Studio: SDK Manager](https://imgur.com/88iz57b.png)

Agora, note o diretório no qual foi instalado o Android SDK. Você vai precisar desse valor para definir uma variável de ambiente em seu terminal. Aqui as coisas podem complicar um pouco porque a sua configuração pode ser diferente da minha. De um modo geral, você terá um dos dois casos à seguir:

* Para bash, adicione as linhas abaixo ao arquivo `~/.bashrc`.
* Para zsh, adicione as linhas abaixo ao arquivo `~/.zshrc`.

    export ANDROID_HOME=$HOME/Library/Android/sdk
    export PATH="$ANDROID_HOME/platform-tools:$PATH"
    

Reinicie o seu terminal para recarregar suas configurações. Para verificar se tudo está funcionando corretamente, execute os comandos abaixo:

    $ echo $ANDROID_HOME
    /Users/fnando/Library/Android/sdk
    
    $ which adb
    /Users/fnando/Library/Android/sdk/platform-tools/adb
    

Se você receber uma saída muito diferente desta, verifique se você adicionou as linhas de `export` nos arquivos corretos e se reiniciou o terminal.

Agora você pode finalmente criar um novo dispositivo virtual. De volta à tela de boas-vindas, vá em “Configure > AVD Manager”.

![Android Studio: Virtual Device Manager](https://s3.amazonaws.com/nandovieira/media/react-native-setup/android-virtual-device-manager.png)

Clique em “Create Virtual Device” e escolha uma definição de dispositivo. Neste exemplo, estou escolhendo Pixel 3.

![Android Studio: Virtual Device Profile Chooser](https://s3.amazonaws.com/nandovieira/media/react-native-setup/android-avd-profile-chooser.png)

Quando você terminar, clique em “Next”. Na tela seguinte você precisará escolher qual versão de Android irá usar. Você pode usar a última disponível, que neste momento é [Android Pie](https://www.android.com/versions/pie-9-0/). Certifique-se de clicar no link “Download”.

![Android Studio: System Image Selection](https://imgur.com/Qy5DdOV.png)

Depois que o download do Android acabar, clique em “Next” mais uma vez. Você verá uma tela com o perfil do dispositivo que está criando. Clique em “Finish”.

![Android Studio: Pie System Image](https://imgur.com/l0c22Qy.png)

Você voltará à lista de dispositivos virtual disponíveis no seu computador. É aí que você iniciará o dispositivo, além de poder criar outros se precisar.

![Android Studio: Virtual Device List](https://imgur.com/3N2UlpB.png)

Para iniciar o simulador de Android, clique no botão de play disponível na coluna “Actions”. Lembre-se sempre de fazer isso. Caso contrário, você verá uma mensagem como `No connected devices!` quando for rodar React Native no simulador de Android.

![Android Studio: Android Emulator Running](https://imgur.com/51vNhrE.png)

Parabéns! Se tudo deu certo, você acabou de configurar o Android Studio e seu simulador. Agora, vamos iniciar um novo app para ver se tudo está funcionando.

## Configurando o React Native

A documentação oficial recomenda instalar o react-native-cli globalmente, mas eu evito fazer isso. Eu prefiro usar o `npx` para gerar o esqueleto de nosso app.

    $ npx react-native-cli init sample
    ...
    
    ✨  Done in 5.90s.
    
      Run instructions for iOS:
        • cd /Users/fnando/Projects/sample && react-native run-ios
        - or -
        • Open ios/sample.xcodeproj in Xcode
        • Hit the Run button
    
      Run instructions for Android:
        • Have an Android emulator running (quickest way to get started), or a device connected.
        • cd /Users/fnando/Projects/sample && react-native run-android
    

Entre no diretório do projeto e execute `react-native run-ios`. Isso irea compilar o app, instalá-lo no simulador e iniciar uma nova aba como o [Metro](https://github.com/facebook/metro), o bundler de JavaScript do React Native que foi criado pelo Facebook.

    $ react-native run-ios
    ...
    info + exit 0
    
    info
    
    info ** BUILD SUCCEEDED **
    
    
    info Installing build/sample/Build/Products/Debug-iphonesimulator/sample.app
    info Launching org.reactjs.native.example.sample
    org.reactjs.native.example.sample: 5043
    

Fique de olho na aba do Metro. É nela que você verá erros enquanto estiver desenvolvendo o app. Depois que toda a compilação inicial terminar, você deverá ver o app de exemplo rodando no simulador como na imagem abaixo.

![Sample app running on iOS simulator](https://imgur.com/IKycqAf.png)

Agora, e o simulador de Android? Certifique-se que o seu disposito virtual está rodando (lembre-se de fazer isso atráves da opção “Configure > AVD Manager” da tela de boas-vindas). Você pode verificar todos os dispositivos em execução com o comando `adb devices`.

    $ adb devices
    List of devices attached
    emulator-5554 device
    

Para executar o app no simulador de Android, execute o comando `react-native run-android`. Essa etapa irá compilar um monte de coisas e, então, irá instalar e iniciar o app de exemplo.

    $ react-native run-android
    ...
    
    BUILD SUCCESSFUL in 14s
    26 actionable tasks: 26 executed
    info Running /Users/fnando/Library/Android/sdk/platform-tools/adb -s emulator-5554 reverse tcp:8081 tcp:8081
    info Starting the app on emulator-5554 (/Users/fnando/Library/Android/sdk/platform-tools/adb -s emulator-5554 shell am start -n com.sample/com.sample.MainActivity)...
    Starting: Intent { cmp=com.sample/.MainActivity }
    

Se tudo deu certo, o simulador será iniciado como na imagem abaixo.

![Sample app running on Android simulator](https://imgur.com/MwxrSpJ.png)

## Executando o app em dispositivos físicos

Em algum momento, você deve testar o app em dispositivos físicos, ou seja, o aparelho de verdade. Isso ajudará a corrigir problemas na experiência que podem não incomodar tanto em simuladores.

### Executando o app no iPhone

Para executar o app no iPhone, abra o arquivo `ios/sample.xcodeproj` no Xcode. Você pode fazer isso através do terminal com o comando `open ios/sample.xcodeproj`.

Primeiro, você terá que criar um novo perfil de desenvolvimento. Clique no nome do projeto, depois no target (nesse caso `sample`). Mude o bundle identifier para seu próprio domínio, ou não considerá compilar o projeto. Clique no botão “Add Account”, informe sua conta da Apple e selecione o seu nome no dropdown. Você também precisará selecionar o seu perfil de desenvolvimento para o target `sampleTests`.

![Xcode developer account](https://imgur.com/WEfIvNB.png)

Conecte o seu iPhone ao computador e clique no seletor de simuladores.

![Xcode's simulator selector](https://imgur.com/vedpeyX.png)

O seu iphone será listado no começo da lista.

![Physical iOS device selected](https://imgur.com/i1UrpRu.png)

Finalmente, clique no botão “Build and Run”, ou pressione cmd-R. Essa etapa irá instalar e abrir o app em seu iPhone.

![Running app on physical iPhone 8](https://imgur.com/HhTRaUS.jpg)

### Executando o app no Android

Eu não tinha um Android antes de começar a desenvolver com React Native. Por isso, decidi comprar um aparelho para testes e, depois de ver diversos reviews, decidi comprar um [Xiaomi Mi A2](https://www.mi.com/global/mi-a2/), que me custou por volta de $170 na Amazon. É um Android muito legal até mesmo para o uso diário, principalmente porque ele vem com o Android oficial, e não uma versão modificada que não presta.

Primeiro, você terá que ativar o Developer Options. Aqui a coisa pode complicar um pouco. No meu caso, eu tive que fazer isso em “Settings > About phone” e dar tap 7 vezes no Build Number para ativar o modo de desenvolvimento. Depois disso, vá em “Settings > System > Advanced > Developer Options” e ative “USB Debugging”.

Para verificar se o seu disposito pode ser visto pelo React Native, execute `adb devices`.

    $ adb devices
    List of devices attached
    bbb5cc28  device

Finalmente, execute `react-native run-android`. Este comando irá instalar e abrir o app em seu Android.

![Running app on physical Android device](https://s3.amazonaws.com/nandovieira/media/react-native-setup/app-running-on-android-device.jpg)

## Usando TypeScript

Essa é uma etapa opcional, mas usar [TypeScript](https://www.typescriptlang.org/), a linguagem tipada da Microsoft que compila para JavaScript, pode ser uma boa opção se você pretende publicar o seu app como um projeto open-source.

Para novos projetos, basta que você use o gerador de apps com `--template typescript`.

    $ npx react-native-cli init sample --template typescript
    ...
    ✨  Done in 4.96s.
    
      Run instructions for iOS:
        • cd /Users/fnando/Projects/sample_ts && react-native run-ios
        - or -
        • Open ios/sample_ts.xcodeproj in Xcode
        • Hit the Run button
    
      Run instructions for Android:
        • Have an Android emulator running (quickest way to get started), or a device connected.
        • cd /Users/fnando/Projects/sample_ts && react-native run-android
    

Para projetos existentes, você terá que configurar manualmente tudo o que o template de TypeScript fornece, além de ter que renomear arquivos para as extensões `.ts` e `.tsx`. Eu não vou mostrar como fazer isso, mas existe um [artigo publicado](https://facebook.github.io/react-native/blog/2018/05/07/using-typescript-with-react-native) no blog oficial que tem o passo-a-passo.

## Finalizando

Apesar de todos os esforços em criar um bom ecossistema, o React Native ainda é um projeto imaturo e você verá que desenvolver apps para ele é bem desafiador. Mesmo com essas dificuldades, eu acredito que o React Native é uma excelente alternativa para times e empresas pequenos que precisam desenvolver apps nativos.

Antes de apostar em React Native, pergunte-se se um [PWA](https://developers.google.com/web/progressive-web-apps/) pode ser uma alternativa viável. Infelizmente, PWA vem com seus próprios desafios, como uma nova forma de instalar apps e inconsistências no suporte entre Android e iOS, assim como diversas limitações do dispositivo. Mesmo assim, pode ser um bom primeiro passo para se criar mobile apps quando responsive web não é suficiente, mas React Native é muito complicado.