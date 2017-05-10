---
title: 'Frame Player: Indo além da tag video em dispositivos móveis'
author: Vagner Santana
type: post
date: 2013-11-27
excerpt: |
  |
    Será que nos dias de hoje todos os problemas envolvendo arquivos de media em dispositivos móveis foram resolvidos, ou novos problemas foram criados?
url: /frame-player-indo-alem-da-tag-video-em-dispositivos-moveis/
dsq_thread_id: 2002987745
categories:
  - Código
  - HTML5
  - JavaScript
  - Mobile
tags:
  - frame player
  - html5
  - JavaScript
  - mobile
  - video

---
Desde que o Flash se tornou obsoleto em dispositivos móveis (ou em outras palavras: quando a Apple o baniu do iOS) a forma de manipular arquivos de media ficou cada vez mais tendenciosa para uso das tags `audio` e `video`, consolidando o padrão Web. De toda forma o Flash ainda sobrevive bem neste ramo (prova disso é o YouTube que mantém seu player), mas este não será o foco deste artigo. O ponto mais importante que iremos tratar aqui é a reprodução de vídeos usando HTML5 em smartphones e tablets.

Será que nos dias de hoje todos os problemas envolvendo arquivos de media em dispositivos móveis foram resolvidos, ou novos problemas foram criados?

Sistemas operacionais móveis tendem a implementar especificidades, seja por limitações dos dispositivos ou algo envolvendo a usabilidade do sistema, o fato é que algumas vezes essas implementações não obedecem especificações, criando barreiras e limitando assim o desenvolvimento de aplicações web.

### Os Problemas com a Tag Video Criados pelos Sistemas Operacionais Móveis

Quando inserimos um vídeo em uma página web utilizando a tag `video` esperamos que o navegador fique responsável por carregar seu player nativo (exibindo seus controles caso seja utilizado o atributo `controls`), até então nenhum problema visto que praticamente <a href="http://caniuse.com/#search=video" target="_blank">todos os navegadores modernos</a> (inclusive de dispositivos móveis) oferecem suporte, claro que cada um serão necessários os vários formatos de vídeo (codec) para poder reproduzir em diferentes navegadores, mas o grande problema não esta ai, e sim no comportamento que este player nativo toma quando carregado em dispositivos móveis.

A especificação da tag `video` define diversos <a href="http://www.w3.org/TR/html-markup/video.html#video-attributes" target="_blank">atributos</a>, vamos nos atentar para alguns em específico: `autoplay`, `preload` e `loop`. Iremos analisar cada um deles e seu comportamento nos próximos parágrafos.

O atributo `autoplay` tem a função de iniciar a reprodução um vídeo automaticamente sem a necessidade de interação do usuário, analisando o <a href="https://developer.apple.com/library/safari/documentation/AudioVideo/Conceptual/Using_HTML5_Audio_Video/Device-SpecificConsiderations/Device-SpecificConsiderations.html" target="_blank">guia da Apple para o Safari</a> na seção de Audio e Vídeo em HTML5 temos um tópico sobre este assunto, no qual relata que os métodos `play()` e `load()` são desabilitados em dispositivos iOS, exceto quando ocorre uma ação do usuário, ou seja, o atributo `autoplay` não funciona, assim como o seguinte código também não irá funcionar:

<pre class="lang-html">&#060;body onload="document.myMovie.play()"&#062;
</pre>

O atributo `preload`, responsável por carregar parte do arquivo de media junto da página e antes de sua reprodução, tem comportamento semelhante ao `autoplay`. Neste caso pode ser levado em consideração esta ação, pois dispositivos móveis se conectam por redes de celulares, que muitas vezes cobram por dados trafegados.

É possível utilizar o atributo `loop` em dispositivos móveis, porém para garantir suporte a todos os dispositivos, é necessário incluir o hack abaixo, pois algumas versões (ex: iOS abaixo da versão 5) não suportam este atributo.

<pre class="lang-javascript">var video = document.getElementById('your-video-elem');

    function loopVideo(){
        video.currentTime = 0.1;
        video.play();
    }

    video.addEventListener('ended', loopVideo, false);
</pre>

Uma outra grande limitação é o controle de volume, ao tentar recuperar o valor atual do volume por JavaScript sempre será retornado 1, e este valor não pode ser alterado por código, tornando possível alterar o volume ou colocar no mudo apenas com interação do usuário pelos botões físicos. Assim como o volume também não é possível definir valores para a propriedade `playbackRate`, tornando impossível implementar slow motion ou fast foward.

