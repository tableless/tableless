---
title: Gerenciando módulos no TypeScript
author: Daniel Schmitz
type: post
date: 2016-01-12
url: /gerenciando-modulos-no-typescript/
categories:
  - JavaScript
tags:
  - JavaScript
  - módulos
  - requirejs
  - typescript

---
Como vimos no [artigo anterior][1], com TypeScript podemos programar de forma orientada a objetos, criando classes, interfaces, get/set etc, e compilar tudo isso para JavaScript. Neste artigo veremos como criar módulos e separar classes e funcionalidades em arquivos distintos, de forma a tornar o nosso projeto mais organizado.

> Para instalar o TypeScript, você precisa ter o Node.js, juntamente com o NPM. Execute o comando `npm install typescript -g`

Existem diversas formas de trabalhar com módulos no typeScript, sendo as 3 mais comuns descritas a seguir:

  * **Combinando tudo em um arquivo somente**: Esta é a forma mais fácil de utilizar TypeScript. Primeiro criamos vários arquivos separados, com a extensão `ts` e depois executamos o comando `tsc` para juntar tudo em um único arquivo. Veja que todos os arquivos TypeScript serão agrupados, o que pode não ser uma boa prática de programação, principalmente para projetos muito extensos. 
  * **Inclusão dinâmica pelo webserver**: Neste método todos os arquivos `ts` terão o seu correspondente `js`, na qual serão carregados de forma dinâmica, via ajax. Como estamos utilizando um carregamento dinâmico, precisamos utilizar a biblioteca RequireJS
  * **Inclusão dinâmica pelo node**: Nesta forma criamos uma estrutura para ser executada diretamente pelo Node.JS, utilizando o padrão commonjs. Não usaremos este conceito aqui porque queremos ilustrar como utilizar o TypeScript em um site. 

## Combinando todos os arquivos em um só 

Esta forma é a mais simples e pode ser usada na maioria dos seus projetos web. Vamos inicialmente criar a pasta `teste1` e nela criaremos duas pastas: `src` e `build`. A pasta src contém o código fonte da aplicação, os arquivos TypeScript. A pasta build conterá o código JavaScript gerado pelo TypeScript. Na pasta `src`, criaremos 3 arquivos: 

**pessoa.ts**

<pre>class Pessoa{
	nome : string;
	constructor(nome:string){
		this.nome = nome;
	}
}
</pre>

Este primeiro arquivo é uma classe simples, com um parâmetro e o método construtor. A próxima classe será chamada de `Aluno`, que irá estender da classe `Pessoa`. Como a classe Aluno usa a classe Pessoa (que está em outro arquivo), precisamos importá-la e isso é feito da seguinte forma: `/// <reference path="" />`. O parâmetro `path` é justamente a classe que se deseja referenciar. Então temos:

**aluno.ts**

<pre>/// &lt;reference path="pessoa.ts" /&gt;

class Aluno extends Pessoa{
	matricula : string;
	
	constructor(nome:string,matricula:string){
		super(nome);
		this.matricula=matricula;
	}
}
</pre>

Nesta classe referenciamos na primeira linha a classe `Pessoa`, informando o nome do arquivo `pessoa.ts`. Depois criamos a classe `Aluno`, que herda de Pessoa. Na classe `Aluno` criamos o parâmetro `matricula`, e no seu construtor usamos a palavra `super` para referenciar o construtor da classe pai, que neste caso é `Pessoa`.

Com as duas classes prontas, podemos finalmente criar o arquivo `index.ts`, que é o arquivo principal do projeto.

**index.ts**

<pre>/// &lt;reference path="aluno.ts" /&gt

var a = new Aluno("Joãozinho","0001");
</pre>

> Veja que não é preciso adicionar a classe pessoa. Ela será adicionada na classe aluno

Veja que o arquivo principal faz uma referência a classe `Aluno`, do arquivo `aluno.ts`. Com os três arquivos prontos, podemos usar o comando `tsc` para compilar tudo em um único arquivo. Este comando é executado a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts05.png" alt="ts05" width="819" height="580" class="aligncenter size-full wp-image-52470" />

