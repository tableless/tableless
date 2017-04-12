---
title: A arquitetura Redux usando Jails
author: Javiani
type: post
date: 2016-04-18
url: /arquitetura-redux-usando-jails/
titulo_personalizado:
  - 'A arquitetura Redux <strong>usando Jails</strong>'
categories:
  - Código
  - Destaques
  - JavaScript
tags:
  - desenvolvimento
  - desenvolvimento web
  - JavaScript
  - padroes web
  - redux

---
Ultimamente tenho me preocupado mais com arquiteturas no front-end do que propriamente com as implementações de alguns frameworks. Isso porque eu acho que realmente nos falta um pouco mais de conhecimento sistêmico, mais arquitetural, porque os problemas só estão crescendo e percebi que pelo menos eu não estava acompanhando devidamente a complexidade das aplicações desenvolvidas em Javascript.

## Uma pequena reflexão

Os frameworks acabaram aparecendo nos últimos tempos e percebo que tiveram uma importância muito maior do que o nosso amadurecimento quanto aos novos desafios nas aplicações web, especificamente na linguagem Javascript. Percebo por comentários de colegas que em entrevistas a preocupação com o conhecimento em determinados frameworks é maior do que a preocupação com o pensamento abstrato do programador Javascript.

Eu acabei escrevendo um micro-framework, já postei ele aqui, o **<a href="http://tableless.com.br/jails-o-framework-e-arquitetura-javascript/" target="_blank">Jails</a>**. Que nada mais é do que uma aplicação de um conceito de relacionamento entre as partes, uma micro-arquitetura baseada em eventos, com alguns padrões, bem simples. Ao invés de vir de fábrica lotada de features, ela apenas resolve o problema básico de **organização.**

## O Problema principal e o secundário

O **Jails** não resolve todos os problemas, aliás, não deve e se devesse, não conseguiria. Eu particularmente acredito que quanto mais simples uma solução for, mais &#8220;composable&#8221; ela vai ser, e se possui componentes que podem ser compostos, sua aplicação tende a ser mais simples e mais otimizada para o seu problema inicial.

Menos tempo também se perde com manutenção de soluções que não estavam no escopo inicial. Aqui entra o velho conceito de divisão e conquista, para um problema complexo, o mais inteligente a se fazer é resolvê-lo quebrando-o em partes menores. O Jails melhorou bastante a organização e a forma de abstrair as coisas para mim sobretudo na reutilização do código, eram estes os problemas iniciais.

Existe porém um problema secundário, como manter a previsibilidade dos estados de uma aplicação? Um exemplo, o usuário escolhe uma opção em um dropdown, outro componente precisa ser atualizado de acordo com esta opção, em conjunto, um terceiro componente precisa atualizar o texto, e um quarto componente deve mostrar na UI algo que tem relação com a escolha feita no primeiro componente, e todos eles estão de forma espalhada na tela, não são portanto um conjunto de um mesmo módulo.

Quer dizer então que o Jails não resolve este problema? Claro que não, e isto não significa que é um problema sem solução. Com framework ou sem você vai resolver esse problema. A questão aqui não é apenas resolvê-lo, é como solucionar de maneira **elegante**, usando uma forma que não comprometa a sanidade do seu código. Isso te ajuda diretamente na manutenção e consequentemente a ser mais ágil quando tiver que fazer alterações ou mesmo criar novas features.

## Redux, a predictable state container

Aqui entra um dos conceitos mais interessantes que vi nestes útimos tempos, não me parece ter recebido tanta atenção quanto deveria, mais é genial, pelo menos para mim. Bom, como o título sugere, ele é basicamente um container de estados para sua a aplicação, ele simplifica a arquitetura Flux, adiciona para nós alguns conceitos como reducers, imutabilidade e funções puras.

A idéia geral dele é, que você tenha apenas uma **Store **que mantêm todos os estados da sua aplicação, e para cada ação do usuário você deve disparar uma &#8220;action&#8221; para esta store que por sua vez vai atualizar os estados e te notificar que esta atualização finalizou, assim, ao ser notificado você resgata estes estados que são read-only e atualiza seus componentes. As mudanças nestes estados devem ser feitas apenas usando funções puras chamadas de &#8220;reducers&#8221;.

