---
title: Vulnerabilidades em Sistemas Web
author: Marcus Aurelius
type: post
date: 2016-07-11
excerpt: Uma das principais vulnerabilidades web se encontram na URL do site e nem todos os desenvolvedores têm conhecimento delas
url: /vulnerabilidades-em-sistemas-web/
titulo_personalizado:
  - 'Vulnerabilidades em <strong>sistemas web</strong>'
categories:
  - Back-end
  - Destaques

---
## O que são vulnerabilidades em sistemas web?

Vulnerabilidades em sistemas web são uma realidade cada vez mais crescente na internet. Primeiro deixem-me explicar rapidamente como funciona a comunicação entre o _browser_ e o servidor web. Sistemas web funcionam com uma dupla muito conhecida neste ramo: requisição e resposta.

A requisição se origina do lado do usuário (pelo Chrome, IE, Firefox, Safari, cURL, etc) composta de elementos como _header_, URL, método, parâmetros, _cookies_, etc. Ela é enviada para um servidor web que responde pelo domínio (o &#8216;www.algumacoisa.com.br&#8217;) da requisição. Por sua vez, o servidor processa a requisição e retorna para o usuário a resposta (42?), também composta de partes conhecidas como _header_, _body_, _code_, _cookies_, etc.

As vulnerabilidades web nascem quando determinadas partes oriundas da requisição, são processadas sem o devido tratamento pelo servidor. Essas partes podem ser _cookies_ mal configurados, o ID de uma sessão exposta no navegador e até mesmo os parâmetros passados pela URL ou num formulário de _login_, por exemplo. Essas informações, quando não são tratadas no servidor se caracteriza como uma falha de segurança, deixando assim o próprio servidor suscetível à ataques específicos através da exploração dessas falhas.

### Como sei se minha URL, ou melhor, se meu site está vulnerável através de minha URL?

Entre as várias formas existentes para explorar vulnerabilidades web, a Nº 01 do <a href="https://www.owasp.org/index.php/Top_10_2013-Top_10" target="_blank">Top 10</a> da OWASP (_Open Web Application Security Project_) é a _A1 &#8211; Injection_, injeção direta de código malicioso através de parâmetros enviados pela requisição, ou seja, pelo usuário. A OWASP é uma organização que visa orientar desenvolvedores, analistas, arquitetos e empresas quanto aos riscos das vulnerabilidades em sistemas web.

Existe um teste bem simples para saber se  existem vulnerabilidades em sua URL: forçando um erro. Tomemos como exemplo um ambiente web, com um banco de dado MySQL, a aplicação em PHP e a URL no padrão:

<p style="text-align: center">
  http://www.meudominio.com.br/produtos.php?id=15
</p>

A extensão da URL não importa muito nesse momento, o problema está nos parâmetros, e estou supondo um banco de dados MySQL apenas para exemplificar o erro.

<p class="lang-php">
  Digamos então que, no lado do servidor, naquele arquivo <em>produtos.php</em> que fica na raiz do site, existe uma linha de código que recebe via GET o parâmetro &#8216;id&#8217; e nosso amiguinho que o desenvolveu implementou a regra de busca de produto no banco de dados com a seguinte consulta SQL:
</p>

`$id = $_GET['id'];<br />
$sql = "SELECT * FROM produtos WHERE produtos.id = {$id}";`

Até aí tudo bem, o código funciona, isso se o valor passado no parâmetro &#8216;id&#8217; da URL sempre for um número. Entendeu? E se eu substituir o valor do parâmetro &#8216;id&#8217; na URL por uma letra, ou até mesmo acrescentar um simples apóstrofo após o número 15 e o servidor retornar algo do tipo:

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near &#8220;15&#8221; LIMIT 1&#8242; at line 1

Não quero assustar ninguém, mas alguém com conhecimentos avançados em consultas SQL pode explorar essa falha de segurança e como resultado obter acesso a todo o banco de dados da aplicação, podendo assim baixar dados sigilosos, como número de cartões de crédito, ou obter acesso ao sistema como um usuário autenticado, quebrando a encriptação de senhas através de força bruta, isso se a senha estiver encriptada. Tudo isso através de sua URL.

Essa técnica é chamada de Injeção de SQL (SQL Injection), quando o atacante tenta alterar o código SQL para conseguir acesso à essas informações, direto do banco de dados e segundo a OWASP é considerada uma das vulnerabilidades em sistemas web mais comuns.

### Como faço para me proteger?

Lembra daquela parte do código que recebeu o parâmetro &#8216;id&#8217; da URL? Pois então, uma solução bem prática seria fazer o parse (forçar o valor) para o tipo inteiro, que no PHP poderia ficar assim:

`$id = (int) $_GET['id'];`

Dessa forma, qualquer valor que não fosse um número inteiro seria forçado para um simples 0 (zero).

Existem outras formas de se explorar falhas como essa, seja através da URL ou de formulários, mas para mitigá-las é necessário realizar uma varredura em todo o código em que a aquisição de dados através de parâmetros se faz presente, e realizando as devidas correções.