Nesta imagem usamos o comando `tree` do DOS apenas para mostrar que o arquivo `script.js` foi criado. O principal comando é o:

<pre>tsc ./src/index.ts --out ./build/script.js
</pre>

Este comando possui como primeiro parâmetro o arquivo ts inicial que neste caso é o `index.ts`. O parâmetro `--out` indica o nome do arquivo que será gerado pela compilação do TypeScript em JavaScript. Este arquivo é exibido a seguir:

**build/script.js**

<pre>var Pessoa = (function () {
    function Pessoa(nome) {
        this.nome = nome;
    }
    return Pessoa;
})();
/// &lt;reference path="pessoa.ts" /&gt;
var __extends = (this && this.__extends) || function (d, b) {
    for (var p in b) if (b.hasOwnProperty(p)) d[p] = b[p];
    function __() { this.constructor = d; }
    d.prototype = b === null ? Object.create(b) : (__.prototype = b.prototype, new __());
};
var Aluno = (function (_super) {
    __extends(Aluno, _super);
    function Aluno(nome, matricula) {
        _super.call(this, nome);
        this.matricula = matricula;
    }
    return Aluno;
})(Pessoa);
/// &lt;reference path="aluno.ts" /&gt;
var a = new Aluno("Joãozinho", "0001");
</pre>

## Utilizando módulos

O uso de módulos na aplicação faz com que as classes não pertençam mais ao escopo global, como Pessoa e Aluno pertenciam no exemplo anterior. Vamos fazer uma refatoração no código e adicionar a criação de módulos no escopo da aplicação. Suponha que a classe Pessoa pertença ao módulo &#8220;comum&#8221; e que a classe Aluno pertença ao módulo &#8220;ensino&#8221;.

**pessoa.ts**

<pre>&lt;u><strong>module</strong>&lt;/u> comum {
	<strong>&lt;u>export&lt;/u></strong> class Pessoa{
		nome : string;
		constructor(nome:string){
			this.nome = nome;
		}
	}
}
</pre>

Deixamos sublinhado as 2 palavras que são novidade neste código. A primeira é a palavra `module`, seguida do nome do seu módulo que neste caso é &#8220;comum&#8221;. Dentro do módulo &#8220;comum&#8221; temos a classe Pessoa, e nela usamos a palavra `export` que diz ao módulo que esta classe é pública ao módulo. Podemos incluir no módulo classes, variáveis, métodos etc. Para expôr estas classes a outros módulos, usamos export.

A classe Aluno é refatorada para o seguinte código: 

**aluno.ts**

<pre>/// &lt;reference path="pessoa.ts" /&gt;
module ensino{
	export class Aluno extends <strong>&lt;u>comum.Pessoa&lt;/u></strong>{
		matricula : string;
		
		constructor(nome:string,matricula:string){
			super(nome);
			this.matricula=matricula;
		}
	}
}
</pre>

A classe Aluno agora é do módulo `ensino` e como novidade temos a referência da classe Pessoa como `comum.Pessoa`. Isso é necessário já que estamos modularizando a aplicação. Finalmente, a classe `index.ts` é refatorada para:

**index.ts**

<pre>/// &lt;reference path="aluno.ts" /&gt;

var a = new ensino.Aluno("Joãozinho","0001");
</pre>

Como novidade temos a chamada da classe Aluno como `ensino.Aluno`. Com estas mudanças, podemos executar novamente a compilação:

<pre>tsc ./src/index.ts --out ./build/script.js
</pre>

e obteremos o seguinte resultado:

**build/script.js**

