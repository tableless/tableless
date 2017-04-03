---
title: Entrevista com Bert Bos (Criador da CSS) e W3C
author: Diego Eis
type: post
date: 2016-09-14
url: /entrevista-com-bert-bos-e-hakon-wium-lie-criador-da-css-e-w3c/
categories:
  - Artigos
  - CSS
  - Tecnologia e Tendências

---
Na [8ª edição da Web.br][1] teremos a presença ilustre de Bert Bos como keynote speaker. Ele, junto com [Håkon Wium Lie][2], foram os dois inventores dos Cascading Style Sheets, tecnologia também conhecida pela sigla CSS. Bert trabalha no W3C desde 1995 com desenvolvimento e padronização do CSS, assim como de outros padrões da web, como HTML, XML e MathML. Nessa entrevista ele descreve o contexto que o levou a trabalhar nos primeiros rascunhos do padrão CSS, o que ainda falta ser aprimorado e sua perspectiva para a evolução do CSS e do HTML a longo-prazo.

**1. Quais eram as necessidades específicas e o contexto que o levaram a trabalhar nos primeiros rascunhos do padrão CSS ?**

Quando Tim Berners-Lee criou seu primeiro navegador Web, este possuía folhas de estilos, mas apenas para o usuário. A ideia era que o autor especificasse o conteúdo de um documento, mas que o navegador junto com o usuário determinassem como melhor exibi-lo.

Durante certo tempo, esse foi o modelo, afinal de contas, o usuário é quem melhor sabe qual tipo de tela ele tem, de quais cores ele gosta mais, o quão grande são as janelas em seu sistema. Foram criados diversos outros navegadores que permitiam ao usuário configurar a exibição do conteúdo, como o [Viola][3] e o [Mosaic][4]. Eu mesmo criei também um navegador dessa forma, chamado [Argo][5]. As folhas de estilo no meu navegador eram mais poderosas, mas ainda assim apenas para o usuário, e não para o autor.

Os primeiros autores na Web eram em sua maioria cientistas. Eles estavam acostumados a escrever documentos e deixar outra pessoa decidir sua aparência: jornais científicos normalmente fornecem suas próprias folhas de estilo (em [LaTeX][6], por exemplo), assim o HTML se encaixou bem nesse modelo.

Mas conforme a Web se tornava mais popular, designers começaram a se interessar e a opinião deles era de que, por serem designers, eles sabiam com mais propriedade que os usuários como apresentar um documento da melhor forma. Assim como a aparência de um livro lhe informa sobre que tipo de livro se trata, a aparência de um documento deveria também lhe dizer algo sobre seu conteúdo.

Mas, naquela época, em 1994, isso era impossível de se fazer usando HTML. Assim, duas coisas aconteceram: os designers perceberam que o HTML permitia o uso de imagens, e então eles começaram a substituir textos por imagens, porque assim eles tinham total controle. E o Netscape, o primeiro navegador comercial, notando essa demanda dos designers, começou a adicionar extensões proprietárias ao HTML, como atributos de cor e de plano de fundo, um elemento <center>, e elementos de espaçamento.

Os usuários não estavam felizes com isso: você não pode redimensionar imagens ou recortar e colar partes delas, e imagens também não proviam acessibilidade. E os elementos proprietários faziam os documentos ficarem grandes e difíceis de serem mantidos, e mais difíceis para o usuário aplicar estilos. E, assim, pessoas na lista de discussão www-talk@w3.org começaram a procurar soluções.

Se você quiser ler a história completa do que aconteceu naquela época, você pode ler o [capítulo relevante no livro que Håkon e eu escrevemos][7] ou a [tese de PhD do Håkon][8]. Em suma: diversas pessoas propuseram linguagens de folhas de estilo, algumas eram novas, e outras eram versões simplificadas do que já existia no mundo do SGML, por que o HTML foi derivado do SGML. Duas dessas linguagens eram a “Cascading HTML Style Sheets” do Håkon e a minha linguagem “Streaming Style Sheets”.

