---
title: Browser Targeting Version
authors: Diego Eis
type: post
date: 2008-01-25
url: /ie8-targeting-version/
tweetbackscheck:
  - 1356458420
shorturls:
  - 'a:3:{s:9:"permalink";s:45:"https://tableless.com.br/ie8-targeting-version";s:7:"tinyurl";s:26:"https://tinyurl.com/4ysu77x";s:4:"isgd";s:19:"https://is.gd/vAvgnb";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037878
categories:
  - Artigos
  - Browsers
  - Tecnologia e Tendências
tags:
  - Browsers
  - desenvolvimento web
  - firefox
  - html
  - internet explorer
  - metatags
  - xhtml

---
Para que possamos entender melhor o assunto do IE8 e como ele tratará as páginas, é bom que possamos entender o que houve no passado. Se você se lembrar bem como foi entre os anos de 1999, 2000 e 2001, provavelmente você vai lembrar que durante algum tempo, tínhamos que nos virar para garantir a total compatibilidade dos nossos sites em diversos browsers. Os principais eram o IE5, IE6, Firefox e Opera. Era uma época que &#8211; como no começo da bolha &#8211; estava tudo acontecendo ao mesmo tempo. Os Padrões Web estavam virando moda, os browsers, pelo menos os mais inteligentes, estavam se virando para suportar os Padrões<!--more-->, e os usuários ficando mais espertos e ativos na internet. Tudo era muito passível de erros de compatibilidade e renderização.

O principal caso era do Internet Explorer 5 e Internet Explorer 6. Os dois browsers tem uma renderização muito diferente. O Internet Explorer 6 tem um suporte melhor ao CSS do que o IE5. Isso causou um problema: pelo menos durante um certo tempo, nós tínhamos que prever a compatibilidade para o IE5. E agora, tínhamos que pensar também no Internet Explorer 6. Os dois renderizavam o CSS de formas bem diferentes, o que causou um certo dilema que foi resolvido com a seguinte solução: Chaveamendo de Doctype.

### O Chaveamento pelo Doctype

O DOCTYPE (Document Type Definition, DTD) serve para indicar qual o tipo do documento o browser está lendo. Ele define qual linguagem estamos utilizando e isso ajuda o browser a saber como ele deve tratar aquele código. O código DOCTYPE deve ser escrito em primeiro lugar no código HTML. Aqui eu falo [um pouco mais sobre o DOCTYPE][1].

A solução é seguinte: dependendo do DOCTYPE colocado no documento o browser renderiza da forma antiga, chamada de Quirks Mode ou em Strict Mode, que é o modo que o browser busca ter mais suporte com os Padrões. Isso é aplicado para o IE6. Se colocarmos um DOCTYPE XHTML 1.0 ou um HTML 4.01 o Internet Explorer 6 renderiza no modo esperto, se colocarmos um DOCTYPE de uma versão velha do HTML &#8211; como o HTML 3 &#8211; ou se não colocarmos o DOCTYPE, o IE 6, renderiza a página como o IE5, com menos suporte aos Padrões. Essa solução é feita para garantir uma certa retrocompatibilidade dos sites. Assim, o desenvolvedor que preferir manter a compatibilidade com o IE5, ele tem essa opção. Essa solução foi ótima no começo e felizmente o IE5 não demorou muito para sair de linha. Hoje é totalmente indicado que o desenvolvedor utilize um DOCTYPE novo (HTML 4.01 ou XHTML 1.0), que é a maneira mais correta de escrever HTML e que faz o IE6 renderizar melhor a página.

### O causo do IE8

O Internet Explorer 7 veio com muitas correções de CSS e trouxe outros problemas, mas teoricamente ele melhorou um bocado a nossa vida, pelo simples fato de que ele é um browser mais moderno e tem um suporte mais avançado que o IE6. Mesmo assim, o problema de retrocompatibilidade ainda existe: muitos sites era bem visualizados em IE6, mas quebravam quando visitados com o IE7.

