---
title: Teste de carga em APIs utilizando Artillery
author: Ulysses Marins
type: post
date: 2017-03-06
url: /teste-de-carga-em-apis-utilizando-artillery/
categories:
  - Back-end
  - NodeJS
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - api
  - artillery
  - buy mac cosmetic online Inflation Unmasked with These Halloween Markdowns WGQAM 234
  - load testing
  - teste
  - teste de carga

---
Independente do produto que você esteja criando, é sempre importante assegurar a qualidade do mesmo fazendo uma bateria de testes antes de colocar no mercado. Se tratando de desenvolvimento de software, existem algumas métricas que são essenciais para deixar claro para todos os envolvidos no projeto, incluindo seus usuários, o quanto determinado sistema/aplicativo é confiável para suportar o uso do público.

Dentro da área de qualidade de software, existem diversos tipos de testes que visam atingir o objetivo citado acima, de mostrar a todos que o produto é estável e robusto, alguns deles: teste de integração, teste unitário, teste de penetração, teste de regressão e por aí vai.

Este post tem como objetivo falar um pouco sobre o teste de carga, que em sua essência foi criado para simular quantidades diferentes de tentativa de acesso a determinado sistema ou device, tendo como saída um relatório de como o software se comportou em determinado cenário.

Quando falamos de APIs e escalonamento de infra, é interessante saber o número exato de requisições que o servidor (ou servidores) consegue responder corretamente em um tempo aceitável para seus clientes.

Caso você já tenha tentado fazer algo do tipo, provavelmente se deparou com o JMeter, que é uma das ferramentas mais famosas e completas para esse tipo de trabalho. Porém, a curva de aprendizado com o JMeter é um pouco longa, pois existem muitas configurações/opções que o usuário acaba se perdendo no início, até encontrar o que realmente precisa para o seu caso.<figure class="graf graf--figure">

<img class="graf-image" src="https://cdn-images-1.medium.com/max/800/1*1hZHPrQKHwCctBX7bFOPmw.png" /></figure> 

Na tentativa de tornar esse processo de teste de carga um pouco mais amigável ao usuário, foi criado o <a class="markup--anchor markup--p-anchor" href="https://artillery.io/" target="_blank" rel="noopener">Artillery</a>, uma ferramenta que com poucos passos permite você simular diversos tipos de cenários para teste de serviços que estejam utilizando para comunicação http e/ou web sockets.

Basicamente você precisa ter o <a class="markup--anchor markup--p-anchor" href="https://nodejs.org/en/" target="_blank" rel="noopener">node</a> e o <a class="markup--anchor markup--p-anchor" href="https://www.npmjs.com/" target="_blank" rel="noopener">npm</a> instalado para poder começar a brincadeira.

Para instalar o Artillery:

<pre class="lang-bash">$ npm install -g artillery</pre>

Para testar sua instalação:

<pre class="lang-bash">$ artillery dino</pre>

Caso tenha aparecido um dinossauro em seu terminal, está tudo certo e você pode seguir adiante.

Para começar a rodar seus testes de carga, é necessário criar um arquivo de configuração. Você pode dar qualquer nome a ele, mas para esse artigo, criarei um chamado <strong class="markup--strong markup--p-strong">artillery.yml</strong>.

Neste cara que você colocará todas as informações referentes a sua API, como endpoint, rotas e cenários. Você pode tanto testar rotas/recursos isolados, quanto cenários mais complexos, como por exemplo um processo de compra em um ecommerce, que basicamente teria uma rota para buscar os produtos, outra pra fazer checkout e outra para pagamento.

Segue abaixo um exemplo desse arquivo:

<pre class="lang-bash">config:
  target: '<a class="markup--anchor markup--pre-anchor" href="http://localhost:3000%27" target="_blank" rel="nofollow noopener noopener">http://localhost:3000'</a>
  phases:
    - duration: 60
      arrivalRate: 20
scenarios:
  -
    name: 'Listagem de usuários'
    flow:
    - get:
        url: "/users"</pre>

No arquivo acima colocamos o endpoint da nossa API, o atributo _duration_ representa a duração deste ciclo de teste em segundos e o _arrivalRate_ o número de novos usuários por segundo.

Para rodar o teste, rode o seguinte comando:

<pre class="lang-bash">$ artillery run artillery.yml</pre>

Após a execução, temos o seguinte resultado:<figure class="graf graf--figure">

<img class="graf-image" src="https://cdn-images-1.medium.com/max/800/1*iuh0Z_BoqM4epjC2pOvt_A.png" /><figcaption class="imageCaption">Output do Artillery</figcaption></figure> 

Todas as métricas de tempo são em milis, <em class="markup--em markup--p-em">RPS</em> (request per second), <em class="markup--em markup--p-em">codes</em> são os códigos HTTP e o número de respostas com o mesmo, no caso acima, tivemos 1200 (60&#215;20, como configuramos) requisições em 60 segundos e todas retornaram 200. <em class="markup--em markup--p-em">Scenarios launched</em> são os ‘usuários virtuais’ criados e <em class="markup--em markup--p-em">Scenarios completed</em> são quantos deles conseguiram executar o cenário com sucesso.

<strong class="markup--strong markup--p-strong">Importante: </strong>Enquanto o teste estiver rodando, um preview do resultado vai sendo printado no terminal a cada 10 segundos, mas só no final você tem os números consolidados do teste completo.

Agora você pode ir alterando números de usuários concorrentes, quantidade de tempo do teste, novos cenários, simulando fluxos mais complexos e etc.

Vale a pena dar uma olhada na <a href="https://artillery.io/docs/index.html" target="_blank" rel="noopener">documentação</a> que é super objetiva e simples de entender.