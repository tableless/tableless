---
title: Angular JS – Service x Factory
author: Guilherme Assemany
type: post
date: 2016-04-10
excerpt: |
  Qual a diferença entre service e factory no AngularJS?
  Esta é uma pergunta muito comum entre os desenvolvedores que estão usando o Angular JS. Neste artigo, vamos tentar responder isso!
url: /angular-js-service-x-factory/
categories:
  - AngularJS
  - Código
  - JavaScript
tags:
  - angularjs
  - factories
  - factory
  - JavaScript
  - service
  - services

---
# Angular JS – Service x Factory

Qual a diferença entre service e factory no AngularJS? Esta é uma pergunta muito comum entre os desenvolvedores que estão usando o AngularJS.

Mas antes de entrar neste assunto, vamos revisar como definir e usar `.service` e `.factory`.

Um `.service` é um método no nosso módulo principal (app), que recebe um nome e uma função que o definem.

Podemos definir um `.service` assim:

<pre class="lang-javascript">(function() {
 'use strict';
 
angular
       .module('meuApp') // Define a qual módulo seu .service pertence
       .service('MeuService', MeuService); //Define o nome a função do seu .service
 
       MeuService.$inject = ['$http']; //Lista de dependências
 
       function MeuService($http) {
 
         var vm = this;
 
         //
         vm.fazerAlgumaCoisa = fazerAlgumaCoisa;
 
         //Implementação das funções
         function fazerAlgumaCoisa() {
           console.log('Fiz alguma coisa');
         }
           
       }
})();

</pre>

Uma vez definido, nós podemos injetar e usar este .service em outros componentes, como por exemplo: Directives, Controllers e Filters. Basta colocá-lo como dependência. Veja o código abaixo:

<pre class="lang-javascript">(function() {
    'use strict';
 
    angular
        .module('meuApp')
        .controller('MeuController', MeuController);
 
    MeuController.$inject = ['MeuService']; // Injetamos o service
 
    /* @ngInject */
    //Injetamos o service
    function MeuController(MeuService) {
        var vm = this;
 
        MeuService.fazerAlgumaCoisa(); // Vai executar o console.log('Fiz Alguma coisa!')
        
    }
})();
</pre>

Se até ai está tudo certo, então ótimo! Agora vamos definir uma `.factory`:

<pre class="lang-javascript">(function() {
    'use strict';

    angular
        .module('meuApp')
        .factory('minhaFactory', minhaFactory);

    minhaFactory.$inject = ['$http'];

    /* @ngInject */
    function minhaFactory($http) {
        var service = {
            fazerAlgumaCoisa: fazerAlgumaCoisa
        };

        return service;

        function fazerAlgumaCoisa() {
          console.log('Fiz alguma coisa');
        }
    }
})();
</pre>

Novamente: `.factory()` é um método em nosso módulo principal(app), e a factory também recebe um nome e uma função que a define. Da mesma forma que injetamos o .service, podemos injetar a `.factory`.

### Qual é a diferença?

Observando bem o código, você deve ter percebido que ao invés de trabalhar com o “this” (var **vm**= **this**) na factory, nós estamos retornando um objeto literal. Por quê?

O que acontece é que um **.service é uma função construtora**, enquanto um .factory não é. Em algum lugar no código fonte do AngularJS, existe um código que chama o **Object.create()** com a função construtora de um .service quando este é instanciado.

Entretanto, um **.factory é somente uma função que é chamada**, por este motivo precisamos retornar um objeto.

Para ficar um pouco mais claro, vamos dar uma olhada no código do Angular JS. Veja uma .factory

<pre class="lang-javascript">function factory(name, factoryFn, enforce) {
  return provider(name, {
    $get: enforce !== false ? enforceReturnValue(name, factoryFn) : factoryFn
  });
}
</pre>

A função factory recebe o nome, e uma outra função para definir a nossa .factory.

Basicamente essa função factory retorna um provider com o mesmo nome, e esse provider tem o método $get, que nesse caso é a nossa função passada para a factory.

Em outras palavras, se nós injetarmos ‘minhaFactory’ em algum lugar, o que acontece é:

<pre class="lang-javascript">minhaFactoryProvider.$get();
</pre>

Certo! Funções Factory apenas são chamadas, mas e o .service?

<pre class="lang-javascript">function service(name, constructor) {
  return factory(name, ['$injector', function($injector) {
    return $injector.instantiate(constructor);
  }]);
}
</pre>

Olhando o código acima, vemos que quando chamamos a função service(), o AngularJS chama na verdade a factory().

Mas ele não passa a função construtora do nosso .service para a .factory do mesmo jeito. Ele passa também uma função que pede ao injetor(**$injector**) para **instanciar o objeto dado pela função construtora**.

Em outras palavras: Um .service chama uma .factory predefinida que por sua vez é acaba sendo um método $get() no provider correspondente.

**$injector.instatiate()** é o método que executa o **Object.create()** com a função construtora do .service. É por isso que usamos o “this” em um .service!

No final das contas, não importa oque vamos usar. Um .service ou .factory, no final é sempre uma função factory que é chamada e cria um provider para nosso serviço.

#### Dica:

Se você já está de olho no ES6, opte por usar .service! Você pode usar facilmente classes do ES6 em um .service, oque não é possível em uma .factory() !