Quando eu olhei para a linguagem do Håkon, eu vi uma ideia interessante, que era a de que você poderia ter um tipo de negociação entre o que o autor propunha e o que o usuário queria. Nós começamos a trabalhar juntos, combinando as ideias dele e as minhas (por exemplo, seletores contextuais e a aplicação de folhas de estilos para outros tipo de documento além de HTML), nós inventamos uma nova sintaxe e logo nossa proposta (chamada “Cascading Style Sheets” omitindo o “HTML” do nome) se tornou a mais popular, e outras pessoas começaram a contribuir.

Em 1995, o novo grupo de trabalho de HTML assumiu a tarefa, de modo a torná-lo um padrão. E um pouco depois o grupo se separou, formando o grupo de trabalho de CSS existente ainda hoje.

**2. Você já considerou aplicar regras de estilo CSS em outros tipos de conteúdo (além de HTML)? Se isso já foi feito, você poderia fornecer um exemplo? Caso contrário, você poderia discutir em que outros conteúdos poderia ser útil o uso de CSS?**

Uma das ideias da minha proposta original de folhas de estilo era justamente isto: usar a mesma linguagem de folhas de estilo para uma ampla gama de documentos, não apenas para HTML (meu próprio navegador podia exibir muitos documentos SGML, e HTML era apenas uma subclasse destes).

Naquela época, ainda não existia XML, mas nós pensamos que deveríamos ter uma linguagem de folhas de estilo para SGML simples ou qualquer coisa que tivesse uma estrutura simples de árvore.

Quando o XML foi criado um pouco depois (pesquisa iniciada em 1996, com a publicação do padrão em 1998), acabou combinando muito bem com o que tínhamos em mente e assim o CSS pôde ser utilizado com grande parte de documentos XML também.

