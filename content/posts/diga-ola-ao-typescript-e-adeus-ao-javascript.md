---
title: Diga olá ao TypeScript e adeus ao JavaScript
author: Daniel Schmitz
type: post
date: 2015-12-14
url: /diga-ola-ao-typescript-e-adeus-ao-javascript/
categories:
  - Geral
  - JavaScript
tags:
  - aprenda
  - desenvolvimento web
  - JavaScript
  - orientação a objetos
  - prototype
  - Técnicas e Práticas
  - typescript

---
Acredito que este artigo tenha chamado a sua atenção pelo título. Como assim??? adeus ao JavaScript??? A linguagem que está bombando em 2015 (e claro, 2016!). Posso estar sendo um pouco ousado aqui, mas eu tenho em mente que, neste momento, o JavaScript para mim é agora &#8220;linguagem de máquina&#8221; ou o famoso bytecode. Porquê? Bom, você conhece um código javascript minificado+comprimido+&#8221;esculachado&#8221;&#8230; Não estou retirando aqui toda a beleza do JavaScript, e consequente importância, mas na evolução que vem acontecendo a cada dia no mundo web, felizmente chegamos ao ponto que podemos tratar o javascript como uma linguagem tipada e semelhante ao c/java/php e derivados.

Neste ponto entra uma questão pessoal. Ou você vai adorar TypeScript ou vai achar completamente inútil, já que a sua principal característica é trazer uma &#8220;tipagem&#8221; a linguagem, e no pacote uma forma de programar em javascript mais parecida com Java e suas vertentes. Se você gosta de tipar suas váriaveis e métodos, criar classes, interfaces, usar Orientação a Objetos, o TypeScript foi feito para você e, claro, pode dizer adeus ao JavaScript.

Lembre-se que TypeScript está sendo usada extensivamente no novo framework Angular2, então se vc ainda não sabe o que é TypeScript, chegou o momento de conhecer.

## O que é TypeScript?

O TypeScript possibilita que você escreva código JavaScript na forma que foi acostumado quando aprendeu Orientação a Objetos. Você lembra dessas aulas, em criar métodos que retornassem um valor com tipo definido, em criar classes e mais classes para o seu programa, em criar interfaces para desacoplar tudo que quisesse, entre diversas outras técnicas. Com TypeScript tudo isso é possível, porque no final ele pega o seu lindo código cheio de classes e transforma em JavaScript puro, no qual o browser vai compreender. No próprio site é definido que o TypeScript compila para JavaScript, o que é um termo tecnicamente errado &#8211; mas cada vez mais aceito, dado que aquele código &#8220;malucão&#8221; em JavaScript pode ser encarado como código de máquina.

No exemplo a seguir, criamos uma interface e uma classe, veja:

<pre class="lang-javascript">interface IComponent{
	getId() : string;
}

class Button implements IComponent{
	id:string;
	getId():string{
		return this.id;
	}
}</pre>

Este é um código 100% TypeScript que você pode criar em um editor de textos ou ide, no qual criamos uma interface chamada `IComponent`e uma classe que chamamos de `Button`. Esta classe implementa a interface e por isso o método `getId()` deve ser criado. Se você salvar este arquivo como um arquivo javascript e adicionar em um documento HTML, nenhum **browser** vai entender isso, quem sabe num futuro distante. Mas isso nao é um problema, pois o TypeScript possui um &#8220;compilador&#8221; que irá pegar o seu código e transformar em algo do tipo:

<pre class="lang-javascript">var Button = (function () {
    function Button() {
    }
    Button.prototype.getId = function () {
        return this.id;
    };
    return Button;
})();</pre>

Este código feioso aí em cima é 100% javascript compreensível em qualquer navegador web. Tem gente que prefere escrever assim, vai entender né. Mas como essa mágica funciona? Vamos explicar a seguir.

## Testando o TypeScript

Abra uma nova aba no seu browser e acesse: <http://www.typescriptlang.org/Playground>. O Playground é um pequeno editor TypeScript que, além de checar possíveis erros de sintaxe, também compila automaticamente o código para Javascript, no qual você pode testá-lo. Não omita o Playground no seu aprendizado, ele pode te ajudar muito, como na figura a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts01.png" alt="ts01" width="856" height="277" class="alignleft size-full wp-image-52433" />

