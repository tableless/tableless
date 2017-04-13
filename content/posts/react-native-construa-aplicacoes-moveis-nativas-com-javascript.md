---
title: 'React Native: Construa aplicações móveis nativas com JavaScript'
author: Carlos Cabral
type: post
date: 2016-04-05
excerpt: |
  |
    Construir aplicações multiplataforma nunca foi tão simples e divertido. Conheça o framework que está mudando os rumos do desenvolvimento mobile baseado em JavaScript.
url: /react-native-construa-aplicacoes-moveis-nativas-com-javascript/
titulo_personalizado:
  - 'React Native: Um framework para aplicações <strong>nativas em React</strong>'
categories:
  - Código
  - CSS
  - Design
  - Destaques
  - JavaScript
  - Mobile
tags:
  - android
  - flexbox
  - ios
  - jsx
  - mobile
  - react

---
## Introdução

O **React Native** é um projeto desenvolvido pelos engenheiros do **Facebook** e que consiste em uma série de ferramentas que viabilizam a criação de aplicações móveis **nativas** para a plataforma **iOS** e **Android**, utilizando o que há de mais moderno no desenvolvimento Front-end &#8211; mirando no futuro. É o estado da arte no que se refere ao desenvolvimento mobile baseado em JavaScript.

O stack do React Native é poderoso, pois nos permite utilizar **ECMAScript 6**, **CSS Flexbox**, **JSX**, diversos pacotes do **NPM** e muito mais. Sem contar que nos permite fazer debug na mesma IDE utilizada para o desenvolvimento nativo com essas plataformas (além de tornar o processo extremamente divertido).

## Setup

Nesta introdução ao React Native iremos criar um aplicativo nativo voltado para a plataforma iOS, o que significa que você precisa de um computador rodando **Mac OS X**. Embora o desenvolvimento para Android já seja possível com o framework (foi anunciado em setembro de 2015), o foco aqui será o iOS. Mas irei falar um pouco sobre o Android mais à frente neste post.

### Instalando o Xcode

A primeira coisa que você precisa instalar (caso ainda não o tenha em sua máquina) é o **Xcode**. Xcode é a IDE de desenvolvimento da Apple para criação de aplicativos para iPhone e iPad. Sua instalação é necessária pois, sem ele, nosso código não poderá ser &#8220;compilado&#8221; para Objective-C. Também é nele que iremos fazer o debug de nossa aplicação.

Para instalar, basta abrir a App Store no seu Mac e buscar por &#8220;Xcode&#8221;. A instalação pode ser um pouco demorada. Aproveite esse tempo pra contar para os seus familiares que você irá construir uma aplicação iOS nativa utilizando apenas JavaScript e os recursos mais modernos da plataforma. 😉

### Instalando o Node.js

O React Native é um projeto que utiliza recursos provenientes do Node.js, portanto precisaremos dele para prosseguir.

Há duas maneiras de instalar o Nodejs: Voce pode fazer download diretamente no <a href="https://nodejs.org/en/download/" target="_blank">site do projeto</a> ou através do <a href="http://brew.sh/" target="_blank">Homebrew</a>, o famoso package manager do Mac OS X. Caso já o tenha instalado na sua máquina, basta digitar o seguinte código no seu Terminal:

`brew install node`

Ter o Homebrew instalado na sua máquina é preferível pois iremos utilizá-lo para instalar a maioria dos outros pacotes necessários para nossa aplicação.

> Conforme sugerido pela documentação oficial, você pode instalar o **NVM** (Node Version Manager) ao invés de instalar o Node diretamente, já que o React Native trabalha com versões do Node iguais ou superiores à versão 4.0. Basta digitar no Terminal &#8220;**brew install nvm**&#8221; e em seguida &#8220;**nvm install node && nvm alias default node**&#8221; para garantir a instalação da versão mais recente.

### Instalando o Watchman

O **Watchman** é um pacote muito bacana responsável por monitorar alterações em nosso código e atualizar a nossas views em tempo real (um recurso extremamente poderoso no qual iremos falar mais à frente).

Digite a seguinte instrução no seu Terminal:

`brew install --HEAD watchman`

O parâmetro `--HEAD` é necessário pois garante que a última versão do Watchman será instalada, evitando problemas de compatibilidade com a versão mais recente do Framework.

Ótimo. Estamos quase lá&#8230;

### Instalando o CLI do React Native

Por fim, precisamos instalar o **CLI** (Command Line Interface) do projeto que consiste em uma série de helpers necessários para a criação dos nossos aplicativos. Dessa vez, iremos instalar utilizando o NPM:

`npm install -g react-native-cli`

Utilizamos o `-g` para instalar o CLI de forma global em nossa máquina.

Perfeito! Agora que todo o nosso arsenal foi preparado, podemos iniciar nossa aventura. Vamos conhecer um pouco do React Native e criar uma aplicação simples de exemplo.

> Caso queira acompanhar através do **Git**, basta clonar o <a href="https://github.com/carloscabral/myFirstProject---React-Native" target="_blank">repositório do projeto no Github</a>, acessar a pasta do mesmo através da linha de comando e digitar as seguintes instruções no Terminal: **git checkout step2 && npm install**

## Executando o aplicativo de exemplo

Criar uma aplicação com o React Native é muito simples. Crie uma pasta qualquer e navegue pra dentro dela utilizando o Terminal. Digite o seguinte comando:

`react-native init MyFirstProject`

Se você abrir a pasta do projeto no seu computador, irá verificar que três arquivos foram automaticamente criados:

  * index.ios.js
  * index.android.js
  * package.json

E três pastas também:

  * ios
  * android
  * node_modules

O arquivo _index.ios.js_ é onde iremos escrever o código da nossa aplicação. A vantagem aqui é que podemos utilizar o nosso editor de texto favorito ao invés de uma IDE (prática comum entre os devs Frontend). O arquivo _package.json_ é criado automaticamente pelo NPM e serve para gerenciar as dependências da nossa aplicação, que, por sua vez, ficam disponíveis na pasta _node_modules_.

A pasta _ios_ é onde a mágica ocorre. Esta é a pasta que contém o projeto iOS nativo gerado pelo React Native (o mesmo conceito para a pasta android). Faça um teste e abra o arquivo _MyFirstProject.xcodeproj_ no Xcode para visualizar sua extrutura no **Project Navigator** (à esquerda). Agora pressione o botão **Run** na barra de ferramentas, conforme a imagem:

[<img class="alignnone size-full wp-image-52737" src="http://tableless.com.br/uploads/2016/01/xcode-run-button.jpg" alt="xcode-run-button" width="442" height="139" />][1]

