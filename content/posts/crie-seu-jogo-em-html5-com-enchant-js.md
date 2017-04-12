---
title: Crie seu jogo em HTML5 com enchant.js
author: Ezequiel M. Mello
type: post
date: 2015-07-28
excerpt: Com poucas linhas de código é possível criar um jogo simples em HTML5 utilizando o framework enchant.js.
url: /crie-seu-jogo-em-html5-com-enchant-js/
categories:
  - Código
  - HTML5
  - JavaScript
  - Técnicas e Práticas
tags:
  - enchant.js
  - html5
  - JavaScript
  - jogos

---
Mantido na UEI (Ubiquitous Entertainment, Inc), por membros do Centro de Pesquisa de Akihabara, o _framework_ japonês chamado **<a href="http://enchantjs.com/pt-br/" target="_blank">enchant.js</a>**, permite criar com poucas linhas de código um jogo simples em HTML5.

Com **enchant.js**, você pode criar desde simples jogos 2D até avançados jogos em três dimensões, graças ao suporte WebGL usado como plugin.

Os elementos criados em um bloco do enchant.js são renderizado através do DOM e do Canvas, além de rodar nas plataformas mais conhecidas. Os eventos são voltados para _mobile_, como o **Event.TOUCH_MOVE**, disparado quando o usuário toca na tela e a segura. O enchant.js ainda possui uma <a href="http://code.9leap.net/" target="_blank">plataforma</a> com bibliotecas e jogos prontos para serem usados quando quiser.

## _Sprites_

O enchant.js trabalha com _sprites_ para renderizar objetos na tela. Esse recurso tem várias utilidades, como criar um personagem ou mesmo um ambiente. O _sprite_ permite além de renderizar um objeto no DOM ou no Canvas, criar animações com frames a partir de uma imagem _sprite_. Cada quadro é definido como um índice em um _array_, iniciado com zero, e com limite máximo da quantidade de imagens. Exemplo:

<pre>var Person = new Sprite(64, 64);
Person.image = game.assets['images/Person.png'];
Person.frame = [0, 1, 4, 5, 1]; // linha importante</pre>

Isto fará que a imagem passe entre estes sprites em um intervalo de tempo determinado pela propriedade **fps** do objeto **Core** (versões mais recentes), e **Game** (versões anteriores).

## O código

Vamos criar um personagem movendo-se em um ambiente usando _sprite_.

### **HTML:**

<pre>&lt;!DOCTYPE html&gt;
&lt;html&gt;

 &lt;head&gt;
 &lt;script src="enchant.js"&gt;&lt;/script&gt;
 &lt;script src="script.js"&gt;&lt;/script&gt;
 &lt;/head&gt;

 &lt;body&gt;&lt;/body&gt;

&lt;/html&gt;</pre>

### **JavaScript**:

<pre>(function() {
   function initialize() {
     enchant();
     var game = new Core(640, 480);
     var gohan = "http://tinyurl.com/p2z8qlt";
     var fundo = "http://tinyurl.com/nc39d4y";
     game.preload(gohan, fundo);
     game.fps = 16; // seta o fps. Quanto maior, mais lento
 
     game.onload = function() {
       // cria fundo
       var background = new Sprite(1024, 698);
       background.image = game.assets[fundo];
      game.rootScene.addChild(background);
 
      // cria player
     var player = new Sprite(63, 97);
     player.image = game.assets[gohan];
     player.frame = [0, 1];
     player.x = (game.width/2)-(player.width/2); // centraliza no eixo X
     player.y = 250;
    player.tl.scaleTo(1.5, 1.5, 50);
    game.rootScene.addChild(player);
 
    // executa o tempo todo enquanto o player existir
    player.onenterframe = function() {
      if (this.age &gt;= 50) this.frame = [2, 3, 4];
      if (this.age % 10 == 0) 
        this.tl.moveBy(50,0,10).moveBy(-50,0,10).loop();
     }
   }
   game.start(); // inicia o jogo
 }
  window.addEventListener('load', initialize, false);
}).apply(this);
</pre>

**<a href="http://plnkr.co/edit/dCxps2" target="_blank">Veja o exemplo no Plunker</a>**.

Primeiro chamamos o enchant.js na linha **3**. Na linha **4** criamos uma variável para guardar o objeto principal do jogo. Na linha **7**, dizemos ao enchant.js o que precisamos carregar antes de iniciar o jogo. Na linha **8** setamos os _frames per second_ do jogo (esta propriedade existe em todos os objetos do enchant.js). Na linha **10** definimos o que acontece quando o enchant.js terminar de carregar os _assets_. Na linha **12** criamos um novo sprite com largura e altura passadas como argumento. Na linha **13**, atribuímos a imagem de fundo, que já foi carregada à propriedade _image_ do _sprite background_. Na linha **14**, adicionamos esse fundo à cena principal (game.rootScene). Na linha **19**, criamos uma animação passando as imagens 0 e 1 do sprite. Na linha **22**, há o efeito de escala, como no CSS _(transform: scale(x, y))_, mas com a diferença do terceiro argumento que define o tempo (quanto maior, mais demorado). Na linha **29**, obtêm-se o efeito de mover em uma determinada direção em X e Y, definindo como terceiro argumento um tempo. O _loop()_ serve para repetir infinitamente a ação atual.