Caso não queira utilizar o Playground, pode-se instalar o TypeScript no seu ambiente de desenvolvimento através do node. O comando a seguir deve ser compreensível para você:

<pre class="lang-shell">$ npm install typescript -g</pre>

Após instalar o TypeScript no ambiente, você pode usar o comando `tsc` para compilar um arquivo que geralmente está na extensão `ts` para `js`. Por exemplo, crie o arquivo `script.ts` com o código TypeScript descrito anteriormente e execute o seguinte comando:

<pre class="lang-shell">tsc --out script.js script.ts</pre>

Editores de texto como o Sublime Text, Atom, VS Code, também tem a capacidade de compilar o arquivo em JavaScript, bastando apenas adicionar plugins relativos ao TypeScript. O `VS Code`, em particular, apresentou um bom comportamento frente aos outros, como pode-se perceber na imagem a seguir.

<div id="attachment_52436" style="width: 549px" class="wp-caption alignleft">
  <img src="http://tableless.com.br/uploads/2015/12/ts02.png" alt="Visual Studio Code" width="539" height="639" class="size-full wp-image-52436" />
  
  <p class="wp-caption-text">
    Visual Studio Code
  </p>
</div>

<div id="attachment_52438" style="width: 566px" class="wp-caption alignleft">
  <img src="http://tableless.com.br/uploads/2015/12/ts03.png" alt="Sublime Text 2.0.2" width="556" height="765" class="size-full wp-image-52438" />
  
  <p class="wp-caption-text">
    Sublime Text 2.0.2
  </p>
</div>

Mas neste artigo vamos nos contentar com o TypeScript Playground, e deixe os editores para a sua escolha pessoal (fique a vontade em perguntar como configurar o TypeScript no Sublime, é um pouco mais trabalhoso). 

Agora que apresentamos o TypeScript e suas maravilhas, vamos compreender um pouco mais desta linguagem.

## Tipos de variáveis

Uma das funcionalidades do TypeScript é criar variáveis com tipos definidos, assim como é feito no Java. 

### Tipos primitivos

Existem 3 tipos primitivos que podemos associar a uma variável. As variáveis são criadas através da palavra reservada `var`, e o tipo é informado da seguinte forma:

<pre class="lang-javascript">var NOMDE_DA_VARIAVEL : TIPO = VALOR
</pre>

  * boolean: Pode assumir os valores `true` ou `false`
  * number: Assume qualquer número, como inteiro ou ponto flutuante.
  * string: Tipo texto, pode ser atribuído com aspas simples ou duplas. 
### Arrays

Arrays no TS podem ser criados através de duas formas. A primeira delas, usa-se `[]` na definição do tipo da variável, veja:

<pre class="lang-javascript">var list:number[] = [1, 2, 3];
</pre>

A segunda é mais conhecida como &#8220;generics&#8221; e usa `<>` para definir o tipo, veja:

<pre class="lang-javascript">var list:Array&lt;number&gt; = [1,2,3];
</pre>

Pode-se usar tipos complexos na criação de arrays, como no exemplo a seguir.

<pre class="lang-javascript">class Pessoa{
	nome:string;
	constructor(nome:string){
		this.nome = nome;
	}
	sayHello():string{
		return "Hello, " + this.nome;
	}
}

var fulano = new Pessoa("fulano");
var beltrano = new Pessoa("beltrano");

var pessoas:Pessoa[]= new Array();
pessoas.push(fulano);
pessoas.push(beltrano);

pessoas.forEach( (p:Pessoa)=&gt;
	console.log(p.sayHello())
	);
</pre>

Neste exemplo, criamos uma classe chamada `Pessoa`, adicionando a propriedade `nome`, o método construtor e o método `sayHello`. Depois, criamos duas variáveis `fulano` e `beltrano`, e adicionamos à variável `pessoas`, que é um array de vaiáveis do tipo `Pessoa`.

Após usar o método `push` para adicionar as variáveis no array, usamos o método `forEach` para percorrer cada item deste array e exibir uma mensagem no console do navegador. 

### Enum