Com isso acabamos de solicitar a execução do aplicativo. Neste momento estamos &#8220;compilando o código JavaScript&#8221; presente no nosso projeto (criado por default) para Objective-C e gerando o bundle da aplicação. Agora já podemos testar o resultado em um emulador.

Geralmente o emulador demora um pouco para exibir alguma coisa na primeira vez que é acionado, mas nada lhe impede de rodar o app em um iPhone real. Basta abrir o arquivo _AppDelegate.m_, localizar a string atribuída ao objeto `jsCodeLocation` com o conteúdo **@http://localhost:8081/&#8230;** e alterar o valor de `localhost` para o número de IP do seu computador. Lembre-se que o device precisa estar conectado ao seu Mac através da porta USB e ambos devem compartilhar da mesma rede Wifi. Por fim, basta selecionar o seu iPhone na lista de emuladores disponíveis no Xcode.

> Para que o procedimento acima seja possível, é necessário que você tenha uma conta de desenvolvedor (iOS developer account) configurada na Apple. Basta gerar um certificado, registrar o seu device e &#8211; depois de efetuar todo o exaustivo processo de configuração &#8211; ele ficará disponível na lista de **deploy target** do Xcode.

Quando o emulador terminar de carregar, o resultado exibido será este:

[<img class="alignnone size-full wp-image-52742" src="http://tableless.com.br/uploads/2016/01/react-native-initial-screen_2.jpg" alt="react native initial screen" width="344" height="524" />][2]

Perceba que o aplicativo de exemplo contém apenas poucos parágrafos com instruções básicas:

  * Para iniciar, basta editar o arquivo _index.ios.js_;
  * Para recarregar a aplicação, basta pressionar **CMD + R** no teclado.

Vamos então abrir o arquivo _index.ios.js_ em nosso editor favorito. No meu caso, irei trabalhar com o <a href="http://www.sublimetext.com/2" target="_blank">Sublime Text 2</a>.

Se você já está acostumado com a escrita de código do React, não há motivos para sustos. Mas, se este não for o seu caso, não entre em pânico: o React Native é muito simples de trabalhar.

Vamos fazer um pouco de mágica agora: Encontre o texto **Welcome to React Native** e modifique-o para **My First Voodoo App!** &#8211; ou qualquer outra coisa que você queira. Abra o emulador e pressione **CMD + R** no seu teclado (caso abra uma action sheet, basta clicar em &#8220;Reload&#8221;). Perceba que, em poucos segundos, sua View foi atualizada com o texto novo. Este, meu amigo, é um dos recursos mais fantásticos presentes na plataforma: O live-reload!

Se você já vem de um background web, deve estar se perguntando: &#8221; &#8211; Sério? Existe motivo para dramatizar com isso?&#8221;. Mas se você já tem experiência no desenvolvimento com **Swift** ou **Objective-C** deve saber que alterações feitas no seu código precisam ser re-compiladas no Xcode para que você possa visualizar o que foi modificado. Alterações em Views não são refletidas em tempo real quando você está trabalhando de forma nativa. Isso, por si só, já faz o React Native merecer sua atenção!

> Fazer preview de alterações visuais de componentes em tempo de desenvolvimento é um recurso que pode ser conseguido com **IBDesignables** de modo nativo. Este recurso está disponível a partir da versão 6 do Xcode. Com ele o desenvolvedor pode visualizar aquilo que está modificando na View sem precisar compilar o app. Mas este é um recurso relativamente avançado utilizado por desenvolvedores mais experientes e que necessita de escrita de código para funcionar.

Vamos agora tentar entender melhor como foi estruturado o código de exemplo e o que cada bloco significa.

## Estrutura do React Native

Todo projeto em React tem como premissa a criação e reutilização de componentes. Basicamente, o que o código de exemplo faz é criar o componente e exibi-lo na tela. Olhando pra ele, você já deve ter reparado que o bloco central é o principal responsável por essa operação:

<pre class="lang-javascript">var MyFirstProject = React.createClass({
 render: function() {
   return (
     &lt;View style={styles.container}&gt;
       &lt;Text style={styles.welcome}&gt;
         My First Voodoo App!
       &lt;/Text&gt;
       &lt;Text style={styles.instructions}&gt;
         To get started, edit index.ios.js
       &lt;/Text&gt;
       &lt;Text style={styles.instructions}&gt;
         Shake or press menu button for dev menu
       &lt;/Text&gt;
     &lt;/View&gt;
   );
 }
});
</pre>

Agora que você já brincou um pouco com o código gerado por default, vamos esquecê-lo por um minuto e criar algo do zero.

Exclua todo o conteúdo do arquivo _index.ios.js_.

Em React, para criar um novo componente, basta criar uma variável qualquer que receba a notação:

<pre class="lang-javascript">React.createClass({});
</pre>

Por exemplo:

<pre class="lang-javascript">var Tableless = React.createClass({

});
</pre>

Agora é necessário suprir esse componente com parâmetros e uma série de instruções, responsáveis por definir o seu comportamento e aspecto visual. Quem se responsabiliza por isso é o método `render`.

Por exemplo, se quisermos retornar alguma coisa na classe **Tableless** que acabamos de criar, faríamos:

<pre class="lang-javascript">var Tableless = React.createClass({
   render: function() {
      return &lt;p&gt;Hello, Tableless!&lt;/p&gt;;
   }
});
</pre>

Mas, pera aí&#8230; O que significa essa tag de parágrafo HTML envolta do texto? Afinal, estamos lidando com HTML ou JavaScript?

### JSX

Para facilitar a escrita de código, o React utiliza **JSX** (opcional), uma sintaxe que possibilita a escrita de componentes JavaScript por meio de tags.

Para ilustrar isso melhor, o componente acima poderia ser escrito da seguinte maneira sem o uso do JSX:

<pre class="lang-javascript">var Tableless = React.createClass({
  render: function() {
     return React.createElement("p", null, "Hello, Tableless!");
  }
});
</pre>

Conforme pode ser observado, esta é uma forma de escrita muito mais verbosa do que a anterior. Eu sei, pode parecer que você está escrevendo HTML dentro de JavaScript mas, com a devida prática, você vai entender como o JSX quebra um grande galho para o desenvolvedor. Optar por não utilizá-lo é certeza de ter um código muito repetitivo e de difícil manutenção.

Agora que você compreendeu como funciona o JSX, deve estar se perguntando (pelo menos eu espero) como uma aplicação móvel pode retornar tags HTML como `p`, `h1` ou `div` dentro de um componente nativo, certo?

