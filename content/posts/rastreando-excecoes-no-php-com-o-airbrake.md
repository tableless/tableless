---
title: Rastreando exceções no PHP com o Airbrake
author: Gustavo Straube
type: post
date: 2014-09-15
excerpt: Aprenda a rastrear erros em aplicações PHP e, assim, simplificar a manutenção do seu código.
url: /rastreando-excecoes-no-php-com-o-airbrake/
categories:
  - PHP
tags:
  - aprenda
  - desenvolvimento
  - Na Prática
  - tutorial

---
Identificar erros, e suas causas, em uma aplicação web pode se tornar uma tarefa complicada. Ter algumas ferramentas à mão pode simplificar bastante essa missão.

Algo que provavelmente ajuda a rastrear uma falha são os logs da aplicação ou do servidor onde ela está sendo executada, mas não é fácil encontrar algo específico, especialmente se o volume de registros é grande.

Outra situação desagradável é quando os erros acontecem em situações específicas, difíceis de reproduzir.

Ainda pode haver um cenário em que as exceções acontecem com os usuários, mas nunca são reportadas aos desenvolvedores. E como verificar logs proativamente é algo muito improvável, esses erros ficam no esquecimento.

Pensando nesses obstáculos, o <a title="Airbrake" href="https://airbrake.io/" target="_blank">Airbrake</a> pode facilitar muito a vida de quem desenvolve e mantém software para web. Conheci ele usando o <a title="Codebase" href="https://www.codebasehq.com/" target="_blank">Codebase</a> (também uma excelente ferramenta, porém para gerenciamento de projetos), que tem integração na parte de tickets/rastreamento de bugs.

## 1. Qual é a mágica?

O princípio do funcionamento do Airbrake é bem simples: toda vez que uma exceção ou erro são gerados, as informações sobre a requisição, sessão do usuário e ambiente são enviadas para o servidor através da API. A partir dessas informações, são gerados relatórios e é possível realizar buscas no histórico. Uma grande vantagem é que os erros são agrupados, então se um mesmo acontece com frequência não “sujará” o log.

A cada novo erro na sua aplicação, uma notificação é enviada por e-mail.

## 2. Configurando o serviço

Para iniciar, você deve ter uma conta no <a title="Airbrake" href="https://airbrake.io/" target="_blank">Airbrake</a>. Não há plano gratuito, mas existe um período de testes de 30 dias.

Ainda existe a opção de usar uma alternativa open source compatível com a mesma API, que é o <a title="Errbit" href="https://github.com/errbit/errbit" target="_blank">Errbit</a>, mas nesse caso você precisa instalar o serviço em um servidor próprio. Caso opte pelo Errbit, as instruções de instalação estão disponíveis no repositório do GitHub: <a title="Repositório do Errbit no GitHub" href="https://github.com/errbit/errbit" target="_blank">https://github.com/errbit/errbit</a>.

## 3. Instalação

Como minha linguagem do dia-a-dia é PHP, vou seguir com as instruções focando nela, mas a lógica de instalação não muda muito de uma linguagem para outra. Caso precise, no site do Airbrake existem <a title="Integração do Airbrake com linguagens" href="https://airbrake.io/languages" target="_blank">instruções para outras linguagens</a>.

Se você já estiver usando o <a href="https://getcomposer.org/" target="_blank">Composer</a>, basta adicionar a dependência no arquivo **composer.json** do seu projeto:

<pre>{ 
    "require": {
        "dbtlr/php-airbrake": "dev-master"
    }
}</pre>

Se não usa o Composer, essa é uma ótima oportunidade para começar. O Andre Cardoso escreveu sobre ele aqui no Tableless: <a title="Composer para iniciantes" href="http://tableless.com.br/composer-para-iniciantes/" target="_blank">Composer para iniciantes</a>.

Caso não esteja usando um framework, provavelmente precisará adicionar a chamada ao class loader do Composer:

<pre>require_once 'vendor/autoload.php';</pre>

## 4. Integração

Agora você precisa fazer com que as exceções e erros do PHP sejam enviadas para a o Airbrake, para isso você tem pelo menos dois caminhos possíveis de acordo com a estrutura do seu projeto:

### Sem framework ou com um framework que não tem manipulação de exceções

Nesse caso, basta usar a manipulação de exceções da própria API, assim:

<pre>Airbrake\EventHandler::start('API_KEY’);</pre>

Lembrando de substituir o **API_KEY** pela sua própria chave da API do Airbrake.

Adicionando essa chamada logo no início do seu script ou em um dos pontos de entrada da sua aplicação as funções set\_exception\_handler e set\_error\_handler, do PHP, são chamadas.

### Com framework que tem manipulação de exceções

Para registrar a API, basta usar o seguinte trecho de código junto ao manipulador de exceções do seu framework:

<pre>$config = new Airbrake\Configuration('API_KEY');
$client = new Airbrake\Client($config);
$client-&gt;notifyOnException($exception);</pre>

Para facilitar, para alguns, vou dar o exemplo em dois frameworks que tenho usado:

#### Com Laravel

Edite o arquivo **app/start/global.php**, da seguinte maneira:

<pre>App::error(function (Exception $exception, $code)
{
    Log::error($exception);

    // Airbrake
    $config = new Airbrake\Configuration('API_KEY');
    $client = new Airbrake\Client($config);
    $client-&gt;notifyOnException($exception);

});</pre>

#### Com Slim Framework

Edite o arquivo **public/index.php**, e adicione o seguinte trecho depois de ter instanciado a aplicação:

<pre>$app-&gt;error(function (\Exception $e) use ($app) {
    $app-&gt;getLog()-&gt;error($e);

    // Airbrake
    $config = new Airbrake\Configuration('API_KEY');
    $client = new Airbrake\Client($config);
    $client-&gt;notifyOnException($e);

});</pre>

## 5. Um pequeno exemplo funcional

Caso você queira fazer um teste rápido, pode usar o seguinte script e executá-lo (depois de ter instalado a dependência com Composer).

<pre>&lt;?php
require_once 'vendor/autoload.php';
Airbrake\EventHandler::start('API_KEY');

throw new Exception('Testando o Airbrake');</pre>

A cada execução desse script, um novo registro de exceção deve ser gravado na sua conta no Airbrake.

## Conclusão

O Airbrake não é a única opção disponível para gerenciar e rastrear as exceções da sua aplicação (apenas para citar mais uma opção, tenho usado o <a title="Sentry" href="https://www.getsentry.com/" target="_blank">Sentry</a> com sucesso em pelo menos um projeto), mas pode ser um ponto de partida interessante para que você tenha uma visão diferente, e mais prática, sobre os erros do seu código.

Caso você opte por usar o Errbit, talvez precise de algumas configurações mais avançadas (como determinar o host ou resource do serviço, por exemplo), então a documentação oficial da bilbioteca para PHP pode te ajudar: <a title="Opções de configurações do PHP Airbrake" href="https://github.com/dbtlr/php-airbrake#configuration-options" target="_blank">https://github.com/dbtlr/php-airbrake#configuration-options</a>