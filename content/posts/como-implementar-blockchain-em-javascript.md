---
title: Como implementar o Blockchain em JavaScript
authors: Matheus Lima
type: post
date: 2017-12-07
excerpt: Aprenda passo-a-passo a fazer uma versão simplificada do Blockchain em JavaScript
image: https://cdn-images-1.medium.com/max/2000/1*ardJWR21kRS5DoLJRAunug.jpeg
categories:
  - Javascript
  - Bitcoin
  - Na prática
tags:
  - tutorial
  - Bitcoin
  - blockchain
  - Javascript
  - Blockchain
  - Bitcoin
---

Ouvimos falar sobre Bitcoin, Ethereum além de outras moedas praticamente todos
os dias. 2017 afinal, foi o ano das
[cryptocurrencies](https://en.wikipedia.org/wiki/Cryptocurrency).

Nesse *post* porém, não vou focar em nenhuma dessas moedas digitais. Mas sim na
tecnologia por trás delas, [que muitas pessoas dizem ser tão revolucionárias
quanto a própria
internet](https://theconversation.com/the-big-business-revolution-why-the-future-is-blockchain-78409),
o Blockchain.

A ideia é implementar passo-a-passo uma versão simplificada do Blockchain em
JavaScript e ir explicando como essa tecnologia disruptiva funciona por baixo
dos panos.

Então, continue lendo esse *post* para aprender:

* O que é e como funciona o Blockchain
* *Proof of Work*?
* Pra que servem os Blocos
* O que é Mineração

*****

## Introdução

O Blockchain parece uma tecnologia de outro mundo e gera muitas dúvidas. Apesar
disso, é algo extremamente fácil de definir:

> O Blockchain nada mais é do que um banco de dados aberto e distribuído.

Esse banco de dados é composto de Blocos. E todos esses Blocos são ligados entre
si em uma sequência. Daí o nome, Blockchain (cadeia de blocos).

Além disso, esse banco de dados é imutável. <br> E faz sentido que seja.

Imagina se fosse possível que alguém intencionalmente modificasse sua conta.
Agora os 10 Bitcoins que você possui viraram 1.

## Blocos

Vamos começar a implementação pela parte mais fácil: os Blocos. A estrutura de
um Bloco deve possuir os seguintes campos:

* *index*
* *timestamp*
* *hash*
* *previousHash*
* *data*

![](https://cdn-images-1.medium.com/max/1600/1*DdJzZUrvyO49UgA1cfLTBA.png)
<span class="figcaption_hack">Crédito:
[https://medium.com/@lhartikk/a-blockchain-in-200-lines-of-code-963cc1cc0e54](https://medium.com/@lhartikk/a-blockchain-in-200-lines-of-code-963cc1cc0e54)</span>

O *index* e o *timestamp* são campos comuns em praticamente todos bancos de
dados. O campo *data* serve principalmente pra guardar transações mas podemos
também colocar outras informações. O *hash* é calculado internamente e serve pra
manter a integridade de cada Bloco e a segurança de todo o sistema (como vamos
ver no final do *post*). E por final, o *previousHash* é o elo de ligação que
liga cada Bloco ao seu Bloco anterior.

Com isso, temos a primeira implementação de um Bloco:

<script src="https://gist.github.com/matheusml/47c7e46685bcf3e861c28bf7f52a9b47.js"></script>

A função *generateHash* usa a biblioteca externa
[crypto-js](https://github.com/brix/crypto-js) pra gerar o *hash* seguindo o
padrão [sha256](https://www.tbs-certificates.co.uk/FAQ/en/sha256.html).

Parece complicado, mas tudo o que você precisa saber é que essa função vai
receber uma *string* como por exemplo:

    foo

E vai retornar uma *string* encriptada:

    2c26b46b68ffc68ff99b453c1d30413413422d706483bfa0f98a5e886266e7ae

## Blockchain

Agora que já temos uma versão mínima de um Bloco, já podemos começar a construir
o Blockchain, que como falei anteriormente é uma sequência de Blocos ligados
entre si.

Com isso, essa é a primeira versão do Blockchain:

<script src="https://gist.github.com/matheusml/3ff5e25ea8a3989fcfae387b6b910c55.js"></script>

No construtor da classe, temos o *array* de Blocos inicializado já com o
[Genesis Block](https://en.bitcoin.it/wiki/Genesis_block) (o primeiro bloco
criado no registro do Bitcoin). Adicionei também o *index* para poder
incrementar toda vez que um novo Bloco for adicionado no Blockchain.

Além disso duas funções foram criadas:

* *getLastBlock*
* *addBlock*

A primeira é extremamente simples, ela serve pra pegar o último Bloco que foi
criado.

A segunda é uma pouco mais complicada, mas também não é nada de outro mundo. Ela
serve pra adicionar novos Blocos ao Blockchain.

## Integridade

Apesar de a versão anterior já funcionar razoavelmente bem, precisamos adicionar
alguma garantia de que o Blockchain não tenha sido alterado por algum ataque
malicioso.

Precisamos adicionar uma nova função para checar a integridade do Blockchain:

<script src="https://gist.github.com/matheusml/0cae69ff3b61192d747660b52c8a3e10.js"></script>

Lembrando que para verificarmos a integridade do Blockchain precisamos garantir
três características:

* O *hash* de cada Bloco foi gerado corretamente
* O *index* dos Blocos está em sequência
* Os Blocos estão ligados entre si através dos *hashes*

Com essa simples função podemos testar se modificações maliciosas foram feitas e
se o Blockchain deve ser invalidado:

<script src="https://gist.github.com/matheusml/7ec5415e4d24f173e91b80f710d2373a.js"></script>

E finalmente com isso já temos uma primeira versão básica e funcional do
Blockchain em JavaScript:

<script src="https://gist.github.com/matheusml/c6e0e6ac8ffd5eefd177c087fdb276d5.js"></script>

*****

## Problemas

Apesar de já termos uma versão inicial funcionando, ainda podemos melhorar
bastante a nossa implementação.

Um dos problemas com essa versão atual é que usuários podem criar novos Blocos
de forma muito rápida, podendo invalidar o Blockchain, ou coisas ainda piores.
Não vou entrar em muitos detalhes dessa particularidade da tecnologia, mas o
*post* abaixo faz um excelente trabalho nesse sentido:

*[Explaining blockchain — how proof of work enables trustless consensus](https://keepingstock.net/explaining-blockchain-how-proof-of-work-enables-trustless-consensus-2abed27f0845)*

Em resumo, precisamos de alguma ferramenta que não permita que usuários possam
criar Blocos desenfreadamente.

## Proof of Work

O conceito de Proof of Work, como o próprio nome já sugere, é um mecanismo que
faz com que um usuário tenha um trabalho computacional significativo ao realizar
determinada tarefa.

Essa ferramenta já era utilizada antes do Bitcoin ser inventado para evitar por
exemplo *spams* e [ataques
DoS](https://pt.wikipedia.org/wiki/Ataque_de_negaÃ§Ã£o_de_serviÃ§o).

No Bitcoin, o Proof of Work funciona da seguinte forma: o *hash* que é gerado
automaticamente em cada Bloco deve começar com uma quantidade X de zeros,
dependendo da dificuldade geral do sistema.

Por exemplo, se a dificuldade geral do sistema for 1, esse *hash* é inválido
porque não começa com um zero:

    a5036427617139d3ad9bf650d74ae43710e36d4f63829b92b807da37c5d38e8d

Porém, esse outro hash é válido porque começa com um zero:

    07da8bff6cfea68a3f0a5bafc9b24d07f503e2282db36ffb58d43f9f4857c54b

Sempre que um usuário for criar um novo Bloco, ele vai precisar criar diversos
*hashes* até que um deles tenha a quantidade de zeros no começo fazendo com que
a regra geral do sistema seja atendida.

Ah, o nome disso é [Mineração](https://en.bitcoin.it/wiki/Mining).

Lembrando que quanto maior o número de zeros que devem estar no começo do
*hash*, maior o poder computacional necessário para a tarefa.

Dito isso, vamos agora implementar a versão final do Blockchain com a mineração.

Primeiramente vamos alterar os Blocos.

<script src="https://gist.github.com/matheusml/6a53ddc0e20441cbed988f84185e39a1.js"></script>

No construtor, adicionamos os campos *difficulty* (dificuldade geral do sistema)
e *nonce* (quantidade de tentativas até que o hash correto seja criado). Além
disso, temos também um chamada para a função *mine*.

<script src="https://gist.github.com/matheusml/9c7e4252ccded53f7d1cdafb6f5a53e3.js"></script>

A função *mine* vai criar *hashes* até que a quantidade de zeros à esquerda do
*hash* seja atentida.

Lembrando que para que os *hashes* criados sejam diferentes, devemos adicionar o
campo *nonce* na função *generateHash:*

<script src="https://gist.github.com/matheusml/137a1cb7fa90395fba034c850015a8a8.js"></script>

Com isso temos a versão final do Blocos com a mineração:

<script src="https://gist.github.com/matheusml/8dc6ffcede5dd1b117de18476f3ddc5d.js"></script>

Agora basta alterarmos o Blockchain para que o campo difficulty seja passado
para os Blocos:

<script src="https://gist.github.com/matheusml/f4c206b248acc7e843942802f9e81248.js"></script>

E é só isso :)

Lembrando que o código está [todo no GitHub](https://github.com/matheusml/blockchain-javascript).

Ah, se você quiser saber mais sobre o Blockchain:

<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/348389598&amp;color=ff5500"></iframe>

**Outras implementações:**

* [https://www.savjee.be/2017/07/Writing-tiny-blockchain-in-JavaScript/](https://www.savjee.be/2017/07/Writing-tiny-blockchain-in-JavaScript/)
* [https://medium.com/@lhartikk/a-blockchain-in-200-lines-of-code-963cc1cc0e54](https://medium.com/@lhartikk/a-blockchain-in-200-lines-of-code-963cc1cc0e54)
* [https://github.com/openblockchains/awesome-blockchains/blob/master/blockchain.js/blockchain_with_proof_of_work.js](https://github.com/openblockchains/awesome-blockchains/blob/master/blockchain.js/blockchain_with_proof_of_work.js)
