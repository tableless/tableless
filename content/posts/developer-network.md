---
title: Locaweb Developer Network
author: Diego Eis
type: post
date: 2013-02-04
excerpt: Portal de Desenvolvedores da Locaweb.
url: /developer-network/
dsq_thread_id: 1059551321
categories:
  - Artigos
  - Notícias
tags:
  - 2013
  - developer network
  - locastyle
  - locaweb
  - locaweb style

---
Já faz um tempo que iniciamos um trabalho muito bacana aqui na Locaweb de padronizar e reestruturar a área de front-end. Nesse processo percebemos que alguns desenvolvedores que conhecem a Locaweb e utilizam nossos serviços, não tinham um acesso facilitado para encontrar informações técnicas, como por exemplo a integração e utilização das APIs dos produtos. Diversos desenvolvedores precisam dessas informações para que integrarem seus produtos aos serviços da Locaweb, tanto para projetos pessoais ou projetos para seus clientes.

Pensando nisso, resolvemos criar um site onde agregamos informações técnicas sobre nossos produtos e que posteriormente virará um grande portal contendo informações valiosas para desenvolvedores e outros profissionais de tecnologia. Esse portal se chama [Locaweb Developer Network][1].

## O que é?

O [Locaweb Developer Network][1] é uma iniciativa para aproximar nossas informações mais técnicas, dos profissionais de fora da Locaweb. Muitos desenvolvedores não sabem das coisas que temos aqui dentro, e esse site pode ser uma porta de entrada para trocarmos informações e batermos um papo bacana sobre tecnologia. Nós também [mantemos um GitHub][2], onde colocamos nossos projetos Open Sources. Por exemplo, nós mantemos um projeto chamado [BrickLayer][3], escrito em Python, que automatiza o empacotamento e publicação dos nossos (ou dos seus, se decidir usar) projetos em servidores de desenvolvimento e homologação. Ele monta o pacote do seu projeto e instala. Simple like that.

### Documentações de APIs

Lá no Locaweb Developer Network você também encontra [documentações sobre APIs][4] dos nossos serviços. Isso era um problema por que as informações sobre as APIs estavam camufladas em [nossa Wiki][5], junto com informações para usuários leigos. Agora, no Developer, separamos as informações importantes para o desenvolvedor, sem blá blá blá, só tendo as coisas técnicas, para aqueles desenvolvedores que desejam integrar seus serviços aos nossos.

Também iremos inserir algumas documentações de projetos internos, open source, que estão [em nosso GitHub][6].

### Locaweb Style

Uma das minhas missões aqui na Locaweb em 2012 foi iniciar uma reestruturação na área de front-end. O processo aqui era meio incompleto: existem equipes de back-end e equipes de UX, mas ninguém para fazer o intermédio entre as duas áreas. Logo, o pessoal de UX produzia todas especificações, que o pessoal de back-end utilizava para programar as funcionalidades. O problema era quando o PSD chegava. Os programadores back-end não tinham ideia de como fazer um HTML semântico ou um CSS sem problemas de compatibilidade. E eles tem razão, já que isso não é a responsabilidade deles. Algumas equipes chegavam a terceirizar na Índia todo o código front-end. As equipes que decidiam contratar alguém, mantinham códigos diferentes para fazer a mesma coisa. Nada escalava. Ninguém conversava. Nada acontecia.

Com a estruturação de uma equipe focada em código front-end, iniciamos a criação de uma biblioteca de estilos, elementos e comportamentos baseada no Bootstrap mas com visual customizado para os nossos serviços, chamado [Locaweb Style][7].

Uma parte dos produtos da Locaweb já está usando o Locaweb Style, aliás, utilizando exatamente as mesmas versões disponibilizadas para vocês. Assim conseguimos identificar erros e corrigí-los imediatamente. Logo, nós somos nossos próprios clientes. Todas as equipes de produtos daqui dentro nos reportam sobre problemas ou novas features.

Essa biblioteca é aberta para que você, se quiser usar em seus projetos, consiga fazê-lo sem problemas. A instalação é simples, basta linkar o CSS e o JS que disponibilizamos e pronto. Se quiser fazer um clone do projeto ou um fork, basta [visitar nosso GitHub][8].

Estou preparando um post explicando alguns detalhes sobre a construção do Locaweb Style. A ideia é que você agilize a produção do seu projeto. Um bocado de desenvolvedores já estão usando e mandando seus feedbacks. [Experimente][7] e nos diga o que achou.

Até lá você pode ler algo que identifiquei no processo de formar um Framework:
  
[Préprocessadores, Framewoks e Bibliotecas][9]
  
[Designers e Programadores][10]

 [1]: http://developer.locaweb.com.br
 [2]: https://github.com/locaweb/
 [3]: https://github.com/locaweb/bricklayer#readme
 [4]: http://developer.locaweb.com.br/documentacoes/
 [5]: http://wiki.locaweb.com.br/pt-br/P%C3%A1gina_principal
 [6]: http://github.com/locaweb/
 [7]: http://developer.locaweb.com.br/locawebstyle/
 [8]: https://github.com/locaweb/locawebstyle/
 [9]: http://tableless.com.br/estruturacao-de-client-side-preprocessadores-framewoks-e-bibliotecas-parte-1/ "Estruturação de Client-side – Parte 1: Préprocessadores, Framewoks e Bibliotecas"
 [10]: http://tableless.com.br/estruturacao-de-client-side-designers-e-programadores-parte-2/ "Estruturação de Client-side – Parte 2: Designers e Programadores"