Enums são velhos conhecidos do C#, e usados como &#8220;datatype&#8221;, que podem definir um status por exemplo. 

<pre class="lang-javascript">enum Color {Red, Green, Blue};
var c: Color = Color.Green;
</pre>

ou 

<pre class="lang-javascript">enum Color {Red = 1, Green = 2, Blue = 3};
var c: Color = Color.Green;
</pre>

Quando criamos um enum, usamos o &#8220;poder&#8221; da ide para que possamos programar de forma mais fácil, conforme a figura a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts04.png" alt="ts04" width="697" height="145" class="alignleft size-full wp-image-52451" />

### Any

Uma variável do tipo `Any` pode assumir qualquer valor.

<pre class="lang-javascript">var notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean

var list:any[] = [1, true, "free"];
list[1] = 100;
</pre>

### Void

O `void` é usado para determinar que um método não retorna nenhum valor, conforme o exemplo a seguir.

<pre class="lang-javascript">function warnUser(): void {
    alert("This is my warning message");
}
</pre>

## Classes

O conceito de classes no TypeScript é o mesmo de uma classe em qualquer linguagem orientada a objetos. As classes no TypeScript seguem o padrão ECMAScript 6 que em teoria será o &#8220;futuro&#8221; do JavaScript. A classe possui uma sintaxe muito familiar com c#, veja:

<pre class="lang-javascript">class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}
var greeter = new Greeter("world");
</pre>

O construtor é definido pela palavra `constructor`. Métodos não necessitam da palavra `function`, bastando apenas usar ``Acredito que este artigo tenha chamado a sua atenção pelo título. Como assim??? adeus ao JavaScript??? A linguagem que está bombando em 2015 (e claro, 2016!). Posso estar sendo um pouco ousado aqui, mas eu tenho em mente que, neste momento, o JavaScript para mim é agora &#8220;linguagem de máquina&#8221; ou o famoso bytecode. Porquê? Bom, você conhece um código javascript minificado+comprimido+&#8221;esculachado&#8221;&#8230; Não estou retirando aqui toda a beleza do JavaScript, e consequente importância, mas na evolução que vem acontecendo a cada dia no mundo web, felizmente chegamos ao ponto que podemos tratar o javascript como uma linguagem tipada e semelhante ao c/java/php e derivados.

Neste ponto entra uma questão pessoal. Ou você vai adorar TypeScript ou vai achar completamente inútil, já que a sua principal característica é trazer uma &#8220;tipagem&#8221; a linguagem, e no pacote uma forma de programar em javascript mais parecida com Java e suas vertentes. Se você gosta de tipar suas váriaveis e métodos, criar classes, interfaces, usar Orientação a Objetos, o TypeScript foi feito para você e, claro, pode dizer adeus ao JavaScript.

Lembre-se que TypeScript está sendo usada extensivamente no novo framework Angular2, então se vc ainda não sabe o que é TypeScript, chegou o momento de conhecer.

## O que é TypeScript?

O TypeScript possibilita que você escreva código JavaScript na forma que foi acostumado quando aprendeu Orientação a Objetos. Você lembra dessas aulas, em criar métodos que retornassem um valor com tipo definido, em criar classes e mais classes para o seu programa, em criar interfaces para desacoplar tudo que quisesse, entre diversas outras técnicas. Com TypeScript tudo isso é possível, porque no final ele pega o seu lindo código cheio de classes e transforma em JavaScript puro, no qual o browser vai compreender. No próprio site é definido que o TypeScript compila para JavaScript, o que é um termo tecnicamente errado &#8211; mas cada vez mais aceito, dado que aquele código &#8220;malucão&#8221; em JavaScript pode ser encarado como código de máquina.

No exemplo a seguir, criamos uma interface e uma classe, veja:

<pre class="lang-javascript">interface IComponent{
	getId() : string;
}

class Button implements IComponent{
	id:string;
	getId():string{
		return this.id;
	}
}</pre>

Este é um código 100% TypeScript que você pode criar em um editor de textos ou ide, no qual criamos uma interface chamada `IComponent`e uma classe que chamamos de `Button`. Esta classe implementa a interface e por isso o método `getId()` deve ser criado. Se você salvar este arquivo como um arquivo javascript e adicionar em um documento HTML, nenhum **browser** vai entender isso, quem sabe num futuro distante. Mas isso nao é um problema, pois o TypeScript possui um &#8220;compilador&#8221; que irá pegar o seu código e transformar em algo do tipo:

<pre class="lang-javascript">var Button = (function () {
    function Button() {
    }
    Button.prototype.getId = function () {
        return this.id;
    };
    return Button;
})();</pre>

Este código feioso aí em cima é 100% javascript compreensível em qualquer navegador web. Tem gente que prefere escrever assim, vai entender né. Mas como essa mágica funciona? Vamos explicar a seguir.

## Testando o TypeScript

Abra uma nova aba no seu browser e acesse: <http://www.typescriptlang.org/Playground>. O Playground é um pequeno editor TypeScript que, além de checar possíveis erros de sintaxe, também compila automaticamente o código para Javascript, no qual você pode testá-lo. Não omita o Playground no seu aprendizado, ele pode te ajudar muito, como na figura a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts01.png" alt="ts01" width="856" height="277" class="alignleft size-full wp-image-52433" />

Caso não queira utilizar o Playground, pode-se instalar o TypeScript no seu ambiente de desenvolvimento através do node. O comando a seguir deve ser compreensível para você:

<pre class="lang-shell">$ npm install typescript -g</pre>

Após instalar o TypeScript no ambiente, você pode usar o comando `tsc` para compilar um arquivo que geralmente está na extensão `ts` para `js`. Por exemplo, crie o arquivo `script.ts` com o código TypeScript descrito anteriormente e execute o seguinte comando:

<pre class="lang-shell">tsc --out script.js script.ts</pre>

Editores de texto como o Sublime Text, Atom, VS Code, também tem a capacidade de compilar o arquivo em JavaScript, bastando apenas adicionar plugins relativos ao TypeScript. O `VS Code`, em particular, apresentou um bom comportamento frente aos outros, como pode-se perceber na imagem a seguir.

<div id="attachment_52436" style="width: 549px" class="wp-caption alignleft">
  <img src="http://tableless.com.br/uploads/2015/12/ts02.png" alt="Visual Studio Code" width="539" height="639" class="size-full wp-image-52436" />
  
  <p class="wp-caption-text">
    Visual Studio Code
  </p>
</div>

<div id="attachment_52438" style="width: 566px" class="wp-caption alignleft">
  <img src="http://tableless.com.br/uploads/2015/12/ts03.png" alt="Sublime Text 2.0.2" width="556" height="765" class="size-full wp-image-52438" />
  
  <p class="wp-caption-text">
    Sublime Text 2.0.2
  </p>
</div>

Mas neste artigo vamos nos contentar com o TypeScript Playground, e deixe os editores para a sua escolha pessoal (fique a vontade em perguntar como configurar o TypeScript no Sublime, é um pouco mais trabalhoso). 

Agora que apresentamos o TypeScript e suas maravilhas, vamos compreender um pouco mais desta linguagem.

## Tipos de variáveis

Uma das funcionalidades do TypeScript é criar variáveis com tipos definidos, assim como é feito no Java. 

### Tipos primitivos

Existem 3 tipos primitivos que podemos associar a uma variável. As variáveis são criadas através da palavra reservada `var`, e o tipo é informado da seguinte forma:

<pre class="lang-javascript">var NOMDE_DA_VARIAVEL : TIPO = VALOR
</pre>

  * boolean: Pode assumir os valores `true` ou `false`
  * number: Assume qualquer número, como inteiro ou ponto flutuante.
  * string: Tipo texto, pode ser atribuído com aspas simples ou duplas. 
### Arrays

Arrays no TS podem ser criados através de duas formas. A primeira delas, usa-se `[]` na definição do tipo da variável, veja:

<pre class="lang-javascript">var list:number[] = [1, 2, 3];
</pre>

A segunda é mais conhecida como &#8220;generics&#8221; e usa `<>` para definir o tipo, veja:

<pre class="lang-javascript">var list:Array&lt;number&gt; = [1,2,3];
</pre>

Pode-se usar tipos complexos na criação de arrays, como no exemplo a seguir.

