---
title: Entendendo as técnicas de prebrowsing
authors: Diego Eis
type: post
date: 2017-11-25
excerpt: Saiba como dar dicas para o browser carregar e pré renderizar arquivos e páginas.
image: https://i.imgur.com/W3y0Thp.jpg
categories:
  - HTML
  - Browser
  - Performance
tags:
  - performance
  - browser
  - HTML
  - prefetch
  - prerender
---

Você já deve saber que boa parte da performance de um site [está relacionado ao tratamento do front-end](https://browserdiet.com/). Além das técnicas como minificação, concatenação, gzip, posição dos links de JS e CSS no HTML, sprite images e etc, existe uma prática que tem se tornado bastante popular (mas é MUITO antiga) chamada **prebrowsing**. O prebrowsing é na verdade uma série de técnicas que dão **dicas** para o browser se adiantar enquanto o usuário não toma uma decisão.

Iremos ver aqui algumas dessas técnicas que formam o **prebrowsing**, sendo elas: *DNS pre-fetching*, *preconnect*, *prefetching* e *pre-render*.

## Explicando os Hints
O W3C chama isso de **Resource Hints** e você pode [ver a documentação aqui](https://www.w3.org/TR/resource-hints/#introduction).

Como eu disse, essas técnicas dão **dicas** para o browser de como ele deve carregar antecipadamente recursos ou até mesmo páginas inteiras. Elas são dividas em duas formas:

- Um **link de dica de recurso** incluem *dns-prefetch*, *preconnect*, *prefetch* ou *prerender*, que são usados para indicar uma origem ou recurso que devem ser conectados pelo browser. 
- O browser pode também **especular uma busca**, iniciando o download, carregando e execução de um recurso ou página usando o *prefetch* ou *prerender*.

Essas dicas são feitas usando o elemento **&lt;link&gt;** direto no HEAD do documento. Todas essas técnicas ajudam o desenvolvedor a ajudar o browser a tomar decisões importantes no processo de performance, indicando como o browser poderá se adiantar enquanto o usuário navega pela página atual.

Vamos às técnicas.

## DNS Pre-fetching
O [DNS Pre-fetching](https://www.w3.org/TR/resource-hints/#dns-prefetch) indica a origem dos recursos usados na página e que o browser poderá resolver o quanto antes. O tempo que o browser leva para resolver o DNS de alguns recursos usados na página podem aumentar um bocado a latência percebida pelos usuários. O DNS Pre-fetch é uma forma do browser resolver dos DNS antes do usuário seguir para um determinado link ou antes do browser precisar carregar um determinado recurso. 

Para usar é muito simples, basta colocar uma tag link com o recurso ou o domínio que quer fazer com que o browser adiante a resolução do DNS:

```
<link rel="dns-prefetch" href="https://code.jquery.com/">
```


## Preconnect
O **Preconnect** é bastante parecido com o DNS Pre-fetching, mas além de resolver o DNS, ele já irá adiantar o TCP Handshake e a negociação TLS se necessário. É usado da mesma forma, trocando o valor do rel para `preconnect`:

```
<link rel="preconnect" href="https://code.jquery.com/">
```

## Prefetching
O link **prefetch** é usado para identificar um recurso que poderá ser usado pelo usuário em navegações futuras e que o browser poderá baixá-la agora, guardando esse recurso no cache para ser usado depois. Você pode fazer isso com uma imagem ou com um script, por exemplo. Perceba que o browser **não irá executar esse recurso**, ele irá apenas guardar para facilitar carregamento quando necessário.

```
<link rel="prefetch" href="//seudominio.com.br/uma-pagina.html" as="html" crossorigin="use-credentials">
```

Perceba que existe ali um atributo `as`, onde você já avisa para o browser como ele deve tratar aquele arquivo, assim ele já entende o contexto daquele recurso, otimizando o processo de fetching, por exemplo, definindo quais tipos de requisições de headers ou a prioridade de transferência e etc...

Há também ali o [atributo crossorigin](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#cors-settings-attributes), onde você indica a política de CORS para o recurso em questão.

Uma boa pedida é usar isso para facilitar o carregamento de fonts!

```
<link rel="prefetch" href="/fonts/suafont.woff" as="font">
```

## Prerender
O **Prerender** é usado para identificar um recurso que será usado numa próxima navegação e que o browser deverá carregar e executar previamente, a fim de entregar uma resposta rápida do recurso quando for a hora.

```
<link rel="prerender" href="https://seusite.com.br/suapagina.html">
```

O browser irá processar o HTML, já fazendo a busca e a execução dos recursos relacionados a este HTML... em outras palavras o browser irá fazer uma **renderização prévia** da página. Isso é como se fosse uma tab escondida no browser do usuário, que vai carregar a página completa.

A dica é que você utilize isso para pré-renderizar uma página que provavelmente será a próxima que o usuário irá visitar. Para carregar um arquivo, por exemplo um plugin JS ou até mesmo o jQuery, é aconselhável usar o **prefetching**.

## Use de forma estratégica
A ideia é que você use cada uma dessas técnicas de forma estratégica. Por exemplo, imagine uma galeria de imagens ou um carrossel, onde o usuário vê as imagens de forma sequencial, nesse caso seria interessante usar o **prefetching** para carregar a próxima imagem.

Outro exemplo são websites que usam serviços de analytics ou outros serviços que usam muito JS, nesse caso é interessante usar o **preconnect**, que já adianta todo o processo de requisição como resolução de DNS, handshake etc...

No caso do **prerender** é bom ter bastante cuidado. Pode ser que você tenha pedido para o browser renderizar previamente uma página pesada, que usa bastante processo da máquina, que poderá consumir bastante bateria ou banda do usuário (lembre-se da galera usando 3/4G), é bom ter a consciência de que o usuário pode clicar num link que provavelmente não foi o link que você pré-renderizou, aí já era, você fez o browser carregar uma página inteira à toa.

Existem cenários onde você vai saber exatamente qual será a próxima página que o usuário deverá ir, como por exemplo depois do login ou quando ele está lendo um artigo/livro com páginas sequenciais... Tenha bom senso.


## Mais fontes:
- [Eliminating Roundtrips with Preconnect](https://www.igvita.com/2015/08/17/eliminating-roundtrips-with-preconnect/)
- [Preload Hints For Web Fonts](https://www.bramstein.com/writing/preload-hints-for-web-fonts.html)
- [Chromium - For Developers](https://dev.chromium.org/developers/design-documents/dns-prefetching)
- [Prebrowsing](https://www.stevesouders.com/blog/2013/11/07/prebrowsing/)
- [Minimize DNS lookups](https://varvy.com/pagespeed/dns-lookups.html)
- [DNS Prefetching - David Walsh](https://davidwalsh.name/dns-prefetching)
- [Prioritising resource loading on the page.](https://patrickhamann.com/workshops/performance/tasks/2_Critical_Path/2_3.html)