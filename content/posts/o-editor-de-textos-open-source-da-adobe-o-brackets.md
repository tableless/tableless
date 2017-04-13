---
title: O editor de textos Open Source da Adobe, o Brackets!
author: Felipe Correia
type: post
date: 2015-01-17
excerpt: O Brackets é um editor de textos muito novo, e é um daqueles projetos que vem para inovar e mudar a forma como as pessoas agem, olham, e fazem determinadas coisas, no nosso caso, o Brackets veio para dar uma acelerada no nosso desenvolvimento Front-end.
url: /o-editor-de-textos-open-source-da-adobe-o-brackets/
categories:
  - Editores
tags:
  - Brackets
  - editores
  - open source

---
Um editor de textos Open Source que vem crescendo com uma grande velocidade, alcançando, e, diria eu, ultrapassando alguns editores de texto já consolidados no mercado, prefiro não citar nomes.

## Principais recursos

**Extract, abra um PSD dentro do editor de textos:**
  
Basicamente essa feature consiste na abertura de um PSD dentro do editor de textos, através do plugin Extract (padrão do Brackets). Mas para que abrir um PSD dentro do editor de textos ? Bem, uma imagem vale mais do que mil palavras:



Mas, palavras também valem muito:
  
Sim, isso é mágico! Podemos perceber no vídeo que quando ele clica em uma layer do PSD e vai para o arquivo CSS digitar, ele recebe opções de autocomplete referente a layer que ele clicou, se ele clicou em uma imagem e começar a digitar “background”, ele vai receber uma sugestão de salvar como imagem a layer selecionada (ele cria a pasta images e salva dentro delas) e já inserir o restante do código automaticamente, que no caso seria “url(caminho/para-imagem.jpg);”.
  
Uma das coisas que mais gosto nisso tudo é que quando eu seleciono uma layer de texto, ele me dá a opção de colocar automaticamente o font-family, o font-size, o line-height etc, ele me dá a opção de inserir automaticamente todas as configurações que foram setadas no Photoshop, sem que eu precise ficar alternando entre as janelas do editor e do Photoshop para verificar qual fonte, qual tamanho, qual cor, ele pega tudo automaticamente e disponibiliza em forma de autocomplete. Uma mão na roda!

**Live Preview: digite e veja o resultado, sem reload**
  
Ok, isso não é nada de inovador. O Live Preview já existe em outros editores e também existe um ou mais softwares dedicados a fazer isso, mas todos que eu conheço fazem isso da mesma forma, eles dão reload na página. O Brackets não, conforme eu vou editando o código ele vai me dando o resultado do meu código sem dar reload na página, em tempo real, como se eu tivesse editando o código no inspect do browser, isso funciona quando a alteração é feita em um arquivo HTML ou CSS, já em arquivos JS ele dá reload na página. Para quem trabalha com dois monitores isso é do c@$#&%$!



Porém esse recurso só funciona com o navegador Google Chrome, mas isso é por enquanto, pois eles já estão trabalhando para que isso funcione em outros browsers, inclusive na ultima versão eles já liberaram para a gente poder testar isso, eu ainda não testei, mas em breve conseguirei um tempo para fazer isso e quem sabe em um próximo artigo conto para vocês, junto com outras novidades, já que a evolução é bem rápida.

**Split mode: vertical ou horizontal**
  
Divida o seu editor em duas telas, divida na horizontal ou na vertical, eu prefiro ficar com a divisão vertical, nunca consegui usar a divisão de horizontal. Gosto de usar com o html na esquerda e o css na direita.

## Atalhos do teclado:

O Brackets assim como outros editores e softwares tem seus atalhos para agilizar o dia-a-dia de quem trabalha com tais ferramentas. Destaco abaixo algumas que achei interessante.

**Ctrl+Shift+A:** Abre um input para você digitar uma tag e teclar enter, fazendo isso, ele irá inserir a tag completa com seu fechamento e seus atributos no html. Ex.: Digite link e tecle enter, ele vai retornar <link rel=&#8221;stylesheet&#8221; href=&#8221;&#8221;>. E quando você dá enter o “ponteiro” do mouse vai parar dentro das aspas do atributo href, dai basta você começar a digitar o endereço que ele vai mostrando as opções em forma de codehint.

**Ctrl+D:** Esse atalho de grande utilidade também está presente no Brackets. Serve para duplicar uma linha.

**Ctrl+Shift+D:** E esse para deletar uma linha.

**Ctrl+E:** Uma grande novidade do Brackets. Basicamente você pode editar o CSS sem ter que abrir o arquivo .css. Basta ir em um arquivo .html ou .php clicar sobre o elemento que deseja alterar as propriedades e pressionar Ctrl+E para abrir a tela de edição!

