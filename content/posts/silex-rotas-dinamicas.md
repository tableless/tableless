---
title: Rotas dinâmicas no Silex
author: Nando Kstro Net
type: post
date: 2015-07-13
excerpt: |
  |
    Como trabalhar com rotas dinâmicas e métodos auxiliares no Silex PHP.
url: /silex-rotas-dinamicas/
categories:
  - Back-end
  - Código
  - O Básico
  - PHP
tags:
  - framework
  - php
  - Silex

---
Continuando nossa jornada sobre o **Silex Framework**, neste post falarei sobre rotas dinâmicas. Se você não está familiarizado com o Silex, confira nosso primeiro post _<a href="http://tableless.com.br/conhecendo-e-instalando-o-silex/" target="_blank">Conhecendo e instalando o Silex</a>_.

Rotas dinâmicas são a possibilidade de passar parâmetros nas rotas da sua aplicação. O Silex possui diversos métodos para facilitar o uso dessa dinâmica em suas rotas.

## Utilização

Para tornar sua rota dinâmica, veja o código abaixo:

<pre>&lt;?php
use Silex\Application;
require 'vendor/autoload.php';
$app = new Application();
$app-&gt;get('users/{name}', function($name){
    return 'Olá, ' . $name;
});
$app-&gt;run();
</pre>

O que nos interessa nesse momento, são as linhas de 5 e 6. Na linha 5 definimos nossa rota _users_, que receberá requisições do tipo `GET`. Perceba que entre chaves `{}`, incluímos um elemento chamado `name`, ou seja, esse é o parâmetro da nossa rota _users_. Agora tudo que passarmos na URL após chamada a rota, poderemos manipular em nosso _callback_, mas para isso devemos passar o mesmo parâmetro da rota como parâmetro do nosso _callback_, como mostrado na mesma linha 5. Na linha 6 apenas retornamos como saída o valor passado na rota. Por exemplo, se acessarmos no navegador o seguinte link `http://url_de_minha_app.com.br/users/Nando`, teríamos como saída:

`Olá, Nando`

Se você deseja passar mais parâmetros, apenas separe os mesmos com `/`, como mostrado abaixo:

<pre>&lt;?php
...
$app-&gt;get('users/{name}/{email}', function($name, $email){
    //Sua_logica_aqui
});
...
</pre>

## Valores Default

Se você deseja definir um valor _default_ para seus parâmetros de rota, é muito simples. O Silex possui um método para isso. Através do método `value()` você definirá valores padrões para estes parâmetros, e quando acessar suas rotas sem informar nenhum valor esperado, entra em ação os valores definidos por padrão. Para usar o método `value()`:

<pre>&lt;?php
...
$app-&gt;get('users/{name}', function($name){
    return 'Olá, ' . $name;
})
-&gt;value('name', NULL);
...
</pre>

Na linha 6 defino o método `value` que têm como primeiro parâmetro o nome definido para o parâmetro da rota, e o segundo parâmetro do método `value` recebe o valor _default_ que você desejar. Sempre que acessarmos a rota _users_ sem definir nenhum valor após a mesma, nosso parâmetro `name` receberá o valor NULL. A partir daí você fica livre para tratar como quiser a lógica da sua aplicação.

## O método convert()

Se você deseja garantir o tipo do valor passado ou apenas deseja conversões simples com estes valores, o método `convert` foi feito para tal operação. Para utilizá-lo:

<pre>...
$app-&gt;get('users/{name}', function($name){
    return 'Olá, ' . $name;
})
-&gt;value('name', NULL)
-&gt;convert('name', function($name){ return (string) $name; });
...
</pre>

O método recebe 2 parâmetros: o primeiro é o nome do parâmetro informado na rota e o segundo um _callback_, onde realizamos nossas conversões. Neste exemplo, garanto apenas que os valores passados na rota `users` serão de fato do tipo `string`, como mostrado na linha 6 do código acima.

## Conclusão

Vimos como é simples trabalhar com rotas dinâmicas em nossas aplicações Silex, e com os métodos auxiliares nossa aplicação de rotas fica ainda mais robusta.

Na sessão <a href="http://silex.sensiolabs.org/doc/usage.html" target="_blank">&#8216;Usage&#8217;</a> da documentação do Silex, você encontrará mais opções além das mostradas aqui.