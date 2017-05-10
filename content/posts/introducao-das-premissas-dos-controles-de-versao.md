---
title: Introdução das premissas dos controles de versão
author: Diego Eis
type: post
date: 2012-01-16
excerpt: Introdução sobre algumas premissas sobre controles de versão. Muito útil para designers e iniciantes na área.
url: /introducao-das-premissas-dos-controles-de-versao/
tweetbackscheck:
  - 1356399301
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5211";s:7:"tinyurl";s:26:"http://tinyurl.com/87mzax3";s:4:"isgd";s:19:"http://is.gd/7h4ZTg";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 541224813
categories:
  - Código
  - Mercado e Comportamento
  - O Básico
  - Tecnologia e Tendências
tags:
  - 2012
  - desenvolvimento web
  - Na Prática
  - web standards

---
Parece ser óbvio, mas muitos desenvolvedores desdenham de ter controle total sobre o código gerado no desenvolvimento. Muitos, por trabalharem sozinhos, entendem que não precisam manter um certo nível de organização do seu código exatamente por que talvez, somente eles, o verão.
  
Quem nunca ficou horas tentando debugar um código que você mesmo fez, mas não lembrava o que uma determinada função fazia&#8230; Esse código pode ter sido por você de madrugada, quando você estava pingando de sono, ou pior, bêbado&#8230; Vai saber&#8230;

Controlar seu código fonte deve ser uma premissa. Um princípio. Se você acha que o undo do seu editor predileto salva sua vida, imagina ter um undo do seu projeto inteiro. Imagine você ter a história de edição de cada um dos arquivos do seu projeto.

Os princípios abaixo servem para qualquer tipo de controle de versão que conhecemos hoje: GIT, SVN, Mercurial etc. 

#### Branchs e trunks

A última revisão, a mais atual, normalmente é chamada de _HEAD_. Existem momentos onde teremos vários HEADs pois o projeto tem vários BRANCHES. Um branch é uma cópia do projeto. Cada branch pode ser editado e evoluído independentemente. 

Imagine que exista a **versão de produção** que é aquela que está no ar. É a versão que o usuário está utilizando. É importante que nós não modifiquemos esta versão porque alguém pode commitar algo errado, quebrar tudo e o usuario reclamar. Por isso nós precisamos de outro ambiente para evoluir as features, resolver bugs e etc, sem afetar o branch principal. Essa forma é usado em projetos pequenos, mas algo parecido é feito em projetos grandes, onde aumentamos o número de servidores para termos mais segurança ao fazer os deploys.

<img src="http://tableless.com.br/uploads/2012/01/branch.jpg" alt="" title="branch" width="770" height="188" class="alignnone size-full wp-image-5212" srcset="uploads/2012/01/branch.jpg 770w, uploads/2012/01/branch-300x73.jpg 300w" sizes="(max-width: 770px) 100vw, 770px" />

É muito útil criarmos novos **trunks** (tronco) quando precisamos fazer modificações drásticas de novas features, resolver bugs ou modificar layout. 

Exemplo: imagine que você esteja trabalhando em uma nova feature, em um branch específico. O cliente liga e diz que encontrou um bug, originado de uma modificação feita na semana passada. Você sai do branch da nova feature, entra no branch que tem o código que está em produção (que é o que o cliente está vendo) e cria um novo branch. Você resolve o bug neste novo branch. Feito isso, você pode mover as modificações deste branch para o branch de produção e aí entra o processo de deploy que pode mudar de empresa para empresa. Quando tudo estiver ok, você volta para o branch onde estava desenvolvendo a nova feature e pronto. Sem misturar códigos, sem subir nada para o FTP, tudo lindo e maravilhoso. A equipe tem o código atualizado à mão e todo mundo fica feliz.

#### Versionamento

Versionamento é uma das características mais básicas do controle de código. Quando comecei a desenvolver, normalmente eu trabalhava guardando pastas com nomes do tipo **nomeDoProjeto-v1**, **nomeDoProjeto-v2** etc&#8230; Estas pastas guardavam apenas as versões com grandes modificações de projeto&#8230; algo como mudança geral de layout, uma feature importante ou algo do tipo. O problema são as pequenas edições&#8230; Quando juntamos as pequenas modificações, temos uma grande modificação. É muito provável que se você perder essa versão, você não se lembre de todas as pequenas modificações feitas e isso é um problemão.

