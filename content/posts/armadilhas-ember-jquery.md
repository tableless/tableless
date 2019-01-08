---
title: Armadilhas Ember <> JQuery
authors: Aurélio Saraiva
type: post
date: 2017-11-07
excerpt: O uso do JQuery em conjunto com o Ember pode trazer diversas armadilhas que vão resultar em lentidão, vazamento de memória e outros problemas.
image: https://i.imgur.com/WUn7weZ.jpg
categories:
  - Javascript
  - front-end
tags:
  - jquery
  - emberjs
  - Frameworks Javascript
---

Sim! O uso do JQuery em conjunto com o Ember pode trazer diversas armadilhas que
vão resultar em lentidão, uso excessivo e vazamento de memória (*memory leak*),
transições lentas, scroll lento podendo causar a impressão de que **Ember é
lento!**

É importante ressaltar que eliminar o uso do JQuery não vai resolver 100% o
problema de performance, o que resolve de fato é ter código bem escrito.

Vamos lá!

## Erro 1: Não destruir os “event listeners”

Não destruir os *event listeners* não é um problema exclusivo do JQuery, este é
um problema que precisa ser tratado manualmente para cada listener registrado.
*Se você registra um event listener, você precisa destruí-lo em algum momento, é
uma regra básica! *Pensar nos detalhes fazem toda a diferença no uso de memória
e performance da sua SPA.

