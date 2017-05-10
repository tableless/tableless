---
title: Webkit to the people
author: Diego Eis
type: post
date: 2013-03-18
excerpt: Entenda por que a monocultura do Webkit pode ser ruim. Ou não.
url: /webkit-to-the-people/
dsq_thread_id: 1145397753
categories:
  - Browsers
  - Código
  - Mercado e Comportamento
  - Tecnologia e Tendências
tags:
  - 2013
  - Browsers
  - w3c
  - webkit

---
Eu sei que a notícia é velha, mas o Opera [anunciou que chegou aos 300 milhões de usuários][1] em todo mundo. 

Muita gente brinca que o Opera é o browser que ninguém usa. De fato os números do browser para desktop são bem pequenos quando comparamos com browsers como Firefox e Chrome. Mas o que ninguém pensa com muita frequencia é que o Opera está presente em uma série de outros dispositivos além do desktop. Há pessoas que dizem que o Opera nunca teve como foco principal os desktops. Eu não concordo. Mesmo assim, ele está presente em dispositivos como TVs, set-top-box e [até em caminhões][2]. [Ou pelo menos estava][3].

Junto com a notícia dos 300 milhões de usuários, eles anunciaram que iniciarão uma transição de substituição do seu engine de renderização. Eles deixarão o Presto de lado e passarão a usar o WebKit! Yeah! 😉

Na verdade não é tão Yeah! assim. Existem prós e contras. Pra ser sincero eu ainda não decidi se isso é bom ou ruim. O assunto é mais &#8220;profundo&#8221; do que se imagina. É tão profundo que há pessoas como o Tim Berners-Lee contra vários browsers utilizarem o mesmo motor de renderização.

## Web aberta

A web foi criada para ser aberta. Para termos realmente o direito de ir e vir. [A internet é neutra][4]. Isso quer dizer que todas as informações que trafegam na web devem ser tratadas igualmente. Nada de bloqueios ou restrições de acesso a informação, seja ela qual for. Você deve ter o direito de acessar da forma que quiser qualquer informação disponibilizada na web. É por isso que todas as [iniciativas de controlar o que e como consumimos conteúdo][5] na web não foram adiante. A web não é de ninguém, mas é de todo mundo ao mesmo tempo.

Isso é importante por um simples motivo: informação acessível. Toda informação que é publicada na web deve ser utilizada e reutilizada por qualquer um, quantas vezes quiser. O Google e outros sistemas de busca faz isso o tempo todo no seu buscador. Você faz isso quando twitta, quando posta no Facebook ou quando manda um simples artigo por email.

> Admittedly, this news would have been considerably more worrying had Microsoft or Mozilla adopted Webkit. We still have three major HTML5 engines but the browser world has lost a little of its color today. [Craig Buckler][6]

O W3C tem lutado para que empresas e governos mantenham seus dados abertos e acessíveis. O Tim Berners-Lee, quando veio para a [Campus Party aqui no Brasil em 2011][7], falou um pouco sobre este assunto.

> Há governos e empresas que estão tentando controlar as informações ou cobrar por elas. É importante que todos nós lutemos para que a rede continue aberta e livre.

Para citar um exemplo besta: quem nunca entrou em algum website de notícias onde você não pode clicar com o botão direito por que ele é travado por um script? Uma decisão tão estúpida que chega a ser hilário.

Claro que não estamos dizendo aqui que toda e qualquer informação deva ser publicada para o uso de qualquer um. Se você já estudou sobre Web Semântica, deve saber que existe um termo utilizado chamado [Provenance][8], que define de onde vem os dados e o que pode ser feito com eles. Os padrões da Web Semântica determina como você pode manipular esses dados e quais são seus direitos de acesso.

Tanto a utilização quanto a publicação de dados na internet deve ser feita com responsabilidade. Embora a internet seja um ambiente de livre acesso, ninguém quer que dados importantes da sua vida estejam livres para qualquer um manipular da maneira que bem entender.

Mas para que a web seja livre de verdade, a internet não pode ser controlada, de forma nenhuma, apenas por uma empresas, órgão, pessoa etc etc etc. Na época da guerra dos browsers esse cenário era muito clara: se uma empresa fizesse um browser que fosse muito utilizado, ela poderia ter possibilidade de tentar e até conseguir, controlar o que os usuários desse browser acessassem. Era isso que a Microsoft pensava, pelo menos. Eles viram que se a Netscape ganhasse a tal guerra, eles teriam muito &#8220;poder&#8221; nas mãos.

