---
title: Angular vs ReactJS - A web sempre ganhando
authors: Manacés Pereira
type: post
image: https://cdn-images-1.medium.com/max/800/1*bWFv50r2E3L1I1OQdP01sg.png
date: 2018-07-28 03:00:00 +0000
excerpt: Uma breve comparação entre Angular e ReactJS.
categories:
- JavaScript
- Opinião
publishdate: 2018-07-28 03:00:00 +0000
tags:
- reactjs
- angularjs

---
Eu vejo muita gente que discute sobre qual tecnologia é melhor em detrimento de outra. Não é diferente quando falamos sobre Angular e ReactJS.

Neste artigo, a intenção não é dizer para você qual é a melhor tecnologia, mas fazer você tirar suas próprias conclusões. Nada que está neste artigo, é na base da minha opinião ou na base do achismo. Vou colocar todas as fontes necessárias para uma credibilidade maior.

### Framework vs Library

Para entendermos a real diferença entre o **Angular** e o **ReactJS**, temos que entender antes o que é um Framework e um que é uma Library.

Segundo [um artigo de 2010 do site Wired](https://www.wired.com/2010/02/get_started_with_web_frameworks/#What_is_a_Web_Framework.3F), framework ou software framework é um conjunto de ferramentas que torna o desenvolvimento mais fácil, sem termos que re-inventar a roda. Ele tem o objetivo de ditar como sua aplicação será desenvolvida.

Já uma library, é um conjunto de classes e definições que resolvem um determinado problema. Tem um foco específico e um conjunto delas compõem um framework, com base no que escrevi acima.

Tendo essas duas definições em mente, podemos separar o **Angular** e o **ReactJS** como um framework e uma library javascript respectivamente.

## Uma breve compração

### ReactJS

**O que é:** Como diz no próprio site — A JavaScript library for building user interfaces — é uma library do javascript, criada para desenvolvermos interfaces de usuário.

**Vantagem:** A principal diferença e vantagem do **RectJS** em relação ao **Angular** é chamada de *Virtual DOM* ou *VDOM,* que é um conceito de programação onde existe uma representação da UI *cacheada* em memória, sincronizada com o *DOM* real do browser, com a utilização do *ReactDOM*. Desse modo, as alterações de DOM são muito mais rápidas, já que temos todo o *cache* e o **ReactJS** se vira para sincronizar e atualizar o nosso DOM real, mudando apenas o que é necessário.

Veja um exemplo:

![](https://cdn-images-1.medium.com/max/2000/1*wVhhftfMDqyPWDMOSeSCJA.gif)

Com o *VDOM,* o **ReactJS** atualiza apenas o que é realmente necessário, neste caso, atualiza apenas o texto do horário, mesmo que todo resto esteja fazendo parte do elemento *h2* do HTML5.

### Angular

**O que é: Angular,** diferente do **ReactJS**, é um framework responsável por tornar o desenvolvimento de uma aplicação web mais fácil. Por ser um framework e não uma lib, por padrão ele já nos disponibiliza templates declarativos, injeção de dependência, integra as boas práticas; e por isso ele dita a forma que devemos desenvolver nossas aplicações, com uma arquitetura pré estabelecida e assim diminui as chances de cometermos erros bobos.

Arquitetura do **Angular:**

![](https://cdn-images-1.medium.com/max/2000/0*xXHHsuEobZdO3DRk.png)

Neste modelo, a camada de *Component* e *Template* têm a responsabilidade de definir nossa *view*. Um *decorator* em nosso *Component* define nosso *metadata,* onde vamos associar qual *Template* faz parte do *Component* e outras configurações. Também temos as diretivas, na camada *Directive,* que tem a função de modificar nossa *view*, baseado nos dados e lógica que vamos utilizar.

Ainda falando sobre este padrão arquitetural do **Angular,** temos também o *Injector,* responsável por prover nossos serviços em um *Component.*

Você pode ver mais detalhes da arquitetura do **Angular** [neste link](https://angular.io/guide/architecture).

**Vantagem:** A vantagem em relação ao **ReactJS,** é que, por ser um framework, o angular disponibiliza features nativas, onde não precisamos nos preocupar com rotas, injeção de dependências, requisições http, uma linha de comando muito rica onde criamos rapidamente uma aplicação do **Angular** totalmente estruturada e pronta para iniciar nosso desenvolvimento, suporte a PWA’s, testes com *Karma* integrados no framework e configurados, animações, e a partir da versão 6, também possui o *Angular Material* já integrado. Dessa forma, quando desenvolvemos uma aplicação mais robusta, se usarmos as boas práticas do framework, teremos uma aplicação escalável, clean e bem desenvolvida.

## Curva de aprendizado

### ReactJS

Tem o desenvolvimento com o ES6, ou ECMAScript 6, utilizando o JSX. Assim o **ReactJS** se responsabiliza por renderizar todo o DOM usando o conceito de *Virtual DOM,* que já falei anteriormente. Sendo assim, para quem já conhece o ES6, é mais fácil começar com o **ReactJS** do que com o **Angular.**

### Angular

Baseado em TypeScript - *javascript com super poderes* -, o framework é complexo para quem nunca utilizou recursos de orientação a objetos e tipagem de dados. Assim, a curva de aprendizado é um pouco mais longa para quem vem apenas do JavaScript.

## Qual escolher?

Segundo John Papa - *e eu concordo com todas as palavras* - [a web está ganhando com ambos](https://twitter.com/john_papa/status/922140900914089984).

Não existe um melhor que o outro, eles tem propósitos diferentes.

Se você precisar de bastante performance, o ideal é usar o **ReacJS.** Não que o **Angular** seja uma péssima ideia quando falamos de performance, mas sim pelo **ReactJS** de fato entregar um resultado mais performático. Porém precisa ter bastante cuidado com o código e muita atenção, pois você é quem vai ditar as próprias regras.

Mas se você vai desenvolver uma aplicação bem robusta, com muita lógica no front-end e mais pro lado empresarial, o ideal é usar o **Angular.** Ele vai ditar a forma como será desenvolvida a aplicação e podemos usar todos os recursos e boas práticas que ele nos disponibiliza, para podermos ter um código mais organizado e suscetível à menos falha.

Também tem que ser levado em consideração a curva de aprendizado da equipe que vai trabalhar no projeto, pois isso é o que mais influencia no resultado. Não adianta uma equipe conhecer o ES6 e nunca ter trabalhado com o paradigma de orientação a objetos e querer utilizar o **Angular** com o Typescript. O ideal seria usar o **ReactJS.**

## Referências

https://twitter.com/john_papa/status/922140900914089984  
[https://reactjs.org/docs/faq-internals.html](https://reactjs.org/docs/faq-internals.html)  
[https://angular.io/features](https://angular.io/features)  

## Social

[https://www.linkedin.com/in/manacesneto/](https://www.linkedin.com/in/manacesneto/)  
[https://github.com/manacespereira](https://github.com/manacespereira)  
[https://twitter.com/manacespereira](https://twitter.com/manacespereira)  
contato@manacespereira.com.br