Exatamente&#8230; não pode.

Embora o código acima execute sem falhas em aplicações web, ele não funcionaria dentro do escopo do React Native, simplesmente porque o que precisamos são de componentes do iOS, como `UIView`, `UILabel` e `UIImage`. Ou seja, se você precisa de um &#8220;wrapper&#8221; na sua tela, você irá retornar o componente `<View>` ao invés de uma `<div>`. Caso queira exibir um texto, você irá utilizar a tag `<Text>` ao invés de um `<p>` e assim por diante.

<a href="https://facebook.github.io/react-native/docs/" target="_blank">Aqui</a> você encontra a listagem completa dos componentes disponíveis, tanto para iOS quanto para Android.

### ES6

Após a criação de um componente precisamos registrá-lo para exibição. Fazemos isso retornando a função com o nome do componente através do `AppRegistry`, dessa forma:

<pre class="lang-javascript">AppRegistry.registerComponent('MyFirstProject', () =&gt; Tableless);
</pre>

Se o código acima não ficou óbvio pra você, não se assuste. Por default o React Native permite que trabalhemos com as novas epecificações do **EcmaScript 6** (ou 2015, para os íntimos). Uma delas é a sintaxe chamada de **arrow functions** (familiar para quem já trabalhou com **CoffeeScript**), que permite uma escrita mais simples baseada em **closures**.

A versão JavaScript **ES5** do código acima seria:

<pre class="lang-javascript">AppRegistry.registerComponent('MyFirstProject', function() {
   return Tableless
});
</pre>

Mas uma vez, é uma questão de preferência e não uma imposição da ferramenta.

Contudo, o que fizemos até aqui não será suficiente para fazer o código rodar. Nós não definimos nenhuma das dependências declaradas na aplicação. Vamos resolver esse problema:

<pre class="lang-javascript">var React = require('react-native');</pre>

A string entre aspas é a biblioteca que estamos solicitando acesso. Nesta caso, estamos atribuindo seu retorno à variável React que acabamos de criar.

Agora que temos acesso à principal biblioteca do React, vamos declarar as restantes, necessárias para rodar nossa aplicação sem erros. A versão completa do nosso código fica assim:

<pre class="lang-javascript">'use strict';

var React = require('react-native');
var AppRegistry = React.AppRegistry;
var View = React.View;
var Text = React.Text;

var Tableless = React.createClass({
    render: function() {
        return &lt;View&gt;
            &lt;Text&gt;
              Hello, Tableless!
            &lt;/Text&gt;
        &lt;/View&gt;
    }
});

AppRegistry.registerComponent('MyFirstProject', () =&gt; Tableless);
</pre>

Se você pressionar **CMD + R** no teclado já terá uma aplicação rodando sem erros. Mas vamos corrigir mais duas coisinhas pra deixar nosso código ainda mais atraente&#8230;

Substitua o código do escopo de declaração pelo seguinte:

<pre class="lang-javascript">var React = require('react-native');
var {
  AppRegistry,
  View,
  Text,
} = React;
</pre>

Como todas as bibliotecas declaradas depois da react-native fazem parte do seu core, podemos assinalar as três variáveis seguintes ao objeto React. Este é mais um recurso disponível do **ES6/ES2015** chamado de **destructuring assignment**.

Outra coisa que não está muito legal no código é a indentação dos componentes no método return. Vamos envolvê-los em um parênteses para que seja permitido pular de linha e tabular tudo seguindo uma melhor hierarquia visual, dessa forma:

<pre class="lang-javascript">render: function() {
     return (
       &lt;View&gt;
          &lt;Text&gt;
             Hello, Tableless!
          &lt;/Text&gt;
       &lt;/View&gt;
     );
  }
</pre>

Vale salientar que sem o parênteses essa tabulação não seria possível e iria disparar um erro no simulador.

Vamos ver como ficou o código final agora:

<pre class="lang-javascript">'use strict';

var React = require('react-native');
var {
  AppRegistry,
  View,
  Text,
} = React;

var Tableless = React.createClass({
   render: function() {
      return (
         &lt;View&gt;
             &lt;Text&gt;
                Hello, Tableless!
             &lt;/Text&gt;
         &lt;/View&gt;
      );
   }
});

AppRegistry.registerComponent('MyFirstProject', () =&gt; Tableless);
</pre>

Se você rodar o aplicativo, irá perceber que o mesmo executa sem erros. Mas, numa primeira olhada, parece que não há nada na tela! Se você observar atentamente, irá perceber que o texto está no canto superior esquerdo da tela, sem qualquer tipo de orientação ou margem. Precisamos corrigir isso!

[<img class="alignnone size-full wp-image-52746" src="http://tableless.com.br/uploads/2016/01/react-native-simple-label_1.jpg" alt="react native simple label" width="344" height="524" />][3]

### Flexbox

Como estamos lidando exclusivamente com JavaScript, não temos acesso a CSS. Mas para aproximar a experiência de criar aplicativos móveis ao desenvolvimento de uma página web, os responsáveis pelo projeto desenvolveram uma maneira declarativa de estilizar componentes bem similar ao CSS.

Insira a seguinte notação no bloco da View principal (linha 2 do código):

<pre class="lang-javascript">return (
      // fazemos referência ao estilo
      &lt;View style={styles.container}&gt;
          &lt;Text&gt;
              Hello, Tableless!
          &lt;/Text&gt;
      &lt;/View&gt;
   );
</pre>

Agora vamos criar uma variável &#8220;styles&#8221; que recebe o objeto **StyleSheet** com os seguintes parâmetros:

<pre class="lang-javascript">var styles = StyleSheet.create({

container: {
   flex: 1,
   flexDirection: 'column',
   justifyContent: 'center',
   alignItems: 'center',
   borderWidth: 2,
   borderColor: 'ff0000',
}

})
</pre>

Antes de executar o código, precisamos incluir o **StyleSheet** em nosso escopo de inicialização:

<pre class="lang-javascript">var {
  AppRegistry,
  StyleSheet,
  Text,
  View,
} = React;
</pre>

Agora sim. Execute o código pelo Xcode e você verá o seguinte resultado:

[<img class="alignnone size-full wp-image-52767" src="http://tableless.com.br/uploads/2016/01/react-native-simple-label_3.2.jpg" alt="react native simple label with border" width="344" height="524" />][4]

O texto agora se encontra alinhado no centro da tela e temos uma borda vermelha envolta do container. O que aconteceu aqui?