Se tiver uma div com um id ou uma class e você clicar em cima de “div” e usar o atalho, ele vai buscar nas folhas de estilo associadas ao documento (.html ou .php) por um seletor que altere “div”, mas se você clicar sobre o id ou sobre a class e apertar Ctrl+E ele irá buscar por um seletor que atinja aquele id ou aquela class clicada. Se você tiver duas ou mais classes você pode clicar em cima da class que você quer editar e usar o atalho que ele vai fazer a buscar por seletores referentes a class que você clicou. Muito legal, né ?

Segue uma tela, mostrando o atalho em funcionamento:

[<img class="aligncenter wp-image-46570 size-full" src="http://tableless.com.br/uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g.png" alt="1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g" width="638" height="300" srcset="uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g.png 638w, uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g-265x125.png 265w, uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g-400x188.png 400w" sizes="(max-width: 638px) 100vw, 638px" />][1]

  1. Caso não exista um seletor, você pode criar ele nesse dropdown “New Rule”, ao clicar nele, você vai poder escolher em que arquivo quer criar a regra (caso tenha mais de um);
  2. Local onde você vai editar a regra e simplesmente dar um Ctrl+S e pronto.
  3. Resultado da busca que ele fez em todos os arquivos .css associados ao documento atual.

Achou muito bom ? Pois é! Ainda tem mais, se você clicar em uma cor e usar o atalho, ele irá abrir um seletor de cor bem completo, se liga na tela:

[Um editor de textos Open Source que vem crescendo com uma grande velocidade, alcançando, e, diria eu, ultrapassando alguns editores de texto já consolidados no mercado, prefiro não citar nomes.

## Principais recursos

**Extract, abra um PSD dentro do editor de textos:**
  
Basicamente essa feature consiste na abertura de um PSD dentro do editor de textos, através do plugin Extract (padrão do Brackets). Mas para que abrir um PSD dentro do editor de textos ? Bem, uma imagem vale mais do que mil palavras:



Mas, palavras também valem muito:
  
Sim, isso é mágico! Podemos perceber no vídeo que quando ele clica em uma layer do PSD e vai para o arquivo CSS digitar, ele recebe opções de autocomplete referente a layer que ele clicou, se ele clicou em uma imagem e começar a digitar “background”, ele vai receber uma sugestão de salvar como imagem a layer selecionada (ele cria a pasta images e salva dentro delas) e já inserir o restante do código automaticamente, que no caso seria “url(caminho/para-imagem.jpg);”.
  
Uma das coisas que mais gosto nisso tudo é que quando eu seleciono uma layer de texto, ele me dá a opção de colocar automaticamente o font-family, o font-size, o line-height etc, ele me dá a opção de inserir automaticamente todas as configurações que foram setadas no Photoshop, sem que eu precise ficar alternando entre as janelas do editor e do Photoshop para verificar qual fonte, qual tamanho, qual cor, ele pega tudo automaticamente e disponibiliza em forma de autocomplete. Uma mão na roda!

**Live Preview: digite e veja o resultado, sem reload**
  
Ok, isso não é nada de inovador. O Live Preview já existe em outros editores e também existe um ou mais softwares dedicados a fazer isso, mas todos que eu conheço fazem isso da mesma forma, eles dão reload na página. O Brackets não, conforme eu vou editando o código ele vai me dando o resultado do meu código sem dar reload na página, em tempo real, como se eu tivesse editando o código no inspect do browser, isso funciona quando a alteração é feita em um arquivo HTML ou CSS, já em arquivos JS ele dá reload na página. Para quem trabalha com dois monitores isso é do c@$#&%$!



Porém esse recurso só funciona com o navegador Google Chrome, mas isso é por enquanto, pois eles já estão trabalhando para que isso funcione em outros browsers, inclusive na ultima versão eles já liberaram para a gente poder testar isso, eu ainda não testei, mas em breve conseguirei um tempo para fazer isso e quem sabe em um próximo artigo conto para vocês, junto com outras novidades, já que a evolução é bem rápida.

**Split mode: vertical ou horizontal**
  
Divida o seu editor em duas telas, divida na horizontal ou na vertical, eu prefiro ficar com a divisão vertical, nunca consegui usar a divisão de horizontal. Gosto de usar com o html na esquerda e o css na direita.

## Atalhos do teclado:

O Brackets assim como outros editores e softwares tem seus atalhos para agilizar o dia-a-dia de quem trabalha com tais ferramentas. Destaco abaixo algumas que achei interessante.

**Ctrl+Shift+A:** Abre um input para você digitar uma tag e teclar enter, fazendo isso, ele irá inserir a tag completa com seu fechamento e seus atributos no html. Ex.: Digite link e tecle enter, ele vai retornar <link rel=&#8221;stylesheet&#8221; href=&#8221;&#8221;>. E quando você dá enter o “ponteiro” do mouse vai parar dentro das aspas do atributo href, dai basta você começar a digitar o endereço que ele vai mostrando as opções em forma de codehint.

**Ctrl+D:** Esse atalho de grande utilidade também está presente no Brackets. Serve para duplicar uma linha.

**Ctrl+Shift+D:** E esse para deletar uma linha.

**Ctrl+E:** Uma grande novidade do Brackets. Basicamente você pode editar o CSS sem ter que abrir o arquivo .css. Basta ir em um arquivo .html ou .php clicar sobre o elemento que deseja alterar as propriedades e pressionar Ctrl+E para abrir a tela de edição!

Se tiver uma div com um id ou uma class e você clicar em cima de “div” e usar o atalho, ele vai buscar nas folhas de estilo associadas ao documento (.html ou .php) por um seletor que altere “div”, mas se você clicar sobre o id ou sobre a class e apertar Ctrl+E ele irá buscar por um seletor que atinja aquele id ou aquela class clicada. Se você tiver duas ou mais classes você pode clicar em cima da class que você quer editar e usar o atalho que ele vai fazer a buscar por seletores referentes a class que você clicou. Muito legal, né ?

Segue uma tela, mostrando o atalho em funcionamento:

[<img class="aligncenter wp-image-46570 size-full" src="http://tableless.com.br/uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g.png" alt="1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g" width="638" height="300" srcset="uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g.png 638w, uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g-265x125.png 265w, uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g-400x188.png 400w" sizes="(max-width: 638px) 100vw, 638px" />][1]

  1. Caso não exista um seletor, você pode criar ele nesse dropdown “New Rule”, ao clicar nele, você vai poder escolher em que arquivo quer criar a regra (caso tenha mais de um);
  2. Local onde você vai editar a regra e simplesmente dar um Ctrl+S e pronto.
  3. Resultado da busca que ele fez em todos os arquivos .css associados ao documento atual.

Achou muito bom ? Pois é! Ainda tem mais, se você clicar em uma cor e usar o atalho, ele irá abrir um seletor de cor bem completo, se liga na tela:

][2] 
  