Há um tempo atrás, quando ainda estava desenvolvendo o Jails, eu já havia notado que em alguns casos seria interessante manter os estados da aplicação em um objeto, fazendo estas alterações neste objeto usando métodos de array como filters, map, reduce para listas, e posteriormente atualizado a view usando um template engine, mustache por exemplo. Uma prova disso é que hoje, as apps e as controllers do Jails compartilham um objeto **data** entre eles com esta finalidade.

<pre class="lang-javascript">import 'components/view'
import jails from 'jails'
jails.app('app', function(html, data){
	this.init = ()=&gt;{
		let view = this.x('[data-component*=view]')
		view('render', data)
	}
})
</pre>

E foi desta forma que resolvia estes problemas de estado da aplicação, mas que possui uma consequência. Não era trivial saber quando ou quem havia alterado aquele objeto. É o clássico problema da variável global, você não consegue dizer com facilidade qual ação foi responsável por uma mudança.

Outro problema é que objetos não são funções, não há callbacks. Você não consegue dizer à outros módulos que houve uma alteração neste objeto. Aí você vai se sentir tentado a usar aquelas manobras de watch, observer, two-way binding ou seja lá qual for o nome que dê para isso, para te alertar quando o objeto é alterado.

Hoje já temos bastante informação sobre estas técnicas e sabemos que é difícil verificar de forma recursiva se alguma propriedade do objeto alterou e não é performático.

É por isso que acho o Redux genial, ele utiliza alguns conceitos do paradigma funcional que resolve de maneira elegante este problema e tem esta idéia de preservar os estados da aplicação em um objeto só, que pra mim por dedução é algo interessante a se fazer hoje em dia, além disso nos garante um mínimo previsibilidade. O Redux usa o conceito de funções puras para alterar os estados e estas funções por serem puras são facilmente passíveis de composições e também são previsíveis. E o melhor, não está preso à implementação do React, é um padrão/arquitetura, um conceito que você pode usar **ONDE VOCÊ QUISER**. Você prefere AngularJS? Ember? Js Vanilão? React? Não importa, e essa qualidade para mim não tem preço.

## Não seja um robô, pense por conta própria&#8230;

Já vi lutas ferrenhas sobre qual framework/solução usar, existem aquelas pessoas que são realmente evangelistas no sentido mais religioso, aprendem a usar alguma ferramenta e aquela é a única que presta, a única que irá salvar à todos&#8230; Você já deve ter conhecido alguns destes pregadores de tecnologias certo? Bom, se eu pensasse da mesma forma, diria que deve seguir e usar o Redux em todas as suas aplicações e seguir de forma &#8220;strict&#8221;, usando EXATAMENTE como foi concebida.

A experiência dos erros que cometi me diz o contrário, não há uma solução que seja ótima para todos os problemas, e é aí que entra o propósito do meu post, só agora posso esclarecer isso.

Existem muitas outras fontes que ensinam de forma muito mais didática sobre o Redux, screencasts do próprio desenvolvedor que concebeu este conceito e uma documentação completa no github. Não faz sentido repassar estas informações que já estão disponíveis na web.

Meu intuito é passar um pouco do aprendizado e experiência que eu tive **usando** e **adaptando** o Redux. Talvez isso seja útil para você que trabalha com Backbone, Angular ou qualquer outro framework. Pense no seu projeto, pense nas pessoas que vão trabalhar nele, pense no quão complexo ele é ou vai ser. Use sua criatividade para adaptar algo no conceito quando ele está verboso demais, complexo demais ou quando não serve exatamente da maneira como foi concebido, o meu conselho é que não lute para fazer com que ele &#8220;caiba&#8221; no seu projeto exatamente como é, pense por conta própria também.

## A implementação e mudanças

Para experimentar este conceito novo para mim, implementei um Todo List, não tão complexo quanto o [TodoMVC][1], serviu apenas para poder fixar as idéias. As primeiras mudanças que fiz foi remover os **actions creators** e as **constantes**. Actions creators são funções que criam as actions (objetos) que são usados como informações pela Store. Uma action também possui uma propriedade **type **que armazena qual o tipo de ação, ela é uma string e portanto na documentação oficial ela é referenciada através de uma constante.

<pre class="lang-javascript">function addTodo( text ){
	return{
		type :ADD_TODO,
		text
	}
}
</pre>

Há alguns motivos pelos quais tanto as constantes quanto as actions creators existem, principalmente em projetos muito grandes, o motivo mais óbvio é que essa granulação ajuda caso seja necessário alterar por exemplo o nome de uma constante, ou adicionar propriedades em uma action sem que seja necesário revisitar todos os lugares onde se usam as constantes ou as actions.

