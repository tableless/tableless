---
title: Fluxo de execução assíncrono em JavaScript – Promises
author: Jean Carlo Emer
type: post
date: 2015-08-07
excerpt: 'Este é o segundo artigo de uma série que trata de execução assíncrona no JavaScript. Neste vamos ver algumas limitações das callbacks e como as <em>promises</em> podem ser um recurso poderoso de programação.'
url: /fluxo-de-execucao-assincrono-em-javascript-promises/
categories:
  - Geral

---
No [primeiro artigo da série][1] falamos sobre o que é execução assíncrona, quais APIs executam código assincronamente e como se livrar de dores de cabeça quando utilizando _callbacks_.

Uma série de problemas encontradas ao utilizar _callbacks_ foram explorados junto com suas soluções. Aprendemos a utilizar _closures_, contornar o tratamento de excessões, reconhecer o comportamento do `this` e evitar o Callback Hell. O que veremos a seguir são algumas das reais limitações das _callbacks_.

## Limitações das Callbacks

Apenas uma _callback_ pode ser associada a um determinado evento do _loop_ interno de eventos do JavaScript.

<pre class="lang-javascript">var xmlhttp = new XMLHttpRequest()
xmlhttp.open('GET', 'http://url.com', true)
xmlhttp.onreadystatechange = function callback() {}
xmlhttp.send()
</pre>

Veja acima o exemplo de uma chamada tradicional Ajax que só aceita uma única _callback_ para lidar com o retorno do servidor. As funções mais antigas da API do DOM enfrentavam este problema para lidar com eventos: `document.getElementById('bla').onclick = callback`.

Algumas APIs suavizam este problema ao modelar suas interações através de uma interface orientada a eventos. Desta maneira, um único evento da API pode ter mais de uma _callback_ a ser executada no futuro. Cada _callback_ associada a um evento da API será registrada no _loop_ de eventos do JavaScript.

Fazemos isto com frequência utilizando jQuery para associar _callbacks_ a eventos do DOM. Cada linha do código abaixo pode muito bem estar distribuída entre módulos da sua aplicação:

<pre class="lang-javascript">element.on('click', callback1)
element.on('click', callback2)
element.on('click', callback3)
</pre>

Porém, para os casos da API não suportar o modelo de eventos, atribuir múltiplas _callbacks_ resulta em um alto acoplamento. Como exemplo, observe o código abaixo que não pode ser facilmente distribuído em diferentes módulos da aplicação:

<pre class="lang-javascript">xmlhttp.onreadystatechange = function callback() {
  callback1()
  callback2()
  callback3()
}
</pre>

Outro ponto que já deve ter notado é que sempre nos referimos a _callbacks_ como porções de código a serem executadas em um tempo conveniente **no futuro**. Isto porque o modelo de _callbacks_ não possui memória. Sempre que o fluxo de execução associado a _callback_ achar oporturno, esta será executada.

Observe o caso em que é preciso esperar que o documento esteja carregado para executar um determinado código. O DOM expõe o evento `DOMContentLoaded` que indica justamente o instante em que o documento está totalmente carregado. Mas este evento ocorre uma única vez.

Os módulos da aplicação que dependem do carregamento do documento devem ser definidos antes deste evento disparar, ou nunca serão executados. Com o domínio de técnicas que temos até aqui, conseguimos contornar este problema de uma maneira grosseira. Teremos apenas que garantir que o código a seguir seja executado antes do documento estar completamente carregado. Sua função é indicar através da variável `isReady` se o documento está carregado:

<pre class="lang-javascript">window.isReady = false
document.addEventListener('DOMContentLoaded', function (){ 
  window.isReady = true
})
</pre>

E então, nos módulos da aplicação, teremos que implementar uma lógica baseada na variável `isReady`. É preciso conferir se o documento está carregado e caso contrário, atribuir uma _callback_ ao evento de carregamento:

<pre class="lang-javascript">if (isReady) {
  callback1()
} else {
  document.addEventListener('DOMContentLoaded', callback1)
}
</pre>

As limitações e dificuldades já estão claras até aqui, mas podemos adicionar um tanto mais de complexidade. Podemos supor que estes mesmos módulos que dependem de o documento estar completo, também dependem da resposta de uma requisição assíncrona que retorna o perfil do usuário. Além da variável `isReady` teríamos mais outra, digamos `isProfileLoaded` para controlar os diferentes carregamentos.

Em resumo: **algumas APIs aceitam uma única _callback_, _callbacks_ não matém memória e são difíceis de coordenar quando temos fluxos assíncronos executando em paralelo**. Conheceremos a seguir as _promises_ que prometem (sic) solucionar todos estes problemas.

## Introdução

Uma promessa representa o possível resultado de uma operação assíncrona. Alguns exemplos serão mais fáceis para esclarecer como as promessas funcionam. Vamos assumir que a função `get` retorna uma _promise_ de uma requisição Ajax.

O código a seguir irá requisitar o perfil de um usuário:

<pre class="lang-javascript"><code>var profile = get('profile.json')</code></pre>

Através da função `then` é possível atribuir duas _callbacks_ a uma promessa. A primeira das _callbacks_ será executada quando tudo ocorrer bem, chamaremos estas de **callbacks de sucesso**. A segunda delas é executada em caso de erro, chamaremos de **callbacks de falha**. Podemos utilzar nossa _promise_ `get` da maneira seguinte:

<pre class="lang-javascript">profile.then(function (response) {
  // requisição Ajax executada com sucesso,
  // perfil do usuário retornado
}, function onRejected() {
  // falha na requisição Ajax
});
</pre>

As promessas são valores que podemos passar para os diferentes módulos da nossa aplicação. **Além disto, as promessas possuem memória**. Mesmo depois de a requisição por `profile.json` completar, podemos adicionar novas _callbacks_ através do `then`. Promessas aceitam múltiplas _callbacks_.

<pre class="lang-javascript">var profile = get('profile.json')

var basket = new Basket(profile)
var toolbar = new Toolbar(profile)

function Basket(profile) {
  profile.then(this.setup, this.error)
}

// ...
</pre>

## Criando Promises

Uma parcela importante para compreender o funcionamento das _promises_ é exercitar sua criação. O exemplo abaixo cria uma promessa que termina bem em 50% dos casos:

<pre class="lang-javascript">var randomPromise = new Promise(function (fulfill, reject) {
  if (Math.random() &gt; .5) {
    fulfill('success')
  } else {
    reject('fail')
  }
}
</pre>

As funções `fulfill` e `reject` permitem resolver (terminar bem) ou rejeitar a promessa. Aumentado o nível de detalhes: ao chamar `fulfill`, as _callbacks_ de sucesso atribuídas a promessa através do `then` são executadas; para o caso de `reject` ser disparado, as _callbacks_ de falha é que serão executadas. **Os valores passados para `fulfill` e `reject` ficam memorizados na promessa** e são sempre passados para as _callbacks_ de sucesso e falha respectivamente.

Existem dois atalhos para criação de promessas. São as funções `Promise.resolve` e `Promise.reject`. Estas funções criam uma promessa resolvida ou rejeitada respectivamente. O código abaixo irá imprimir &#8220;salve&#8221; em um diálogo de alerta:

<pre class="lang-javascript">Promise.resolve('salve').then(function (message) { 
  alert(message)
})
</pre>

Como último exercício, vamos escrever a função `get` que fomos apresentados anteriormente:

<pre class="lang-javascript">function get(url) {
  return new Promise(function (fulfill, reject) {
    var req = new XMLHttpRequest()
    req.open('GET', url)

    req.onload = function () {
      if (req.status == 200) {
        fulfill(req.response)
      } else {
        reject(Error(req.statusText))
      }
    }

    req.send()
  })
}
</pre>

A promessa instanciada no interior da função, como deve ser, encapsula uma operação assíncrona. A requisição Ajax é disparada pela promessa. O resultado da requisição resolve ou rejeita a promessa no interior da _callback_ de `onload`.

Vale lembrar que as funções Ajax da jQuery já retornam promessas. A função `get` que acabamos de criar é equivalente a função `$.get` da jQuery.

## Encadeando Promises

Encadeamento ou _chaining_ é bastante comum no universo JavaScript desde a popularização da jQuery. Usando promessas, é possível chamar um `then` após outro conforme abaixo:

<pre class="lang-javascript">parser.start()
  .then(getFiles)
  .then(generateIndex)
  .then(generatePosts)
</pre>

Cada função passada para o `then` pode retornar um valor ou mesmo uma promessa. Aquilo que for retornado será passado para o próximo `then`.

Voltando a nosso exemplo, para o caso de `getFiles` disparar uma requisição assíncrona e retornar uma _promise_, o `generateIndex` será chamado apenas quando esta promessa for resolvida. O `generateIndex` poderá então processar os arquivos e retorná-los. Na sequência, a função `generatePosts` irá receber os mesmos arquivos e fará seu trabalho.

Um detalhe do funcionamento deve ajudar no entendimento. Uma nova promessa é criada a cada chamada de `then` com o valor retornado pela sua _callback_ de sucesso ou falha. Esta nova promessa é que será utilizada pelo próximo `then` do encadeamento. Para o caso da _callback_ não retornar um valor promessa, a função `Promise.resolve` será chamada.

Graças a este comportamento, a rejeição é tratada de um jeito bem poderoso em meio a um encadeamento. Sempre que a promessa é rejeitada, a primeira _callback_ de falha do encadeamento é chamada. **Esta _callback_ terá como missão tratar a falha**. O valor retornado pela _callback_ de falha irá **disparar as próximas _callbacks_ de sucesso do encadeamento a não ser que esta retorne uma promessa rejeitada**.

O código a seguir irá imprimir o erro &#8220;Oops&#8221; e a mensagem &#8220;Tudo certo&#8221; no _console_ do navegador. Nele usaremos o `catch(callback)` que é equivalente a `then(null, callback)`.

<pre class="lang-javascript">Promise.resolve('Yep')
  .then(function(data) {
     return Promise.reject('Oops')
  }, function (error) {
    // nada de errado com a promise Yep
  })  
  .catch(function (error) {
    console.error(error)
    // o erro é tratado por esta primeira callback de falha
    return 'Tudo certo'
  })
  .then(function (message) {
    // o valor retornado pela callback de falha é transformado
    // em uma promessa resolvida
    console.log(message)
  })
</pre>

## Tratando Excessões

No primeiro artigo conhecemos o quanto excessões podem ser uma dor de cabeça quando utilizamos _callbacks_. As promessas possuem um mecanismo muito mais inteligente e fácil para lidar com excessões.

Sempre que uma _callback_ de sucesso ou falha disparar uma excessão, uma promessa de rejeição é criada. A função de _parser_ de JSON, por exemplo, dispara uma excessão quando recebe um JSON inválido. O código a seguir abre uma janela de diálogo informando que há algo de errado com o JSON passado:

<pre class="lang-javascript">Promise.resolve('oops')
  .then(function (data) { 
    JSON.parse(data) 
  })
  .catch(function (err) { 
    alert(err.message) 
  })
</pre>

Até aqui, vimos que promessas possuem memória e aceitam mais de uma _callback_. Por serem valores, _promises_ podem ser facilmente passadas para os módulos da nossa aplicação. Vimos também que promessas possuem um mecanismo poderoso para contornar falhas e excessões. O único tópico que falta é lidar com paralelismo.

## Trabalhando com paralelismo

O paralelismo acontece sempre que utilizamos simultaneamente recursos computacionais com o objetivo de reduzir o tempo necessário para resolver um determinado problema. O navegador faz isto a todo tempo quando, por exemplo, requisita diversas imagens para o servidor.

Quando falávamos das limitações das _callbacks_, apresentamos o problema de um módulo da aplicação que precisava esperar o documento estar carregado e também ter os dados do perfil de usuário carregados via Ajax. Podemos tratar estas duas tarefas como operações assíncronas paralelas.

O primeiro passo é criar uma promessa que deve resolver quando o documento estiver carregado. Esta promessa é equivalente a variável `isReady` que criamos no início do arquivo:

<pre class="lang-javascript">var documentReady = new Promise(function (fulfill) {
  document.addEventListener('DOMContentLoaded', fulfill)
})
</pre>

Note que, assim como o código do da variável `isReady`, este código deve ser adicionado ao documento antes que o evento `DOMContentLoaded` seja disparado. A [promessa retornada pela jQuery][2] através de `$.ready.promise()` tem comportamento semelhante porém é bem mais robusta. Usaremos esta e a função `$.get` da jQuery para carregar as informações do usuário.

Tudo o que precisamos é a função `Promise.all` que permite esperar que duas ou mais promessas estejam resolvidas. A _callback_ de sucesso do `then` a seguir será chamada com a lista de resultados retornados pelas promessas:

<pre class="lang-javascript">var profile = $.get('profile.json')
var ready = $.ready.promise()

Promise.all([
  profile,
  ready
])
  .then(function (results) {
    var profileData = results[0]
    /* podemos disparar o comportamento do 
       módulo a partir daqui */
  }, function (result) {
    // recebe o resultado da primeira promessa que falhar
  })
</pre>

Outra função interessante é a `Promise.race`. Como você deve imaginar, esta função tem uso semelhante à anterior com a diferença que as _callbacks_ de sucesso são chamadas assim que a primeira promessa for resolvida. Funções como esta podem ser bem interessantes para definir _timeout_ para outras tarefas.

## Conclusão

As promessas são um conceito um tanto antigo e existem diversas implementações. No universo JavaScript, existe uma discussão sobre qual o padrão mais adequado. O padrão [Promises/A+][3] é o mais aceito e muitas [bibliotecas tem feito esforço para ficarem compatíveis a ele][4]. Os exemplos mostrados aqui seguem este padrão.

Promessas também possuem seus pontos contra, [alguns artigos alertam][5], por exemplo, para o fato de que memorizar todos os resultados pode pesar bastante na memória ocupada pela aplicação.

Todos os fatores devem ser considerados quando optamos por utilizar uma determinada tecnologia. Mesmo assim, espero que os exemplos que vimos aqui o tenham convencido de que promessas são um recurso a mais para escrever aplicações melhores.

Os problemas enfrentados quando utilizamos puramente _callbacks_ estão intimamente ligados com o fato de tentarmos soluções baseadas em controle de fluxo ao invés de dependências entre valores. _Promises_ são ótimas aliadas nesta briga, lembre-se que: **programação funcional é sobre trabalhar com valores e não com funções**.

<p style="text-align: center;">
  ***
</p>

Ufa, esta leitura deve ter sido um tanto pesada. Alguns conceitos não são nada fáceis, tentei deixá-los o mais claro possível e apoiados por exemplos.

O próximo e último artigo da série irá tratar de _generators_ e como estes podem ser utilizados em conjunto com as promessas. Veremos também algumas propostas futuras para lidar com execução de código assíncrono no JavaScript.

 [1]: http://tableless.com.br/fluxo-de-execucao-assincrono-em-javascript-callbacks
 [2]: https://github.com/jquery/jquery/blob/842958e7aecd0d75a7ee9e2aaec83457701aa2f3/src/core/ready.js
 [3]: https://promisesaplus.com
 [4]: http://blog.jquery.com/2015/07/13/jquery-3-0-and-jquery-compat-3-0-alpha-versions-released
 [5]: http://sealedabstract.com/code/broken-promises