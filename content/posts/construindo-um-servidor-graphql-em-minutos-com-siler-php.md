---
title: Construindo um servidor GraphQL em minutos com a Siler PHP
author: Leo Cavalcante
type: post
aliases:
    - /?p=57397
image: uploads/2017/03/postart.jpg
date: 2017-04-04
stick: yes
excerpt: GraphQL - uma query language como o SQL, mas desenhada para rodar no lado client
categories:
  - Código
---


Apresento-lhes:

<a href="http://graphql.org/">GraphQL</a>: uma query language como o SQL, mas desenhada para rodar no lado <em>client</em>, no caso: front-end.

<a href="https://github.com/leocavalcante/siler">Siler</a>: uma biblioteca PHP que tem como diferencial simplificar o desenvolvimento evitando <em>overheads</em>.
<h2>GraphQL</h2>
A GraphQL trás, na verdade, uma nova abordagem pro desenvolvimento, ela praticamente faz uma inversão de quem fará a consulta aos dados, ou pelo menos, trás essa possibilidade pro lado <em>client</em>, o lado front-end, que antes era refém do que o back-end devolvia no JSON e principalmente a forma como esses dados estavam relacionados nesse JSON.

<strong>Graças à GraphQL, nós podemos trazer esse poder de consulta e interface de dados pro <em>client</em>.</strong>

É uma tecnologia desenvolvida pelo Facebook, caprichada pra funcionar com React, mas vai muito bem com outras bibliotecas JavaScript e até <em>clients</em> que não sejam o navegador como Android (Java) e iOS (Swift/Obj-C).

https://www.youtube.com/watch?v=9sc8Pyc51uU

Na especificação da GraphQL tem um conceito de extrema relevância pra tecnologia que é o sistema de tipos (<em><a href="http://facebook.github.io/graphql/#sec-Type-System">Type System</a></em>). Isso faz com que seus dados sejam forte e estaticamente "tipados", algo bem diferente do que estamos acostumados com JSON e principalmente Percent-encoding (application/x-www-form-urlencoded) onde tudo é uma String. Mas isso é uma especificação e o lado que infere a implementação é o do servidor; <em>então o que o PHP tá fazendo aqui, Léo?</em> Bom, hoje o PHP 7 tem um sistema de declaração de tipos que pode até ser estrito dentro do seu projeto, mas a GraphQL não é sobre os tipos da linguagem que você implementa é sobre os tipos do seu <em>endpoint</em>, eles são normalmente implementados de acordo com seu domínio, suas <em>entities</em> (ou <em>Models</em> pra galera que curte um MVC).

Claro, você não precisa implementar do zero tipo primitivos escalares como Int, Float, String, Boolean e ID (se usar uma biblioteca descente). E existem tipos abstratos pra você usar como base na implementação dos seus próprios tipos como: Object, Interface e List.

Por falar em biblioteca descente, a Siler não implementa a GraphQL, ela é um <em>wrapper</em> da <a href="https://github.com/webonyx/graphql-php">graphql-php</a>, importante ressaltar isso e dar os devidos créditos.
<h3>Chega de "falar". Bora pro código!</h3>
Vamos criar um projetinho PHP usando Composer e um template bem simples da Siler.

<pre class="lang-bash">$ composer create-project siler/project siler-graphql</pre>

Caso não conheça o <a href="https://getcomposer.org/">Composer</a>, esse comando vai clonar o projeto <a href="https://github.com/leocavalcante/siler-project">leocavalcante/siler-project</a> e depois executar <code>composer install</code> pra instalar as dependências, que nesse caso é só a <a href="https://github.com/leocavalcante/siler">Siler</a> mesmo.

Como falei antes, a Siler não implementa a especificação da GraphQL, nela acompanha um <em>wrapper/helper</em> de uma biblioteca que já implementa essa especificação. Na Siler as dependências são explícitas, então vamos entrar no diretório do projeto e trazer a graphql-php:

<pre class="lang-shell">$ cd siler-graphql
$ composer require webonyx/graphql-php
</pre>

E agora nosso <code>index.php</code> vai ficar da seguinte forma:

<pre class="lang-php">&lt;?php

use Siler\{
    Route,
    Http\Response,
    Functional as F,
    Graphql
};

