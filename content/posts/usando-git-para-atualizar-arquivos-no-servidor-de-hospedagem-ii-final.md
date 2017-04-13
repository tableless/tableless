---
title: Usando GIT para atualizar arquivos no servidor de hospedagem II – Final
author: João A. Zonta
type: post
date: 2015-11-19
url: /usando-git-para-atualizar-arquivos-no-servidor-de-hospedagem-ii-final/
categories:
  - Artigos
  - Back-end
  - Código
  - Git
  - PHP
  - Técnicas e Práticas
tags:
  - bitbucket
  - deploy
  - desenvolvimento
  - desenvolvimento web
  - git
  - Na Prática
  - php
  - Técnicas e Práticas

---
Esta é a segunda e última parte do artigo que explica como fazer um esquema simples para deploy automático usando GIT + Bitbucket

A mesma configuração pode ser usada em qualquer servidor GIT e qualquer serviço de hospedagem que tenha acesso via ssh e git instalado

Se você ainda não leu a primeira parte, segue o link: <http://tableless.com.br/usando-git-para-atualizar-arquivos-no-servidor-de-hospedagem>

No artigo anterior, criamos as chaves SSH para autenticação no Bitbucket, criamos um repositório GIT e manualmente executamos o comando | git pull | para atualizar o nosso repositório.

Nessa segunda parte vamos executar o comando para atualização, de forma automatizada, sem precisar acessar o servidor. Vamos fazer um painel de controle para acompanhar os logs de deploy, mostrando se o comando foi executado com sucesso ou se aconteceu algum erro.

Gostaria de lembrar que essa é uma solução simples, existem várias maneiras de fazer deploy automatizado, eu escolhi fazer usando php e shell_exec, é mais rápido e para projetos simples isso funciona muito bem. O mesmo pode ser feito usando [CGI][1] ou [Shell Script][2], ou ainda você pode usar um serviço online como o heroku.com, ou configurar o Capistrano, ou Jenkins, etc&#8230;

#### O Comando shell_exec no PHP

No manual do php:
  
(PHP 4, PHP 5, PHP 7)
  
shell_exec — Executa um comando via shell e retorna a saída inteira como uma string

Isso quer dizer que podemos executar um comando no servidor e ler o retorno desse comando, no nosso caso vamos executar o comando | git pull origin master | o mesmo comando que estávamos executando manualmente lá no servidor, lembra que tínhamos que acessar o servidor via putty, navegar até a pasta do nosso repositório e depois executar um git pull, já que isso é uma tarefa repetitiva, vamos automatizar, é isso que devemos fazer com todos os processos repetitivos.

Em muitos servidores de hospedagem esse comando é bloqueado por padrão, se estiver bloqueado você vai receber um aviso parecido com esse:

<pre class="lang-shell">Warning:  shell_exec() has been disabled for security reasons in /var/www/deploy.php on line 10</pre>

No meu caso eu abri um chamado no painel da hospedagem, explicando que precisava da liberação para usar em um sistema de deploy automático usando GIT e prontamente fui atendido e o comando foi liberado.