Bem, nós criamos um objeto container com seis parâmetros: `flex`, `flexDirection`, `justifyContent`, `alignItems`, `borderWidth` e `borderColor`. Os dois últimos são autoexplicativos e similares à aplicação de bordas do CSS. A diferença aqui é que ao invés de declarar `border-width`, com hífen, declaramos `borderWidth`, em **camelCase** (lembrando que estamos lidando com JavaScript e não CSS de verdade). Outra observação importante é que não precisamos atribuir **px** ao final do valor como fazemos na web, pois aplicativos nativos tem suas resoluções de tela baseada em pontos **(pt)** e não em pixels.

O React Native utiliza o **Flexbox** para organização visual dos componentes, o que simplifica, em muito, a construção de layouts. Basicamente, o parâmetro `flex: 1` significa que o container ocupa 100% de altura e largura na tela. O parâmetro `flexDirection: column` significa que os elementos seguirão o fluxo baseado em colunas, que é de cima para baixo. A outra opção seria `flexDirection: row`, onde os elementos são ordenados da esquerda para a direita. Por default, O fluxo padrão é o de colunas, portanto você pode apagar essa instrução sem nenhum impacto no seu código.

Por fim, temos a instrução `justifyContent: center` e `alignItems: center`. O primeiro é responsável por alinhar o conteúdo de forma vertical (eixo y), enquanto o último serve para alinhar de forma horizontal (eixo x). Além de `center`, também existem outros valores como `flex-start` e `flex-end`. Tente utilizá-los para ver o que acontece no seu layout&#8230;

> Se ainda restou alguma dúvida, <a href="http://tableless.com.br/centralizando-conteudo-na-vertical-e-horizontal-com-css-flexbox/" target="_blank">este post</a> escrito pelo Diego Eis pode te ajudar a entender.

E se eu quiser uma borda arredondada envolta do texto e não no container? Também gostaria de mudar a cor do texto, centralizá-lo e inserir um padding envolta do mesmo. Simples&#8230;

<pre class="lang-javascript">'use strict';

var React = require('react-native');
var {
 AppRegistry,
 StyleSheet,
 Text,
 View,
} = React;

var Tableless = React.createClass({
   render: function() {
      return (
         &lt;View style={styles.container}&gt;
             // criamos um novo estilo para o componente de texto
             &lt;Text style={styles.myText}&gt;
                 Hello, Tableless!
             &lt;/Text&gt;
         &lt;/View&gt;
      );
   }
});

var styles = StyleSheet.create({

 container: {
   flex: 1,
   flexDirection: 'column',
   justifyContent: 'center',
   alignItems: 'center',
 },
 // declaração do nosso novo estilo
 myText: {            
   borderWidth: 2,
   borderColor: 'ff0000',
   borderRadius: 4,
   textAlign: 'center',
   padding: 10,
 // também é permitido passar uma string da cor ao invés de um hexadecimal
   color: 'green',
 }

})

AppRegistry.registerComponent('MyFirstProject', () =&gt; Tableless);
</pre>

Executando o código:

[<img class="alignnone size-full wp-image-52746" src="http://tableless.com.br/uploads/2016/01/react-native-simple-label_2.jpg" alt="react native simple label" width="344" height="524" />][5]

Agora que você já está familiarizado com o &#8220;modo React&#8221; de criar aplicações, vamos tentar entender rapidamente o que acontece por baixo dos panos&#8230;

## JavaScriptCore

Se você já ouviu falar sobre React, já ouviu sobre **Virtual DOM**. Essa é uma forma genial de abstração que os engenheiros do facebook desenvolveram para trazer melhorias na performance de aplicações web, uma vez que um <a href="https://pt.wikipedia.org/wiki/Modelo_de_Objeto_de_Documentos" target="_blank">DOM</a> Virtual fica em memória e apenas modificações significativas em sua estrutura são novamente renderizadas na tela, sem necessidade de percorrer toda a árvore novamente.

Em algum momento eles pensaram: _&#8220;E se, utilizando essa abordagem, pudéssemos também abstrair uma camada qualquer diferente do DOM para conseguir resultados similares em relação à performance?&#8230;&#8221;_

Até então, o único componente presente no iOS e no Android que viabiliza a execução de código JavaScript de modo nativo são seus browsers internos, conhecidos como WebViews. Com base nesse cenário, vários frameworks surgiram nos últimos anos com a proposta de utilizar a camada de código nativa apenas para disparar uma aplicação com código escrito em HTML, CSS e JavaScript no próprio Browser (sem a barra de endereços, obviamente). Como o container responsável pelo ciclo de vida da aplicação é nativo, isso possibilita que essas aplicações sejam desenvolvidas e distribuídas através das lojas oficiais, como a **App Store** e <a href="https://play.google.com/store/apps" target="_blank">Google Play</a>, sem maiores problemas. Esse movimento originou o termo atualmente conhecido como **Aplicativos Híbridos**. Embora essa abordagem provou-se vitoriosa em alguns cenários, ainda consiste em uma página web que simula uma aplicação escrita de forma nativa, o que, algumas vezes, peca em questão de performance e experiência.

Em React Native continuamos escrevendo um aplicativo em JavaScript, mas que não exibe uma página web como resultado. Ao invés disso, o nosso código executa uma instância do chamado <a href="http://trac.webkit.org/wiki/JavaScriptCore" target="_blank">JavaScriptCore</a> responsável por renderizar componentes **verdadeiramente nativos** dentro do nosso app. Por exemplo, se você abrir o arquivo _/ios/MyFirstProject/AppDelegate.m_ no Xcode, vai encontrar sempre o seguinte conteúdo, independente da quantidade de código que tiver escrito no seu editor de texto:

[<img class="alignnone size-full wp-image-53026" src="http://tableless.com.br/uploads/2016/01/AppDelegate.png" alt="AppDelegate.m image " width="844" height="777" />][6]

O segredo está nessa classe `RCTRootView`. Ela é uma classe criada pelo próprio framework, responsável por apresentar os elementos da classe `UIKit` com base no código que escrevemos em JS. Ou seja, o controle do comportamento do nosso app é feito em JavaScript, mas em nenhum momento ocorre compilação desse código para Objective-C, binário ou coisa do tipo. Por isso conseguimos ver atualizações em tempo real em nossa aplicação, uma vez que nenhum código em Objective-C é escrito, apenas código JavaScript. Não tem nada pra re-compilar! Genial.

