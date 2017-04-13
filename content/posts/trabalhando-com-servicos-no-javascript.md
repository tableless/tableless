---
title: Trabalhando com serviços no Javascript
author: Vinicius Reis
type: post
date: 2016-11-08
url: /trabalhando-com-servicos-no-javascript/
categories:
  - Código
  - JavaScript
  - O Básico
  - Técnicas e Práticas
tags:
  - design patterns
  - ecmascript
  - ES6
  - JavaScript
  - Node

---
JavaScript é uma _linguagem multiparadigma_. Pode-se “_emular_” várias técnicas de programação com ele, e isso é **incrível** pois podemos decidir qual o melhor paradigma para a resolução dos problemas dos nossos projetos. Porém se por um lado isso pode parecer poderoso para a linguagem, também pode deixar os iniciantes bem confusos, é muito comum escolher a abordagem errada para o problema. Por esse motivo que o JavaScript em sido polêmico nos últimos anos.

Pensando nisso muitos desenvolvedores criam suas próprias soluções, uns pensando em ajudar e outros em forçar padrões.
  
Eu prefiro ensinar a pescar, pois JavaScript não tem que ser complexo. A **versão 6 do JavaScript (ES6/ES2015)** tornou a linguagem muito mais expressiva, facilitando muito o entendimento.

### Encapsulando lógicas

Tudo em JavaScript são objetos (exceto _undefined_), então **serviços também são objetos**, dominando como criamos e trabalhamos com objetos todas as coisas ficam bem mais tranquilas.

O Jean Carlo Emer fez um artigo muito, [mas muito bom sobre Modularização no JavaScript][1]. Sugiro que você leia, mas vou explicar um pouco sobre o assunto logo abaixo.

<img class="size-medium aligncenter" src="https://cdn-images-1.medium.com/max/800/1*hsXIPyBqqI7ZTh2QyLfizw.gif" alt="i know JavaScript basics " width="320" height="237" />

#### Scope e Closures

JavaScript possui escopo léxico. Entre outras coisas isso permite que você crie _closures_.
  
De maneira resumida você cria um “ambiente controlado” onde há funções/variáveis que só podem ser acessadas naquele escopo, criando um enclausuramento (_closure_).

<pre class="lang-javascript">const initPage = (root) =&gt; {
  const $root = $(root);
  const $menu = $root.find('.menu');
  const $profile = $menu.find('.profile');

  const initProfile = () =&gt; {
    $.get('/me')
      .then(response =&gt; $profile.text(response.username));
    // ...
  };

  const showProfileModal = e =&gt; {
   // ...
  };

  $profile.on('click', e =&gt; showProfileModal(e));

  initProfile();
};

initPage('body');
</pre>

Este é um exemplo bem bobo, mas que ilustra bem como criamos _closures_.
  
As variáveis declaradas dentro de _initPage_ só existem naquele escopo.
  
No mesmo exemplo podemos refatorar esse código em uma **IIFE (Immediately-Invoked Function Expression)**

<pre class="lang-javascript">((root) =&gt; {
  const $root = $(root);
  const $menu = $root.find('.menu');
  const $profile = $menu.find('.profile');

  const initProfile = () =&gt; {
    $.get('/me')
     .then(response =&gt; $profile.text(response.username));
    //  ...
  };

  const showProfileModal = e =&gt; {
    // ...
  };

  $profile.on('click', e =&gt; showProfileModal(e));

  initProfile();
})('body');
</pre>

Nesse código declaramos uma função e a executamos imediatamente, passando um argumento. Isso é extremamente útil quando queremos fazer um processamento de uma informação que vai servir apenas para criar uma variável.

<pre class="lang-javascript">const timezones = (() =&gt; {
  const zones = [];
  const min = -12;
  const max = 13;
  let simbol;

  for (let i = min; i &lt;= max; i++) {
    simbol = (i &lt; 0) ? '' : '+';
    zones.push(`GMT${simbol}${i}`);
  }

  return zones;
})();
</pre>

Como você já pode perceber, é possível expor dados de uma _closure_ como no exemplo anterior. A variável zones é retornada, assim a variável _timezones_ agora possui como valor o resultado da _closure_.
  
Nesse exemplo a _closure_ não usa dados externos a ela (_parent scope_/escopo pai) porém dada a natureza do JavaScript isso é perfeitamente possível.

Isso é útil para não poluir o escopo principal com informações irrelevantes.

<pre class="lang-javascript">const makeCounter = (start = 0) =&gt; {
  let current = start;

  const add = (value = 1) =&gt; current += value;
  const remove = (value = 1) =&gt; add(value * -1);
  const get = () =&gt; current;

  return { add, remove, get };
};

const counter = makeCounter(10);

counter.add() // 11
counter.add() // 12
counter.add(8) // 20
counter.remove(10) // 10
</pre>

Este é um exemplo bem interessante. Estamos combinando _closures_ com _factory_.

Com isso podemos criar vários contadores, e trabalhar como melhor convir com estes contadores.