Mas no meu caso o projeto é pequeno, e a consequência disso é que ao invés de ajudar isso acaba atrapalhando um pouco na manutenção. Se o projeto é pequeno e possui apenas um lugar onde estas actions existem, este processo acaba tornando sua arquitetura burocrática desnecessariamente, você força o programador a alterar várias partes diferentes da aplicação ainda que a mudança seja algo muito simples, costumamos chamar isso de _over engineering_.

No **Jails** a controller é como um módulo fechado, que controla os eventos. Para uma _todo_ list, o processo de adicionar _todos_ ou_ _remover _todos_ só fará sentido neste módulo ( neste meu projeto ). Portanto, não preciso dar tantas voltas:

<pre class="lang-javascript">import 'components/riot-view/riot-view'
import 'components/submitter/submitter'

import jails from 'jails'
import store from 'stores/todos'

jails.controller('todos', function(){

	const view = this.x('.view')

	this.init = ()=&gt;{

		this.on('blur', 'li .form-control', save)
		this.on('click', '.remove', remove)
		this.listen('submitter:post', add)

		//...
	}

	function update( state = todos.getState() ){
		view('update', state )
	}

	function save( id, text ){
		let id = +e.target.title,
			text = e.target.value
		if ( text ){
			store.dispatch({ id, text, type :'UPDATE_TODO' })
		}
	}

	function add( e, opt ){
		let form = e.target,
			text = opt.params.text.trim()
		if( text ){
			store.dispatch({ text, type :'ADD_TODO' })
		}
	}

	function remove( e ){
		let id = +e.target.title
		store.dispatch({ id, type :'REMOVE_TODO' })
	}
        //...
})


</pre>

Um pouco mais direto&#8230;  Como podem ver no código, o Jails abstrai a parte de eventos do DOM, e interpreta qual é a ação executada pelo usuário e delega a action para o módulo **store**. Aí estão algumas ações que a minha todo list espera, como adicionar um todo, remover e salvar.

## A Store

A minha store é bem simples para este caso, não precisei fazer mudanças drásticas, o modelo da documentação já me serviu, as mudanças apenas são de forma estrutural por causa do framework que eu utilizo:

<pre class="lang-javascript">import Reduxtore from 'modules/reduxtore/reduxtore'
import storage from 'modules/storage/storage'
import reducer from 'reducers/todos/index'

export default (()=&gt;{

	let list, store

	list = storage.session.get('todos') || []

	store = new Reduxtore( reducer, {
		filter	:'all',
		todos 	:list,
		items	:list
	})

	store.subscribe(()=&gt;{
		storage.session.set('todos', store.getState().todos )
	})

	return store
})()
</pre>

Aqui está a definição da store da minha aplicação, eu importo um módulo AMD que abstrai o processo de local storage, para poder salvar o estado da aplicação, importo um reducer que será passado como parametro para minha store, e também defino o estado inicial e os campos que minha aplicação deve conter.

A classe Reduxtore é apenas uma implementação que fiz em AMD do conceito de Store do Redux, seguindo a especificação, possui os métodos .**getState()**, .**dispatch()** e **subscribe()**. Na especificação existem outros métodos, mas estes para mim por enquanto são suficientes.

Toda vez que quero disparar uma ação utilizo .**dispatch()**, o callback de uma alteração de estado é registrado pelo método .**subscribe()** e sempre que quiser resgatar o estado atual da aplicação, utilizo .**getState()**. No meu caso, a minha store salva os dados no local storage e resgata-os assim que inicia.

## Reducers e Funções puras

Se a Store é responsável por manter e armazenar o estado da minha aplicação, você deve se perguntar quem faz as alterações nos estados. Eu havia dito anteriormente que são os reducers, o nome pode assustar um pouco porque podemos fazer algumas assunções, mas a grosso modo, são apenas funções puras, que recebem um estado como primeiro parâmetro e uma &#8220;action&#8221; como segundo parâmetro.

De forma bem grosseira, funções puras são aquelas do tipo f(x, y) => x + y , por exemplo, onde o resultado esperado como saída deve ser sempre o mesmo quando passados os mesmos valores. O que significa que para a função acima de exemplo, se x for 10 e y for 5 o resultado final SEMPRE será 15. Ela não pode ser não-determinística a ponto de te retornar um valor diferente para os mesmos parametros. Tipo : **f(10, 5) = 15**,** <span style="color: #ff0000">f(10, 5) = 20</span>**.

