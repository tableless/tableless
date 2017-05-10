---
title: Dominando o uso de prototype em JavaScript
author: Clovis Neto
type: post
date: 2014-06-14
excerpt: |
  |
    Neste artigo vamos aprender a utilizar um aspecto bastante importante das funções: protótipos.
url: /dominando-o-uso-de-prototype-em-javascript/
dsq_thread_id: 2543564374
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - aprendendo a ultilizar prototipos javascript
  - Clóvis Neto JavaScript
  - como criar classes com prototype
  - como usar o prototype em javascript
  - criando classes javascript com protótipos
  - javascript prototype
  - javascript prototype método
  - Orientação a objetos com protótipos
  - Orientação a objetos com prototype
  - prototipos de javascript

---
Vários desenvolvedores web falam que protótipos representam uma forma de definirmos tipos de objetos, mas se você observar com cuidado, isto é uma característica de funções.

Perceba que todas as funções têm uma propriedade _prototype_ que, inicialmente, referencia um objeto vazio.

Usando a palavra chave _New_ para invocar a função construtor, temos agora um objeto recém instanciado  como seu contexto.

Ex:

<pre class="lang-javascript">function Lutador(){}
 var lutador1 = new Lutador();</pre>

## O básico &#8211; Incluindo métodos numa classe (função)

Temos nossa classe **Lutador**, que se encontra vazia e queremos anexar um método a ela. Logo utilizamos a seguinte estrutura:

<pre class="lang-javascript">function Lutador(){}
Lutador.prototype.Socar = function(){
 return true;
}
 var lutador1 = new Lutador();

console.log(lutador1.Socar());</pre>

Um protótipo nos permite predefinir propriedades, incluindo métodoss. Você pode saber como acessar as propriedades de protótipos a partir da instância do objeto com _lutador1.constructor.prototype.Socar_.

Uma observação importante é que não importa a ordem onde o protótipo é declarado, pois &#8220;suas atualizações&#8221; são feitas dinamicamente, ex:

Isto:

<pre class="lang-javascript">function Lutador(){}
Lutador.prototype.Socar = function(){
 return true;
}
 var lutador1 = new Lutador();</pre>

Tem o mesmo sentido de:

<pre class="lang-javascript">function Lutador(){}
 var lutador1 = new Lutador();
Lutador.prototype.Socar = function(){
 return true;
}</pre>

Podemos também instânciar um objeto deste modo:

<pre class="lang-javascript">function Lutador(){}
var lutador1 = new Lutador();
var lutador2 = new lutador1.constructor();
console.log("Verificanco se esta afirmção é verdadeira: "+lutador1 !== lutador2);</pre>

> Note que **lutador1** não é o mesmo objeto de **lutador2**, mas são duas instâncias distintas.

Tudo que vimos até agora, foi o básico de que os protótipos oferecem, agora está na hora de avançar um pouco mais.

## Herança e a cadeia de protótipos

Existem várias formas de como obter uma herança com protótipos, mas sem dúvida, a melhor forma é este modo:

<pre class="lang-javascript">function Lutador(){
 this.attackPlayer = function(){
  return true;
 }
} 

function Habilidades(){
 this.esquivaPlayer = function(){
  console.log("esquivou");
 }
}

//fazendo Lutador herdar de Habilidades
Lutador.prototype = new Habilidades();
lutador1 = new Lutador();

//verificando
console.log(lutador1 instanceof Lutador);
console.log(lutador1 instanceof Habilidades);</pre>

> _Nota: &#8220;Existe também outra técnica semelhante a esta, e que eu desaconselho. É utilizar o objeto do protótipo de_ Habilidades_ diretamente como protótipo de_ Lutador_&#8230; Ex:_ Lutador.prototype = Habilidades.prototype; _pois fazendo isto, qualquer alteração no protótipo de_ Lutador _também modificará o protótipo de_ Habilidades_, porque eles serão o mesmo objeto, e isso com certeza terá alguns efeitos colaterais indesejaveis_

## Incluindo novo método nos elementos HTML por meio do protótipo HTMLElement

Nos navegadores atuais e antigos (IE8+) temos uma funcionalidade bastante interessante que nos permite estender qualquer nó HTML de nossa escolha, vejamos então o próximo exemplo:

<pre class="lang-javascript">HTMLElement.prototype.remover = function() {
		this.parentNode.removeChild(this);
	};

	document.querySelector("#a").remover();</pre>

Neste exemplo incluimos um novo método &#8220;remover&#8221;, em todos os elementos do DOM por meio do protótipo do contrutor HTMLElement. Logo depois removemos o elemento html que tem por _id=&#8221;a&#8221; _

