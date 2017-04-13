---
title: Internet Explorer dá lugar para o sucessor
author: Diego Eis
type: post
date: 2015-03-25
excerpt: Entendendo um pouco mais sobre novo browser Spartan e seu novo motor de renderização.
url: /internet-explorer-da-lugar-para-o-sucessor/
categories:
  - Browsers
  - Tecnologia e Tendências
tags:
  - ie
  - internet explorer
  - microsoft browser
  - spartan

---
Não é de hoje que a Microsoft tem mudado sua forma de pensar em vários assuntos ligados ao desenvolvimento web. Agora, a última novidade, é que você vai parar de ouvir o nome Internet Explorer nos próximos anos. 

A Microsoft revelou que está planejando uma nova marca e um novo nome para um browser para Windows 10. O codenome do browser é Projeto Spartan. O novo browser Spartan será o browser padrão no Windows 10. Em Janeiro a Microsoft já tinha comentado sobre o [novo motor de renderização][1] que irá fazer parte deste novo browser e muito possivelmente no IE também.

Spartan é um browser desenhado para trabalhar entre os diversos dispositivos que rodam Windows 10, desde aparelhos com mouse até touch, gestos, vozes, controles, sensores etc.

<img src="http://tableless.com.br/uploads/2015/03/1541.project-spartan-diagram.gif" alt="1541.project-spartan-diagram" width="739" height="370" class="alignnone size-full wp-image-47933" />

A ideia do Internet Explorer é que ele seja usado apenas para motivos de legado e compatibilidade. Não está ainda muito claro como o IE fará parte do Windows 10 ou se ele será apenas direcionado para versões corporativas. O que eles deixam claro é que o Internet Explorer não fará mais parte do futuro da Microsoft.

<img src="http://tableless.com.br/uploads/2015/03/7041.psatwjpb-image4.png" alt="7041.psatwjpb-image4" width="924" height="700" class="alignnone size-full wp-image-47934" />

O que o novo browser e o novo motor de renderização significa para os Devs?

  1. O novo motor Spartan será default no Windows 10, no Spartan e possivelmente no Internet Explorer. O motor será interoperável e o suporte e o roadmap pode ser visto aqui: <http://status.modern.ie>
  2. Os sites serão renderizados pelo novo motor, usando os padrões modernos. Os comportamentos específicos do Internet Explorer não serão suportados no novo motor. Se seu site depende do IE para funcionar, a Microsoft encoraja fortemente que você mude para os padrões mais modernos. Isso quer dizer que os famosos Hacks e possivelmente o prefixo **-ms-** não funcionarão.
  3. O objetivo da Microsoft é a interoperabilidade com os browsers mais modernos. Você pode testar o novo motor via <http://remote.modern.ie>.

A ideia é não ficar em pânico. Eu aconselho esquecer o Spartan até que ele comece a pipocar no seu analytics e ainda assim mantenha em mente a compatibilidade de dois IEs antigos. Eu sempre suporto o IE mais novo, no caso hoje o 11, e duas versões anteriores, ou seja, o IE 10 e 9.

Se for para melhorar nossa vida, mesmo que seja daqui há alguns anos, não importan, eu voto pelo sucesso do novo Spartan.

 [1]: http://blogs.msdn.com/b/ie/archive/2015/01/22/project-spartan-and-the-windows-10-january-preview-build.aspx