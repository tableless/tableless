---
title: Usando GIT para atualizar arquivos no servidor de hospedagem
author: João A. Zonta
type: post
date: 2015-10-08
url: /usando-git-para-atualizar-arquivos-no-servidor-de-hospedagem/
categories:
  - Artigos
  - O Básico
tags:
  - git

---
## Solução usando Bitbucket + Kinghost

A mesma configuração pode ser usada em qualquer servidor GIT e qualquer serviço de hospedagem que tenha acesso via ssh e git instalado

Vamos imaginar um cenário em que você está desenvolvendo um site, nesse site você tem vários arquivos, distribuídos em pastas separadas, css, javascript, html, etc&#8230;

Sempre que você altera algum arquivo, precisa enviar por FTP, para atualizar seu site. Um fluxo ([antigo][1]), mas parece ser ainda muito normal ([infelizmente][2]) por aí. As vezes você faz várias alterações e pode esquecer de enviar alguma coisa, ou você não sabe se já atualizou ou não, ou então você mandou alguma coisa errada para o servidor e seu site parou de funcionar, como fazer para voltar a versão anterior?

Com o GIT esse problema é solucionado, você pode voltar para a versão desejada com apenas um comando git, atualizar apenas os arquivos que foram alterados e muito mais.

#### Requisitos para executar este tutorial:

  * Conta no site <a href="https://bitbucket.org/" target="_blank">https://bitbucket.org/</a>
  * Serviço de hospedagem linux com acesso SSH
  * Cliente GIT instalado na sua máquina &#8211; <a href="https://git-scm.com/downloads" target="_blank">https://git-scm.com/downloads</a>
  * Putty, baixe o pacote completo, é um arquivo .zip com os binários para windows &#8211; <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html" target="_blank">http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html</a>

Antes de tudo vamos criar nossa chave de ssh no windows, essa chave serve para autenticação no bitbucket, com a chave ativa no windows você não precisa ficar digitando seu login e senha para autenticar;

Descompacte o arquivo putty.zip e execute o arquivo PUTTYGEN.EXE;

Clique em |Generate|, para que a chave seja criada você deve movimentar o mouse na área em branco do programa e esperar a barra de progresso chegar até o final:

[<img class="alignnone size-full wp-image-51450" src="http://tableless.com.br/uploads/2015/09/puttygen_01.jpg" alt="puttygen_01" width="492" height="476" />][3]

Clique em |Save private key|, vai aparecer uma janela avisando que não definimos um passphrase, clique em sim e salve sua chave.ppk, o arquivo ppk é usado para identificar seu computador no bitbucket, vamos usa-lo mais tarde.

Ainda no PuttyGen, vamos copiar a nossa chave |Public Key| para inserir no bitbucket.

[<img class="alignnone size-full wp-image-51451" src="http://tableless.com.br/uploads/2015/09/puttygen_02.jpg" alt="puttygen_02" width="492" height="476" />][4]

Abra o bitbucket, clique em |Gerenciar conta| > |Chaves SSH| > |Adicionar Chave|;

Na janela que abrir escolha um nome para identificar a chave, pode ser qualquer nome, e no campo key cole a chave que copiamos lá do PuttyGen.

[<img class="alignnone size-full wp-image-51443" src="http://tableless.com.br/uploads/2015/09/chave_bitbucket.jpg" alt="chave_bitbucket" width="786" height="466" />][5]

Já pode fechar o PuttyGen, vamos agora inicializar a chave no computador, execute o PAGEANT.EXE, quando você executa aparece um ícone na barra de tarefas ao lado do relógio do windows, clique duas vezes para abrir o PAGEANT;

Com o PAGEANT aberto, clique em |Add Key| e selecione o arquivo .ppk que salvamos anteriormente, depois pode fechar o PAGEANT, ele vai ficar minimizado na barra de tarefas.

&nbsp;

#### Criando repositório no Bitbucket

Depois de logado no site do bitbucket, clique em criar e selecione a opção criar repositório;

Na tela a seguir você deve escolher um nome, aqui vou usar o nome |artigo\_atualizacao\_arquivos|;

Nos níveis de acesso você escolhe se vai ser um repositório privado ou público, se for privado somente as pessoas que você conceder permissão terão acesso, no meu caso criei um repositório público;

Não precisa mexer no restante das configurações, veja abaixo como ficou:

[<img class="alignnone size-full wp-image-51444" src="http://tableless.com.br/uploads/2015/09/configuracao_bitbucket_01.jpg" alt="configuracao_bitbucket_01" width="614" height="580" />][6]

Após essa etapa vai aparecer uma tela de confirmação dizendo que o repositório está vazio e algumas dicas de como configurar, vamos criar um repositório do zero.

No seu computador abra o terminal e vamos verificar se o git está instalado, digite |git &#8211;version| se o git estiver instalado você deve ver uma mensagem dizendo qual a versão você tem instalada;

_* Caso não tenha o GIT instalado ainda, faça o download e instale https://git-scm.com/downloads_

Ainda no terminal navegue até a pasta que vai ter o conteúdo do seu repositório, caso necessário crie uma;

Digite |git init| para iniciar um novo repositório local;