require_once __DIR__.'/vendor/autoload.php';

$query = Graphql\type('Query')([
    Graphql\str('foo')(F\always('bar'))
]);

Response\header('Access-Control-Allow-Headers', 'content-type');
Response\header('Access-Control-Allow-Origin', 'http://localhost:3000');

Graphql\init(new \GraphQL\Schema([
    'query' =&gt; $query(),
]));
</pre>

Não se assuste, vou explicar.

No primeiro bloco (3-8) estamos declarando o que iremos usar da Siler, como podem notar, ela não é só pra GraphQL, também abstrai HTTP e alguns conceitos de programação functional. E é bom deixar claro: estamos usando a notação agrupada da <em>keyword</em> <code>use</code> que veio com o PHP 7.

O que importa pra gente é 12-14 e 19-21, porque na 16 e 17 estamos apenas declarando alguns <em>headers</em> que irão na nossa resposta HTTP pro <a href="https://en.wikipedia.org/wiki/Cross-origin_resource_sharing">CORS</a> funcionar direitinho.

No bloco 12-14 estamos declarando um novo tipo GraphQL, aquele comentado anteriormente, com a Siler é só questão de chamar uma função. Na <code>Siler\Graphql\type</code> nós declaramos um <a href="http://facebook.github.io/graphql/#sec-Objects"><code>ObjectType</code></a> de nome Query, ali pode ser qualquer nome que você queira dar pra <a href="http://facebook.github.io/graphql/#sec-Initial-types">Root Query</a> do seu endpoint GraphQL. Essa função retorna outra função (porque programação funcional rulez) onde o primeiro argumento é um <em>array</em> de <em>fields</em>. Na linha 13 nós estamos declarando um novo <em>field</em> do tipo <a href="http://facebook.github.io/graphql/#sec-String"><em>String</em></a> e com mais um extra-help da Siler, passamos a função <code>always</code> que significa que vai retornar sempre esse mesmo valor (&lt;code&gt;bar&lt;/code&gt;) independente dos argumentos que essa função for chamada (<a href="http://hackage.haskell.org/package/base-4.9.1.0/docs/Prelude.html#v:const"><em>vide <code>const</code> do Haskell</em></a>).

No bloco 19-21 nós estamos iniciando um novo <em>endpoint</em> que irá ouvir e interpretar a <em>query</em> de GraphQL que veio no <em>request</em>. Estamos prontos para testar a funcionalidade da nossa API e existe uma ferramenta excelente pra isso, onde podemos testar <em>endpoints</em> GraphQL com uma interface gráfica - seria o Postman do GraphQL - é do próprio Facebook e se chama <a href="https://github.com/graphql/graphiql">GraphiQL</a>!

Se você estiver com dificuldades para configurar seu app GraphiQL, pode dar uma olhada <a href="https://github.com/leocavalcante/graphiql-app">nesse projeto</a>.

Com o GraphiQL rodando na 3000 (default do create-react-app) e a API na 8000 (default do siler/project). Podemos testar nosso <em>endpoint</em> com a premissa de que uma chamada pro <em>field</em> <code>foo</code> na <code>Query</code> o retorno deve ser <code>bar</code>:

<img class="alignnone size-full wp-image-57429" src="uploads/2017/03/Capture.png" alt="" width="370" height="233" />

<strong>Maravilha!</strong> Temos aí um Hello World de GraphQL com PHP em apenas 20 linhas de código.

Já tem muita informação pra um post só, que inclusive tá cheio de links pra você se aprofundar no assunto e descobrir que tem algo chamado <em>mutations</em> que seria a especificação para mudanças na GraphQL que não é feita só de consultas.

Se não aguenta esperar um próximo post e já sacou a ideia. Tem um <a href="https://github.com/leocavalcante/siler#graphql">trechinho no README da Siler</a> com uma <em>mutation</em> que faz a soma de dois argumentos.

Espero que tenha se interessado pela GraphQL, IMHO é uma tecnologia divisora de águas trazendo esse conceito de <em>queries</em> pro front-end. Nós temos caminhado cada vez mais para soluções menos monolíticas onde o <em>client</em> e o <em>server</em> estão bem separados e essa é a "cola" que eles precisam!