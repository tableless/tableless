+++
authors = "Diego Eis"
categories = ["carreira", "opinião"]
date = "2018-08-13T05:14:00-03:00"
excerpt = "Existem responsabilidades que talvez você ache que sejam exclusivas do front-end, mas não são. Tais responsabilidades são compartilhadas pelo time."
image = "https://cdn-images-1.medium.com/max/1000/1*Iam3a4m2IeS6G2C_4t5VzQ.jpeg"
publishdate = "2018-08-13T05:14:00-03:00"
tags = ["mercado"]
title = "Os dois front-ends: designer e engineer — Parte 3: Questionando as responsabilidades de um front-end"
type = "post"

+++
Nos outros dois artigos da série ([Parte 1](https://medium.com/@diegoeis/frontend-design-engineer-parte1-d3156d8dddd4) e [Parte 2](https://medium.com/@diegoeis/frontend-design-engineer-parte2-498bada72d84)), eu tentei desbravar os perfis de front-end que surgiram e até citei uma transformação que tem acontecido nos bastidores, onde é possível que designers se aproximem mais do código, juntamente com a ajuda do perfil **front-end designer.** E que essa aproximação tem acontecido com os back-ends, que estão cada vez mais interessados em tecnologias como NodeJS.

**Nesse artigo, eu quero tentar questionar as responsabilidades de um front-end**, tentando dar um outro ponto de vista. 

Eu acho que no final você pode sair com mais perguntas do que respostas sobre quais as responsabilidades de um dev front-end, a ideia é essa mesmo: cavar, procurar e encontrar bifurcações dos caminhos desse profissional. 

_Escrevi ouvindo essa música. Recomendo para a leitura:_  
[**There is A Light That Never Goes Out — The Smiths**](https://open.spotify.com/track/0WQiDwKJclirSYG9v5tayI?si=Ad3Pjt8aQROb3LdpGHQlBw)

# O front-end levanta e atende os requisitos de interface?

Historicamente, o dono do layout é o Designer. É ele que levanta os requisitos de como uma interface deve ser criada, levando em consideração todos os estudos, pesquisa e entrevistas que ele fez com o usuário.   
O front-end, nesse ponto, pode ser um participante influenciador. Mas ele não levanta os requisitos.

Contudo, o front-end se torna um tradutor do designer ao implementar a primeira camada de código desse layout. 

> Essa é uma responsabilidade compartilhada com o Designer, sendo que o Designer é o DONO da interface e do layout. 

Se um layout vai pra produção com partes da interface mal feitas, com elementos desalinhados, sem seguir as especificações de layout, é uma constatação que tanto o designer quanto o front-end são desleixados. O designer é relaxado por não ter tido a preocupação de avaliar e modificar o layout antes de ir para produção e o front-end por não ter tido o esmero de seguir as especificações do layout. Aliás, durante MUITO TEMPO, essa foi a única responsabilidade dos front-ends.

![](https://cdn-images-1.medium.com/max/800/1\*uDDA28iT0vKm2v-QkA_U0g.png)[https://www.slideshare.net/diegoeis/ux-and-frontend/49](https://www.slideshare.net/diegoeis/ux-and-frontend/49 "https://www.slideshare.net/diegoeis/ux-and-frontend/49")

Exatamente por isso que **Designers estão cada vez mais se aproximando do código front-end**. O suficiente pra conseguir traduzir seu próprio layout pra código. E obviamente, isso faz que surjam cada vez mais ferramentas que ajudam os Designers, abstraindo a camada de código, e fazendo a ponte entre design e back-end. 

![](https://cdn-images-1.medium.com/max/800/1\*JeGEj0TnKnex-ThfkXcB7g.png)

Quem trabalha nessa área sabe como é difícil encontrar front-ends realmente capazes implementar interfaces perfeitas. Há muito tempo atrás tinha aquele orgulho de fazer um layout pixel perfect, hoje não mais.

# O front-end garante funcionalidade da interface em qualquer dispositivo?

Esse ponto é muito relacionada com a responsabilidade anterior e tem muito a ver com o perfil que já nos anteriormente o front-end designer.

Mas sejamos sinceros: a maioria dos front-ends **não começa** a fazer as funcionalidades e a interface iniciando pelo Mobile. **Manja aquela história de Mobile First? Na maioria da vezes isso não acontece na vida real.**

Não é de hoje que existem plugins e outros softwares de design que dão esse poder para os designers. Só para citar dois: [https://macaw.co/](https://macaw.co/ "https://macaw.co/") e [https://trymason.com](https://trymason.com "https://trymason.com"). Obviamente o uso desses serviços **ainda é muito restrito e só serve para alguns projetos, não todos**. Tem vários outros. Inclusive que devolvem o código em Sass ou Less.

Mesmo assim — por conta da falta de designers que codificam — **a responsabilidade de ter um projeto que funcione bem em tablets e mobile é sim do front-end. O**front-end designer, nesse caso dos perfis de front-end, é o responsável por essa tarefa. Contudo cabe ao designer dar todas as especificações. O que quase nunca acontece. :-)

# O front-end garante a escabalabilidade e manutenibilidade do código?

A escalabilidade aqui se refere a de código e não de infra. Logo, nesse caso, temos que falar sobre código legível/bonito.

Fiz uma pequena enquete no twitter perguntando:

Foram 46 pessoas respondendo a pergunta. 99% das respostas foram algo assim:

* eu faço código bonito para outra pessoa ou eu mesmo entender posteriormente;
* eu faço código bonito para executar um trabalho decente e impecável;
* eu faço código bonito para reduzir complexidade e tempo;

Logo, se tirarmos da conta o ser humano, não precisamos nos preocupar com código bonito (que é diferente de código que funciona e com boa lógica). Código bonito não serve pra aumentar performance, não faz uma feature funcionar melhor, não faz a empresa vender mais. Mas um código bem escrito sim.

Aliás, artifícios como **minificar código, image sprites e outras, são gambiarras em sua essência** para solucionar um problema de performance não de funcionamento de código, mas de carregamento de arquivos. Com tecnologias como o HTTPv2, nenhuma dessas gambiarras serão necessárias. Obviamente, códigos bem programados, com uma lógica impecável, faz a performance do sistema melhorar muito. Mas a beleza do código não.

Existe sim uma complexidade na organização de estrutura de arquivos, nomenclatura e componentização no front-end que afeta e muito a escalabilidade e manutenção **do projeto**. Todos sabem que CSS é fácil, mas se ele não for bem organizado desde o início, vira um inferno.

# O front-end  pensa e calcula os custos de desenvolvimento, afim de defender o alto impacto por baixo custo?

Eu não acho que isso seja responsabilidade de um dev front-end. Diretor de Tecnologia, Gerente de tecnologia, Operações, infraestrutura, DevOps são só alguns dos profissionais que, na minha opinião, devem pensar nesses assuntos muito antes de front-end.

Quando um dev resolve ir pra parte de gestão, ele fica sabendo que **desenvolvimento é tratado como custo nos projetos**. Decisões como contratar uma empresa terceira ou um funcionário CLT fazem parte do cotidiano e causam mais impacto no custo do que a stack de front.

# O front-end é responsável por garantir entregas rápidas, estáveis e testáveis, monitorar o software para correção ou prevenção de falhas

Garantir entregas, estabilidade e monitoração não é responsabilidade exclusiva de front, mas do time inteiro. Mas coisas como monitoração é com o pessoal de Operações, por exemplo.

Eu acho que todas essas responsabilidades são divididas em diversas especialidades na empresa.

Por exemplo testes: praticamente todos os times, no momento do Pull Request, fazem _apenas_ a leitura do código e dão sugestões de melhorias, boas práticas e tudo mais. Contudo quase nunca um membro do time baixa o código pra testar a funcionalidade. **Pasme: diversas vezes já vi códigos que passaram por um crivo rígido de code review, mas que não estavam funcionando.**

Pull Request/Merge Request/Code Review são uma oportunidade para o dev testar a funcionalidade do código, além da lógica.

# O front-end é o responsável por fazer a ponte entre back-end e design?

Eu já pensei isso no começo e no meio da minha carreira de front-end. Contudo, conforme o penso foi passando, eu comecei a entender que isso era uma esquizofrenia do sistema. O mercado estava tão quebrado, ou seja: o designer SÓ queria fazer telinha e o back-end só queria escrever código de servidor. NENHUM DOS DOIS era capaz de fazer o trabalho manjado de HTML/CSS/JS.

É bem esse ponto produtos como Sketch, [Supernova](https://supernova.studio), [Framer-X](https://tableless.com.br/framerx-design-to-code/) e tantos outros estão tentando resolver: **não tem sentido você criar um design e ter alguém que replica isso em código**. São dois processos que não precisam ser separados. Aliás, eles são separados hoje em dia pela falta de tecnologia.

Conversando com um ex dev do [MarvelApp](https://marvelapp.com/), ele disse: **_The future is in collaboration. Rather than taking static pictures and trying to convert them into code, we are taking code and simplifying it. By visualising code, we can make it easier to digest, so designers can understand it and manipulate it._**

Nenhuma tecnologia criada até agora dava conta de fazer isso. Vide Dreamweaver, frontpage e outros que geravam código horrível. O problema principal desses softwares era que eles tentavam gerar código que um ser humano pudesse dar manutenção, ou seja, eles tentavam fazer um código bonito pra gente entender.

![](https://cdn-images-1.medium.com/max/800/1\*AZAOWnaGlDkDQZhH3MWupQ.png)

Mas veja, se um dev não precisasse abrir o código pra fazer manutenção, então, a feiúra do código que esses sistemas geravam não seria problema. Mas naquele tempo, a quantidade de código gerada era um problema por causa do tamanho do arquivo final que afetava o download do site. Hoje nós temos problemas com performance de carregamento de site e tentamos resolver isso de todos os jeitos absurdos. Naquele tempo, fazer um site funcionar na conexão de um modem de 14kbps era realmente um desafio.

Além disso, o movimento de ter profissionais full-stack no time veio exatamente pra acabar com o processo waterfall repetitivo que existia. 

Conheço vários front-ends experientes que preparam o banco, criam a API e depois implementam a interface… tanto fazem isso que eles nem deveriam ser considerados front-end. Só são chamados assim, poois sua linguagem principal é Javascript. 

Essa coisa de fazer ponte entre back e design não existe mais — ou não deveria mais existir. 

![](https://cdn-images-1.medium.com/max/800/1\*dFQotHXacgbUruHOYTxvfg.png)

Um dev web experiente, já percebeu que não existe mais profissionais X ou Y. Você é um desenvolvedor e resolve problemas.

E entenda: não sou a favor ou contra full-stack ou especialistas. Eu sou a favor do [profissional com perfil em T](https://tableless.com.br/o-perfil-t-shaped-e-o-dev-full-stack/). 

# Colaboração

Esse não é o futuro do front-end, mas do mercado de desenvolvimento como um todo. Pense num ambiente onde você automatiza boa parte do processo e passa seu tempo realmente pensando na estrutura e arquitetura do sistema. Pense num ambiente onde designers e front-ends usam uma mesma plataforma para editar a mesma tela. 

Esse é o tema do próximo artigo.