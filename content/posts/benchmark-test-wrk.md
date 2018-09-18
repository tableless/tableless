---
title: Realizando testes de stress em sua API
authors: Breno Panzolini
type: post
date: 2018-04-23
excerpt: Como realizar testes de stress em suas aplicações na sua máquina local com o wrk.
categories:
  - Tooling
  - back-end
tags:
  - Tooling
image:  https://fredericoporto.com.br/wp-content/uploads/2017/07/post-alta-performance-head-banner.jpg
---

Nesse post vou mostrar como podemos executar de maneira muito simples e fácil testes de stress nas nossas APIs utilizando o nosso próprio computador.

# Introdução

Cada vez mais como desenvolvedores precisamos nos preocupar com a performance das nossas APIs, não importa o quão bom o nosso front-end foi arquiteturado e desenvolvido, se nossas APIs demorarem para responder isso irá se refletir para o usuário final.

## O que são testes de stress?

Testes de stress (ou _load tests_ como o termo é conhecido em inglês) são testes de performance que visam testar o nosso software sobre condições extremas de uso em um curto período de tempo.

Esse tipo de teste é uma importante forma de mensurar, medir e identificar o quanto a nossa aplicação consegue responder diante de condições extremas. Além disso, esse tipo de teste pode nos ajudar a escolher determinada tecnologia ou linguagem de programação na hora do desenvolvimento das nossas APIs.

# Realizando testes de stress

Existem diversas formas de realizarmos testes de stress nas nossas aplicações, muitas delas necessitam que ambientes inteiros sejam montados para isolar nossa aplicação de quaisqueres fatores externos.

Eu concordo que a maneira mais correta e eficaz de realizar esse tipo de teste é realmente executá-lo em um ambiente totalmente separado e exclusivo para que fatores externos não impactem o teste. Porém, muitas vezes como desenvolvedores precisamos de uma maneira rápida, simples e eficaz de executarmos esse tipo de teste.

Além disso, muitas vezes estamos na fase inicial da arquitetura de uma nova API e precisamos coletar dados iniciais para decidirmos com qual linguagem específica ou caminho seguir.

## Instalando o wrk

O **wrk** é uma ferramenta opensource que está disponível no [GitHub](https://github.com/wg/wrk) e que possibilita a execução completa de testes de stress na nossa máquina local.

Você pode instalar o wrk em todos os sistemas operacionais, e todas elas podem ser encontradas no [wiki do projeto](https://github.com/wg/wrk/wiki). Como estou utilizando o sistema OS X, vou realizar a instalação através do **brew**.

```
$ brew install wrk
```

Após isso teremos a ferramenta **wrk** à nossa disposição.

```
$ where wrk
/usr/local/bin/wrk
```

# Montando nossa aplicação

Como o objetivo desse artigo não é entrar no desenvolvimento em si das aplicações, vou apenas explicar bem brevemente o que vou fazer.

Vou realizar o teste de stress em duas APIs muito simples, uma delas será desenvolvida em **Node com express** e a outra em **Go**.

O objetivo aqui não é comparar qual das duas linguagens é melhor, mas sim mostrar como executar os testes de stress.

## Aplicação Node

```javascript
const express = require('express')
const app = express()

function fibonacci (num) {
  if (num === 0 || num === 1) {
    return num
  }
  return fibonacci(num - 1) + fibonacci(num - 2)
}

app.get('/', (req, res) => {
  const result = fibonacci(10)
  return res.send(`Result = ${result}`)
})

app.listen(5050, () => console.log('Listening on port 5050'))
```

## Aplicação Go

```go
package main

import (
	"fmt"
	"log"
	"net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
	result := fibonacci(10)
	fmt.Fprintf(w, "Result = %v", result)
}

func main() {
	http.HandleFunc("/", handler)
	err := http.ListenAndServe(":5050", nil)
	if err != nil {
		log.Fatal(err)
	}
}

func fibonacci(num int) int {
	if num == 0 {
		return num
	}
	if num == 1 {
		return num
	}
	return fibonacci(num-1) + fibonacci(num-2)
}
````

# Executando os testes de stress

Ambas as aplicações vão rodar na porta 5050 e vamos executar o seguinte teste: fazer a requisição no nossa aplicação durante 10 segundos simulando 100 conexões, ou seja, vamos ter que executar o seguinte comando **wrk**

```
$ wrk -c 100 -d 10s https://localhost:5050
```

## Testando a aplicação Node

```
# Primeiro inicio a API
$ node index.js
Listening on port 5050
```

Agora em um outro terminal vou executar o teste:

![Teste stress Node](https://i.imgur.com/rm3gw1f.png)

## Testando a aplicação Go

```
# Primeiro inicio a API
$ go run main.go
```

Agora em um outro terminal vou executar o teste:

![Teste stress Go](https://i.imgur.com/qkQCmGU.png)

## Resultados do teste

Após realizar os dois testes acima, podemos tirar métricas importantes como latência, e a quantidade de requests por segundo. No exemplo podemos notar que a aplicação em **Node** rodando no meu computador local **(o que não se compara com as configurações de um servidor real de produção)** consegue atender 5.936 requests/seg, enquanto que a aplicação em **Go** atende 38.400 requests/seg.

# Conclusão

Esse artigo foi para mostrar uma maneira simples de realizarmos testes de stress na nossa máquina localmente, óbvio que para cenários mais concretos e complexos precisamos executar o teste em ambientes específicos para esse tipo de teste de performance, porém o **wrk** se mostra uma eficiente ferramenta para testes iniciais.

Quem quiser conhecer todos os parâmetros e opções disponíveis do **wrk** basta consultar o [repositório oficial](https://github.com/wg/wrk).