Como essa &#8220;passagem de bastão&#8221; entre o código JavaScript e Objective-C é feita está fora do escopo desse post, mas caso tenha curiosidade de saber onde vai parar o código que escrevemos, basta acessar a url <a href="http://localhost:8081/index.ios.bundle?platform=ios& dev=true" target="_blank">http://localhost:8081/index.ios.bundle?platform=ios& dev=true</a> enquanto a aplicação estiver no ar. Você irá perceber nosso código em meio à um monte de outros gerados pelo framework.

## Explorando as APIs e componentes nativos

Uma das coisas mais legais &#8211; e vantajosas &#8211; de se trabalhar com o React Native é a possibilidade de utilizar os componentes e APIs nativos da plataforma. Indiscutivelmente, é um recurso que oferece uma experiência mais atrativa para o usuário e que torna dispensável a utilização de serviços de terceiros como o <a href="https://cordova.apache.org/" target="_blank">Apache Cordova</a>, por exemplo. O React Native também trabalha em uma thread separada da thread principal, o que faz com que sua aplicação mantenha a alta performance sem sacrificar a capacidade do seu smartphone (o que é incrível!).

Para começar a ilustrar esses pontos, vamos modificar o nosso código para exibir um alerta nativo do iOS quando um botão for clicado.

### Capturando eventos e fornecendo feedback visual

Assim como todos os demais componentes, o React Native criou um específico para recuperar o evento de **touch** (ou tap) na tela do device. Seu nome é `<TouchableHighlight>`, que nada mais é do que um wrapper invisível responsável por fazer algum outro componente responder ao toque do usuário e, em seguida, conectá-lo a algum evento/método:

<pre class="lang-javascript">&lt;TouchableHighlight onPress={this.someFunction}&gt;
   // aplicação de estilo no componente
   &lt;View style={styles.button}&gt;
      &lt;Text&gt;An Alert Message&lt;/Text&gt;
   &lt;/View&gt;
&lt;/TouchableHighlight&gt;
</pre>

No código acima temos um exemplo de como podemos fazer uso desse componente. Perceba que dentro dele temos uma outra `<View>` que abriga um componente `<Text>` com um texto indicativo. O `<TouchableHighlight>` recebe uma função de nome `someFunction` quando o evento **onPress** for acionado. Outra coisa bacana do componente é que o mesmo fornece feedback visual do momento em que o usuário pressiona e solta o botão. Por default, o React Native aplica um efeito de **overlay** ao componente sem que precisemos fazer nada. Awesome!

O `<TouchableHighlight>` também responde à outros eventos, como `onPressIn`, `onPressOut` e `onLongPress`, para atender às demais necessidades de interação com o usuário.

Vamos agora mexer no nosso código e substituir a função `someFunction` do evento `onPress` do nosso botão por um **alert dialog** nativo da plataforma. O código do alerta é muito simples, conforme abaixo:

<pre class="lang-javascript">AlertIOS.alert(
  'Simple Title',
  'Hi, I am a native iOS alert component in action.'
)
</pre>

Nosso alerta é simples e recebe apenas dois parâmetros: O título e a descrição que serão exibidos para o usuário. Vamos juntar tudo e ver como fica o nosso código final (`git checkout step3`):

<pre class="lang-javascript">'use strict';

var React = require('react-native');
var {
   AppRegistry,
   StyleSheet,
   Text,
   View,
   // declaramos o TouchableHighlight.
   TouchableHighlight,     
   // declaramos o AlertIOS.
   AlertIOS,           
} = React;

var Tableless = React.createClass({

 render: function() {
   return (
      &lt;View style={styles.container} &gt;
        &lt;Text style={styles.myText}&gt;
          Hello, Tableless!
        &lt;/Text&gt;
        // inserimos o código do alerta no lugar da função
        &lt;TouchableHighlight onPress={() =&gt; AlertIOS.alert(    
             'Simple Title',
             'Hi, I am a native iOS alert component in action.'
           )}&gt;
           &lt;View style={styles.button}&gt;
               // exemplo de estilo inline.
               &lt;Text style={{color: '#fff'}}&gt;An Alert Message&lt;/Text&gt; 
           &lt;/View&gt;
        &lt;/TouchableHighlight&gt;
      &lt;/View&gt;
    );
 }
});

var styles = StyleSheet.create({

container: {
   flex: 1,
   flexDirection: 'column',
   justifyContent: 'center',
   alignItems: 'center',
},
myText: {
   borderWidth: 2,
   borderColor: 'ff0000',
   borderRadius: 4,
   textAlign: 'center',
   padding: 10,
   marginBottom: 10,
   color: 'green',
},
// estilo do botão.
button: {                
   backgroundColor: 'lightblue',
   padding: 20,
   borderRadius: 5,
},

})

AppRegistry.registerComponent('MyFirstProject', () =&gt; Tableless);
</pre>

Pressione **CMD + R** no teclado e veja o resultado do que criamos no seu emulador com poucas linhas de código:

[<img class="alignnone size-full wp-image-52771" src="http://tableless.com.br/uploads/2016/01/react-native-alert-ios.gif" alt="react native alert ios" width="640" height="480" />][7]

### Props & State

Tudo o que fizemos até o momento foi ótimo, mas não é o suficiente para manter uma aplicação em funcionamento. E se eu quisesse alterar o valor do texto que aparece na tela de forma dinâmica, com base em um input do usuário? Podemos fazer isso facilmente utilizando o conceito de **state**, que nada mais é do que **gerenciar um componente e aplicar alterações em seu valor durante seu ciclo de vida**.

Para que isso seja possível, precisaremos de três coisas novas em nosso código:

  * Um método que defina o **estado inicial** do meu componente;
  * Um componente nativo que receba **inputs do usuário** na tela;
  * Um método responsável por **modificar o valor** desse meu componente.

Primeiramente, vamos criar o estado inicial do meu componente:

<pre class="lang-javascript">getInitialState : function() {
   // Inicializamos nosso componente com uma String de texto.
   return { myText : "Hello, Tableless!" };
},    
</pre>

Em seguida, um componente para receber inputs do usuário:

<pre class="lang-javascript">&lt;TextInput
         placeholder="Type something..."
         onChange={this.textInputDidChange} /&gt;
// Input com um placeholder + método.
</pre>

E, por fim, a função com o método responsável por atualizar o estado da minha View sempre que o valor do meu componente for modificado:

<pre class="lang-javascript">textInputDidChange : function (event) {      
   this.setState({ myText: event.nativeEvent.text });
},   
</pre>

Vamos ver como tudo isso fica no nosso código (`git checkout step4`).

<pre class="lang-javascript">'use strict';

var React = require('react-native');
var {
   AppRegistry,
   StyleSheet,
   Text,
   View,
   TouchableHighlight,
   AlertIOS,
   // declaramos o TextInput.
   TextInput,        
} = React;

