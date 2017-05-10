---
title: JavaScript com café
author: Davi Ferreira
type: post
date: 2012-04-09
excerpt: Conheça a linguagem CoffeeScript que, diferente dos frameworks e bibliotecas, compila código JavaScript puro ao invés de ser apenas mais uma camada sobre a linguagem.
url: /javascript-com-cafe/
tweetbackscheck:
  - 1356445044
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5840";s:7:"tinyurl";s:26:"http://tinyurl.com/bq5gbzj";s:4:"isgd";s:19:"http://is.gd/URbqAZ";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 642090982
categories:
  - JavaScript
tags:
  - coffeescript
  - JavaScript
  - JQuery

---
CoffeeScript é uma tentativa de tornar JavaScript mais agradável para nós, programadores. 

Diferente dos frameworks e bibliotecas, que foram desenvolvidos como uma camada extra, o código escrito em CoffeeScript é compilado e resulta em JavaScript puro.

A sintaxe é inspirada em linguagens como Ruby e Python (principalmente Ruby), portanto você pode esperar códigos intuitivos e limpos, sem pontos-e-vírgulas, chaves e parênteses (quase).

## Instalação & Comandos

Não vou entrar muito em detalhes sobre a instalação da linguagem. A maneira mais fácil de instalar as ferramentas para desenvolvimento em CoffeeScript é através do sistema de pacotes do NodeJS, o npm.

