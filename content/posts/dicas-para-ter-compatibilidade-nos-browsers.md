---
title: Dicas para ter compatibilidade nos browsers
author: Diego Eis
type: post
date: 2007-11-30
url: /dicas-para-ter-compatibilidade-nos-browsers/
tweetbackscheck:
  - 1356392508
shorturls:
  - 'a:3:{s:9:"permalink";s:67:"http://tableless.com.br/dicas-para-ter-compatibilidade-nos-browsers";s:7:"tinyurl";s:26:"http://tinyurl.com/44fvbok";s:4:"isgd";s:19:"http://is.gd/vMOVgb";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037660
categories:
  - Artigos
  - Geral
  - Tecnologia e Tendências

---
Estava lendo o [artigo do Fugita][1] e pensei comigo mesmo: &#8211; Porque todo mundo sempre quer matar o Internet Explorer?
  
A pergunta não foi difícil de responder: Compatibilidade.

Quando desenvolvemos com Padrões Web, a primeira coisa que aprendemos é a odiar o Internet Explorer. Sei disso porque a frase mais falada nos meus cursos e em algumas palestras é: Não funciona no IE6. Ou: Se funcionasse no IE6.
  
Grande parte dos problemas de desenvolvimento de um site se deve pela falta de compatibilidade entre browsers.

Infelizmente não posso dizer: &#8211; Esqueça o IE6.
  
Ele é até hoje o browser mais usado, &#8211; não por mérito, mas isso é outra história &#8211; portanto, viveremos por um tempo com a falta de compatibilidade e alguns bugs não só do IE, mas de todos os browsers. Mesmo assim, há maneiras de minimizar os problemas:

### Graceful Degradation

Para quem não sabe, isso é uma premissa do desenvolvimento com Padrões Web. Este assunto é bem interessante. A idéia é a seguinte: existem diversos dispositivos, aparelhos e softwares que podem acessar sua aplicação web ou site. Acontece que cada destes meios tem sua limitação, seja uma limitação de software ou hardware. Mesmo assim, seu site precisa funcionar quando for acessado por eles. Se você faz um site com PNG semi-transparente, que não funciona no IE6, os usuários do IE6, precisam utilizar o site sem problemas. Se você faz seu site em flash e o camarada entra no site com algum SmartPhone que não funciona flash, seu site precisa funcionar de alguma maneira alternativa.

A moral da história é a seguinte: faça o site funcionar da melhor maneira possível para aquele meio de acesso. Você precisa dar a melhor experiência para aquele usuário. Mesmo que tenha que abrir mão de algumas coisas, como design, por exemplo. O importante é que funcione.

Logo, o usuário de desktop terá uma melhor experiência que o usuário de Smartphone. Mesmo assim, o usuário de smartphone terá a melhor experiência que o seu aparelho pode lhe trazer.

### Entenda e estude a solução dos bugs

É mentira que apenas o IE6 tem bugs. Mas é fato que o IE6 é campeão em número de bugs. O remédio para contornar os bugs é sempre saber mais de uma técnica para fazer a mesma coisa. Acredite, sempre há mais de uma alternativa com CSS.

O mais importante é conhecer soluções simples, que não lhe tragam trabalho posteriormente. Se você sabe que determinada combinação de propriedades pode gerar algum tipo de bug em determinado browser, tente uma maneira alternativa. Crie, invente, converse com outras pessoas, pesquise. Se mesmo assim não houver jeito, use CSS HACK, mas apenas em ÚLTIMO CASO!

### CSS HACKS, use com moderação

Vou ser sincero: CSS HACK pode fazer sua vida virar o inferno. Não estou brincando. Use com moderação. Com cuidado, com inteligência.

Grande parte dos desenvolvedores não gostam de perder seu precioso tempo tentando entender o problema para achar uma solução inteligente. Acabam usando CSS HACK par a resolver um problema imediato e acabam se acostumando mal. Sou a favor de perder tempo procurando a solução, mesmo naquelas horas apertadas e que cliente respira fundo no seu cangote. Você vai trabalhar duro apenas uma vez para nunca mais perder tempo com aquele problema.

Repita comigo: CSS HACK apenas em último caso.

Hoje, felizmente é possível fazer sites complicadíssimos sem utilizar CSS HACKS. Na maioria das vezes o uso do Hack é necessário por causa de um problema anterior: o código complicado.

### Seja simples

Pense quantas vezes for necessário. Se você resolveu um problema com 3 divs, tente resolver com apenas 2. Se resolveu com 2, tente resolver com 1. Apenas se não conseguir, volte para 2 divs. E assim você faz com o resto do site. Quanto menos código HTML, melhor. Mas lembre-se, o pouco código HTML que você escrever, precisa ter significado. A semântica ajuda bastante neste sentido. Escrevendo código semântico, você garante que o código escrito será mínimo e significativo para sistemas de busca e outras aplicações que dependam da semântica para funcionar.

Escrever código demais é herança da metodologia antiga, onde nós escrevíamos uma gambiarra atrás de outra. Onde colocávamos tabelas em todos os lugares. Lembre-se que tudo mudou. Você tem que mudar também e o desenvolvimento apenas muda se você mudar sua maneira de pensar. Pense simples. Reaprenda o que puder e esqueça o antigo.

### Visualize o resultado no próprio browser.

Outro costume terrível nosso é visualizar o resultado nos previews nojentos dos editores. Geralmente estes previews são baseados em apenas um browser, normalmente o browser padrão. Há uma opção de mudar o preview para o browser que você que quiser. Mesmo assim, pense comigo: Você sabe qual será o browser do visitante? Você sabe, na melhor das hipóteses que ele pode navegar com pelo menos 4 browsers: Firefox, IE, Safari e Opera. Isso se ele usar Windows. Portanto, não tem sentido utilizar o preview do editor.

Minha sugestão é a seguinte: abra os principais browsers e visualize a implementação ao mesmo tempo.
  
Eu abro Firefox, IE e Safari (de vez em quando). A cada modificação no CSS e no HTML, eu aperto F5 em cada um deles e vejo o resultado. Se percebo algum erro, já corrijo e sigo em frente. Nunca deixo para visualizar em todos os browsers depois que termino a implementação. Esso é um método muito perigoso. Você procrastina todos os problemas que você teve para o final. Isso pode gerar problemas irreversíveis e na maioria das vezes, quando acontece, é mais fácil recomeçar.

Lembre-se de que com Padrões Web ficou tudo mais fácil.
  
Era tudo muito mais difícil quando tentávamos desenvolver com padrões, mas nenhum browser suportava grane parte dos métodos. Hoje, todos estão interessados em ter suporte com os padrões e felizmente os browsers estão mais espertos.
  
O jeito é estudar, estudar e estudar. Pelo menos se você quiser ser um bom profissional.

 [1]: http://www.techbits.com.br/2007/11/29/vamos-matar-o-ie6/