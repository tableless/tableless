---
title: Processo front-end na Locaweb
author: Diego Eis
type: post
date: 2015-08-10
excerpt: Nosso processo e stack de front-end na Locaweb.
url: /processo-front-end-na-locaweb/
categories:
  - Artigos
  - Código
  - HTML
  - JavaScript
  - Tecnologia e Tendências
tags:
  - CSS
  - html
  - locaweb
  - mercado
  - SASS
  - wraith

---
É muito interessante entender como funcionam os processos em grandes empresas e comparar com processo que você executa na sua própria empresa. Depois que li [o post que o Jaydson fez falando um pouco sobre o processo de desenvolvimento no Terra][1], fiquei de escrever um artigo parecido mostrando mais ou menos como nós aqui da Locaweb fazemos nosso front-end. Sugiro que leia o post do Jaydson e mate a sua curiosidade sobre o processo que eles tem lá.

## Testes

Eu vou repetir o que o Jaydson e o Rafael Rinaldi já falaram tantas vezes em eventos e artigos: Fazer testes front-end é difícil. Ferramentas front-end ainda estão caminhando e nos últimos anos tivemos uma explosão de novidades que nos ajudou muito a avançar na profissionalização da área. Mas testes ainda é um dos pontos fracos. Conseguimos testar muito bem JavaScript usando Jasmine, QUnit e tantos outros, mas testes CSS ainda é um problema grande.

Essa semana adotamos na equipe a utilização do [Wraith][2], um [teste de comparação de telas feito pelos desenvolvedores da BBC][3]. Essa é só uma forma de conseguir testar a consistência das telas do seu produto. O [Hardy][4], por exemplo, que usa o Cucumber para comparar seu código.

Se você se interessar por testes CSS e quiser se aventurar nesse mundo, sugiro que [visite o site CSSTe.st][5]. Eles compilaram informações de várias iniciativas e sistemas que fazem o trabalho de testar CSS mais fácil. Dá uma vasculhada lá, você vai achar coisas bem interessantes.

## Pull Request

Fazemos branch feature. Isso quer dizer que ninguém faz fork do projeto. As modificações são feitas em branchs separadas e submetidas via Pull Request (ou Merge Request, dependendo do sistema que você usar).

O Pull Request precisa ter o OK de duas pessoas do time antes de ser aprovado. Antes de baixar o branch, a gente avalia algumas coisas antes: 

  1. As issues e o Pull Request estão bem descritivos mostrando qual o problema e o qual a solução adotada, com instruções exatas do que deve ser testado e avaliado?
  2. O CI passou? Tá okay?
  3. Se for JavaScript, os testes foram feitos? Se já existiam, precisou de modificação?
  4. Documentação está okay? Todas as atualizações foram feitas?

O pior momento é descrever bem o Pull Request e as Issues. Temos que ter em mente que isso faz parte do Changelog e é muito útil para consultas posteriores.

O pessoal da PlataformaTec tem uma cultura muito rica nesse assunto (e outros também). [Dá uma olhada no processo deles][6], que interessante!

## Framework

Desenvolvemos um framework interno chamado [Locaweb Style][7]. Na verdade, hoje existem 3 tipos de frameworks de interface aqui na firma. Cada um serve para serviços com designs e propósitos totalmente diferentes: um para a área de Checkout (compra), outro para área de Central do Cliente e o principal que é para a interface dos produtos. 

Esso deve ser padrão em muitas empresas e várias pessoas vão perguntar por que não usamos o Bootstrap. Nosso framework principal, que é o que faz a interface dos produtos que tem contato direto com o usuário se chama **Locaweb Style** e você pode ver o projeto (que é totalmente open source) [no nosso GitHub][8]. A documentação está bem completa e [pode ser vista aqui][7]. A ideia é que todos os produtos que tenham interface com o usuário use esse framework. Esse ponto é importante porque resolve uma série de problemas como:

  * **Processo** &#8211; As três equipes trabalham melhor quando as responsabilidades são bem dividas.
  * **Experiência padronizada** &#8211; Padronizando a interface e as interações, o usuário tem uma experiência melhor entre os produtos.
  * **Tirar a responsabilidade do client-side dos back-ends** &#8211; Cá entre nós: back-end não tem que se preocupar se o layout está bonito, se tem botão desalinhado, se aquilo vai ser bem visto no celular, se o CSS está bem escrito etc etc etc…
  * **Excesso de projetos** &#8211; São diversos projetos ao mesmo tempo, com equipes enxutas, trabalhando paralelamente. Não perde-se mais tempo de desenvolvimento criando telas parecidas do zero.
  * **UX com mais liberdade** &#8211; O time de UX precisa de atenção, carinho e de alguém que sente com eles para se preocupar com coisas que façam o nosso cliente amar o produto.
  * **Liberar gargalos** &#8211; Os times de UX e de front-end eram gargalos constantes. Precisávamos agilizar o processo.