<pre>var comum;
(function (comum) {
    var Pessoa = (function () {
        function Pessoa(nome) {
            this.nome = nome;
        }
        return Pessoa;
    })();
    comum.Pessoa = Pessoa;
})(comum || (comum = {}));
var __extends = (this && this.__extends) || function (d, b) {
    for (var p in b) if (b.hasOwnProperty(p)) d[p] = b[p];
    function __() { this.constructor = d; }
    d.prototype = b === null ? Object.create(b) : (__.prototype = b.prototype, new __());
};
/// $lt;reference path="pessoa.ts" /&gt;
var ensino;
(function (ensino) {
    var Aluno = (function (_super) {
        __extends(Aluno, _super);
        function Aluno(nome, matricula) {
            _super.call(this, nome);
            this.matricula = matricula;
            console.log(this.matricula);
        }
        return Aluno;
    })(comum.Pessoa);
    ensino.Aluno = Aluno;
})(ensino || (ensino = {}));
/// $lt;reference path="aluno.ts" /&gt;
var a = new ensino.Aluno("Joãozinho", "0001");
</pre>

## Módulos em diretórios

Geralmente a organização de módulos é feita em diretórios, para que todos os arquivos não fiquem em somente um único diretório. No caso anterior, poderíamos (na verdade deveríamos) criar os diretórios `src/comum` e `src/ensino` e reorganizar as classes de acordo com a imagem a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts06.png" alt="ts06" width="186" height="256" class="aligncenter size-full wp-image-52476" />

A única mudança que precisamos realizar no código é no `reference`, que deverá ser:

<pre>/// &lt;reference path="../comum/pessoa.ts" /&gt;
</pre>

Na classe aluno, como temos que subir um nível para encontrar o diretório &#8220;comum&#8221;, usamos &#8220;../&#8221;.

<pre>/// &lt;reference path="ensino/aluno.ts" /&gt;
</pre>

No arquivo index.ts, não precisamos usar &#8220;../&#8221; pois estamos no mesmo nível do diretório `ensino`.

## Módulos externos com requirejs

Até este momento todos os módulos estão em um único arquivo de saída, o `build/script.js`. Agora desejamos criar uma forma de carregar os módulos sob demanda, ou seja,
  
ao invés de carregar tudo de uma vez, vamos carregando os arquivos javascript na medida que eles forem sendo requisitados. Para isso precisamos criar uma estrutura um pouco mais complexa, e também precisaremos utilizar um framework qualquer para carregar módulos. Neste caso usamos o `Requirejs`. 

### Criando a estrutura inicial

Crie uma nova pasta e copie os arquivos Pessoa.ts, Aluno.ts e index.ts com a mesma estrutura anterior. Ao invés de criarmos o diretório &#8220;build&#8221;, crie o diretório &#8220;public&#8221;, conforme a imagem a seguir.

 <img src="http://tableless.com.br/uploads/2015/12/ts07.png" alt="ts07" width="181" height="292" class="aligncenter size-full wp-image-52478" />

### Redefinido as classes

Ao utilizarmos módulos externos precisamos alterar a forma como referenciamos as classes. Ou seja, não usaremos mais o `<reference path="../comum/pessoa.ts" />` conforme aprendemos, e não será necessário neste momento definir um módulo. Vamos aos ajustes:

**comum/pessoa.ts**

<pre>export class Pessoa{
	nome : string;
	constructor(nome:string){
		this.nome = nome;
	}
}
</pre>

O que temos agora é o fim do `module` e o uso do `export` antes do nome da classe. Na classe Aluno, temos:

**ensino/aluno.ts**

<pre>&lt;u><strong>import comum = require("../comum/pessoa")</strong>&lt;/u>

export class Aluno extends comum.Pessoa{
	matricula : string;
	
	constructor(nome:string,matricula:string){
		super(nome);
		this.matricula=matricula;
	}
}
</pre>

Alem do fim da palavra `module` e do uso do `export`, temos uma importante alteração na primeira linha do arquivo _aluno.ts_. Estamos utilizando a seguinte sintaxe:

<pre>import MODULO = require("caminho");
</pre>

Aqui tivemos uma inversão do uso do nome do módulo. Se antes definimos o nome do módulo como &#8220;comum&#8221; na classe &#8220;pessoa&#8221;, agora definimos na própria classe &#8220;aluno&#8221;. Como temos agora o `import comum`, podemos usar `comum.Pessoa`. O arquivo `index.js` é refatorado para:

**index.js**