## Adicionando um novo personagem

Que tal deixar nosso jogo mais emocionante e adicionar um inimigo para combater nosso protagonista?

<pre>(function() {
   function initialize() {
   enchant();

   var game = new Core(640, 480)
   , gohan = "http://tinyurl.com/p2z8qlt"
   , fundo = "http://tinyurl.com/nc39d4y"
   , freeza = "http://tinyurl.com/parueup"
   , powerImage = "http://tinyurl.com/o734vyr";
   game.preload(gohan, fundo, freeza, powerImage);
   game.fps = 16;
 
   game.onload = function() {
 
     var scene = new Scene(); // cria nova cena
     game.pushScene(scene); // nova cena na principal
 
     // adiciona o fundo
     var background = new Sprite(1024, 698);
     background.image = game.assets[fundo];
     scene.addChild(background);
 
     // modelo de player
    var Player = Class.create(Sprite, {
        initialize: function(data) {
          Sprite.apply(this, [data.w, data.h]);
          this.image = game.assets[data.image];
          data.scene.addChild(this);
      }
    });
 
    var Power = Class.create(Sprite, {
      initialize: function(w, h, image, scene) {
        Sprite.call(this, w, h);
        this.image = game.assets[image];
        scene.addChild(this);
      }
    });
 

    // Gohan
    var player = new Player({
    w: 63, h: 97, scene: scene, image: gohan
    });
 
    player.frame = [0, 1];
    player.x = ((game.width/2)-(player.width/2))-200;
    player.y = 250;
    player.tl.scaleTo(1.5, 1.5, 50);
 
   player.onenterframe = function() {
     if (this.age &gt;= 50) this.frame = [2, 3, 4];
     if (this.age % 10 == 0) 
    this.tl.moveBy(50,0,10).moveBy(-50,0,10).loop();
   }
 
   player.addEventListener(Event.TOUCH_START,function(evt){
     var power = new Power(133, 61, powerImage, scene);
     power.x = evt.x;
     power.y = evt.y;

     power.addEventListener('enterframe', function() {
       this.x += 2;
       if (this.intersect(enemy)) {
         scene.removeChild(enemy);
         player.frame = 0;
       }
     });
   });
 
   // Freeza
   var enemy = new Player({
     scene: scene, w: 65, h: 85, image: freeza
   });
 
   enemy.x = 400;;
   enemy.y = 180;
   enemy.tl.scaleTo(-1, 1, 1);
   enemy.tl.scaleTo(-3,3, 100);
 
   enemy.onenterframe = function() {
     if (this.age &gt;= 50) this.frame = [2, 3, 4];
     if (this.age%10==0) this.tl.moveBy(0,-50,10).moveBy(0,50,10).loop();
   }

 }
 game.start();
}

 window.addEventListener('load', initialize, false);
}).apply(this);
</pre>

**<a href="http://plnkr.co/edit/7F6ytf" target="_blank">Veja o exemplo com dois personagens no Plunker</a>**.

Neste segundo exemplo, temos funções novas:

### Class.create()

Este método recebe dois argumentos (classe e objeto). O objeto utiliza a propriedade _initialize_ para executar o objeto quando é criado como um construtor. Outras propriedades funcionam como eventos:

<pre>Class.create(Class,{initialize:function(){},onenterframe:function(){}});</pre>

Dentro do _initialize_, precisamos chamar a classe com _call_ ou _apply_ e seguir o mesmo padrão do exemplo 1 ao criar um objeto.

### intersect()

Esta função facilita a nossa vida, detectando uma colisão. Só é preciso usar este método em um objeto e passar ao outro como argumento. Exemplo:

<pre>player.intersect(enemy); // true ou false</pre>

Isto nos poupa de fazer uma lógica como esta:

<pre>function intersect(t, other) {
  return t.x &lt; other.x + other.width
    && other.x &lt; t.x + t.width 
    && t.y &lt; other.y + other.height 
    && other.y &lt; t.y + t.height;
}
</pre>

<pre>intersect(player, enemy); // true ou false</pre>

Apesar deste ser um exemplo simples de como criar um jogo em HTML5, a <a href="http://enchantjs.com/resource/api-documentation/" target="_blank">documentação</a> do enchant.js é bastante completa, e tem muita coisa que permite ser incorporada para tornar nosso exemplo mais dinâmico e interativo.

Confira mais <a href="http://enchantjs.com/pt-br/" target="_blank">demos</a> no site, os <a href="http://enchantjs.com/tutorial/lets-start-with-enchant-js/" target="_blank">tutoriais</a> e os <a href="http://enchantjs.com/showcase/games-on-9leap-net/" target="_blank">jogos já desenvolvidos</a> com a plataforma.