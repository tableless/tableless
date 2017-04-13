---
title: Criando uma aplicação móvel com Ionic 2 e Angular 2 em dez passos
author: Carlos Cabral
type: post
date: 2016-11-04
url: /criando-uma-aplicacao-movel-com-ionic-2-e-angular-2-em-dez-passos/
categories:
  - AngularJS
  - Código
  - JavaScript
  - Mobile
tags:
  - android
  - angular2
  - angularjs
  - ionic
  - ionic2
  - ios
  - JavaScript
  - mobile
  - tutorial

---
## Introdução

À esta altura do campeonato é provável que você já tenha ouvido falar da nova versão deste famoso framework para criação de aplicações móveis híbridas. O **<a href="https://ionicframework.com/docs/v2/" target="_blank">Ionic 2</a>** acaba de chegar em seu _Release Candidate_ e, com ele, trás uma série de recursos e otimizações de código, além de um considerável ganho de performance! Muito desse mérito se deve ao **<a href="https://angular.io/" target="_blank">Angular</a>** (como é chamada a nova versão do framework, que deixa para trás o &#8220;JS&#8221; ao final do nome) que chega &#8211; finalmente &#8211; na sua versão estável, provando que não está para brincadeiras.

Depois de passar por várias mudanças e quebras de código à cada novo release, o **Ionic 2** agora atinge a maturidade e se torna um competidor ainda mais forte do modelo de desenvolvimento tradicional (nativo). No entanto, se você já está familiarizado com o **<a href="http://ionicframework.com/" target="_blank">Ionic 1</a>**, a mudança nos conceitos pode lhe soar um tanto quanto desagradáveis à primeira vista. Mas uma vez que você entende como as peças se encaixam, vai perceber que criar aplicações móveis com o framework tornou-se uma atividade ainda mais simples e recompensadora.

### O que tem de novo?

O Ionic foi desenvolvido com base no **<a href="https://angularjs.org/" target="_blank">AngularJS</a>**, um framework voltado para a criação de aplicações web modernas, construídas com base em uma página **HTML5** que atualiza seu conteúdo de maneira dinâmica (as famosas _Single Page Applications_ ou _SPAs_). Ao tirar proveito dessa arquitetura &#8211; e adicionar uma série de estilos que emulam o visual de aplicações nativas &#8211; o Ionic facilitou, em muito, a tarefa de construir um app híbrido, ou seja, aquele que executa tanto em smartphones **iOS** quando **Android**, otimizando o seu **<a href="https://en.wikipedia.org/wiki/Time_to_market" target="_blank">Tempo de Mercado</a>**.

Mesmo ainda sendo executado em uma **WebView** (browser interno dos smartphones), uma aplicação baseada no Ionic 2 é muito mais rápida, modular e escalável, se comparada com a primeira versão. Principalmente porque o framework segue os padrões web mais recentes, como a nova especificação **ES6** (ou ES2015), trazendo para o javaScript conceitos como **classes**, **módulos** e **arrow functions**. Além disso, temos também a presença do polêmico **<a href="https://www.typescriptlang.org/" target="_blank">TypeScript</a>** (opcional), que trás o poder da tipagem para o seu código, com o intuito de minimizar erros, simplificar a injeção de dependências, facilitar testes, e etc.

![Too much information - gif][1]

Mas embora tudo isso pareça um verdadeiro balaio de gato que funciona mais como repelente do que atrativo, não se deixe enganar: A versão 2 do Ionic dá um considerável salto de inovação em relação à sua versão original e abre caminho para <a href="https://ionicframework.com/docs/v2/resources/progressive-web-apps/" target="_blank">novas e interessantes tendências</a> que valem a pena serem exploradas!

## Mão na massa!

Para entender melhor como se constrói uma aplicação com o Ionic 2, vamos criar uma do zero 😀

A aplicação que iremos construir é um simples leitor de feeds baseado na API do **<a href="https://www.reddit.com/" target="_blank">Reddit</a>**, o poderoso canal agregador de notícias, onde membros da comunidade podem submeter conteúdos como links, textos, imagens, etc. O app será 100% funcional e poderá ser instalado no seu smartphone e, quem sabe, até mesmo evoluir com a inclusão de novas funcionalidades.

### Instalando o framework

Se você já tem o Ionic 1 instalado na sua máquina, basta digitar o seguinte comando no terminal:

`npm install -g ionic`

Esse comando atualiza o framework para trabalhar com o Ionic 2 sem afetar a instalação da versão 1.

Mas caso você seja marinheiro de primeira viagem, certifique-se que tenha o **<a href="https://nodejs.org/en/" target="_blank">Node.js</a>** instalado na sua máquina e, em seguida, digite no terminal:

`npm install -g ionic cordova`

> Lembre-se de que você também deve ter o SDK do Android e o Java instalados para fazer build para Android e/ou o Xcode para o build no iPhone:



  * <a href="https://ionicframework.com/docs/v2/resources/platform-setup/mac-setup.html" target="_blank">Guia de instalação para Mac</a>
  * <a href="https://ionicframework.com/docs/v2/resources/platform-setup/windows-setup.html" target="_blank">Guia de instalação para Windows</a>

Depois que a instalação for concluída, você pode verificar a versão do framework no terminal, digitando:

`ionic -v`

### Criando um novo projeto

O CLI (_Command Line Interface_) do Ionic vem com um monte de comandos úteis que nos ajudam na criação e na manutenção dos projetos. Para conferir a lista de comandos disponíveis, digite:

`ionic help`

Por enquanto o que nos interessa é o comando **start**. Digite o seguinte no terminal:

`ionic start MyReader blank --v2 --appname "Best Reader Ever" --id "com.tableless.myreader"`

O comando **start** oferece três tipos de templates com código boilerplate. São eles:

  * **sidemenu** &#8211; adiciona um menu lateral à aplicação (estilo de navegação <a href="https://material.google.com/patterns/navigation-drawer.html" target="_blank">padrão no Android</a>);
  * **tabs** &#8211; cria uma navegação baseada em guias (modelo de organização de conteúdo <a href="https://developer.apple.com/ios/human-interface-guidelines/ui-bars/tab-bars/" target="_blank">incentivado pelo iOS</a>);
  * **blank** &#8211; cria um projeto com boilerplate básico, sem nenhum template específico.

O comando que digitamos no terminal vai utilizar o template **blank**. Também passamos mais três parâmetros adicionais: **v2** que informa que queremos trabalhar com a versão 2 do Ionic, **appname**, que define um nome de projeto menos formal e **id**, que nos possibilita definir o package da aplicação.

Vamos agora acessar a pasta do nosso projeto, digitando:

`cd MyReader`

### Passo 1 &#8211; Conhecendo a arquitetura

Depois de tantas configurações e explicações iremos, enfim, para a parte divertida do processo!

Se você visitar a pasta do projeto dentro de **src/pages/**, vai notar a presença de uma outra pasta chamada **home**. Dentro dela há três arquivos:

  * home.html;
  * home.scss;
  * home.ts.

Essas pastas e arquivos foram criados como resultado do comando **start**. O Ionic é baseado no Angular que, por sua vez, considera que os principais componentes de uma aplicação devem ter escopos isolados. Portanto, cada &#8220;página&#8221; de um projeto tem seu próprio template visual (html), estilo (scss) e classe (ts). Perceba também que, por padrão, o Ionic utiliza **Sass** para a escrita de CSS e TypeScript para as classes, ao invés de JavaScript puro. Fique à vontade para vasculhar as pastas do projeto e entender como as informações são organizadas, uma vez que este tutorial não tem o propósito de explorar isso com detalhes.

Antes de modificar algo no projeto, vamos verificar o que já foi gerado de graça. Digite no terminal:

`ionic serve`

Este comando inicia um servidor local na nossa máquina e abre uma nova aba no browser com a aplicação no ar. Como o _LiveReload_ já vem habilitado por padrão, modificações que fizermos no código serão refletidas automaticamente no browser:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic-2-localhost-1.jpg" alt="Ionic 2 - Screenshot 1 localhost" />

Vamos ver isso acontecendo em tempo real. Abra o arquivo **home.html** e remova o código desnecessário até que ele fique assim:

<pre class="lang-html">&lt;ion-header&gt;
  &lt;ion-navbar&gt;
    &lt;ion-title&gt;My Feed Reader&lt;/ion-title&gt;
  &lt;/ion-navbar&gt;
&lt;/ion-header&gt;

&lt;ion-content&gt;

&lt;/ion-content&gt;</pre>

Confira a mudança ocorrendo automaticamente no browser:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic-2-localhost-2.jpg" alt="Ionic 2 - Screenshot 2 localhost" />

Agora vamos dar uma olhada no componente responsável por controlar nosso template. Abra o arquivo **home.ts**:

<pre class="lang-javascript">import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';

@Component({
   selector: 'page-home',
   templateUrl: 'home.html'
})
export class HomePage {
   constructor(public navCtrl: NavController) {}
}
</pre>

Perceba que o arquivo é composto por três blocos distintos, que eu chamo carinhosamente de os **3D**: **Declaration**, **Decorator** e **Definition**. A primeira parte é onde declaramos componentes externos ou bibliotecas que iremos utilizar em nosso projeto:

<pre class="lang-javascript">import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';
</pre>

O segundo bloco é composto por um **Decorator**. No Angular, todo componente tem um &#8220;decorador&#8221;, que é responsável por fornecer metadados ou informações sobre a classe. No nosso caso, o decorador está dizendo que as modificações no html serão feitas apenas no componente **page-home** e que este arquivo, ou seja, o template html que iremos utilizar, se chama **home.html**, veja:

<pre class="lang-javascript">@Component({
   selector: 'page-home',
   templateUrl: 'home.html'
})
</pre>

> Lembre-se que, por padrão, os Decorators ficam sempre em cima do bloco de definição da classe.



O seletor **page-home** será útil quando for necessário criar regras de estilo em CSS aplicadas apenas à ele.

E, por fim, temos nosso escopo de classe. Classes em qualquer linguagem de programação orientada à objeto servem para definir a estrutura e o comportamento de objetos. Por enquanto o que você precisa saber é que nossa classe tem apenas um construtor que recebe um objeto do tipo **NavController** por parâmetro. Nosso próximo passo será inserir novos atributos e métodos para definir melhor o seu comportamento:

<pre class="lang-javascript">export class HomePage {
  constructor(public navCtrl: NavController) {}
</pre>

### Passo 2 &#8211; Consumindo dados de uma API pública

Agora que você já sabe mais ou menos como as coisas funcionam, vamos fazer rapidamente uma requisição à uma API externa (Reddit) para exibir seu resultado em uma lista no nosso template.

#### 2.1 &#8211; Trabalhando com Observables

Inclua o seguinte código em **home.ts**:

<pre class="lang-javascript">import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';
import { Http } from '@angular/http';
import 'rxjs/add/operator/map';

@Component({
  selector: 'page-home',
  templateUrl: 'home.html'
})
export class HomePage {

  public feeds: Array&lt;string&gt;;
  private url: string = "https://www.reddit.com/new.json";  

  constructor(public navCtrl: NavController, public http: Http) {

    this.http.get(this.url).map(res =&gt; res.json())
      .subscribe(data =&gt; {
        this.feeds = data.data.children;
      }); 
  }

}
</pre>

_Caso queira entender melhor sobre os endpoints da API, dê uma olhada <a href="https://www.reddit.com/dev/api/" target="_blank">nesse link</a>._

O que fizemos acima foi importar o componente **Http** e injetá-lo no método construtor. Isso nos possibilita acessar sua instância através do objeto **this**. Note que também estamos importando o operador **map** da biblioteca **<a href="https://github.com/Reactive-Extensions/RxJS" target="_blank">rxjs</a>**. O rxjs é uma das extensões que compõe a **<a href="http://reactivex.io/" target="_blank">reactiveX</a>** (Reactive Extensions), uma biblioteca assíncrona que trabalha com o stream de dados no padrão **Observable**.

No objeto http estamos fazendo uma requisição do tipo **GET** à um endpoint que definimos na variável **url**, acima do método construtor. Note que, com o uso do TypeScript, podemos definir seu escopo (pública ou privada) e ainda definir o seu tipo (string, number, array&#8230;). Ponto para o TypeScript!

Em seguida, transformamos o resultado dessa requisição utilizando o operador map e o convertemos para JSON através do método **subscribe** (&#8220;similar&#8221; ao método **then** de uma Promise).

> É importante salientar que o map da biblioteca rxjs é utilizado exclusivamente para mapear um **array do tipo Observable** e não é o mesmo map que utilizamos em um array comum no JavaScript. Aprenda mais sobre requisições remotas com Observables <a href="https://angular.io/docs/ts/latest/guide/server-communication.html#!#rxjs" target="_blank">nesse link</a>.

&nbsp;

Por fim, incluímos o resultado da requisição (agora um objeto do tipo JSON) dentro da variável pública **feeds**, que aqui representa um array de strings. Seu escopo precisa ser público pois iremos acessar seu conteúdo no template.

#### 2.2 &#8211; Exibindo resultado para o usuário

Como você percebeu, dentro do nosso arquivo **home.ts** há uma referência ao template **home.html** dentro do bloco **@Component**. Esse template, na verdade, é aquilo que o usuário realmente vê na tela do seu smartphone, com base no que definimos dentro da nossa classe. Por enquanto ele não está exibindo nada. Modifique o conteúdo de **home.html** conforme abaixo:

<pre class="lang-html">&lt;ion-header&gt;
  &lt;ion-navbar&gt;
    &lt;ion-title&gt;My Feed Reader&lt;/ion-title&gt;
  &lt;/ion-navbar&gt;
&lt;/ion-header&gt;

&lt;ion-content&gt;
  &lt;ion-list&gt;
    &lt;ion-item *ngFor="let feed of feeds"&gt;
      {{feed.data.title}}
    &lt;/ion-item&gt;
  &lt;/ion-list&gt;
&lt;/ion-content&gt;
</pre>

O Ionic fornece uma grande variedade de componentes visuais _out of the box_ que nos permite construir uma interface praticamente idêntica à de uma aplicação nativa. Não só isso como também é capaz de adaptar o seu estilo visual de acordo com cada plataforma (algo que veremos em breve).

A tag **<ion-navbar>** representa a barra de navegação que fica no topo da tela. Essa barra geralmente comporta o título da aplicação (como visto na tag **<ion-title>**) mas também pode conter botões de ação e demais itens, caso necessário.

Já as informações dinâmicas sempre são inseridas dentro da tag **<ion-content>**, como acabamos de fazer ao inserir o componente **<ion-list>**.

> Não iremos nos aprofundar nos detalhes dos templates visuais fornecidos pelo Ionic. Você pode encontrar exemplos do markup de cada componente <a href="https://ionicframework.com/docs/v2/components" target="_blank">aqui</a>. O componente que estamos utilizando no exemplo acima é <a href="https://ionicframework.com/docs/v2/components/#lists" target="_blank">este</a>. Eu apenas copiei o markut e inseri aqui, alterando apenas aquilo que é necessário. Esta é, sem dúvida, uma das features mais importantes do framework, uma vez que ela acelera o processo de prototipação de um aplicativo.

&nbsp;

Observe o seguinte bloco de código:

<pre class="lang-html">&lt;ion-list&gt;
    &lt;ion-item *ngFor="let feed of feeds"&gt;
      {{feed.data.title}}
    &lt;/ion-item&gt;
  &lt;/ion-list&gt;
</pre>

Note o loop que estamos executando com a instrução ***ngFor**. Estamos acessando o conteúdo do array **feeds** e iterando sobre ele com uma variável local (**feed**) para popular nossa lista. Esta é uma conveniência fornecida pelo Angular conhecida como _Embedded templates_ ou diretivas html, que nos ajuda na renderização dos atributos disponíveis na classe associada. Observe agora o seguinte trecho:

<pre class="lang-html">{{feed.data.title}}</pre>

Ele representa o valor que será exibido em cada célula da lista, que, neste caso, representa o título do feed. Esta sintaxe entre chaves duplas é chamada de **Interpolação**.

Agora salve o arquivo e verifique o resultado no browser. É provável que você esteja vendo algo assim:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic-2-localhost-3.jpg" alt="Ionic 2 - Screenshot 3 localhost" />

Se você entendeu tudo que foi explicado até aqui, significa que você já domina boa parte dos principais conceitos não só do Ionic 2 como também do Angular 2. Parabéns!

Agora é o momento em que nos despedimos das explicações mais detalhadas e partimos para a ação. Vamos dar um tapinha no visual desse app e inserir alguns recursos extras que irão torná-lo ainda mais sexy 😉

### Passo 3 &#8211; Customizando o template

Nosso próximo passo será incluir mais informações nas células dessa lista, uma vez que apenas o título não é o suficiente para capturar a atenção do usuário.

#### 3.1 &#8211; Adicionando informações extras

Ainda em **home.html**, altere o conteúdo atual de dentro da tag **<ion-content>** para:

<pre class="lang-html"> &lt;ion-list&gt;
    &lt;ion-item *ngFor="let feed of feeds"&gt;
       &lt;ion-thumbnail item-left&gt;
          &lt;img [src]="feed.data.thumbnail"&gt;
       &lt;/ion-thumbnail&gt;
       &lt;h2&gt;{{feed.data.title}}&lt;/h2&gt;
       &lt;p&gt;{{feed.data.domain}}&lt;/p&gt;
    &lt;/ion-item&gt;
 &lt;/ion-list&gt;
</pre>

Salve o arquivo e visualize o resultado no browser:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic-2-localhost-4.jpg" alt="Ionic 2 - Screenshot 4 localhost" />

Agora estamos utilizando um novo template de lista, que comporta imagens. O Ionic já faz o serviço de ajustar os itens pra você contanto que indiquemos isso através dos atributos e classes que o framework nos oferece. Perceba, por exemplo, o atributo **item-left** presente dentro da tag **<ion-thumbnail>**. Altere seu nome para **item-right** e você verá que as imagens serão posicionadas à direita da célula. Tente também alterar a tag **<ion-thumbnail>** para **<ion-avatar>** e verá que as imagens ficarão menores e com bordas arredondadas. Muito conveniente!

Note que o atributo **src** da tag de imagem está envolto por colchetes. Essa sintaxe se chama _Property binding_ e é utilizada para atribuir uma propriedade da view ao valor de uma expressão. No entanto, a mesma sintaxe pode ser substituída por esta:

<pre class="lang-html">&lt;img src="{{ feed.data.thumbnail }}"&gt;
</pre>

Para fins didáticos iremos deixar a expressão com colchetes neste exemplo.

Perceba também que o título do feed agora aparece dentro da tag **h2** e um novo item foi inserido dentro de uma tag **p**. Você pode utilizar o _Chrome Developer Tools_ para inspecionar a conteúdo da listagem disponível no array inserindo a instrução `console.log(this.feed);` ao fim da requisição, dessa forma:

<pre class="lang-javascript">this.http.get(this.url).map(res =&gt; res.json())
    .subscribe(data =&gt; {
      this.feeds = data.data.children;
     // Exibindo conteúdo do array no console do browser
      console.log(this.feeds);
    }); 
</pre>

### Passo 4 &#8211; Fornecendo feedback ao cliente e capturando eventos

Embora nossa aplicação consiga requisitar dados externos com sucesso, não há nada que informe ao usuário sobre o status dessa ação. Ele pode aguardar poucos segundos como também pode esperar uma eternidade até que alguma coisa apareça na tela do celular, dependendo do tipo de conexão que esteja enfrentando.

#### 4.1 &#8211; Adicionando um Loading

Insira o seguinte conteúdo no arquivo **home.ts**:

<pre class="lang-javascript">import { Component } from '@angular/core';
import { NavController, LoadingController } from 'ionic-angular';
import { Http } from '@angular/http';
import 'rxjs/add/operator/map';

@Component({
  selector: 'page-home',
  templateUrl: 'home.html'
})
export class HomePage {

  public feeds: Array&lt;string&gt;;
  private url: string = "https://www.reddit.com/new.json";  

  constructor(public navCtrl: NavController, public http: Http, public loadingCtrl: LoadingController) {

    this.fetchContent();

  }

  fetchContent ():void {
    let loading = this.loadingCtrl.create({
      content: 'Fetching content...'
    });

    loading.present();

    this.http.get(this.url).map(res =&gt; res.json())
      .subscribe(data =&gt; {
        this.feeds = data.data.children;
        loading.dismiss();
      });  
  }
</pre>

Salve o arquivo e verifique imediatamente o resultado no browser:

![Ionic 2 - Screenshot 5 localhost][2]

O Loading é um ótimo componente para fornecer feedback visual para o usuário, indicando que alguma atividade está sendo executada em background. Nada mais é que uma caixa de diálogo que bloqueia qualquer atividade do usuário até que determinada ação seja concluída. A nossa caixa de diálogo inclui um spinner e um texto indicativo por padrão, mas todas essas opções podem ser customizadas para atender melhor a necessidade do seu app.

Incluir um Loading é extremamente simples: Primeiro nós importamos o componente **LoadingController** da biblioteca **ionic-angular** e injetamos o objeto no método construtor. Em seguida, inicializamos o Loading com uma mensagem de feedback e depois apresentamos ele através do método **present**. Depois nós retiramos o componente da tela caso tenhamos sucesso na requisição através do método **dismiss**. Simples!

Perceba também que, como boa prática, movemos a requisição da API para um método chamado **fetchContent** que é então chamado imediatamente no construtor. Outra novidade é a inclusão do tipo de retorno do método, tipado como **void**. Se você vem de linguagens como Java, sabe que esta é uma maneira de dizer que o método não retorna nada, apenas executa uma ação.

#### 4.2 &#8211; Eventos html

Antes de passarmos para a próxima etapa, vamos incluir um evento nas células. Faça a seguinte modificação em **home.html**:

<pre class="lang-html">&lt;ion-item *ngFor="let feed of feeds" (click)="itemSelected(feed)"&gt;
</pre>

Queremos executar alguma ação sempre que o usuário clicar/tocar em uma das células. Conseguimos isso fazendo o _binding_ do método **itemSelected** no evento html **click** e passando o feed como argumento. Essa sintaxe de incluir eventos html dentro de parênteses é chamado de _Event Binding_ no Angular.

Agora basta incluir o método dentro da classe:

<pre class="lang-javascript">itemSelected (feed):void {
    alert(feed.data.url);
  } 
</pre>

Salve o arquivo e clique em cima de alguma célula. A url do post será exibida em um alert!

### Passo 5 &#8211; Exibindo o conteúdo de uma url no browser

Agora que você já entendeu como capturar uma ação do usuário, vamos prosseguir com as funcionalidades do nosso app e fazer com que o post seja exibido no browser.

#### 5.1 &#8211; Instalando plugin InAppBrowser

Em uma nova aba do terminal, entre na pasta do projeto e digite o seguinte:

`ionic plugin add cordova-plugin-inappbrowser`

Este plugin nos possibilita abrir sites externos em um browser diretamente do app. Mas só será possível testar essa funcionalidade se você fizer o build para testar no emulador ou no seu próprio dispositivo. Para isso, digite a seguinte instrução no terminal caso você possua um iPhone:

`ionic platform add ios`

Ou, caso tenha um dispositivo Android:

`ionic platform add android`

Agora altere o parâmetro do método no arquivo **home.html** para enviar apenas a url como argumento:

<pre class="lang-html">&lt;ion-item *ngFor="let feed of feeds" (click)="itemSelected(feed.data.url)"&gt;
</pre>

E agora basta fazer as seguintes alterações em **home.ts**. Primeiro, importar a classe do plugin:

<pre class="lang-javascript">import { InAppBrowser } from 'ionic-native';
</pre>

Em seguida, faça a seguinte alteração no método:

<pre class="lang-javascript">itemSelected (url: string):void {
   let browser = new InAppBrowser(url, '_system');
 }
</pre>

Pronto! Agora só resta testar se a funcionalidade está sendo executada conforme desejado.

#### 5.2 &#8211; Executando testes nas plataformas

Para instalar o emulador do iOS e preparar o ambiente para testes no seu próprio iPhone, basta digitar no terminal:

`npm -g install ios-sim ios-deploy`.

Agora digite a instrução abaixo e, caso tudo tenha dado certo, é provável que você veja o aplicativo abrindo no seu emulador:

`ionic run ios`

Caso esteja com o celular conectado ao computador através da porta USB, o deploy será automaticamente executado no seu iPhone. Se mesmo assim você encontrar dificuldades, tente digitar:

`ionic run ios --device`

Para testar no Android, apenas digite:

`ionic run android`

Maiores detalhes sobre deploy e testes em ambas plataformas você encontra <a href="https://ionicframework.com/docs/v2/resources/developer-tips/" target="_blank">aqui</a>.

Caso você tenha conseguido testar com sucesso, deve ter percebido que, ao clicar em uma das células, há um certo delay entre o momento do clique e o carregamento da página. Para corrigir isso, apenas insira o conteúdo da célula dentro de um **botão** (button) com o atributo **ion-item**, dessa forma:

<pre class="lang-html"> &lt;button ion-item *ngFor="let feed of feeds" (click)="itemSelected(feed.data.url)"&gt;
    &lt;ion-thumbnail item-left&gt;
       &lt;img [src]="feed.data.thumbnail"&gt;
    &lt;/ion-thumbnail&gt;
    &lt;h2&gt;{{feed.data.title}}&lt;/h2&gt;
    &lt;p&gt;{{feed.data.domain}}&lt;/p&gt;
 &lt;/button&gt;
</pre>

Agora o delay não só é removido como é adicionado um overlay em tom mais escuro na célula quando a mesma é pressionada.

Tem mais uma coisa que está incomodando: Perceba que os posts sem imagens estão quebrando nosso layout e deixando a nossa lista com aspecto pouco profissional. Vamos mudar isso incluindo o seguinte trecho de código dentro do método **subscribe** de **fecthContent**:

<pre class="lang-javascript">this.feeds.forEach((e, i, a) =&gt; {
   if (!e.data.thumbnail || e.data.thumbnail.indexOf('b.thumbs.redditmedia.com') === -1 ) { 
      e.data.thumbnail = 'http://www.redditstatic.com/icon.png';
   }
 })
</pre>

Utilizamos o método **forEach** do JavaScript para iterar pelo array de feeds e verificar quais itens estão sem imagem. Em seguida, para estes itens, incluímos uma imagem padrão do próprio reddit, que está disponível em um link público e irá servir de placeholder.

Veja o resultado de todas estas modificações rodando em um device iOS:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic2-step5.gif" alt="Ionic 2 - InAppBrowser" />

### Passo 6 &#8211; Adicionando scroll infinito na célula

Nosso app está ficando bem legal mas ainda necessita de algumas modificações para ficar realmente atrativo. Uma delas é viabilizar alguma maneira de acessar os posts mais antigos, já que nosso app tem uma restrição de apenas 25 itens por request. Isto é muito ruim, pois o usuário fica limitado à visitar apenas estes itens.

Se você explorar a API do reddit vai perceber que ela nos fornece vários parâmetros do tipo GET para controlar filtros e paginações. Um deles é chamado _after_, que utiliza o o atributo _fullName_ (junção do tipo do post mais o seu ID) como identificador único e funciona como âncora para os demais posts.

Em outras palavras, uma requisição como esta:

`https://www.reddit.com/new.json?after=t3_57ct5z`

Pode ser lida como: &#8220;_Busque os novos posts que vem depois do post de nome t3_57ct5z_&#8221;

> Fique atento com a forma como você lê a instrução pois há uma pegadinha: **Depois** aqui se refere ao array de posts, ou seja, os posts mais velhos e não os mais recentes. Veremos como buscar os mais recentes na próxima etapa do app

&nbsp;

Agora que você já entendeu a mecânica, vamos começar inserindo o componente responsável por acionar o scroll infinito na nossa página. Insira a seguinte instrução em **home.html** imediatamente após o fim da tag **<ion-list>**:

<pre class="lang-html"> &lt;ion-infinite-scroll (ionInfinite)="doInfinite($event)"&gt;
    &lt;ion-infinite-scroll-content
       loadingText="Loading more data..."&gt;
    &lt;/ion-infinite-scroll-content&gt;
 &lt;/ion-infinite-scroll&gt; 
</pre>

E criamos o método correspondente em nossa classe:

<pre class="lang-javascript">doInfinite(infiniteScroll) {

    let paramsUrl = (this.feeds.length &gt; 0) ? this.feeds[this.feeds.length - 1].data.name : "";

      this.http.get(this.olderPosts + paramsUrl).map(res =&gt; res.json())
        .subscribe(data =&gt; {
        
          this.feeds = this.feeds.concat(data.data.children);
          
          this.feeds.forEach((e, i, a) =&gt; {
            if (!e.data.thumbnail || e.data.thumbnail.indexOf('b.thumbs.redditmedia.com') === -1 ) {  
              e.data.thumbnail = 'http://www.redditstatic.com/icon.png';
            }
          })
          infiniteScroll.complete();
        }); 
  }  
</pre>

Por fim, inserimos a url da requisição:

<pre class="lang-javascript">private olderPosts: string = "https://www.reddit.com/new.json?after=";
</pre>

O novo método é bem parecido com o **fetchContent**, com a diferença de que criamos uma variável local que guarda o valor do atributo **nome** do último item do array de feeds e insere este valor no fim da url. Em seguida, pegamos o array resultante da requisição e adicionamos no fim do array original através do método **concat** do JavaScript. Note também que utilizamos o método **complete** do componente, indicando que o mesmo deve ser removido da view.

O resultado você confere abaixo:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic2-step6.gif" alt="Ionic 2 - Infinite Scroll" />

E, com isto, incluímos uma funcionalidade extremamente importante em aplicações móveis: A habilidade de adicionar itens em uma lista por demanda, algo que enriquece em muito a experiência do usuário. Se você estava esperando instruções muito complexas, sinto lhe desapontar!

### Passo 7 &#8211; Atualizando a lista com pull-to-refresh

Da mesma forma que adicionamos uma funcionalidade para carregar posts mais antigos sempre que chegarmos ao fim da nossa lista, precisamos agora viabilizar uma maneira de atualiza-la com os posts mais recentes. Uma excelente maneira de fazer isso é incluindo o componente **Refresher** na nossa aplicação.

O Refresher é um componente que adiciona o recurso de **pull-to-refresh** à nossa lista. O pull-to-refresh consiste em manter o dedo pressionado no topo de uma lista e arrastá-la até uma determinada posição até que um evento seja disparado. No nosso caso, utilizaremos esse evento para inserir os posts mais recentes no início do array, ao contrário do que fizemos com o componente InfiniteScroll.

Sem mais delongas, vamos começar inserindo o markup do componente antes da tag **<ion-list>** no arquivo **home.html**:

<pre class="lang-html"> &lt;ion-refresher (ionRefresh)="doRefresh($event)"&gt;
    &lt;ion-refresher-content
       pullingIcon="arrow-dropdown"
       pullingText="Pull to refresh"
       refreshingSpinner="circles"
       refreshingText="Refreshing..."&gt;
    &lt;/ion-refresher-content&gt;
 &lt;/ion-refresher&gt; 
</pre>

Diferentemente do InfiniteScroll, desta vez eu incluí alguns parâmetros adicionais, como os textos de início e fim do evento, o formato padrão do spinner, o ícone da seta, etc.

A url da requisição também precisa ser diferente, uma vez que iremos buscar os itens mais novos. Utilizaremos então o parâmetro _before_ oferecido pelo Reddit, fazendo com que a nossa nova url fique assim:

<pre class="lang-javascript">private newerPosts: string = "https://www.reddit.com/new.json?before=";
</pre>

Por fim, inserimos o método na classe:

<pre class="lang-javascript">doRefresh(refresher) {

    let paramsUrl = this.feeds[0].data.name;

    this.http.get(this.newerPosts + paramsUrl).map(res =&gt; res.json())
      .subscribe(data =&gt; {
      
        this.feeds = data.data.children.concat(this.feeds);
        
        this.feeds.forEach((e, i, a) =&gt; {
          if (!e.data.thumbnail || e.data.thumbnail.indexOf('b.thumbs.redditmedia.com') === -1 ) {  
            e.data.thumbnail = 'http://www.redditstatic.com/icon.png';
          }
        })
        refresher.complete();
      });
  } 

</pre>

Perceba como o método é similar àquele que escrevemos para o scroll infinito. A única diferença está na variável de parâmetro (que agora guarda o nome do primeiro item da lista como referência) e a maneira como concatenamos o array de feeds, inserindo os novos dados no início da lista e não no fim. Observe também a instrução **refresher.complete**, que informa que operação foi concluída e que o componente pode ser removido da view.

Nossa aplicação agora utiliza o refresher para atualizar a lista com os novos posts, veja:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic2-step7.gif" alt="Ionic 2 - Refresher" />

### Passo 8 &#8211; Filtrando a lista com uma Action Sheet

Agora que a nossa lista tem potencial para aumentar cada vez mais de tamanho, seria interessante termos uma opção de filtrar posts pertencentes à determinadas categorias. Podemos fazer isso facilmente com uma **Action Sheet**.

No arquivo **home.html** vamos incluir um botão do lado direito da nossa AppBar/NavBar que será responsável por disparar o método:

<pre class="lang-html">&lt;ion-header&gt;
   &lt;ion-navbar&gt;
       &lt;ion-title&gt;My Feed Reader&lt;/ion-title&gt;
       &lt;ion-buttons end&gt;
          &lt;button ion-button icon-only (click)="showFilters()"&gt;
              &lt;ion-icon name="funnel"&gt;&lt;/ion-icon&gt;
          &lt;/button&gt;
       &lt;/ion-buttons&gt; 
   &lt;/ion-navbar&gt;
&lt;/ion-header&gt;
</pre>

Observe o atributo **end** na tag **<ion-buttons>**, indicando que o botão deve ser posicionado à direita, ou seja, no fim da barra de navegação. O atributo **start** posicionaria o botão à esquerda. O **<ion-buttons>** funciona como um container de botões. No nosso caso, só precisamos de um que será representado por um ícone (por isso o atributo **icon-only**). Fizemos o binding do método **showFilters** no evento **click** e escolhemos o ícone de nome **funnel** para representar o filtro.

> Os ícones no Ionic são uma implementação própria do que chamamos de **icon fonts**, ou seja, fontes que contém símbolos ao invés de texto ou números e que podem ser estilizados utilizando CSS. Utilizar esse tipo de fonte é conveniente pois reduz a necessidade de imagens, o que torna nosso aplicativo ligeiramente mais rápido e menos pesado. Para ter acesso à lista de ícones do Ionic 2, dê uma olhada <a href="https://ionicframework.com/docs/v2/ionicons/" target="_blank">aqui</a>.

&nbsp;

Antes de incluir nosso método, precisamos de mais duas variáveis. Uma que será responsável por guardar a versão íntegra do nosso array de feeds (sem nenhum filtro) e uma outra que será um booleano, com a função de indicar se há ou não um filtro ativo:

<pre class="lang-javascript">public noFilter: Array&lt;any&gt;;
 public hasFilter: boolean = false;
</pre>

Com isso podemos incluir as seguintes instruções no final do método **subscribe** das funções **doRefresh** e **doInfinite**, com a finalidade de remover qualquer filtro ativo:

<pre class="lang-javascript">this.noFilter = this.feeds;
 this.hasFilter = false;
</pre>

Por fim, vamos agora incluir o método **showFilters** na classe:

<pre class="lang-javascript">showFilters() :void {

    let actionSheet = this.actionSheetCtrl.create({
      title: 'Filter options:',
      buttons: [
        {
          text: 'Music',
          handler: () =&gt; {
            this.feeds = this.noFilter.filter((item) =&gt; item.data.subreddit.toLowerCase() === "music");
            this.hasFilter = true;
          }
        },
        {
          text: 'Movies',
          handler: () =&gt; {
            this.feeds = this.noFilter.filter((item) =&gt; item.data.subreddit.toLowerCase() === "movies");
            this.hasFilter = true;
          }
        },        
        {
          text: 'Cancel',
          role: 'cancel',
          handler: () =&gt; {
            this.feeds = this.noFilter;
            this.hasFilter = false;
          }
        }
      ]
    });

    actionSheet.present();

  }  
</pre>

Primeiramente inicializamos o componente com a função **create** em uma variável local. Este componente recebe um título e um array de botões onde cada botão tem, obrigatoriamente, um texto indicativo e um handler que dispara o evento correspondente. Estes botões representam as opções que serão apresentadas para o usuário na tela. O código do filtro é autoexplicativo.

O último botão tem a função de cancelar a operação e remover qualquer filtro que esteja ativo. Perceba que este botão tem uma propriedade **role** com o valor de **cancel**, indicando que adota o comportamento padrão da plataforma e sempre estará posicionado como última opção da lista. Vale ressaltar que se o usuário clicar fora da Action Sheet, ou seja, no overlay da camada de fundo, a ação será interpretada como um cancelamento (o mesmo comportamento do botão com a role &#8220;cancel&#8221;).

Em seguida adicionamos o método **actionSheet.present** para que o componente seja apresentado na tela.

Por enquanto só estamos filtrando os subreddits com as categorias música ou filmes, mas nada nos impede de inserir mais opções de filtro no componente. O código final da nossa classe fica assim:

<pre class="lang-javascript">import { Component } from '@angular/core';
import { NavController, LoadingController, ActionSheetController } from 'ionic-angular';
import { Http } from '@angular/http';
import 'rxjs/add/operator/map';
import { InAppBrowser } from 'ionic-native';

@Component({
  selector: 'page-home',
  templateUrl: 'home.html'
})
export class HomePage {

  public feeds: Array&lt;any&gt;;
  private url: string = "https://www.reddit.com/new.json";
  private newerPosts: string = "https://www.reddit.com/new.json?before=";  
  private olderPosts: string = "https://www.reddit.com/new.json?after=";

  public hasFilter: boolean = false;
  public noFilter: Array&lt;any&gt;;

  constructor(public navCtrl: NavController, public http: Http, 
       public loadingCtrl: LoadingController, public actionSheetCtrl: ActionSheetController) {

    this.fetchContent();

  }

  fetchContent ():void {
    let loading = this.loadingCtrl.create({
      content: 'Fetching content...'
    });

    loading.present();

    this.http.get(this.url).map(res =&gt; res.json())
      .subscribe(data =&gt; {
        this.feeds = data.data.children;

        this.feeds.forEach((e, i, a) =&gt; {
          if (!e.data.thumbnail || e.data.thumbnail.indexOf('b.thumbs.redditmedia.com') === -1 ) {  
            e.data.thumbnail = 'http://www.redditstatic.com/icon.png';
          }
        })

        this.noFilter = this.feeds;  

        loading.dismiss();
      });  
  }

  doRefresh(refresher) {

    let paramsUrl = this.feeds[0].data.name;

    this.http.get(this.newerPosts + paramsUrl).map(res =&gt; res.json())
      .subscribe(data =&gt; {
      
        this.feeds = data.data.children.concat(this.feeds);
        
        this.feeds.forEach((e, i, a) =&gt; {
          if (!e.data.thumbnail || e.data.thumbnail.indexOf('b.thumbs.redditmedia.com') === -1 ) {  
            e.data.thumbnail = 'http://www.redditstatic.com/icon.png';
          }
        })

        this.noFilter = this.feeds;
        this.hasFilter = false;

        refresher.complete();
      });
  }  

  doInfinite(infiniteScroll) {

    let paramsUrl = (this.feeds.length &gt; 0) ? this.feeds[this.feeds.length - 1].data.name : "";

      this.http.get(this.olderPosts + paramsUrl).map(res =&gt; res.json())
        .subscribe(data =&gt; {
        
          this.feeds = this.feeds.concat(data.data.children);
          
          this.feeds.forEach((e, i, a) =&gt; {
            if (!e.data.thumbnail || e.data.thumbnail.indexOf('b.thumbs.redditmedia.com') === -1 ) {  
              e.data.thumbnail = 'http://www.redditstatic.com/icon.png';
            }
          })

          this.noFilter = this.feeds;
          this.hasFilter = false;          
          
          infiniteScroll.complete();
        }); 
  }   

  itemSelected (url: string):void {
    let browser = new InAppBrowser(url, '_system');
  } 
  
  showFilters() :void {

    let actionSheet = this.actionSheetCtrl.create({
      title: 'Filter options:',
      buttons: [
        {
          text: 'Music',
          handler: () =&gt; {
            this.feeds = this.noFilter.filter((item) =&gt; item.data.subreddit.toLowerCase() === "music");
            this.hasFilter = true;
          }
        },
        {
          text: 'Movies',
          handler: () =&gt; {
            this.feeds = this.noFilter.filter((item) =&gt; item.data.subreddit.toLowerCase() === "movies");
            this.hasFilter = true;
          }
        },
        {
          text: 'Games',
          handler: () =&gt; {
            this.feeds = this.noFilter.filter((item) =&gt; item.data.subreddit.toLowerCase() === "gaming");
            this.hasFilter = true;
          }
        },
        {
          text: 'Pictures',
          handler: () =&gt; {
            this.feeds = this.noFilter.filter((item) =&gt; item.data.subreddit.toLowerCase() === "pics");
            this.hasFilter = true;
          }
        },                
        {
          text: 'Ask Reddit',
          handler: () =&gt; {
            this.feeds = this.noFilter.filter((item) =&gt; item.data.subreddit.toLowerCase() === "askreddit");
            this.hasFilter = true;
          }
        },        
        {
          text: 'Cancel',
          role: 'cancel',
          handler: () =&gt; {
            this.feeds = this.noFilter;
            this.hasFilter = false;
          }
        }
      ]
    });

    actionSheet.present();

  }        

}

</pre>

Por questões de bom senso, seria interessante indicar ao usuário quando um filtro está ou não ativo alterando a cor do ícone do funil. Podemos fazer isso utilizando o conceito de _Property binding_ explicado mais acima, com a diferença de que agora a propriedade será atribuída baseada em uma condição.

insira o seguinte código na tag **<ion-icon>** em **home.html**:

<pre class="lang-html">&lt;ion-icon name="funnel" [style.color]="hasFilter ? 'orange' : 'inherit'"&gt;&lt;/ion-icon&gt;
</pre>

O resultado pode ser visto abaixo:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic2-step8.gif" alt="Ionic 2 - Action Sheet" />

### Passo 9 &#8211; Adicionando um provider e uma barra de busca

Apesar de termos avançado com sucesso até aqui, tenho certeza de que a quantidade de código repetitivo presente em nossa classe deve ter te causado um certo incômodo. Podemos muito bem mover a responsabilidade de conexão com a API para um outro serviço externo, no intuito de evitar o <a href="https://en.wikipedia.org/wiki/Don%27t_repeat_yourself" target="_blank">DRY</a> e a propagação de <a href="https://en.wikipedia.org/wiki/Code_smell" target="_blank">code smell</a>.

#### 9.1 &#8211; Criando um Injectable

O Angular nos permite criar uma classe com a anotação **@Injectable** para estes cenários. Esse tipo de classe também são conhecidos como **Providers** e podem tanto ser criados &#8220;na mão&#8221; quanto com a ajuda do CLI. Digite no terminal:

`ionic g provider RedditService`

Esse código cria uma pasta **providers** no nosso projeto com um arquivo de nome **reddit-service.ts**, onde o Ionic insere alguns códigos de boilerplate para facilitar nossa vida. Altere seu conteúdo conforme abaixo:

<pre class="lang-javascript">import { Injectable } from '@angular/core';
import { Http } from '@angular/http';
import 'rxjs/add/operator/map';

@Injectable()
export class RedditService {

  private feeds: Array&lt;any&gt;;

  constructor(private http: Http) {}

  fetchData(url: string): Promise&lt;any&gt; {
    
    return new Promise(resolve =&gt; {

      this.http.get(url).map(res =&gt; res.json())
        .subscribe(data =&gt; {
          this.feeds = data.data.children;
          
          this.feeds.forEach((e, i, a) =&gt; {
            if (!e.data.thumbnail || e.data.thumbnail.indexOf('b.thumbs.redditmedia.com') === -1 ) {  
              e.data.thumbnail = 'http://www.redditstatic.com/icon.png';
            }
          })
          resolve(this.feeds);
        }, err =&gt; console.log(err));          
    });
  }
}
</pre>

Replicamos boa parte do código presente no método **fetchContent** da classe **home.ts** aqui no nosso método **fetchData**, com algumas diferenças. A primeira delas é a já citada anotação **@Injectable()** presente antes do nome da classe, o que nos permite mover a definição do serviço para o construtor de **home.ts** dessa forma:

<pre class="lang-javascript">constructor(public redditService: RedditService) {}
</pre>

Isso evita que tenhamos de instanciar o serviço utilizando **new**. Clique <a href="https://en.wikipedia.org/wiki/Dependency_injection" target="_blank">aqui</a> para saber mais sobre **Injeção de Dependência**.

Outra mudança importante é que, por conveniência, a assinatura do método retorna uma **Promise** do tipo **any** (para evitar que tenhamos qualquer erro em tempo de compilação) ao invés de um **Observable**.

Por fim, para utilizar este serviço em nossa classe **home.ts** precisamos incluí-lo no arquivo **app.module.ts**, dentro da pasta **src/app**. Este arquivo faz uso da anotação **@NgModule**, onde todas as dependências da aplicação devem ser declaradas previamente:

<pre class="lang-javascript">import { NgModule } from '@angular/core';
import { IonicApp, IonicModule } from 'ionic-angular';
import { MyApp } from './app.component';
import { HomePage } from '../pages/home/home';
//indicamos o source path do arquivo:
import { RedditService } from '../providers/reddit-service';

@NgModule({
  declarations: [
    MyApp,
    HomePage
  ],
  imports: [
    IonicModule.forRoot(MyApp)
  ],
  bootstrap: [IonicApp],
  entryComponents: [
    MyApp,
    HomePage
  ],
//declaramos o nome do nosso provider:
  providers: [RedditService]
})
export class AppModule {}
</pre>

Com isso é possível escrever os métodos da nossa classe **home.ts** da seguinte maneira:

<pre class="lang-javascript">this.redditService.fetchData(this.url).then(data =&gt; {
     this.feeds = data;
     this.noFilter = this.feeds;
     loading.dismiss();
 })
</pre>

Repare que além de muito mais simples, agora utilizamos o método **then** ao invés do **subscribe** para recuperar os dados do serviço e preencher nosso array.

#### 9.2 &#8211; Adicionando uma SearchBar

Para aplicativos que utilizam listas e exibem conteúdo sob demanda é uma boa prática adicionar algum recurso de busca para que o usuário procure informações com base em uma palavra específica ou sequência de caracteres. Para tal, o Ionic fornece um componente chamado **SearchBar**.

Para evitar conflitos com as ações da nossa lista, escolhi inserir o componente diretamente na AppBar/NavBar da aplicação. Para tal, insira o seguinte bloco de código dentro da tag **<ion-title>** em **home.html**:

<pre class="lang-html"> &lt;ion-searchbar 
    [(ngModel)]="searchTerm"
    (ionInput)="filterItems()" 
    placeholder="Type here..." &gt;
 &lt;/ion-searchbar&gt;
</pre>

Perceba que a junção das sintaxes de _Event binding_ e _Input binding_ do **ngModel** nos permite replicar o tão famoso recurso de _Two-way data binding_ no Angular 2.

Agora inclua o seguinte método em **home.ts**:

<pre class="lang-javascript">filterItems() {
    this.hasFilter = false;
    this.feeds = this.noFilter.filter((item) =&gt; {
        return item.data.title.toLowerCase().indexOf(this.searchTerm.toLowerCase()) &gt; -1;
    });
  }
</pre>

Veja o resultado rodando em um iPhone:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic2-step9.gif" alt="Ionic 2 - SearchBar" />

Antes de concluir eu gostaria de mostrar um recurso fornecido pelo framework que nos permite testar o comportamento e visual da nossa aplicação em diferentes plataformas chamado **Ionic Lab**. Caso ainda esteja com o servidor ativo, basta inserir **/ionic-lab** após o número da porta na url ou digitar `ionic serve --lab` no terminal. O resultado é o seguinte:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic-2-ionic-lab.jpg" alt="Ionic 2 - Ionic Lab" />

Na imagem acima você consegue visualizar o nosso aplicativo no **iOS**, **Android** e **Windows Phone**! O Ionic não apenas executa o build da aplicação com uma única base de código para dispositivos diferentes como também se adapta ao comportamento e estilo visual de cada um, numa tentativa de fazer com que o usuário sempre tenha uma experiência condizente com a plataforma que utiliza. Perceba, por exemplo, como o spinner, a barra de busca, os ícones e estilo da lista são diferentes entre as plataformas. No caso do iOS, são incluídos até mesmo as setas na lateral direita da célula, o que é comum na plataforma. Além de tudo isso, poder testar aplicativos dessa maneira e ainda tirar proveito do recurso de _LiveReload_ enquanto você está programando é algo realmente especial.

Estamos chegando ao fim da criação do nosso aplicativo. Vimos que, apenas com pequenos ajustes, foi possível obter um código mais modular e ainda incluir o componente **SearchBar** com o estilo visual adequado para cada plataforma. Tudo isso de maneira simples e rápida, graças ao casamento perfeito entre o **Angular** e os componentes estilizados fornecido pelo **Ionic**.

### Passo 10 &#8211; Melhorando a experiência do usuário

Mesmo com todos os recursos que o Ionic 2 nos oferece é sempre importante garantir a melhor experiência possível para o usuário fazendo otimizações gerais, como customização de UI, ajustes no comportamento de componentes, ganho de performance, etc. Essa última etapa será dedicada à este propósito.

#### 10.1 &#8211; Controlando o scroll

Notei alguns problemas ao utilizar a Action Sheet para filtrar a lista quando o scroll está numa posição muito abaixo, pois a ação de carregar posts antigos pode ser disparada indevidamente. Podemos evitar isso fazendo a lista rolar para o topo antes de executar qualquer filtro. Mas como controlar isso programaticamente?

O componente **Content** (que gere a tag **<ion-content>** do nosso template html) disponibiliza um método de controle do scroll chamado **scrollToTop**. Podemos inserir o código no início do método **showFilters** da Action Sheet dessa forma:

<pre class="lang-javascript">this.content.scrollToTop();
</pre>

Antes precisamos obter uma referência à este componente utilizando a anotação **@ViewChild** da biblioteca **@angular/core** (algo similar à maneira como protocolos funcionam no iOS):

<pre class="lang-javascript">@ViewChild(Content) content: Content;
</pre>

Agora a lista vai rolar para o topo sempre que acionarmos a Action Sheet!

#### 10.2 &#8211; Melhorando a busca com Observables

Apesar de termos nossa barra de buscas funcionando perfeitamente, a cada caractere digitado estamos emitindo uma nova requisição, o que é desnecessário. Mas há uma forma elegante de lidar com isso utilizando Observables, uma vez que o evento só será disparado quando uma requisição for considerada válida.

O que queremos fazer é monitorar o componente de duas maneiras: A primeira é oferecendo um tempo maior para que o usuário conclua a digitação da palavra que está buscando através do método **debounceTime** e a segunda é utilizando o método **distinctUntilChanged** que irá comparar a palavra (ou a sequência de caracteres) digitada com a última que foi procurada, evitando que uma nova requisição seja emitida para um resultado que já se encontra na tela.

Iremos utilizar o **FormControl** de **@angular/forms** que irá conectar uma variável da classe ao input presente no nosso html (similar à maneira como o _Two way binding_ funciona).

Inclua as seguintes instruções no componente **<ion-searchbar>** em **home.html**:

<pre class="lang-html"> &lt;ion-searchbar 
    [(ngModel)]="searchTerm"
    [formControl]="searchTermControl" 
    [showCancelButton]=true
    (ionInput)="filterItems()" 
    placeholder="Type here..." &gt;
 &lt;/ion-searchbar&gt;
</pre>

Note que além do **formControl** também atribuímos o valor **true** à propriedade **showCancelButton**, que irá apresentar um botão para cancelar a busca e retirar o teclado digital da tela.

E a seguinte instrução que irá controlar quando devemos disparar a busca:

<pre class="lang-javascript">this.searchTermControl = new FormControl();
  this.searchTermControl.valueChanges.debounceTime(1000).distinctUntilChanged().subscribe(search =&gt; {
    if (search !== '' && search) {
      this.filterItems();
    }
  })  
</pre>

E com isso o componente se torna mais coerente com a expectativa do usuário, que irá perceber um ganho de performance ao filtrar resultados em uma lista com muitas células.

#### 10.3 &#8211; Ajustando o visual dos componentes com CSS

Nosso aplicativo agora depende de algumas mudanças visuais para corrigir alguns pequenos detalhes. O primeiro deles é referente ao Android. O Ionic 2, ao rodar em um dispositivo Android, oferece automaticamente suporte ao **<a href="https://material.google.com/" target="_blank">Material Design</a>** do **Google** (uma linguagem visual que sintetiza princípios clássicos daquilo que considera o &#8220;bom design&#8221;). Em resumo, o Material Design se preocupa em criar uma experiência unificada de layout entre as plataformas que rodam o sistema operacional do Android. <a href="https://material.google.com/#introduction-principles" target="_blank">Aqui</a> você pode conhecer melhor sobre seus princípios fundamentais.

Um dos pontos de atenção é a maneira como os textos devem ser apresentados ao usuário. O Material Design trabalha com a noção de hierarquia baseada em tons e opacidade. Em outras palavras, textos primários (que representam títulos e informações de destaque) recebem 87% de opacidade enquanto subtítulos recebem 54%. Veja abaixo:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic-2-material-design-spec.jpg" alt="Ionic 2 - Material Design Spec" />

Se você for inspecionar as cores presentes nos textos das células (utilize o _Devtools_ para tal) vai notar que elas não seguem este ponto da especificação da linguagem. O texto principal, por exemplo, utiliza preto puro e é sempre bom (fica aqui a dica) <a href="https://ianstormtaylor.com/design-tip-never-use-black" target="_blank">evitar</a> preto puro em seus designs sempre que possível.

Diferentemente do Android, a preocupação do iOS está voltada para o conteúdo, por isso não existe nenhuma linguagem tão restritiva quanto o Material Design na plataforma. No entanto, irei replicar a mudança visual que faremos para o Android também no iOS, tornando nossos textos ainda mais agradáveis para leitura.

Em **home.scss** inclua o seguinte código:

<pre class="lang-css">// iOS & Android only
  .item-md, .item-ios {
      h2 {
          color: rgba($color: #000, $alpha: .87);
      }
      p {
          color: rgba($color: #000, $alpha: .54);
      }
  }
</pre>

Repare que podemos fazer o nesting dos elementos por estar utilizando **Sass**. Também perceba que aplicamos a alteração apenas para as plataformas Android e iOS mas não para Windows Phone. As classes você pode obter facilmente ao inspecionar o DOM no console do browser.

Outro problema aparente são os títulos dos posts que somem ao atingir a borda da célula. Precisamos incluir uma quebra de linha para que eles sejam apresentados por completo. Dessa vez iremos aplicar a alteração às três plataformas:

<pre class="lang-css">// iOS, Android & WP
  .item-md, .item-ios, .item-wp {
      h2, p {
          white-space: normal;
      }
  }
</pre>

Por fim, gostaria de melhorar a maneira como a barra de busca se apresenta na versão iOS. Ela está pequena e diminui ainda mais de tamanho quando o botão de cancelar está ativo. Também seria interessante escurecer um pouco mais a opacidade do background para lhe conferir maior destaque:

Inclua o seguinte código (desta vez aplicado apenas para o iOS):

<pre class="lang-css">// iOS only
  .toolbar-ios { 
      ion-title {
          padding: 0 90px 0 1px;  
      } 
      .searchbar-ios .searchbar-input {
          background: rgba($color: #000, $alpha: 0.12);            
      }
  }
</pre>

> Caso prefira, você também pode alterar o valor das variáveis Sass do Ionic. <a href="https://ionicframework.com/docs/v2/theming/overriding-ionic-variables/" target="_blank">Neste link</a> há uma lista de todas elas.



#### 10.4 &#8211; Ajustes finais no html

Vamos iniciar modificando a cor da NavBar. Inclua o seguinte atributo na tag **<ion-navbar>** em **home.html**:

<pre class="lang-html">&lt;ion-navbar color="secondary"&gt;
</pre>

Como estamos utilizando **Sass**, fazemos uma referência à variável **secondary** do array **colors** que está listado no arquivo **src/theme/variable.scss**. Isso significa que você pode alterar o valor da cor na variável ao invés de escrever diretamente no template html.

Agora eu gostaria de inserir um ícone na frente do meu endereço de domínio (que representa meu subtítulo na lista) sempre que a categoria estiver relacionada com alguma das listadas na nossa Action Sheet. Eu posso controlar esse comportamento utilizando a diretiva de html do Angular chamada **ngSwitch**.

Substitua esta linha:

<pre class="lang-html">&lt;p&gt;{{feed.data.domain}}&lt;/p&gt;
</pre>

Por esta instrução:

<pre class="lang-html"> &lt;div [ngSwitch]=feed.data.subreddit.toLowerCase()&gt;
   &lt;p *ngSwitchCase="'askreddit'"&gt;&lt;ion-icon name="help-circle"&gt;&lt;/ion-icon&gt;&nbsp;{{feed.data.domain}}&lt;/p&gt;
   &lt;p *ngSwitchCase="'gaming'"&gt;&lt;ion-icon name="logo-playstation"&gt;&lt;/ion-icon&gt;&nbsp;{{feed.data.domain}}&lt;/p&gt;
   &lt;p *ngSwitchCase="'music'"&gt;&lt;ion-icon name="musical-notes"&gt;&lt;/ion-icon&gt;&nbsp;{{feed.data.domain}}&lt;/p&gt;
   &lt;p *ngSwitchCase="'movies'"&gt;&lt;ion-icon name="film"&gt;&lt;/ion-icon&gt;&nbsp;{{feed.data.domain}}&lt;/p&gt;
   &lt;p *ngSwitchCase="'pics'"&gt;&lt;ion-icon name="image"&gt;&lt;/ion-icon&gt;&nbsp;{{feed.data.domain}}&lt;/p&gt;
   &lt;p *ngSwitchDefault&gt;{{feed.data.domain}}&lt;/p&gt;
 &lt;/div&gt;
</pre>

Observe que os ícones apenas serão aplicados no caso de coincidirem com os argumentos. Em caso contrário, será exibido apenas o texto sem nenhum ícone, conforme descrito na cláusula **ngSwitchDefault**.

Outra coisa que me incomoda é o componente **Refresher** ser acionado com muito pouco esforço. Eu sinto que o usuário poderia puxar um pouco mais a lista para evitar que o evento seja disparado com muita facilidade. Podemos modificar isso alterando a propriedade **pullMin**, veja:

<pre class="lang-html">&lt;ion-refresher (ionRefresh)="doRefresh($event)" [pullMin]=90&gt;
</pre>

Alteramos para 90 dpi a distância mínima que o usuário deve alcançar para disparar o evento. A distância padrão é 60.

Seria também interessante alterar a cor da barra de status da aplicação para a cor branca, já que o fundo da NavBar agora está colorido. Como a barra de status é um componente nativo, para modificá-lo precisaremos instalar um plugin do **Cordova**. Verifique se ele já está instalado procurando no arquivo **package.json** por &#8220;**cordova-plugin-statusbar**&#8220;. Caso contrário, digite no terminal:

`ionic plugin add cordova-plugin-statusbar`

E insira a seguinte instrução dentro do método construtor do arquivo **src/app/app.component.ts**:

<pre class="lang-javascript">StatusBar.backgroundColorByHexString('#ffffff');
</pre>

E agora veja como ficou o visual final da nossa aplicação rodando em um iPhone 6:

<img style="border: 1px solid #666" src="http://tableless.com.br/uploads/2016/10/ionic2-step10.gif" alt="Ionic 2 - UX enhancement" />

#### 10.5 &#8211; Aumentando o desempenho

Se você pensa em evoluir de um protótipo para um aplicativo real, se preocupar com o seu desempenho é tarefa essencial. Abaixo eu listo algumas sugestões que podem ajudar:

  * **WKWebView** &#8211; Recentemente o time do Ionic tornou possível rodar os aplicativos iOS utilizando o browser WKWebView (evolução do antigo browser UIWebView). Este novo engine oferece aos aplicativos iOS um ganho de performance muito superior ao antigo browser, principalmente na experiência com listas. Para instalar o plugin, digite: `ionic plugin add https://github.com/driftyco/cordova-plugin-wkwebview-engine.git --save`
  * **Crosswalk** &#8211; Como o Android tem algumas limitações de desempenho que podem ser encontradas em alguns devices (principalmente nos antigos devido às várias versões de sistema existentes), fica difícil garantir que o aplicativo irá rodar exatamente da maneira como queremos. O Crosswalk é um browser moderno que é empacotado junto com o seu app no momento que você faz o build para Android. Isso significa que, independente do device do usuário, ele estará executando o app no Crosswalk. O ganho de performance é visível mas ele pode aumentar o tamanho final da sua aplicação. Para instalar, digite: `ionic plugin add cordova-plugin-crosswalk-webview`
  * **Virtual Scroll** &#8211; O nosso aplicativo pode adicionar novos itens à lista de várias maneiras. Isso significa que, quanto mais a lista aumenta de tamanho, mais itens precisarão ser renderizados, o que irá consumir muita memória e impactar o desempenho geral. O Virtual Scroll foi criado com o intuito de minimizar este impacto, uma vez que ele apenas renderiza uma quantidade &#8220;x&#8221; de células na tela, suficientes para preenche-la. Dessa forma elas podem ser reutilizadas, o que evita uma sobrecarga de memória (comportamento muito similar ao de uma **ListView** no iOS). Para entender melhor sobre como utilizar o Virtual Scroll, visite <a href="https://ionicframework.com/docs/v2/api/components/virtual-scroll/VirtualScroll/" target="_blank">este link</a>.

## Considerações finais

Sim, é um post gigantesco. Mas a minha meta ao escrevê-lo era gerar o máximo de valor para profissionais que ainda não tiveram contato com o Ionic 2 ou aqueles que desejam entender melhor como ele funciona, uma vez que somos carentes de tutoriais mais densos escritos sobre o assunto em português.

Seja você um desenvolvedor, gerente de produto ou CIO de uma empresa, é muito importante compreender que ainda é difícil nos dias de hoje suportar a grande diversidade de aparelhos e plataformas existentes em um ecossistema que vive em constante mudança. Os custos para manter uma equipe multidisciplinar sempre atualizada (e com boa sinergia) é altíssimo e isso se reflete no orçamento repassado para o cliente. Optar pelo desenvolvimento de aplicativos híbridos é, antes de mais nada, uma opção estratégica que deve ser avaliada de acordo com o contexto de cada projeto. Muitas das vezes os argumentos à favor do desenvolvimento nativo não se justificam, principalmente se o projeto não demanda um _frame rate_ muito alto (como aplicativos com muitas animações, transições customizadas ou jogos).

Outro ponto que precisa ser esclarecido é que o Ionic tem um papel importantíssimo no que se refere à uma fase que é tão ou mais importante que o desenvolvimento em si: A **prototipação**. Poder validar o produto com o cliente ainda em fase inicial é um grande diferencial. Algo que lhe confere uma posição de destaque em um mercado extremamente competitivo.

## Conclusão

Há muito espaço para melhorias e recursos adicionais que podem ser implementados no aplicativo que criamos. Caso tope desafios, você pode tentar os seguintes:

  * Incluir data de publicação do post na lista;
  * Incluir recurso de navegação entre telas (deixei o NavController lá de propósito);
  * Oferecer opção de alterar url para exibir resultados de um determinado subreddit;
  * Considerar cenários onde o usuário pode perder a conexão com a internet;
  * Opção de utilizar algum recurso nativo do smartphone (ex: Câmera).

Para facilitar o seu aprendizado, o projeto está disponível no **<a href="https://github.com/carloscabral/my-reader---Ionic2" target="_blank">GitHub</a>** separado por branches. Por exemplo, caso você queira ter acesso ao passo 4 do tutorial, baixa digitar no terminal `git checkout step4` e o código fonte referente à este passo estará disponível.

Bons estudos e até a próxima!

> Se você ficou curioso sobre a criação de aplicativos multiplataforma que utilizam tecnologia da web, saiba que o Ionic não é a única opção existente. Leia meu post sobre **<a href="http://tableless.com.br/react-native-construa-aplicacoes-moveis-nativas-com-javascript/" target="_blank">React Native</a>** e descubra como já é possível criar uma aplicação 100% nativa utilizando JavaScript.

 [1]: http://tableless.com.br/uploads/2016/10/tumblr_npjjd6T4Lu1tq4of6o1_400.gif
 [2]: http://tableless.com.br/uploads/2016/10/ionic-2-localhost-5.jpg