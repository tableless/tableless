---
title: Usando ESlint e hooks no git
authors: Tailo Mateus Gonsalves
type: post
image: https://cdn-images-1.medium.com/max/1600/1*5ytPO1t6Dhz-RuN0NtBiJw.jpeg
date: 2018-03-05
excerpt: Como mandar bem nos commits
categories:
  - Front-end
  - Javascript
  - Código
  - Git
---

Quantas vezes você mandou aquele push com erros ou totalmente fora do padrão? Aquele commit faltando 5 minutos para acabar o horário de expediente.  Isso pode acontecer com qualquer pessoa, indiferente se você é um iniciante ou um “senior” que só faz coisas fantásticas. Cabe a nós melhorar as nossas limitações ou falta de atenção. O objetivo deste artigo é te ajudar nesse quesito.

## Criando o package.json

Com isso, vai criar o arquivo e aceitar todos os valores default:
```
npm init –y
```
Para saber mais:

[Working with package.json] (https://docs.npmjs.com/getting-started/using-a-package.json)

[npm-init] (https://docs.npmjs.com/cli/init)

## Instalando ESlint

É um analisador de código JavaScript, criado em 2013 por Nicholas C. Zakas. Basicamente, ESlint permite que os desenvolvedores encontrem problemas e criem suas próprias regras e padrões de desenvolvimento. Escrito em Node.js podemos instalá-lo via npm.

```
npm install eslint --save-dev
```
Configurando o arquivo de configuração:
```
./node_modules/.bin/eslint --init
```
Selecione a opção: “Use a popular style guide” e após selecione o style guide da empresa que preferir.

Selecione o formato do arquivo em “JavaScript”. Após esses passos e se tudo ocorreu bem, vai ser criado o arquivo .eslintrc.js. 

## Testando ESlint

Crie um arquivo chamado main.js, dentro dele coloca o código:
```
a = 10
const b = 5;
b = 10
```

Ao ler o código, podemos perceber que vai acontecer alguns erros. Mas vamos testar como o ESlint se comporta, para executar:

```
./node_modules/.bin/eslint *.js
```

Agora é só corrigir os erros :D

Para saber mais: 

[Documentação ESlint] (https://eslint.org)

[Demo ESlint] (https://eslint.org/demo/)

[Setting up ESLint on Sublime Text 3] (https://medium.com/@junshengpierre/making-the-switch-from-jshint-to-eslint-5b6c4fa3c92a)

## Utilizando npm Scripts

No arquivo package.json, substitua esse trecho:
```
“scripts”: {
	“lint”: “./node_modules/.bin/eslint *.js”
}
```
Para rodar no terminal:
```
npm run lint
```

Para saber mais:
[Why npm Scripts? ] (https://css-tricks.com/why-npm-scripts/)

## Hooks no git

São scripts que fazem algo antes ou depois de alguma tarefa, por exemplo, antes de um commit faça algo.

Instalando o Husky:
```
npm install husky@next --save-dev
```
Para utilizar vamos adicionar o comando prepush no npm scripts:
```
“scripts”: {
	“lint”: “./node_modules/.bin/eslint *.js”,
	“prepush”: “lint”
}
```
Antes de enviarmos o push, vai executar o lint.

Para saber mais:

[Repositório GitHub] (https://github.com/typicode/husky)

## Conclusão

Espero ter ajudado. Qualquer dúvida, em todas as partes deste artigo tem referências. Tem alguma dica? Deixa nos comentários :D