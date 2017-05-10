---
title: Otimizando e organizando seu front-end com PHP
author: Layo Azevedo
type: post
date: 2013-04-28
excerpt: Quer ser diferente no mercado? Conheça o PHP e suas vertentes. Auxiliando e organizando seus projetos front-end
url: /otimizando-e-organizando-seu-front-end-com-php/
dsq_thread_id: 1234115424
categories:
  - Código
  - HTML
tags:
  - CSS
  - html com php
  - php

---
Não é de hoje que se fala em otimização e organização de scripts. Não há dor de cabeça maior para um desenvolvedor back-end receber uma marcação HTML bagunçada e sem padronização. Isso é mais comum do que imaginamos e nem sempre é por falta de conhecimento ou preguiça. O maior fator é o curto tempo para finalizar os projetos.

A ideia desse post é justamente auxiliar os desenvolvedores a criarem um núcleo de código no PHP para reaproveitá-lo diversas vezes, como se fosse um módulo.

#### O PHP e suas vertentes

O primeiro passo é conhecer um pouco dessa linguagem. Ela é muito extensa e com diversos recursos. Vai depender muito do que o desenvolvedor quer se especializar. Existem desenvolvedores que mandam muito bem em programação voltada para e-commerce, outros se especializam em sistemas ERP, sites institucionais, webservices, processadores de emails e assim por diante… No nosso caso vou mostrar alguns recursos que são bem direcionados a qualquer projeto front-end.

#### HTML e PHP

Muitos desenvolvedores acham que é cada um por si, eu particulamente não sigo esse raciocinio. Vou ilustrar algumas situações que auxiliarão e facilitarão a manutenção dos scripts, mesclando a linguagem de programação PHP com a marcação HTML.

##### Imagine a seguinte situação:

Tenho um site com 250 páginas HTMLs e meu cliente deseja modificar o menu principal, colocando mais um item, como eu desenvolveria em HTML? Entraria nas 250 páginas e alterava todos os menus? Criaria um iframe? Muitos fariam isso, mas a partir de hoje, não mais!

<pre class="lang-html">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" xml:lang="pt-br" lang="pt-br"&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;
&lt;title&gt;Trabalhando com PHP no front-end&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div id="menu"&gt;
&lt;ul&gt;
&lt;li&gt;&lt;a href="index.html" class="ativo" title="Inicio"&gt;Inicio&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="quem-somos.html" title="Quem somos"&gt;Quem somos&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="contato.html" title="Contato"&gt;Contato&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

Primeiro passo, crie uma página PHP. No meu caso irei colocar o nome &#8220;menu-principal.php&#8221; com a div que contém o menu:

<pre class="lang-html">&lt;div id="menu"&gt;
&lt;ul&gt;
&lt;li&gt;&lt;a href="index.html" class="ativo" title="Inicio"&gt;Inicio&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="quem-somos.html" title="Quem somos"&gt;Quem somos&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="contato.html" title="Contato"&gt;Contato&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/div&gt;</pre>

