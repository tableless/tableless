---
title: Indo além no Mundo React-Native
author: Jose Urbano Duarte Junior
type: post
image: http://i.imgur.com/oudmGva.png
date: 2017-05-24
excerpt: Um estudo pessoal sobre as possibilidade do React Native. 
url: /indo-alem-no-react-native/
categories:
  - JavaScript
  - Mobile
  - ReactJS
  - Código
tags:
  - ReactNative
  - Android
---

# Indo além no Mundo React-Native.
Nos últimos meses resolvi aprofundar meus estudos no React Native. Após anos trabalhando apenas com desenvolvimento mobile nativo, um grande amigo me convenceu a experimentar esse novo framework.

Confesso que até então, eu era um pouco reticente sobre frameworks que prometem entregar aplicativos nas duas plataformas (iOS e Android) a partir de um código único. Minha experiência com Cordova me dizia que isso não funcionava bem. A perfomance era sempre pobre e frustrante.

Se você ainda não acredita muito nesse tipo de solução, talvez seja a hora de você experimentar coisas novas. Acredito que, em breve, você também será um entusiasta dessa tecnologia.




---

## Mergulhando um pouco mais fundo ##
Na internet, você encontra milhares de posts explicando como começar um projeto React-Native. Há tutoriais para todos os lados. O framework é simples e qualquer um com poucas horas irá conseguir criar uma tela básica. Entretanto, a situação é um pouco diferente quando falamos em integração com aplicações nativas e sobre escalabilidade.

**Nesse post quero sair do óbvio e explorar um cenário diferente. Nada para iniciantes ou desenvolvedores que querem construir aplicações simples.**

**Faremos duas "aplicações" React-Native rodando em um mesmo aplicativo. Uma sobre a outra.**

