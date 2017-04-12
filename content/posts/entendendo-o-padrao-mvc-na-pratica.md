---
title: Entendendo o padrão MVC na prática
author: Erik Figueiredo
type: post
date: 2015-06-25
excerpt: Exemplo prático utilizando PHP e Composer para separar o código entre as diversas camadas do MVC
url: /entendendo-o-padrao-mvc-na-pratica/
categories:
  - Back-end
  - PHP
tags:
  - composer
  - mvc
  - php
  - php-fig

---
Práticas modernas do PHP exigem estudo e preparação, e o padrão de projeto que merece muita atenção é o MVC. Muita gente conhece este padrão através dos _frameworks_ (isso não é um problema, eu mesmo estou neste grupo), mas ir a fundo é essencial para evitar erros e falar coisas como:

> Seu MVC está errado, o _controller_ está maior que o _model_.

Este erro de definição acontece pois em nenhum lugar está escrito que a quantidade de linhas define o padrão MVC, mas vamos entender isto melhor?<!--more-->

## As camadas do MVC

### O que é _Model_?

_Model_ é onde fica a lógica da aplicação. Só isso.

Vai disparar um e-mail? Validar um formulário? Enviar ou receber dados do banco? Não importa. A _model_ deve saber como executar as tarefas mais diversa, mas não precisa saber quando deve ser feito, nem como mostrar estes dados.

### O que é _View_?

_View_ exibe os dados. Só isso.

_View_ não é só o HTML, mas qualquer tipo de retorno de dados, como _PDF_, _Json_, _XML_, o retorno dos dados do servidor _RESTFull_, os _tokens_ de autenticação _OAuth2_, entre outro. Qualquer retorno de dados para uma interface qualquer (o navegador, por exemplo) é responsabilidade da _view_. A _view_ deve saber renderizar os dados corretamente, mas não precisa saber como obtê-los ou quando renderizá-los.

### O que é _Controller_?

O _controller_ diz quando as coisas devem acontecer. Só isso.

É usado para intermediar a _model_ e a _view_ de uma camada. Por exemplo, para pegar dados da _model_ (guardados em um banco) e exibir na _view_ (em uma página HTML), ou pegar os dados de um formulário (_view_) e enviar para alguém (_model_). Também é responsabilidade do _controller_ cuidar das requisições (_request_ e _response_) e isso também inclui os famosos _middlewares_ (<a href="http://laravel.com/" target="_blank">Laravel</a>, <a href="http://www.slimframework.com/" target="_blank">Slim Framework</a>, <a href="http://expressjs.com/" target="_blank">Express</a>, <a href="http://www.rubyonrails.com.br/" target="_blank">Ruby on Rails</a>, etc.). O _controller_ não precisa saber como obter os dados nem como exibi-los, só quando fazer isso.

## Na prática

Uma sugestão aos desenvolvedores é criar seu próprio _framework_ de estudo (e publicar no <a href="https://github.com/" target="_blank">GitHub</a>) mas nunca os usar em produção. Esta prática te faz compreender o quanto você conhece da linguagem, e daqui a algum tempo, ver o quanto melhorou.

Neste estudo, vamos criar uma aplicação MVC simples com PHP, usando práticas modernas.

Para começar, vamos utilizar a ideia de que não devemos criar nada que já existe: este é o princípio da interoperabilidade buscada pelo <a href="http://www.php-fig.org/" target="_blank">PHP-FIG</a> (grupo formado pelas principais empresas e grupos PHP para definir boas práticas e padrões). Utilizaremos <a href="http://www.php-fig.org/psr/psr-4/" target="_blank">PSR-4</a> e <a href="https://getcomposer.org/" target="_blank">Composer</a> para gerenciar o carregamento das classes.

Para instalar o Composer, cito uma parte do artigo <a href="http://tableless.com.br/composer-para-iniciantes/" target="_blank">Composer para iniciantes</a> de <a href="http://www.andrebian.com/" target="_blank">Andre Cardoso</a> aqui no Tableless:

  * Primeiramente você precisa realizar o download do _phar_ do composer. O <a title="Descubra o que é um arquivo Phar" href="https://php.net/manual/pt_BR/book.phar.php" target="_blank">phar</a> é um empacotamento de uma aplicação e é utilizado para fornecer bibliotecas e ferramentas nas quais o desenvolvedor não tem de se preocupar com sua estrutura. Em outras palavras, é pegar e usar.
  * Para que você obtenha o composer há duas maneiras distintas. Através da biblioteca <a title="Descubra o que é cURL" href="http://en.wikipedia.org/wiki/CURL" target="_blank">cURL</a> e através do próprio PHP. Basta selecionar uma das opções abaixo e executar em seu terminal.
  * Instalando via cURL:
  
    `curl -sS https://getcomposer.org/installer | php`
  * Instalando via PHP:
  
    `php -r “readfile(‘https://getcomposer.org/installer’);” | php`

Para saber mais sobre <a href="http://www.php-fig.org/psr/psr-4/" target="_blank">PSR-4 veja o guia oficial aqui</a>.

