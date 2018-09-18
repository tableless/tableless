---
title: Uma introdução prática às threads no Node.js
authors: Breno Panzolini
type: post
date: 2018-08-19
publishdate: 2018-08-19
excerpt: Uma introdução prática às threads no Node.js
categories:
  - Javascript
  - NodeJS
tags:
  - nodejs
image: https://i.imgur.com/R4xZrtd.jpg
---

Agora no final de junho (mais precisamente no dia 20/06/2018), foi feito o _release_ da versão 10.5.0 do Node.js e uma das _features_ principais foi a inclusão inicial (e ainda experimental, diga-se de passagem), do **suporte às threads**.

Nesse post vou tentar simplificar ao máximo a documentação do [pull request](https://github.com/nodejs/node/pull/20876) e alguns detalhes técnicos, porém acredito ser suficiente para entendermos o básico da funcionalidade.

## Por que Threads?

Muita gente deve estar se perguntando do porque se utilizar threads em uma linguagem que sempre se orgulhou de nunca precisar desse tipo de mecanismo especialmente por conta do fantástico **event loop** e do **async I/O**.

O motivo disso é que o Node nunca foi a melhor opção para computação "pesada" de CPU, e por isso mesmo raramente é utilizado em projetos de _machine learning_, inteligência artificial e _data science_.

Não estou dizendo que com essa implementação de **threads** vamos poder jogar todos os nossos projetos fora e já sair implementando todas essas coisas, porém como um entusiasta de Node fico feliz em ver que a comunidade está progredindo tentando resolver esse tipo de problema.

## Como começar?

Primeiramente é necessário ter a versão mais recente do Node instalado, aconselho fortemente a utilizarem o [NVM](https://github.com/creationix/nvm) para gerenciarem as versões instaladas na sua máquina.

Outro detalhe importante é que como o módulo de **threads** (que na verdade é chamado de **worker_threads**) ainda está na versão experimental, quando formos executar o nosso script será necessário passar a flag `--experimental-worker`, caso contrário o módulo não será encontrado.

## Exemplo

Antes de mostrar um exemplo, é importante ressaltar que o módulo de **threads** é para ser utilizadas em tarefas que realmente exijam mais da CPU, utilizar esse tipo de recurso para _async I/O_ é um disperdício de recurso computacional (já que o Node lida muito bem com esse tipo de operação).

### Código:

Antes de iniciar vamos criar a estrutura de pastas e arquivos:

    $ mkdir exemplo-worker
    $ cd exemplo-worker
    $ npm init -y
    $ npm install request
    $ touch index.js
    $ touch worker-code.js

* Código do **worker-code.js**:

```js
const { parentPort } = require('worker_threads')

const start = Date.now()

// Simulando computação "pesada"
for (let i = 0; i < 1000000; i++) {
  for (let j = 0; j < 10000; j++) {
  }
}

parentPort.postMessage({ start, end: Date.now() })
```

* Código do **index.js**:

```js
const { Worker, workerData } = require('worker_threads')
const request = require('request')

function startWorker(path, cb) {
	const worker = new Worker(path, { workerData: null })
	worker.on('message', (msg) => {
		cb(null, msg)
	})
	worker.on('error', cb)
	worker.on('exit', (code) => {
		if(code != 0)
	    console.error(new Error(`Worker finalizado com exit code = ${code}`))
   })
	return worker
}

console.log("Thread principal")

// Inicia o worker em outra thread
startWorker(__dirname + '/worker-code.js', (err, result) => {
	if(err) return console.error(err)
  console.log("** COMPUTAÇÃO PESADA FINALIZADA **")
	console.log(`Duração = ${(result.end - result.start) / 1000} segundos`)
})

// Continua com o a execução na thread principal
request.get('https://www.google.com', (err, resp) => {
	if(err) return console.error(err)
	console.log(`Total bytes recebidos = ${resp.body.length}`)
})
```

### Executando o código:

Para executar o código será necessário utilizar a flag `--experimental-worker`:

    $ node --experimental-worker index.js

![exemplo execução](https://i.imgur.com/Ba5rVYu.png)

### Explicando o código:

* A thread principal e o código do worker estão separados cada um em seus respectivos arquivos.
* A função `startWorker` (do arquivo **index.js**) retorna a instância de um worker (permitindo com que mensagens sejam enviadas, caso necessário).
* O código do arquivo **worker-code.js** simplesmente tem dois `for` encadeados para simular uma tarefa computacionalmente "pesada".
* No arquivo **worker-code.js** é utilizada a função `postMessage` que envia um objeto JSON para a thread principal.
* Na thread principal (arquivo **index.js**), basicamente o que fazemos é chamar a função `startWorker` para iniciar a tarefa em outra thread e após isso fazemos um request no Google.

## Conclusão

Esse artigo foi para mostrar os passos iniciais para quem quer conhecer um pouco mais sobre as novidades que estão saindo no Node.js e também para conhecer os conceitos básicos do módulo de threads.

Algumas ressalvas importantes:

* O módulo de threads é algo novo e totalmente experimental, ou seja, muita coisa do que foi apresentado pode vir a mudar no futuro.
* Se você se interessou por esse assunto recomendo fortemente dar uma olhada na [documentação oficial](https://nodejs.org/api/worker_threads.html) e também na [PR do GitHub](https://github.com/nodejs/node/pull/20876).