Dispositivos móveis ao encontrarem um arquivo de vídeo em páginas web, renderizam esse quadro definindo uma imagem de placeholder por cima da imagem carregada pelo atributo `cover` (quando definida), esta ação torna inviável o uso de vídeos como background por exemplo.

<img src="http://f.cl.ly/items/1L3Y1p1r1Y3B1E0l0W11/ios-video-placeholder.png" width="338" height="600" alt="iOS video placeholder image" />
      
_iOS video placeholder image (a big play icon on center)._ 

O elemento `canvas` possui um método `drawImage` em sua API, no qual permite inserir imagens, vídeos e até mesmo outro elemento canvas, porém este método <a href="https://developer.apple.com/library/safari/documentation/AudioVideo/Conceptual/HTML-canvas-guide/PuttingVideoonCanvas/PuttingVideoonCanvas.html" target="_blank">não é suportado em dispositivos iOS</a>, a Apple afirma que este método utiliza muitos recursos do sistema, no Safari Desktop o método funciona perfeitamente.

Por fim chegamos em dois fatores que considero mais limitantes, por serem impossíveis de serem solucionados. O primeiro fator é: vídeos em smartphones não podem ser carregados inline, somente em tela cheia. Já o outro fator é: não podemos reproduzir dois ou mais arquivos de aúdio ou vídeo simultaneamente, apenas um arquivo é permitido por vez, simplesmente por opção das empresas que desenvolvem os sistemas móveis.

### Uma Alternativa para Vídeos e Gifs

Considerando os problemas relatados anteriormente, quando surge a necessidade de desenvolver uma aplicação web baseada em videos para smartphones, isto é, uma aplicação que tem como base arquivos de vídeo com elevado nível de personalização e interação com o usuário, é perfeitamente possível de ser desenvolvida para navegadores desktop, porém inumeros problemas serão apresentados em dispositivos móveis. Um bom case para exemplificar este tipo de aplicação é o <a href="https://vimeo.com/79706014" target="_blank">site que a Apple desenvolveu em 2012 para promover seus novos produtos</a>.

Criar animações de imagens similares a um vídeo é uma tarefa que o GIF já faz, porém este tipo possui <a target="_blank" href="http://stories4all9858180.wordpress.com/2012/12/05/advantages-and-limitations-of-gifs/">diversas limitações</a>, tendo como principal a profundidade de cor máxima: 256 bit, o que torna a qualidade da imagem baixa, inviabilizando seu uso em dispositivos com alta resolução de tela.

Pensando nestes fatos surgiu a necessidade de criar uma alternativa que pudesse solucionar os problemas do vídeo e do GIF em dispositivos móveis, algo que pudesse reproduzir imagens em sequência (com uma certa qualidade) e que pudesse ser personalizado com a necessidade da aplicação, deixando isso a cargo do desenvolvedor. Esta necessidade é tão real que a Apple, em seu site citado acima, <a href="http://www.tuaw.com/2012/10/16/how-apples-iphone-5-website-works/" target="_blank">criou uma alternativa própria</a> para desenvolver estas animações sem utilizar vídeo e garantir suporte em todos os tipos de dispositivos, esta solução é bem próxima do que será discutido a seguir, existe uma <a target="_blank" href="https://docs.google.com/document/pub?id=1GWTMLjqQsQS45FWwqNG9ztQTdGF48hQYpjQHR_d1WsI">análise minuciosa</a> sobre esta técnica utilizada pela Apple.

### Criando um Player de Frames

A necessidade comentada no parágrafo anterior teve seus requisitos bem definidos: reproduzir animações baseadas em imagens em uma certa taxa de velocidade, que tenha bom desempenho em dispositivos móveis, que seja personalizável e possa ter mais de uma instância executando em uma mesma página. Surgiu ai então o <a href="http://vagnervjs.github.io/frame-player/" target="_blank">Frame Player</a>.

#### O que é o Frame Player?

O Frame Player é uma biblioteca JavaScript desenvolvida por <a href="https://twitter.com/vagnervjs" target="_blank">Vagner Santana</a> (eu) para reproduzir videos utilizando imagens no lugar de tipos comuns deste formato de media (i.e.: .mp4, .avi). A biblioteca se encarrega de mostrar uma sequência de imagens em uma determinada taxa de velocidade (fps), desta forma não é necessário utilizar a tag video.

#### Transformando Vídeo em Imagens

