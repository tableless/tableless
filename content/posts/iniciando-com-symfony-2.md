---
title: Iniciando com Symfony 2
author: Candido Souza
type: post
date: 2015-01-21
excerpt: Neste simples tutorial, vamos fazer a instalação do Symfony 2 e abordar alguns conceitos inicias.
url: /iniciando-com-symfony-2/
categories:
  - Back-end
  - O Básico
  - PHP
  - Técnicas e Práticas
tags:
  - desenvolvimento
  - framework
  - php
  - phpOO
  - Symfony
  - tutorial

---
O symfony é um framework fullstack de aplicações web para as necessidades de alto desempenho, é um conjunto de componentes PHP, para grandes e avançados projetos, porém podemos instalar seus componentes separadamente em casos de projetos menores. É muito respeitado pela comunidade, não é apenas um Framework popular, mas também é uma das melhores plataformas para construir projetos Open-Source. Muitos projetos PHP estão incorporando alguns dos componentes ou estão usando o framework full-stack, projetos como <a title="DrupAl" href="http://symfony.com/projects/drupal" target="_blank">Drupal</a>, <a title="Laravel" href="http://symfony.com/projects/laravel" target="_blank">Laravel</a>, entre outros, <a title="Projetos com Symfony" href="http://symfony.com/projects" target="_blank">veja a lista</a>.

## Iniciando

Vou abordar nesse simples tutorial a instalação do Symfony, para que, em tutoriais futuros possamos dar continuidade a dicas mais avançadas.

Primeiramente vamos criar uma pasta, para que nosso projeto se mantenha organizado, digitando o comando no terminal:

<pre class="lang-bash">$ mkdir tableless</pre>

Após a criação da pasta, vamos entrar na mesma, com o comando:

<pre class="lang-bash">$ cd tableless</pre>

## Instalação

Vamos instalar o Symfony via composer, caso não o conheça, ou tenha dúvidas, leia este post (<a title="Composer para iniciantes" href="//tableless.com.br/composer-para-iniciantes/" target="_blank">Composer para iniciantes</a>). Para fazermos o Download do Symfony entramos no <a title="Symfony Download" href="http://symfony.com/download" target="_blank">site</a> e copiamos o comando, como na imagem abaixo:
  
