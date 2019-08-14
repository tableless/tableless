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
