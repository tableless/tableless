---
title: 'Utilizando Fragment no React'
authors: Raphael Guastaferro
type: post
image: https://cdn-images-1.medium.com/max/800/1*y6C4nSvy2Woe0m7bWEn4BA.png
date: 2017-12-15
excerpt: 'Uma das mais notáveis breaking changes do React foi a versão 16, a chamada React Fiber, que inclui o React.Fragment.'
categories:
  - javascript
tags:
  - reactjs
  - javascript
  - Na prática
---

Uma das mais notáveis *breaking changes* do React foi a versão 16, a chamada
[React Fiber](https://reactjs.org/blog/2017/09/26/react-v16.0.html), em que todo
o *core* da aplicação foi reescrito. Além da adição de
[Portals](https://reactjs.org/blog/2017/09/26/react-v16.0.html#portals),
[componentDidCatch](https://reactjs.org/blog/2017/07/26/error-handling-in-react-16.html),
melhorias no [Server
Rendering](https://reactjs.org/blog/2017/09/26/react-v16.0.html#better-server-side-rendering)*
*e mais…

Depois desse grande anúncio, não eram esperadas mudanças significativas nas
próximas versões… Até que nos deparamos com o novo
[React.Fragment](https://reactjs.org/blog/2017/11/28/react-v16.2.0-fragment-support.html).

Se você já desenvolveu aplicações React para o mundo real (Além do ToDoList),
com certeza já se frustrou tentando renderizar vários elementos de uma vez:

    render() {
      return (
        <h1>App React</h1>
        <h2>Vamos começar!</h2>
      )
    }


Ou apenas um array direto:

    render() {
      return [
        <h1>App React</h1>
        <h2>Vamos começar!</h2>
      ]
    }


Pra isso, era necessário encapsular os elementos em uma tag:

    render() {
      return <div>
        <h1>App React</h1>
        <h2>Vamos começar!</h2>
      </div>
    }


Ok, essa *div *não serve pra nada, mas o problema foi resolvido.

E se você deseja separar apenas alguns itens de uma lista dentro de um
componente, para renderizá-los dentro de uma UL? Encapsular com uma div vai
quebrar sua aplicação (ul>div>li??)…

Então, no [React
16](https://reactjs.org/blog/2017/09/26/react-v16.0.html#new-render-return-types-fragments-and-strings)
foi implementado uma nova possibilidade de *render*, onde é permitido retornar
um array diretamente, a única exigência é colocar o atributo key nos elementos
do array:

    render() {
      return [
        <h1 key="1">App React</h1>
        <h2 key="2">Vamos começar!</h2>
      ]
    }

É preciso lembrar de colocar atributos key nos elementos que estão dentro de um
array, mas ok. Problema resolvido novamente.

Essas soluções funcionam, mas são um incômodo, geram código desnecessário, e
sujam o HTML com *divs *que não tem utilidade, ou nos forçam a ficar colocando
atributos *key *que não nos interessam muito.

Finalmente, no React 16.2 foi implementada a funcionalidade
[React.Fragment](https://reactjs.org/blog/2017/11/28/react-v16.2.0-fragment-support.html).

Na prática, podemos encapsular um array, ou múltiplos elementos com uma “tag
fantasma", que não será renderizada no HTML final:

    import React, { Fragment } from 'react'

    render() {
      return <Fragment>
        <h1>App React</h1>
        <h2>Vamos começar!</h2>
      </Fragment>
    }


Agora não precisamos mais sujar o HTML, nem ficar retornando array de elementos
com atributo key (meio confuso, não?!).

Apesar de ser um elemento que não será renderizado, ele também aceita *keys,
*caso necessário:

    render() {
      
    }


Pra simplificar ainda mais, se você é do tipo preguiçoso e não quer escrever
*Fragment*, *pode configurar seu projeto* (Babel, ESlint, etc) para aceitar a
sintaxe reduzida, que é apenas uma tag vazia *&lt;&gt;…*

    return (
      <>
        <h1>App React</h1>
        <h2>Vamos começar!</h2>
      </>
    );


É sério, isso funciona! A equipe do React disponibilizou um [Codepen com isso funcionando](https://codepen.io/reactjs/pen/VrEbjE?editors=1000).

### Conclusão

Enquanto nós mortais dormimos, o time do React está trabalhando arduamente para
melhorar mais a experiência dos desenvolvedores.

Espero que depois desse breve post, você possa apagar do seu projeto aquele
monte de *divs* inúteis, e substituí-las por *&lt;Fragments&gt;!*

Gostou? Recomende, compartilhe, comente!

Obrigado! :)