---
title: Melhorando a resiliência do seu serviço em Golang
authors: Breno Panzolini
type: post
date: 2019-08-13
excerpt: Como deixar seu serviço mais resiliente utilizando os pacotes da biblioteca go-resiliency.
categories:
  - Back-end
  - Tecnologia e Tendências
tags:
  - Golang
image: https://fiverr-res.cloudinary.com/images/t_main1,q_auto,f_auto/gigs/105341569/original/74716f149ed9a43376a98249d6bca73957bf8c8c/code-the-program-in-golang-go-programming-language.png
---

"Design for failure and nothing will fail". Acredito que grande parte dos desenvolvedores já ouviram essa frase, e atualmente cada vez mais com as arquiteturas de sistemas distribuídos, adotar padrões de resiliência deixou de ser "perfumaria" para ser algo quase que obrigatório.

Nesse post, vou mostrar como podemos melhorar a resiliência dos nossos serviços em [Go](https://golang.org/) utilizando o [go-resiliency](https://godoc.org/github.com/eapache/go-resiliency).

# go-resiliency

O [go-resiliency](https://godoc.org/github.com/eapache/go-resiliency) é um pacote que implementa alguns padrões de resiliência para serem utilizados nos seus projetos em Go.

Na verdade, podemos até classificar o **go-resiliency** como um _wrapper_ de vários padrões inspirados em diversas outras libs, entre elas podemos citar:

- [Hystrix](https://github.com/Netflix/Hystrix): desenvolvida pelo Netflix, é uma biblioteca escrita em Java que como o próprio README diz:
  
  > Hystrix is a latency and fault tolerance library designed to isolate points of access to remote systems, services and 3rd party libraries, stop cascading failure and enable resilience in complex distributed systems where failure is inevitable.

- [Semian](https://github.com/Shopify/semian): biblioteca de resiliência para Ruby

Vamos então, dar uma olhada nos principais pacotes que a biblioteca nos oferece.

## Circuit Breaker

Para entender melhor esse padrão, vou deixar a [referência do Martin Fowler](https://martinfowler.com/bliki/CircuitBreaker.html), ela é muito boa e explica tudo bem detalhadamente.

Basicamente, *circuits breakers* são importantes para proteger os pontos de integrações dos nossos serviços.

Dentro do **go-resiliency** o *circuit breaker* está no pacote **breaker**. Exemplo de uso:

```go
import github.com/eapache/go-resiliency/breaker

b := breaker.New(3, 1, 5*time.Second)

result := b.Run(func() error {
  // aqui vai o código que você deseja "proteger"
})

switch result {
  case nil:
    // sucesso na chamada
  case breaker.ErrBreakerOpen:
    // nossa função não foi chamada pois o circuito estava aberto
  default:
    // algum outro erro
}
```

## Retriable

Como o próprio nome diz, esse padrão consiste em tentar executar uma operação novamente antes de efetivamente "aceitar" o erro. 

Essa técnica parte do pressuposto de que dependendo do erro que acontece, se a operação for executada novamente ela poderá dar sucesso (por exemplo a perda de conexão momentânea com um servidor).

Dentro do **go-resiliency** o *retriable* está no pacote **retrier**. Exemplo de uso:

```go
import github.com/eapache/go-resiliency/retrier

r := retrier.New(retrier.ConstantBackoff(3, 100*time.Millisecond), nil)

err := r.Run(func() error {
  // aqui vai o código que você deseja tentar novamente
})

if err != nil {
  // se após 3 tentativas ainda obter um erro
}
```

## Deadline

Implementa um padrão de *timeout*, ou seja, protege seu código de funções que podem demorar mais tempo do que o desejável para executar.

Dentro do **go-resiliency** o *deadline* está no pacote **deadline**. Exemplo de uso:

```go
import github.com/eapache/go-resiliency/deadline

dl := deadline.New(1 * time.Second)

err := dl.Run(func() error {
  // aqui vai o código que você deseja implementar o timeout
})

switch err {
  case deadline.ErrTimedOut:
    // execução longa
  default:
    // algum outro erro
}
```

# Conclusão

Esse post foi para mostrar uma opção de pacote para melhorar a resiliência dos nossos serviços escritos em Go. Além dos padrões mencionados, o **go-resiliency** ainda fornece outros padrões como _batching_ e _semaphore_.

Recomendo fortemente para quem quiser saber mais, que consulte a [GoDoc do pacote](https://godoc.org/github.com/eapache/go-resiliency).