Agora basta chamar nossa página principal utilizando o php (Lembre-se a página principal deve utlizar a extensão &#8220;.php&#8221;):

<pre class="lang-php">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" xml:lang="pt-br" lang="pt-br"&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;
&lt;title&gt;Trabalhando com PHP no front-end&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;? require_once ("menu-principal.php"); ?&gt;

&lt;/body&gt;
&lt;/html&gt;</pre>

OBS: Existem 4 formas de chamar o arquivo &#8220;menu-principal.php&#8221; include, include\_once, require e require\_once. Utilizei o require\_once pois ele salva em cache, ou seja, puxa uma vez os dados. Toda hora que requisitar uma página o menu já vai estar disponivel no browser do cliente ao contrário do include, que chama os dados a cada requisição e se houver algum erro, ele não para o código ao contrário do require\_once que dá o famoso erro FATAL ERROR.

É simples?

Muito simples não precisamos de conhecimentos aprofundados na linguagem, porém conseguimos melhorar a manutenção do código não é? Por quê não desenvolvemos tambem para o rodapé? Ou qualquer elemento que irá repetir várias vezes? Agora é com você.

##### Segunda situação

Imagine diversos formulários em um projeto ERP onde você é o responsável front-end, seria uma dor de cabeça desenvolver diversas páginas, vários tipos de inputs, selects etc.. Por quê não criamos padrões para esse tipo de situação tambem? Que tal desenvolvermos um núcleo igual fizemos com o menu, porém com informações que são dinâmicas e com características próprias:

Temos a seguinte página HTML:

<pre class="lang-html">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" xml:lang="pt-br" lang="pt-br"&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;
&lt;title&gt;Trabalhando com PHP no front-end&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;form method="post" action="envio.php"&gt;
&lt;p&gt;&lt;input type="text" name="nome" class="base-form"/&gt;&lt;/p&gt;
&lt;p&gt;&lt;input type="text" name="email" class="base-form"/&gt;&lt;/p&gt;
&lt;p&gt;&lt;input type="text" name="telefone" class="base-form"/&gt;&lt;/p&gt;
&lt;p&gt;&lt;input type="submit" name="envio" value="Envio" /&gt;&lt;/p&gt;
&lt;/form&gt;

&lt;/body&gt;
&lt;/html&gt;</pre>

Vou entrar em uma questão agora que Orientação a objeto no PHP é um assunto muito bem falado na internet e muito utlizado por desenvolvedores. Irei tentar explicar com um exemplo bem simples, o aprendizado dessa técnica, que é fantástica.

Vamos criar um padrão para um simples formulário, utilizando uma classe chamada (formulario) no PHP, ela irá conter todas as características que necessitamos no front-end:

<pre class="lang-php">&lt;?php
class Formulario {

function __construct ($AcaoForm, $MetodoDeEnvio) {
echo '&lt;form action="'.$AcaoForm.'" method="'.$MetodoDeEnvio.'"&gt;';
}

function __destruct () {
echo "&lt;/form&gt;";
}

function Input ($Tipo, $Nome, $Classe) {
echo '&lt;p&gt;&lt;input type="'.$Tipo.'" name="'.$Nome.'" class="'.$Classe.'" /&gt;&lt;/p&gt;';
}

function Submit ($NomeSubmit, $Valor) {
echo '&lt;p&gt;&lt;input type="submit" name="'.$NomeSubmit.'" value="'.$Valor.'" /&gt;&lt;/p&gt;';
}
}

?&gt;</pre>

Nesta classe desenvolvemos um corpo para todos os formulários. Criamos apenas para os elementos: input e submit. Você pode desenvolver para todas as propriedades como select, radio, textarea etc&#8230; O nosso passo agora é instanciar a nossa classe e chamar os nossos métodos colocando suas propriedades:

<pre class="lang-php">&lt;?php
$objeto = new Formulario('pagina.php','post');
$objeto-&gt;Input('text', 'nome', 'formulario-classe');
$objeto-&gt;Input('text', 'email', 'formulario-classe');
$objeto-&gt;Input('text', 'telefone', 'valida-tel');
$objeto-&gt;Input('hidden', 'token', 'ok');
$objeto-&gt;Submit('envio', 'Enviar');
?&gt;</pre>

Ou seja, criamos essa estrutura HTML :

<pre class="lang-html">&lt;form method="post" action="envio.php"&gt;
&lt;p&gt;&lt;input type="text" name="nome" class="formulario-classe"/&gt;&lt;/p&gt;
&lt;p&gt;&lt;input type="text" name="email" class="formulario-classe"/&gt;&lt;/p&gt;
&lt;p&gt;&lt;input type="text" name="telefone" class="valida-tel"/&gt;&lt;/p&gt;
&lt;p&gt;&lt;input type="hidden" name="token" value="ok" /&gt;&lt;/p&gt;
&lt;p&gt;&lt;input type="submit" name="envio" value="Enviar" /&gt;&lt;/p&gt;
&lt;/form&gt;</pre>

Ficamos assim com o script final:

<pre class="lang-php">&lt;?php
class Formulario {

function __construct ($AcaoForm, $MetodoDeEnvio) {
echo '&lt;form action="'.$AcaoForm.'" method="'.$MetodoDeEnvio.'"&gt;';
}

function __destruct () {
echo "&lt;/form&gt;";
}

function Input ($Tipo, $Nome, $Classe) {
echo '&lt;p&gt;&lt;input type="'.$Tipo.'" name="'.$Nome.'" class="'.$Classe.'" /&gt;&lt;/p&gt;';
}

function Submit ($NomeSubmit, $Valor) {
echo '&lt;p&gt;&lt;input type="submit" name="'.$NomeSubmit.'" value="'.$Valor.'" /&gt;&lt;/p&gt;';
}
}
?&gt;

&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" xml:lang="pt-br" lang="pt-br"&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /&gt;
&lt;title&gt;Trabalhando com PHP no front-end&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;?php
$objeto = new Formulario('pagina.php','post');
$objeto-&gt;Input('text', 'nome', 'formulario-classe');
$objeto-&gt;Input('text', 'email', 'formulario-classe');
$objeto-&gt;Input('text', 'telefone', 'valida-tel');
$objeto-&gt;Input('hidden', 'token', 'ok');
$objeto-&gt;Submit('envio', 'Enviar');
?&gt;

&lt;/body&gt;
&lt;/html&gt;</pre>

O ideal é criar um diretório apenas com arquivos que possuem classes, por exemplo: Class.Html, Class.Form, Class.SQL, Class.CSS, etc..
  
Depois chamamos esses dados com um require, include ou mesmo através do __autoload() desse jeito você irá desenvolver e criar seus padrões, melhorarando ainda mais seu nível de desenvolvimento.

Que tal criarmos uma função que utilize um alerta do javascript apenas mudando o parâmetro de entrada. Com o PHP isto é possível, no exemplo abaixo utilizei um outro estilo de programação que é a linear/procedural.

<pre class="lang-php">function MensagemAlert($parametro) {
echo '
&lt;script&gt;
alert("'.$parametro.'");
&lt;/script&gt;
';
}

// chamar a função na página de envio
MensagemAlert('Preencha os dados corretamente');

?&gt;</pre>

No PHP podemos trabalhar com o modelo de programação Orientado a objeto, linear ou mesclando os dois.

Bom, é isso. Espero que tenham gostado e aguçado a imaginação e criatividade de todos vocês.