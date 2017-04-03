---
title: Organizando equipes
author: Diego Eis
type: post
date: 2015-10-20
excerpt: Sobre organizar equipes multifuncionais em uma empresa gigante.
url: /organizando-equipes/
categories:
  - Artigos
  - Mercado e Comportamento

---
Não existem muitas maneiras de organizar um time de desenvolvimento, eu posso citar basicamente duas: ou você agrupa os integrantes de acordo com suas funções, formando os famosos times “funcionais” (ou silos), ou você organiza os times agrupando os integrantes que tenham funções diferentes, formando times multifuncionais.

Faz quase 4 anos que eu trabalho em uma empresa que tem muitos produtos. Cada projeto tem um P.O (Product Owner), seguido de um time de desenvolvedores back-end. As pessoas que fazem UX, Front-end e QA forma times funcionais, recebendo e entregando demandas específicas para os projetos. Mas desde ontem decidimos mudar: o time de front-end está se dividindo e por isso cada integrante do time está indo fazer parte dos times dos projetos. É o primeiro passo para criarmos uma organização com times multifuncionais.

Isso quer dizer que eu deixo de ser coordenador de um time específico de front-end e inicio uma nova jornada sendo coordenador de um time de desenvolvimento multifuncional.

## Times funcionais

Os integrantes desses times geralmente se comunicam muito bem. Eles falam e fazem as mesmas coisas, participam dos mesmos eventos, tem os mesmos interesses. Melhorar a motivação e a capacidade técnica dos integrantes de times funcionais é relativamente simples já que eles exercem a mesma função e falam o mesmo idioma. Coloque um desenvolvedor front-end junto de outro desenvolvedor front-end e você verá suas capacidades amadurecerem e as metodologias de trabalho dentro de sua função evoluírem. Isso vai acontecer com back-ends, com os UX etc. Isso é muito bom, já que eles evoluem juntos, resolvem problemas juntos e fazem parte de uma mesma tribo.

Contudo, esses times tem seus próprios objetivos, que quase sempre diferem dos objetivos dos times dos produtos, como por exemplo entregar mais rápido as demandas, definir um padrão de escrita de código e definir um métodos de comunicação com outras equipes, só pra citar alguns. Como geralmente os integrantes do time funcional interagem com mais de um projeto por vez, é muito raro que eles compartilhem os mesmos objetivos de negócio dos projetos, por um motivo simples: é muito difícil que eles se sintam parte do time do projeto. Geralmente há um sentimento de que estão de passagem… que são forasteiros por ali. Na verdade, os P.Os e os integrantes do time do produto também os enxergam dessa maneira. Por isso nenhum deles quer estabelecer uma relação mais profunda, pois sabem que dali algum tempo, essa relação vai se quebrar e o produto vai sofrer com a saída de um integrante, que na verdade, nunca fez parte de verdade do time do produto. É aí que o projeto perde conhecimento e capacidade técnica.

Mas em times assim, as demandas escalam melhor. Mesmo para um time pequeno, dependendo da área e da forma com que o time é gerido, as demandas podem ser entregues rapidamente. Obviamente há um limite de demandas que esse time pode receber até que se crie filas de entregas. Nesse caso, a priorização fica prejudicada, porque o gestor do time funcional é quem decide qual dos projetos é mais ou menos importante. Essa decisão não fica na mão do P.O ou do Gerente do Projeto. O que é ruim, já que eles conhecem mais do seu próprio projeto. Alguém vai sofrer e esperar na fila.

Esse formato também favorece bastante o conceito de [waterfall][1]: onde o processo de desenvolvimento é mais linear e muito menos paralelo, onde o produto depende da finalização de tarefas de outros times antes que o próximo possa por a mão na massa.

Você pode trabalhar de várias maneiras para minimizar os problemas de comunicação e de entrega mas é um formato que precisa de “manutenção” o tempo inteiro. Você sempre vai cair nos problemas de priorização, falta de braço e troca frequente de projetos entre os integrantes do time.

## Times Multifuncionais

Em times multifuncionais, misturamos profissionais que exercem várias funções necessárias para que aquele projeto saia do papel. Eles trabalham para entregar o mesmo valor para o negócio. Eles correm atrás de um mesmo objetivo. Eles falam de um mesmo produto, de um mesmo cliente, de uma mesma feature.

Geralmente projetos formados por times multifuncionais são mais independentes, dessa forma eles não precisam esperar por times externos, facilitando na tomada de decisões inerentes do projeto. Aqui o trabalho pode ser feito de forma mais paralela e em conjunto.

> In fact, having only one front-end developer in a team with other **developers doing only server-side** work is a recipe for disaster. _[Don Roby][2]_

O problema nos times multifuncionais é que a expertise de cada função pode ser prejudicada. É comum existirem mais desenvolvedores back-end em um time do que os integrantes de outras funções. Isso é bom para eles pois as decisões de back-end são feitas em grupo. Agora, pegue como exemplo um time multifuncional, que tem apenas um front-end. Nesse caso, quem decide quais seus padrões de código? Qual o pattern de JavaScript será usado? São decisões difíceis de serem tomadas e com certeza se houver somente um cara no time, ele vai decidir pelo gosto pessoal. Esse é o começo do caos. Isso pode se agravar se houver um front-end contra vários back-ends “pró-ativos”, escrevendo código JS e metendo o bedelho no CSS, o código front-end vira um inferno. Sério. Nesse caso, o meu conselho é igual ao de muita gente: é bom que cada função seja exercido por pelo menos uma dupla. As decisões tomadas são baseadas na carga de conhecimento e experiência de duas pessoas, onde não há espaço para gosto pessoal.

