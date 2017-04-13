---
title: DeployBot faz o build e deploy do seu projeto para produção
author: Diego Eis
type: post
date: 2015-10-05
url: /deploybot-faz-o-build-e-deploy-do-seu-projeto-para-producao/
categories:
  - Técnicas e Práticas
  - Tooling

---
Eu suponho que você não usa mais FTP. Nem preciso dizer que isso é coisa do passado e faz mal para sua saúde. Mesmo que você use hoje GIT, um monte de tasks runners e etc: fazer o build e deploy da sua aplicação pode ser muito chato e trabalhoso. Mas o DeployBot tem a missão de tentar mudar isso tudo.

A ideia é que o DeployBot centralize o deploy do seus projetos desde a fase inicial de testes, homologação e depois produção. Ele cuida de rodar seus tasks runners como Gulp ou Grunt e também a compressão do seu Sass. As &#8220;changes&#8221; podem ser feitas facilmente em vários locais, pegando do seu repositório e jogando direto para o seu servidor. É um CI simplão, ready to use.

Manual ou automático. Você pode disparar o deploy automaticamente a cada push para um branch específico ou disparar manualmente quando você achar que está tudo pronto.

<img src="http://tableless.com.br/uploads/2015/09/deploy-bot-2.jpg" alt="deploy-bot-2" width="943" height="933" class="alignnone size-full wp-image-51479" />

Ele pode ser perfeito para você, freelancer sozinho ou para pequenos (e talvez até grandes) times. Quando os deploys são feitos, você pode avisar todo mundo via Slack, Basecamp ou outros chats ou clientes de instant messengers. O legal também é que todas as changes podem ser monitoradas direto do browser. 

<img src="http://tableless.com.br/uploads/2015/09/deploybot-screen.jpg" alt="deploybot-screen" width="560" height="451" class="alignnone size-full wp-image-51481" />

Nem preciso dizer que você também consegue fazer um rollback para a change anterior caso algo dê muito errado. A interface é bem facinha de usar e eu já tinha configurado tudo em alguns passos simples: conectei no repositório, depois o ambiente foi feito automaticamente e por último &#8220;liguei&#8221; num servidor, defini o caminho da aplicação e os triggers. Pá pum!

Se você for usar apenas um repositório, é grátis, com a disponibilidade de ter deploys e usuários ilimitados. Tem uma [documentação da sua API bem aqui][1].

 [1]: http://deploybot.com/api/overview