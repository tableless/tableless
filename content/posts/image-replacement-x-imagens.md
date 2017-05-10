---
title: Image-Replacement x Imagens
author: Diego Eis
type: post
date: 2007-12-06
url: /image-replacement-x-imagens/
tweetbackscheck:
  - 1356126331
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/image-replacement-x-imagens";s:7:"tinyurl";s:26:"http://tinyurl.com/4yzokuc";s:4:"isgd";s:19:"http://is.gd/MUjCFl";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037759
categories:
  - Artigos
  - Técnicas e Práticas
tags:
  - CSS
  - firefox
  - html
  - imagereplacement
  - Na Prática
  - Semântica
  - tecnicascss
  - xhtml

---
Este assunto é muito abrangente e divertido de ser debatido.
  
Portanto, se você discordar deste texto, quero que lembre que é minha opinião&#8230; claro, sempre podemos mudar de idéia. 😀

Para não viajarmos muito, vamos pegar como pauta deste texto, o ponto que discutimos na &#8220;Lições Sobre Semântica #3&#8221;.
  
O ponto era fazer títulos com imagens ou image-replacement?

Bem, felizmente temos uma base para nos guiar&#8230; O código deve ficar o mais semântico possível.
  
Se o código deve ser semântico, já sabemos que as tags Hn que são usadas para definir títulos não podem ser descartadas, então elas devem continuar.

Ótimo, sabendo disso, vamos analisar as opções:

  1. Colocoar a imagem dentro de uma tag Hn.
  2. Fazer image-replacement sem tag span.

Eu poderia colocar como opção a técnica de image-replacement com tag span. Acontece que a tag span, suja nosso código, e queremos ter um código descomplicado.

### Colocando a imagem dentro de uma tag Hn

A solução seria:
  
<h1> <img src=&#8221;imagem.jpg&#8221; alt=&#8221;Texto&#8221; /> </h1>

Hmm&#8230; Essa solução é bastante atraente&#8230;
  
Se o usuário desabilitar as imagens, ou se por ventura a imagem aparecer quebrada, o texto alternativo (alt) irá aparecer no lugar da imagem.
  
Os browsers mais modernos como Firefox tratam esse texto como um texto normal, dando até para você selecionar. E esse texto pode ficar com o estilo que você definiu no CSS para a tag de título.

### Fazer image-replacement

A solução seria:
  
<h1> Texto </h1>

E assim, sumir com o texto pelo css e colocar a imagem como background.

Essa solução é muito, muito atraente&#8230;
  
Seu código não fica sujo com tags span ou tags img. Se a pessoa entra no site com algum tipo de browser baseado em texto, ela não terá problemas&#8230; Existe um porém.
  
Se o usuário desabilitar apenas as imagens, o texto não aparece.

Mas, agora vem a vantagem que fará você decidir o que fazer.

Se você optar por Image-Replacement, você terá uma flexibilidade que se colocando apenas imagens, você não teria.
  
Imagine que você tenha um site grande, e que todos os títulos tem que usar uma fonte maluca que o designer escolheu&#8230; Fatalmente estes títulos terão que ser imagem.

Um certo dia, o cliente se encheu da fonte maluca e decidiu que a fonte dos títulos devem mudar para Verdana.
  
Se você tivesse colocado as imagens direto no código, você teria que procurar cada uma das imagens e mudar para texto.
  
Se você fez com image-replacement, bastava desabilitar a image do background e fazer o texto aparecer&#8230; Muito, mas muito mais fácil.

Agora é com você. Essa é a principal diferença.
  
Os robos de busca, indexam os texto alternativos das imagens bem como o texto do image-replacement, então, não há problemas com isso.

Como disse, o assunto é bastante abrangente. E não é só este &#8220;problema&#8221; que existe. Mas o importante é analisar o caso, e aplicar a melhor solução para o caso.