Agora, não há apenas um time multifuncional em uma empresa. Existem vários outros times espalhados, com mais ou menos a mesma estrutura de funções. Nesse caso, é muito mais interessante que os integrantes desses times, que exercem as mesmas funções, se comuniquem. Aí é que entra algo chamado Grupos de Interesse. Se esse caso for em uma empresa que tem vários times multifuncionais, os integrantes de cada time que exercem a mesma função (por exemplo, todos os front-ends dos diferentes projetos), se juntam para definir discutir e solucionar problemas comuns entre os projetos, de forma que o objetivo final seja estabelecer um padrão comum entre todos os projetos.

## Comunicação

A comunicação dos times nos dois formatos são bem difíceis. Mas a comunicação é a parte crucial em qualquer uma das duas variações. Pessoas com diferentes funções, mas que trabalham no mesmo projeto, precisam se comunicar com mais frequência com pessoas que tem as mesmas funções em projetos diferentes.

É imprescindível que quando há mais do que um time em uma empresa, os integrantes desses times se comuniquem para se organizar e decidir as soluções de problemas comuns. Todos os times podem decidir juntos qual a melhor forma de fazer o deploy dos projetos, por exemplo. Isso não precisa ser uma decisão individual de cada time. Se assim fosse, todos os times tentariam resolver sozinhos os mesmos problemas. Não faz sentido. É muito melhor que uma decisão seja tomada em grupo. <figure> 

![Grupos de interesse - No Spotify são chamados de Guild][3]<figcaption>Grupos de interesse &#8211; No Spotify são chamados de Guild</figcaption></figure> 

Os Grupos de Interesse são um time formado por integrantes que tem um objetivo comum, sem a coordenação de um gerente ou um coordenador. Eles conseguem entender que há um problema entre os diversos produtos e se organizam para juntos encontrarem uma solução. O Spotify tem uma cultura de organização que leva isso muito a sério. [Veja esse vídeo][4] para entender melhor como eles se organizam por lá.



[Spotify Engineering Culture &#8211; part 1][4] from [Spotify Training & Development][5]

É muito, muito importante que a comunicação entre esse pessoal seja frequente, objetiva e natural. Eles precisam ter autonomia para solucionar problemas que envolvem as suas capacidades e responsabilidades.<figure> 

![Grupos de Interesse com Autonomia no Spotify][6]<figcaption>Grupos de Interesse com Autonomia no Spotify</figcaption></figure> 

No documento acima, o Spotify fala que o maior desafio deles até hoje, foi lidar com 30 times divididos por 3 cidades. Pensa na complexidade disso. Você pode até dizer: “Bah, mas eles tem apenas um produto, nós temos 15!”. Você precisa entender é que eles realmente entregam apenas um produto único no final, mas eles tratam cada parte da interface e das funcionalidades do sistema como um produto separado. 

Aqui na firma tomamos uma decisão bem difícil de mudar. Eu estava coordenando um time funcional de front-end e sabíamos desde sempre que isso seria bom durante apenas um período de tempo (durou 4 anos). Hoje decidimos mudar, dividindo os integrantes para os diferentes times de produto. Obviamente eu não tinha integrantes suficientes para todos os produtos. Os times que não tem front-end, deverão contratar um em breve. A ideia é que as necessidades de front-end sejam supridas pela própria equipe do projeto.<figure> 

![Front-end da Locaweb fazendo um exercício chamado Meddlers][7]<figcaption>Esse exercício que os caras estão se fazendo se chama [Meddlers][8].</figcaption></figure> 



Com esse time sendo distribuído, nós criamos automaticamente um Grupo de Interesse para cuidar do [framework de interface][9] que a empresa utiliza. Esse framework tem duas versões muito usadas pelos produtos e é preciso um time cuidando da manutenção e criação de novos módulos. O time de front-end era o responsável, agora o Grupo de Interesse, formado pelos front-ends de cada produto, mais alguns integrantes de UX (que ainda são um time funcional, infelizmente), formarão esse Grupo de Interesse. A ideia é que o desenvolvimento do framework não pare (nem pode parar, senão o caso será instalado na empresa). Vai ser um grande desafio.

Conforme o tempo for passando, escrevo mais falando como estamos lidando como essa nova organização. Vai ser divertido.

Se você quiser ler mais sobre o assunto, sugiro que inicie lendo o livro [Management 3.0][10] e veja os vídeos ([parte 1][4] e [parte 2][11]) de como o Spotify montou seus times.

 [1]: https://en.wikipedia.org/wiki/Waterfall_model
 [2]: http://bit.ly/18MX8cg
 [3]: https://dl.dropboxusercontent.com/u/177663/assets-diegoeis-com/guia-interesse-spotify.jpg
 [4]: https://vimeo.com/85490944
 [5]: https://vimeo.com/user14023874
 [6]: https://dl.dropboxusercontent.com/u/177663/assets-diegoeis-com/autonomy-alignment.jpg
 [7]: https://dl.dropboxusercontent.com/u/177663/assets-diegoeis-com/frontend-meddlers-locaweb.jpg
 [8]: http://noop.nl/2011/09/meddlers-free-exercise.html
 [9]: http://opensource.locaweb.com.br/locawebstyle/
 [10]: https://management30.com/product/management30/
 [11]: http://vimeo.com/94950270