Para que um vídeo seja reproduzido no Frame Player, é necessário extrair cada frame deste arquivo genrando uma sequência de imagens.

Para gerar essa sequência de imagens a documentação do Frame Player instrui o uso do software <a href="http://www.ffmpeg.org/" target="_blank">FFmpeg</a> para conversão, utilizando o seguinte comando: 

<pre class="lang-terminal">$ ffmpeg -i video.mp4 -an -f image2 "%d.jpg"
</pre>

Onde `video.mp4` é o arquivo original em formato de vídeo, e `%d.jpg` o destino final dos arquivos de imagens que serão gerados com nome em ordem numérica.

Após a extração dos frames, cada imagens deverá ser codificada em `base64` utilizando <a href="https://developer.mozilla.org/en-US/docs/data_URIs" target="_blank">Data URI Scheme</a> e armazenadas todas em um único arquivo `JSON`. Para isso junto do Frame Player foi desenvolvido um `script` (disponível em PHP e Node.js) que codifica e cria um arquivo de saída `JSON`. O script é executado em linha de comando da seguinte forma: 

<pre class="lang-terminal"># Option 1: Node.js
    $ cd converter
    $ node app.js frameStart frameEnd folder/to/imgs/ json/video.json

    # Option 2: PHP
    $ php to_data_uri.php frameStart frameEnd folder/to/imgs/ json/video.json
</pre>

Os parâmetros `frameStart` e `frameEnd` deverá ser um valor numérico representando o frame inicial do vídeo e o frame final respectivamente. O caminho `folder/to/imgs/` será a endereço para a pasta contendo a sequência de imagens geradas e `json/video.json` deve ser o caminho para o arquivo `JSON` de saída.

Passada por essas duas etapas teremos transformado nosso vídeo em um arquivo `JSON` que será processado pela biblioteca.

#### Por Dentro do Frame Player

O código do Frame Player é todo escrito em JavaScript puro utilizando o paradigma de orientação a objetos baseado em protótipo, sem uso de nenhuma depêndencia. Desenvolver esta biblioteca usando orientação a objetos foi uma decisão primordial para viabilzar a capacidade de possuir multiplas instâncias do player em uma mesma página.

Para utilizar a biblioteca em uma página, é necessário carregar dois arquivos referêntes ao código JavaScript e a folha de estilo do player:

<pre class="lang-html">&#060;link rel="stylesheet" href="src/css/frameplayer.css"&#062;
    &#060;script src="src/js/frameplayer.js"&#062;
</pre>

A primeira versão da biblioteca não contava com o arquivo CSS adicional, porém a possibilidade de carregar a folha de estilo em um arquivo separado permite ao utilizador ir além e personalizar qualquer elemento do player e ainda desacoplar o código CSS do JavaScript.

Com os arquivos carregados, é necessário definir em seu código HTML o elemento que irá representar o player:

<pre class="lang-html">&#060;div id="my-player" class="frameplayer" data-vidsrc="videos/video.json"&#062;
</pre>

A classe `frameplayer` é responsável por definir o estilo ao player, o `id` pode ser qualquer nome definido pelo utilizador e o atributo `data-vidsrc` deverá receber como valor o camaminho para o arquivo JSON gerado previamente.

O player possui uma barra de controle do vídeo onde é inserido os botões de ação como play e pause. Essa barra é opcional ao utilizador, podendo ser desabilitada facilmente pelo parâmetro de opções. A contrução da barra de controle é feita por um método especifico da biblioteca (`FramePlayer.prototype.createControlsBar`), em caso de desabilitado pelo utilizador a barra não é construida, evitando assim criar código de marcação que não será utilizado.

A biblioteca possui dois parâmetros, o primeiro é o `id` do elemento `div` definido na marcação que será responsável por armazenar o player. Já o segundo parâmetro é referente as opções do player, esse parâmetro é um objeto JavaScript que possui a seguinte estrutura:

<pre class="lang-javascript">var options = ({
        'rate': 30,
        'controls': false,
        'autoplay': true,
        'width': '640px',
        'height': '390px',
        'radius': '50%'
    });
</pre>

Abaixo constam as informaçõe de cada atributo do parâmetro de opções:

  * `rate`: valor da taxa de velocidade de reprodução. O valor padrão é 20.
  * `controls`: habilita ou desabilita a barra de controles. O valor padrão é true.
  * `autoplay`: permite a execução automática do vídeo após ser carregada a página. Seu valor padrão é false.
  * `width`: valor referente a largura do player em pixel. O valor padrão é 480px.
  * `height`: valor referente a altura do player em pixel. O valor padrão é 320px.
  * `radius`: valor referente a borda arredondada do player. O valor padrão é null, portanto, sem bordas arredondadas por padrão.