<pre>import ensino = require("ensino/aluno")

var a = new ensino.Aluno("Joãozinho","0001");
</pre>

### Instalando o requirejs

Precisamos instalar o requirejs no projeto, e podemos fazer isso com npm, através do comando `npm i requirejs --save`. Este comando irá instalar o ``Como vimos no [artigo anterior][1], com TypeScript podemos programar de forma orientada a objetos, criando classes, interfaces, get/set etc, e compilar tudo isso para JavaScript. Neste artigo veremos como criar módulos e separar classes e funcionalidades em arquivos distintos, de forma a tornar o nosso projeto mais organizado.

> Para instalar o TypeScript, você precisa ter o Node.js, juntamente com o NPM. Execute o comando `npm install typescript -g`

Existem diversas formas de trabalhar com módulos no typeScript, sendo as 3 mais comuns descritas a seguir:

  * **Combinando tudo em um arquivo somente**: Esta é a forma mais fácil de utilizar TypeScript. Primeiro criamos vários arquivos separados, com a extensão `ts` e depois executamos o comando `tsc` para juntar tudo em um único arquivo. Veja que todos os arquivos TypeScript serão agrupados, o que pode não ser uma boa prática de programação, principalmente para projetos muito extensos. 
  * **Inclusão dinâmica pelo webserver**: Neste método todos os arquivos `ts` terão o seu correspondente `js`, na qual serão carregados de forma dinâmica, via ajax. Como estamos utilizando um carregamento dinâmico, precisamos utilizar a biblioteca RequireJS
  * **Inclusão dinâmica pelo node**: Nesta forma criamos uma estrutura para ser executada diretamente pelo Node.JS, utilizando o padrão commonjs. Não usaremos este conceito aqui porque queremos ilustrar como utilizar o TypeScript em um site. 

## Combinando todos os arquivos em um só 

Esta forma é a mais simples e pode ser usada na maioria dos seus projetos web. Vamos inicialmente criar a pasta `teste1` e nela criaremos duas pastas: `src` e `build`. A pasta src contém o código fonte da aplicação, os arquivos TypeScript. A pasta build conterá o código JavaScript gerado pelo TypeScript. Na pasta `src`, criaremos 3 arquivos: 

**pessoa.ts**

<pre>class Pessoa{
	nome : string;
	constructor(nome:string){
		this.nome = nome;
	}
}
</pre>

Este primeiro arquivo é uma classe simples, com um parâmetro e o método construtor. A próxima classe será chamada de `Aluno`, que irá estender da classe `Pessoa`. Como a classe Aluno usa a classe Pessoa (que está em outro arquivo), precisamos importá-la e isso é feito da seguinte forma: `/// <reference path="" />`. O parâmetro `path` é justamente a classe que se deseja referenciar. Então temos:

**aluno.ts**

<pre>/// &lt;reference path="pessoa.ts" /&gt;

class Aluno extends Pessoa{
	matricula : string;
	
	constructor(nome:string,matricula:string){
		super(nome);
		this.matricula=matricula;
	}
}
</pre>

Nesta classe referenciamos na primeira linha a classe `Pessoa`, informando o nome do arquivo `pessoa.ts`. Depois criamos a classe `Aluno`, que herda de Pessoa. Na classe `Aluno` criamos o parâmetro `matricula`, e no seu construtor usamos a palavra `super` para referenciar o construtor da classe pai, que neste caso é `Pessoa`.

Com as duas classes prontas, podemos finalmente criar o arquivo `index.ts`, que é o arquivo principal do projeto.

**index.ts**

<pre>/// &lt;reference path="aluno.ts" /&gt

var a = new Aluno("Joãozinho","0001");
</pre>

> Veja que não é preciso adicionar a classe pessoa. Ela será adicionada na classe aluno

Veja que o arquivo principal faz uma referência a classe `Aluno`, do arquivo `aluno.ts`. Com os três arquivos prontos, podemos usar o comando `tsc` para compilar tudo em um único arquivo. Este comando é executado a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts05.png" alt="ts05" width="819" height="580" class="aligncenter size-full wp-image-52470" />