var Tableless = React.createClass({

getInitialState : function() {
   return { myText : "Hello, Tableless!" };
},    

textInputDidChange : function (event) {      
   this.setState({ myText: event.nativeEvent.text });
},

 render: function() {
  return (
    &lt;View style={styles.container} &gt;
      // Repare os estilos inline (opcional).
      &lt;TextInput style = {{ height: 50, padding: 6, fontSize: 16, borderColor: "lightblue", borderWidth: 1,     margin: 10, borderRadius: 4 }}
               placeholder="Type something..."
               onChange={this.textInputDidChange} /&gt;   
         &lt;Text style={styles.myText}&gt;
            // Ao invés do texto estático, fazemos referência à variável myText.
            {this.state.myText}   
         &lt;/Text&gt;
         &lt;TouchableHighlight onPress={() =&gt; AlertIOS.alert(
                 'Simple Title',
                 'Hi, I am a native iOS alert component in action.'
              )}&gt;
           &lt;View style={styles.button}&gt;
                &lt;Text style={{color: '#fff'}}&gt;An Alert Message&lt;/Text&gt;
           &lt;/View&gt;
         &lt;/TouchableHighlight&gt;
    &lt;/View&gt;
  );
 }
});

var styles = StyleSheet.create({

 container: {
   flex: 1,
   flexDirection: 'column',
   justifyContent: 'center',
   alignItems: 'center',
 },
 myText: {
   borderWidth: 2,
   borderColor: 'ff0000',
   borderRadius: 4,
   textAlign: 'center',
   padding: 10,
   marginBottom: 10,
   color: 'green',
 },
 button: {
   backgroundColor: 'lightblue',
   padding: 20,
   borderRadius: 5,
 },

})

AppRegistry.registerComponent('MyFirstProject', () =&gt; Tableless);
</pre>

Agora nosso label reflete o valor que digitamos em nosso input, veja:

[<img class="alignnone size-full wp-image-52776" src="http://tableless.com.br/uploads/2016/01/react-native-text-input-ios.gif" alt="react native text input ios" width="640" height="480" />][8]

> Caso queira simular o teclado do device, basta ir na barra de ferramentas do emulador e procurar a opção **Hardware -> Keyboard -> Toggle Software Keyboard**. Ao habilitar essa opção, o teclado nativo do device será exibido sempre que um input for solicitado.

Se você tem o costume de utilizar aplicativos no iPhone já deve ter reparado que o comportamento de transição de telas é ligeiramente diferente daquilo que observamos na web. Ao invés de exibir uma outra página qualquer como resultado de alguma ação (como clique em um link ou uma busca) no iOS nós trabalhamos com um componente chamado **UINavigationController** que gerencia essa transição de forma hierárquica. Obviamente já temos à nossa disposição um componente para lidar com isso, chamado **NavigatorIOS**.

Dito isso, a primeira coisa que precisamos fazer é mudar o componente **root** da nossa aplicação que, ao invés de apontar para **Tableless**, agora irá apontar para a classe **MainNav**, conforme abaixo:

<pre class="lang-javascript">AppRegistry.registerComponent('MyFirstProject', () =&gt; MainNav);</pre>

Agora vamos criar a classe **MainNav** que irá funcionar como um container que fará referência à tela **Tableless** que estávamos trabalhando anteriormente, dessa forma:

<pre class="lang-javascript">var MainNav = React.createClass({
  render: function() {
    return (
      // Incluímos o NavigatorIOS em MainNav e fazemos ele apontar para Tableless.
      &lt;NavigatorIOS
        initialRoute={{ component: Tableless, title: 'MyFirstProject' }} 
        style={{ flex: 1 }} /&gt;
    );    
  }
});
</pre>

Perfeito. Agora vamos criar uma outra tela que será responsável por exibir o texto que iremos digitar em nossa View principal. Irei chamar essa tela de **NextScreen**:

<pre class="lang-javascript">var NextScreen = React.createClass({
  render: function() {
    return (
      &lt;View&gt;
        &lt;Text&gt;
          You entered: {this.props.inputText}
        &lt;/Text&gt;
      &lt;/View&gt;
    );
  }
});
</pre>

Perceba a instrução `{this.props.inputText}` dentro do componente `<Text>`. Ele será o responsável por apresentar o valor digitado no nosso input. Mas para que isso ocorra, precisamos de um novo evento em nosso `<TextInput>` que guarde esse valor e o conduza até a próxima tela que acabamos de criar. Já que não temos um botão pra disparar esse método, que tal chamá-lo logo após pressionar o **Return** do teclado? Existe um evento chamado `onEndEditing` que faz justamente isso:

<pre class="lang-javascript">&lt;TextInput placeholder="Type something..."
              onChange={this.textInputDidChange}
              // incluímos o novo evento aqui.
              onEndEditing={ event =&gt; this.callNextScreen(event.nativeEvent.text) } /&gt;
</pre>

Referenciamos a função de nome **callNextScreen** que recupera o texto que digitamos através do evento de nome `event.nativeEvent.text`. Vamos criar essa função:

<pre class="lang-javascript">// a função recebe o texto digitado como parâmetro
callNextScreen: function (inputText) {
  // chamamos a transição <strong>push</strong> nativa do iOS.
  this.props.navigator.push({
     title: "The Next Screen",
     component: NextScreen,
     // enviamos o parâmetro para a tela <strong>NextScreen</strong>
     passProps: { 'inputText': inputText }
  });
}
</pre>

Perceba que nós chamamos a função `push` do `navigator` que faz parte do atributo props da nossa tela **NextScreen**. Uma outra novidade é o parâmetro `passProps` que recebe um objeto com chave e valor de nome `inputText`, responsável por guardar o texto que digitamos e conduzi-lo à próxima tela. Vamos ver como ficou o código final (`git checkout step5`):

<pre class="lang-javascript">'use strict';

var React = require('react-native');
var {
  AppRegistry,
  StyleSheet,
  Text,
  View,
  TouchableHighlight,
  AlertIOS,
  TextInput,
  // novo componente NavigatorIOS
  NavigatorIOS, 
} = React;

