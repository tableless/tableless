---
title: Conhecendo e instalando o Silex
author: Nando Kstro Net
type: post
date: 2015-06-30
excerpt: O Silex é um micro framework baseado nos componentes do Symfony, criado por Fabien Potencier e concebido para a criação de aplicações pequenas com foco na agilidade, extensibilidade e para ser facilmente testável.
url: /conhecendo-e-instalando-o-silex/
categories:
  - Back-end
  - Código
  - PHP
tags:
  - composer
  - framework
  - php
  - Silex
  - Symfony

---
O <a href="http://silex.sensiolabs.org/" target="_blank">Silex</a> é um micro framework baseado nos componentes do <a href="http://symfony.com/" target="_blank">Symfony</a>. Foi desenvolvido por <a href="http://fabien.potencier.org/" target="_blank">Fabien Potencier</a>, o mesmo criador do Symfony.

O Silex foi concebido para a criação de aplicações pequenas com foco na agilidade, extensibilidade e para ser facilmente testável. Ele provê um sistema de rotas muito poderoso, e se propõe a resolvê-las através dos Services e Providers, conceitos que veremos mais à frente. Você perceberá que ele é facilmente estendido e suas funcionalidades recebem uma vantagem através dessas integrações.

## Instalação

Para instalar o Silex em nossos projetos é muito simples: precisamos apenas do <a href="https://getcomposer.org" target="_blank">Composer</a> para gerenciar nossas dependências.

Mas afinal, o que é o Composer? O Composer é um gerenciador de dependências para aplicações PHP, baseado nas GEMs do Ruby e no NPM do Node.JS. Com o Composer você pode facilmente gerenciar a instalação de pacotes de terceiros, bem como preparar o seu pacote para que ele fique disponível para os desenvolvedores que utilizam essa ferramenta. Tudo que precisaremos é de um arquivo composer.json na raiz de nosso projeto. Utilizaremos `api-events` como nome da nossa pasta.

Na raiz dessa pasta crie um arquivo composer.json com o seguinte conteúdo:

<pre class="lang-json">{
    "require" : {
	"silex/silex" : "^1.2"
    }
}
</pre>

O composer.json é o arquivo que o Composer lê para poder realizar as tarefas de download e instalação dos pacotes especificados.

Agora vamos instalar o Composer em nosso projeto. O Composer pode ser utilizado de duas maneiras: de forma local e de forma global. Abordarei aqui a forma local. Para instalá-lo em sistemas Unix, você precisará da _lib curl_ disponível. Se você utiliza o Windows, baixe o executável <a href="https://getcomposer.org/Composer-Setup.exe" target="_blank">aqui</a>. O seguinte comando, executado via terminal (e na raiz de nosso projeto), deve instalar o Composer para você:

[<img class="alignnone wp-image-49783 size-full" src="http://tableless.com.br/uploads/2015/06/curl-composer.png" alt="Curl Composer" width="902" height="72" />][1]

O comando fará o download e irá compilar o composer.phar e arquivos [`.phar`][2], que são extensões executáveis do PHP. Agora que temos o arquivo de configuração e o Composer em nosso projeto, podemos instalar nossas dependências, ou seja, o Silex propriamente dito. É muito simples realizar a instalação dos pacotes: na raiz do seu projeto, execute o seguinte comando:

`php composer.phar install`

É preciso que você tenha o <a href="http://www.php-cli.com/" target="_blank">php-cli</a> disponível em seu terminal. O comando acima verificará o arquivo `composer.json` e logo em seguida fará o download do Silex, conforme requerido no arquivo `.json` da versão 1.2. Após tudo concluído, você verá uma imagem semelhante a essa:

[<img class="alignnone wp-image-49784 size-full" src="http://tableless.com.br/uploads/2015/06/packages-installed.png" alt="Silex - Packages instalados" width="742" height="769" />][3]

O Composer instalou o Silex bem como as dependências utilizadas pelo mesmo dentro da pasta `vendor` do nosso projeto. Além do download, ele também mapeia os _namespaces_ dos pacotes e cria um _autoload._ Através deste _autoload_ teremos acesso a todos os pacotes baixados até o momento.

## Silex: Hello World!

Agora que nossas dependências foram baixadas e instaladas, podemos começar a utilizar nosso micro framework: crie um arquivo `index.php` na raiz da sua pasta e adicione a abertura do código PHP utilizando o seguinte comando:

`echo "<?php " > index.php`

Abaixo segue o código do index na íntegra:

<pre class="lang-php">&lt;?php
use Silex\Application;
require 'vendor/autoload.php';
$app = new Application();
$app-&gt;get('/', function(){
	return 'Hello World';
});
$app-&gt;run();
</pre>

Na linha 2 informo ao meu script para utilizar o Silex com o namespace `Silex\Application`. Para ter acesso aos namespaces dos pacotes baixados (como comentado anteriormente sobre o autoload) precisamos adicionar o mesmo em nosso index. Para isso utilizamos o `require` na linha 3. Na linha 4 simplesmente instanciamos nosso micro framework. O já citado poderoso sistema de rotas pode ser visto das linhas 5 a 6, onde utilizamos o método `get`. O método `get` manipula as requisições GET vindas do _client_ e no nosso caso fazemos o seguinte:

Quando o cliente realizar uma requisição do tipo GET em nossa rota raiz, referenciada através da `/`, nós executaremos o que for passado dentro do _callback_, o segundo parâmetro do método `get` do `Silex\Application`. Como queremos apenas realizar (imprimir) um &#8220;Hello World&#8221;, vamos retornar essa _string_ em nosso _callback_ para a rota raiz.

E por fim, para que as respostas emitidas pelo Silex sejam enviadas ao browser ou a quem as solicitou, utilizamos o método `run` em nossa linha 8. Ao rodar nosso app no browser, temos a seguinte resposta:

`Hello World`

Podemos ver o quão simples é utilizar esse micro framework através dos processos vistos até aqui. Para os próximos artigos, vamos nos aprofundar mais neste micro framework e ver como utilizá-lo melhor em casos reais.

Por hora, pratique os conhecimentos aqui passados. Nos vemos em breve!

 [1]: http://tableless.com.br/uploads/2015/06/curl-composer.png
 [2]: http://php.net/phar
 [3]: http://tableless.com.br/uploads/2015/06/packages-installed.png