Nesta imagem usamos o comando `tree` do DOS apenas para mostrar que o arquivo `script.js` foi criado. O principal comando é o:

<pre>tsc ./src/index.ts --out ./build/script.js
</pre>

Este comando possui como primeiro parâmetro o arquivo ts inicial que neste caso é o `index.ts`. O parâmetro `--out` indica o nome do arquivo que será gerado pela compilação do TypeScript em JavaScript. Este arquivo é exibido a seguir:

**build/script.js**

<pre>var Pessoa = (function () {
    function Pessoa(nome) {
        this.nome = nome;
    }
    return Pessoa;
})();
/// &lt;reference path="pessoa.ts" /&gt;
var __extends = (this && this.__extends) || function (d, b) {
    for (var p in b) if (b.hasOwnProperty(p)) d[p] = b[p];
    function __() { this.constructor = d; }
    d.prototype = b === null ? Object.create(b) : (__.prototype = b.prototype, new __());
};
var Aluno = (function (_super) {
    __extends(Aluno, _super);
    function Aluno(nome, matricula) {
        _super.call(this, nome);
        this.matricula = matricula;
    }
    return Aluno;
})(Pessoa);
/// &lt;reference path="aluno.ts" /&gt;
var a = new Aluno("Joãozinho", "0001");
</pre>

## Utilizando módulos

O uso de módulos na aplicação faz com que as classes não pertençam mais ao escopo global, como Pessoa e Aluno pertenciam no exemplo anterior. Vamos fazer uma refatoração no código e adicionar a criação de módulos no escopo da aplicação. Suponha que a classe Pessoa pertença ao módulo &#8220;comum&#8221; e que a classe Aluno pertença ao módulo &#8220;ensino&#8221;.

**pessoa.ts**

<pre>&lt;u><strong>module</strong>&lt;/u> comum {
	<strong>&lt;u>export&lt;/u></strong> class Pessoa{
		nome : string;
		constructor(nome:string){
			this.nome = nome;
		}
	}
}
</pre>

Deixamos sublinhado as 2 palavras que são novidade neste código. A primeira é a palavra `module`, seguida do nome do seu módulo que neste caso é &#8220;comum&#8221;. Dentro do módulo &#8220;comum&#8221; temos a classe Pessoa, e nela usamos a palavra `export` que diz ao módulo que esta classe é pública ao módulo. Podemos incluir no módulo classes, variáveis, métodos etc. Para expôr estas classes a outros módulos, usamos export.

A classe Aluno é refatorada para o seguinte código: 

**aluno.ts**

<pre>/// &lt;reference path="pessoa.ts" /&gt;
module ensino{
	export class Aluno extends <strong>&lt;u>comum.Pessoa&lt;/u></strong>{
		matricula : string;
		
		constructor(nome:string,matricula:string){
			super(nome);
			this.matricula=matricula;
		}
	}
}
</pre>

A classe Aluno agora é do módulo `ensino` e como novidade temos a referência da classe Pessoa como `comum.Pessoa`. Isso é necessário já que estamos modularizando a aplicação. Finalmente, a classe `index.ts` é refatorada para:

**index.ts**

<pre>/// &lt;reference path="aluno.ts" /&gt;

var a = new ensino.Aluno("Joãozinho","0001");
</pre>

Como novidade temos a chamada da classe Aluno como `ensino.Aluno`. Com estas mudanças, podemos executar novamente a compilação:

<pre>tsc ./src/index.ts --out ./build/script.js
</pre>

e obteremos o seguinte resultado:

**build/script.js**