A mesma ideia pode se aplicar agora se todos os browsers decidirem migrar para o WebKit. Praticamente quem decidirá quais novidades dos padrões web devem ser implementados agora, será o grupo que cuida do WebKit e não os fabricantes browsers.

O desenvolvedor Robert O’Callahan disse por que a adoção em massa do WebKit pelos browsers pode não ser uma boa coisa:

> some people are wondering whether engine diversity really matters. &#8220;Webkit is open source so if everyone worked together on it and shipped it, would that be so bad?&#8221; Yes. Web standards would lose all significance and standards processes would be superseded by Webkit project decisions and politics. Webkit bugs would become the standard: there would be no way for developers to test on multiple engines to determine whether an unexpected behavior is a bug or intended.

Olha só o que o Tim Berners-Lee retuitou estes dias:

<blockquote class="twitter-tweet">
  <p>
    If you think a WebKit monoculture is good for web developers or the Web, you’re incredibly short-sighted (and likely inexperienced), sorry.&mdash; Lea Verou (@LeaVerou) <a href="https://twitter.com/LeaVerou/status/301727973273391104">February 13, 2013</a>
  </p>
</blockquote>

Não estou dizendo que ter todos os browsers sob um mesmo motor de renderização não iria melhorar nossas vidas, por que sem dúvida, iria. O problema é que isso não é bom para web, entende? Embora seus problemas de compatibilidade entre browsers diminuiriam para quase zero, a web não iria ter a liberdade que ela merece.

imagina se uma empresa que tem dinheiro infinito (posso pensar em pelo menos duas, uma delas tem um sistema de busca e a outra iniciou o projeto do Webkit), coloca centenas de desenvolvedores para &#8220;ajudar&#8221; a desenvolver o Webkit. Será, será mesmo, que uma empresa dessas estaria fazendo isso só para ajudar todo mundo? Don&#8217;t be evil my ass, alguns diriam.

Tem pessoas que [pensam que a monocultura de motores de renderização não é uma má ideia][9] e defendem que os browsers não competem entre si apenas pela quantidade de padrões que cada um suporta. E eu concordo. Hoje em dia a experiência que o usuário tem com a interface de cada browser pode ser definitiva para a escolha. Há outros aspectos de decisão que podem ser explorados com mais vigor, como por exemplo a forma com que o browser gerencia suas senhas e contas ou como ele sincroniza seu perfil entre os dispositivos, gerenciamento de bookmarks ou sincronização com serviços e redes sociais. Há estes e vários outros campos onde os browsers podem competir e que talvez seriam mais interessantes para os usuários.

Eu mesmo já me peguei várias vezes desejando que todos os browsers tivessem o mesmo motor de renderização só por causa de um ou outro problema na hora do desenvolvimento. Imagina só, não precisaríamos nos preocupar em utilizar prefixos de browsers ([esta é outra guerra][10]). Também atingiríamos um número maior de browsers com um mesmo código, já que Chrome, Opera, Safari e suas respectivas versões mobiles estariam sob o mesmo motor de renderização. Sem falar em mobiles como Blackberry.

Essa história ainda vai dar o que falar quando o Opera anunciar sua primeira versão com Webkit. Qual é a sua opinião?

 [1]: http://www.opera.com/press/releases/2013/02/13/
 [2]: http://techcrunch.com/2009/04/02/opera-browser-chosen-for-mobile-office-computer-in-ford-pickup-trucks/
 [3]: http://business.opera.com/press/releases/2009/04/02_2/
 [4]: http://pt.wikipedia.org/wiki/Neutralidade_da_rede
 [5]: http://tecnologia.terra.com.br/internet/google-e-casa-branca-somam-46-mi-de-assinaturas-contra-sopa,a6a8fe32cdbda310VgnCLD200000bbcceb0aRCRD.html
 [6]: http://www.sitepoint.com/opera-switches-to-webkit-rendering-engine/
 [7]: http://revistagalileu.globo.com/Revista/Common/0,,EMI203321-17770,00-AL+GORE+E+TIM+BERNERS+LEE+FALAM+SOBRE+LIBERDADE+DE+INFORMACAO+NA+CAMPUS+PAR.html
 [8]: http://www.w3.org/2005/Incubator/prov/wiki/What_Is_Provenance
 [9]: http://braintrace.ru/posts/2013-02-14-opera-and-webkit-good-or-bad.html
 [10]: http://tableless.com.br/prefixos-dos-browsers-a-web-precisa-de-voce/