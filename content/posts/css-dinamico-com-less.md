---
title: CSS dinâmico com LESS
author: Davi Ferreira
type: post
date: 2011-11-16
excerpt: 'Já imaginou poder declarar variáveis, implementar funções e mixins em suas folhas de estilo? Este é objetivo principal da biblioteca LESS: ampliar o funcionamento do CSS, tornando-o altamente dinâmico.'
url: /css-dinamico-com-less/
tweetbackscheck:
  - 1356399713
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4191";s:7:"tinyurl";s:26:"http://tinyurl.com/67zce5y";s:4:"isgd";s:19:"http://is.gd/T6zkWy";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503017843
categories:
  - CSS
  - HTML
tags:
  - CSS
  - LESS

---
O desenvolvimento front-end nunca esteve tão dinâmico. Ferramentas como HAML, SASS e ZenCoding vêm revolucionando a maneira como trabalhamos. Em projetos onde qualquer coisa pode mudar a qualquer hora, flexibilidade é um ponto importantíssimo.

O [LESS][1] chega nesse barco, adicionando um alto nível de personalização e permitindo recursos de programação em folhas de estilo estáticas. Com a biblioteca, é possível utilizar recursos como variáveis, funções, operações e escopo dentro de simples regras CSS.

## Variáveis

Uma das principais funcionalidades do LESS é a criação de variáveis.

<pre class="lang-css">@azul: #4ca5fe;
@cor_link: #df0d32;
@fonte_titulo: bold 25px/25px "Georgia", "Times New Roman", serif; 
</pre>

Variáveis servem para definir valores padrões para seus projetos e facilitar a manutenção e alteração dos mesmos. As variáveis acima poderiam ser utilizadas em diferentes estilos, por exemplo:

<pre class="lang-css">.titulo {
    color: @azul;
    font: @fonte_titulo;
}

.li {
    color: @azul;
}

.li a {
    color: @cor_link;
}
</pre>

## Mixins

Mixin é um conceito de programação orientada a objetos e basicamente representa a utilização de classes dentro de classes. Essas classes não são instanciadas e servem apenas para reaproveitamento de código.

No LESS, mixins são classes/declarações que serão utilizadas dentro de outras classes de estilo.

<pre class="lang-css">.fonte-titulo{
    font-size: 36px;
    font-family: Helvetica, Arial, sans-serif;
    color: #666;
    letter-spacing: -2px;
    font-weight: 700;
}

h1 {
    text-transform: uppercase;
    .fonte-titulo;
}

h2 {
    .fonte-titulo;
    color: #000;
}
</pre>

Variáveis e mixins são as principais ferramentas para evitar uma terrível prática: repetição de código (no nosso caso, repetição de estilos).

## Funções

Estendendo o conceito acima, funções são mixins que recebem parâmetros. Os parâmetros podem ter um valor padrão, como o exemplo _borda_arredondada_ abaixo (6px), que será utilizado caso nenhum parâmetro seja passado.

<pre class="lang-css">.titulo(@azul){
    color: @azul;
    border: 1px dotted @azul;
}

.borda_arredondada(@radius: 6px){
    border-radius: @radius;
    -moz-border-radius: @radius;
    -webkit-border-radius: @radius;
}

.thumbnail{
    background: #ccc;
    .borda_arredondada(10px);
}

.foto_materia{
    background: #000;
    padding: 4px;
    .borda_arredondada;
}
</pre>

## Regra dentro de regra dentro de regra&#8230;

Alguns desenvolvedores já aplicam essa técnica visualmente. No entanto, com LESS, as regras aninhadas também herdam os valores de seus &#8220;pais&#8221;.

<pre class="lang-css">#menu {
    letter-spacing: -2px;
    color: @azul;

    .item {
        padding: 2px;
        margin: 2px;
    
        &.inactive {
            color: #666;
        }

        &:hover {
            color: red;
        }
    
    }

}
</pre>

Note o símbolo &#8220;&&#8221; que representa a concatenação. O elemento não herda simplesmente os atributos de seu antecessor, ele também sobrescreve o novo valor. Essa regra é importantíssima para pseudo-elementos como :hover, :focus etc.

## Operações

O LESS também permite operações com valores e cores. Por exemplo, é possível multiplicar uma cor hexa-decimal ou dividir uma certa quantidade em pixels.

As funções de cores englobam efeitos como dessaturação e fade.

Para valores compostos, como o border do div#conteudo abaixo, é obrigatório o uso de parênteses.

<pre class="lang-css">@borda_padrao: 6px;
@cor_padrao: #111;

div#conteudo {
    color: @cor_padrao * 2;
    border: (@borda_padrao / 3) solid #ccc;
}

div#menu { 
    color: darken(@cor_padrao, 10%);
}
</pre>

Na [documentação oficial do LESS][1] você encontra uma lista completa das funções para cores.

## Escopo & Namespace

Para quem já programa, os conceitos explicados até agora são familiares. O LESS nada mais é do que um framework que transforma o CSS em uma pseudo linguagem de programação.

Escopo é outro conceito importante em programação que também está presente no LESS.

Uma variável possui um escopo global e outro local, dentro de sua função/mixin. O LESS vai sempre procurar primeiro por varáveis no escopo local e depois em seus antecessores.

<pre class="lang-css">@variavel: 1px;

div#conteudo {
    @variavel: 2px;
    div#titulo {
        border-size: @variavel;
    }
}

div#menu {
    border-size: @variavel;
}
</pre>

Você também pode reutilizar apenas uma parte de um mixin aplicando um namespace para encapsular seu código.

<pre class="lang-css">#titulo {
    .principal {
        font-size: 36px;
        letter-spacing: -2px;
    }
    .secundario {
        font-size: 24px;
        letter-spacing: -1.4px;
    }
}

#header h1 {
    color: #df0d32;
    #titulo &gt; .principal;
}
</pre>

O h1 do elemento #header herda apenas o .principal do #titulo.

## Implementações

A implementação do LESS pode ser feita _on the fly_, com JavaScript. Esse método é recomendado para sites pequenos, com pouca audiência. Para sites mais visitados, pré-processe seus arquivos LESS, transformando-os em folhas de estilo estáticas.

Por exemplo, para aplicativos Ruby/Rails existe uma [gem][2] que converte arquivos LESS para CSS. Já o o módulo _compressor_ do Django oferece suporte nativo.

<img src="http://tableless.com.br/uploads/2011/09/less.jpg" alt="Screenshot do aplicativo LESS para Mac OS" width="620" height="354" class="aligncenter size-full wp-image-4535" srcset="uploads/2011/09/less.jpg 620w, uploads/2011/09/less-300x171.jpg 300w" sizes="(max-width: 620px) 100vw, 620px" />

Outra solução bacana é o [aplicativo LESS para Mac][3].

E se você procura elementos básicos já prontos, a dica é visitar o site [Less Elements][4]. Nele você encontra soluções para bordas, degradês e sombras.

 [1]: http://lesscss.org/#-color-functions ""
 [2]: http://rubygems.org/gems/less ""
 [3]: http://incident57.com/less/ ""
 [4]: http://lesselements.com/ ""