E o CSS pode ser usado, e está de fato sendo usado, para outras coisas também. Um exemplo é a biblioteca de interfaces gráficas [Qt][9]. Ela usa CSS para aplicar estilo aos componentes da interface gráfica ([http://doc.qt.io/qt-5/][10]). Outro exemplo é o MapCSS, usado por diversos programadores para desenhar mapas cartográficos ([http://wiki.openstreetmap][11]).

**3. Quais partes da atual versão da estecificação do CSS você acha que ainda precisa de mais aprimoramentos?**

Tem muitas coisas que ainda estão faltando, especialmente agora que editores estão usando CSS fortemente para editoração de livros, tanto em papel quanto para e-books.

Originalmente nós desenhamos o CSS para ser a linguagem de estilos simples, e adicionamos XSL (por exemplo, XSLT + XSL-FO) em 2001 para as tarefas complexas, como edição de livros. Mas, no momento, o desenvolvimento do XSL parou, e nós não sabemos quando ele irá continuar, e então os editores estão migrando para o CSS.

Apenas para dar alguns exemplos de coisas que estão faltando no CSS: para o tratamento adequado de hipertexto, nós precisamos de elementos colapsantes (veja [aqui][12]) ou, de modo geral, uma forma de alternar o estado de elementos (e não apenas ‘checkboxes’) entre dois possíveis estilos. Nós também não temos ainda containers que formem um conjunto de páginas em abas.

E temos \*muito\* trabalho a ser feito para tudo que envolva texto paginado: notas de rodapé, elementos flutuantes no topo ou no pé da página, texto que se estenda atravessando colunas, divisão de texto em múltiplos fluxos e alinhamento desses fluxos de texto em um template de página baseado em uma grade, referências cruzadas (como “veja página 7″), índices alfabéticos, ‘copyfitting’ (fazer um texto caber exatamente em um espaço alocado), cabeçalhos e rodapés contendo texto bidirecional ou fórmulas matemáticas etc. Eu comecei a colecionar uma lista de requisitos que pode ser vista [aqui][13].

Existem propostas e implementações experimentais para algumas dessas funcionalidades, mas grande parte do trabalho ainda não foi realizado.

**4. Qual é a sua perspectiva para a evolução do CSS e do HTML em longo prazo? Como você acha que essas tecnologias evoluirão nas próximas décadas?**

Foi muito bom o HTML4 ter permanecido sem modificações por tanto tempo. Isso nos permitiu compreendê-lo e criar softwares interessantes. Nós esperávamos certos tipos de aplicações, mas algumas vezes levou muitos anos para que as pessoas se tornassem capazes de efetivamente criá-los. Por exemplo, nós esperávamos que algo como os microformatos fosse surgir, mas levou bastante tempo até algumas pessoas de fato descobrirem como fazê-lo corretamente. E algumas coisas foram inesperadas e apenas descobertas depois.

Então, de certa forma, é uma pena que agora nós tenhamos que migrar nossos softwares para o HTML5, mesmo que o HTML5 adicione novas funcionalidades interessantes. Eu estou lentamente migrando meus softwares, mas levará um bom tempo até que eu possa fazer com o HTML5 o que eu posso fazer com o HTML4. Assim, estou esperançoso de que grande parte de tudo o que é o HTML5, ou sua próxima revisão, volte a permanecer estável por 10 ou 15 anos.

Para o CSS, não tenho muita certeza sobre o que quero. Como visto acima, há várias coisas que precisamos adicionar para satisfazer os vários novos usos. Mas o CSS não foi desenhado para tarefas complexas. Ele foi feito para ser usado por usuários comuns para aplicação de estilos simples. Ao adicionar novas capacidades ao seu modelo original, o CSS está se tornando complexo demais para a maioria das pessoas. Então talvez seja o momento de se recomeçar do zero criando duas novas linguagens: uma simples que todas as pessoas saibam usar, mas que talvez seja limitada na quantidade de controles detalhados que oferece, e uma avançada, adequada até mesmo para editoração complexa de livros e revistas. Mas eu ainda não vi nenhuma proposta que tenha me agradado.

É bom ver diversos pré-processadores de CSS para ajudar os usuários avançados, como o [SASS][14] e o [LESS][15]. Eu tinha esperança de eles aparecessem mais cedo. Espero que eles se desenvolvam e se tornem ainda melhores. Por outro lado, estou surpreso com o tamanho de algumas folhas de estilo que as pessoas têm criado. As mais complexas que eu mesmo criei têm 10 kbytes, e a maioria é bem menor que isso. Fico me questionando se eles estão fazendo a coisa certa…

Dessa forma, em termos práticos, acho que ainda iremos adicionar novas funcionalidades ao CSS durante os próximos poucos anos. Haverá, sem dúvidas, novos módulos no CSS3, e alguns módulos que já estão finalizados serão provavelmente estendidos ou substituídos por um módulo do CSS4.

Continuaremos mantendo a retrocompatibilidade do CSS, mas isso também significa se tornará gradativamente mais difícil de adicionar novas funcionalidades a ele, e suas sintaxes poderão não ser as mais intuitivas.

 [1]: http://conferenciaweb.w3c.br/
 [2]: https://en.wikipedia.org/wiki/Håkon_Wium_Lie
 [3]: https://en.wikipedia.org/wiki/ViolaWWW
 [4]: https://en.wikipedia.org/wiki/Mosaic_%28web_browser%29
 [5]: https://en.wikipedia.org/wiki/Argo_%28web_browser%29
 [6]: https://en.wikipedia.org/wiki/LaTeX
 [7]: http://www.w3.org/Style/LieBos2e/history/
 [8]: http://people.opera.com/howcome/2006/phd/
 [9]: http://qt-project.org/doc/qt-4.8/stylesheet.html
 [10]: http://doc.qt.io/qt-5/stylesheet.html
 [11]: http://wiki.openstreetmap.org/wiki/MapCSS
 [12]: http://en.wikipedia.org/wiki/StretchText
 [13]: http://www.w3.org/Style/2013/paged-media-tasks
 [14]: http://en.wikipedia.org/wiki/Sass_%28stylesheet_language%29
 [15]: http://en.wikipedia.org/wiki/LESS_%28stylesheet_language%29