[cce lang=&#8221;bash&#8221;]npm install -g coffee-script[/cce]

O criador do npm disponibilizou um <a href="https://gist.github.com/579814" title="Instruções para instalação do NodeJS e NPM" target="_blank">gist</a> com instruções variadas para a instalação do NodeJS e seu gerenciador de pacotes. 

Depois de seguir todos os passos necessários, para conferir se a instalação foi concluída com sucesso, digite o seguinte comando em um terminal:

[cce lang=&#8221;bash&#8221;]coffee -v[/cce]

O comando _coffee_, executado via terminal, pode ser utilizado como um console interativo, como um compilador ou como um _watcher_. Como um _watcher_, o comando vigia qualquer alteração em códigos-fonte CoffeeScript e, automaticamente, gera os arquivos JavaScript.

[cce lang=&#8221;bash&#8221;]# executa o console
  
coffee
  
\# compila o arquivo codigo.coffee para codigo.js
  
coffee -c codigo.coffee
  
\# compila o arquivo codigo.coffee para script.js
  
coffee -co script.js codigo.coffee
  
\# observa os arquivos no diretório coffeescripts e compila para o diretório javascripts
  
coffee -cwo javascripts coffeescripts[/cce]

Além disso, ele pode também executar diretamente um script:

[cce lang=&#8221;bash&#8221;]coffee codigo.coffee[/cce]

Uma maneira mais fácil de testar e experimentar CoffeeScript é visitando o link &#8220;Try CoffeeScript&#8221; no <a href="http://coffeescript.org" title="CoffeeScript: Site oficial" target="_blank">site oficial da linguagem</a>. Lá você pode observar, em tempo real, o resultado da transformação de CoffeeScript em JavaScript.

## Variáveis & Funções

A simplificação começa com a declaração de variáveis, eliminando a necessidade de instanciá-las:

[cce lang=&#8221;coffeescript&#8221;]mensagem = "Olá, Tableless!"
  
alert mensagem[/cce]

O código acima resulta no seguinte JavaScript:

[cce lang=&#8221;javascript&#8221;]var mensagem;
  
mensagem = "Olá, Tableless!";
  
alert(mensagem);[/cce]

Já uma função em CoffeeScript é representada pela junção dos caracteres &#8220;-&#8221; e &#8220;>&#8221;:

[cce lang=&#8221;coffeescript&#8221;]cafe = -> "Café!"[/cce]

JavaScript:

[cce lang=&#8221;javascript&#8221;]var cafe;
  
cafe = function() {
    
return "Café!";
  
};[/cce]

O compilador CoffeeScript vai sempre transformar suas funções em expressões, ou seja, funções armazenadas em variáveis.

Vale lembrar que assim como em Python, a indentação em CoffeeScript precisa ser seguida à risca. Seu código deve respeitar um padrão de indentação &mdash; tab ou espaços, nunca os dois ao mesmo tempo.

O valor retornado por uma função é sempre a última linha de sua implementação. Não é necessário utilizar _return_.

Os argumentos devem ser declarados antes do símbolo da função. A concatenação segue o estilo Ruby de ser:

[cce lang=&#8221;coffeescript&#8221;]cafe = (sabor) -> "Quero café #{sabor}!"[/cce]

JavaScript:

[cce lang=&#8221;javascript&#8221;]var cafe;
  
cafe = function(sabor) {
    
return "Quero café " + sabor + "!";
  
};[/cce]

Eles podem ainda possuir valores padrões, caso não seja passado nenhum parâmetro:

[cce lang=&#8221;coffeescript&#8221;]cafe = (sabor = "forte") -> "Quero café #{sabor}!"[/cce]

E, como já deu pra perceber, quando uma função é chamada, os parênteses são opcionais:

[cce lang=&#8221;coffeescript&#8221;]cafe("suave")
  
cafe "suave"
  
[1, 2, 3, 4].slice(0, 1)
  
[1, 2, 3, 4].slice 0, 1[/cce]

## Objetos

Existem duas maneiras de representar objetos em JavaScript. A primeira é utilizando _new_:

[cce lang=&#8221;javascript&#8221;]pessoa = new Pessoa();[/cce]

A maneira mais comum, no entanto, é utilizando a notação JSON:

[cce lang=&#8221;javascript&#8221;]pessoa = {};[/cce]

Este tipo de criação é simplificado no CoffeeScript, com a remoção das chaves e vírgulas, utilizando apenas indentação para formatar o objeto:

[cce lang=&#8221;coffeescript&#8221;]autor =
    
nome: "Davi Ferreira"
    
especialidades: ["javascript", "jquery"]
    
sites:
      
blog: "http://www.daviferreira.com/blog"
      
portfolio: "http://www.daviferreira.com"
    
social:
      
twitter: "davitferreira"[/cce]

Agora o mesmo objeto, em JavaScript:

[cce lang=&#8221;javascript&#8221;]var autor;
  
autor = {
    
nome: "Davi Ferreira",
    
especialidades: ["javascript", "jquery"],
    
sites: {
      
blog: "http://www.daviferreira.com/blog",
      
portfolio: "http://www.daviferreira.com"
    
},
    
social: {
      
twitter: "davitferreira"
    
}
  
};[/cce]

## Operações condicionais e comparativas

As operações condicionais em CoffeeScript são bastante flexíveis e mais poderosas do que as operações nativas em JavaScript. O CoffeeScript introduz novos tipos de implementações de operações condicionais:

[cce lang=&#8221;coffeescript&#8221;]alert "Frio" if temperatura < 20[/cce]
  
[cce lang=&#8221;coffeescript&#8221;]if temperatura < 20 then alert "Frio" else alert "Calor"[/cce]

O segundo exemplo, compilado, fica assim:

[cce lang=&#8221;javascript&#8221;]if (temperatura < 20) {
    
alert("Frio");
  
} else {
    
alert("Calor");
  
}[/cce]

Os operadores também receberam uma repaginada, ganhando versões &#8220;escritas&#8221;:

[cce lang=&#8221;coffeescript&#8221;]if temperatura < 20 and cidade is "Rio de Janeiro" then alert "Frio"[/cce]
  
[cce lang=&#8221;coffeescript&#8221;]if alarme is on and not snooze and hora is "09:00" then alert "Beep!"[/cce]

Javascript:

[cce lang=&#8221;javascript&#8221;]if (alarme === true && !snooze && hora === "09:00") alert("Beep!");[/cce]

Outra implementação legal é a comparação em cadeia:

[cce lang=&#8221;coffeescript&#8221;] if 12 < idade < 18 then alert "Adolescente"[/cce]

Javascript:

[cce lang=&#8221;javascript&#8221;] if (12 < idade && idade < 18) alert("Adolescente");[/cce]

## Loops

Antes de falar sobre operações de _loop_, vamos conhecer _ranges_ ou intervalos. Em CoffeeScript é possível declarar _ranges_ dinâmicos:

\[cce lang=&#8221;coffeescript&#8221;]horas = [0..24\]\[/cce\]

O código acima gera a lista completa, de 0 a 24. O resultado ainda pode ser trabalhado retornando apenas os quatro primeiros valores (0, 1, 2, 3):

\[cce lang=&#8221;coffeescript&#8221;]horas[0..3\] \[/cce\]

A manipulação de dados via loops é bem completa, com diferentes possibilidades:

[cce lang=&#8221;coffeescript&#8221;]times = ["Flamengo", "Vasco", "Botafogo", "Fluminense"]
  
for time in times
    
alert "Time: #{time}"[/cce]

O código acima resulta no seguinte JavaScript (!):

[cce lang=&#8221;javascript&#8221;]var time, times, \_i, \_len;
  
times = ["Flamengo", "Vasco", "Botafogo", "Fluminense"];
  
for (\_i = 0, \_len = times.length; \_i < \_len; _i++) {
    
time = times[_i];
    
alert("Time: " + time);
  
}[/cce]

Outra maneira de executar um _loop_ é declarando tudo em uma única linha:

[cce lang=&#8221;coffeescript&#8221;]alert "Time: #{time}" for time in times[/cce]

Podemos ainda manipular os dados diretamente no _loop_:

[cce lang=&#8221;coffeescript&#8221;]alert "#{time} &#8211; RJ" for time in times[/cce]

E para finalizar essa parte sobre _loops_, uma ferramenta muito útil é a _keyword_ _when_, utilizada para filtrar os dados do _loop_:

[cce lang=&#8221;coffeescript&#8221;]alert "Segunda divisão!" for time in times when time isnt "Flamengo"[/cce]

## Integração com jQuery

Escrever código em CoffeeScript não significa abandonar bibliotecas e frameworks JavaScript. A integração com CoffeeScript é direta:

[cce lang=&#8221;coffeescript&#8221;]$ -> [/cce]

Equivale a:

[cce lang=&#8221;javascript&#8221;]$(function() {});[/cce]

A premissa básica continua sendo a simplificação do código, principalmente devido a remoção de chaves, parênteses, vírgulas e pontos-e-vírgulas.

[cce lang=&#8221;coffeescript&#8221;]$(window).konami ->
	  
$("html").addClass "tremetudo"[/cce]

O código acima é a implementação do Konami Code aqui no Tableless.

Veja o JavaScript original:

[cce lang=&#8221;javascript&#8221;]$(window).konami(function(){
	  
$("html").addClass("tremetudo")
  
});[/cce]

* * *

Essa foi uma visão geral da linguagem. A desvantagem de implementar CoffeeScript em produtos e aplicativos grandes é o fato de ainda ser difícil debugar o código diretamente, já que as ferramentas disponíveis nos navegadores só indicam os erros no arquivo JavaScript gerado. O compilador aponta os erros de sintaxe, mas erros de lógica dão um pouco mais de trabalho.

Muitos aspectos ficaram de fora deste artigo, como os splats, escopo, propriedades, switches, soaks e, principalmente, classes. No próximo artigo falo mais sobre eles.