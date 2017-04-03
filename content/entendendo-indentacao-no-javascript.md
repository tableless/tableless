---
title: Entendendo a indentação no Javascript
author: Júlio Carneiro
type: post
date: 2016-07-06
url: /entendendo-indentacao-no-javascript/
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - indentação
  - JavaScript

---
Código sem indentação não é legal de se ler, mas tem uma coisa um pouco pior que isso, ou tão ruim quanto, que é a falta de um padrão na indentação do projeto. Por exemplo, eu uso tab pois consigo ajustar meu editor para que ele exiba a quantidade que eu julgue necessária de espaços, mas pode ser que alguém da minha equipe use os próprios espaços, eai já imagina a beleza que vai ficar o código né? É **MUITO** importante **padronizar** o uso da indentação para não ter problemas futuros.

_Para quem usa espaços, o padrão de validação do_ **_JSLint_** _por exemplo é de 4 (apesar de ser customizável a sua escolha), e é este que vamos usar neste artigo._

#### O que deve ser indentado?

Mas o que será que eu indento? O que precisa ser indentado? Simples, qualquer coisa dentro de chaves. <strong class="markup--strong markup--p-strong">Funções, loops, ifs, switches e propriedades de objetos</strong>, vou mostrar a baixo exemplos de indentação:

<pre class="lang-js">function algumaFuncao(a, b) {
    var c = 1,
        d = 2,
        inner;
    if (a &gt; b) {
        inner = function() {
        return {
            r: c - d
        };
    };
    } else {
        inner = function () {
            return {
                r: c + d
            };
        };
    }
    return inner;
}
</pre>

Caso você tenha apenas uma instrução em um **if** ou **for**, as chaves não são obrigatórias, porem, mesmo que sejam opcionais é importante **sempre usa-las**. Isto faz com que seu código seja mais fácil de dar manutenção pois outras pessoas vão entende-lo melhor.

Exemplo, imagina que você tenha um **loop for** com uma instrução. Você pode optar por não por as chaves e mesmo assim não haveriam erros de sintaxe:

<pre class="lang-js">for (var i = 0; i &lt; 10; i += 1)
    alert(i);
</pre>

E se caso mais tarde você decidir adicionar outra linha no loop?

<pre class="lang-js">for (var i = 0; i &lt; 10; i += 1)
    alert(i);
    alert(i + &#039; is &#039; +(i % 2 ? &#039;odd&#039; : &#039;even&#039;));
</pre>

O segundo **alert()** está fora do **loop** neste caso, apesar da indentação estar tentando te enganar. Por isso temos que **sempre usar as chaves**, pois evitamos ter problemas futuros, precisamos pensar a longo prazo aqui.

#### Chave de abertura

Tendemos a ter preferência sobre onde colocar a chave de abertura no código, uns preferem por na **mesma linha**, outros na **linha seguinte**, veja:

<pre class="lang-js">if (true){
    alert('É true!')
}
</pre>

Ou:

<pre class="lang-js">if (true)
{
    alert('É true!')
}
</pre>

Neste exemplo é uma questão de preferência porém, em alguns casos o programa pode se comportar diferentemente, dependendo de onde a chave está. Isto ocorre por causa do _mecanismo de inserção de ponto e vírgula — _o JS não alarma caso você queira não terminar suas linhas com ponto e vírgula, pois neste caso **ele adiciona para você**. Isso pode causar problemas quando uma função retorna um objeto literal e a chave de abertura está na linha seguinte:

<pre class="lang-html">function func() {
    return
    {
        nome: 'Julio'
    };
}
</pre>

Se você queria que sua função retornasse o objeto “**nome**”, você vai ter uma surpresa, experimente rodar no seu console do node e ver o resultado para melhor compreender. Por causa dos pontos e vírgulas a função retorna “**undefined”**.

Concluindo:
  
Sempre usar chaves, e sempre colocar a de abertura na mesma linha da instrução anterior:

<pre class="lang-js">function func() {
    return {
        nome: 'Julio'
    };
}
</pre>

Espero que tenham curtido, e que eu possa ter contribuído com o conhecimento de quem acessa o Tableless, este é meu objetivo em geral, ajudar! Abraços, te espero no próximo post!