---
title: 10 extensões essenciais para VS Code
authors: Gustavo Bento de Paula
type: post
image: https://i.imgur.com/xYgjtTK.png
date: 2019-05-13
url: /10-extensoes-essenciais-para-vs-code/
excerpt: 10 extensões essenciais para VS Code
categories:
  - Front-end
  - Código
---

Desde o lançamento do Visual Studio Code em 2015 a popularidade do editor de código-fonte só vem crescendo e ganhando o espaço que era divido entre editores como Sublime Text, Atom, Vim, e muitos outros.

Há cerca de 3 anos, eu, como outros desenvolvedores que trabalham comigo, decidi testar a troca do Sublime Text, como editor padrão, para o VS Code. E desde então não larguei.

Existem alguns motivos, que me levaram a optar pela troca, que não se limitam aos plugins, mas não focarei neles nessa postagem.

Hoje falarei dos 10 principais plugins (para mim) que adiciono no editor sempre quando configuro um novo ambiente de trabalho.

## 1 - [Sublime Text Keymap and Settings Importer](https://marketplace.visualstudio.com/items?itemName=ms-vscode.sublime-keybindings)

Para os acostumados com os atalhos do Sublime Text, essa extensão ajuda muito no processo de migração, pois ela permite configurar os atalhos do VS Code para executarem as mesmas funções que os atalhos Sublime Text.

## 2 - [Document This](https://marketplace.visualstudio.com/items?itemName=joelday.docthis)

Quando você trabalha em projetos com vários desenvolvedores, é de extrema importância que o seu código esteja bem escrito, legível, e documentado. Pois outras pessoas poderão vir a dar manutenção no mesmo código e, com ele bem documentado, facilitará muito esse processo.

O Document This ajuda muito na padronização da documentação dos códigos em Javascript, trazendo um template simples de comentário acima das suas funções, métodos e classes e colaborando para o intelliSence do VS Code.

## 3 - [npm Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)

Está cada vez mais comum projetos que utilizam dependências instaladas via npm. E essa extensão facilita na importação desses módulos no seu código.

## 4 - [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)

É comum cada desenvolvedor ter suas preferências de configurações do editor para codar da forma que lhe convém.

Porém pra projetos compartilhados é importante manter algumas configurações do editor (como charset, estilo de indentação, tamanho da indentação, entre outros) em comum para todos os devs que colaboram com o projeto. Além da importância do padrão de desenvolvimento do projeto, caso você ou sua empresa use o git para o versionar, facilmente ele alertará conflitos simplesmente porque uma linha está com a indentação de espaço e um outro dev "commitou" o arquivo com a indentação em tab, por exemplo.

O EditorConfig nos ajuda nessa questão. Basta instalar o plugin e criar um arquivo chamado `.editorconfig` com as configurações que você quer que sejam padronizadas para todos os devs,  e essas configurações serão aplicadas a todos os editores, que tenham o plugin instalado, somente para aquele determinado projeto.

## 5 - [Project Manager](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)

O Project Manager ajuda a você organizar os seus projetos locais.

Você pode definir projetos Favoritos ou escolher Projetos auto detectáveis do VS Code, repositórios Git, Mercurial e SVN.

## 6 - [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

O ESLint é um linter de Javascript já bem conhecido. Ele serve para criar regras e padrões para seu código Js (ponto e vírgula, indentação, etc.), alertando erros ou avisos caso o seu código esteja fora das regras definidas.

Caso você não conheça, vale a pena ler a documentação (https://eslint.org/) pois ele ajuda muito na qualidade do seu código.

## 7 - [Sass Lint](https://marketplace.visualstudio.com/items?itemName=glen-84.sass-lint)

Outro linter muito útil, porém para Sass.

Da mesma maneira que o ESLinter, o Sass Lint permite você criar regras e padrões para seu código Sass (ponto e vírgula, indentação) alertando erros ou avisos caso o seu código esteja fora das regras definidas.

Saiba mais na documentação: https://github.com/sasstools/sass-lint

## 8 - [Git Tags](https://marketplace.visualstudio.com/items?itemName=howardzuo.vscode-git-tags)

Onde trabalho, versionamos todos os nossos projetos com o Git e criamos tags e releases para cada deploy realizado.

A criação de tags não é algo complexo, porém é um processo a mais dentre vários, como criação de branch, pull request, merge, entre outros.

O plugin Git Tags encurta o processo de criação de tags com uma interface simples e intuitiva.

## 9 - [Git Lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

O VS Code já possui integração nativa com o Git, porém o Git Lens é uma extensão muito poderosa que estende os recursos do versionador que não estão disponíveis nativamente.

Ele ajuda você a visualizar a autoria de código rapidamente através de anotações, a navegar e explorar os repositórios Git, a obter informações valiosas por meio de poderosos comandos de comparação e muito mais.

## 10 - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

O Live Server te oferece de uma forma muito fácil um servidor local com direito a live reload para você desenvolver os seus projetos.

É um ótimo auxílio principalmente para projetos pequenos.

## Bônus - [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)

Na verdade esse é a primeira extensão que eu adiciono quando instalo o VS Code em alguma máquina nova e com certeza é uma das minhas prediletas.

Usando o GitHub Gist o Settings Sync sincroniza todas as suas configurações, temas e extensões para você não ter o retrabalho quando configurar um novo ambiente de trabalho ou se quiser manter todas as instâncias do editor, instaladas em máquinas diferentes, iguais.

---

Essas são algumas das extensões que uso no dia a dia, porém todas elas são muito compatíveis com a forma que eu trabalho. Para você, outras das inúmeras extensões disponíveis no marketplace da Microsoft podem ser mais vantajosas.

Espero que essas dicas possam te ajudar no seu dia a dia também.
