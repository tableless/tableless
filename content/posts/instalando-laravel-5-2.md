---
title: Instalando Laravel 5.2
author: Eduardo Abreu
type: post
date: 2016-01-13
excerpt: Como instalar e começar a utilizar o framework PHP Laravel 5.2
url: /instalando-laravel-5-2/
categories:
  - Back-end
  - Código
  - PHP
tags:
  - artisan
  - composer
  - Laravel
  - php

---
Neste artigo irei demonstrar como instalar e começar a utilizar o <a class="markup--anchor markup--p-anchor" href="http://laravel.com/" rel="nofollow">Laravel</a> 5.2, framework que vem ganhando visibilidade no mercado.

<p id="42c9" class="graf--p graf-after--p">
  O que iremos utilizar:
</p>

<ul class="postList">
  <li id="1067" class="graf--li graf-after--p">
    <a class="markup--anchor markup--li-anchor" href="http://getcomposer.org/" target="_blank" rel="nofollow">Composer</a>
  </li>
</ul>

<p id="a825" class="graf--p graf-after--li">
  Requisitos do servidor:
</p>

<ul class="postList">
  <li id="e023" class="graf--li graf-after--p">
    PHP versão maior ou igual a 5.5.9;
  </li>
  <li id="9d69" class="graf--li graf-after--li">
    OpenSSL PHP Extension;
  </li>
  <li id="9f4e" class="graf--li graf-after--li">
    PDO PHP Extension;
  </li>
  <li id="f2d1" class="graf--li graf-after--li">
    Mbstring PHP Extension;
  </li>
  <li id="ee0f" class="graf--li graf-after--li">
    Tokenizer PHP Extension;
  </li>
</ul>

#### Instalando o Composer {#00b3.graf--h4.graf-after--li}

<p id="d940" class="graf--p graf-after--h4">
  Na pasta onde localiza-se a aplicação, abra o terminal e digite:
</p>

<pre class="lang-bash">#Caso tenha o Curl instalado
curl -s https://getcomposer.org/installer | php
## ou ##
#Caso não possua o Curl instalado
php -r "readfile('https://getcomposer.org/installer');" | php</pre>

#### Baixando o Laravel Installer {#87d9.graf--h4.graf-after--p}

<p id="25d6" class="graf--p graf-after--h4">
  Para baixar o instalador do Laravel, execute o seguinte comando:
</p>

<pre class="lang-bash">composer global require "laravel/installer"
</pre>

Agora é necessário adicioná-lo ao PATH do sistema, para que ele possa ser executado de qualquer lugar.

<pre class="lang-bash">export PATH="$PATH:$HOME/.composer/vendor/bin"
</pre>

Uma vez feito esta sequência, o comando “laravel” já está disponível para ser usado. Para criar um novo projeto, execute o seguinte comando:

<pre class="lang-bash">laravel new AppName
</pre>

Este comando irá criar toda a estrutura necessária para sua aplicação.

#### Configurando {#e83c.graf--h4.graf-after--p}

<p id="f600" class="graf--p graf-after--h4">
  Todas as configurações do Laravel estão armazenadas no diretório “config” e estão bem documentadas.
</p>

#### Permissões de Pasta {#2c0c.graf--h4.graf-after--p}

<p id="3fdf" class="graf--p graf-after--h4">
  As pastas “storage” e “bootstrap/cache” precisam ter permissão de escrita pelo servidor, ou o Laravel não funcionará corretamente.
</p>

#### Configuração Local {#629e.graf--h4.graf-after--p}

<p id="c0d5" class="graf--p graf-after--h4">
  Em desenvolvimento de softwares é normal termos uma equipe para todo o processo de criação do software, e cada membro da equipe possui suas preferências quanto a nome de banco de dados, senhas etc. Para tratar isto, o Laravel utiliza arquivos “.env” (<a class="markup--anchor markup--p-anchor" href="https://github.com/vlucas/phpdotenv" target="_blank" rel="nofollow">leia mais sobre este projeto</a>). O arquivo .env deve ser ignorado em seu controle de versão. Para criar seu arquivo .env utilize o exemplo do próprio Laravel e altere as configurações de acordo com seu ambiente.
</p>

#### Application Key {#5e69.graf--h4.graf-after--p}

<p id="a431" class="graf--p graf-after--h4">
  O próximo passo é setar a <em>application key</em>, chave de segurança que será utilizada para encriptar dados em sua aplicação. Utilize o comando no Artisan para gerar sua <em>application key</em>.
</p>

<pre class="lang-bash">php artisan key:generate</pre>

#### Testando sua instalação {#61a4.graf--h4.graf-after--figure}

<p id="e0c1" class="graf--p graf-after--h4">
  Para verificar se a instalação está funcionando, utilize o Artisan para subir um servidor <em>built-in</em>. No terminal exibirá um endereço como: http://localhost:8000. Digite o comando &#8220;serve&#8221; (sem r mesmo):
</p>

<pre class="lang-bash">php artisan serve
</pre>

E é isto pessoal, mais nenhuma configuração adicional é necessária para começar a brincar com o Laravel. Agora é com você, pois há muito o que explorar neste fascinante framework. _Regards_!