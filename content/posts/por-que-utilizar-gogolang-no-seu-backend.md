---
title: Por que utilizar Go/Golang no seu backend?
author: Ulysses Marins
type: post
date: 2016-06-28
excerpt: Com o respaldo dos criadores do Unix, UTF-8 e Google, a Golang promete ser rápida, simples e legível.
url: /por-que-utilizar-gogolang-no-seu-backend/
categories:
  - Back-end
  - Código
tags:
  - backend
  - go
  - golang
  - microservices

---
O tempo passa e quando você é viciado no que faz, no meu caso, codar, a busca por se aprimorar ou descobrir novas maneiras de resolver os problemas da sua área nunca param, assim sendo, um belo dia, cheguei até o **Go** e desde então não parei mais de aprender sobre a linguagem. A ideia é a cada semana fazer um post sobre, iniciando agora com uma simples introdução e sugestões de artigos para se animar.

&nbsp;

<img class="aligncenter" src="http://synflood.at/tmp/golang-slides/images/gophercolor.png" alt="Imagem do gopher" />

### O que é Go/Golang? {#o-que--gogolang}

**Go** ou **Golang** &#8211; termo que facilita buscas no google &#8211; é uma linguagem _open source_ criada em 2009 pelo **Google**, mais especificamente por caras como _Rob Pike_ e _Ken Thompson_. Caso você não conheça, são engenheiros renomados, que tiveram grande influência na história da computação e em projetos _open source_ de grande escala, pra citar um bem &#8220;simples&#8221;: **Unix**.

Só por esta constatação, você já poderia largar tudo e seguir os passos deles cegamente, afinal, Rob e Ken provavelmente não estariam trabalhando em algo meia boca. Brincadeiras à parte, a Go foi criada com objetivos simples, dentre os principais, ter a rapidez do C, mas ser um pouco mais legível e/ou fácil de programar. Inclusive, nos meus primeiros passos com a linguagem, pude sentir exatemente isso. <a href="https://www.youtube.com/watch?v=FTl0tl9BGdc" target="_blank">Aqui</a> tem um vídeo bem massa do Rob dizendo o porquê você deve aprender Go.

### Por que eu usaria Go? {#por-que-eu-usaria-go}

Acima, eu disse algumas vantagens de utilizar a linguagem, porém, a lista é bem mais vasta. Tentarei compilar os pontos que mais me chamam atenção e que possivelmente seriam casos de uso para você utilizá-la:

  * Go é incrivelmente ‘leve’ em termos de uso de memória. Existe <a href="http://www.iron.io/how-we-went-from-30-servers-to-2-go/" target="_blank">um caso conhecido</a> de uma companhia que rodava um serviço em Ruby utilizando 50 servidores e foram para 2 com Go.
  * Concorrência é um dos pontos fortes da linguagem, se você precisar sobrecarregar um backend com diversos processamentos simultâneos, as `goroutines` e `channels` <a href="https://matt.aimonetti.net/posts/2012/11/27/real-life-concurrency-in-go/" target="_blank">vão te ajudar bastante</a>.
  * Compila muito rápido.
  * Tem _garbage collector_, você não precisa se preocupar tanto com memória como nos seus dias de C.
  * É fortemente tipada. (eu pelo menos acho isso bom, phpeiros)

### Quem está usando Go? {#quem-est-usando-go}

Existe uma infinidade de empresas que ao descobrirem os poderes mágicos de Go, foram migrando seus serviços/backend. Abaixo algumas grandes:

  * Uber &#8211; <a href="https://eng.uber.com/go-geofence/" target="_blank">How we built uber engineering’s highest query per second service using Go</a>
  * Docker &#8211; <a href="http://pt.slideshare.net/jpetazzo/docker-and-go-why-did-we-decide-to-write-docker-in-go" target="_blank">Why did we decide to write Docker in Go?</a>
  * Dropbox &#8211; <a href="https://blogs.dropbox.com/tech/2014/07/open-sourcing-our-go-libraries/" target="_blank">Open sourcing our Go libraries</a>
  * OpenShift &#8211; <a href="https://blog.gopheracademy.com/birthday-bash-2014/openshift-3-old-dogs-new-tricks/" target="_blank">OpenShift3 and Go &#8211; Teaching Old Dogs New Tricks</a>
  * Twitter &#8211; <a href="https://blog.twitter.com/2015/handling-five-billion-sessions-a-day-in-real-time" target="_blank">Handling five billion sessions a day – in real time</a>

Enfim, existem muito mais empresas que se importam e/ou tem necessidade de melhorar a performance de seus serviços e grande parte delas estão olhando para Go e outras linguagens com poderes maiores do que as ‘enterprise languages’ que vemos há anos por aí nas grandes empresas do país.

Espero que o post tenha sido informativo e inspirador para você descobrir mais sobre a linguagem Go.