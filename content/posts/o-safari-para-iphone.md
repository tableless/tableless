---
title: O Safari para iPhone – Desenvolvimento web para iPhone
author: Diego Eis
type: post
date: 2008-10-13
excerpt: O desenvolvimento web para mobiles está se tornando algo comum. Fazer sites para aparelhos como o iPhone deixou de ser coisa de outro mundo, mesmo assim, há certos detalhes que precisamos entender.
url: /o-safari-para-iphone/
aktt_tweeted:
  - 1
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356441562
shorturls:
  - 'a:3:{s:9:"permalink";s:44:"http://tableless.com.br/o-safari-para-iphone";s:7:"tinyurl";s:26:"http://tinyurl.com/3aww5sv";s:4:"isgd";s:19:"http://is.gd/zpkzBS";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038571
categories:
  - Artigos
  - Browsers
  - Mobile
  - Técnicas e Práticas
tags:
  - CSS
  - desenvolvimento
  - internetmovel
  - iphone
  - Mobile
  - mobilidade
  - tableless
  - xhtml

---
Esse texto e muitos outros fazem parte do [Campus Online][1]. Visite e [cadastre-se grátis][2]!
  
[Sessão exclusiva sobre Desenvolvimento web para iPhone][3].

### Um pouco de História

Por volta de 1997, os computadores da Apple traziam por padrão o Netscape. Naquele tempo o mercado de browsers não era tão acirrado como hoje e os concorrentes eram poucos. O Internet Explorer estava em sua versão 2/3. Mesmo assim, o Internet Explorer para Mac era também distribuído com o MacOS durante os 5 anos de acordo entre Apple e Microsoft. A Microsoft laçou 3 versões principais do seu navegador para o Mac, parando na versão 5 em março de 2000.<!--more-->

Em 2003, a Apple anunciou que eles estavam desenvolvendo seu próprio browser baseado no motor de renderização KHTML. A versão 1.0 foi lançado como browser padrão do MacOS por volta de Junho de 2003. O Internet Explorer ainda era distribuido no sistema, mas agora como um navegador alternativo, até Abril de 2005.

### Motor de Renderização WebKit

O Safari utiliza um motor de renderização chamado WebKit. O WebKit tem dois motores de renderização: o WebCore, que é o motor de renderização baseado no KTHML do Konqueror. E o JavaScriptCore, baseado no motor de javascript KDE chamado KJS. Esses motores estão sob Licensa GNU.

A Apple, ao fazer o Safari fez muitas atualizações e modificações no motor KHTML, deixando-o mais maduro e robusto. Essas modificações foram devolvidas para a comunidade e incorporadas no Konqueror.

### MobileSafari e Safari para Desktop

A idéia é que o usuário tenha uma experiência muito próxima a experiência que ele tem no desktop. Por isso o Safari para iPhone (MobileSafari) foi feito sob o mesmo motor de renderização WebKit do Safari para Windows e Mac. Diferenças: 1) Se o site não foi feito para iPhone, ele renderiza a página da mesma forma como renderiza em um Safari para desktop, mas miniaturizada. 2) A interação do usuário.

### Padrões Suportados

Para que a renderização do MobileSafari seja fiel ao Safari para desktop, ele tem grande suporte aos Padrões Web.

  * HMTML 4.01
  * HTML 5
  * XHTML 1.0
  * CSS 2.1
  * Parte do CSS 3
  * Javascript 1.4
  * Ajax
  * DOM

É interessante notar que temos uma certa liberdade de desenvolvimento web no iPhone. Há facilidades como cantos arredondados que não podemos contar no desenvolvimento focado para desktops. Isso tráz vantagens pra você, desenvolvedor, porque facilitará seu trabalho, e para o usuário porque ele terá uma experiência mais rica.

### Limites dos recursos

Embora o iPhone suporte as tecnologias mais atuais de desenvolvimento web, não podemos esquecer de que ele é um dispositivo móvel, com capacidade de processamento muito menor que a de um desktop. Por isso, há algumas limitações de recursos que devemos nos atentar.

Para códigos:

  * 10Mb para arquivos Javascripts e XML
  * O tempo de execução de um Javascript é limitado a 10 segundos. Se passar de 10 segundos, o Safari pára a execução em algum lugar aleatório do seu código.
  * Javascripts alocados limitados a 10Mb
  * Máximo de 8 documentos abertos de uma vez

Para imagens:

  * Limite máximo do tamanho de GIF, PNG e TIFF são 2 Megapixels
  * A decodificação máxima dos tamanhos de JPGs são 32 Megapixels. Utilizando SubSampling
  * O tamanho máximo de GIFs animados deve ser menor que 2MB. Para arquivos animados maiores, só é mostrado o primeiro frame.

Verifique sempre o tamanho final de sua página. Normalmente o sites com 30Mb para menos funcionam muito bem no iPhone.

 [1]: http://visie.com.br/campus/ "Vídeos tutoriais sobre Tableless"
 [2]: http://visie.com.br/campus/cadastrese
 [3]: http://visie.com.br/campus/iphone "Desenvolvimento web para iPhone"