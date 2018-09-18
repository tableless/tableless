+++
authors = "Udacity Brasil"
canonical = "https://br.udacity.com/blog/post/react-o-que-e-como-funciona"
categories = ["javascript"]
date = "2018-09-13T10:00:00-03:00"
excerpt = "Como definido por seus criadores, React é “uma biblioteca JavaScript declarativa, eficiente e flexível para a criação de interfaces de usuário (UI)”."
image = "https://i.imgur.com/wRTG7kS.png"
publishdate = "2018-09-13T10:00:00-03:00"
tags = ["reactjs"]
title = "React: o que é e como funciona essa ferramenta?"
type = "post"

+++
O desenvolvimento de sistemas e aplicativos está em constante evolução. Nesse exato momento, milhares de desenvolvedores estão criando frameworks, bibliotecas e ferramentas com o objetivo de ajudar outros desenvolvedores a atingir o máximo de eficiência possível.

Muitas vezes, essas tecnologias são concebidas dentro de grandes empresas, como projetos paralelos que buscam resolver gargalos internos das equipes técnicas.

Algumas se tornam soluções tão interessantes que as companhias decidem compartilhá-las com o mundo.

O React é um desses casos.

## O que é React?

Como [definido](https://reactjs.org/tutorial/tutorial.html) por seus criadores, [React](https://br.udacity.com/course/react-nanodegree--nd019) é “uma biblioteca JavaScript declarativa, eficiente e flexível para a criação de interfaces de usuário (UI)”.

Essa biblioteca surgiu em 2011, no Facebook, e passou a ser utilizada na interface do mural de notícias da rede social.

No ano seguinte, passou a integrar também a área de tecnologia do Instagram e de várias outras ferramentas da empresa. Em 2013, o código foi aberto para a comunidade, o que colaborou para sua grande popularização.

A imagem abaixo mostra uma comparação do uso do React em relação a outras tecnologias (Angular e Vue.js):

![](https://d20vrrgs8k4bvw.cloudfront.net/images/blog/pt-BR/react-imagem-1.jpg)   
_Comparação do número de downloads \[Fonte:_ [_Medium/unicorn.supplies_](https://medium.com/unicorn-supplies/angular-vs-react-vs-vue-a-2017-comparison-c5c52d620176)_\]_

## 7 fatos sobre React

### 1. React é uma biblioteca

Dizer que React é uma biblioteca significa que este [não é um framework](https://reactjs.org/blog/2013/06/05/why-react.html), mas simplesmente uma coleção de funcionalidades relacionadas que podem ser chamadas pelo desenvolvedor para resolver problemas específicos — a criação de interfaces de usuário reaproveitáveis, no caso do React.

Já a principal característica de um framework é a [Inversão de Controle](https://pt.wikipedia.org/wiki/Invers%C3%A3o_de_controle), também conhecida como [Hollywood Principle](https://wiki.c2.com/?HollywoodPrinciple). Ou seja, quem dita o que (e como) algo deve ser feito é o framework, não o desenvolvedor — é ele quem chama o seu código, e não o contrário.

O importante disso tudo é que, em geral, bibliotecas são mais flexíveis e menos complexas do que frameworks.

No caso do React, sua única e principal função é a criação de interfaces de usuário, que organiza o que será mostrado para o usuário final na tela sem se preocupar em saber sobre o resto.

### 2. React é JavaScript

Referência para quem trabalha com desenvolvimento front-end, JavaScript é a linguagem de programação que mais evoluiu nos últimos tempos, consolidando-se como a mais utilizada pelos desenvolvedores atualmente.

De acordo com o [StackOverflow Survey 2017](https://insights.stackoverflow.com/survey/2017#most-popular-technologies), seu uso cresceu 20% em relação a 2016:

![](https://d20vrrgs8k4bvw.cloudfront.net/images/blog/pt-BR/react-imagem-2.jpg)   
_JavaScript é a linguagem mais popular entre desenvolvedores atualmente \[Fonte: StackOverflow Survey 2017\]_

Esse crescimento está diretamente relacionado à “revolução” trazida por ferramentas como NodeJS, Angular, VueJS e, claro, React. Elas facilitam o trabalho dos desenvolvedores e expandem os casos de uso, permitindo, inclusive, o uso de JavaScript na criação de APIs e servidores em back-end.

Isso significa que um número cada vez maior de programadores está migrando ou começando seus estudos em JavaScript — o que, em consequência, aumenta o mercado de trabalho para quem domina essa linguagem.

Outra grande vantagem é que a comunidade JavaScript (e de React) é imensa, o que ajuda muito na hora de buscar soluções ou tirar dúvidas online.

Por isso, é importante salientar: quem quer começar a aprender React precisa ter uma boa base em JavaScript, além de conhecimentos em HTML e CSS.

Caso você não tenha ainda muita familiaridade com essas tecnologias, a recomendação é buscar cursos e tutoriais online sobre o tema.

Um bom passo inicial é fazer cursos abertos da Udacity, como [Introdução ao HTML e CSS](https://br.udacity.com/course/intro-to-html-and-css--ud304) e [JavaScript Básico](https://br.udacity.com/course/javascript-basics--ud804).

### 3. React é uma linguagem de programação declarativa

Uma linguagem de programação declarativa é geralmente definida como o contrário de uma linguagem imperativa. Mas o que isso significa?

Em poucas palavras, enquanto a declarativa se preocupa com o que o programador quer fazer, a imperativa quer saber como atingir o objetivo desejado.

Ficou confuso? Vamos usar um exemplo para esclarecer esse ponto. Imagine que você tenha a possibilidade de “curtir” uma publicação em seu site.

Caso essa publicação seja curtida, a cor do botão é alterada. Se não havia sido curtida antes, o botão fica azul. Caso já tenha sido curtida anteriormente, a publicação será "descurtida", ou seja, o botão voltará a ser cinza.

Em uma linguagem imperativa, usando JavaScript, o resultado poderia ser obtido do seguinte modo:

    if( usuario.curtiu() ) { 
    
    if( botaoEstaAzul() ) { 
    
        removeAzul(); 
    
        adicionaCinza(); 
    
    } else { 
    
        removeCinza(); 
    
        adicionaAzul(); 
    
    } 
    
    }
    

Veja como o programador precisa se preocupar com cada passo da ação para mudar a cor do botão.

Se o usuário clica e o botão já está azul, remove-se a cor azul e adiciona-se a cor cinza. Caso contrário, o processo é o inverso.

Você deve ter percebido como esse tipo de solução pode ficar complexo em uma aplicação real.

Veja agora como fazer a mesma ação usando o React:

    if( this.state.curtido ) { 
    
    return <curtidaAzul />; 
    
    } else { 
    
    return <curtidaCinza />; 
    
    }
    

O código acima deixa claro que a linguagem não está preocupada em saber todos os passos para executar a ação.

Caso o _state.curtido_ do botão seja verdadeiro, retorna o _componentecurtidaAzul_; se for falso, retorna _curtidaCinza_. Assim, o React se preocupa apenas com o que é exibido na interface do usuário.

### 4. React é flexível: tudo é componente

Com esse exemplo surge também o conceito de componentes, uma das bases do React.

O modo como o React trabalha para criar interfaces de usuário (ou User Interfaces, as UIs) é por meio da quebra de toda a estrutura da aplicação em componentes.

Se você tem experiência na criação de sites, deve estar acostumado a ter todo o código HTML de uma página em um único arquivo.

O que o React propõe é o contrário: separar todo o código em pequenas partes (em arquivos diferentes), que se comportam como componentes reutilizáveis.

Para entender melhor essa proposta, vamos analisar a página principal da Udacity:

![](https://d20vrrgs8k4bvw.cloudfront.net/images/blog/pt-BR/react-imagem-3.jpg)

Pensando em uma hierarquia, é possível organizar a página em componentes da seguinte maneira:

* BarraNewsletter (1)
* MenuSuperior (2)
* BotaoMenu (3)
* BotaoChamada (4)
* PainelPrincipal (5)
* PainelLateral (6)
* Chamada
* Patrocinadores (7)

Esse é apenas um dos possíveis modos de organização, claro: cabe ao desenvolvedor pensar como será a estrutura dos componentes.

O importante aqui é entender que cada um desses componentes pode ser reutilizado em qualquer outra página do site, como o MenuSuperior.

Uma vez que o desenvolvedor esteja familizariado com a abstração proposta pelo React, o trabalho se torna muito mais fácil — e menos tempo é gasto na criação das aplicações.

### 5. React é eficiente

Se há uma vantagem clara que o React traz é no modo como ele trabalha com o DOM (Document Object Model) e atualiza os componentes de acordo com seus estados.

Em uma aplicação JavaScript tradicional, o programador deve se preocupar em descobrir quais dados mudaram para poder alterar o DOM e os estados dos elementos criados. Isso é muito trabalhoso e pouco eficiente (lembra do exemplo do botão de curtir acima?).

O que o React propõe é a criação do seu próprio DOM, mais eficiente, no qual os componentes vivem, o que é mais conhecido como Virtual DOM.

Assim, toda vez que um componente é renderizado, o React atualiza o Virtual DOM de cada componente já renderizado e busca as mudanças. E como o Virtual DOM é leve, esse processo é muito rápido.

O React então compara o Virtual DOM com uma imagem do DOM feita antes da atualização e descobre o que realmente mudou, atualizando somente os componentes que mudaram de estado. Há um enorme ganho de performance aqui.

Na prática, o resultado é o seguinte:

![](https://d20vrrgs8k4bvw.cloudfront.net/images/blog/pt-BR/react-imagem-4.jpg)

Como fica evidente, caso apenas um elemento da lista seja atualizado, o React não renderiza novamente toda a lista, somente o componente que mudou de nome.

É aí que está a eficiência dessa biblioteca.

### 6. React é móvel

Outra grande vantagem do React é que, com os mesmos conhecimentos utilizados para criar sites, também é possível criar aplicativos móveis nativos através do React Native.

Várias empresas, como Walmart e Uber Eats, já usam a biblioteca para criar seus aplicativos, o que reduz o custo de produção e permite aproveitar desenvolvedores em diversos ambientes.

Isso é um grande diferencial – e um ótimo motivo para se envolver com React.

### 7. React é amado

Ainda segundo a pesquisa StackOverflow Survey 2017, React é a tecnologia mais amada pelos desenvolvedores. Isso é muito importante, pois é preciso se sentir bem com a tecnologia escolhida para trabalhar de maneira otimizada em seus projetos.

E quanto mais gente existe envolvida e animada com uma tecnologia, maiores são as possibilidades de uso e as inovações que podem surgir dentro daquela comunidade.

Se você já possui alguma experiência com JavaScript, HTML e CSS, não perca tempo e se inscreva no programa [**Nanodegree Seja um Desenvolvedor React**](https://br.udacity.com/course/react-nanodegree--nd019)!

Não há melhor maneira de aprender do que com um curso focado na prática – e assim conseguir aproveitar todas as oportunidades de um mercado em expansão.