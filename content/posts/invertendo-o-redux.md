---
title: Invertendo o Redux
author: Javiani
type: post
date: 2016-09-09
url: /invertendo-o-redux/
titulo_personalizado:
  - 'Invertendo o <strong>Redux</strong>'
categories:
  - Código
  - Destaques
  - JavaScript
  - Técnicas e Práticas
tags:
  - front-end
  - JavaScript
  - redux

---
## Introdução

&nbsp;

Já faz um tempo desde que implementei pela primeira vez o [Redux][1]. Numa época que só se falava nos frameworks, ele apareceu do nada, pelo menos para mim. Eu já conhecia o Flux, mas ainda não era o que estava procurando. O **Redux** realmente é uma das melhores idéias que vi, para mim faz todo o sentido e ainda é simples de entender e de se implementar.

Depois de usá-lo algumas vezes você precisa se policiar para não se ver usando esta arquitetura em todos os projetos e virar um pregador da arquitetura. A idéia deste post é apresentar alguns aspectos que aprendi usando este padrão, ter um olhar mais crítico apesar do entusiasmo, e apresentar uma proposta um pouco diferente que pode lhe ser útil em alguma situação.

## Uma visão crítica

&nbsp;

Como havia dito, apesar de todo o amor que se pode ter por uma solução, é preciso um pouco de maturidade e entender que tudo o que você gosta possui contras, pontos negativos. Ter consciência disso pode te ajudar a tomar uma decisão melhor quando possui diferentes soluções parecidas para um determinado problema. Te ajudará também a saber quando dar mais atenção aos contras quando estes podem ser mais prejudiciais do que os benefícios dos seus prós. Isso te fará ser mais lúcido, mais racional, tomará menos decisões com natureza emocional. Com isto dito, vamos à alguns pontos sobre o **Redux** sob minha perspectiva.

  1. **Redux** não é para todas as aplicações, é claro. Me vi em alguns projetos que não eram dos mais complexos, mas também não eram tão simples, nestes casos, a implementação do **Redux** parece ser demais, um over-engineering, em português claro, um canhão para matar um mosquito.
  2. Todos os reducers tem um grupo de switch cases que testam o tipo de ação disparada. Estes reducers podem ficar incrivelmente grandes além de ser difícil saber de forma rápida e prática, quais reducers respondem uma determinada ação. Para saber isso você deve abrir cada arquivo do _reducer_ para descobrir.
  3. A composição dos reducers pode ser um pouco complicada às vezes de se entender. Principalmente para que está iniciando.
  4. Em algumas situações você vai preferir que o relacionamento entre as ações e os reducers fosse mais direta, mais simples.

## Metodologia

&nbsp;

Resumidamente, o Redux funciona alterando as propriedades de um único objeto que armazena todo o estado de sua aplicação, utiliza funções puras ( _reducers ) _para aplicar mudanças nestes estados de acordo com uma determinada ação.

Os tipos das ações são imutáveis, ou seja, são constantes é por isso são usadas strings em _uppercase. _

Pensando em uma alternativa,  removi os tipos das ações de dentro dos reducers, e coloquei no contexto da minha Store. No Redux você pode executar vários reducers para uma mesma ação, mas não pode disparar várias ações usando um reducer.

Então,  a conclusão que tirei é que posso escrever os tipos das ações como métodos de um objeto. A vantagem disso é que especifico todos os reducers que quero executar para cada um destes métodos, resolvendo o **item 2.** É fácil enxergar qual _reducer_ é executado numa ação disparada e como efeito colateral eu resolvo o **item 3** também, pois a composição entre reducers é direta.

A lógica no final é: Ao invés de executar _n_ reducers que vão testar todos os tipos das ações, eu faço isso de maneira **inversa**, eu testo apenas a ação, se esta ação existir no meu objeto, então executo os _n_ reducers. Por isso chamei esse formato de _**Inverted Redux**_.

## IRedux Store

&nbsp;

Com esta lógica em mente, foi só necessário escrever o código que comprove a eficácia ou não da hipótese do Inverted Redux. Para meu espanto foi ridiculamente simples. Para simplificar ainda mais por questões de didática, vou partir do princípio que esta nova Store receberá um objeto que implementa o padrão [publish/subscribe][2] ( _que é um padrão bem simples de se implementar_ ).

Esta é a implementação final desta Store:

<pre>export default ( pubsub, state ) =&gt; {
        let Store = {
            getState(){
                return state
        },
            subscribe( callback ){
                pubsub.subscribe('store:update', callback)
            },
            dispatch( action ){
                pubsub.publish('store', action)
            }
        }
        pubsub.subscribe('store', ( payload ) =&gt;{
            if( payload.type in Store ){
                var newstate = Store[ payload.type ].call(null, state, payload );
                pubsub.publish( 'store:update', newstate );
            }
        });

    return Store
}