var Tableless = React.createClass({

getInitialState : function() {
  return {
    myText : "Hello, Tableless!"
  };
},

callNextScreen: function (inputText) {
  this.props.navigator.push({
    title: "The Next Screen",
    component: NextScreen,
    passProps: { 'inputText': inputText }
});
},

textInputDidChange : function (event) {
  this.setState({ myText: event.nativeEvent.text });
},

render: function() {
  return (
   &lt;View style={styles.container} &gt;
    &lt;TextInput style = {{ height: 50, padding: 6, fontSize: 16, borderColor: "lightblue", borderWidth: 1, margin:    10, borderRadius: 4 }}
      placeholder="Type something..."
      onChange={this.textInputDidChange}
      onEndEditing={ event =&gt; this.callNextScreen(event.nativeEvent.text) } /&gt;
    &lt;Text style={styles.myText}&gt;
      {this.state.myText}
    &lt;/Text&gt;
    &lt;TouchableHighlight onPress={() =&gt; AlertIOS.alert(
        'Simple Title',
        'Hi, I am a native iOS alert component in action.'
      )}&gt;
      &lt;View style={styles.button}&gt;
        &lt;Text style={{color: '#fff'}}&gt;An Alert Message&lt;/Text&gt;
      &lt;/View&gt;
    &lt;/TouchableHighlight&gt;
   &lt;/View&gt;
  );
}

});

var MainNav = React.createClass({
 render: function() {
   return (
     &lt;NavigatorIOS
       initialRoute={{
         component: Tableless,
         title: 'MyFirstProject'
       }}
       style={{ flex: 1 }} /&gt;
   );
 }
});

var NextScreen = React.createClass({
 render: function() {
   return (
     &lt;View style = {{ backgroundColor: 'green', flex: 1, justifyContent: 'center', alignItems: 'center' }} &gt;
       &lt;Text style = {{ color: '#fff', fontSize: 22 }} &gt;
         You entered: {this.props.inputText}
       &lt;/Text&gt;
     &lt;/View&gt;
   );
 }
});

var styles = StyleSheet.create({

 container: {
   flex: 1,
   flexDirection: 'column',
   justifyContent: 'center',
   alignItems: 'center',
 },
 myText: {
   borderWidth: 2,
   borderColor: 'ff0000',
   borderRadius: 4,
   textAlign: 'center',
   padding: 10,
   marginBottom: 10,
   color: 'green',
 },
 button: {
   backgroundColor: 'lightblue',
   padding: 20,
   borderRadius: 5,
 },

})

AppRegistry.registerComponent('MyFirstProject', () =&gt; MainNav);
</pre>

O resultado:

[<img class="alignnone size-full wp-image-52778" src="http://tableless.com.br/uploads/2016/01/react-navigator-ios.gif" alt="react native navigator ios" width="640" height="480" />][9]

Faça um teste no seu device e observe o quão suave são as animações. Uma vez na tela seguinte, você pode retornar para a anterior com um simples gesto de deslizar os dedos da esquerda para a direita (o famoso **swipe gesture**). Você consegue até mesmo simular uma transição similar em html com `overflow`, mas não será a mesma coisa. Esse é o verdadeiro ganho de trabalhar com componentes 100% nativos: As transições em **60fps** (60 frames por segundo).

[<img class="alignnone size-full wp-image-52793" src="http://tableless.com.br/uploads/2016/01/react-native-swipe-60fps.gif" alt="react native swipe 60fps" width="640" height="480" />][10]

Por fim, você foi apresentado aos dois principais conceitos do React: **props**, utilizado quando queremos compartilhar valores entre componentes e **state**, quando desejamos monitorar o estado de um componente e suas alterações (geralmente ocasionado por algum evento de usuário).

## Modularidade

Você tem consciência da bagunça que nosso código pode se tornar se prosseguirmos com a escrita de toda a lógica em um mesmo arquivo, né? Mas uma das vantagens da plataforma é justamente a modularização, uma vez que cada componente pode estar isolado em arquivos diferentes, gerenciando seus próprios estados de forma individual. Fazemos isso através do **module.exports** do Node, presente na especificação do **CommonJS**.

Para ilustrar como isso pode ser feito, vamos separar nossa seção de estilos no arquivo _style.js_ e requisitar seu acesso no arquivo _index.ios.js_ (`git checkout step6`).

Conteúdo de _style.js_:

<pre class="lang-javascript">var React = require('react-native');
var { StyleSheet } = React;

var styles = StyleSheet.create({

 container: {
   flex: 1,
   flexDirection: 'column',
   justifyContent: 'center',
   alignItems: 'center',
 },
 myText: {
   borderWidth: 2,
   borderColor: 'ff0000',
   borderRadius: 4,
   textAlign: 'center',
   padding: 10,
   marginBottom: 10,
   color: 'green',
 },
 button: {
   backgroundColor: 'lightblue',
   padding: 20,
   borderRadius: 5,
 },

});
// viabilizamos a exportação do módulo.
module.exports = styles;
</pre>

E no arquivo _index.ios.js_:

<pre class="lang-javascript">'use strict';

var React = require('react-native');
var {
  AppRegistry,
  StyleSheet,
  Text,
  View,
  TouchableHighlight,
  AlertIOS,
  TextInput,
  NavigatorIOS,
} = React;

// solicitamos acesso ao conteúdo de <em>style.js</em>
var styles = require('./style');

var Tableless = React.createClass({ ... })
</pre>

Seguindo esse conceito, sua aplicação fica muito mais legível, principalmente se utilizarmos o **Nesting** de componentes (não abordado nesse tutorial).

Como exercício, tente fazer o mesmo com os demais componentes que criamos.

### Android

Uma das vantagens oferecidas pelo framework é poder criar aplicações agnósticas, que compartilham a mesma base de código. Neste caso, você poderia ter os arquivos _index.ios.js_ e _index.android.js_ apontando para uma classe &#8220;root&#8221;, responsável por executar o código com base no sistema utilizado pelo usuário: iOS ou Android. Isso é possível se você fizer uso de componentes que não são específicos de cada plataforma, como `View`, `Image`, `ListView`, `MapView`, `Modal`, `TouchableHighlight`, `Text`, etc.

Outra possibilidade, em aplicações mais complexas, é de compartilhar a mesma lógica entre ambas as plataformas com a diferença de utilizar componentes específicos para cada uma delas. A vantagem seria proporcionar a melhor experiência **nativa** possível para o usuário. Como exemplo, temos os componentes `DrawerLayoutAndroid`, `ProgressBarAndroid`, `ToolbarAndroid`, etc.

## Um futuro móvel para o JavaScript

