---
title: Entendendo os componentes funcionais
authors: Tailo Mateus Gonsalves
type: post
image: https://cdn-images-1.medium.com/max/1600/1*vHHBwcUFUaHWXntSnqKdCA.png
date: 2019-01-02
excerpt: Vamos entender qual componente utilizar.
tags:
  - Componentes funcionais
  - Componentes de classes
categories:
  - ReactJS
  - Front-end
  - JavaScript
---

### Introdução

<br> 

Os componentes são blocos de códigos e eles desempenham o papel fundamental em tornar o [React](https://reactjs.org/) modular. Ao utilizar o tipo correto de componente, estamos tentando garantir que nossa aplicação se torne reutilizável e escalável. Atualmente existem dois tipos de componentes, entre eles, os componentes funcionais e os baseados em classes. 

Vamos ver algumas diferenças entre as duas formas, e quando é o melhor momento para usar um ou outro.

Robert Martin, em Clean Code:

> “The ratio of time spent reading versus writing (code) is well over 10 to 1 … making it easy to read makes it easier to write.”

### Quais são os componentes funcionais?

<br> 

Vamos criar um componente apenas retornando uma mensagem, o famoso “Hello world”. Vamos utilizar a sintaxe do ES6+.

```
const helloWorld = () => { 
  return "Hello World" 
}
export default helloWorld
```

Esse código simples, pode ser compreendido por qualquer desenvolvedor Javascript, aqui não possui nada de React, apenas Javascript. Temos a definição da função e no final exportamos ela como padrão. Isso é tudo que precisamos para criar o nosso primeiro componente funcional. 

Embora isso seja um componente React, na maioria das situações acabamos retornando [JSX](https://reactjs.org/docs/introducing-jsx.html), com base no que recebemos por parâmetro. Dessa forma, criamos componentes reutilizáveis. A
partir disso, vamos alterar nosso componente para quando receber uma entrada, gerar uma saída [JSX](https://reactjs.org/docs/introducing-jsx.html).

```
import React from "react"
const helloWorld = props => {
  return (
    <div>
      <p><b>{props.name}</b> Hello World</p>
    </div>
  )
}
export default helloWorld
```

Agora podemos  utilizar nosso componente dentro do React, passando nossa props da seguinte maneira: 

```
import React, { Component } from "react"
import helloWorld from "./helloWorld"
class App extends Component {
  render() {
    return (
      <helloWorld name="Testing"/>
    )
  }
}
export default App
```

### Vantagens de componentes funcionais

<br> 

* Ajudam a manter o código simples, legível e reutilizável;

* Desempenho, como não possui nenhum método de estado ou de ciclo de vida, não é necessário alocar memória;

* Como são funções mais puras, é mais fácil para testar.

Então sempre devo criar componentes funcionais? Isso vai depender de cada caso. Mas, eles são sempre um ponto de partida para criar componentes. Na próxima parte vamos observar quando usamos componentes baseados em classes.

### Componentes baseados em classes

<br> 

Basicamente é uma classe que estende de React.Component. Para você entender melhor como funciona, veremos nosso mesmo código acima, mas em forma de componente em classe: 


```
import React, { Component } from "react"
class helloWorld extends Component {
  render() {
    return (
      <div>
        <p><b>{this.props.name}</b> Hello World</p>
      </div>
    )
  }
}
export default helloWorld
```

Em alguns casos você precisara acompanhar o estado do seu componente ou criar outras funções, por exemplo, para saber se clicou em algum botão, ou fazer alguma ação e salvar o estado. Nesse caso, componentes em classes é uma opção melhor. Geralmente, sempre começa criando componentes funcionais, e com a necessidade podemos refatorar para classes.

Além disso, esses componentes possuem algumas funções de ciclo de vida, tais como componentDidMount(). Após a tela ser renderizada essa função é chamada. Podemos utiliza-lá consultando uma API. Sempre podemos e devemos separar nossa
regra de negócio da nossa apresentação, criando outras funções, além da render().

### Resumo

<br> 

* Inicie com componentes funcionais e quando sentir a necessidade, altere para componentes baseados em classes;

* Componentes funcionais mantém o código mais simples e reutilizável;

* Componentes funcionais são mais fáceis de testar;

* Quando usar o estado, use componentes de classe;

* Ao usar o estado do componente, isso tornará ele mais lento. Use o componente adequado para o problema que quiser solucionar.

### Leia mais

<br> 

[React Stateless Functional Components: Nine Wins You Might Have Overlooked](https://hackernoon.com/react-stateless-functional-components-nine-wins-you-might-have-overlooked-997b0d933dbc)

[Stateless Component vs Pure Component](https://medium.com/groww-engineering/stateless-component-vs-pure-component-d2af88a1200b)

[Understanding Functional Components](https://hackernoon.com/understanding-functional-components-895321b1af84)

[React Functional or Class Components: Everything you need to know](https://programmingwithmosh.com/react/react-functional-components/)

[Components and Props](https://reactjs.org/docs/components-and-props.html)<br>
<br> 


