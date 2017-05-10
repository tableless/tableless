---
title: Desafios de um desenvolvedor front-end
author: Deivid Marques
type: post
date: 2014-02-28
excerpt: Veja os caminhos e os desafios vividos por um desenvolvedor front-end em um projeto web.
url: /desafios-de-um-desenvolvedor-front-end/
dsq_thread_id: 2333622791
categories:
  - Geral
  - Semântica
  - UX

---
A Web evolui constantemente. Essa evolução traz muitos benefícios e ao mesmo tempo nos obriga a estar sempre atualizados.

Você pode ter o melhor designer, o melhor desenvolvedor front-end e back-end no seu projeto e ainda assim, corre o risco de nenhum deles não pensarem ou desenvolverem focados no usuário. Não adianta ter um layout lindo e maravilhoso e os melhores códigos se seu projeto é pesado, lento e sem nenhuma usabilidade e acessibilidade.

Todos sabem que para um desenvolvedor front-end não basta saber html e css muito bem. Se ele for um mago do javascript, quer dizer que ele é top? Pode até ser, porém o que pretendo mostrar nesse artigo é algo mais simples, nada técnico, já que nem tudo é só código. Saber bem a teoria ajuda a direcioná-lo e facilita na hora da prática, esse é o grande desafio do profissional front-end.

### Conversando com  todos &#8220;eles&#8221;

Quando recebemos um layout, nossa missão é de criá-lo fielmente utilizando html, css e javacript com todas as boas práticas possíveis.

Precisamos:

  * validar em todos os navegadores (Chrome, Firefox, Safari, Opera e Internet Explorer);
  * que seu código tenha significado atrelado ao conteúdo para levar a informação do projeto até o usuário e também às máquinas;
  * que seu código possa receber e entregar os dados para os bots, crawlers, indexadores e robots através de microdados e semântica;
  * de um código responsivo;
  * que seja acessível para usuários com as mais diversas ausências visuais e motoras;

O usuário pode usar qualquer smartphone para ver o conteúdo ou mesmo um tablet, televisão, e por que não em uma geladeira? O conteúdo deve ser acessível por todos os dispositivos.

Hoje estes dispositivos já são responsáveis por quase todo o acesso, porém se contarmos os acessos de dispositivos específicos, ou seja, computadores com leitores de tela, cursores para mobilidade reduzida, celulares com assistente por voz e quem sabe o que mais vai surgir, o seu código tem que refletir a informação de forma coerente.

### Da semiótica à semântica

O designer transforma a necessidade do cliente em um produto no formato PSD, PNG ou AI, para isso ele busca na semiótica a essência do que precisa. O front-end pega o resultado e aplica semântica no conteúdo de forma que a informação relevante seja sempre devidamente compreendida pelos passos anteriores e principalmente pelo usuário, e nesta hora a marcação do html deve ser a melhor possível e o back-end vai tentar traduzir o que o designer produziu e pensou com a marcação que o front-end fez de forma a levar interação ao conteúdo ou melhora na leitura da informação por parte desse usuário.

Para entregar a melhor experiência, nós desenvolvedores front-end, podemos utilizar de uma rica linguagem de marcação, afinal H1 ao H6, p, a, cite, strong, section, article são mais que suficientes para interagir com os mais variados conjuntos de conteúdo. A implementação da [WAI-ARIA][1] traz interação para pessoas com alguma ausência ou redução dos cognitivos.

### Resumindo

O desenvolvedor front-end necessita do dom da palavra, ser o cara do bate papo, fazer seu código dialogar com navegadores, robots, devices, leitores de tela, isso não é uma tarefa fácil, precisa de muita leitura, prática e principalmente realizar testes.

Pensem no usuário ao criar layouts, ao desenvolver seu código ao criar uma interação. É um jogo praticamente onde seu html se dá bem com tudo e com todos, pois ele é a base para que o back-end prossiga depois com o seu bom trabalho. O seu código é o ponto de encontro que une o design com a programação, por isso ele é tão importante e precisa ser muito bem feito.

Desenvolver e projetar interfaces não é fácil, no entanto, o caminho é o foco no usuário, até porque é ele quem utilizará. Lembre-se disso!

 [1]: http://tableless.com.br/wai-aria-estendendo-o-significado-das-interacoes/