> _Um exemplo muito bom de utilização deste recurso é a biblioteca Prototype, por ela conseguimos obter muitas funcionalidades nos elementos DOM, por exemplo injetar HTML e manipular CSS._

#### Extenção de Object e Array

Por meio de protótipos também podemos estender os tipos primitivos do javascript, como: Object, Array e Number. Vejamos como estender uma variável do tipo array por meio de protótipos:

<pre class="lang-javascript">Array.prototype.cataFruta = function(callback) {
	for(var i = 0; i &lt; this.length; i++){
		callback.call(this,this[i],i);
	}
};
var frutas = ["laranja","uva","pinha","morango"];
frutas.cataFruta(function(element,index){
	console.log("fruta: "+element+" sua posição é: "+index);
});</pre>

Note que adicionamos um método &#8220;cataFruta()&#8221;, que serve como um forEach dentro do array, e este mesmo método pode receber um callback que retorna dois parâmetros, que é o elemento atual em execução e o seu índice. Também podemos estender Object:

<pre class="lang-javascript">Object.prototype.esconde = function(callback) {
	if(this.hasOwnProperty("style")){
		this.style.opacity = 0;
		this.style.filter = "alpha(opacity=0)";
		callback.call(this,this);
	}
};
document.getElementById('escondido').esconde(function(element){
	console.log("escondemos a div com o id: "+element.getAttribute("id")+"!!");
});</pre>

Note que usamos a mesma lógica para os dois, só mudou que ao invés de _Array.prototype_ colocamos _Object.prototype._ Também podemos estender o tipo Number, algo que não recomendo pois ele é um protótipo nativo muito problemático.

> _&#8220;Devido à forma como números e propriedades de números são processados pelo engine JavaScript, alguns resultados podem ser bastante confusos&#8230;&#8221; (Segredos do Ninja Javascript::Novatec)_

#### Subclasse do objeto Array

Como expliquei mais à cima, existe um modo de herdamos heranças em classes JavaScript, isso não é diferente com o objeto Array. Vejamos um exemplo de como podemos criar uma subclasse do tipo array:

<pre class="lang-javascript">function MinhaClasse(){}
MinhaClasse.prototype = new Array();
var meu = new MinhaClasse();
meu.push(1,2,3);
console.log("O tamanho da subclasse meu é: "+meu.length);

Ou ao invés de criar, podemos apenas "simular" a criação de uma subclasse do tipo array, ex:</pre>

<pre class="lang-javascript">function MinhaClasse(){}
MinhaClasse.prototype.length = 0;

(function(){
	var novos_metodos = ['push','shift','join','unshift','slice','pop','splice'];
	for (var i = 0; i &lt; novos_metodos.length; i++)(function(metodo){
		MinhaClasse.prototype[metodo] = function(){
			return Array.prototype[metodo].apply(this,arguments);
		}
	})(novos_metodos[i]);
})();

var meu = new MinhaClasse();
meu.push(1,2,3);
console.log("O tamanho da subclasse meu é: "+meu.length);</pre>

## Um erro grave de usuário

Tudo que vimos até agora é muito bom e ajuda bastante para nossas aplicações JavaScript, com esse conhecimento e um pouco de esforço da até mesmo para criar sua própria biblioteca JavaScript. Mas ainda eu não poderia encerrar o artigo sem antes lhes prevenir de um erro que alguns usuários com pouco conhecimento de JavaScript cometem&#8230;

Tudo que vimos não terá utilidade nenhuma se não invocarmos a função como construtor. Imagine que um usuário leigo de JS pegou seu código mas tenta invocar a função &#8220;como função&#8221; achando que é assim que tem que ser feito. ex:

<pre class="lang-javascript">function Pessoa(nome,sobrenome){
	this.name = nome+" "+sobrenome;
}

var homem = Pessoa("Clóvis","Neto");
console.log(homem.name);</pre>

Note no console de seu navegador que um erro aconteceu ao tentarmos verificar o _name_ de homem. Logo isto ocorrerá sempre que o usuário tentar invocar a &#8220;função como função&#8221;.

>  _Então qual será a solução para este problema? _

Simples podemos fazer uma verificação, se o objeto é uma instância da função&#8230; caso não seja, retornaremos a forma correta de como chamar a função e tudo estará resolvido. Ex:

<pre class="lang-javascript">function Pessoa(nome,sobrenome){
        if(!(this instanceof arguments.callee)){
		return new Pessoa(nome,sobrenome);
	}

	this.name = nome+" "+sobrenome;
}

var homem = Pessoa("Clóvis","Neto");
console.log(homem.name);</pre>

Rode agora nosso script e veja que tudo vai bem, e não aparece erro nenhum no console 🙂

Bem vou parar por aqui para o artigo não ficar muito grande, por hoje é só, um forte abraço de Clóvis Neto e até a próxima 😀