<pre class="lang-javascript">class Pessoa{
	nome:string;
	constructor(nome:string){
		this.nome = nome;
	}
	sayHello():string{
		return "Hello, " + this.nome;
	}
}

var fulano = new Pessoa("fulano");
var beltrano = new Pessoa("beltrano");

var pessoas:Pessoa[]= new Array();
pessoas.push(fulano);
pessoas.push(beltrano);

pessoas.forEach( (p:Pessoa)=&gt;
	console.log(p.sayHello())
	);
</pre>

Neste exemplo, criamos uma classe chamada `Pessoa`, adicionando a propriedade `nome`, o método construtor e o método `sayHello`. Depois, criamos duas variáveis `fulano` e `beltrano`, e adicionamos à variável `pessoas`, que é um array de vaiáveis do tipo `Pessoa`.

Após usar o método `push` para adicionar as variáveis no array, usamos o método `forEach` para percorrer cada item deste array e exibir uma mensagem no console do navegador. 

### Enum

Enums são velhos conhecidos do C#, e usados como &#8220;datatype&#8221;, que podem definir um status por exemplo. 

<pre class="lang-javascript">enum Color {Red, Green, Blue};
var c: Color = Color.Green;
</pre>

ou 

<pre class="lang-javascript">enum Color {Red = 1, Green = 2, Blue = 3};
var c: Color = Color.Green;
</pre>

Quando criamos um enum, usamos o &#8220;poder&#8221; da ide para que possamos programar de forma mais fácil, conforme a figura a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts04.png" alt="ts04" width="697" height="145" class="alignleft size-full wp-image-52451" />

### Any

Uma variável do tipo `Any` pode assumir qualquer valor.

<pre class="lang-javascript">var notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean

var list:any[] = [1, true, "free"];
list[1] = 100;
</pre>

### Void

O `void` é usado para determinar que um método não retorna nenhum valor, conforme o exemplo a seguir.

<pre class="lang-javascript">function warnUser(): void {
    alert("This is my warning message");
}
</pre>

## Classes

O conceito de classes no TypeScript é o mesmo de uma classe em qualquer linguagem orientada a objetos. As classes no TypeScript seguem o padrão ECMAScript 6 que em teoria será o &#8220;futuro&#8221; do JavaScript. A classe possui uma sintaxe muito familiar com c#, veja:

<pre class="lang-javascript">class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}
var greeter = new Greeter("world");
</pre>

O construtor é definido pela palavra `constructor`. Métodos não necessitam da palavra `function`, bastando apenas usar`` . Perceba que, no exemplo apresentado, não definimos visibilidade das propriedades da classe, nem o tipo de retorno do método `greet`. É claro que podemos definir estes parâmetros, conforme o próximo exemplo.

<pre class="lang-javascript">class Greeter {
    private greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    public greet() : string {
        return "Hello, " + this.greeting;
    }
}

var greeter = new Greeter("world");
</pre>

### Visibilidade de métodos e propriedades

Métodos e propriedades de uma classe podem assumir a visibilidade: private, public e protected. 

### Herança

A herança entre uma classe e outra é definida pela palavra `extends`. Pode-se sobrecarregar métodos e usar a palavra `super` para chamar o método da classe pai, conforme o exemplo a seguir.

<pre class="lang-javascript">class Animal {
    name:string;
    constructor(theName: string) { this.name = theName; }
    move(meters: number = 0) {
        alert(this.name + " moved " + meters + "m.");
    }
}

class Snake extends Animal {
    constructor(name: string) { super(name); }
    move(meters = 5) {
        alert("Slithering...");
        super.move(meters);
    }
}

class Horse extends Animal {
    constructor(name: string) { super(name); }
    move(meters = 45) {
        alert("Galloping...");
        super.move(meters);
    }
}

var sam = new Snake("Sammy the Python");
var tom: Animal = new Horse("Tommy the Palomino");

sam.move();
tom.move(34);
</pre>

Neste exemplo usamos o `super` da classe `Snake` para chamar o método construtor da classe pai `Animal`. Se isso não for claro para você, dê uma estudada em OO para que possa compreender melhor, pois estas características são da Orientação em Objetos como um todo, e não do TypeScript.

## Accessors (ou métodos get/set)

