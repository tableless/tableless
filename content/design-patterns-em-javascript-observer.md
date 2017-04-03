---
title: Design Patterns em JavaScript – Observer
author: Bruno Ruiz
type: post
date: 2014-09-19
excerpt: Entenda um pouco mais sobre o pattern JavaScript Observer.
url: /design-patterns-em-javascript-observer/
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - JavaScript
  - pattern

---
## O que é Design Patterns?

Desenvolver um software é se deparar constantemente com problemas. Esses problemas surgem em diversas situações e em grande quantidade. Em termos simples: nos deparamos várias vezes com um mesmo problema em diversas situações em momentos diferentes no mesmo projeto.

Se os problemas são sempre os mesmos as soluções se repetem. Mas é muito comum darmos as mesmos soluções aos mesmos problemas de formas diferentes; isto porque não padronizamos soluções para problemas que sempre estamos resolvendo.

> Padronizar soluções é a melhor forma de resolver problemas durante o desenvolvimento de softwares.

Em linguagens orientadas a objetos temos a disposição uma série de padrões que auxiliar na criação de objetos, na forma como eles se relacionam e nos comportamentos que eles podem adotar. Em JavaScript não é diferente. Nós podemos implementar padrões com o objetivos de auxiliar o processo de desenvolvimentos nestes aspectos.

Vamos falar um pouco sobre um padrão de estrutura JavaScript chamada Observer.

## O que é o Design Pattern Observer?

Um Observer é um padrão que possibilita a um objeto observar o estado de outro objeto, sendo notificado quando ele muda de estado. Portando, existem dois papéis neste padrão de desenvolvimento: o observador e o observado. No entanto, esta relação pode ter múltiplos objetos observadores e múltiplos observados. Uma característica deste padrão, que o torna poderoso, é o **acoplamento fraco**; o objeto observado e o observador podem ter seu acoplamento desfeito em tempo de execução a qualquer momento.

## Implementando o Design Pattern Observer?

Vamos à pratica do padrão! Nós criaremos um objeto que será responsável por gerenciar o relacionamento entre os objetos observados e observadores.

<pre class="lang-javascript">var observador</pre>

O objeto `observador` terá quatro métodos: o primeiro método é responsável pela assinatura dos objetos observadores à objetos observados. Estes são adicionados a uma lista de objetos inscritos, conforme podemos ver abaixo:

<pre class="lang-javascript">observador = {
    adicionaInscricao: function(callback){
                 this.inscritos[this.inscritos.length] = callback;
               }
   }
</pre>

O segundo método remove a inscrição de objeto na estrutura de um observer. Esta  possibilidade torna possível, não somente a adição, mas também a remoção de uma inscrição em tempo de execução.

<pre class="lang-javascript">observador = {
    adicionaInscricao: function(callback){
                 this.inscritos[this.inscritos.length] = callback;
               },
   removeInscricao: function(callback){
                 for (var i = 0; i &lt; this.inscritos.length; i++) {
                     if (this.inscritos[i] === callback) {
                          delete(this.inscritos[i]);
                        }
                   }
              }
        }
</pre>

Devemos ter uma forma pela qual a execução dos métodos dos objetos observados possam passar pelo observador. Somente assim os objetos inscritos poderão ser avisados da execução para a qual eles estão inscritos.

<pre class="lang-javascript">observador = {
    adicionaInscricao: function(callback){
                 this.inscritos[this.inscritos.length] = callback;
               },
   removeInscricao: function(callback){
                 for (var i = 0; i &lt; this.inscritos.length; i++) {
                     if (this.inscritos[i] === callback) {
                          delete(this.inscritos[i]);
                        }
                   }
              },

    publica:function (oque) {
              for (var i = 0; i &lt; this.inscritos.length; i++) {
                            if (typeof this.inscritos[i] === 'function') {
                                            this.inscriots[i](oque);
                             }
                        }
                 }
          }</pre>

Fazer de um objeto um observado deve  ser uma atribuição da estrutura do  nosso observador. Para isto temos o método fazObservado abaixo.

<pre class="lang-javascript">observador = {
    adicionaInscricao: function(callback){
                 this.inscritos[this.inscritos.length] = callback;
               },
   removeInscricao: function(callback){
                 for (var i = 0; i &lt; this.inscritos.length; i++) {
                     if (this.inscritos[i] === callback) {
                          delete(this.inscritos[i]);
                        }
                   }
              },

    publica:function (oque) {
              for (var i = 0; i &lt; this.inscritos.length; i++) {
                            if (typeof this.inscritos[i] === 'function') {
                                            this.inscritos[i](oque);
                             }
                        }
                 },
   fazObservado:function (o) { 
              for (var i in this) {
                  o[i] = this[i];
                  o.inscritos= [];
               }
            }
    };</pre>

## Como usar o Design Pattern Observer?

Ter a estrutura de observer disponibilizada em seu projeto possiblita uma orgnanização em todas as estapdas do desenvolvimento. Para termos uma idéia disto vejamos como utilizar a estrutura do observer.

<pre class="lang-javascript">var observado = {
	    executa:function(){
	         var conteudo = 'Executado em: ' + new Date();
                 this.publica(conteudo);
          }
   };

   observador.fazObservado(observado);

var observaObservado = {
      verifica:function(oque){
		   console.log("Observou "+oque)
           }
     };

    observado.adicionaInscricao(observaObservado.verifica);
    observado.executa();
</pre>

Sempre que implementamos um padrão de desenvolvimento, ganhamos produtividade, agilidade e organização. Portanto, implemente padrões e seja feliz!