No Ember, sempre que você registrar qualquer evento em
[didInsertElement](https://guides.emberjs.com/v2.9.0/components/the-component-lifecycle/#toc_integrating-with-third-party-libraries-with-code-didinsertelement-code),
você deve destruí-lo corretamente sempre que o componente for destruído usando
[willDestroyElement](https://emberjs.com/api/classes/Ember.Component.html#event_willDestroyElement).

<script src="https://gist.github.com/aureliosaraiva/9d51cdcdfbb22b57c40b7878821014f5.js"></script>

No exemplo acima, parece que o registro do listener será destruído corretamente.
Porém temos um **bind** que fará duas referências diferentes, logo não será
destruído, pois não é o mesmo listener.

Confira o funcionamento correto do
[bind](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind)*:*

<script src="https://gist.github.com/aureliosaraiva/6df067237fb476ca658f53fa50a3d1a6.js"></script>

<span class="figcaption_hack">Exemplo de execução do bind</span>

A forma correta para destruir todos os listeners de uma vez é usar
*$(this.element).off(‘click’)*. A outra é usar a referência direta do listener a
ser destruído. Assim utilizamos exatamente a mesma referência de memória:

<script src="https://gist.github.com/aureliosaraiva/278a5d03dcb72755a69c9605a2a74c1a.js"></script>
<span class="figcaption_hack">Neste exemplo, **clickHandlerRef** recebe uma referência do metódo que será
vinculado, guardando-a para posteriormente ser destruído em
**willDestroyElement**.</span>

Essa abordagem é boa, porém pode aumentar a complexidade do código dificultando
a leitura e compreensão.

Isso é válido inclusive para todo e qualquer listener personalizado que você
registrar.

Quando um listener não é destruído, o elemento (nó) mantém uma referência para
todos os elementos internos. Na melhor das hipóteses, este será apenas um
vazamento de memória (*memory leak*), porém pode gerar outros problemas.

Próximo exemplo:
<script src="https://gist.github.com/aureliosaraiva/a415bc17d81c8aea1e36e328bc08238e.js"></script>
No código acima, o desenvolvedor pressupõem que todos os itens que correspondem
a **li.link** deveriam ter um listener para o evento de *click*. Porém, se esse
componente for utilizado duas ou mais vezes na mesma tela, esse listener para
**li.link** será duplicado. Durante a destruíção de um componente, neste caso,
ele vai destruir todos os listeners, incluindo os listeners do outro componente,
pois não foi definido um escopo de seleção.

Para resolver isso alguns desenvolvedores adicionaram identificação nos
listeners para contornar o problema de escopo.

```javascript
jQuery('li.linked').on(`click.${this.id}` ...

...

jQuery('li.linked').off(`click.${this.id}`);
```


Isso somente resolve o problema de destruição dos listeners, porém não resolve
os listeners duplicados.

A maneira correta de resolver isso é utilizar escopo do componente com
**this.$()** ou **$(this.element)** e usar o **find**. Além de resolver o
problema de listeners, evita que elementos fora do escopo do componente sejam
afetados.

```javascript
jQuery(this.element).find('li.link').on('click', ...
...
this.$().find('li.link').on('click', ...
```

## Erro 2: Uso de seletores globais

Existem diversos erros no uso de seletores, e aos poucos, temos erros compostos
de mais erros são criados. Vimos nos exemplos acima que nosso componente
involuntariamente acrescentou listeners duplicados em itens dentro de outro
componente.

Na prática a solução é definitivamente usar selector JQuery delimitado dentro do
escopo do componente. *Quando você ignora este conselho*, **você consegue
produzir bugs divertidos**.

Engraçado? Vou explicar a seguir!

Antes disso da uma olhada na documentação de
[element.getElementsByTagName](https://developer.mozilla.org/en-US/docs/Web/API/Element/getElementsByTagName)
e
[document.getElementsByTagName](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByTagName).

O retorno deles é um
[HTMLCollections](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection),
isso significa que é sempre atualizado quando ocorrer uma mudança no DOM:

> An HTMLCollection in the HTML DOM is live; it is automatically updated when the
> underlying document is changed.

O metódo
[getElementsByClassName](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
tem o mesmo comportamento.

Já
[querySelectorAll](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)
retorna [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList),
ou seja, NodeList é um retorno estático que não é modificado quando o DOM é
atualizado.

Veja dois exemplos de código (*habilite o console do seu navegador para ver o
log*)

[https://codepen.io/aureliosaraiva/pen/ObWbeM](https://codepen.io/aureliosaraiva/pen/ObWbeM)

[https://codepen.io/aureliosaraiva/pen/VmPmJJ](https://codepen.io/aureliosaraiva/pen/VmPmJJ)

Certo, o que isso tudo significa?

[JQuery](https://blog.jquery.com/2012/07/04/the-new-sizzle/) usa a lib
[Sizzle](https://sizzlejs.com/) para encontrar elementos no DOM. Sempre que
puder, ela vai utilizar esses seletores para se conectar aos elementos. Isso
tudo significa que quanto mais alto na hierarquia o *HTMLCollection* estiver
conectado, mais mudanças ele terá que observar e mais trabalho de processamento
ele irá realizar.

Quando você usa um seletor global para fazer alguma coisa, sempre que
*HTMLCollection* precisar atualizar, uma serie de processamentos são realizados
e diversas chamadas JQuery serão executadas.

Existem dois momentos críticos de performance em uma SPA: (1) quando ocorre uma
transição da rota A para a rota B, e (2) quando é realizada uma reciclagem para
reduzir a quantidade de elementos DOM na tela. Um único seletor JQuery
utilizando uma lista *HTMLCollection* é capaz de causar lentidão tornando sua
SPA instável.

## Erro 3: Caching de seletor JQuery

Existem diversos tutoriais de melhoria de desempenho que sugerem o armazenamento
em cache dos seletores JQuery. A sugestão não é errada, o problema é não ter um
controle para remover esse cache depois de utilizá-lo. Seletores em cache muitas
vezes fazem referência a elementos no DOM resultando em *memory leak*,
felizmente isso muitas vezes é temporário (até que o componente seja destruído),
mas dependendo de como e onde você fez o cache, o problema de *memory leak* pode
ser permanente.

## Erro 4: Uso de plugins JQuery

Imagine o seguinte, você está com um prazo curto, e você precisa criar um
recurso drag&drop, ou utilizar um carrossel ou até mesmo uma visualização
especial de imagem, etc. Você lembra que quando trabalhava só com JQuery, você
utilizava um JQuery Plugin para resolver o problema e sempre funcionava. Com
apenas uma chamada ele fazia tudo por você. Talvez alguém até já tenha criado um
addon no Ember para ser instalado.

Poucos dias depois de começa a utilizar surgem as primeiras falhas: minha SPA
não está respondendo. O número de erros aumenta, lentidão, *memory leak* e tudo
fica fora de controle.

Você já usou este plugin mil vezes, o que aconteceu?

Eis o que aconteceu.

## O mundo não é mais o mesmo!

Por mais de uma década, desenvolvedores de JavaScript foram capazes utilizar
diversos plugins JQuery para resolver problemas em curto espaço de tempo. A
maioria dos plugins JQuery não foi construído pensando em uma SPA.

No passado, os desenvolvedores não precisavam pensar na destruição do DOM e dos
event listeners. Um plugin/biblioteca era instanciado no carregamento da página
e existia até o momento que ocorria uma atualização completa ou um nova página
era chamada.

Este código não está preparado para páginas web dinâmicas, e tão pouco essa
situação vem sendo corrigida pelos mantenedores. Porque se importar então? O
padrão plugin é um conceito morto, componentes e frameworks baseados em
componentes tem contribuído para isso nos últimos anos.

A probabilidade do seu plugin JQuery favorito não ter um processo de limpeza do
DOM é alta. Como mencionado acima, seletores com *HTMLCollection* são perigosos.
Quais desses o plugin utilizam? Como é o cache de seletor?

Os vazamentos de memória e problemas de performance estão em toda parte, o uso
de dois ou três plugins combinados podem trazer diversos problemas.

É importante sempre verificar se o plugin/biblioteca implementam *destroy*,
*teardown* ou *cleanup* (ou algo semelhante) e verificar se elas são executadas
corretamente quando se está destruíndo o componente. Mesmo os plugins/biblioteca
que implementam esse recurso, nem sempre fazem um trabalho bem feito. Portanto,
o seu único recurso é implementar e, em seguida, se certificar (com uso de
profiling) de que nenhum *memory leak* ficou pendente.

## Conclusão

Problemas com event listeners e seletores não são os únicos causadores de
instabilidade. Desenvolvedores estão viciados em suas rotinas de trabalho e
esquecem de dar atenção aos detalhes, ou até mesmo de buscar mais informações de
como as APIs funcionam.

Como resolver esses problema?

Você pode monitorar, estudar o código do plugin/biblioteca, se houver essas
falhas, você pode sugerir um Pull Request e contribuir com a comunidade. No
final todos ganham!

## Comunidade EmberJS no Brasil

* Esse texto é parte de uma iniciativa da comunidade *[EmberJS Brasil](https://github.com/EmberJSBrasil)*, que busca disseminar conteúdo sobre
* [Ember](https://emberjs.com/), que seja de qualidade, autoral ou traduzido.
Siga nosso *[Twitter](https://twitter.com/emberjsbrasil)*! 
* Participe da comunidade global de Ember no [Slack](https://ember-community-slackin.herokuapp.com/)! 
* E acesse o canal: [#lang-portuguese](https://ember-community-slackin.herokuapp.com/)!


