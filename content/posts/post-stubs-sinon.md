---
title: Fazendo o stub de dependências com Sinon
authors: Breno Panzolini
type: post
date: 2018-05-27
excerpt: Como realizar o stub de suas dependências com o Sinon para simplificar seus testes.
categories:
  - NodeJS
  - Javascript
tags:
  - NodeJS
  - Javascript
image: https://i1.wp.com/www.zsoltnagy.eu/wp-content/uploads/2015/05/sinon1.png
---

Muitas vezes queremos testar funções que tem dependências externas, como por exemplo uma função que faz o request para uma API.

Nesse post vou mostrar como podemos criar stubs dessas dependências para facilitar os nossos testes e até mesmo conseguir testar todos os tipos de comportamentos dessas dependências.

## O que são Stubs?

Stubs em resumo são funções com um comportamento pré-programável que será fixo e previsível.

Nos nossos testes podemos utilizar stubs principalmente em dois casos:
* Quando queremos evitar a chamada de alguma dependência, por exemplo uma chamada a uma API externa.
* Quando queremos testar determinados caminhos específicos na nossa aplicação, e com isso conseguir testar os diversos cenários, por exemplo retornar *null* na chamada de determinada função.

## O Sinon

O Sinon é um pacote open-source que fornece diversas funcionalidades (como mocks, spies e stubs) que facilitam os nossos testes no JavaScript.

O Sinon por sí só não é um framework de testes, ele deve ser utilizado em conjunto com outra ferramenta para execução de testes, como por exemplo o Mocha ou Ava.

A documentação do Sinon é bem completa com diversos exemplos práticos e pode ser encontrada no [site oficial](https://sinonjs.org/), lá também podemos encontrar o passo a passo para realizar a instalação do pacote no nosso projeto.

## Exemplo Prático

Para esse exemplo, vamos tomar como base as seguintes funções:

```js
// Apenas como exemplo, o arquivo contendo essas funções estaria no path: ./src/users.js

const got = require('got')

function getUsers () {
  return got.get('https://api.com.br/v1/users')
    .then(({body}) => body)
}

async function findUser (username) {
  const users = await getUsers()
  if (users.length === 0) return undefined

  return users.find(u => u.username === username)
}

module.exports = {
  getUsers,
  findUser
}
```

Agora vamos pensar nos testes apenas da função **findUser**, de cara podemos querer testar dois cenários:

* A função **getUsers** que faz a requisição para a API retornar um array vazio
* A função **getUsers** retornar um array de usuários

Perceba que para fazer esses testes acima na função **findUser**, precisamos obrigatoriamente mudar o comportamento da função **getUsers** e é aí que podemos utilizar todo o poder que os stubs nos fornecem:

```js
// Apenas como exemplo, o arquivo contendo esses testes estaria no path: ./test/users.test.js
// Vamos assumir também que estamos utilizando Mocha + Chai para realizar os testes

const sandbox = require('sinon').createSandbox()
const users = require('../src/users')

describe('Test findUser', () => {
  afterEach(() => {
    sandbox.restore()
  })
  
  it('should return undefined if no users', async () => {
    // Na linha abaixo estou fazendo o stub da função getUsers, para simular o retorno 
    // de um array vazio e assim testar o comportamento desejado
    sandbox.stub(users, 'getUsers').returns([])
    
    const user = await users.findUser('Pedro')
 
    sandbox.assert.calledOnce(users.getUsers)
    assert(user).to.be.undefined
  })
  
  it('shuld return user by username', async () => {
    // Na linha abaixo estou fazendo o stub da função getUsers, para simular o retorno 
    // de um array contendo usuários e assim testar o comportamento desejado
    sandbox.stub(users, 'getUsers').returns([{ username: 'Maria' }, { username: 'Pedro' }])
    
    const user = await users.findUser('Pedro')
    
    sandbox.assert.calledOnce(users.getUsers)
    assert(user).to.deep.equal({username: 'Pedro'});
  })
})
```

Reparem que em ambos os testes precisávamos mudar o retorno da função **getUsers** para que fosse possível testar a função **findUser** e foi nesse momento que utilizamos o **stub** do Sinon para mudar o retorno esperado.

Observações importantes:
* Após cada teste estamos chamando a função **restore()** no **afterEach**, isso é necessário para restaurar o comportamento padrão das funções.
* Nesse exemplo estou utilizando o **sandbox** que o pacote Sinon fornece. Eu particularmente prefiro sempre utilizar o sandboxes ao invés do stub direto, pois dessa forma facilitamos o *cleanup* depois dos testes.

## Conclusão

Esse post foi para mostrar o básico de como podemos realizar o stub de funções através do pacote **Sinon**, e assim facilitar a nossa vida na hora dos testes.

Esse pacote fornece diversas outras funções bem utéis e por isso recomendo fortemente que para quem achou interessante que acesse todos os exemplos práticos que estão disponíveis na [documentação oficial](https://sinonjs.org/releases/v5.0.7/).
