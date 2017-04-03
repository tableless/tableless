---
title: Criando alias para executar testes com PHPUnit
author: alanricardox
type: post
date: 2015-09-30
excerpt: Uma maneira prática e fácil de testar múltiplos projetos que fazem uso do PHPUnit com um único alias "phpunit" para qualquer projeto ou um alias dedicado a realizar testes para projetos pré-definidos.
url: /criando-alias-para-executar-testes-com-phpunit/
categories:
  - Geral

---
O PHPUnit com certeza é uma das melhores ferramentas de teste automatizado em PHP, e normalmente lidar com vários projetos é realmente chato alternar entre eles e toda vez ter que digitar o comando **/vendor/bin/phpunit**. Não seria muito mais LEGAL ter um alias global que identifique em qual projeto você está no terminal e que disponibilize o comando **phpunit** ou melhor ainda, ter um alias de teste para cada projeto, como por exemplo: **phpunit\_project\_1** ou **phpunit\_project\_2**.

Neste artigo irei demonstrar uma maneira prática e fácil de testar múltiplos projetos que fazem uso do PHPUnit com um único alias &#8220;phpunit&#8221; para qualquer projeto ou um alias dedicado a realizar testes para projetos pré-definidos. _(Os comandos de exemplos foram testados no terminal do Mac)._

Vamos supor que temos 2 projetos em nosso diretório **&#8220;/www&#8221;**, com uma estrutura similar do exemplo abaixo:

<pre class="lang-html">| www
-------| project_1
-------------------| app<em> (código de produção)</em>
-------------------| vendor<em> (phpunit e outros pacotes)</em>
-------------------| tests <em> (testes automatizados)</em>
-------| project_2
-------------------| app<em> (código de produção)</em>
-------------------| vendor<em> (phpunit e outros pacotes)</em>
-------------------| tests <em> (testes automatizados)</em>
</pre>

Para executar os testes no **project_1**, temos que: 

  1. Acessar a pasta do projeto pelo terminal: <pre class="lang-html">cd /www/project_1</pre>

  2. Executar os testes: <pre class="lang-html">/vendor/bin/phpunit</pre>

Para qualquer projeto temos que realizar o mesmo processo, acessar a pasta e executar os testes com o comando **/vendor/bin/phpunit**.

FELIZMENTE, temos outras maneiras de fazer isso de forma mais confortável e ágil, com o **.bash_profile** temos esse poder!!!!

Por exemplo, para utilizar o comando **phpunit** e executar o comando **/vendor/bin/phpunit** automaticamente na pasta de qualquer projeto, podemos fazer o seguinte:

  1. No Terminal digite: <pre class="lang-html">cd</pre>

  2. Pressione ENTER e em seguida digite o comando abaixo e pressione ENTER novamente: <pre class="lang-html">sudo nano .bash_profile</pre>

  3. Dentro do arquivo digitamos o seguinte: <pre class="lang-html">alias phpunit='$(pwd)/vendor/bin/phpunit'</pre>

  4. Para salvar o arquivo pressione: <pre class="lang-html"><strong>COMMAND + X</strong> e em seguida digite <strong>Y</strong> e pressione <strong>ENTER</strong>.</pre>

  5. Para carregar as novas configurações digite: <pre class="lang-html">source ~/.bash_profile</pre>

O comando basicamente irá criar um novo alias chamado **phpunit** e será atribuído a ele o caminho atual **(pwd)** que você estiver no terminal _(por exemplo /www/project_1)_, mais o caminho até o **phpunit** do seu projeto **/vendor/bin/phpunit**.

Agora para utilizarmos nosso novo alias, basta entrarmos na pasta do projeto, como por exemplo: **&#8220;cd /www/project_1&#8221;** e digitarmos **&#8220;phpunit&#8221;** e pressionar **ENTER**.

Podemos realizar este processo para qualquer projeto, por exemplo: **cd /www/project_2** e em seguida **phpunit** os testes do projeto 2 serão executados.

PERFEITO, certo?!!!
  
NÃO, ainda podemos melhorar nosso bash para que ele tenha um alias dedicado para cada projeto, vamos alterar algumas coisas:

  1. No Terminal digite: <pre class="lang-html">cd</pre>

  2. Pressione ENTER e em seguida digite o comando abaixo e pressione ENTER novamente: <pre class="lang-html">sudo nano .bash_profile</pre>

  3. Dentro do arquivo removemos o código anterior: <pre class="lang-html">alias phpunit='$(pwd)/vendor/bin/phpunit'</pre>

  4. E inserimos essas duas linhas _(aqui você poderá inserir todos os seus projetos conforme desejar)_:</p> <pre class="lang-html">alias phpunit_project_1='cd /caminho_pasta_www/project_1/; $(pwd)/vendor/bin/phpunit'</pre>
    
    <pre class="lang-html">alias phpunit_project_2='cd /caminho_pasta_www/project_2/; $(pwd)/vendor/bin/phpunit'</pre>

  5. Para salvar o arquivo pressione: <pre class="lang-html"><strong>COMMAND + X</strong> e em seguida digite <strong>Y</strong> e pressione <strong>ENTER</strong>.</pre>

  6. Para carregar as novas configurações digite: <pre class="lang-html">source ~/.bash_profile</pre>

PRONTO!!
  
Agora podemos executar os nossos testes de qualquer lugar, sem a necessidade de acessar a pasta do projeto para executá-los.

Valeu pessoal, espero que tenha ajudado!