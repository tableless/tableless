---
title: Como instalar Node.js no Linux corretamente (Ubuntu, Debian, Elementary OS)
author: Mateus Malaquias
type: post
date: 2017-01-09
url: /como-instalar-node-js-no-linux-corretamente-ubuntu-debian-elementary-os/
categories:
  - Código
  - JavaScript
  - NodeJS
tags:
  - angular2
  - linux
  - NodeJS

---
Recentemente comecei a minha migração do JSF para o Angular então busquei por um bom curso, pela documentação do _Framework_ e um bom livro técnico.

No caso do curso escolhi inicialmente o do [Flávio Almeida][1] na [Alura][2] e logo de cara fica claro que não é um _Framework_ para iniciantes no mundo do JavaScript e nem para iniciantes no mundo da programação, o próprio Flávio avisa sobre isso mais de uma vez além de informar sobre a necessidade de dominar o terminal (o terror dos novatos) do seu sistema operacional.

Neste curso o Flávio já começa explicando como instalar os requisitos básicos para se começar a estudar sendo basicamente necessário ter instalado o [Node][3], qualquer editor de texto (utilizo muito o [SublimeText][4], mas pra quem ta começando recomendo usar o [Visual Code][5] porque ele nativamente consegue trabalhar muito bem com Angular e Node) e o NPM.

Em distribuições _Debian Based_ é muito comum utilizar o comando **apt install -nome do pacote-** e com o [Node][3] isso pode lhe trazer problemas, novamente o Flávio avisa sobre o possível problema. Entretanto tenho certeza que os mais novos no linux vão preferir utilizar o comando **apt install -nome do pacote-** do que fazer a instalação do pacote binário e muito provavelmente isso vai quebrar tudo, porque até o momento que estou escrevendo esse texto os repositórios do Debian estão desatualizados (o Debian tem o costume de demorar para atualizar seus repositórios).

Minha recomendação é que você **não instale o Node** pelo comando **sudo apt-get install -y nodejs** vai acontecer um conflito de nomes entre _node_ e _nodejs_, parece besteira que uma simples nomenclatura quebre tudo, mas não é! O NPM que é o gerenciador de dependências vai ficar perdido e algumas funções não funcionarão.

![][6]

**Calma! É tentador entrar em desespero, mas segure sua onda…**

Se você não deseja compilar o arquivo binário de instalação do Node na mão grande, a solução de instalação contínua simples, instale o NVM primeiro e depois o Node. O legal do NVM é que você pode instalar várias versões do Node e ficar alternando entre elas, mas antes de instalar o NVM precisamos de alguns pacotes de dependências que já estão no repositório de sua distribuição Debian Based.

#### _sudo apt-get update sudo apt-get install build-essential libssl-dev_

Agora que você já tem o necessário em seu sistema vamos instalar o NVM:

#### _curl -sL_ [_https://raw.githubusercontent.com/creationix/nvm/_**_v0.31.0_**_/install.sh_][7] _-o install_nvm.sh_

O número da versão que está em negrito pode mudar com o tempo, então recomendo você acessar a [página do projeto no GitHub][8] e procurar pela nova versão.

Execute o scrpit com:

#### _bash install_nvm.sh_

Não tenha medo, o que está sendo feito aqui é o download de um script e a execução do mesmo, tudo vai ser instalado em um diretório oculto na pasta do seu usuário **não é necessário utilizar o comando com** _sudo_ **nesse caso**.

Agora execute:

#### _nvm ls-remote_

Ele vai te exibir várias versões do Node e assim sabemos que o NVM está funcionando corretamente. Eu escolhi a versão mais recente do momento a v7.3.0, você pode instalá-la digitando:

#### _nvm install 7.3.0_

Caso você instale mais de uma versão e no futuro tenha necessidade de alternar entre elas utilize o comando:

#### _nvm use -número da versão-_

Agora vamos verificar a versão do Node para ter certeza que tudo foi instalado corretamente utilizando o comando:

#### _node -v_

Pronto, agora você já pode dar continuidade aos seus estudos de Angular ou Node.

 [1]: https://twitter.com/flaviohalmeida
 [2]: https://www.alura.com.br/curso-online-angular2-parte1
 [3]: https://nodejs.org
 [4]: https://www.sublimetext.com/
 [5]: https://code.visualstudio.com/
 [6]: uploads/2017/01/gritos.jpeg
 [7]: https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh
 [8]: https://github.com/creationix/nvm