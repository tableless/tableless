---
title: Instalando o CAKEPHP 3.0 via Composer
author: Eduardo Abreu
type: post
date: 2015-06-07
excerpt: Instalando o CakePHP via Composer.
url: /instalando-o-cakephp-3-0-via-composer/
categories:
  - Back-end
  - Código
  - PHP
tags:
  - cakephp
  - composer
  - php

---
Requisitos do tutorial:

  1. PHP instalado e configurado
  2. Ambiente Linux

No dia 22/03/2015 foi disponibilizado para download no [site do CakePHP][1] a [versão 3.0 do framework para PHP CakePHP][2]. Já utilizamos a versão 2.x em projetos aqui na empresa e tivemos bons resultados.

Com o lançamento desta nova versão, muita coisa mudou: um novo ORM foi lançado; o uso de namespaces foi adotado; entre outras features que iremos abordar em outras publicações.
  
Neste artigo irei realizar um passo a passo da instalação do Cakephp 3.0 [utilizando o Composer][3].

### O que é o Composer

O Composer é o gerenciador de dependências do PHP, com ele é possível definir uma lista de bibliotecas que sua aplicação necessita para funcionar, além de poder definir requisitos como, versão do PHP, extensions etc.

Para aprender mais sobre o Composer, listei alguns artigos abaixo:

  1. <a href="http://tableless.com.br/composer-para-iniciantes/" target="_blank">http://blog.thiagobelem.net/gerenciando-dependencias-com-o-composer/</a>
  2. <a href="http://tableless.com.br/composer-para-iniciantes/" target="_blank">http://tableless.com.br/composer-para-iniciantes/</a>
  3. <a href="http://getcomposer.org ( site oficial)" target="_blank">http://getcomposer.org ( site oficial)</a>

### Instalando o Composer

Na pasta onde irá ficar localizada a aplicação, abra o terminal e digite o seguinte:

<pre class="lang-bash">#Caso tenha o Curl instalado
curl -s https://getcomposer.org/installer | php
## ou ##
#Caso não possua o Curl instalado
php -r "readfile('https://getcomposer.org/installer');" | php</pre>

Documentação do comando usado: <a href="http://php.net/manual/pt_BR/features.commandline.options.php%20http://curl.haxx.se/mail/lib-2004-07/0017.html" target="_blank">http://php.net/manual/pt_BR/features.commandline.options.php</a>
  
 [http://curl.haxx.se/mail/lib-2004-07/0017.html][4]

### Instalando o CakePHP 3

#### Requisitos Mínimos

  1. HTTP Server. Exemplo: Apache, Ngix. Com mod_rewrite habilitado de preferência, mas não é obrigatório.
  2. PHP 5.4.16 ou maior
  3. extensão mbstring
  4. extensão intl (Como instalar/habilitar: http://goo.gl/qz6tqT)

Para instalar o framework, na pasta do projeto onde também o Composer foi instalado e digite o seguinte comando:

<pre class="lang-bash">#Install cakephp3
composer create-project --prefer-dist cakephp/app [nome da app]</pre>

Documentação do comando usado: <a href="https://getcomposer.org/doc/03-cli.md#create-project" target="_blank">https://getcomposer.org/doc/03-cli.md#create-project</a>

Para testar se a aplicação foi instalada com sucesso, acesse a pasta da aplicação, no caso o mesmo nome que digitou em [nome da app] e digite o seguinte comando:

<pre class="lang-bash">#Inicia built-in server
./bin/cake server</pre>

Documentação do comando usado: <a href="http://book.cakephp.org/3.0/en/console-and-shells.html" target="_blank">http://book.cakephp.org/3.0/en/console-and-shells.html</a>

Após, se tudo ocorrer bem, uma mensagem será exibida no terminal informando que o servidor embutido foi iniciado e que se encontra disponível no endereço: http://localhost:8765/.

Por enquanto é só galera, caso tenham alguma dúvida ou problema durante a instalação, ficarei feliz em ajudar.

 [1]: http://cakephp.org
 [2]: http://book.cakephp.org/3.0/en/installation.html
 [3]: http://tableless.com.br/composer-para-iniciantes/
 [4]: http://php.net/manual/pt_BR/features.commandline.options.php%20http://curl.haxx.se/mail/lib-2004-07/0017.html