Já estamos na versão 3 e cometemos uma série de erros nas duas primeiras versões. O maior erro que eu posso citar é a utilização do Bootstrap como base. Geralmente, o design definido pelo designer do time não era igual ao do Bootstrap. Claro. A empresa precisa de uma identidade própria. Logo, tínhamos o problema de recriar o design dos módulos e muitas vezes, precisávamos estender as funcionalidades JS de alguns módulos do Bootstrap. Quando percebemos, estávamos reescrevendo boa parte do framework. Logo, decidimos retirar totalmente o Bootstrap da versão atual, mantendo apenas o GRID.

## Stack de desenvolvimento

Não vou explicar detalhadamente cada uma das tecnologias, mas segue todas que usamos hoje para manter principalmente o framework:

  * **SASS** &#8211; Usando sintaxe **.sass**.
  * **Wraith** &#8211; Como teste de comparação visual de interface.
  * **Jasmine** &#8211; Para testes JS.
  * **JSHint** &#8211; Para manter a escrita de JS padronizada.
  * **Rake** &#8211; Para executar os testes e outras tarefas como publicação da documentação e fechamento de pacote para deploy.
  * **Middleman** &#8211; Para manter as documentações.
  * **.editorconfig** &#8211; Para manter o padrão dos editores em dia.

Nos projetos, nós nem nos preocupamos com o build dos assets. O Asset Pipeline está plugado em todos os projetos e faz tudo muito bem. Não há Grunt ou Gulp nos projetos.

Usamos Travis ligado no nosso [GitHub][9]. Os projetos todos internamente usam Jenkins.

## Deploy e ambiente

O deploy melhorou muito nos últimos anos. Hoje estamos assim: alguns produtos, não todos, podem fazer deploy a qualquer hora. Alguns precisam abrir um ticket para agendar uma janela. Nós, quando precisamos fazer um deploy do framework, ainda precisamos agendar. Mas já estamos andando para fazer deploy a qualquer momento do dia sem limite de vezes. Como os produtos usam o Locaweb Style com a versão travada, não há nenhum tipo de risco. O Deploy também pode ser descomplicado e automatizado, já que são apenas assets.

O nosso ambiente é bastante comum: temos um ambiente de teste, um de homologação e produção. Simples assim.

## Pontos falhos

Existem uma série de coisas que precisamos melhorar assim que encontrarmos tempo entre um projeto e outro. Mas o principal é manter a padronização de escrita de JS nos projetos. Há projetos que não usam nenhum tipo de pattern (nós usamos o [Revealing Module Pattern][10]), outros que usam CoffeeScript (o padrão é não usar), outros projetos que misturam JS puro com jQuery (o padrão é usar sempre a abstração do jQuery). A ideia é que nenhum projeto precise ter CSS para customizações. Toda a interface precisa estar dentro do Locaweb Style. Nem sempre é possível, já que há uma premissa que tudo o que está no framework precisa ser usado em dois produtos no mínimo. Não tem sentido colocar algo lá se apenas um produto vai usar e os outros não.

## Entrosamento

Ter uma equipe unida e entrosada é difícil. Todo mundo precisa estar disposto a fazer aquele relacionamento dar certo, sempre entendendo as diferenças pessoais de cada um, como em um casamento. Ter uma equipe 100% unida, sem brigas, concordando com tudo é impossível. Eu tenho a sorte de trabalhar com uma equipe que se conhece e sabe exatamente onde temos que melhorar mais, entendendo os pontos fracos e principalmente nossos pontos fortes. Leva tempo para criar esse entrosamento. Muito trabalho, suor e sangue. São muitas reuniões de feedback, 1 on 1, retrospectiva&#8230; 

Outra coisa que ajuda é a multidisciplinaridade entre os integrantes. Temos caras que lá programam um pouco de back. Outros que são mestres no CSS e tem um chamego especial para o lado de UX e Design, outros que gostam de mexer com infra. Isso tudo conta como ponto positivo. 

Lendo assim, até parece simples! 😉

 [1]: http://jaydson.org/processo-front-end-no-terra/
 [2]: https://github.com/BBC-News/wraith
 [3]: http://bbc-news.github.io/wraith/
 [4]: http://hardy.io
 [5]: http://csste.st
 [6]: http://guidelines.plataformatec.com.br/pull-requests.html
 [7]: http://opensource.locaweb.com.br/locawebstyle/
 [8]: http://github.com/locaweb/locawebstyle/
 [9]: http://github.com/locaweb/
 [10]: http://addyosmani.com/resources/essentialjsdesignpatterns/book/#revealingmodulepatternjavascript