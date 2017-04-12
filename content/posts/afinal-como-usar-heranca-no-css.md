---
title: Afinal, como usar herança no CSS?
author: fernahh
type: post
date: 2015-10-11
url: /afinal-como-usar-heranca-no-css/
categories:
  - CSS
tags:
  - CSS
  - extend
  - herança css
  - oocss
  - SASS

---
Herança surgiu para ajudar desenvolvedores a escreverem mesmo e produzirem mais. Vamos ver aqui como esse conceito básico das folhas de estilo pode nos ajudar no dia-a-dia.

Geralmente quando alguém começa a desenvolver interfaces web, o processo é aos trancos e barrancos. Nessa situação, iniciantes buscam aprender como se faz aquela borda arredondada ou como aplicar transparência. Por fim, acabam deixando de lado conceitos básicos de CSS. Levando isso em conta, precisamos primeiramente aprender sobre **especificidade** e **efeito cascata**. Esses dois pontos são essenciais para aprendermos como escrever folhas de estilo usando herança.

## A especificidade de seletores

Um documento web possui derivadas fontes de estilo, sendo elas:

  * a folha de CSS servida pela página;
  * configurações setadas pelo usuário;
  * o estilo _default_ aplicado pelo _user agent_ (ex: navegadores).

A primeira é a mais importante. A folha de estilo pode sobrescrever as configurações do usuário, que por sua vez pode sobrescrever os estilos aplicados _user agent_.

Apesar do CSS servido pela página web ser mais específico, é importante lembrar que o usuário tem a opção de forçar o estilo desejado por ele. Porém, isso **não vale para regras** que recebem `!important`.

A <a href="http://www.w3.org/TR/css3-selectors/#specificity" target="_blank">W3C criou uma forma de calcular a especificidade de seletores</a>. Para entender de forma simples, basicamente distribuímos pesos diferentes as regras aplicadas:

  * CSS inline: 1000 pontos;
  * ID: 100 pontos;
  * Classes, pseudo-classe e atributos: 10 pontos;
  * Elementos: 1 ponto.

Na prática, podemos fazer cálculos como os exemplos a seguir:

  * `p.foobar`: 1 classe + 1 elemento = 11 pontos.
  * `div#foobar .foo .bar`: 1 ID + 1 elemento + 3 classes = 131

A especificidade pode dar grandes dores de cabeça em projetos complexos, ainda mais quando o número de desenvolvedores é maior. Não é rara a aplicação com um grande número de uso do `!important`. Isso funciona como uma forma de quebrar a especificidade para sobrescrever uma regra.

<pre>header h1 {
  color: red;
}

/* Essa regra será mais específica. */

h1 {
  color: red !important;
}
</pre>

Evite ao máximo usar `!important`. Os 5 minutos que você economiza fazendo uso dele podem se tornar horas no futuro. Fica a dica:

<blockquote class="twitter-tweet" lang="pt">
  <p dir="ltr" lang="en">
    Easy way to tell how screwed you are when dealing with CSS from a legacy project: `grep -rin &#8216;!important&#8217; assets/sass/ | wc -l`
  </p>
  
  <p>
    — Rafael Rinaldi (@rafaelrinaldi) <a href="https://twitter.com/rafaelrinaldi/status/586216597913739264">9 abril 2015</a>
  </p>
</blockquote>

## Efeito cascata: o coração do CSS

Não é a toa que o a palavra _cascade_ está no nome nas folhas de estilo. Essa técnica é utilizada para definir o estilo a um seletor mesmo em caso de conflitos.

_Pergunta: você sabe o que acontece quando existem duas regras para um mesmo seletor?_

A cascata define o peso de uma regra através das seguintes características:

  * importância;
  * origem;
  * especificidade;
  * ordem de declaração.

Saber como o efeito cascata funciona irá lhe poupar boas horas de trabalho.

_Mas e como o navegador lida com conflitos de regras?_ Primeiramente, ele vasculha **todas as regras** que se aplicam ao elemento. Como segundo passo, ele irá classificar os **níveis de importância** e suas **origens**. Depois disso, irá ocorrer um _match_ das declarações com o **mesmo nível de importância**. Por último, se houver duas regras com o mesmo peso, a que é **declarada por último** ganhará.

Você já deve ter percebido que quanto mais fácil esse processo para o navegador, mais performática será sua aplicação.

Caso queira saber mais sobre efeito cascata e herança, <a href="http://tableless.com.br/efeito-cascata-e-especificidade-do-css/" target="_blank">recomendo esse post do Tableless de 2009</a>.

## A herança

A palavra herança rapidamente remete ao paradigma de <a href="https://pt.wikipedia.org/wiki/Orienta%C3%A7%C3%A3o_a_objetos" target="_blank">Orientação a Objetos</a>. Caso você acompanhe discussões sobre _front-end_, já deve saber que o termo &#8220;_orientação a objetos_&#8221; não é bem visto tratando-se de CSS.

Assim como você herda métodos e atributos de objetos, no CSS você herda as regras de um elemento pai.

<pre>/* 
 * Todo o conteúdo textual do documento
 * terá 16px de tamanho, pois herdam do
 * `body`.
 */

body {
  font-size: 16px;
}</pre>

É importante lembrar que nem todas as propriedades serão herdadas por elementos filho. Geralmente as propriedades que se referem ao _box-model_ (`height`, `width`, `margin`, `padding`) não aceitam herança. Caso você queira forçar a herança, pode usar o valor `inherit`. Aliás, você sabe a <a href="http://tableless.com.br/entendendo-os-valores-initial-e-inherit-do-css/" target="_blank">diferença entre initial e inherit</a>?

