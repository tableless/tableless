---
title: JavaScript com café, parte 2
author: Davi Ferreira
type: post
date: 2012-05-29
excerpt: Conheça conceitos avançados sobre a linguagem CoffeeScript. Aprenda a utilizar classes, escopo e operadores existenciais.
url: /javascript-com-cafe-parte-2/
tweetbackscheck:
  - 1356393277
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6193";s:7:"tinyurl";s:26:"http://tinyurl.com/7ytcsho";s:4:"isgd";s:19:"http://is.gd/pGFqWH";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 707047908
categories:
  - Código
  - JavaScript
tags:
  - coffeescript
  - JavaScript

---
No [artigo anterior][1] vimos as funcionalidades básicas da linguagem CoffeeScript. Falamos sobre variáveis, funções, objetos, condicionais, loops e integração com jQuery. Neste artigo, veremos algumas implementações mais avançadas, com destaque para o conceito de classes.

## Splats

Uma função em CoffeeScript pode receber um ou mais parâmetros definidos em sua especificação. Através de _splats_ (&#8230;) podemos definir também parâmetros variáveis, ou seja, você pode passar quantos parâmetros quiser. Estes parâmetros serão convertidos pelo compilador CoffeeScript em um _array_:

[cce lang=&#8221;coffeescript&#8221;]lista_autores = (site, autores…) ->
      
$(&#8220;#nome-site&#8221;).text site
      
$(&#8220;#autores&#8221;).text autores.join(&#8220;,&#8221; )[/cce]

O código acima resulta no seguinte JavaScript:

[cce lang=&#8221;javascript&#8221;]var lista_autores,
    
__slice = [].slice;
    
lista_autores = function() {
    
var autores, site;
    
site = arguments[0], autores = 2 <= arguments.length ? __slice.call(arguments, 1) : [];
    
$("#nome-site").text(site);
    
return $("#autores").text(autores.join(","));
  
};[/cce]

Poderíamos, então, chamar a função **lista_autores** passando **n** autores nos argumentos:

[cce lang=&#8221;coffeescript&#8221;]lista_autores &#8220;Tableless&#8221;, &#8220;Davi Ferreira&#8221;, &#8220;Diego Eis&#8221;, &#8220;Zeno Rocha&#8221;
  
lista_autores &#8220;DaviFerreira.com&#8221;, &#8220;DaviFerreira&#8221;, &#8220;Chico Stallone&#8221;[/cce]

## Classes

Em JavaScript, classes e objetos são uma coisa só. Um objeto não é uma instância de uma classe, como em outras linguagens. Podemos dizer que tudo é um objeto e existem _prototypes_. Um _prototype_ é um objeto que possui suas propriedades compartilhadas por outros objetos. CoffeeScript faz uso deste recurso para criar Classes e Objetos.

Vejamos a declaração de uma classe:

[cce lang=&#8221;coffeescript&#8221;]class Jogador
    
constructor: (nome, time) ->
      
@nome = nome
      
@time = time
      
@jogos = []
      
Jogador.total_jogadores++

total_jogos: ->
      
console.log @jogos.length

adiciona_jogo: (jogo) ->
      
@jogos.push(jogo)

@total_jogadores = 0[/cce]

Desconstruindo o código, o _constructor_ da classe, compilado em JavaScript, vira uma função com o mesmo nome do objeto. Os métodos _total_jogos_ e _adiciona_jogo_ são _prototypes_ do objeto Jogador. E, por fim, a variável _total_jogadores_ faz referência à classe Jogador, ou seja, ao objeto original que dá origem às instâncias de jogadores. Por exemplo:

[cce lang=&#8221;coffeescript&#8221;]j1 = new Jogador &#8220;Zico&#8221;, &#8220;Flamengo&#8221;
  
j1.nome # &#8220;Zico&#8221;
  
j1.time # &#8220;Flamengo&#8221;
  
Jogador.total_jogadores # 1

j2 = new Jogador &#8220;Roberto Dinamite&#8221;, &#8220;Vasco&#8221;
  
j2.nome # &#8220;Roberto Dinamite&#8221;
  
j2.time # &#8220;Vasco&#8221;
  
Jogador.total_jogadores # 2[/cce]

Portanto, existem três diferentes tipos de propriedades em uma classe CoffeeScript: 1) o _constructor_ da classe, 2) métodos (_prototypes_) e propriedades referentes à uma instância da classe e 3) métodos e propriedades referentes ao objeto &#8220;pai&#8221; da classe.

## Herança

Em JavaScript, a herança entre classes é feita através do encadeamento de _prototypes_. Esse encadeamento pode ser bem confuso quando falamos de muitos objetos. A linguagem CoffeeScript resolve esse problema implementando o recurso _extends_. 

[cce lang=&#8221;coffeescript&#8221;]class Goleiro extends Jogador
    
constructor: (nome, time) ->
      
super nome, time
      
@gols_sofridos = []
      
Goleiro.total_goleiros++

adiciona\_gol\_sofrido: (gol) ->
      
@gols_sofridos.push(gol)

total\_gols\_sofridos: ->
      
console.log @gols_sofridos.length

@total_goleiros = 0[/cce]

Notem a chamada especial _super_, que invoca o método _constructor_ da classe Jogador. Um objeto Goleiro herda todos os métodos da classe pai (Jogador) e pode ainda sobrescrever e/ou ter seus próprios métodos e propriedades.

## Escopo

É comum uma aplicação CoffeeScript vir separada em módulos. Cada módulo, como vimos no artigo anterior, está encapsulado em uma função anônima autoexecutável. E se quisermos compartilhar variáveis e funções entre os módulos?

Para isso, precisamos definir um escopo global, criando um elemento _root_, por exemplo.

[cce lang=&#8221;coffeescript&#8221;]root = global ? window

root.site = &#8220;Tableless&#8221;
  
root.lista_autores = (autores) ->
    
console.log autores.join(&#8220;, &#8220;)[/cce]

Dessa forma, qualquer módulo tem acesso à variável _site_ e à função _lista_autores_.

## Switches

Assim como outros exemplos, um _switch_ em CoffeeScript é infinitamente mais bonito e legível do que sua parte original em JavaScript. Como em Ruby, um _switch_ CoffeeScript aceita múltiplos argumentos em um caso:

[cce lang=&#8221;coffeescript&#8221;]switch time
    
when &#8220;Flamengo&#8221; then console.log &#8220;Primeira Divisão&#8221;
    
when &#8220;Vasco&#8221;, &#8220;Botafogo&#8221; then console.log &#8220;Segunda Divisão&#8221;
    
when &#8220;Fluminense&#8221; then console.log &#8220;Terceira Divisão&#8221;[/cce]

O resultado em JavaScript:

[cce lang=&#8221;javascript&#8221;]switch (time) {
    
case &#8220;Flamengo&#8221;:
      
console.log(&#8220;Primeira Divisão&#8221;);
      
break;
    
case &#8220;Vasco&#8221;:
    
case &#8220;Botafogo&#8221;:
      
console.log(&#8220;Segunda Divisão&#8221;);
      
break;
    
case &#8220;Fluminense&#8221;:
      
console.log(&#8220;Terceira Divisão&#8221;);
  
}[/cce]

## Operador existencial

Mais uma vez inspirada em Ruby, CoffeeScript implementa o operador existencial &#8220;?&#8221;. Este operador retorna _true_ exceto se a variável testada for **null** ou **undefined**. 

[cce lang=&#8221;coffeescript&#8221;]time = &#8220;Flamengo&#8221; if primeira\_divisao? and campeao\_mundial?[/cce]

Em JavaScript:

[cce lang=&#8221;javascript&#8221;]var time;

if ((typeof primeira\_divisao !== &#8220;undefined&#8221; && primeira\_divisao !== null) && (typeof campeao\_mundial !== &#8220;undefined&#8221; && campeao\_mundial !== null)) {
    
time = &#8220;Flamengo&#8221;;
  
}[/cce]

Como vimos acima ela também pode ser utilizada para definir variáveis. O exemplo abaixo define a variável _site_ com _root.site_ se essa última existir, caso contrário utiliza o valor &#8220;Tableless&#8221;.

[cce lang=&#8221;coffeescript&#8221;]site = root.site ? &#8220;Tableless&#8221;[/cce]

O operador condicional pode também ser utilizado para evitar uma quebra em encadeamento de métodos. Por exemplo:

[cce lang=&#8221;coffeescript&#8221;]autor = artigo.retorna\_autor?().total\_artigos?.nome [/cce]

Em JavaScript:

[cce lang=&#8221;javascript&#8221;]var autor, _ref;

autor = typeof artigo.retorna\_autor === &#8220;function&#8221; ? (\_ref = artigo.retorna\_autor().total\_artigos) != null ? _ref.nome : void 0 : void 0;[/cce]

Desse modo, ao invés de _TypeError_, o código acima retornaria **undefined** quando qualquer um dos métodos da cadeia for **null** ou **undefined**.

## Ferramentas

Através do console podemos executar todas as operações do compilador e gerar nosso código JavaScript. No entanto, algumas ferramentas facilitam esse trabalho através de interfaces gráficas:

### LiveReload

Meu favorito é o [Live Reload][2], disponível como uma app para Mac e Windows e um comando para Linux. Além de compilar CoffeeScript, o LiveReload utiliza extensões para os navegadores e recarrega a página quando qualquer alteração é realizada no código (não apenas CoffeeScript).

### CodeKit

Lançado recentemente, o aplicativo [CodeKit][3], disponível apenas para Mac, é um concorrente do LiveReload e, além de monitar alterações e recarregar páginas no navegador, conta também com integrações com frameworks, otimização de imagens e validação (lint) de código.

### CoffeeConsole

Outra ferramenta interessante é a extensão [CoffeeConsole][4], para Chrome. Esta extensão adiciona um novo painel ao Chrome Developer Tools, possibilitando a execução de códigos CoffeeScript, similar ao console JavaScript já integrado na ferramenta.

## Mais CoffeeScript

Essa foi uma visão geral da linguagem CoffeeScript que, recentemente, entrou para o [ranking das dez linguagens mais populares no GitHub][5], desbancando ObjectC.

Finalizando, para aprender mais sobre CoffeeScript, indico os seguintes recursos:

  * [The Little Book on CoffeeScript][6] &#8211; Livro disponível na íntegra online e em versões impressa, PDF e para Kindle via O&#8217;Reilly.
  * [A sip of CoffeeScript][7] &#8211; Curso interativo do pessoal da CodeSchool com vídeos e exercícios online. Bem legal!
  * [Smooth CoffeeScript][8] &#8211; Outro livro disponível de graça online e também em PDF. Possui ainda uma versão interativa em HTML5.

 [1]: http://tableless.com.br/javascript-com-cafe/ ""
 [2]: http://livereload.com/ ""
 [3]: http://incident57.com/codekit/ ""
 [4]: https://github.com/snookca/CoffeeConsole ""
 [5]: https://github.com/languages ""
 [6]: http://arcturo.github.com/library/coffeescript/ ""
 [7]: http://www.codeschool.com/courses/coffeescript ""
 [8]: http://autotelicum.github.com/Smooth-CoffeeScript/ ""