[<img class="alignnone size-full wp-image-46532" src="http://tableless.com.br/uploads/2015/01/01.png" alt="Download do Symfony" width="750" height="403" srcset="uploads/2015/01/01.png 750w, uploads/2015/01/01-259x139.png 259w, uploads/2015/01/01-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][1]

Vamos trocar o final do código, onde está path/ vamos colocar symfony/ que será a pasta onde instalaremos o Symfony, o comando ficará assim:

<pre class="lang-bash">$ composer create-project symfony/framework-standard-edition symfony/</pre>

Ao darmos enter, a instalação irá começar como na imagem abaixo, isso poderá demorar alguns minutos, já que o composer irá baixar a distribuição padrão do Symfony, juntamente com todas as suas bibliotecas.

[<img class="alignnone size-full wp-image-46533" src="http://tableless.com.br/uploads/2015/01/02.png" alt="Instalação do symfony" width="750" height="403" srcset="uploads/2015/01/02.png 750w, uploads/2015/01/02-259x139.png 259w, uploads/2015/01/02-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][2]

Ao baixar todos os componentes, a instalação do symfony vai nos fazer diversas perguntas.

1º &#8211; Gostaria de instalar Acme demo bundle? [y/N] digitamos &#8220;N&#8221; e damos enter.
  
O Acme demo bundle é apenas uma demonstração de alguns recursos que podemos trabalhar, e nesse caso não vamos instalar!

<pre class="lang-bash">$ Would you like to install Acme demo bundle? [y/N]:N</pre>

2º &#8211; O symfony nos pergunta qual o drive de banco de dados que vamos utilizar.
  
Em nosso caso vamos usar o PDO, que hoje é <a title="PHP PDO" href="http://php.net/manual/pt_BR/book.pdo.php" target="_blank">basicamente um padrão do PHP</a>, e o próprio symfony nos recomenda, damos apenas um enter para continuar.

<pre class="lang-bash">$ database_driver (pdo_mysql):</pre>

3º &#8211; Nos pergunta qual o host do banco de dados, como estamos em localhost apenas damos um enter.

<pre class="lang-bash">$ database_host (127.0.0.1):</pre>

4º &#8211; Qual a porta que vamos usar, por defult vamos deixar como está, e damos um Enter

<pre class="lang-bash">$ database_port (null)</pre>

5º &#8211; Qual o nome do banco de dados vamos usar, nesse caso, vamos deixar como está, mas você pode utilizar o nome que quiser, e damos enter.

<pre class="lang-bash">$ database_name (symfony):</pre>

6º &#8211; Qual o nome do nosso usuário do banco, no meu caso vou deixar como está, meu usuário é root, damos um enter.

<pre class="lang-bash">$ database_user (root):</pre>

7º &#8211; Qual é nossa senha, no meu caso é root, deixo assim em ambiente de desenvolvimento, digito root e dou enter.

<pre class="lang-bash">$ database_password (null): root</pre>

8º &#8211; Nos pergunta sobre nossos dados de e-mail, vamos apenas dar um enter, pois não vamos usar agora.

<pre class="lang-bash">$ mailer_transport (smtp):</pre>

9º &#8211; Qual o host de e-mail, apenas damos um enter.

<pre class="lang-bash">$ mailer_host (127.0.0.1):</pre>

10º &#8211; Nos pergunta sobre o usuário de e-mail, damos enter.

<pre class="lang-bash">$ mailer_user (null):</pre>

11º &#8211; Nos pergunta sobre a senha, enter.

<pre class="lang-bash">$ mailer_password (null):</pre>

12º &#8211; Sobre localidade, e digitamos pt_BR, e enter

<pre class="lang-bash">$ locale (en): pt_BR</pre>

13º &#8211; Nos pergunta sobre a chave secreta de nossa aplicação, vamos deixar como está, apenas damos um enter.

<pre class="lang-bash">$ secret (ThisTokenIsNotSoSecretChangeIt):</pre>

Segue a imagem para comparação, se tudo ocorreu bem, ficará assim:

[<img class="alignnone size-full wp-image-46534" src="http://tableless.com.br/uploads/2015/01/03.png" alt="Instalando Symfony" width="750" height="403" srcset="uploads/2015/01/03.png 750w, uploads/2015/01/03-259x139.png 259w, uploads/2015/01/03-400x215.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][3]

## Rodando a aplicação

Pronto, o Symfony está instalado!
  
Para vê-lo rodando vamos iniciar nosso servidor.
  
A partir do PHP 5.4, o próprio vem com um servidor web embutido (<a title="Manual Servidor PHP" href="http://php.net/manual/pt_BR/features.commandline.webserver.php" target="_blank">PHP&#8217;s built-in Web Server</a>). Ele pode ser usado para executar suas aplicações PHP localmente durante o desenvolvimento, para testar ou para demonstrações de aplicativos. Desta forma, você não tem que se preocupar em configurar um servidor full-featured web como o Apache ou Nginx.

Para iniciarmos o servidor do php digitamos no terminal:

<pre class="lang-bash">$ php -S 127.0.0.1:8080</pre>

ou

<pre class="lang-bash">$ php -S 127.0.0.1:8080 -t public_html/</pre>

para indicar que seu index.php está na pasta public_html.

Mas em nosso caso, não vamos utilizar os comandos citados acima, como estamos usando o Symfony, entramos em nossa pasta, que está instalado o projeto:

<pre class="lang-bash">$ cd symfony</pre>

e digitamos:

<pre class="lang-bash">$ php app/console server:run</pre>

e teremos a resposta:

<pre class="lang-bash">$ Server running on http://127.0.0.1:800</pre>

Abrimos nosso navegador e digitamos a url: http://127.0.0.1:8000/
  
E Pronto!

[<img class="alignnone size-full wp-image-46535" src="http://tableless.com.br/uploads/2015/01/04.png" alt="Página do Symfony" width="736" height="403" srcset="uploads/2015/01/04.png 736w, uploads/2015/01/04-254x139.png 254w, uploads/2015/01/04-400x219.png 400w" sizes="(max-width: 736px) 100vw, 736px" />][4]

Irá aparecer um erro na tela, por não termos configurado as nossas rotas no Controller, porém sabemos que nossa aplicação está rodando. O Symfony gera uma rota de teste automaticamente, e para vermos se está tudo certo sem erros, então digitamos em nosso navegador a url:
  
http://127.0.0.1:8000/app/example
  
Aparecerá uma página em branco escrita Homepage, junto com a barra de debug do Symfony (a debug toolbar) utilizada em desenvolvimento, que estará no rodapé!

O Symfony está rodando com sucesso!

## Olhando rapidamente para a debug toolbar

A debug toolbar é uma barra de ferramentas do Symfony, fantástica, que nos traz informações valiosas.

[<img class="alignnone size-full wp-image-46590" src="http://tableless.com.br/uploads/2015/01/061.png" alt="Debug toolbar Symfony2" width="750" height="83" srcset="uploads/2015/01/061.png 750w, uploads/2015/01/061-265x29.png 265w, uploads/2015/01/061-400x44.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][5]

1 &#8211; No início temos o ícone do Symfony, que ao colocarmos o ponteiro do mouse em cima, a barra nos mostra a versão do Symfony juntamente com um link para a documentação.

2 &#8211; Informações sobre o PHP, como versão e extensões usadas, e ao clicarmos, nos retorna uma página com um phpinfo(), onde estão todas as configurações do PHP de nossa máquina.

3 &#8211; Informações a respeito da requisição principal de nossa aplicação, indicando, que estamos em ambiente de desenvolvimento e o token de requisição.

4 &#8211; Informações sobre o status code, o Controller e Action de nossa página, o nome da rota que estamos acessando e se temos ou não uma sessão.

5 &#8211; Requisições de AJAX.

6 &#8211; Tempo em que nossa página demorou pra carregar.

7 &#8211; Quantidade de memória que a aplicação utilizou.

8 &#8211; Informações, quantidade de formulários.

9 &#8211; Informação sobre autenticação, usuários anônimos, admins, etc&#8230;

10 &#8211; Informações sobre consultas no banco de dados, tempos de queries, &#8230;

## Configurações básicas

Vamos deixar nosso projeto um pouco mais limpo, excluindo os arquivos de UPGRADEs.md, que não tem relevância em nossa aplicação nesse momento.
  
Podemos excluir os arquios:

UPGRADE.md
  
UPGRADE-2.2.md
  
UPGRADE-2.3.md
  
UPGRADE-2.4.md

Também vamos modificar o conteúdo do nosso arquivo README.md, lembrando que a linguagem usada nesse arquivo é Markdown, para ser lida pelo GitHub, <a title="Noções básicas de Markdown" href="https://help.github.com/articles/markdown-basics/" target="_blank">nesse link</a> você encontra algumas noções básicas.
  
Apague todo o conteúdo do arquivo, que pode ser feito por um simples editor de texto, como bloco de notas, pela IDE de sua preferência, ou até mesmo pelo vim no terminal!

E adicionamos o conteúdo abaixo:

<pre class="lang-markdown">Iniciando com Symfony 2
=======================

http://tableless.com.br/
-----------------------

**Tutorial do Portal Tableless**

&gt;1º -  *Iniciando com Symfony 2*
</pre>

Podemos modificar o conteúdo do arquivo composer.json somente as linhas 2 e 5.
  
De:

<pre class="lang-json">"name": "symfony/framework-standard-edition",
"description": "The \"Symfony Standard Edition\" distribution",
</pre>

Para:

<pre class="lang-json">"name": "tableless/iniciando-com-Symfony",
"description": "Tableless: Iniciando com Framework Symfony 2",
</pre>

## Controlando nossa aplicação

Após essas simples configurações iniciais, podemos iniciar o Git em nosso projeto, para termos maior controle sobre nossa aplicação, não abordaremos conceitos sobre Git, mas em caso de <a title="Comandos iniciais Git" href="http://tableless.com.br/alguns-comandos-git/" target="_blank">dúvidas, Consulte</a>!

O projeto se encontra no <a title="GitHub Candido Souza" href="https://github.com/candidosouza/tableless" target="_blank">meu GitHub</a>, assim ficará mais fácil para você analisar, estudar e comparar os códigos como o seu projeto! Lembrando que até o momento só instalamos o Symfony2, mas nos próximos tutoriais daremos continuidade ao nossos exemplos!

## Concluindo

Para finalizarmos, recomendo a <a title="Documentação do Symfony" href="http://symfony.com/doc/current/index.html" target="_blank">documentação do Symfony</a>, ótima para estudos!

 [1]: http://tableless.com.br/uploads/2015/01/01.png
 [2]: http://tableless.com.br/uploads/2015/01/02.png
 [3]: http://tableless.com.br/uploads/2015/01/03.png
 [4]: http://tableless.com.br/uploads/2015/01/04.png
 [5]: http://tableless.com.br/uploads/2015/01/061.png