Podemos fazer um uso inteligente de herança para economizar várias linhas de código. É muito mais fácil especificar valores para elementos pais e utilizá-los em seus filhos do que especificar um por um. Se você der uma olhada em códigos de _frameworks_ de CSS, irá notar que herança é fortemente usada para melhorar a manutenção do projeto.

## Herança com Sass

Pré-processadores deram super poderes para desenvolvedores escreverem CSS. Em nosso contexto, `@extend` e _mixins_ nos trazem benefícios, mas que devem ser usados com bastante cautela.

### @extend

Podemos extender _placeholders_ (`%placeholder`) e classes. Muitos autores desencorajam desenvolvedores a usarem esse recurso. O motivo é o CSS gerado.

Por exemplo, digamos que temos uma classe `.error` e queremos usar os estilos dela em outra classe.

<pre>.error {
  color: red;
}

.icon--error {
  @extend .error;
}
</pre>

O CSS gerado será o seguinte:

<pre>.error, .icon--error {
  color: red;
}</pre>

Ou seja, o Sass não _&#8220;copia&#8221;_ os valores, ele apenas separa o valor em uma _mesma regra_.
  
Agora digamos que em outro contexto precisamos reescrever a cor de erro para um tom mais forte.

<pre>.other_context .error {
  color: darken(red, 10%);
}
</pre>

Além de criar a regra para a classe `.error`, o pré-processador irá aplicar a regra para as outras _&#8220;instâncias&#8221;_ da classe:

<pre>.other_context .error, .other_context .icon--error {
  color: #cc0000;
}
</pre>

**Isso é péssimo**. Além de tirar o controle do desenvolvedor, isso irá gerar **código desnecessário** e prejudicar outras áreas de uma interface. Lembre-se: tome cuidado com o _bug_ dos <a href="http://blogs.msdn.com/b/ieinternals/archive/2011/05/14/10164546.aspx" target="_blank">4095 seletores</a>.

Usando _placeholders_, o Sass irá realmente &#8220;copiar&#8221; os estilos para a classe que possui o `@extend`. Porém, se o _placeholder_ for alterado em um contexto, isso também irá gerar uma regra para as classes que o estenderam.

<pre>%error,
.error {
  color: red;
}

.icon--error {
  @extend %error;
}

.other_context .error {
  color: darken(red, 10%);
}
</pre>

O output será esse:

<pre>.error {
  color: red;
}

.icon--error {
  color: red;
}

.other_context .error {
  color: #cc0000;
}
</pre>

Perceba que dessa vez a instância de `.error`, a classe `.icon--error` **não herdou as regras** em outro contexto.

**Resumindo: evite o `@extend`. Se for usar, vá de _placeholders_.**

### Mixins

Outra forma criar herança é usando _mixins_. Com eles você pode realmente _copiar_ propriedades e valores para uma classe.

<pre>@mixin error {
  color: red;
}

.icon--error {
  @include error;
}

.label--error {
  @include error;
}
</pre>

O problema com essa abordagem é que ela não será tão performática, levando em conta que ela gerará duas regras com o mesmo código:

<pre>.icon--error {
  color: red;
}

.label--error {
  color: red;
}
</pre>

Porém, mixins são eficientes se você precisar de parâmetros.

Vamos continuar com nosso exemplo. Se precisarmos de uma cor mais forte, poderemos passar essa opção por parâmetro.

<pre>@mixin error($critical: false) {
  @if $critical {
    color: darken(red, 10%);
  } @else {
    color: red;
  }
}

.icon--error {
  @include error;
}

.icon--critical-error {
  @include error($critical: true);
}
</pre>

O Sass irá gerar o vermelho mais escuro quando passarmos o valor `true` para a variável `$critical`:

<pre>.icon--error {
  color: red;
}

.icon--critical-error {
  color: #cc0000;
}
</pre>

## Concatenação de classes

Se você é purista e não gosta de pré-processadores ou prefere não usar as &#8220;mágicas&#8221; do Sass, você pode fazer uso da concatenação/composição de classes no HTML. O <a href="http://getbootstrap.com/" target="_blank">Bootstrap</a> usa essa abordagem.

Basicamente você terá estilo padrão em uma classe e usará outras, se necessário, para alterar o layout.

No HTML com um elemento de botão, teríamos a classe `.button`. Se precisarmos criar um botão de sucesso, usamos a classe `.button--success` juntamente com `.button`.

<pre>.button {
  display: inline-block;
  padding: 10px;
  color: black;
  background-color: white;
}

.button--success {
  color: white;
  background-color: green;
}
</pre>

Na minha opinião essa é a forma mais correta de usarmos herança. Sempre opte por usar _features_ nativas do CSS ao invés das mágicas do Sass.

## Conclusão

Herança é uma abordagem extremamente necessária para começar a entender o desenvolvimento de CSS escalável. Depois de entender bem o conceito, estude <a href="http://tableless.com.br/oocss-smacss-bem-dry-css-afinal-como-escrever-css/" target="_blank">padrões de escrita</a>. Olhe o código fonte de _frameworks_ para entender a arquitetura usada.

Nunca saia escrevendo CSS até dar certo. Entenda as regras e planeja seus passos. Pensar antes de começar sem dúvidas será mais produtivo.