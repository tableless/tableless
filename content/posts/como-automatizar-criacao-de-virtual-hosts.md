---
title: Como automatizar a criação de Virtual Hosts
author: Léo WG
type: post
date: 2015-12-06
url: /como-automatizar-criacao-de-virtual-hosts/
categories:
  - Código
tags:
  - configuração no apache
  - virtual host automático
  - virtual host no apache

---
Qualquer desenvolvedor que se preze tenta automatizar tarefas recorrentes, mesmo que não sejam tarefas diárias. É dessa forma que você consegue tempo para melhorar seu software, ganhando tempo para quebrar a cabeça com o que realmente importa.

Para quem não sabe os Virtual Hosts são apelidos dados ao caminho onde está rodando seu site ou aplicação web. Geralmente isso é feito em servidores de desenvolvimento para facilitar o acesso ao projeto. Por exemplo: em vez de colocar &#8220;**http://localhost/sites2015/joomla3/sitesdeloja/loja10**&#8221; você pode configurar o Virtual Host do servidor para simplesmente acessar com &#8220;**http://l****oja10**&#8220;.

<a href="http://do.co/1jlJLe0" target="_blank">Nesse link tem um tutorial bem completo de como configurar um virtual host no Ubuntu >></a>

Mas nesse artigo vou mostrar dois scripts que fiz para automatizar esse processo.

O 1º script é o **geravhost.sh**. O que esse script basicamente faz é pegar duas entradas, o nome que você quer dar para o vhost e o caminho do site ou aplicação web. Com essas duas informações ele já irá fazer todo o restante para você.

`<br />
<a href="http://tableless.com.br/uploads/2015/11/geravhostlinux.png"><img class="aligncenter size-full wp-image-52355" src="http://tableless.com.br/uploads/2015/11/geravhostlinux.png" alt="Código do arquivo geravhostlinux.sh" width="513" height="696" /></a>`

<a href="https://github.com/lauroguedes/vhautlinux" target="_blank">Script está no GitHub >></a>

Como o script está muito bem comentado não explicarei o passo a passo. Lembrando que fiz os testes em Ubuntu 14.04. Para facilitar a chamada do script no terminal movi o arquivo para **/usr/local/bin**, assim você simplesmente digita &#8220;**sudo geravhost.sh**&#8221; e ele já irá rodar.

Para quem usa o linux para servidor de desenvolvimento e o windows para acessar os projetos, também fiz um script para automatizar a criação do vhost no arquivo de hosts do Windows. Nesse caso ainda é mais simples, criei um arquivo chamado **gerarvhost.bat** que pede somente o nome que você quer dar para o vhost. Lembrando que fiz os testes no Windows 10.

`<br />
<a href="http://tableless.com.br/uploads/2015/11/geravhostwindows.png"><img class="aligncenter size-full wp-image-52356" src="http://tableless.com.br/uploads/2015/11/geravhostwindows.png" alt="Código do arquivo geravhostwindows.bat" width="399" height="142" /></a>`

<a href="https://github.com/lauroguedes/vhautwindows" target="_blank">Script está no GitHub >></a>

Você pode também melhorá-lo e pedir para o usuário colocar o servidor, ficando ainda mais dinâmico. Ao executar o arquivo **bat**, ele insere a string do vhost no final do arquivo. Para funcionar o nome do vhost do windows deve ser o mesmo do linux para que seja feita a associação. Depois disso é só abrir o navegador e digitar o virtual host criado. Faça os testes ai e me fala se deu tudo certo.

Espero que esse artigo lhe ajude e aumente sua produtividade. Caso tenha ficado alguma dúvida ou tenha alguma sugestão melhor comente ai.

Um abraço e até a próxima.