+++
authors = "Diego Eis"
categories = ["carreira", "opinião"]
date = "2018-07-22T19:10:47+00:00"
excerpt = "O perfil do desenvolvedor front-end mudou e se transformou em dois (talvez mais)\nperfis diferentes. Entenda como tudo começou e saiba em qual perfil você se\nencaixa mais."
image = "https://i.imgur.com/k12zslh.jpg"
tags = ["mercado"]
title = "Os dois tipos de front-end: design e o engineer — Parte 1 : Uma breve história"
type = "post"

+++
_Escrevi ouvindo essa música. Recomendo para a leitura:_  
[The Little Things That Give You Away — U2](https://open.spotify.com/track/4hZBQElqZGij1ffHQdMQVa?si=zyzRE-HxRXe7S26VhMCe4g)

***

O **menino do HTML**. Essa era a visão padrão que o mercado web tinha do front-end por um simples motivo: front-end não tinha responsabilidades importantes. Pelo menos era o que o Designer, o Back-end e os clientes (resumindo: o mundo) achavam.

O designer e o back-end detinham as grandes responsabilidades de um projeto. Enquanto um definia o layout, fluxo do sistema e como seria o comportamento do usuário no projeto, o outro fazia tudo isso funcionar. Ele era o cara que manjava de servidor, modelagem de banco de dados, linguagens de servidor e tudo quanto era mandinga.

Por sua vez, o front-end não se encaixava em nenhum dos dois extremos. Ele fazia código, **mas o código não funcionava sozinho, sem linguagem de servidor envolvida**. Ele transformava o layout para código HTML/CSS/JS, **mas o layout não era ele que tinha feito**. Junte isso com o fato de que NINGUÉM sabia exatamente o que era desenvolvimento para internet e pronto, um homem foi jogado ao mar.

**Era uma época infeliz.**

Mas hoje vivemos nos tempos modernos. Vivemos num momento onde a tecnologia parece não ter fronteiras e que o desenvolvimento web vive numa evolução contínua de ferramentas e novos padrões, transformando a Web numa plataforma real para o futuro (há controversas).

## MVC: Quem determinou até onde vai o front-end e onde começa o back-end?

Essa coisa de limites entre back-end e front-end sempre foi uma polêmica.

Em todos os projetos, de todos os tamanhos, era necessário haver uma conversa entre os desenvolvedores e os front-ends — **sim, as pessoas separavam os devs "verdadeiros" dos front-ends… briguei muito com isso nas empresas que eu trabalhei** — para combinar até onde o back-end iria, para que o front-end pudesse implementar o layout.

Em uma época não muito distante, todo mundo trabalhava ou queria trabalhar em projetos com estrutura MVC. [Você pode saber o que é a estrutura MVC aqui](https://tableless.com.br/entendendo-o-padrao-mvc-na-pratica/).

Alguns times preferiam que o back-end fosse até a camada de Model. O Front-end era o responsável então por montar as Controllers para então manipular as Views. Em outros times, os front-ends preferiam que os back-ends fossem até as Controllers para que eles ficassem responsáveis apenas pela View.

Nem preciso dizer que era uma grande confusão, pois se você ir pela lógica, o front-end só mexe no client-side. A Controller é a área cinza. É na Controller que intermediamos o Model (só dados, faz sentido ficar com back-end) e a View (totalmente client-side, faz sentido ficar com front-end).

Tinha outros times que combinavam que todo mundo podia mexer na Controller. Obviamente não dava certo.

### Até que veio a era das APIs e o início da depressão

Quando todo mundo começou a trabalhar com APIs, microserviços, webservices e todas as outras tecnologias relacionadas, foi aí que a coisa começou a se organizar.

**Com a criação de APIs havia um limite claro entre back-end e front-end**: o back-end criava os endpoints e o front-end lia as informações contidas nesses endpoints e fazia o que tinha de ser feito. O único acordo que as duas partes deveriam fazer era como a estrutura desses dados seria exposto: o famoso contrato.

> As APIs ajudaram a demarcar um limite de atuação dos back-ends e front-ends. A > briga entre os dois lados cessou um pouco e a coisa começou a andar > decentemente.

Com isso, a briga entre os dois mundos acabou. Mas infelizmente nem tudo são flores. Com a vinda das APIs, uma série de complexidades foram criadas para o lado do front-end. Alguma da lógica e da regra de negócio começou a ficar do lado de front-end. Agora não era só exibir informação na interface do layout, alguém gerir os estados de componentes, lidar rotas, gerenciar tokens de acesso, segurança e tudo o mais.

Foi aqui que centenas de frameworks e bibliotecas JS surgiram (e morreram) da noite pro dia, tentando resolver os problemas que antes eram de back-end, no client-side.

## Todo mundo ficou desconfortável, mas a coisa andou

**No meio dessa mudança toda, muitos front-ends não estavam acostumados a lidar com lógica e regras de negócio que agora estavam transbordando para o lado do client-side,** exatamente por que a praia deles era escrever CSS e Javascript para interface.

Nessa revolução, houve um breve momento onde o Javascript ganhou MUITA visibilidade. E aí os front-ends que sabiam MUITO Javascript se destacaram. Isso era bom e ruim. Os front-ends que não gostavam ou não sabiam trabalhar com programação pesada de JS, acabaram se decepcionando. Houve uma momento onde era até **vergonhoso dizer que não manjava de JS, e só sabia trabalhar com JS para interface**.

Aí aconteceu de tudo um pouco: **vários devs não se consideravam mais devs, exatamente porque eles só sabiam CSS e HTML com um pouco de JS** para interface e achavam que não tinham competência para fazer toda essa coisa nova. Outros simplesmente não gostavam de lidar com lógica, mas adoravam a parte visual.

Em paralelo o mercado mudou de vez: teve front-end que virou back-end. Teve back-end que virou front-end. Teve front-end que saiu da área. Teve empresa que demitiu back-end pra contratar front-end, dado que o trabalho de integrar API na Interface se tornou maior que fazer APIs. Uma revolução total na era.

# **Mas desse balaio saiu uma reformulação do perfil do desenvolvedor front-end.**

Dois perfis de profissionais ficaram bem claros no mercado:

* Um dev que manjava MUITO de interface. Que dominava CSS como ninguém e todos os   truques de JS para manipular elementos no DOM com CSS, além de conseguir lidar   com o designer discutindo soluções de layout;
* E outro profissional que tinha uma grande facilidade para a parte funcional da   coisa. Ele não era um back-end, mas consegue discutir soluções funcionais de   igual para igual.

**No próximo artigo**, escrevi um pouco sobre cada um desses perfis e como eles se encaixam no desenvolvimento de software atual.

## Bônus para quem está começando agora

Abaixo, segue uma imagem muito interessante que o [Kamran Ahmed](https://medium.com/@kamranahmedse) fez no seu artigo [Modern Frontend Developer](https://medium.com/tech-tajawal/modern-frontend-developer-in-2018-4c2072fa2b9c), mostrando uma opção de caminho que geralmente alguém toma para se tornar um front-end. Fique como referência, mas não como verdade. Talvez o início pode acontecer igual para todo mundo, mas no meio do caminho pode haver algumas mudanças de pessoa para pessoa. Mesmo assim é uma grande referência.

![](https://cdn-images-1.medium.com/max/1000/1\*w9QmGI34BP7sDpbyMoj7LQ.png)