<pre>var comum;
(function (comum) {
    var Pessoa = (function () {
        function Pessoa(nome) {
            this.nome = nome;
        }
        return Pessoa;
    })();
    comum.Pessoa = Pessoa;
})(comum || (comum = {}));
var __extends = (this && this.__extends) || function (d, b) {
    for (var p in b) if (b.hasOwnProperty(p)) d[p] = b[p];
    function __() { this.constructor = d; }
    d.prototype = b === null ? Object.create(b) : (__.prototype = b.prototype, new __());
};
/// $lt;reference path="pessoa.ts" /&gt;
var ensino;
(function (ensino) {
    var Aluno = (function (_super) {
        __extends(Aluno, _super);
        function Aluno(nome, matricula) {
            _super.call(this, nome);
            this.matricula = matricula;
            console.log(this.matricula);
        }
        return Aluno;
    })(comum.Pessoa);
    ensino.Aluno = Aluno;
})(ensino || (ensino = {}));
/// $lt;reference path="aluno.ts" /&gt;
var a = new ensino.Aluno("Joãozinho", "0001");
</pre>

## Módulos em diretórios

Geralmente a organização de módulos é feita em diretórios, para que todos os arquivos não fiquem em somente um único diretório. No caso anterior, poderíamos (na verdade deveríamos) criar os diretórios `src/comum` e `src/ensino` e reorganizar as classes de acordo com a imagem a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts06.png" alt="ts06" width="186" height="256" class="aligncenter size-full wp-image-52476" />

A única mudança que precisamos realizar no código é no `reference`, que deverá ser:

<pre>/// &lt;reference path="../comum/pessoa.ts" /&gt;
</pre>

Na classe aluno, como temos que subir um nível para encontrar o diretório &#8220;comum&#8221;, usamos &#8220;../&#8221;.

<pre>/// &lt;reference path="ensino/aluno.ts" /&gt;
</pre>

No arquivo index.ts, não precisamos usar &#8220;../&#8221; pois estamos no mesmo nível do diretório `ensino`.

## Módulos externos com requirejs

Até este momento todos os módulos estão em um único arquivo de saída, o `build/script.js`. Agora desejamos criar uma forma de carregar os módulos sob demanda, ou seja,
  
ao invés de carregar tudo de uma vez, vamos carregando os arquivos javascript na medida que eles forem sendo requisitados. Para isso precisamos criar uma estrutura um pouco mais complexa, e também precisaremos utilizar um framework qualquer para carregar módulos. Neste caso usamos o `Requirejs`. 

### Criando a estrutura inicial

Crie uma nova pasta e copie os arquivos Pessoa.ts, Aluno.ts e index.ts com a mesma estrutura anterior. Ao invés de criarmos o diretório &#8220;build&#8221;, crie o diretório &#8220;public&#8221;, conforme a imagem a seguir.

 <img src="http://tableless.com.br/uploads/2015/12/ts07.png" alt="ts07" width="181" height="292" class="aligncenter size-full wp-image-52478" />

### Redefinido as classes

Ao utilizarmos módulos externos precisamos alterar a forma como referenciamos as classes. Ou seja, não usaremos mais o `<reference path="../comum/pessoa.ts" />` conforme aprendemos, e não será necessário neste momento definir um módulo. Vamos aos ajustes:

**comum/pessoa.ts**

<pre>export class Pessoa{
	nome : string;
	constructor(nome:string){
		this.nome = nome;
	}
}
</pre>

O que temos agora é o fim do `module` e o uso do `export` antes do nome da classe. Na classe Aluno, temos:

**ensino/aluno.ts**

<pre>&lt;u><strong>import comum = require("../comum/pessoa")</strong>&lt;/u>

export class Aluno extends comum.Pessoa{
	matricula : string;
	
	constructor(nome:string,matricula:string){
		super(nome);
		this.matricula=matricula;
	}
}
</pre>

Alem do fim da palavra `module` e do uso do `export`, temos uma importante alteração na primeira linha do arquivo _aluno.ts_. Estamos utilizando a seguinte sintaxe:

<pre>import MODULO = require("caminho");
</pre>

Aqui tivemos uma inversão do uso do nome do módulo. Se antes definimos o nome do módulo como &#8220;comum&#8221; na classe &#8220;pessoa&#8221;, agora definimos na própria classe &#8220;aluno&#8221;. Como temos agora o `import comum`, podemos usar `comum.Pessoa`. O arquivo `index.js` é refatorado para:

**index.js**