Outra característica das funções puras é o fato delas não acarretarem efeitos colaterais na sua execução, ou seja, passados x, y ela apenas irão computar x e y. Não se pode inserir um z na questão, ou executar um método de I/O como ler um arquivo , executar um ajax ou mesmo alterar um elemento do dom. Por isso as funções puras são previsíveis, o que nos ajuda e muito na sanidade da nossa aplicação, ao invés disso, o que costumamos fazer é algo do tipo:

<pre class="lang-javascript">function soma( x, y ){
	document.body.innerHTML = 'AHAHAHHAH'
	global.var = null
	return x+y
}
</pre>

Esta função não é pura, inclusive é imunda. Esse exemplo é caricato, mas pode perceber que faz muito isso olhando pros seus códigos, esta função soma que deveria apenas somar produz efeitos colaterais, no caso acima, no DOM e numa variável global. E se retirar a linha que altera o DOM e a linha da variável global, e por algum motivo sua função retorna soma algumas vezes e outras retorna a divisão, pros mesmos parâmetros, então ela também não é pura. É interessante que mantenha em mente o que eu disse anteriormente sobre não ser um robô. Não mude todas as suas funções para funções puras. As funções impuras também tem sua utilidade.

Então teríamos um reducer que modificaria um determinado campo do nosso objeto que armazena os estados da nossa aplicação.

Abaixo segue a implementação do reducer que modifica o estado **{ todos:[] } **da minha Store:

<pre class="lang-javascript">export default function( state = [], action ){

	switch( action.type ){

		case 'ADD_TODO': return [
			...state, {
				text 		:action.text,
				completed 	:false,
				edit		:false,
				id		:(Math.random() * Math.pow(10, 20))
			}
		]

		case 'UPDATE_TODO': return state.map( item =&gt;{
			if( item.id == action.id ){
				item.text = action.text
				item.edit = false
			}
			return item
		})

		case 'REMOVE_TODO': return state.filter( item =&gt;
			item.id != action.id
		)

		default : return state
	}
}
</pre>

Como o estado **todos **é uma lista, eu sempre vou retornar uma lista, todos os reducers recebem as ações disparadas, cabe a você definir à quais ações o seu reducer irá responder. Isso é muito legal no Redux, facilita e MUITO no processo de inserir novas features no seu projeto.

Para o estado **filter** que cuida dos filtros da minha todo list como &#8220;completos&#8221; &#8220;ativos&#8221; ou &#8220;todos&#8221;, eu crio outro reducer, responsável por alterar apenas este estado:

<pre class="lang-javascript">export default (state = 'all', action) =&gt;{
	return action.filter? action.filter :state
}
</pre>

Este é bem simples. Este reducer sempre vai retornar valores entre &#8220;all&#8221;, &#8220;completed&#8221;, &#8220;active&#8221;. Note que aqui estou desconsiderando o tratamento do action.filter, portanto se for passado um estado que não está dentro dos valores que mencionei, o código irá quebrar. Mantive desta forma por questões didáticas.

## Combinação de Reducers

Lembra que na definição da minha Store, eu podia passar apenas um reducer, certo? Como eu tenho dois para essa aplicação como eu passo estes reducers se minha store recebe apenas um?

Aqui é onde você percebe que as coisas encaixam&#8230;  Se você tem duas funções puras que recebem um estado como primeiro parâmetro e a mesma action como segundo, basta criar uma terceira que engloba as outras duas, combinando os reducers:

<pre class="lang-javascript">import todos from 'reducers/todos/todo'
import visibility from 'reducers/todos/visibility'

export default ( state, action ) =&gt;{

	        let list = todos( state.todos, action ),
		filter 	 = visibility( state.filter, action ),
		filtered = todos( list, { type 	:'FILTER_TODO', filter })

	return {
		filter,
		todos 	:list,
		items	:filtered
	}
}
</pre>

Este reducer é exatamente o que é importado lá em cima na nossa Store. Lembrando que na nossa Store, nos passamos um objeto com 3 estados, { **todos, items, filter **}. Essa main reducer vai receber como primeiro parametro esse objeto com os 3 estados, e vai repassar cada estado para seu reespectivo reducer que por sua vez, vai retornar um novo estado dado aquela ação, e todos recebem a mesma action! \o/

