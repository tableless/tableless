+++
authors = "Igor Octaviano"
categories = ["javascript", "reactjs"]
date = "2018-09-17T08:08:00+00:00"
publishdate = "2018-09-17T08:08:00+00:00"
excerpt = "Desmistificando o limiar entre JavaScript e React."
image = "https://i.imgur.com/78BBavz.jpg"
tags = ["reactjs"]
title = "(React + this + bind) = só sei que é assim"
type = "post"
+++


## Desmistificando o limiar entre JavaScript e React

**Só sei que é assim** agora é passado! vamos conhecer melhor esses recursos e
como eles podem influenciar na performance quando você desenvolve aplicações em
React.

Em um componente React você pode definir métodos de classe e então os utilizar
no método `render` de seu componente. Exemplo:

    class
     extends React.Component {

    () {
        console.dir(this); // "this" é quem vai chamar o método risada
        return "HAHAHAHA!!!";
      }

      render() {
        return
    ;
      }
    }

    ReactDOM.render(<
    />, document.getElementById('root'));

Nesse exemplo utilizei o método `risada` dentro do método `render` como
`this.risada` porque dentro do `render`, a palavra-chave `this` refere-se à
instância do componente associado com o elemento da DOM que representa esse
componente.

Internamente o React vai garantir de que aquele “`this`” dentro de seus métodos
de classe se refere à instância. Embora o JavaScript não vincula a instância
automaticamente quando você usa uma referência para o método `risada`.

A linha`console.dir` no método`risada` vai mostrar corretamente a instância do
componente porque aquele método foi chamado diretamente do método `render`
especificando o chamador explícitamente (`this`). Você poderá ver o objeto
`RisadaCruel` no console quando você executar o código abaixo:

![](https://cdn-images-1.medium.com/max/1000/1*fJ2RuHAoypEU2iCGVTuh-A.png)

Acontece que quando você usa o mesmo método em uma situação em que esse método
não vai ser executado instantaneamente como um event handler da vida, "quem" irá
chamar aquele método não vai mais ser explícito e a linha do `console.dir` não
vai reportar a instância do componente como antes.

![](https://cdn-images-1.medium.com/max/1000/1*Xue25y2pX7dD-sCBQn9Tuw.png)

No codigo acima o React invoca o método `evento` quando você clica na string,
mas não lhe dará acesso à instância do componente dentro dela fazendo com que
você receba um `undefined`na sua cara quando você clicar na string. Esse é um
problema se seu método de classe precisa ter acesso a coisas como `this.props` e
`this.state`. Isso simplesmente não irá funcionar do jeito que você imagina.

Calma, existem varias solucoes para esse problema. Você pode abraçar o método em
uma função inline ou usar a chamada `.bind` para forçar o método a lembrar quem
o chamou. Essas são soluções ok se seus componentes não são atualizados tão
frequentemente. Você pode também otimizar o método `bind` do JavaScript chamando
ele lá no construtor da classe do seu componente ao invés de fazer isso no
método `render` que é chamado constantemente.

![](https://cdn-images-1.medium.com/max/1000/1*NatVKCvaXgtncrzHusaXfw.png)

Agora você pode estar se perguntando… Mas pera ai, porque eu faria isso? não
entendi nada! E eu lhe diria em seguida.. Sim, isso seria totalmente normal meu
caro aventureiro, vamos entender isso melhor!

## Entendendo um pouquinho de otimização em React

Imagine a situação em que você esteja passando funções/eventos com a chamada
`.bind` visando definir uma ação para os botões de cada item de uma lista que
você esteja criando lá dentro do metodo `render`. Acontece que em JavaScript,
quando o método `bind` recebe o seu primeiro argumento `this` em sua chamada,
isso é justamente para definir explicitamente quem chamou aquela função, ou
seja, o contexto no qual você quer que essa função seja executada. Assim o
método `bind` retorna uma função novinha em folha que retorna uma chamada a sua
função original forçando esse `this`, ou seja, fazendo com que a função original
reconheça quem for que seja o argumento `this` como quem a chamou,
consequentemente quem é o seu contexto de chamada. Como seria essa função na
vida real?

2 exemplos simplificados da implementação da função `bind`:


    function
    (algumaFuncao, algumThis) {
        return function() {
            return algumaFuncao.apply( algumThis, arguments );
        };
    }

     objetoLegal = {};
     algumaFuncao = function() {};
     funcaoLegal = bind(algumaFuncao, objetoLegal);
    // funcaoLegal agiria como se fosse: objetoLegal.algumaFuncao();


    Function.prototype.
     = function(algumThis) {
        return function() {
            return this.apply(algumThis, arguments);
        }
    };

     objetoFamoso = {};
     algumaFuncao = function() {};
     funcaoFamosa = this.algumaFuncao.bind(objetoFamoso);
    // funcaoFamosa agiria como se fosse: objetoFamoso.algumaFuncao();

* A implementação oficial do método `bind` é muito mais sofisticada do que isso.
* Existem dois métodos para definição explícita de contexto em JavaScript, o
método `call` e o `apply` que vieram antes do método `bind` com o advento do
ES6.
* A diferença entre o método `call` e o `apply` é que o `apply` lhe deixa chamar a
função com o parâmetro `arguments` sendo um array tipo
`algumaFuncao.apply(algumThis, arrayDeArgumentos)`. Já o `call` você terá que
chamar com os parâmetros explicitamente separados por vírgulas tipo
`algumaFuncao.call(algumThis, arg1, arg2, ...)`. Uma mnemónica útil para
entender a diferença entre esses dois métodos é “**A** para array e **C** para
comma.”.** Créditos por essa explicação para
**[flatline](https://stackoverflow.com/questions/1986896/what-is-the-difference-between-call-and-apply)**.**
* Use o método `bind` quando quiser que essa função seja chamada posteriormente
com um determinado contexto. Use `call` ou `apply` quando você quiser invocar a
função imediatamente modificando ou forçando o contexto.

## Uhum, depois disso tudo que você escreveu ainda nao sei o que que isso tem haver
com otimização!

![](https://cdn-images-1.medium.com/max/600/1*wUziNc_YXExdynhe3_5YWQ.png)
<span class="figcaption_hack">Tyler The Sloth by allheartsgoboom</span>

Acontece que em JavaScript objetos complexos como as funções são instâncias
diferentes e possuem identidades diferentes, sendo assim a verificação de
igualdade superficial que o React faz entre os componentes sempre produz
resultado falso, ou seja, sempre resulta em diferença! 😨

Isso faz com que o React renderize novamente esses componentes que receberam
essa função novinha e única (em termos de referência) que foi criada toda vez
que o método `bind` foi chamado naquele evento dentro do método `render` do
componente.

A mesma coisa acontece se ao invés de utilizar uma função você esteja passando
um `array` para cada item dessa lista no `render`, porque em JavaScript, o
literal `array` é a mesma coisa que chamar `new Array()`que cria uma nova
instância (única em termos de referência) de um `array`. Isso destrói (muito
trágico) completamente toda otimização de renderização pura do React!

Outra situação onde uma função novinha é criada no `render` causando essa coisa
toda que eu falei:

    class
     extends PureComponent {
      render() {
        return <
          onChange={e
     this.props.update(e.target.value)} />;
      }
    }

Isso mesmo, essa [arrow
function](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
é de fato uma função que não foge a regra, nesse caso vai ser também uma
entidade única para cada `Input` como mostra o caso acima. É interessante saber
dessas coisas né? já fiz “errado” muitas vezes! mas calma lá em, esse errado na
verdade é um pseudo errado porque cada caso é um caso e na maioria das vezes a
performance não vai ser um ponto crítico para você. A não ser, é claro, que seja
o caso de uma lista gigante, animações, etc. Enfim, se seu componente atualiza
constantemente.

## Voltando ao exemplo do nosso componente RisadaCruel

Uma melhor solução para esse método **atualmente** é habilitar o recurso de
class-fields (campos de classe) do ECMAScript (no qual esta em stage-3) através
do Babel e simplesmente utilizar uma arrow function para os handlers:

    class RisadaCruel extends React.Component {


    render() {
        return (
         <div onClick={
    }>
            Hello World
          </div>
        );
      }
    }

> **Nice! mas pera ai, habilitar o recurso de class-fields em** stage-3**? Como é
> que é esse stage aí?**

No TC39, o comitê que desenvolve o JavaScript no qual seus membros são empresas
(entre outros camaradas como também todos os principais fornecedores de
navegadores) e cada proposta de um recurso para a linguagem passa por vários
estágios de maturidade, começando pelo estágio 0. O stage-3 ou estágio 3 que foi
mencionado anteriormente, significa que a proposta de tal recurso está
praticamente finalizada e agora precisa de feedback de implementações e usuários
para progredir ainda mais. Mais detalhes do TC e dos outros estágios
[aqui](https://2ality.com/2015/11/tc39-process.html).

## fecharPost.bind(this);

É isso aí pessoal! espero ter desmistificado um pouco do limiar entre o que é
realmente JavaScript do que é realmente coisa do React e também como o React se
comporta com o uso "as vezes" inadequado do JavaScript em uma aplicação React. É
sabendo um pouco mais da ferramenta que utilizamos que podemos escrever
aplicações ainda melhores e mais performáticas.

## Fim!!!

E valeu por ter chegado até aqui! 🤓

Está interessado ou já é explorador do mundo React? dê uma olhada no meu outro
post sobre tutoriais fantásticos e onde habitam!