</pre>

## Reducers

&nbsp;

Com esta mudança, os reducers ficaram muito mais simples do que a versão com os _**switch cases**,_ ficando mais fácil de entender, de compor e de reutilizar também.

Eu prefiro exportar um objeto contendo os meus reducers agrupados por um contexto em comum. Para exemplificar, vou criar aqui um objeto com as tarefas de **adicionar**, **remover** e **editar** itens de uma lista.

<pre>export default{

    add( state = [], action ){
        return [...state, {
            text :action.item,
            id   :(Math.random() * Math.pow(10, 20))
        }]
    },

    remove( state = [], action ){
        return state.filter( item =&gt; item.id != action.id )
    },

    edit( state = [], action ){
        return state.map( item =&gt; {
            if( item.id == action.id )
                return { id : item.id, text : action.text }
            else
                return { id : item.id, text : item.text }
        })
    }
}

</pre>

Neste formato a principal diferença é que os reducers não testam as ações, apenas se preocupam no tratamento dos dados que lhe são passados.

## Juntando as peças

&nbsp;

Bom, o resultado final ficou bem simples, considerando que você já tem sua implementação do Inverted Redux e tem os seus reducers prontos, a junção da instância da sua Store com os reducers se dá da seguinte forma:

<pre>import store from 'Iredux'
import Pubsub from 'Pubsub'
import reducersList from 'reducers/list'

let AppStore = store( Pubsub, {
    produtos :[]
})

AppStore.subscribe( state =&gt;
    console.log( 'AppStore.State', state )
)

AppStore.ADD = ( state, action ) =&gt;{
    state.produtos = reducersList.add( state.produtos, action )
}

AppStore.REMOVE = ( state, action ) =&gt;{
    state.produtos = reducersList.remove( state.produtos, action )
}

AppStore.EDIT = ( state, action ) =&gt;{
    state.produtos = reducersList.edit( state.produtos, action )
}

</pre>

Os métodos representam os tipos das ações do Redux, usei a mesma convenção de constantes, usando os nomes em _uppercase_. Sua Store além de ter os métodos `dispatch()`, `subscribe()` e `getState()`, ainda contém estes métodos que serão executados no disparo de uma ação.

Esta mudança me ajudou não só na visualização, pois você facilmente consegue identificar quais ações sua Store possui, como também na hora de compor os reducers. Posso também disparar um evento de remoção passando apenas o id, sem a necessidade de passar a lista ( de produtos no meu caso ) na hora de criar uma ação:

<pre>import PubSub from 'PubSub'

$(document.body).on('click', '.remove-item', (e)=&gt;{
    let id = e.target.id
    PubSub.publish('store', { type:'REMOVE', id })
})
</pre>

No caso do código acima, eu usei o Singleton PubSub para publicar `store` , passando apenas o id, porque no arquivo da minha Store propriamente dita, eu já mando o estado `produtos` que sempre será uma lista conforme meu reducer `edit` espera.

Assim que a minha Store tiver executado todos os reducers ela disparará novamente outro evento global para meu pubsub, o `store:update` . Diferente do Redux, eu preferi sempre enviar o estado da minha aplicação para receber como argumento na hora de registrar um callback, porque eu vi que sempre tinha de executar o método .getState() e tava ficando redundante.

<pre>AppStore.subscribe( state =&gt;
    console.log( 'AppStore.State =&gt;', state )
)
</pre>

Ao usar este padrão, percebi também que em alguns casos eu sempre repetia as mesmas chamadas dos reducers em diferentes ações, isso deixava o código meio duplicado e redundante. Mas a solução foi novamente muito simples, bastava criar um reducer intermediário, um middleware, que executava todos os reducers que precisava para uma determinada ação. Passei por isso pela primeira vez quando implementei uma aplicação `todomvc` para testar os conceitos, criei um reducer chamado `common` :

<pre>import r from 'stores/reducers/todos'