Toda vez que o desenvolvedor termina uma determinada tarefa, em geral um commit que por sua vez gera um ponto de referência, uma versão, daqueles arquivos modificados. Cada commit gera uma versão do seu código. A graça é que se você tem versões do código, você tem praticamente um **undo** gigante do seu projeto&#8230; Se depois de uma determinada modificação seu projeto começou a dar pau, você consegue entender com a história do seu versionamento &#8211; o famoso log &#8211; a partir de onde exatamente o problema foi iniciado.

#### Logs

Quando cada revisão é comitada, o desenvolvedor pode ou não adicionar uma mensagem explicando o que ele fez naquela tarefa. É importante que essa mensagem seja clara e rica em detalhes, mas não um texto gigante, apenas o suficiente para que você mesmo ou outras pessoas envolvidas entenda o que aquela submissão significa.

#### Diffs

Diffs são sensacionais. Imagine que você queira comparar duas versões de um mesmo arquivo para descobrir as linhas modificadas. Fazer um diff entre as versões do arquivo te possibilita encontrar exatamente onde está o erro e o melhor, quando juntamos com o Log, podemos saber exatamente o por que a pessoa incluiu aquela linha ou aquele código, e o melhor, quem fez aquela alteração. 

#### Rollback

Mantendo uma história de commits, você tem **pontos de volta** na história do arquivo, possibilitando a facilidade de voltarmos para antes de alguma modificação. Você pode voltar a partir de um commit, por exemplo. Se o sistema ou o arquivo passou a dar problema depois de uma determinada revisão, é simples de você voltar o arquivo para a versão daquele determinado commit.

#### Edição multiusuário e merge

Isso é uma maravilha. Me lembro de equipes inteiras perdendo arquivos e partes de código pois dois membros abriam o mesmo arquivo para editar. Obviamente nunca, mas nunca dava certo. Isso fazia com que grandes equipes criassem mecanismos da idade das pedras para avisar o resto do pessoal que determinado arquivo estava sendo usado. O trabalho remoto nunca era possível. Com um controle de versão isso muda. Qualquer um pode editar qualquer arquivo a qualquer hora.

O sistema de controle de versão compara as modificações feitas no arquivo pelos desenvolvedores e junta os códigos automaticamente. Muito bonito, hein?

E quando os desenvolvedores modificam a mesma linha de código? Aí o controle de versão gera um conflito, esse conflito deve ser resolvido pelo desenvolvedor que enviou as modificações por último. Funciona assim:

1. Dois desenvolvedores abrem o mesmo arquivo para editar.
  
2. Quando os desenvolvedores terminam, eles geram um commit. Se os desenvolvedores fizeram edições em partes diferentes do arquivo, por exemplo, um no começo do arquivo e o outro no final, o sistema junta os códigos fazendo um merge e criando um arquivo atualizado com as duas revisões. Indolor.
  
3. Se sistema percebe que os desenvolvedores fizeram as modificações na mesma linha, o sistema gera um conflito, por que o sistema não sabe qual dos dois códigos é o correto.
  
4. O conflito é resolvido pelo desenvolvedor que comitar o código por último. Eu commitei minha versão de código e subi essa atualização para o servidor. Quando você commitar seu código, você é obrigado a baixar o que está no servidor aí o controle de versão avisará que há um conflito em uma parte do seu código. O conflito é resolvido mostrando algo mais ou menos assim:

<pre class="lang-css">p {
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD:style.css
   color: red;
=======
   color: blue;
>>>>>>> 77976da35a11db4580b80ae27e8d65caf5208086:estilo.css
}
</pre>

A primeira linha mostra a sua linha. A segunda linha mostra a modificação do outro dev. Aquele hash maluco no final é a identificação do commit do outro dev.
  
Bom, nesses casos você precisa ver qual código é o correto, e algumas vezes isso significa perguntar para o outro brother que diachos é aquela coisa que ele fez.

### Concluindo

Estas são algumas premissas sobre os controles de versão utilizados hoje em dia. Os controles de versão mais usados hoje são o GIT, SVN e Mercurial. Cada um deles tem comandos diferentes para lidar com as premissas acima e cada um deles faz o controle de sua forma particular. Mesmo assim todos trazem as vantagens que citamos no artigo. Mesmo que você trabalhe sozinho, é recomendado que você trabalhe com controle de versão. Assim você guarda seu projeto de forma segura e tem um histórico das suas modificações durante o tempo.