Hoje em dia o desenvolvedor JavaScript vive um momento fantástico, pois além de contar com frameworks como <a href="http://ionicframework.com/" target="_blank">Ionic</a>, que tem o intuito de explorar o desenvolvimento híbrido através de tecnologias web, agora temos o React Native à nossa disposição, com o intuito de conduzir o JavaScript ao ambiente nativo. No entanto, diferente do conhecido termo imortalizado pelo Java &#8220;_Write once, run anywhere_&#8220;, o framework defende o &#8220;_Learn once, write anywhere_&#8220;, o que significa que cada plataforma tem seu próprio visual, estrutura e recursos únicos. E que você, como engenheiro de software, deve ser capaz de construir aplicações para qualquer que seja a plataforma &#8211; sem necessariamente aprender uma gama de novas tecnologias &#8211; mas sempre respeitando o ecossistema nativo de cada uma delas. Isso é fantástico!

Outro ponto que vale ressaltar é a otimização que o framework oferece ao dia a dia de uma equipe, uma vez que ele tem o potencial de acelerar todo o processo &#8211; não só de desenvolvimento, mas também de lançamento de um aplicativo. Como exemplo, a Apple possibilita que alterações sejam executadas no &#8220;ar&#8221; em aplicativos baseados no tal JavaScriptCore **sem precisar aguardar pelo exaustivo processo de review deles**. Ou seja, mais produtividade e mais clientes felizes!

Embora o React Native seja um framework fantástico no que se propõe a oferecer, ele não é o único. Existem outras ferramentas que permitem o desenvolvimento de aplicativos nativos utilizando JavaScript, como é o caso do já conhecido <a href="http://www.appcelerator.com/mobile-app-development-products/" target="_blank">Titanium</a> e, do mais recente, <a href="https://www.nativescript.org/" target="_blank">NativeScript</a>. Mas a grande sacada do React Native é o **React** em si. Sua natureza declarativa, a metodologia de reutilização de componentes e o foco primário na interface do usuário proporcionam uma experiência, até o momento, inédita para o desenvolvedor web que deseja migrar para o mundo do desenvolvimento móvel.

Em resumo, o React Native merece sua atenção porque&#8230;

  * **Não remove você do ecossistema da web: **As mesmas ferramentas que usamos para o desenvolvimento web são basicamente as mesmas que utilizaremos para desenvolvimento mobile. Ao invés de depender exclusivamente do Xcode ou Android Studio, um <a href="http://www.sublimetext.com/" target="_blank">SublimeText</a>, <a href="https://atom.io/" target="_blank">Atom</a> ou <a href="http://brackets.io/" target="_blank">Brackets</a> já darão conta do recado pra você. Com se isso não bastasse, você ainda tem a opção de fazer debug do código via <a href="https://developers.google.com/web/tools/chrome-devtools/" target="_blank">Chrome DevTools</a>, através de uma extensão desenvolvida exclusivamente para o React, como se fosse uma aplicação web de verdade!
  * **Utiliza Flexbox e CSS: **O Flexbox permite que você estruture sua camada visual de maneira muito simples e intuitiva. Esse é um ponto crítico em aplicações nativas. Tome o AutoLayout do iOS, como exemplo. Lidar com Constraints, Size Classes e outros recursos não são assim tão simples. Sem contar que essa fica sendo uma tarefa exclusiva do Desenvolvedor e não do Designer. Em contrapartida, se você já é um Webdesigner, pode aproveitar seu código CSS diretamente na plataforma &#8211; ou solicitar que o Designer gere ele pra você incluir no seu app. Não é o máximo?
  * **É extremamente extensível: **Você pode compartilhar o seu código JavaScript com o seu colega de trabalho que desenvolve em Objective-C, Swift ou Java sem maiores problemas. O framework possibilita a integração de módulos nativos, proporcionando um ambiente colaborativo ainda mais rico e transparente. Ou seja, sempre que houver a necessidade de implementar um módulo nativo &#8211; ou reaproveitar algum que já tenha sido criado pela sua equipe &#8211; basta importá-lo no seu projeto e ele estará disponível. Yes!
  * **Utiliza Polyfills para tirar vantagem dos recursos web: **APIs como `fetch`, `geolocation`, `setTimeout` e o próprio `flexbox` não existem em ambiente nativo, mas existem no Browser! Mais uma vez, a transição entre os ambientes web e nativo fica ainda mais simples de ser feita.
  * **Simples gerenciamento das dependências do projeto:**Programadores JavaScript já estão acostumados a utilizar o NPM para gerir dependências e fazer build de suas aplicações. Trazer essa ferramenta para dentro do escopo nativo significa menos uma barreira adicional. Em um simples arquivo _package.json_ você é capaz de organizar todas as suas dependências como se estivesse trabalhando na web, sem a necessidade de aprender ferramentas como <a href="https://cocoapods.org/" target="_blank">Cocoapods</a> para iOS ou <a href="http://gradle.org/" target="_blank">Gradle</a> no caso do Android.

## Conclusão

O desenvolvimento mobile está mudando com a mesma velocidade da demanda de mercado. Mais e mais ferramentas vêm sendo desenvolvidas com o intuito de prover uma experiência mais rica, tanto para o desenvolvedor quanto para o usuário final. Frameworks como React Native surgem como uma prova de conceito de que existem falhas em ambos os ecossistemas e o que resta fazer é unir o melhor dos dois mundos. O mais importante, no fim das contas, é a tal da estratégia. Se <a href="https://en.wikipedia.org/wiki/Time_to_market" target="_blank">tempo de mercado</a> e produtividade fazem parte do seu vocabulário (ou de sua startup), fique de olho nas mudanças. Elas estão apenas começando&#8230;

Enfim&#8230; é uma época excelente para ser um desenvolvedor JavaScript. 🙂

> Conheça mais sobre o React para web <a href="http://tableless.com.br/react-javascript-reativo/" target="_blank">neste post</a> do Davi Ferreira.

 [1]: http://tableless.com.br/uploads/2016/01/xcode-run-button.jpg
 [2]: http://tableless.com.br/uploads/2016/01/react-native-initial-screen_2.jpg
 [3]: http://tableless.com.br/uploads/2016/01/react-native-simple-label_1.jpg
 [4]: http://tableless.com.br/uploads/2016/01/react-native-simple-label_3.2.jpg
 [5]: http://tableless.com.br/uploads/2016/01/react-native-simple-label_2.jpg
 [6]: http://tableless.com.br/uploads/2016/01/AppDelegate.png
 [7]: http://tableless.com.br/uploads/2016/01/react-native-alert-ios.gif
 [8]: http://tableless.com.br/uploads/2016/01/react-native-text-input-ios.gif
 [9]: http://tableless.com.br/uploads/2016/01/react-navigator-ios.gif
 [10]: http://tableless.com.br/uploads/2016/01/react-native-swipe-60fps.gif