Na raiz do diretório do seu projeto crie estes 5 arquivos (e diretórios):

  * src/App/Mvc/Controller.php
  * src/App/Mvc/Model.php
  * src/App/Mvc/View.php
  * composer.json
  * index.php

Ao baixar o composer.phar (explicado acima) você também o terá no diretório raiz, junto ao composer.json e ao index.php

O seu arquivo composer.json deverá ter o conteúdo a seguir:

<pre>{
   "autoload": {
      "psr-4": {
         "App\\": "src/App"
      }
   }
}</pre>

Rode o comando `php composer.phar install.`

A ideia é que o nosso _controller_ carregue as informações da _model _e as envie para a _view_. Pensando nisso, faremos com que o _controller_ carregue ambas as classes: _Model_ e _View_. A sequência para criá-las é:

Conteúdo do arquivo src/App/Mvc/Controller.php:

<pre>&lt;?php
   namespace App\Mvc;
   class Controller
   {
      ...
   }</pre>

Conteúdo do arquivo src/App/Mvc/Model.php:

<pre>&lt;?php
   namespace App\Mvc;
   class Model
   {
      ...
   }</pre>

Conteúdo do arquivo src/App/Mvc/View.php:

<pre>&lt;?php
   namespace App\Mvc;
   class View
   {
      ...
   }</pre>

Seguimos algumas regras da PSR-4: primeiro registramos um _namespace_ no composer.json que vai até o diretório src/App. Toda classe tem um _namespace_ e o App do começo indica o diretório que registramos (src/App). O Mvc é o diretório seguinte (ficando src/App/Mvc) e a classe tem o mesmo nome do arquivo (src/App/Mvc/Controller.php). Com isso podemos carregar as classes dinamicamente:

Conteúdo do arquivo index.php:

<pre>&lt;?php
   require 'vendor/autoload.php';
   $controller = new App\Mvc\Controller();</pre>

Nossa classe ainda não faz nada, então vamos testar com algo mais concreto: no Controller.php adicione um novo método chamado index() &#8211; os métodos públicos de um _Controller_ são chamados de _actions_.

<pre>&lt;?php
   namespace App\Mvc;
   class Controller
   {
      public function index()
      {
         echo 'Olá mundo!';
      }
   }</pre>

E no index.php adicione no final a linha:

<pre>$controller-&gt;index();</pre>

Ao rodar o index.php você verá um _&#8220;Olá mundo!&#8221;_ na tela. Agora vamos separar este código nas camadas do MVC.

No _model_, vamos criar o método que serve o texto em questão. Ele poderia carregar um componente que facilitaria as tarefas com o banco de dados, como o <a href="http://www.doctrine-project.org/" target="_blank">Doctrine</a>, por exemplo, mas aqui só retorna um texto.

<pre>&lt;?php
   namespace App\Mvc;
   class Model
   {
      public function getText($str = 'Olá mundo!')
      {
         return $str;
      }
   }</pre>

Na _view_ vamos imprimir este texto na tela. Poderíamos carregar um _template engine_ (<a href="http://laravel.com/docs/5.0/templates" target="_blank">Blade</a>, <a href="http://twig.sensiolabs.org/" target="_blank">Twig</a>, etc.), ou até criar o nosso próprio, mas ele só fará um _echo_ mesmo.

<pre>&lt;?php
   namespace App\Mvc;
   class View
   {
      public function render($str)
      {
         echo $str;
      }
   }</pre>

E o _controller_ intermediando tudo isso:

<pre>&lt;?php
   namespace App\Mvc;
   class Controller
   {
      public function index()
      {
         $model = new Model;
         $view = new View;
         $view-&gt;render($model-&gt;getText());
      }
   }</pre>

Rode o index.php novamente e você vai obter o mesmo resultado anterior, mas agora com uma estrutura MVC.

## Conclusão

Note que neste exemplo a maior classe é o _controller_ (com 14 linhas) e mesmo assim não estamos &#8220;quebrando o MVC&#8221;. Também não há nada de absurdo, como carregar a classe _Model_ no _Controller_ e passar todas as configurações gigantescas ali dentro. Mesmo que não seja uma quebra de MVC, o _Model_ ainda vai cuidar de tudo. O ideal é mover o máximo de lógica para dentro da _Model_.

Apenas para reforçar, o exemplo abaixo deveria estar dentro de um arquivo de _Model_, e nunca no _Controller_:

<pre>$users = User::whereRaw('age &gt; ? and votes = 100', [25])-&gt;get();</pre>

Este último exemplo foi retirado de <a href="http://laravel.com/docs/5.0/eloquent" target="_blank">http://laravel.com/docs/5.0/eloquent</a>

Quanto mais organizada e centralizada a lógica, melhor. Pense nisso e comece a pesquisar <a href="https://www.google.com.br/search?q=Dependency+Injection&oq=Dependency+Injection&aqs=chrome..69i57&sourceid=chrome&es_sm=122&ie=UTF-8" target="_blank">Dependency Injection</a>. Isso organiza seu código ainda mais.