No meu main reducer ali eu mudei um pouco, fiz diferente do modo como vi na implementação do redux no TodoMVC, eu criei  um estado a mais que é o estado **items**, porque este é o que aparece para o usuário, mas não é o reflexo de todos os **todos** que eu possuo. O que acontecia antes de eu adicionar esse campo é que na hora de escolher por um filtro que apenas mostrava os **todos** completados a minha Store automaticamente salvava este estado no session storage e eu perdia os items que estavam **incompletos** por exemplo. Então eu precisava de um campo para realmente armazenar todas as entradas que eu tinha, e outro campo chamado &#8220;**items**&#8221; que serve de forma visual na hora de filtrar os **todos**.

Na documentação do redux usando React ele resolve esse problema dos itens filtrados na view. Eu particularmente prefiro ter **menos lógica possível** na view e isso é só uma questão de preferência.

Essa alteração foi extremamente simples e é incrível como é fácil resolver problemas deste tipo de forma elegante, não fugi do padrão do reducer, das funções puras, e consegui reutilizar o reducer **todos **apenas passando a ação de filtro para a mesma lista de items usando a mesma função salvando em outro estado.

## Conclusão

De fato isso melhorou bastante o desenvolvimento de aplicações complexas que estava desenvolvendo, é preciso amadurecimento nessa arquitetura ainda. Faz apenas alguns meses que estou mexendo nisso e não posso incluir essa arquitetura em qualquer projeto, então o processo de amadurecimento e experiência é lento.

Realmente isso resolve muitos problemas recorrentes que tinha e de quebra você ganha um poder que nem percebeu, de graça. Por concentrar todos os estados da sua aplicação em um objeto, e realizar todas as mudanças neste objeto, você pode &#8220;voltar no tempo&#8221;, basta fazer um subscribe na sua Store, e sempre que ela atualizar, armazene o último estado em um array. Dessa forma, como sua aplicação responde sempre à um estado, você pode incluir uma funcionalidade de &#8220;undo&#8221; e &#8220;redo&#8221;, apenas navegando entre os estados desse array =).

Além disso você perde menos tempo com detalhes do DOM, delegue isso para alguma lib de template, e se concentre nos estados, isso inclusive te ajuda na hora de testar o comportamento da sua aplicação, você não precisa emular o DOM, basta testar as propriedades de cada estado.

## Finalizando&#8230;

Bom galera, era isso que eu tinha pra falar, eu não postei a aplicação por completo para não estender ainda mais esse post, deixarei no final do post um link com o app funcionando e o código-fonte no caso de alguém se interessar. A idéia do post não é servir como referência para suas aplicações baseadas em Redux, serve apenas para instigar um pouco a curiosidade com relação à padrões e arquiteturas, deixando os frameworks em segundo plano. Há outros conceitos não discutidos como **imutabilidade** e outras coisas mais, sugiro a leitura da documentação oficial para maiores detalhes.

O TodoApp que fiz é um projeto feito em AMD, usando o micro-framework Jails para relacionamento entre componentes e módulos, o projeto foi escrito usando a sintaxe do ES6 usando **Babel** para gerar os AMD&#8217;s em ES5. Estou usando como componente de renderização o <a href="http://riotjs.com/" target="_blank">RiotJS</a> que implementa virtualDOM e é extremamente leve, tornou-se minha engine padrão nos projetos para renderização de templates, embora ela seja muito mais que isso. O Riotjs é uma ótima alternativa para quem quer colocar os conceitos do React em prática.

Um grande abraço.

  * <a href="https://github.com/jails-org/Demos/tree/master/TodoApp" target="_blank">Jails TodoApp</a>
  * <a href="https://egghead.io/lessons/javascript-redux-the-single-immutable-state-tree?series=getting-started-with-redux" target="_blank">Redux Course ( Screencasts )</a>
  * <a href="http://redux.js.org/" target="_blank">Redux Documentation</a>
  * <a href="https://en.wikipedia.org/wiki/Pure_function" target="_blank">Pure Functions</a>
  * <a href="http://riotjs.com/" target="_blank">RiotJS</a>
  * [Babel & AMD modules][2]

 [1]: http://todomvc.com/
 [2]: http://babeljs.io/docs/plugins/transform-es2015-modules-amd/