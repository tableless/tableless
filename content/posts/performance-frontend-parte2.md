---
title: Performance front-end – Parte 2
author: Diego Eis
type: post
date: 2013-01-28
excerpt: 'O front-end é um dos grandes responsáveis pela performance de um website ou serviço online. '
url: /performance-frontend-parte2/
dsq_thread_id: 1050033325
categories:
  - Browsers
  - Código
  - HTML
  - JavaScript
  - O Básico
tags:
  - 2013
  - browsrs
  - CSS
  - html
  - JavaScript
  - performance

---
Se você ainda não leu a primeira parte desse assunto, veja aqui: [Performance front-end &#8211; Parte 1][1].

Os browsers ajudam em muitos sentidos otimizando o carregamento de assets e a renderização da página, mesmo assim é necessário fazer algumas tarefas para que sua aplicação/website carregue mais rápido.

Quando colocamos a performance como uma tarefa durante o desenvolvimento, determinamos o aumento ou a diminuição da conversão e da quantidade de pageviews. Dependendo do tamanho do seu cliente, isso significa ter grandes resultados apenas diminuindo milésimos de segundos do carregamento.

[Nessa imagem][2], veja alguns dos resultados obtidos em grandes websites quando eles melhoraram a performance dos seus serviços. Os números podem estar meio ultrapassados, mas servem para ter uma ideia. Por exemplo: a cada 100 milisegundos que a Amazon diminui do carregamento do seu site, eles aumentam 1% do seu redimento. Faça a conta: a [Amazon teve uma receita de 13.18 Bilhões no último trimetre][3]. A cada 400 milisegundos otimizados o Yahoo! aumenta em 9% o seu tráfego. Fazendo as páginas carregarem 2.2 segundos mais rápidas, a Mozilla aumentou em 60 milhões de downloads do Firefox por ano.
  
Por isso, quando alguém disser que melhorar milisegundos de performance do seu site não é grande coisa, mostre estes números para a pessoa. Claro, que dependendo do tamanho do seu site, você não vai dobrar suas visitas apenas diminuindo 100 milisegundos do carregamento seu site. Mas com certeza ajuda.

## Medindo

Para começarmos, indico o [PageSpeed][4] para a medição da performance dos seus websites. Há outras maneiras de medir, milhares de sites e plugins, mas esse é do pessoal do Google, que além de dar uma pontuação, ele oferece fontes de informação para você entender melhor o que é cada tópico medido.

Você pode ver online [como está a performance do seu site][5]. Veja aqui o nosso em [desktops][6] ou em [mobiles][7].

No [site deles existem uma série de regrinhas e boas práticas][8]. Se quiser deixar esse artigo de lado e ir direto para lá, eu não vou ficar chateado. 😉

Veja também uma série de [ferramentas e downloads][9] para você não se sentir sozinho ao fazer o trabalho sujo.

O [YSlow][10] do Yahoo! também é ótimo. Ele tem as mesmas características do PageSpeed, logo, é questão de gosto qual dos dois você usará.

## Diminuindo o tempo de viagem

RTT (Road-trip Time) é o tempo que leva para o browser (ou qualquer outro cliente) conversar com o servidor buscando a informação solicitada pelo usuário.
  
Normalmente um browser inicia a comunicação com o servidor com pelo menos 3 RTTs: Uma requisição para a resolução do DNS. Outra para o setup de conexão TCP e outra para a requisição HTTP. Normalmente os websites tem muitas requisições HTTP. E isso é muito ruim.  

Ter muitas requisições significa que seu browser precisa ir e voltar várias vezes durante a abertura da página. Essa ida e volta são os RTT, ou a Road-trip Time. São as RTTs que contribuem para uma latência ruim nas redes. Se seu cliente demora para trazer a informação, o download da página é prejudicado.

[Nós falamos sobre isso neste artigo.][11]

## Onde colocar as chamadas de CSS e Javascript

O browser tem uma ordem correta para carregar os arquivos do site. Por isso há uma ordem específica para linkar o arquivos de CSS e Javascript, otimizando o trabalho de carregamento do browser.

Para você entender melhor, note que:
  
O CSS bloqueia a renderização da página. Isso por que o browser não quer carregar primeiro um HTML feio só para depois fazer um render da página novamente aplicando seu estilo. Por isso ele bloqueia o máximo que puder a renderização da página até que tenha carregado seu código CSS. Esta é a razão pela qual você deve inserir o link do CSS no HEAD, afim de que o browser o encontre rapidamente.

O Javascript por sua vez bloqueia o download de outros arquivos. Lembre-se de que o browser procura baixar vários arquivos ao mesmo tempo enquanto ele carrega a página. Quando carregamos o Javascript, ele pára tudo e carrega um script de cada vez. Ele faz isso por que geralmente o Javascript modifica o HTML e também o CSS. Logo, ele não pode fazer isso se o código HTML, o CSS ou outros arquivos como as imagens não foram baixados.
  
Isso também é aplicado na ordem em que você linka os arquivos de Javascript. Um exemplo simples: você não consegue fazer funcionar um plugin de jQuery se não tiver linkado o jQuery antes do script de plugin.

## Melhorando o download paralelo

Como já comentamos acima o browser sempre tenta fazer o máximo de downloads de arquivos em paralelo afim de aumentar a velocidade do carregamento. O problema é que há um limite para o download de arquivos simultâneos em um mesmo domínio. De acordo com o protocolo HTTP, os browsers podem pode ter duas conexões simultâneas por domínio. Eu não consegui encontrar um lugar que dê o número exato, mas dizem por aí que o Firefox e Chrome conseguem baixar até 6 arquivos por vez. Se um documento contem referencias para várias recursos como CSS, Javascripts, Imagens e etc, de forma que estoure o máximo permitido pelo host, o browser começa a baixar um parte e deixa os outros arquivos na fila esperando. Quando ele termina de baixar todos os recursos atuais, ele vai pra fila e pega o próximo grupo.

A estratégia é separar parte destes recursos em outro domínio. Fazendo isso o browser pode baixar o máximo de recursos por domínio paralelamente. Por isso é que normalmente separamos arquivos &#8211; como imagens &#8211; em outro servidor.

Qualquer grande site faz isso. Veja por exemplo o endereço do meu avatar no twitter: **[https://si0.twimg.com/profile\_images/2927099623/a39b6f1a9af28d8dada6bc8958392cf3\_normal.jpeg][12]**

O endereço começa com **si0.twimg.com** que é um servidor do Twitter para servir assets estáticos. Se você abrir o código fonte de qualquer grande site vai ver que isso é bem comum para diminuir a carga de carregamento.

Uma solução interessante também é usar arquivos como o jQuery ou outros scripts via CDNs. O jQuery, por exemplo, [tem uma série de CDNs pela Microsoft, MediaTemple e Google][13] que você pode usar para linkar o script ao seu projeto sem precisar fazer a requisição no seu próprio servidor.
  
Isso é bom por que você não sobrecarrega seu servidor. As vezes o donwload do arquivo pode demorar mais do que se estivesse no seu servidor. Mesmo assim, mantendo um arquivo em outro servidor, você abre caminho para que o browser faça o carregamento de outro arquivos paralelamente.

## Link prefetching e Prerender

Link prefetching é um mecanismo que utiliza o tempo ocioso do browser para fazer o download ou buscar doumentos que talvez serão usados no futuro pelo usuário. Por exemplo: se o usuário está visitando determinada página no site e você tem quase certeza de qual será a próxima página que ele visitará, você pode avisar o browser para que ele faça o download dos arquivos dessa página para o seu cache enquanto ele estiver ocioso, de forma que quando o usuário for visitar essa página a renderização é agilizada.

<pre class="lang-html">&lt;link rel="prefetch" href="/imagens/destaque.jpg"&gt;
</pre>

Ou:

<pre class="lang-html">&lt;link rel="prefetch" href="http://seuwebsite.com.br/parte2/"&gt;
</pre>

Existe também o link prerender. Nesse caso o browser além de baixar os assets necessários, ele pré renderiza a página na memória de forma que ao visitar essa página, ela já estará totalmente renderizada. Diferentemente do link prefetch que apenas baixa os arquivos e só renderiza a página quando o usuário fizer a visita.

Nem preciso dizer que isso deve ser usado com muito cuidado, principalmente quando estamos produzindo algo para mobiles. Você não quer acabar com a bateria e o pacote de dados do usuário baixando páginas que talvez ele nem vá visitar. Por isso é recomendável fazer o prefetch/prerender de poucas páginas e arquivos por vez. Se você não tem certeza de qual será a página a próxima página visitada, é melhor nem utilizar essa tática.

<pre class="lang-html">&lt;link rel="prerender" href="http://seuwebsite.com.br/parte2/"&gt;
</pre>

## Concluindo

A busca por performance deve ser algo constante. Há alguns pontos que você não conseguirá cobrir, nesse caso, não se preocupe. Faça um estudo do seu caso e entenda até onde você pode ir para melhorar a performance de seus serviços. Use e abuse de ferramentas para melhorar seu trabalho e entenda melhor como funciona os browsers. Todas essas informações melhorarão seu processo de produção e definirão uma experiência mais amigável para o usuário.

### Para ler mais

  * [Best Practices for Speeding Up Your Web Site][14]
  * [Front-end performance for web designers and front-end developers][15]
  * [Maximizing Parallel Downloads in the Carpool Lane][16]
  * [Five Ways to Speed Up Page Response Times][17]

 [1]: http://tableless.com.br/performance-frontend-parte1/
 [2]: http://www.strangeloopnetworks.com/assets/images/infographic2.jpg
 [3]: http://computerworld.uol.com.br/negocios/2012/04/27/receita-da-amazon-cresce-34-no-trimestre-e-bate-expectativas/
 [4]: https://developers.google.com/speed/pagespeed/?hl=pt-BR
 [5]: https://developers.google.com/speed/pagespeed/insights
 [6]: https://developers.google.com/speed/pagespeed/insights#url=tableless.com.br&mobile=false
 [7]: https://developers.google.com/speed/pagespeed/insights#url=tableless.com.br&mobile=true
 [8]: https://developers.google.com/speed/docs/best-practices/rules_intro?hl=pt-BR
 [9]: https://developers.google.com/speed/tools?hl=pt-BR
 [10]: http://yslow.org/
 [11]: http://bit.ly/WhiWbW
 [12]: https://si0.twimg.com/profile_images/2927099623/a39b6f1a9af28d8dada6bc8958392cf3_normal.jpeg
 [13]: http://jquery.com/download/
 [14]: http://developer.yahoo.com/performance/rules.html
 [15]: http://csswizardry.com/2013/01/front-end-performance-for-web-designers-and-front-end-developers/
 [16]: http://www.yuiblog.com/blog/2007/04/11/performance-research-part-4/
 [17]: http://sixrevisions.com/web-development/five-ways-to-speed-up-page-response-times/