export default ( store )=&gt;{

    let common = ( state, action )=&gt;{
        state.items     = r.filter( state.todos, { filter : state.filter } )
        state.remaining = r.remaining( state.remaining, { todos: state.todos } )
        return state
    }

    store.ADD = ( state, action ) =&gt;{
        state.todos = r.add( state.todos, action )
        return common( state, action )
    }

    store.REMOVE = ( state, action ) =&gt;{
        state.todos = r.remove( state.todos, action )
        return common( state, action )
    }

    store.UPDATE = ( state, action ) =&gt;{
        state.todos = r.update( state.todos, action )
        return common( state, action )
    }

    store.TOGGLE = ( state, action ) =&gt;{
        state.todos = r.toggle( state.todos, action )
        return common( state, action )
    }

    store.TOGGLE_ALL = ( state, action ) =&gt;{
        state.todos = r.toggle_all( state.todos, action )
        return common( state, action )
    }

    store.EDIT = ( state, action ) =&gt;{
        state.todos = r.edit( state.todos, action )
        return common( state, action )
    }

    store.CANCEL = ( state, action ) =&gt;{
        state.todos = r.cancel( state.todos, action )
        return common( state, action )
    }

    store.CLEAR = ( state, action ) =&gt;{
        state.todos = r.clear( state.todos, action )
        return common( state, action )
    }

    store.FILTER = ( state, action )=&gt;{
        state.filter = action.filter || 'all'
        return common( state, action )
    }
}
</pre>

Deixei o `common`  ali para ficar mais claro de entender o que ele faz, poderia muito bem ter colocado dentro do objeto que contém todos os reducers relacionados à minha lista de Todo&#8217;s e referenciá-lo como fiz com outros métodos. Ali dá para ver que eu atualizo os estados `items` e `remaining` , e passo normalmente para estes reducers actions customizadas, enviando dados que meus reducers sempre esperam.

Claro, é possível perceber logo de cara que o arquivo da sua Store vai crescer, você pode resolver isso movendo estas ações para outro arquivo, e mandando sua store como parâmetro:

<pre>import Pubsub from 'Pubsub'
import store from 'Iredux'
import actions from 'stores/actions'

let AppStore = store( Pubsub, {
    produtos :[]
})

AppStore.subscribe( state =&gt;
    console.log( 'AppStore.State', state )
)

// @Actions
actions( AppStore )</pre>

Neste arquivo `stores/actions` eu exporto uma função que recebe a store e faz o registro de todas as ações que esta store deve ter. Aí a organização com relação à estrutura de pastas e a lógica como isso vai se dar, depende de você e também da sua aplicação.

## Conclusões

&nbsp;

Eu fiquei bastante surpreso com o resultado disso na prática. Há projetos onde criar todos os componentes usando **Redux** ou mesmo o _Inverted Redux_ é loucura, principalmente porque muitos componentes acabam trabalhando bem sozinhos, são stand-alone, e não precisam estar num flow mais complexo de relacionamento.

Na prática, no mundo real, há uma necessidade de se analisar quais estados realmente devem estar em sua Store. Alguns componentes apenas precisam resolver problemas de UI, ou validação, não implicando em um relacionamento mais complexo entre as partes. Você não deve criar toda uma arquitetura Redux, Flux ou qualquer que seja, se sua página apenas contém um formulário que faz um post para uma outra página depois de uma validação simples, ou mesmo ao desenvolver um sticky header.

Muitas vezes você se depara com soluções do mercado e não sabe se é ou não uma solução otimizada para o seu projeto. Pense que muitas soluções do mercado estão focando nos problemas das **Single Page Applications**, e fazem isso com toda a razão pois _SPA&#8217;s_ são difíceis de se desenvolver e mais difícil ainda é criar uma aplicação neste formato com fácil manutenção. Porém há um nicho muito grande que são as páginas que possuem ajax, possuem uma forma um pouco mais rica na interface, mas que não podem ser consideradas totalmente _SPA&#8217;s_. Você não deve desprezar  ou subestimar estas aplicações, grandes dores de cabeça costumam vir de onde menos se espera.

Ao meu ver existe uma supervalorização do verbo &#8220;**escalar**&#8221; no contexto do desenvolvimento front-end. Vejo muitas soluções serem vendidas utilizando o argumento de que você deve usar isto ou aquilo pois caso contrário sua aplicação não irá escalar. Nenhuma solução é ótima por si só, não há regras inquebráveis e todas elas dependem de um contexto. É por este motivo que escolher um Framework A ou B, ou um padrão C ou D não será suficiente para que sua aplicação escale. É necessário mais que isso, experiência, boas análises de requisitos, funcionalidades e especificações, refactories constantes, organização etc. Portanto, não é um caminho simples.

A minha intenção com este post, além de compartilhar minhas experiências, é mostrar que o Redux abriu minha mente, minha forma de pensar, fez com que eu voltasse a pensar fora da caixa. Deve servir como solução mas também como uma inspiração, uma forma de te motivar à pensar em outras soluções, à questionar as que já tem, a seguir em frente estimulando sua criatividade.

Até a próxima, um grande abraço.

 [1]: http://redux.js.org/
 [2]: https://davidwalsh.name/pubsub-javascript