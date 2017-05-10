---
title: PHP Slim Framework
author: George Moura
type: post
date: 2014-06-04
excerpt: Iniciando com o SLIM Framework.
url: /php-slim-framework/
dsq_thread_id: 2735945634
categories:
  - Back-end
  - Código
  - PHP
tags:
  - back-end
  - backend
  - framework
  - php
  - slim

---
O Slim Framework é um microframework PHP que facilita sua vida na hora de fazer pequenas APIs.

Vou falar sobre um problema que tive em um projeto em uma empresa que trabalho. Lá eu codifico com diferentes linguagens de programação em pequenos sistemas. Esses sistemas precisam ser acessados por 3 filiais e os usuários se logam com o mesmo login usado no E.R.P. que eles utilizam.

Para simplificar meu trabalho resolvi criar uma API simples para autenticar os usuários. Como eu queria usar uma estrutura REST e não queria fazer tudo na unha e nem queria colocar um framework grande como Rails, Laravel, Zend ou Django. Pesquisei sobre microframeworks PHP e cheguei ao [Sinatra][1], que já conhecia, e o [Flask][2] (Python). Então encontrei o [Slim][3] um microframework PHP.

Eu queria trabalhar com uma estrutura REST e o Slim já faz isso de forma muito simples criando rotas, como qualquer outro framework que trabalha com REST, a diferença é que um microframework é mais leve e não precisa de tantas configurações. É uma mão na roda para quem precisa escrever uma API. Para vocês terem ideia: em um dia consegui resolver meu problema de autenticação.

## Código

Agora vamos ao código! O Slim pode ser instalado via [Composer][4] ou fazendo o download do código fonte, para quem não conhece ele é um gerenciador de dependências para PHP assim como [Bundler][5] é para o Ruby, nesse post vou mostrar a instalação via composer:

### Passo 1 &#8211; Instalação do composer

Leia o post ([Composer para iniciantes][6]) do [Andre Cardoso][7]. Mas basicamente, para quem tem linux, é só abrir o terminal e digitar o código abaixo, se tiver windows, é só pegar o executável no site e instalar.

<pre class="lang-bash">curl -s https://getcomposer.org/installer | php</pre>

### Passo 2 &#8211; Criar o arquivo composer.json

Crie um diretorio para seu projeto(no meu caso eu chamei de api) e coloque um arquivo chamado composer.json dentro dela:

<pre class="lang-bash">mkdir api
cd api
</pre>

No arquivo composer.json adicione as seguintes linhas:

<pre class="lang-json">{
    "require": {
        "slim/slim": "2.*"
    }
}
</pre>

### Passo 3 &#8211; Instalar as dependências

<pre class="lang-bash">composer install</pre>

Caso você não tenha o Composer, as suas variáveis de ambiente deverão ser assim:

<pre>php composer.phar install</pre>

### Passo 4 &#8211; Criação da app

Crie um arquivo `index.php` e dentro dele coloque:

<pre class="lang-php">&lt;?php
require 'vendor/autoload.php';

//instancie o objeto
$app = new \Slim\Slim();

//defina a rota
get('/', function () { 
  echo "Hello, World!"; 
}); 
//rode a aplicação Slim 
$app-&gt;run();</pre>

Se você acessar `http://localhost/api/` você verá a mensagem **&#8220;Hello World!&#8221;**.

Mas não é isso que queremos, queremos uma API REST que retorne um JSON. Então vamos ver um exemplo bem simples. O Slim também trabalha com templates, então dentro do diretório da nossa aplicação vamos criar um diretório chamado de `templates` e dentro dele criaremos um arquivo chamado `default.php`, neste arquivo coloque o seguintes conteúdo:

<pre class="lang-php">&lt;?php 
header('Content-Type: application/json; charset=utf-8');
echo json_encode($data);
</pre>

Agora voltando ao nosso arquivo `index.php` edite-o deixando da seguinte forma:

<pre class="lang-php">&lt;?php
require 'vendor/autoload.php';

//instancie o objeto
$app = new \Slim\Slim(array(
'templates.path' =&gt; 'templates'
));

//defina a rota
$app-&gt;get('/', function () use ($app){ 
  //defina
  $data = array("data"=&gt;array("Hello"=&gt;"World!")); 
  //set o arquivo de template
  $app-&gt;render('default.php',$data,200); 
}); 

//rode a apliçicação Slim
$app-&gt;run();</pre>

Quando você acessar a url novamente você verá algo como:

<pre class="lang-json">{"Hello":"World!"}
</pre>

Agora vamos incrementar mais. No mesmo arquivo `index.php` antes de <code class="lang-php">$app-&gt;run();</code> adicione:

<pre>$app-&gt;group('/users',function() use ($app){

  //rota para a home
  $app-&gt;get('/',function() use ($app){
    //exemplo de lista de usuarios
    $users = array(
     'users'=&gt;array(
       'jo'=&gt;'senhadejo',
       'luca'=&gt;'senhaluca',
       'yasmin'=&gt;'senhayasmin',
       'eric'=&gt;'seric'
     )
    );
    $data = array(
      'data'=&gt;$users
      );
    $app-&gt;render('default.php',$data,200);
  });

  //rota para login
  $app-&gt;post('/login/',function() use ($app){
    if(isset($_POST))
    {
      $data = $_POST;
      $app-&gt;render('default.php',$data,200);
    }
    else
    {
      $app-&gt;render(404);
    }
  });

});
</pre>

Caso você esteja acessando o sistema por subdiretório crie um arquivo chamado `.htaccess` com o seguinte conteúdo:

<pre>RewriteEngine On
RewriteBase /api/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /api/index.php [L]
</pre>

Perceba que adicionei o método group no arquivo `index.php.` O Slim trabalha também com grupos de rotas, então é possível criar vários grupos com rotas próprias, dessa forma podemos organizar o código e não ter que ficar digitando o mesmo código várias vezes. Com o grupo de rotas chamado /users tudo que tiver dentro dele deverá vir precedido de /users ex: (/users/login/, /users/update/).

Acessando `http://localhost/api/users/` você verá uma lista de usuários, caso acesse `http://localhost/api/users/login/` você verá uma página de erro. Isso ocorre porque setamos apenas uma rota POST para /users/login/ e como você acessou via GET o sistema redirecionou pois não existe a rota GET para /users/login/.

Daqui para frente é só continuar implementando coisas novas, criando uma classe para conectar ao banco de dados, utilizando outros verbos HTTP, novos templates e etc. Você pode criar classes e usá-las normalmente é só incluí-las com o require e instanciar o objeto;

O post termina aqui. O link para documentação do Slim é esse <http://docs.slimframework.com/> divirtam-se e mãos a obra! ;D

 [1]: http://www.sinatrarb.com/
 [2]: http://flask.pocoo.org/
 [3]: http://www.slimframework.com/
 [4]: https://getcomposer.org/
 [5]: http://bundler.io/
 [6]: http://tableless.com.br/composer-para-iniciantes/
 [7]: http://tableless.com.br/author/andrecardosodev/