Após ser definida as opções, o utilizador deverá instanciar o Frame Player da seguinte forma:

<pre class="lang-javascript">var player = new FramePlayer('my-player', options);
        player.play();
</pre>

Deve-se chamar o método construtor do Frame Player passando como parâmetro o `id` do elemento e a variável com as opções. Após isso basta chamar o método play para executá-lo.

#### O Método Play

O método play `(FramePlayer.prototype.play)` pode ser considerado o coração do Frame Player, pois ele é o responsável pela troca em sequência das imagens, levando em consideração a taxa de velocidade. A primeira ação deste método é carregar o arquivo JSON, quando é terminado o carregamento, executa-se o trecho código abaixo, que faz com que os frames sejam trocados.

<pre class="lang-javascript">setInterval(function() {
        if(!player.paused){
            i++;
            if (i &gt;= jsonVideoFile.frames.length) {
                i = 0;
            }
            img.src = jsonVideoFile.frames[i];
        }
    }, Math.round(1000 / player.rate));
</pre>

Acima podemos observar que a cada intervalo define-se um novo valor para o atributo `src` do elemento imagem, este novo valor refere-se a ao próximo frame do vídeo. Dessa forma, conforme muda-se o valor de tempo do intervalo a velocidade da troca de imagens é afetada.

#### Base64 vs Image File

Uma grande questão surgiu após o lançamento da biblioteca: o uso de imagens codificadas em Base46 ser lento, pois o browser tem o trabalho de decodificar essa string, e por ser tratar de muitas imagens, este trabalho ficaria pesado em dispositivos móveis. Para saber mais sobre este fato tivemos um <a href="http://www.mobify.com/blog/data-uris-are-slow-on-mobile" target="_blank">bom artigo como referência</a>.
  
Com essa questão levantada, foi desenvolvida uma versão utilizando os arquivos de imagens em vez de Base64 URI, e a melhora do desempenho foi significativa.
  
Você pode conferir mais sobre isso nesta <a href="https://github.com/vagnervjs/frame-player/issues/4" target="_blank">issue</a>. A versão baseada em arquivos de imagens está disponivel em uma <a href="https://github.com/vagnervjs/frame-player/tree/img-tag" target="_blank">branch especifica</a>.

### Conclusão

Em nenhum momento o objetivo do desenvolvimento desta biblioteca foi eliminar o uso da tag `video` em dispositivos móveis, muito pelo contrário, quando é necessário carregar arquivos de video com objetivo de apresentação da media apenas, é extremamente recomendável o uso dessa tag específica para isso. O real objetivo da bibliteca é criar uma alternativa para carregar animações em video quando é necessário integração com o restante da página, viabilizando múltiplos carregamento e personalização.

A biblioteca Frame Player encontra-se em uma versão estável para uso em dispositivos móveis e mostra-se como uma boa solução para videos curtos, o maior ponto positivo é a liberdade que o desenvolvedor ganha para tornar a página dinâmica com o uso de videos nos dispositivos móveis, podendo desviar do player nativo da plataforma, e sem a dependencia do usuário dar o play para reproduzir o vídeo, o player conta ainda com um método específico para inserir filtros (grayscale, sepia, invert) nas imagens do vídeo.
  
Existem ainda alguns trabalhos futuros para o Frame Player como buffer, compressão de imagens baseando-se em keyframes e até mesmo aúdio. 

Confira o <a href="http://vagnervjs.github.io/frame-player" target="_blank">site</a> do Frame Player e seu <a href="https://github.com/vagnervjs/frame-player" target="_blank">repositório no Github</a>.

### Referências:

  * <a target="_blank" href="http://www.w3.org/TR/html-markup/video.html#video-attributes">HTML Video Element specification</a>
  * <a target="_blank" href="https://developer.apple.com/library/safari/documentation/AudioVideo/Conceptual/Using_HTML5_Audio_Video/Device-SpecificConsiderations/Device-SpecificConsiderations.html">Safari HTML5 Audio and Video Guide</a>
  * <a target="_blank" href="http://blog.millermedeiros.com/unsolved-html5-video-issues-on-ios/">Unsolved HTML5 video issues on iOS</a>