<div id="attachment_56186" style="width: 510px" class="wp-caption aligncenter">
  <img class="wp-image-56186 size-full" src="http://tableless.com.br/uploads/2016/10/wtf.gif" alt="Só isso! Simples, né?" width="500" height="284" />
  
  <p class="wp-caption-text">
    Só isso! Simples, né?
  </p>
</div>

Se você entendeu como o exemplo do contador funciona, parabéns você já sabe criar serviços com javascript.

Isso mesmo, este contator é um serviço. Na verdade ele é um _factory_, mas com pequenos ajustes ele vira um serviço de fácil reuso.

<pre class="lang-javascript">// makeCounter.js -&gt; factory
const makeCounter = (start = 0) =&gt; {
  let current = start;

  const add = (value = 1) =&gt; current += value;
  const remove = (value = 1) =&gt; add(value * -1);
  const get = () =&gt; current;

  return { add, remove, get };
};

export default makeCounter
</pre>

<pre class="lang-javascript">// counter.js -&gt; service
import makeCounter from './makeCounter.js';

export default makeCounter(0);
</pre>

Agora temos dois arquivos, um contendo o _factory_ do contador, e outro contendo o serviço de contagem.

## Módulos JavaScript

<img class="size-full wp-image-56185 aligncenter" src="http://tableless.com.br/uploads/2016/10/module.gif" alt="module" width="400" height="250" />

Como visto anteriormente, é bem simples criar serviços com JavaScript, basta antes entender alguns conceitos.

Porém isso não é tudo, se você esta criando um serviço é porque tem a intenção de reusar esta lógica em mais de um local da aplicação. Isto não é uma regra, talvez você queira apenas centralizar a lógica da operação.

Não importa o objetivo inicial, você vai acabar criando um módulo JavaScript para aquela sua operação/serviço. No exemplo do contador foram criados dois arquivos, o _contador_ e o _factory do contador_. Nesse momento você precisa entender minimamente o que são módulos JavaScript.

Em resumo: um arquivo JavaScript é um módulo e um módulo JavaScript é um arquivo.

Você pode criar um módulo a partir de outros módulos, como é o exemplo do contador, ele é composto a partir do módulo _makeCouter_.

Em geral a lógica dos módulo é encapsulada em _closures_ e o retorno delas é _cacheado_, sendo assim, uma vez que você importa um módulo, ele será **o mesmo sempre, compartilhando seu estado**. Saiba mais [aqui][2].

### Usando serviços

Agora que você possui essas informações acredito que criar seus próprios serviços não será nenhum _bicho de sete cabeças_.

> Vale a pena dizer que tudo pode ser considerado um serviço, inclusive _factories_.

Para reforçar vou deixar mais um exemplo de uso de serviços.

<pre class="lang-javascript">import Http from './http.js';
import UsersService from './modules/users/service.js';

Http.setToken('XPTO'); // Define o token de autentificação

// Cattega a primeira página de usuários
// Exibe um alerta com o nome do primeiro usuário retornado pelo serviço

UsersService
  .getAll({ page: 1 })
  .then(result =&gt; result.data)
  .then(data =&gt; data[0])
  .then(first =&gt; {
    alert(first.name);
  });
</pre>

Para efeito de aprendizado uma sintaxe alternativa, com [_import binding_][3].

<pre class="lang-javascript">import { setToken } from './http.js';
import { getAll as getAllUsers } from './modules/users/service.js';

setToken('XPTO'); // Define o token de autentificação

// Carrega a primeira página de usuários
// Exibe um alerta com o nome do primeiro usuário retornado pelo serviço

getAllUsers({ page: 1 })
  .then(result =&gt; result.data)
  .then(data =&gt; data[0])
  .then(first =&gt; {
    alert(first.name);
  });
</pre>

Este pode não parecer para alguns mas é um exemplo bem prático do uso de serviços.
  
O serviço de _Http_ também é usado pelo _serviço de usuários_, por isso é possível definir o **_token_** de autentificação antes de efetivamente usar os serviços, pois eles vão compartilhar o mesmo estado/serviço.

Outra característica interessante é que esses serviços não estão ligados diretamente a nenhum contexto. Isso significa que não importa que ambiente você esteja ou que _framework_ você esta usando, os serviços são agnósticos. Eles podem ser usados no **NodeJS, VueJS, ReactJS**, etc.
  
Este é um dos princípios do polimorfismos do JavaScript porém este é outro assunto.

&nbsp;

Se quiser saber mais sobre meu trabalho visite meu blog[ https://medium.com/@luizvinicius73][4]

* * *

Este artigo foi originalmente postado no meu [blog no medium][5] em 31 de Julho de 2016

 [1]: http://tableless.com.br/modularizacao-em-javascript/
 [2]: http://www.vuejs-brasil.com.br/utilizando-vuex-na-forma-modular-2/#vamosentenderoqueaconteceu
 [3]: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/import
 [4]: https://medium.com/@luizvinicius73
 [5]: https://medium.com/by-vinicius-reis/trabalhando-com-servicos-no-javascript-864310cf386c