---
title: Porque o Codeigniter ainda é uma boa opção
author: Fernando Vargas
type: post
date: 2015-06-26
excerpt: Neste primeiro post no Tableless enumero vantagens em considerar o Codeigniter uma boa opção como framework PHP.
url: /porque-codeigniter-ainda-e-uma-boa-opcao/
categories:
  - Back-end
  - O Básico
  - PHP
tags:
  - codeigniter
  - mvc
  - php

---
## O que é Codeigniter?

O **Codeigniter** é um _framework_ para desenvolvimento web baseado na arquitetura MVC. Se você não sabe o que significa MVC ou não entende bem o seu funcionamento poderá encontrar maiores informações <a href="http://tableless.com.br/mvc-afinal-e-o-que/" target="_blank">neste post</a> do Tableless.

Este _framework_ apresenta uma estrutura que lhe permite de forma rápida fazer uso de bibliotecas para ganhar tempo e aproveitar a reutilização de código. Entenda este _framework_ como um kit de ferramentas que tornarão seu ambiente de desenvolvimento ainda mais rápido.

## Porque o Codeigniter ainda é uma boa opção?

  * Possui uma excelente documentação: considere documentação imprescindível para qualquer ferramenta de desenvolvimento que você usar. Sem documentação suficiente você sofre muito para fazer coisas que deveriam ser simples;
  * Permite de forma não tão complexa ter um _engine_ segura;
  * Não precisa instalar \o/;
  * Você não terá problemas para estender classes se precisar (e acredite, você vai precisar 😀 );
  * Não precisa se preocupar tanto com pré-requisitos em servidores;
  * É muito leve em relação a outros _frameworks_;
  * Não será descontinuado tão cedo. O medo já passou;
  * Mantém-se atualizado;
  * Está entre os _frameworks_ PHP favoritos para 2015 (<a title="frameworks PHP favoritos 2015" href="http://icl.googleusercontent.com/?lite_url=http://blog.a-way-out.net/blog/2015/03/27/php-framework-benchmark/&ei=UJ3_QIlA&lc=pt-BR&s=1" target="_blank">veja aqui</a>);

Se você nunca usou o Codeigniter, veja dicas e técnicas de utilização hackeando a <a title="codeigniter" href="http://www.codeigniter.com/" target="_blank">documentação aqui</a>.

## Faça seu Hello World com o Codeigniter

Acesse a página inicial do Codeigniter para fazer <a href="http://www.codeigniter.com/download" target="_blank">download</a> da versão atual do _framework_. A versão utilizada para a realização deste post é a 3.0.

Para que você possa fazer uso do _framework_ será necessário a utilização de um servidor local. Você pode usar, por exemplo, ferramentas como o <a href="https://www.apachefriends.org/pt_br/index.html" target="_blank">Xampp</a>, que possui Apache, PHP e MySql disponíveis.

Após isto, descompacte o conteúdo do arquivo que você baixou no site do Codeigniter e mova o seu conteúdo para a pasta do servidor, no caso do Xampp (usando o Windows) ficaria em C:\xampp\htdocs.

Colocando a pasta do Codeigniter neste local será possível visualizar uma estrutura como a que segue:

<img class="aligncenter wp-image-49601 size-full" src="http://tableless.com.br/uploads/2015/05/estrutura-inicial-codeigniter.png" alt="estrutura do codeigniter" width="688" height="273" />

Dentro da pasta _application_, ficarão todos os arquivos importantes para o desenvolvimento da sua aplicação.  Na pasta _system_ ficam o que podemos chamar de &#8220;_kernel_&#8221; do _framework_, mas isso é assunto para outro momento. 😀

Dentro da pasta _application_ você encontrará duas pastas importantes para o nosso &#8220;_Hello World_&#8220;, sendo elas: a pasta _controller_ e a pasta _views_. Novamente, se você tem dúvidas sobre a nomenclatura destas pastas e como funciona a arquitetura MVC, <a href="http://tableless.com.br/mvc-afinal-e-o-que/" target="_blank">este post</a> pode te auxiliar.

Com o Apache inicializado, acesse o endereço: **_http://localhost/CodeIgniter-3.0.0/_**. Será possível ver seu Codeigniter funcionando conforme a imagem a seguir:

[<img class="alignnone wp-image-49602 size-full" src="http://tableless.com.br/uploads/2015/05/screenshot-localhost-2015-06-17-10-47-23.png" alt="Tela - Seja bem vindo ao Codeigniter" width="1512" height="394" />][1]

Ao acessar a pasta _controller_ será possível visualizar o controlador responsável pela exibição desta tela. Dentro do arquivo também será possível verificar qual a _view_ chamada para exibir os dados na tela.

Acesse a _view_ existente (na pasta _views_) e você poderá alterar o conteúdo HTML a ser exibido, como no exemplo abaixo:

[<img class="aligncenter wp-image-49603 size-full" src="http://tableless.com.br/uploads/2015/05/screenshot-localhost-2015-06-17-10-51-21.png" alt="Conteúdo HTML Hello World com Codeigniter" width="302" height="141" />][2]

Ao acessar os arquivos conforme explicado neste post você verá como é fácil a realização deste exemplo. Até breve \o/

 [1]: http://tableless.com.br/uploads/2015/05/screenshot-localhost-2015-06-17-10-47-23.png
 [2]: http://tableless.com.br/uploads/2015/05/screenshot-localhost-2015-06-17-10-51-21.png