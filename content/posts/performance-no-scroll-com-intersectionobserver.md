---
title: Performance no scroll com IntersectionObserver
authors: Morais Junior
type: post
date: 2019-04-18
excerpt: Temos várias técnicas para tratar da performance na rolagem de uma página web, porém muito pouco se fala do IntersectionObserver, neste artigo iremos conhecer melhor essa implementação e os benefícios que ela traz :)
categories:
  - Front-end
  - Técnicas e Práticas
  - Javascript
tags:
  - web performance

---
# Conhecendo o IntersectionObserver

Temos várias técnicas para tratar da performance na rolagem de uma página web, porém muito pouco se fala do IntersectionObserver, neste artigo iremos conhecer melhor essa implementação e os benefícios que ela traz :)

É comum no javascript a necessidade de implementarmos o evento*“scroll”* porém poucos fazem isso de forma correta, esse é um evento muito delicado, é chamado em cada alteração de pixel, então se você precisa verificar se um objeto está visível na tela e decidir utilizar um *addEventListener(“scroll”, func)* é quase certo que terá um caso de [layout trasting](https://tableless.com.br/repaint-reflow-layout-thrashing-performance-alem-do-carregamento/).

Para evitar constantes leituras na [Dom Tree](https://javascript.info/dom-nodes), foi criado o **IntersectionObserver**, a implementação do mesmo é bem simples, basta criar uma instância de um Observer, e depois atribuir elementos ao observador, abaixo descrevo um exemplo de sua utilização:

```javascript
       var observador = new IntersectionObserver(function(entries) {
            entries.forEach(function (entry) { //loop em todos os elementos atingidos
                const {isIntersecting, intersectionRatio} = entry;
                if (isIntersecting === true || intersectionRatio > 0) {
                   console.log( entry.target );
					         // entry.boundingClientRect 
					         // entry.intersectionRatio
 					         // entry.intersectionRect 
					         // entry.isIntersecting
 					         // entry.rootBounds 
					         // entry.time
                   observador.unobserve(entry.target); // se você só precisar do event uma vez utilize essa linha
                }
            });
        }, {
			rootMargin: '400px'
		});

  //iniciando o opservador para #myDiv
  observador.observe(  document.querySelector(‘#myDiv’)  );

```

No exemplo acima sempre que o elemento com o ID myDiv, chegar próximo de 400px da viewport ele irá aparecer no console.

Alguns atributos podem ser passados para o Observador, são eles:
**root: **
Elemento inicial para observação, ele irá buscar os objetos filhos de root, esse é um atributo muito importante, quanto mais abaixo o elemento estiver na Render Tree menor o uso de memória e consumo de CPU
**rootMargin: **
Margem de segurança para o observador, se sua tela tem 500px, e vc define uma margem de 100px, o observador vai considerar a área de visão como tendo 600px.
**threshold:**
Indica em qual porcentagem da visibilidade do alvo o retorno de chamada do observador deve ser executado. Se você quiser apenas detectar quando a visibilidade ultrapassar a marca de 50%, você poderá usar um valor de 0,5.

## Deixando de observar
```javascript
observador.unobserve(element);
```
## Desligando o observador
```javascript
observador.disconnect();
```

# Conclusão
O momento do scroll é um dos mais delicados em um produto Web, nele o cliente nos mostra que quer mais do produto, portanto todo cuidado nesse momento é pouco, leia com cuidado a [documentação](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) e evite uma quantidade excessiva de manipulações ou leituras no DOM. 