Veja a lista completa de atalhos <a href="https://github.com/adobe/brackets/wiki/Brackets-Shortcuts" target="_blank">aqui</a>.

## Extensões:

Apesar de ser um editor com pouco tempo no mercado já conta com um grande quantidade de plugins para dar aquela incrementada no nosso workflow! Segue alguns deles que eu testei e já estou utilizando:

**Brackets Git:** bastante completo, disponibiliza uma interface para você usar o controle de versões mais queridinho de todos. Para aqueles que não gostam de usar o git através de interfaces, tranquilo cara, não precisa me xingar, ele te dá, de fácil acesso, um botão que leva diretamente para o terminal, aberto já na pasta do projeto, sem ter que navegar até o projeto pelo terminal (eu acho isso um saco).

**Emmet:** provavelmente você deve conhecer esse plugin que basicamente disponibiliza abreviações para agilizar o desenvolvimento de HTML e CSS.

**Code Folding:** esse plugin agiliza a organização do seu código. Ele disponibiliza a função de comprimir um determinado bloco de código em uma linha (e, claro, posteriormente você pode expandir novamente), deixando assim o código mais curto para se navegar entre o arquivo com mais legibilidade. Quem vem do DreamWeaver deve sentir falta desse recurso.

**Indent Guide:** muito bom para facilitar a leitura do código e evitar que você deixe tags HTML abertas sem querer. Ele cria uma linha guia ligando a tag de abertura e a tag de fechamento de determinado elemento, assim você pode verificar se tá tudo indentado certinho e ver se está fechando corretamente.

Entre outras milhares de extensões e recursos, isso é só um resumo.

Se você se interessou, você pode fazer o download no <a href="http://brackets.io/" target="_blank">site oficial</a>, tem versões para Windows, MAC OS X e Linux, funciona muito bem nos três sistemas. Teste, é de graça!

Se você já usa o Brackets e quer fazer um adendo ou uma correção, por favor, colabore, tenho interesse em saber o que você descobriu sobre ele.
  
E se você tem alguma dúvida ou quer mais artigos sobre ele, só deixar também seu comentário.

Até a próxima!

 [1]: http://tableless.com.br/uploads/2015/01/1bdjMIZVWtgGU99McRDyncLzxSq-osBjUEE1k9g.png
 [2]: http://tableless.com.br/uploads/2015/01/1lhZwadIKR8PR2gXXQrNu8nJCPW_PhW_NhqpHdA.png