![Overview](http://i.imgur.com/DiTFTwM.png)

Inicialmente você poderá ter dificuldade em visualizar um motivo para construir tal cenário, mas tenha certeza que ao final desse post sua cabeça terá ideias malucas da aplicabilidade dessa brincadeira.



## Começando ##
Depois do ambiente React-Native instalado na sua máquina, vamos inicializar um projeto React-Native com dois arquivos um chamado _"App 1"_ e outro chamado _"App2"_.

Eu já disponibilizei um projeto em: https://github.com/oximer/react-inside-react

## Editando e Empacotando o App 2 ##

Agora, vamos começar editando o _"App 2"_.

Abra o arquivo _"app2.js"_ e o modifique conforme o desejado. Nesse primeiro exemplo, não adicione imagens ou outros recursos. Em um outro post, posso explicar como é possível adicionar recursos dentro desse projeto.

Após a realização das alterações, faça o empacotamento desse projeto. Para isso acesse o folder base do teu projeto e execute o "react-native bundle"

```
react-native bundle — platform android — dev false — entry-file app2.js — bundle-output app2.jsbundle
```

![react-native-bundle](http://i.imgur.com/OUzgVp0.png)

Você observará que o empacotador irá criar um arquivo chamado app2.jsbundle. Esse arquivo é semelhante ao que o teu servidor node disponibiliza por padrão na porta 8081.

Caso você nunca tenha feito isso, como o servidor node rodando em algum outro projeto, acesse o endereço http://localhost:8081/index.android.bundle?dev=false&mimify=true&platform=android no teu browser. Olhe esse arquivo e o compare com o arquivo gerado pelo empacotador.

## Editando e Empacotando o App 1 ##
Após concluir a edição do App 2, vamos para a modificação do aplicativo _"App 1"_. Agora iremos modificar também as camadas nativas do Android.

Primeiro abra a pasta "android" do projeto 1 no Android Studio. Pegue o arquivo _"app2.jsbundle"_ e o coloque dentro da pasta "assests" do projeto.

Agora vamos criar uma View que irá conter o App 1 e o App 2.

```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    ReactRootView app1RootView = new ReactRootView(getApplication());
    ReactInstanceManagerBuilder builder = ReactInstanceManager.builder()
            .setApplication(getApplication())
            .setDefaultHardwareBackBtnHandler(this)
            .setInitialLifecycleState(LifecycleState.RESUMED)
            .addPackage(new MainReactPackage())
            .setCurrentActivity(this)
            .setBundleAssetName("app1.jsbundle")
            .setJSMainModuleName("app1")
            .setUseDeveloperSupport(false);
    ReactInstanceManager appReactInstanceManager = builder.build();

    app1RootView.startReactApplication(appReactInstanceManager, "app1", null);
    LinearLayout linearLayout = (LinearLayout) findViewById(R.id.app1);
    linearLayout.addView(app1RootView);

    ReactRootView app2RootView = new ReactRootView(getApplication());
    builder = ReactInstanceManager.builder()
            .setApplication(getApplication())
            .setDefaultHardwareBackBtnHandler(this)
            .setInitialLifecycleState(LifecycleState.RESUMED)
            .addPackage(new MainReactPackage())
            .setCurrentActivity(this)
            .setBundleAssetName("app2.jsbundle")
            .setJSMainModuleName("app2")
            .setUseDeveloperSupport(false);
    ReactInstanceManager appReactInstanceManager2 = builder.build();

    app2RootView.startReactApplication(appReactInstanceManager2, "app2", null);
    FrameLayout frameLayout = (FrameLayout) findViewById(R.id.app2);
    frameLayout.addView(app2RootView);
}
```

Feito isso, volte para o mundo JS. Modifique o Aplicativo 1 e o empacote de maneira semelhante ao App2. Também, o coloque dentro da pasta _"assets"_

```
react-native bundle — platform android — dev false — entry-file app1.js — bundle-output app1.jsbundle
```

## Resultado Final

![finalResult](http://i.imgur.com/qDFU91F.png)
---

## Visão Geral
Esse projeto pode lhe parecer um pouco maluco e sem serventia, mas lhe garanto que entendê-lo é um importante passo para compreender como o React-Native realmente funciona.

O famoso Code Push da Microsoft entende essa ideia muito bem e tira proveito dele. O Code Push serve esses arquivos estáticos em um servidor na internet e como isso consegue atualizar as aplicações 1 e 2 remotamente.

Outro aspecto interesse é o fato de cada aplicativo funcionar como uma sandbox. Eles não compartilham estados e variáveis. Eles são literalmente independentes e podem até mesmo ser desenvolvidos por times diferentes.

Experimente colocar um contador e um botão em cada um deles… Você verá que as aplicações são independentes.

Finalmente, entenda que não existe mágica no React-Native. O seu aplicativo é uma View como qualquer outra, nesse caso uma ReactRootView. O ReactInstanceManger é outra classe essencial para o desenvolvedor que irá integrar uma aplicação React em uma aplicação nativa já existente.

## Nem tudo são flores
Ao optar pelo empacotamento estático, você fica sem algumas features legais do React-Native. Nada de _**reload**_ ou _**hot-reload**_ nesse cenário.

**Vocês vêem alguma solução?**

Eu vejo e posso detalhar mais em outros posts, mas lhes garanto que é possível colocar dois servidores node locais em sua máquina (cada um em uma porta) e ter as principais features de desenvolvimento do React.

Outro problema está relacionado à comunicação entre esses dois aplicativos. Se esses aplicativos são independentes, como eles se comunicam?

A resposta passa pela DeviceEventManagerModule e a criação de um ReactPackage. Elas exploraram a comunicação entre a camada Java e a camada Javascript.

Seria possível fazer isso no iOS? Sim, mas esse post já está longo demais.


**Referências para iniciantes em português**

https://tableless.com.br/react-native-construa-aplicacoes-moveis-nativas-com-javascript/
https://facebook.github.io/react-native/docs/getting-started.html
https://medium.com/react-native-training

**Referências para iniciantes em inglês**

https://www.raywenderlich.com/126063/react-native-tutorial

**Curso pago, mas bem interessante para quem quer investir um pouco mais**

https://www.udemy.com/the-complete-react-native-and-redux-course/