No bitbucket, selecione o seu repositório, depois no menu a esquerda, clique em clonar, vai abrir uma janela, selecione ssh e copie o texto que tem no campo ao lado;

[<img class="alignnone size-full wp-image-51445" src="http://tableless.com.br/uploads/2015/09/configuracao_bitbucket_02.jpg" alt="configuracao_bitbucket_02" width="667" height="390" />][7]

Cole o texto copiado no seu terminal e espere a mensagem de confirmação, deve ser parecida com a mensagem abaixo:

[<img class="alignnone size-full wp-image-51448" src="http://tableless.com.br/uploads/2015/09/configuracao_git_windows.jpg" alt="configuracao_git_windows" width="657" height="282" />][8]

Entre na pasta do seu repositório e crie um arquivo para fazer nosso primeiro commit, eu criei um arquivo chamado &#8220;artigo.html&#8221;;

Depois de criar o arquivo vamos adicionar ao commit com o comando |git add artigo.html-|

Agora vamos fazer o commit |git commit -m &#8220;Primeiro Commit|

Depois enviar para o servidor com o comando |git push -u origin master|

[<img class="alignnone size-full wp-image-51449" src="http://tableless.com.br/uploads/2015/09/configuracao_git_windows_01.jpg" alt="configuracao_git_windows_01" width="657" height="301" />][9]

Nossa configuração no windows já está pronta, já pode enviar e receber arquivos do repositório, agora vamos configurar nosso servidor de hospedagem.

Abra o putty e faça uma conexão ssh com o servidor, vamos fazer o mesmo processo do windows para saber se o git está instalado;

|git &#8211;version|

Vamos criar a chave de ssh para autenticar no bitbucket sem usar senha:

Digite |ssh-keygen|, vc vai ver uma mensagem pedindo em qual arquivo você quer salvar a chave, ao lado ele exibe uma sugestão, se apertar Enter sem escrever nada ele vai usar o arquivo padrão que foi sugerido, se o arquivo já existir vai pedir pra substituir, confirme |Y|, no meu caso usei o arquivo sugerido;

Logo após vai pedir o passphrase, novamente é só apertar Enter, pode deixar em branco;

[<img class="alignnone size-full wp-image-51446" src="http://tableless.com.br/uploads/2015/09/configuracao_git_linux_01.jpg" alt="configuracao_git_linux_01" width="652" height="409" />][10]

Se você usou o arquivo padrão para gerar a chave digite |cat ~/.ssh/id_rsa.pub| para visualizar a sua chave, copie esse código, e adicione uma nova chave no bitbucket com essa chave, da mesma maneira que fizemos com a chave que foi criada no windows.

[<img class="alignnone size-full wp-image-51447" src="http://tableless.com.br/uploads/2015/09/configuracao_git_linux_02.jpg" alt="configuracao_git_linux_02" width="642" height="131" />][11]

Pronto, agora vamos clonar nosso repositório, da mesma maneira que fizemos no windows, abra o repositório no bitbucket, depois no menu a esquerda, clique em clonar, vai abrir uma janela, selecione ssh e copie o texto que tem no campo ao lado;

[<img class="alignnone size-full wp-image-51445" src="http://tableless.com.br/uploads/2015/09/configuracao_bitbucket_02.jpg" alt="configuracao_bitbucket_02" width="667" height="390" />][7]

Execute o comando no seu terminal ssh;

Agora que seu repositório já esta configurado você pode usar o comando |git pull| para atualizar os arquivos sempre que quiser.

Ou pode voltar uma versão usando |git checkout| vale a penas estudar um pouco os comandos do git e entender todos os seus recursos.

Link para material de estudo sobre o GIT: <a href="http://pt.slideshare.net/slide_user/magia-git" target="_blank">http://pt.slideshare.net/slide_user/magia-git</a>
  
Link oficial do git: <a href="https://git-scm.com/" target="_blank">https://git-scm.com/</a>

ATENÇÃO: para evitar conflitos no git não use mais FTP nas pastas que você está usando versionamento através do GIT

No próximo artigo vou explicar como fazer o deploy automático usando php, sempre que o GIT for atualizado ele envia um aviso ao servidor que executa os comandos para atualizar os arquivos.

 [1]: http://elcio.com.br/pare-de-usar-ftp/
 [2]: http://tableless.com.br/tornar-dev-front-end/
 [3]: http://tableless.com.br/uploads/2015/09/puttygen_01.jpg
 [4]: http://tableless.com.br/uploads/2015/09/puttygen_02.jpg
 [5]: http://tableless.com.br/uploads/2015/09/chave_bitbucket.jpg
 [6]: http://tableless.com.br/uploads/2015/09/configuracao_bitbucket_01.jpg
 [7]: http://tableless.com.br/uploads/2015/09/configuracao_bitbucket_02.jpg
 [8]: http://tableless.com.br/uploads/2015/09/configuracao_git_windows.jpg
 [9]: http://tableless.com.br/uploads/2015/09/configuracao_git_windows_01.jpg
 [10]: http://tableless.com.br/uploads/2015/09/configuracao_git_linux_01.jpg
 [11]: http://tableless.com.br/uploads/2015/09/configuracao_git_linux_02.jpg