<pre>import ensino = require("ensino/aluno")

var a = new ensino.Aluno("Joãozinho","0001");
</pre>

### Instalando o requirejs

Precisamos instalar o requirejs no projeto, e podemos fazer isso com npm, através do comando `npm i requirejs --save`. Este comando irá instalar o`` no diretório `node_modules` do seu projeto. Se isso não acontecer, execute antes o comando `npm init` para inicializar o repositório npm no projeto. Após instalar o requirejs, copie o arquivo `node_modules/requirejs/require.js` para a pasta `public/js`. Se você não está confortável com o uso do npm para instalar o requirejs, utilize o seguinte CDN:

<pre>&lt;script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.22/require.min.js" data-main="js/index.js"&gt;&lt;/script&gt;
</pre>

### Configurando o arquivo index.html

O arquivo `index.html` é configurado da seguinte forma:

**public/index.html**

<pre>&lt;html&gt;
	&lt;head&gt;
		&lt;title&gt;TypeScript Modules&lt;/title&gt;
		&lt;script src="js/require.js" data-main="js/index.js"&gt;&lt;/script&gt;
	&lt;/head&gt;
	&lt;body&gt;
		Olá Mundo....
	&lt;/body&gt;
&lt;/html&gt;
</pre>

Neste simples arquivo apenas incluímos o `require.js` que foi copiado do `node_modules` e usamos o atributo `data-main="js/index.js"` para informar o arquivo no qual será carregado inicialmente. 

### Compilando a aplicação

Aliás este arquivo ainda não foi criado, já que não executamos o comando `tsc`. O comando para compilar o JavaScript para que o requirejs possa entendê-lo é o seguinte:

<pre>tsc ./src/index.ts --outDir ./public/js/ --module "amd"
</pre>

Neste comando indicamos como primeiro parâmetro `./src/index.ts` o arquivo inicial no qual será compilado. O parâmetro `--outDir ./public/js/` indica o diretório de saída da compilação, neste caso será o diretório `public/js`, o mesmo onde se encontra o arquivo require.js. O terceiro parâmetro `--module "amd"` indica a forma como o tsc vai compilar os arquivos, onde AMD significa `Asynchronous Module Definition`. Após executar este comando, os arquivos jsvascript serão criados na pasta `public/js` conforme a imagem a seguir.

<img src="http://tableless.com.br/uploads/2015/12/ts08.png" alt="ts08" width="1171" height="580" class="aligncenter size-full wp-image-52480" />

### Executando no navegador

Chegou o momento de testar o carregamento dinâmico das classes javascript, e para isso você precisa usar um servidor web. Se você possui um servidor web como o apache, basta copiar a pasta `public` para o diretório web e testá-la. Caso negativo, podemos usar o **live-server** que é facilmente instalado através do node: `npm i live-server /g`. Após instalar, acesse o diretório public pela linha de comando e digite o comando `live-server`. O navegador será aberto automaticamente e o arquivo `index.html` será carregado.

Você verá a mensagem _Olá mundo_, mas o que estamos interessados é no carregamento dos arquivos javascript da aplicação. Para isso, se estiver no Chrome, tecle F12, navegue até a aba Networking e recarregue a aplicação com F5. Você obterá um resultado semelhante a figura a seguir. <img src="http://tableless.com.br/uploads/2015/12/ts09.png" alt="ts09" width="960" height="677" class="aligncenter size-full wp-image-52481" />

## Conclusão

Neste artigo criamos duas formas para utilizar TypeScript no qual os arquivos estão inicialmente separados. A primeira é utilizando o padrão do TypeScript e o `/// <reference path="arquivo.ts" />` e a segunda é usando `requirejs` para carregar os arquivos javascript via ajax. Para que você possa se aprofundar ainda mais neste conceito, que é complexo, sugiro a leitura da documentação: <a href="http://www.typescriptlang.org/Handbook#modules" target="_blank">http://www.typescriptlang.org/Handbook#modules</a>

 [1]: http://tableless.com.br/diga-ola-ao-typescript-e-adeus-ao-javascript/