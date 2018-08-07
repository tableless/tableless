---
title: Deploy grátis de aplicações na cloud com o Now
authors: Breno Panzolini
type: post
date: 2018-08-08T08:08:00+00:00
publishdate: 2018-08-08T08:08:00+00:00
excerpt: Como fazer o deploy gratuito de aplicações na cloud utilizando o Now.
categories:
  - Tecnologia e Tendências
  - NodeJS
tags:
  - Tecnologia e Tendências
  - NodeJS
image: https://cdn-images-1.medium.com/max/1500/1*HwLQ0aoCqrkrRNFuIEQ_dQ.png
---

Hoje no mercado existem algumas plataformas e soluções que fornecem o deploy na nuvem de forma gratuita e claro que com certas limitações, afinal todo deploy tem um custo envolvido.

Acredito que a *PaaS (platform as a service)* mais conhecida atualmente é o [Heroku](https://www.heroku.com/), porém existem outras soluções disponíveis e nesse post quero apresentar o [Now](https://zeit.co/now) da Zeit.

## O que é o Now?

O **Now** é uma ferramenta que te permite fazer o deploy de aplicações JavaScript (Node), sites estáticos, serviços, entre outros de uma maneira muito simples na nuvem.

Basicamente qualquer aplicação que tenha um **package.json** ou um **Dockerfile** podem ser colocadas na nuvem com um único comando, o `now`.

## Instalando o Now

Primeiramente, vamos realizar a instalação e configuração básica do Now:

```sh
$ npm install -g now
```

Após a instalação você terá disponível o comando `now`. Para realizar o login digite:

```sh
$ now login
```

## Comandos Básicos

Nessa parte vou mostrar alguns comandos básicos do **now**, a documentação completa pode ser encontrada no [site oficial](https://zeit.co/docs/features/now-cli).

- **now login**: faz o login com uma conta de e-mail específica (não precisa de senha pois um e-mail de verificação é enviado para a conta informada)
- **now logout**: faz o logout da conta atual
- **now list**: lista os deploys vigentes
- **now remove**: remover uma aplicação pelo nome ou id da aplicação

## Exemplo Prático

Agora que já sabemos o básico, vamos fazer um deploy bem simples, apenas como exemplo.

```sh
$ mkdir exemplo-now
$ cd exemplo-now

$ touch package.json
$ touch index.js
```

- Código do package.json:
```js
{
  "scripts": {
    "start": "micro"
  },
  "dependencies": {
    "micro": "latest"
  }
}
```

- Código do index.js:
```js
module.exports = () => 'Meu primeiro teste no Now'
```

E para fazer o deploy basta rodar o comando `now`:

```sh
$ now
```

![deploy](https://i.imgur.com/w6fnp2N.png)

Nesse caso, foi gerada a URL https://exemplo-now-hyikuehach.now.sh/ para a minha aplicação.

## Pontos Positivos

Vale ressaltar alguns pontos positivos que o **Now** nos oferece:

- Facilidade: não é necessário configurarmos nenhuma chave/token de acesso e nem sequer ter o *git* instalado (como por exemplo no Heroku)
- Ilimitado: toda vez que executamos o comando *now*, uma nova URL com a nossa aplicação é gerada não havendo necessidade de removermos as versões antigas
- Tráfego Seguro: toda a comunicação com as aplicações são feitas através de HTTPS e além disso o tráfego é realizado através de *HTTP/2*

## Conclusão

Esse post foi para mostrar uma solução e alternativa para o deploy de forma gratuita das nossas aplicações na nuvem. Assim como outras *PaaS* o **Now** tem diversas vantagens e desvantagens.

Existe uma [lista de *awesome*](https://github.com/zeit/awesome-zeit) no GitHub com vários links e features bem legais para quem está utilizando o **Now**.
