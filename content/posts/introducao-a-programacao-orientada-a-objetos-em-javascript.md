---
title: Introdução à programação orientada a objetos em Javascript
author: Henrique Schreiner
type: post
date: 2014-09-16
excerpt: Neste post, vamos criar uma pequena classe em javascript que aborda este método, para que possamos entendê-lo de forma simples e aplicar em nossos projetos.
url: /introducao-a-programacao-orientada-a-objetos-em-javascript/
categories:
  - JavaScript

---
Para quem já programa em alguma linguagem de programação (Java, PHP, C#), com certeza já ouviu falar no conceito de orientação à objetos. Apesar do conceito abordar o mesmo assunto (encapsulamento de variáveis, atributos e métodos de uma classe), o mesmo pode ser abordado de forma diferente, dependendo da linguagem utilizada.

Em Javascript, existem diferentes maneiras e métodos para aplicar este conceito de programação (uso de Prototypes, heranças de classe, etc), mas para entendermos melhor o conceito de orientação a objetos, vamos criar uma classe bem simples para mostrar como o conceito pode ser aplicado.

Na maioria das linguagens de programação, a conotação de classe e função (ou método), se diferencia como `classe NomeDaClasse {}` e `function nomeDaFuncao(){}`, geralmente utilizando-se do padrão <a title="Padrão CamelCase" href="http://pt.wikipedia.org/wiki/CamelCase" target="_blank">CamelCase</a>.

Em Javascript, tanto classes como métodos utilizam a conotação **function** (`function NomeDaClasse(){}` e `function nomeDaFuncao(){}`).

## Criando a Classe

Vamos criar uma classe simples chamada **&#8220;Aluno&#8221;**, onde vamos registrar algumas informações como o nome do aluno, a idade e o curso.

<pre class="lang-javascript">function Aluno () {
 var nome;
 var idade;
 var curso;
}
</pre>

Logo abaixo das declarações das variáveis da classe, vamos criar alguns métodos para &#8220;setar&#8221; e &#8220;pegar&#8221; as variáveis:

<pre class="lang-javascript">this.setNome = function (vNome) {
    this.nome = vNome;
  }

  this.setIdade = function (vIdade) {
    this.idade = vIdade;
  }

  this.setCurso = function (vCurso) {
    this.curso = vCurso;
  }

  this.getNome = function () {
    return this.nome;
  }

  this.getIdade = function () {
    return this.idade;
  }

  this.getCurso = function () {
    return this.curso;
  }
</pre>

Verifique que utilizamos o &#8220;**this**&#8221; para referenciarmos objetos/variáveis da própria classe, já os parâmetros em cada método &#8220;set&#8221;, refere-se apenas ao parâmetro passado ao método para atribuição da variável.

Por último, vamos criar um método para mostrar os parâmetros que usamos em nossas variáveis:

<pre class="lang-javascript">this.mostraDados = function () {
    alert("Nome do aluno: " + this.nome + "\nIdade: " + this.idade + "\nCurso: " + this.curso);
  }
</pre>

Com a nossa classe pronta, agora podemos criar um novo objeto, instanciando a classe para usarmos seus métodos:

<pre class="lang-javascript">var Aluno = new Aluno();

Aluno.setNome("Henrique");
Aluno.setIdade("25");
Aluno.setCurso("Introdução à programação orientada a objetos em Javascript");
Aluno.mostraDados();
</pre>

Aqui está um <a title="Exemplo Javascript OO" href="http://jsfiddle.net/hmschreiner/d2x7qgsd/" target="_blank">exemplo</a> de nossa classe funcionando. Coloque seus próprios dados e veja o resultado.

A nossa classe completa ficou assim:

<pre class="lang-javascript">function Aluno () {
 var nome;
 var idade;
 var curso;

  this.setNome = function (vNome) {
    this.nome = vNome;
  }

  this.setIdade = function (vIdade) {
    this.idade = vIdade;
  }

  this.setCurso = function (vCurso) {
    this.curso = vCurso;
  }

  this.getNome = function () {
    return this.nome;
  }

  this.getIdade = function () {
    return this.idade;
  }

  this.getCurso = function () {
    return this.curso;
  }

  this.mostraDados = function () {
    alert("Nome do aluno: " + this.nome + "\nIdade: " + this.idade + "\nCurso: " + this.curso);
  }
}
</pre>

Espero que este artigo ajude a entender o princípio de orientação à objetos em javascript para quem está começando e quer ter uma noção de como começar.
  
**Não deixe de comentar e deixar suas opiniões e dúvidas.**