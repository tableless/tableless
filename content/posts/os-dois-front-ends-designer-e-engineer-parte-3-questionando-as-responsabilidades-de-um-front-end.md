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
_Escrevi ouvindo essa música. Recomendo para a leitura:  
_[**_There is A Light That Never Goes Out — The Smiths_**](https://medium.com/r/?url=https%3A%2F%2Fopen.spotify.com%2Ftrack%2F0WQiDwKJclirSYG9v5tayI%3Fsi%3DAd3Pjt8aQROb3LdpGHQlBw)

***

Nos outros dois artigos da série ([Parte 1](https://tableless.com.br/os-dois-tipos-de-front-end-design-e-o-engineer-parte-1-uma-breve-historia/ "Primeira parte do artigo.") e [Parte 2](https://tableless.com.br/os-dois-front-ends-designer-e-engineer-parte-2-os-dois-perfis/ "Parte 2 do artigo.")), eu tentei desbravar os perfis de front-end que surgiram e até citei uma transformação que tem acontecido nos bastidores, onde é possível que designers se aproximem mais do código, juntamente com a ajuda do perfil **front-end designer.** E que essa aproximação tem acontecido com os back-ends, que estão cada vez mais interessados com em tecnologias como NodeJS.

**Eu quero tentar questionar essas pseudo-responsabilidades de um front-end**, tentando dar um outro ponto de vista, jogando essas responsabilidades para dois extremos: designers e programadores. E lembre-se dois dois primeiro artigos, aplicando as responsabilidades do front-end designer e do front-end engineer em cada um dos cenários.

Essa é uma responsabilidade compartilhada com o Designer, sendo que o Designer é o DONO do layout.

Se um layout vai pra produção com partes da interface mal feitas, com elementos desalinhados, sem seguir as especificações de layout, é uma constatação que tanto o designer quanto o front-end são desleixados. O designer é relaxado por não ter tido a preocupação de avaliar e modificar o layout antes de ir para produção e o front-end por não ter tido o esmero de seguir as especificações do layout.

**O front-end não é o responsável por atender aos requisitos de uma interface. Mas sim o designer.** Contudo, por meio do front-end o Designer preza pela qualidade do layout. Mas o front-end tem sim a responsabilidade de traduzir em código o desenho do layout. Aliás, durante MUITO TEMPO, essa foi a única responsabilidade dos front-ends.

![](https://cdn-images-1.medium.com/max/1000/1\*uDDA28iT0vKm2v-QkA_U0g.png)

[https://www.slideshare.net/diegoeis/ux-and-frontend/49](https://www.slideshare.net/diegoeis/ux-and-frontend/49 "https://www.slideshare.net/diegoeis/ux-and-frontend/49")

Exatamente por isso que **Designers estão cada vez mais se aproximando do código front-end**. O suficiente pra conseguir traduzir seu próprio layout pra código. E obviamente, isso faz que surjam cada vez mais ferramentas que ajudam os Designers, abstraindo a camada de código, e fazendo a ponte entre design e back.

**Pegar uma interface que o designer criou e de forma manual transformar esse layout em código é como fazer cópias analógicas de fitas VHS pra VHS**: _sempre fica pior que o original_. Se o designer conseguir entregar o código da interface (seja de forma automática ou ele mesmo codificando a interface) o resultado final **pode** ser MUITO melhor. Ou não.

![](https://cdn-images-1.medium.com/max/1000/1\*JeGEj0TnKnex-ThfkXcB7g.png)

Quem trabalha nessa área sabe como é difícil encontrar front-ends realmente capazes implementar interfaces perfeitas. Há muito tempo atrás tinha aquele orgulho de fazer um layout pixel perfect, hoje não mais.

Esse ponto é muito relacionada com a responsabilidade anterior e tem muito a ver com o perfil que já nos anteriormente o front-end designer.

Mas sejamos sinceros: a maioria dos front-ends **não começa** a fazer as funcionalidades e a interface iniciando pelo Mobile. **Manja aquela história de Mobile First? Na maioria da vezes isso não acontece na vida real.**

Não é de hoje que existem plugins e outros softwares de design que dão esse poder para os designers. Só para citar dois: [http://macaw.co/](http://macaw.co/ "http://macaw.co/") e [http://trymason.com](http://trymason.com "http://trymason.com"). Obviamente o uso desses serviços **ainda é muito restrito e só serve para alguns projetos, não todos**. Tem vários outros. Inclusive que devolvem o código em Sass ou Less.

Mesmo assim — por conta da falta de designers que codificam — a responsabilidade de ter um projeto que funcione bem em tablets e mobile é sim do front-end, mais especificamente ao perfil que vimos anteriormente, o front-end designer. Contudo cabe ao designer dar todas as especificações.

Creio que escalabilidade que ele se referia seria escalabilidade de código e não de infra. Logo, nesse caso, temos que falar sobre código legível/bonito.

Fiz uma pequena enquete no twitter perguntando:

Foram 46 pessoas respondendo a pergunta. 99% das respostas foram algo assim:

* eu faço código bonito para outra pessoa ou eu mesmo entender posteriormente;
* eu faço código bonito para executar um trabalho decente e impecável;
* eu faço código bonito para reduzir complexidade e tempo;

Logo, se tirarmos da conta o ser humano, não precisamos nos preocupar com código bonito (que é diferente de código que funciona e com boa lógica). Código bonito não serve pra aumentar performance, não faz uma feature funcionar melhor, não faz a empresa vender mais. Mas um código bem escrito sim.

Aliás, artifícios como **minificar código, image sprites e outras, são gambiarras em sua essência** para solucionar um problema de performance não de funcionamento de código, mas de carregamento de arquivos. Com tecnologias como o HTTPv2, nenhuma dessas gambiarras serão necessárias. Obviamente, códigos bem programados, com uma lógica impecável, faz a performance do sistema melhorar muito. Mas a beleza do código não.

Existe sim uma complexidade na organização de estrutura de arquivos, nomenclatura e componentização no front-end que afeta e muito a escalabilidade e manutenção **do projeto**. Todos sabem que CSS é fácil, mas se ele não for bem organizado desde o início, vira um inferno.

Eu não acho que isso seja responsabilidade de um dev front-end. Diretor, Gerente de tecnologia, Operações, infraestrutura, DevOps são só alguns dos profissionais que, na minha opinião, devem pensar nesses assuntos muito antes de front-end.

Se você ouvir um dev front-end falar isso, fique atento, ele não deve ter uma visão de verdade sobre como funciona uma empresa, um time, processos e com certeza ele acha que o front-end é o cara mais importante do pedaço.

Quando um dev resolve ir pra parte de gestão, ele fica sabendo que **desenvolvimento é tratado como custo nos projetos**. Decisões como contratar uma empresa terceira ou um funcionário CLT fazem parte do cotidiano e causam mais impacto no custo do que a stack de front.

Garantir entregas, estabilidade e monitoração não é responsabilidade exclusiva de front, mas do time inteiro. Monitoração é com o pessoal de Operações, por exemplo.

Eu acho que todas essas responsabilidades são divididas em diversa especialidades na empresa.

**POLEMICA. SE VOCÊ NÃO GOSTA DE POLÊMICAS, SE VAI ME ATACAR NO TWITTER DEPOIS, SE VAI ABRIR THREAD GIGANTE NOS FÓRUNS ALHEIOS, POR FAVOR, PULE ESSE PARÁGRAFO.** Boa parte dos devs front-ends hoje em dia gostam de centralizar responsabilidades ou achar que algumas das responsabilidades são deles. Por exemplo, componentização de interface é uma responsabilidade do front-end ou do designer? Muito provavelmente os front-ends que você perguntar, te responderão que é do front-end. Eu não acho… Eu acho que é uma responsabilidade totalmente compartilhada entre designer, front-end e back-end.

Um componente é feito pelo **designer, que define o comportamento e o layout**, pelo **front-end que materializa o layout em código e aplica o comportamento planejado pelo designer** e controla a **informação que é provida pelo back-end**.

Agora sobre testes: já cansei de ver times que no momento do Pull Request, fazem apenas a leitura do código e dão sugestões de melhorias, boas práticas e tudo mais, contudo NUNCA baixam o código pra testar a funcionalidade. Varias vezes já vi códigos que passaram por um crivo rígido de code review, mas que não estavam funcionando.

**Pull Request/Merge Request/Code Review** são uma oportunidade para o dev testar a funcionalidade do código, além da lógica de escrita.

Outro ponto pouco falado é o teste de regressão de interface. É um assunto pouco explorado, pouco aplicado e pouco conhecido pela maioria dos profissionais. Em 2013/2014 nós tentamos aplicar na Locaweb, mas as tecnologias para esse tipo de teste eram precárias. Até então usávamos o [Wraith](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2FBBC-News%2Fwraith), feito pelo pessoal da BBC. Testamos também o [Backstop](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2Fgarris%2FBackstopJS), que até então dava tantos paus que desistimos. Em 2016 surgiu o [Spectre](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2Fwearefriday%2Fspectre) que tenta fazer esse trabalho de uma maneira melhor. Não sei dizer, porque não testei.

Essa é uma responsabilidade que nenhum front-end precisava ter e só tem por falta de skill dos profissionais e também pela falta de tecnologia.

É bem esse ponto produtos como Sketch, [Supernova](https://medium.com/r/?url=https%3A%2F%2Fsupernova.studio), [Framer-X](https://medium.com/r/?url=https%3A%2F%2Ftableless.com.br%2Fframerx-design-to-code%2F) e tantos outros estão tentando resolver, exatamente pelo motivo de que **não tem sentido você criar um design e ter alguém que replica isso em código**. São dois processos que não precisam ser separados. Aliás, eles são separados hoje em dia pela falta de tecnologia. Nenhuma tecnologia criada até agora dava conta de fazer isso. Vide Dreamweaver, frontpage e outros que geravam código horrível. O problema principal desses softwares era que eles tentavam gerar código que um ser humano pudesse dar manutenção, ou seja, eles tentavam fazer um código bonito pra gente entender.

![](https://cdn-images-1.medium.com/max/1000/1\*AZAOWnaGlDkDQZhH3MWupQ.png)

Mas veja, se um dev não precisasse abrir o código pra fazer manutenção, então, a feiúra do código que esses sistemas geravam não seria problema. Mas naquele tempo, a quantidade de código gerada era um problema por causa do tamanho do arquivo final que afetava o download do site. Hoje nós temos problemas com performance de carregamento de site e tentamos resolver isso de todos os jeitos mais absurdos. Naquele tempo, fazer um site funcionar na conexão de um modem de 14kbps era realmente um desafio.

Além disso, o movimento de ter profissionais full-stack no time veio exatamente pra acabar com esse processo waterfall repetitivo que existe hoje. Conheço vários front-ends experientes que preparam o banco, criam a api e depois implementam a interface… tanto fazem isso que eles nem deveriam ser considerados front-end. Só são chamados assim, porque sua linguagem principal é JavaScript. Essa coisa de fazer ponte entre back e design não existe mais — ou não deveria mais existir — exatamente por que nem back e nem designer precisa mais de intermediários, ou não vai precisar em um futuro próximo… essa necessidade foi dissolvida e o próprio front-end que resolveu.

![](https://cdn-images-1.medium.com/max/800/1\*dFQotHXacgbUruHOYTxvfg.png)

Aquele argumento de ser especialista era pra um tempo que realmente haviam tantas particularidades entre as áreas, que pra um dev cuidar de back e cuidar de front, ao mesmo tempo, era difícil.  
Hoje temos tecnologia suficiente para nos ajudar a criar rapidamente APIs, também temos frameworks que nos ajudam com as particularidades de front, liberando os devs a aprenderem a ser profissionais full-stacks totalmente capazes de lidar com os problemas diários do desenvolvimento sem se importar se é um problema de server ou problema de front.

Há muito tempo atrás, fiz uma palestra falando sobre essa divisão e o que eu penso sobre ela.

Perceba bem o título da palestra. Queria sua atenção para o final da palestra.  
Eu realmente achava também que o front-end resolvia uma série de problemas. Mas só o fato de separarmos design, front-end e back-end já é uma esquisitice sem tamanho. E se houvessem apenas designers e programadores? Esse ser que chamamos de front-end hoje seria dissolvido nesses dois extremos. Os front-ends mais ligados a design, estariam “categorizados” como designers, cuidando de código para aprimorar o design. Hoje chamamos esse profissional de front-end designer. O outro lado seria o profissional que prefere mais trabalhar com lógica programando coisas. Ele é um programador.

Um dev web experiente, já percebeu que não existe mais profissionais X ou Y. Você é um desenvolvedor e resolve problemas.

Okay, mas quais as responsabilidades atuais ou futuras de um front-end? Vou tentar responder, na minha opinião, na segunda parte desse artigo.