Vou usar o mesmo repositório que usei para a primeira parte, [https://bitbucket.org/jzonta/artigo\_atualizacao\_arquivos][3]

Vamos Começar, e vamos usar um dos termos da metodologia XP &#8211; Extremme Programing, &#8220;Baby Steps&#8221;, vamos executar todo o processo em pequenos passos, eu vou atualizar o repositório no GIT com todos os passos, você pode acessar e ver todos os commits &#8211; inclusive os errados 🙂 &#8211; é bacana pra ver a evolução do código.

Vou criar uma pasta chamada deploy e dentro um arquivo chamado index.php, quando executado pelo navegador ele atualiza nosso servidor executando o comando git pull no servidor e imprimindo na tela o resultado do commnado.

A pasta deploy deve ficar dentro da pasta do seu projeto, você pode ver a estrutura que usei no repositório desse artigo no Bitbucket.

_* Note que no final do comando git pull eu adicionei &#8220;2>&1&#8221; isso quer dizer que alem das saídas normais eu quero exibir as saídas de erro do nosso comando no servidor._

index.php

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"/&gt;
&lt;title&gt;Usando GIT para atualizar arquivos no servidor de hospedagem&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
	&lt;pre&gt;
	&lt;?php
		$exec = shell_exec("git pull origin master 2&gt;&1");
		echo $exec;
	?&gt;
	&lt;/pre&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

A saída na tela é a mesma que aparece quando executamos o comando lá no servidor, veja o exemplo da saída no servidor e no navegador:

[<img class="alignnone size-full wp-image-51941" src="http://tableless.com.br/uploads/2015/10/comando_shell_navegador.jpg" alt="comando_shell_navegador" width="657" height="210" />][4]

_* Lembre-se que para enviar esse arquivo ao servidor você não deve usar o ftp, faça isso utilizando o comando |git pull|, já fizemos isso na primeira parte do artigo._

Já estamos atualizando nosso servidor apenas acessando uma url em nosso navegador \o/, mas não é só isso que queremos, eu quero que essa url seja chamada sempre que eu enviar um push para o repositório, então acesse sua conta no Bitbucket e vamos configurar isso.

Acesse seu repositório, no menu lateral esquerdo, clique em &#8220;Configurações&#8221;.
  
Na tela configurações clique em &#8220;Webhooks&#8221; e depois em &#8220;Add Webhook&#8221;
  
No campo &#8220;Title&#8221; adicione um nome de sua preferência e no campo &#8220;URL&#8221; adicione o endereço para a sua url que executa o comando de atualização, no meu caso a URL é &#8220;http://joaozonta.com.br/artigo\_atualizacao\_arquivos/deploy/index.php&#8221;
  
Mas não podemos deixar essa URL aberta, porque qualquer um poderia acessar e isso iria executar o comando git pull em nosso servidor, então vamos criar um token de autenticação, junto com a URL eu passo um token que mais tarde vamos validar lá no nosso código, então a URL ficaria assim: http://joaozonta.com.br/artigo\_atualizacao\_arquivos/deploy/index.php?token=d41d8cd98f00b204e9800998ecf8427e

_* Use este site para gerar seu token: <http://www.miraclesalad.com/webtools/md5.php>_

[<img class="alignnone size-full wp-image-51940" src="http://tableless.com.br/uploads/2015/10/adicionar_webhook.jpg" alt="adicionar_webhook" width="850" height="439" />][5]

Feito isso, toda vez que enviar um push para o Bitbucket ele vai acessar a URL, e nossa url vai disparar o comando |git pull| no servidor e os arquivos serão atualizados. Nosso deploy já esta funcionando, mas eu também quero visualizar os logs, para ter maior controle sobre oque esta acontecendo.

[<img class="alignnone size-full wp-image-51943" src="http://tableless.com.br/uploads/2015/10/local_git_servidor.jpg" alt="local_git_servidor" width="444" height="352" />][6]

_*No seu repositório no Bitbucket, vc pode ver os requests que foram feitos entrando em &#8220;Configurações&#8221;, &#8220;Web Hooks&#8221;, ao lado do Title do seu webhook você clica em &#8220;View Requests&#8221; e pode ver todas as requisições que o Bitbucket fez para a sua URL._

#### Gravando Log

Primeiro vamos gerar o texto que queremos gravar no nosso arquivo de log, poderíamos apenas colocar a saída do comando shell_exec, mas vamos adicionar a data, hora e algumas quebras de linha para deixar o nosso log mais legível, veja como ficou o código:

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"/&gt;
&lt;title&gt;Usando GIT para atualizar arquivos no servidor de hospedagem&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
	&lt;pre&gt;
	&lt;?php
		$exec = shell_exec("git pull origin master 2&gt;&1");
		echo $exec;

		$textoLog = PHP_EOL."Data: ".date(d."/".m."/".Y." - ".H.":".i.":".s);
		$textoLog .= PHP_EOL.$exec;

		$arquivoLog = fopen('log.txt', 'a+');
		fwrite($arquivoLog, $textoLog);
		fclose($arquivoLog);
	?&gt;
	&lt;/pre&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>

Não precisa explicar muito o código php porque é bem simples, se alguém tem dúvida dobre alguma das funções usadas é só dar uma procurada no site do php (<php.net>) ou no google, tem bastante material.

Se tudo está ocorrendo como planejado, quando você executar novamente seu endereço URL ele vai criar um arquivo chamado log.txt na mesma pasta, e gravar os logs neste arquivo.

#### Adicionando Token de Validação

Vamos deixar nosso deploy um pouco mais seguro. Lembra que na URL que adicionamos lá no webhook do Bitbucket colocamos um token? Então, agora vamos validar esse token.

Criei uma variavel chamada $token e adicionei a nossa string MD5
  
Depois a variavel $tokenValido recebe true se o token enviado via post ou get for igual ao token que configuramos na variavel $token, caso contrário recebe false.
  
Depois verificamos se $tokenValido for igual a true executa o deploy se não exibe o log e um botão para atualizar manualmente.

<pre>&lt;?php
$token = "d41d8cd98f00b204e9800998ecf8427e";
if($_REQUEST['token'] == $token)
	$tokenValido = true;
?&gt;
&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"/&gt;
&lt;title&gt;Usando GIT para atualizar arquivos no servidor de hospedagem&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;pre&gt;
	&lt;?php
		if($tokenValido) {
			$exec = shell_exec("git pull origin master 2&gt;&1");
			echo $exec;

			$textoLog = PHP_EOL."Data: ".date(d."/".m."/".Y." - ".H.":".i.":".s);
			$textoLog .= PHP_EOL.$exec;

			$arquivoLog = fopen('log.txt', 'a+');
			fwrite($arquivoLog, $textoLog);
			fclose($arquivoLog);
		} else {
			//Deve exibir o log e um botão para para executar a atualização
		}
	?&gt;
&lt;/pre&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

#### Implementando a Leitura do Log e Botão Para Atualizar

No código abaixo foi adiciona a implementação que lê o arquivo de log através do comando file() e depois exibe na tela, também foi adicionado um formulário com o botão &#8220;Atualizar&#8221;, caso ocorra alguma falha na atualização automática através do webhook esse botão pode ser utilizado para forçar essa atualização e executar o nosso deploy.

<pre class="lang-php">&lt;?php
$token = "d41d8cd98f00b204e9800998ecf8427e";
if($_REQUEST['token'] == $token)
	$tokenValido = true;
?&gt;
&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"/&gt;
&lt;title&gt;Usando GIT para atualizar arquivos no servidor de hospedagem&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
	&lt;pre&gt;
		&lt;?php
		if($tokenValido) {
			$exec = shell_exec("git pull origin master 2&gt;&1");
			echo $exec;

			$textoLog = PHP_EOL."Data: ".date(d."/".m."/".Y." - ".H.":".i.":".s);
			$textoLog .= PHP_EOL.$exec;

			$arquivoLog = fopen('log.txt', 'a+');
			fwrite($arquivoLog, $textoLog);
			fclose($arquivoLog);
		} else {
		?&gt;
			&lt;form action="index.php" method="post"&gt;
				&lt;input type="hidden" name="token" value="d41d8cd98f00b204e9800998ecf8427e"&gt;
				&lt;input type="submit" value="Atualizar"&gt;
			&lt;/form&gt;
		&lt;?php
		$texto = file('log.txt');
		foreach ($texto as $linha) {
			echo $linha;
		}
		}
		?&gt;
	&lt;/pre&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

#### Adicionando Autenticação

Tudo funcionando, mas qualquer um pode entrar na nossa URL, visualizar os logs e clicar no botão para atualizar o servidor.

Então vou implementar uma autenticação simples, iniciando uma sessão e usando a variável $senhaAcesso, então nossas regras seriam as seguintes:

Se receber o token, faz a validação, se estiver correto, atualiza o nosso servidor
  
Se receber a senhaAcesso, faz a validação se estiver correto, mostra o log e o botão para atualizar
  
Se não receber o token e nem a senhaAcesso mostra um form solicitando a senha

Nosso código tem apenas 3 condições no if, eu preferi deixar assim pra ficar mais fácil de entender, as condições separadas para ficar mais fácil de entender:

<pre>if($tokenValido) {
		    // Se o toquem for válido
		    // Executa o comando git pull para atualizar o servidor e grava o log
		} else if($_SESSION['usuarioValido']) {
		    // Se o usuário estiver logado mostra o log e o botão para atualizar
		} else {
		    //Se o usuário não estiver logado mostra o formulário para logar
		}
</pre>

Abaixo o código completo desta etapa:

<pre>&lt;?php
session_start();
$token = "d41d8cd98f00b204e9800998ecf8427e";
$senhaAcesso = 'joaozonta';

if($_REQUEST['token'] == $token)
	$tokenValido = true;

if($_REQUEST['senhaAcesso'] == $senhaAcesso && empty($_SESSION['usuarioValido']))
	$_SESSION['usuarioValido'] = true;

if($_REQUEST['sair'])
	unset($_SESSION['usuarioValido']);
?&gt;
&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"/&gt;
&lt;title&gt;Usando GIT para atualizar arquivos no servidor de hospedagem&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;pre&gt;
	&lt;?php
		if($tokenValido) {
			$exec = shell_exec("git pull origin master 2&gt;&1");
			echo $exec;

			$textoLog = PHP_EOL."Data: ".date(d."/".m."/".Y." - ".H.":".i.":".s);
			$textoLog .= PHP_EOL.$exec;

			$arquivoLog = fopen('log.txt', 'a+');
			fwrite($arquivoLog, $textoLog);
			fclose($arquivoLog);
		} else if($_SESSION['usuarioValido']) {
		?&gt;
		&lt;form action="index.php" method="post"&gt;
			&lt;input type="hidden" name="token" value="d41d8cd98f00b204e9800998ecf8427e"&gt;
			&lt;input type="submit" value="Atualizar"&gt;
		&lt;/form&gt;
		&lt;?php
		if($_SESSION['usuarioValido'])
			echo '&lt;p&gt;&lt;a href="index.php?sair=true"&gt;Sair&lt;/a&gt;&lt;/p&gt;';
			$texto = file('log.txt');
			foreach ($texto as $linha) {
				echo $linha;
			}
		} else {
		?&gt;
		&lt;form action="index.php" method="post"&gt;
			&lt;div&gt;
				&lt;input type="text" placeholder="Senha" name="senhaAcesso"&gt; 
			&lt;/div&gt;
			&lt;input type="submit" value="Acessar Sistema"&gt;
		&lt;/form&gt;
		&lt;?php
		}
	?&gt;
&lt;/pre&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

#### Conclusão

De uma maneira muito simples você pode atualizar seu servidor sem depender de um sistema complexo de deploy e sem muitas configurações.

Você pode implementar muitas outras opções para deixar o seu sistema cada vez mais completo, pode adicionar um botão para limpar o log ou adicionar o log em um banco de dados. Já imaginou mostrar um combo com os últimos commits realizados e você escolher qual desses commits você quer atualizar no servidor, podendo assim voltar e avançar versões.

Não falei sobre banco de dados nesse artigo, acho que isso pode ser tratado em outro tópico.

Você pode ver o exemplo funcionando em [http://joaozonta.com.br/artigo\_atualizacao\_arquivos/deploy/][7], use a senha &#8220;joaozonta&#8221;

*_No exemplo que esta no ar foram comentadas as linhas que fazem o deploy automático, está apenas simulando o funcionamento._

Fique á vontade para entrar em contato para qualquer dúvida, sugestão, crítica ou erro que encontrar nesse artigo.

João A. Zonta
  
[joaozonta.com.br][8]
  
[@joaozontaweb][9]
  
<joao@joaozonta.com.br>

 [1]: https://pt.wikipedia.org/wiki/CGI
 [2]: https://pt.wikipedia.org/wiki/Shell_script
 [3]: https://bitbucket.org/jzonta/artigo_atualizacao_arquivos
 [4]: http://tableless.com.br/uploads/2015/10/comando_shell_navegador.jpg
 [5]: http://tableless.com.br/uploads/2015/10/adicionar_webhook.jpg
 [6]: http://tableless.com.br/uploads/2015/10/local_git_servidor.jpg
 [7]: http://joaozonta.com.br/artigo_atualizacao_arquivos/deploy/
 [8]: http://www.joaozonta.com.br
 [9]: https://twitter.com/joaozontaweb