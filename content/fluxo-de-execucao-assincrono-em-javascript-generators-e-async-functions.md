---
title: Fluxo de execução assíncrono em JavaScript – Generators e Async Functions
author: Jean Carlo Emer
type: post
date: 2016-05-23
excerpt: Tardou mas não falhou e veio como presente de ano novo. Este é o terceiro artigo de uma série que trata sobre execução assíncrona no JavaScript. Veremos a seguir como funcionam Generators e qual a sua aplicação em conjunto com Promises. Tratando um pouco do que vem por ai, faremos uma análise sobre a especificação de Async Functions.
url: /fluxo-de-execucao-assincrono-em-javascript-generators-e-async-functions/
titulo_personalizado:
  - 'Fluxo de execução assíncrono em <strong>JavaScript</strong>'
categories:
  - Destaques
  - JavaScript
  - Técnicas e Práticas
tags:
  - async
  - JavaScript

---
Os últimos artigos tratam de [Callbacks][1] e [Promises][2], corre conferir ou relembrar antes de prosseguirmos. Promises são abstrações muito importantes na evolução de escrita de código assíncrono. Tanto isto é verdade, que as técnicas e conceitos que veremos neste artigo são todos apoiados em _promises_.

<pre class="lang-javascript">function mountUserComponent() {
  return get('profile.json').then(function (response) {
    return new UserComponent(response);
  }, function onRejected() {
    // falha na requisição Ajax
  });
}
</pre>

A intenção a partir daqui é eliminar muito desta necessidade de declarar _callbacks_ de sucesso e falha para recuperar o resultado de uma promessa. Por enquanto, deixaremos de lado os Generators, que são mais complicados de serem compreendidos neste contexto de uso, e partiremos direto para as Async Functions.

## Async Functions

As Async Functions são o fruto de algumas experimentações com Generators e execução de código assíncrono. As [Async Functions][3] devem fazer parte da especificação ES2016 e permitem a escrita de códigos poderosos como este a seguir.

<pre class="lang-javascript">async function mountUserComponent() {
  let profile = await get('profile.json');
  return new UserComponent(profile);
}
</pre>

O uso de Async Functions como o nome já sugere, exige a declaração de uma função que encapsule as chamadas assíncronas. Note o `async` precedendo a declaração da função no exemplo. A chamada Ajax será disparada e a variável `profile` irá receber os dados retornados. O papel do `await` é interromper a execução do código a espera que a promessa resulte em sucesso. Nossa promessa é constituída pela requisição Ajax e portanto a próxima linha será executada apenas depois do retorno dos dados.

O resultado da execução de uma Async Function, por sua vez, é uma _promise_. Este resultado será o valor ao lado direito do `return`. Porém, caso alguma das promessas passadas para `await` falhar, esta promessa é que será retornada:

<pre class="lang-javascript">mountUserComponent().then(function(component) {
   // resultado final da execução da async function
}).catch(function(error) {
  // falha na requisição Ajax
});
</pre>

Note que as chamadas de `await` que resultam em uma promessa rejeitada são transformadas em uma exceção. As exceções também podem ser tratadas internamente na função conforme o código abaixo:

<pre class="lang-javascript">async function mountUserComponent() {
  try {
    let profile = await get('profile.json');
    return new UserComponent(profile);
  } catch (error) {
      // falha na requisição Ajax
  }
}
</pre>

Agora que os conceitos básicos foram apresentados, vamos conferir como alcançar as mesmas funcionalidades utilizando Generators. Outras construções e conceitos avançados serão abordados a partir do tópico **trabalhando com paralelismo**.

## Generators e código assíncrono

Os Generators permitem escrever um algoritmo interativo através de uma função que armazena estado. Sob um ponto de vista mais prático, Generators são utilizados para construir uma coleção de dados sob demanda.

<pre class="lang-javascript">function* infiniteLoopGenerator() {
    let i = 0;
    while (true) {
        yield i++;
    }
}
</pre>

O código acima representa uma sequência infinita de números. A cada chamada de `yield` a execução da função é interrompida permitindo que um valor seja retornado. A intenção aqui não é apresentar todos os conceitos e modos de uso dos Generators, mais detalhes sobre seu funcionamento podem ser encontrados neste [artigo da MDN sobre Iterators e Generators][4].

Com um pouco de imaginação, podemos observar a semelhança entre o `yield` e `await`: ambos interrompem a execução do nosso código. O resultado de portar nosso código para utilizar Generators seria o seguinte:

<pre class="lang-javascript">function* mountUserComponentGenerator() {
  let profile = yield get('profile.json');
  return new UserComponent(profile);
}
</pre>

A diferença aqui é que precisaríamos pegar as _promises_ produzidas pelo `yield`, esperar que fossem resolvidas e então passar seu valor de retorno para o Generator:

<pre class="lang-javascript">let userComponentGenerator = mountUserComponentGenerator();
userComponentGenerator.next().value.then(function(profile) {
    return userComponentGenerator.next(profile).value;
}).then(function(component) {
    // aqui teríamos o componente pronto
});
</pre>

Apesar do `mountUserComponent` ter um código elegante, como você pode ver, sua execução é um tanto complicada. Por causa disto, surgiram bibliotecas como [Co][5] e [bluebird coroutine][6] para fazer este trabalho sujo. Abaixo o mesmo `mountUserComponentGenerator` sendo executado utilizando Co:

<pre class="lang-javascript">co(mountUserComponentGenerator).then(function(component) {
    // aqui teríamos o componente pronto
});
</pre>

