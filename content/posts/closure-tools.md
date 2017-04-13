---
title: Closure Tools
author: Leonardo Lima
type: post
date: 2015-01-25
excerpt: Uma excelente ferramenta de minificação de arquivo javascript. Vou falar alguma coisa sobre Closure Tools e alguns exemplos de código fonte.
url: /closure-tools/
categories:
  - Artigos
  - Geral
  - JavaScript
  - Técnicas e Práticas

---
O projeto Closure Tools é mantido por engenheiros do Google, esta ferramenta é utilizada em vários projetos e aplicações web em geral.
  
As aplicações web evoluíram bastante de simples páginas HTML para aplicativos ricos e interativos que proporcionam uma ótima experiência para o usuário final (UX). As web apps de hoje representam um desafio para os desenvolvedores, como por exemplo, você criar e manter o código JavaScript eficiente que baixa rapidamente e trabalha em diferentes navegadores.
  
O Closure Tools ajuda os desenvolvedores a construir aplicações web ricas com ferramentas de desenvolvimento web que são ambas poderosas e eficientes.

## Um otimizador de Javascript

O Closure compiler, como o próprio nome diz, compila o seu arquivo javascript e deixando-o um código de alta performance. O compiler remove o código absoleto, realiza rewrites e minimiza o restante do código fonte, para depois rodar rapidamente.
  
Ele também verifica a sintax, variável e avisa sobre alguns problemas comuns de Javascript.
  
Essas verificações e otimizações ajudam o desenvolvedor a criar web apps com menos erros e deixa o código fonte fácil para manutenção.

## Como se pode utilizar o Closure Compiler

Você pode utilizar o Closure Compiler como:

-Uma aplicação Java open source que pode ser executada por linha de comando;
  
-Uma simples web app;
  
-Um RESTful API;

## Uma biblioteca JavaScript abrangente

Closure Library é uma biblioteca JavaScript ampla, bem testada, modular e cross-browser. Você pode utilizar apenas o que você precisa de um grande conjunto de widgets de interface do usuário reutilizáveis e controles, e de utilitários de nível inferior para a manipulação de DOM, a comunicação do servidor, animação, estruturas de dados, testes unitários, edição de rich-text, e muito mais.

## Um sistema de template fácil

[Closure Templates][1] simplesmente uma tarefa dinamica gerando HTML. Ele tem uma simples sintax que é de fácil compreensão para programadores. Em contraste com tradicionais sistemas de template, que você utiliza um grande template por página, você pode pensar em Closure Templates como sendo pequenos componentes que você utiliza para formar a interface de usuário.O template é utlizado para ambos Javascript e Java, sendo assim você pode utilizar o mesmo template para ambos server e client side. Para o client side, Closure Template é pré-compilado para um Javascript eficiente. 

## Quais os benefícios de utilizar Closure Compiler

&#8211; Eficiência: O Closure Compiler reduz o tamanho do seu arquivo javascript e faz com que ele fique mais eficiente, ajudando sua aplicação a carregar rapidamente e reduzindo se caso precisar de mais largura de banda (bandwidth).

-Verificação de código: O Closure Compiler realiza uma verificação profunda para diagnosticar operações perigosas, ajudando na produção de um arquivo javascript sem bugs e de fácil manutenção. 

## Iniciando com Closure Compiler UI

Uma maneira fácil de se familiarizar com a ferramenta é verifica o que acontece ao otimizar uma simples function no serviço web [Closure Compiler UI][2].
  
Vamos realizar um passo a passo com a ferramenta online.
  
1.Primeiro você vai acessar a url [http://closure-compiler.appspot.com/home][2] ;

2. Ao acessar a página você vera uma simples function, para realizar um teste básico;

[<img src="http://tableless.com.br/uploads/2015/01/Closure-Compiler-Service-2015-01-24-01-41-58.png" alt="Closure Compiler Service 2015-01-24 01-41-58" width="1280" height="663" class="aligncenter size-full wp-image-46694" srcset="uploads/2015/01/Closure-Compiler-Service-2015-01-24-01-41-58.png 1280w, uploads/2015/01/Closure-Compiler-Service-2015-01-24-01-41-58-265x137.png 265w, uploads/2015/01/Closure-Compiler-Service-2015-01-24-01-41-58-400x207.png 400w" sizes="(max-width: 1280px) 100vw, 1280px" />][3]

## Na prática com Closure Compiler Service API

O Closure Compiler Service API é um ótimo lugar para iniciar com poucas linhas de código javascript ou uma url, mas se você gosta de automatizar o processo de otimização do seu arquivo javascript, veja abaixo o que pode ser feito com o Closure Compiler Service API.

  1. Primeiro vamos criar um HTML básico, onde você vai utilizar a API com HTTP POST request. <pre class="lang-html">&lt;html&gt;
  &lt;body&gt;
    &lt;form action="http://closure-compiler.appspot.com/compile" method="POST"&gt;
    &lt;p&gt;Type JavaScript code to optimize here:&lt;/p&gt;
    &lt;textarea name="js_code" cols="50" rows="5"&gt;
    function hello(name) {
      // Greets the user
      alert('Hello, ' + name);
    }
    hello('New user');
    &lt;/textarea&gt;
    &lt;input type="hidden" name="compilation_level" value="WHITESPACE_ONLY"&gt;
    &lt;input type="hidden" name="output_format" value="text"&gt;
    &lt;input type="hidden" name="output_info" value="compiled_code"&gt;
    &lt;br&gt; &lt;br&gt;
    &lt;input type="submit" value="Optimize"&gt;
   &lt;/form&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>

  2. Você pode ver também o exemplo no [JSFIddle][4]. </ol> 
    ## Referência
    
    As informações sobre a ferramenta, foram pesquisadas no site [developers google][5].
    
    ## Conclusão
    
    Ao utilizar a Closure Tools, pude perceber que o tamanho do arquivo depois de compilado diminuiu bastante. Gostei muito das três opções de otimização (WHITESPACE\_ONLY,SIMPLE\_OPTIMIZATIONS e ADVANCED_OPTIMIZATIONS).
  
    Algumas coisas que percebi ao utilizar a ferramenta foi que no final de um alert() coloquei mais de um ponto e vígula e não identificou um erro no código. Agora, em comparação com outras bibliotecas javascripts de minificação, o que me surpreendeu foi o desempenho da Closure Compiler. Então pessoal, depois de utilizar a biblioteca favor deixar comentários.

 [1]: https://www.google.com/url?q=https%3A%2F%2Fdevelopers.google.com%2Fclosure%2Ftemplates
 [2]: https://www.google.com/url?q=http%3A%2F%2Fclosure-compiler.appspot.com%2Fhome
 [3]: http://closure-compiler.appspot.com/home
 [4]: http://jsfiddle.net/leonardo403/mgozvgu0/2/
 [5]: https://developers.google.com/closure/