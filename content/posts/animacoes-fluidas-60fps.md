---
title: Animações fluídas à 60fps
author: Alan Cezar
type: post
date: 2015-06-29
excerpt: Fazendo animações a 60fps nos browsers atuais.
url: /animacoes-fluidas-60fps/
categories:
  - Browsers
  - CSS
  - Técnicas e Práticas
tags:
  - performance

---
Existem diversas maneiras da página interagir com o usurário, e uma dessas maneiras é a interação com animações. Podem ser desde animações mais triviais como o scroll de um elemento, até animações mais complexas como gráficos de jogos.
  
Algumas vezes sentimos nossa UI engasgar durante essas interações, dando o sentimento de que algo está sendo executado com muito esforço. E pode apostar que é isso mesmo.

Para criar essas animações o browser basicamente se comporta como outros softwares que reproduzem vídeo, gerando uma sequência de imagens e renderizando elas na tela do seu dispositivo.

Vou resumir o processo executado pelo browser para gerar essa sequencia de quadros, e como o nosso pode influenciar esse processo de forma negativa ou positiva.

## 30fps ou 60fps?

Como foi dito acima, o browser procura renderizar cerca de 60 quadros por segundo. Mas essa deve ser a nossa meta? Dá pra sentir diferença?

Alguns estudos dizem que 30fps é o suficiente para a percepção humana, porém 60fps é ideal pois dá uma sensação de fluidez.

Pessoalmente, percebo diferença entre 30fps e 60fps, acima disso não. Se você quiser fazer um teste dá uma olhada <a href="http://frames-per-second.appspot.com/" target="_blank">nesse site</a>.

Acredito que o ideal é entregar o mais próximo possível dos 60fps, assim fica mais fácil agradar gregos e troianos.

## O Trampo do Browser

[<img class="alignnone wp-image-49672 size-full" src="http://tableless.com.br/uploads/2015/06/rsz_fluxo_de_renderização_do_browser.png" alt="Fluxo de renderização de um frame" width="800" height="230" />][1]

O fluxo acima resume as etapas que o browser pode seguir para criar um frame. Nosso código pode influenciar esse fluxo, podendo diminuir o trabalho executado pela engine de renderização. Vamos conhecer cada etapa e descobrir como o código que escrevemos influencia essa sequencia.

### DOM

Ocorre sempre que o DOM é alterado.

Criar ou remover um elemento dispara essa etapa. Esse é um dos motivos pelos quais o acesso ao DOM é sagrado, e não deve ser feito em vão.

Exemplos:
  
Incluir ou remover _trs_ em um _tbody_.
  
Alterar o texto de algum elemento.

### CSSOM

Ocorre sempre que alguma regra de estilo é alterada.

Pode ser causado por uma nova folha de estilo inserida na página, alteração da classe de algum elemento e alteração de alguma regra de estilo inline.

Exemplos:
  
Inserção de novas regras via tag _style_ ou por alguma folha de estilo externa.
  
Alteração de algum estilo inline (lembra do $.hide() do jQuery?).

### Arvore de Renderização

Após criar ou alterar o DOM e/ou o CSSOM ele precisa mapear os elementos que ficarão visíveis na tela, e quais regras de estilo se aplicam a cada elemento. Esse mapeamento fica na Árvore de Renderização.

### Layout

Ocorre sempre que a geometria de algum elemento é alterada e a posição de algum elemento é alterado na tela.

Exemplos:
  
Alteração de altura ou largura de algum elemento.
  
Alteração da margem de algum elemento.

### Pintura

Ocorre quando são necessárias alterações visuais que não alteram o tamanho ou posicionamento de algum elemento.

Exemplos:
  
Alterar a cor de fundo de uma _div_.
  
Alterar a cor da fonte.
  
Alterar o z-index de algum elemento.

## Inspecionando no browser

Vou dar um exemplo básico de como inspecionar esses eventos no browser. Será um overview simples e não entrarei nos detalhes de cada ferramenta.

Eles entregam as métricas de maneira bem distintas umas das outras, mas durante uma dor de barriga fazem um bom trabalho pra te ajudar á achar quais são os eventos problemáticos.

Não importa qual browser você está usando, aperte F13 para abrir as ferramentas de desenvolvedor. Se você não achar o F13 no seu teclado, quer dizer que você caiu na pegadinha. =)

Geralmente o F12 abre essas ferramentas pra você (pelo menos no Windows).

### Google Chrome

[<img class="alignnone wp-image-49668 size-full" src="http://tableless.com.br/uploads/2015/06/rsz_2style_render_-_gc.jpg" alt="Google Chrome - Timeline" width="800" height="432" />][2]

Costumo usar o Chrome diariamente. Acredito que ele é atualmente o mais completo pois entrega bastante informações. Mas muitas informações. Seria assunto pra um post inteiro.

### Internet Explorer 11 / Microsoft Edge

[<img class="alignnone wp-image-49669 size-full" src="http://tableless.com.br/uploads/2015/06/rsz_style_render_-_ie.jpg" alt="Microsoft Edge - Análise de Desempenho" width="800" height="432" />][3]

No momento estou usando o Windows 10 Preview e tenho á disposição o IE11 e o Microsoft Edge. Posso afirmar que ele faz um trabalho decente mas ainda tem muito pra melhorar.

### Firefox Developer Edition

[<img class="alignnone wp-image-49670 size-full" src="http://tableless.com.br/uploads/2015/06/rsz_style_render_-_ff.jpg" alt="Firefox - Análise de Desempenho" width="800" height="215" />][4]

O Firefox faz um bom trabalho e tem uma ótima documentação, mas nesse quesito ainda tem muito para melhorar se o compararmos ao Chrome.

### Dicas de outras ferramentas e recursos

<a href="http://csstriggers.com/" target="_blank">CSS Triggers</a>
  
Este site tenta listar as propriedades CSS e o efeito que a alteração delas causam na renderização de um frame. Ótimo recurso!

<a href="https://developers.google.com/web/fundamentals/performance/index?hl=pt-br" target="_blank">Google Web Fundamentals</a>
  
No Google Web Fundamentals existe uma sessão focada no assunto. Ótimo ponto de partida para aprender sobre o assunto.

<a href="https://www.udacity.com/course/website-performance-optimization--ud884" target="_blank">Udacity &#8211; Website Performance Optimization</a>
  
Curso gratuito desenvolvido pela Udacity com a Google. Além das explicações teóricas, tem bastante exercícios práticos.

 [1]: http://tableless.com.br/uploads/2015/06/rsz_fluxo_de_renderização_do_browser.png
 [2]: http://tableless.com.br/uploads/2015/06/rsz_2style_render_-_gc.jpg
 [3]: http://tableless.com.br/uploads/2015/06/rsz_style_render_-_ie.jpg
 [4]: http://tableless.com.br/uploads/2015/06/rsz_style_render_-_ff.jpg