O comportamento de um Generator invocado pelo Co é o mesmo de uma Async Function. Mas apesar de serem equivalentes, o uso de Async Functions é mais adequado para nossas intenções de escrita de código assíncrono. Os próximos exemplos seguirão com o uso de Async Functions mesmo sendo possíveis e facilmente portáveis para utilizarem Generators com Co.

## Trabalhando com paralelismo

Conforme vimos nos artigos anteriores, paralelismo é um dos principais recursos que queremos explorar quando escrevemos código assíncrono.

Vamos considerar que nossa requisição de `profile.json`, necessária para montar o componente de usuário, precisa ser acompanhada de uma requisição por `avatar.json`. O componente só pode ser montado depois de conseguidas as informações de perfil e _avatar_ do usuário.

A mudança parece simples, mas o código que utiliza puramente _promises_ precisará ser totalmente reescrito:

<pre class="lang-javascript">function mountUserComponent() {
  return Promise.all([
    get('profile.json'),
    get('avatar.json')
  ]).then(function (responses) {
    profile = responses[0];
    avatar = responses[1];
    new UserComponent(profile, avatar);

  }, function onRejected() {
    // falha em alguma requisição Ajax
  });
}
</pre>

Ao contrário do código acima, o código utilizando Async Functions irá sofrer poucas alterações:

<pre class="lang-javascript">async function mountUserComponent() {
  try {
    let profile = get('profile.json');
    let avatar = get('avatar.json');
    return new UserComponent(await profile, await avatar);
  } catch (error) {
    // falha em alguma requisição Ajax
  }
}
</pre>

Vale notar que deslocamos as chamadas de `await` para o momento em que o componente precisasse ser instanciado. Se tivéssemos mantido o `await` junto ao `get('profile.json')`, a execução seria interrompida até o retorno da requisição. A requisição pelo _avatar_ não seria então executada paralelamente.

Uma boa prática é postergar as chamadas de `await` para quando o resultado é estritamente necessário. Adotando esta prática, nosso código que faz uso apenas do `profile.json` ficaria da seguinte maneira:

<pre class="lang-javascript">async function mountUserComponent() {
  try {
    let profile = get('profile.json');
    return new UserComponent(await profile);
  } catch (error) {
      // falha na requisição Ajax
  }
}
</pre>

## Execução assíncrona

Apoiando nosso estudo em um pouco de formalismo, a expressão de _await_ é composta por `await` e mais outra expressão: `await expression`. Até agora, vimos apenas exemplos onde `expression` são _promises_, mas outros valores também podem ser utilizados:

<pre class="lang-javascript">async function notSoAsyncAlert() {
  alert(await 'O await pode receber qualquer tipo de valor');
}
</pre>

Esta característica favorece a escrita de um código mais flexível. Mas lembre-se que as _promises_ são valores que representam resultados ainda não alcançados. O `await` irá transformar esta mensagem em uma _promise_ resolvida e isto tem implicações.

As _callbacks_ passadas para uma _promise_ são executadas em um próximo fluxo e não no mesmo fluxo em que são definidas. Algumas postagens sobre [performance de _promises_][7] e [comparações com nextTick][8] podem auxiliar a compreender melhor a problemática.

Voltando a nosso exemplo, graças ao `await`, o `alert` será executado apenas em um próximo fluxo de execução o que garante um atraso ínfimo. Isto caracteriza nosso código como assíncrono e garante que o funcionamento seja o mesmo quando no futuro, por exemplo, a mensagem a ser impressa for o resultado de uma chamada Ajax.

## Encadeando awaits

Um dos recursos mais inteligentes das _promises_ é a capacidade de encadear _callbacks_. Esta mesma funcionalidade pode ser alcançada com o uso de Async Functions. O código a seguir carrega arquivos de artigos e os transforma em um _blog_:

<pre class="lang-javascript">async function blogGenerator() {
  let files = getPostFiles('./posts');
  let index = generateIndex(await files);
  let posts = generatePosts(await files);

  return {
      index: await index,   
     posts: await posts
  };
}
</pre>

O encadeamento fica pouco evidente, mas a execução de `generateIndex` está restrita ao término do resgate dos arquivos de postagens. Ao fim, a função só termina quando páginas de postagem e listagem terminarem de serem geradas.

Quando comparadas com o encadeamento de _promises_ utilizando `then`, as Async Functions resultam em um código mais simples e elegantes.

## Conclusões

Utilizar Generators e Async Functions para escrita de código assíncrono são práticas recentes. O [suporte a Generators][9] ainda é restrito a poucos navegadores e as [Async Functions não possuem nenhum suporte][10] até o momento desta postagem. Porém, o uso de transpiladores é a cada dia mais comum, as funcionalidades apresentadas neste artigo podem ser utilizadas em seus projetos com o [auxílio do Babel][11], por exemplo.

Por hoje é só, pessoal. Compartilhem nos comentários suas experiências e aprendizados com esta série de artigos e até a próxima!

 [1]: http://tableless.com.br/fluxo-de-execucao-assincrono-em-javascript-callbacks
 [2]: http://tableless.com.br/fluxo-de-execucao-assincrono-em-javascript-promises
 [3]: http://tc39.github.io/ecmascript-asyncawait
 [4]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators
 [5]: https://github.com/tj/co
 [6]: http://bluebirdjs.com/docs/api/promise.coroutine.html
 [7]: http://thanpol.as/javascript/promises-a-performance-hits-you-should-be-aware-of
 [8]: http://blog.millermedeiros.com/promise-nexttick
 [9]: http://kangax.github.io/compat-table/es6/#generators
 [10]: http://kangax.github.io/compat-table/es7/#test-async_functions
 [11]: http://stackoverflow.com/a/28709165