O Internet Explorer 8 será muito mais diferente dos IEs passados. O pessoal que desenvolve o IE8 está criando um motor de renderização totalmente diferente. Ele já passa no [Test Acid 2][2] e promete ter o máximo de compatibilidade sobre o CSS 2.1. Isso é um problema.

Os problemas que os desenvolvedores enfrentam são muitos. A falta do suporte total das linguagens que usamos, traz problemas de interpretação dos padrões. É normal hoje em dia, que dois browsers, atualizados, tragam renderizações diferentes de uma mesma ação.

A solução que o pessoal da Microsoft, juntamente com o WaSP foi a seguinte: usando uma declaração de <a href=""https://tableless.com.br/metatags title="Para que servem as MetaTags?">metatag</a>, nós poderemos especificar a maneira que o motor de um browser como o IE8 deverá renderizar a página. O exemplo da metatag é o seguinte:

<pre><meta http-equiv="X-UA-Compatible" content="IE=8" />
</pre>

Isso faz com que o IE8 renderize a página utilizando o máximo de Padrões (lembre-se de que eles estão trabalhando para que o IE8 tenha suporte total ao CSS 2.1. Bem como o pessoal do Firefox 3 e Safari).

Esta meta será colocada no HEAD do documento. Isso pode ser incorporado em outros Browsers, dessa forma: 

<pre><meta http-equiv="X-UA-Compatible" content="IE=8;FF=3;OtherUA=4" />
</pre>

Para melhorar a velocidade de processamento do navegador, será importante priorizar esta metatag colocando, se possível, em primeiro lugar dentro da tag HEAD, antes das outras tags meta e não poderá ser incluído via Javascript DOM.

Um problema que pode causar é o seguinte: imagine que você coloque a metatag dizendo que o IE8 deverá renderizar aquele site da melhor maneira possível. Quando um IE9 for lançado, o site estará travado para o IE8. O IE9 não renderizará direito o site. O desenvolvedor deverá atualizar a metatag para o IE9.

### Minha opinião

Como tudo no desenvolvimento web, devemos esperar para ver. Não podemos prever muita coisa antes da efetivação dessa regra. Só iremos ter certeza dos resultados e os possíveis problemas, quando aplicarmos essa solução.

Mesmo assim, acho que tudo deveria ser nivelado por cima. Porque os desenvolvedores que se preocupam e utilizam os Padrões da maneira correta, são os que devem marcar o browser? Não seria mais fácil criar uma metatag para marcar os sites que não devem ser renderizados com o suporte avançado de Padrões? Quem deve se preocupar, são os desenvolvedores que não dão a mínima para os Padrões. Eles sim devem trabalhar para deixar seus sites atualizados.

Minha parte terrorista diz que provavelmente seria uma boa idéia quebrar a regra &#8220;Don&#8217;t Break the Web&#8221; e ver o que aconteceria com os sites que não estão nos Padrões. Talvez isso iria mobilizar clientes e desenvolvedores e forçá-los a dar mais crédito aos Padrões e a fazer atualizações estruturais no site. Normalmente os clientes não sabem e nem querem saber dos dilemas que passamos com a falta de compatibilidade. Faz parte do papel deles.

Não podemos esquecer da falta de informação dos usuários. Muitos nem sabem o que é &#8220;Navegador&#8221;. Ter uma maneira que os browsers deles fossem atualizados sem que eles mexessem um dedo seria uma forma interessante de ter a compatibilidade dos browsers sob controle. Os devenvolvedores teríam mais acesso às informações sobre o que mudou na renderização comparando com a versão anterior do browser. Isso facilitaria o trabalho de atualização e ajustes dos sites. Seria maravilhoso, se o mundo fosse perfeito. Mas&#8230; 

**(09/03/08) UPDATE: [E a Microsoft mudou de idéia][3].**

 [1]: https://tableless.com.br/escrevendo-um-xhtml-valido "Escrevendo um XHTML válido"
 [2]: https://webstandards.org/action/acid2/ "Teste de suporte aos Padrões"
 [3]: https://tableless.com.br/ie8-o-sonho-nao-acabou "A Microsoft mudou de idéia quanto ao Browser Targeting"