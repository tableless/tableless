---
title: Modulando o CSS
author: Diego Eis
type: post
date: 2008-11-12
excerpt: 'As vezes não é inteligente fazer o código CSS todo em apenas um arquivo CSS. É aí que entra a modularização do CSS. '
url: /modulando-o-css/
aktt_tweeted:
  - 1
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356439890
shorturls:
  - 'a:3:{s:9:"permalink";s:39:"http://tableless.com.br/modulando-o-css";s:7:"tinyurl";s:26:"http://tinyurl.com/4234zmo";s:4:"isgd";s:19:"http://is.gd/coxXlO";}'
twittercomments:
  - 'a:5:{i:19755909173481472;s:6:"136508";i:24894803330207744;s:6:"136671";i:104183957406498817;s:7:"retweet";i:104183163777069057;s:7:"retweet";i:104182941319573504;s:7:"retweet";}'
tweetcount:
  - 5
dsq_thread_id: 503038666
categories:
  - Artigos
  - CSS
  - Técnicas e Práticas
tags:
  - CSS
  - desenvolvimento
  - padroes web
  - tableless

---
Quando trabalhamos com Padrões Web, trabalhamos com três camadas principais: Informação, formatação e comportamento.
  
A informação seria controlada pelo **HTML**. Ele exibiria a informação na tela com significado.
  
O **CSS** manipularia a formatação desses elementos para que ficassem belos e controlaria suas posições na tela.
  
E o **Javascript / Ajax** cuidaria do comportamento destes elementos.
  
<!--more-->


  
Vamos nos focar um bocado na segunda camada, o CSS. O CSS é uma linguagem de formatação é extremamente flexível.
  
O CSS, por ser uma linguagem com uma sintaxe fácil, muita gente coloca a mão durante o processo de desenvolvimento. E como seu código só tende a crescer, temos que ter um cuidado especial na organização dos arquivos.

Há várias maneiras de organizar os arquivos CSS de um site. Há sites que não precisarão de vários arquivos, bastando apenas um. Para estes devemos apenas ter cuidado com o código. Deixando-o simples e legível. Sempre tomando cuidado com a quantidade de linhas e código desnecessário. A estrutura seria mais ou menos essa:

[<img class="alignnone size-full wp-image-1035" title="Um CSS para todo o site" src="http://tableless.com.br/uploads/2008/11/umcss.jpg" alt="" width="499" height="414" srcset="uploads/2008/11/umcss.jpg 574w, uploads/2008/11/umcss-300x248.jpg 300w" sizes="(max-width: 499px) 100vw, 499px" />][1]

Grandes portais e sites com uma visitação extrema, podem querer otimizar esse código. Isso é considerável apenas para estas excessões. O preço da banda é alto e qualquer 1Kb que economizarem será um caminhão de dinheiro que economizarão. Para sites pequenos, e até mesmo alguns sites de médio porte, na minha opinião, não é necessário haver uma &#8220;[otimização de código][2]&#8220;.

Se você perceber que as páginas são muito diferentes uma das outras e que o código está aumentando descontroladamente, é muito aconselhável você dividir o código CSS para cada padrão de página. Isso ajuda a controlar o tamanho do código e permite que você modifique uma parte do site sem interferir em outras páginas.

[<img class="alignnone size-full wp-image-1034" title="Um arquivo para cada padrão" src="http://tableless.com.br/uploads/2008/11/umcss-padrao.jpg" alt="" width="499" height="414" srcset="uploads/2008/11/umcss-padrao.jpg 574w, uploads/2008/11/umcss-padrao-300x248.jpg 300w" sizes="(max-width: 499px) 100vw, 499px" />][3]

Essa opção é ótima para um site que tenha várias seções e cada seção tem um design diferente. Há um inconveniente: o código dentro do HEAD pode ficar enorme com tantas tags de LINK importando os arquivos de formatação. Para mudar isso, você pode fazer duas coisas: a primeira é fazer um arquivo CSS que importe todos os outros arquivos e linkar no HEAD apenas este arquivo.

[<img class="alignnone size-full wp-image-1033" title="Um arquivo CSS importando vários" src="http://tableless.com.br/uploads/2008/11/importando-todos.jpg" alt="" width="500" height="412" srcset="uploads/2008/11/importando-todos.jpg 577w, uploads/2008/11/importando-todos-300x247.jpg 300w" sizes="(max-width: 500px) 100vw, 500px" />][4]

Com essa primeira opção, o browser ainda carregará todos os arquivos CSS de uma vez. Pode ser que o carregamento fique pesado.
  
Por isso, há uma segunda opção que é conversar com seu programador para que ele faça uma mágica onde o site carregue apenas o arquivo CSS relativo àquela página. Quando visitamos a página interna, não é necessário carregar o arquivo CSS da HOME, por exemplo. Essa mágica previniria isso.

Outras pessoas preferem separar todo o código CSS em dois arquivos. Um arquivo conterá apenas informações de cor e fonte. E no outro arquivo haverá apenas informações sobre a estrutura do site: largura, altura, tamanho, margin, padding, position, float, etc.
  
Essa maneira é ótima para caso você quiser dar ao usuário opções de cores. O programador pode fazer um javascript maneiro que permita o usuário clicar e mudar a cor. O designer prepara vários CSS com regras de cores diferentes. A estrutura pode continuar a mesma, mas a paleta de cores muda. A mesma coisa pode-se fazer com a estrutura. A cor continua, mas a estrutura pode ser alterada de acordo com a opção do usuário.

[<img class="alignnone size-full wp-image-1032" title="Um css para estrutura e outro para cor" src="http://tableless.com.br/uploads/2008/11/estrutura-cor.jpg" alt="" width="500" height="412" srcset="uploads/2008/11/estrutura-cor.jpg 577w, uploads/2008/11/estrutura-cor-300x247.jpg 300w" sizes="(max-width: 500px) 100vw, 500px" />][5]

Essas seriam as formas mais comuns de organizar seu CSS. Perca um bocado de tempo planejando essa estratégia. Se o site é muito grande, esse tipo de planejamento prévio pode salvar o projeto. Vale a pena a equipe definir padrões desenvolvimento. O CSS é um dos fatores definitivos para manutenção, velocidade e compatibilidade do site. Um CSS fora de controle é um pesadelo que você não quer ter.

 [1]: http://tableless.com.br/uploads/2008/11/umcss.jpg
 [2]: http://tableless.com.br/nao-otimize-seu-codigo
 [3]: http://tableless.com.br/uploads/2008/11/umcss-padrao.jpg
 [4]: http://tableless.com.br/uploads/2008/11/importando-todos.jpg
 [5]: http://tableless.com.br/uploads/2008/11/estrutura-cor.jpg