Os Accessors visam proteger as propriedades de uma classe, pois você já deve saber que expor propriedades de uma classe não é algo legal 🙂

Os accessors do TypeScript são feitos pelas palavras `get` e `set`, e claro, deixe a sua propriedade como `private`. Veja o exemplo a seguir.

<pre class="lang-javascript">class Pessoa {
    private _password: string;

    get password(): string {
        return this._password;
    }
	
    set password(p : string) {
        if (p != "123456") {
            this._password = p;
        }
        else {
            alert("Ei, senha não pode ser 123456");
        }
    }
}

var p = new Pessoa();
p.password = "123456"; //vai exibir o erro
</pre>

### Métodos estáticos

É possível criar métodos estáticos definindo a palavra `static` antes do método. Existem dezenas de aplicações para métodos estáticos, sendo uma delas não precisar instanciar uma classe, como no exemplo a seguir.

<pre class="lang-javascript">class SystemAlert{
	
	static alert(message:string):void{
		alert(message);
	}
	
	static warm (message:string):void{
		alert("Atenção: " + message);
	}
	
	static error(message:string):void{
		alert("Erro: " + message);
	}
	
}

SystemAlert.alert("Oi");
SystemAlert.error("Não foi possível conectar na base de dados");
</pre>

## Interfaces

Uma interface define um contrato para a classe. A interface é criada da seguinte forma:

<pre class="lang-javascript">interface Ponto{
 x: number;
 y: number;
 x: number;
}
</pre>

Para implementar a interface, usamos `implements`

<pre class="lang-javascript">class Ponto3d implements Ponto{
   (aqui implementamos x,y,z)
}
</pre>

## Funções

Vamos exemplificar algumas particularidades de uma função em TypeScript. A função pode ser criada fora de uma classe ou dentro, sendo as observações que faremos a seguir podem ser aplicadas em ambas.

Tome nota apenas que, em uma classe, não precisamos usar a palavra `function` para definir uma função, mas fora da classe precisamos.

### Parâmetros com valores padrão

Pode-se definir um valor padrão para um parâmetro de uma função da seguinte forma:

<pre class="lang-javascript">function buildName(firstName: string, lastName : string = "Smith") {
}
//ou
class Foo{
  buildName(firstName: string, lastName : string = "Smith") {
  }
}
</pre>

### Parâmetros opcionais

Use o caractere `?` para definir um parâmetro opcional.

<pre class="lang-javascript">class Foo{
  buildName(firstName: string, lastName? : string) {
     if (lastName){
           // blablabla
     }
  }
}
</pre>

### Parâmetros REST

Pode-se repassar um array de valores diretamente para um parâmetro. É válido lembrar que este modo só pode ser usado no último parâmetro da sua função. Exemplo:

<pre class="lang-javascript">class Foo{
 static alertName(firstName: string, ...restOfName: string[]) {
 	alert(firstName + " " + restOfName.join(" "));
 }
}
Foo.alertName("Fulano","de","Tal");
</pre>

### Parâmetros no formato JSON

Umas das maiores facilidades do Javascript é repassar parâmetros no formato JSON. Com TypeScript é possível utilizar este mesmo comportamento, conforme o exemplo a seguir.

<pre class="lang-javascript">class Ponto{
	
	private _x : number = 0;
	private _y : number = 0;
	private _z : number = 0;
	
	constructor( p: {x:number;y:number;z?:number;}){
		this._x = p.x;
		this._y = p.y;
		if (p.z)
			this._z = p.z;
	}
	
	is3d():boolean{
		return this._z!=0;
	}
	
}

var p1 = new Ponto({x:10,y:20});

alert(p1.is3d());
</pre>

Observe que no construtor da classe `Ponto` criamos o parâmetro `p` e na definição do seu tipo repassamos um objeto anônimo com três parâmetros, sendo que o parâmetro `z` é opcional.

## Conclusão

Neste artigo vimos algumas funcionalidades do TypeScript, sendo ainda existem diversos tópicos a serem abordados. Gostaria de lhe encorajar a testar esta nova linguagem, e caso tenha dúvidas, não deixe de comentar abaixo. Sugira também novos artigos sobre TypeScript, estaremos avaliando cada pedido!