---
title: Como desenvolver com Docker no Linux dentro do Windows sem dual boot – WSL 2
date: 2020-06-18 16:59:11 UTC
image: https://marquesfernandes.com/wp-content/uploads/2020/06/windows_and_linux.jpg
authors: Henrique Marques Fernandes
type: post
excerpt: Esse é um artigo que esperei ansiosamente durante anos para poder escrever, finalmente é possível, de uma forma descomplicada e otimizada, desenvolver usando todas as vantagens do Linux diretamente do Windows.
categories:
  - Código
---

Esse é um artigo que esperei ansiosamente durante anos para poder escrever, finalmente é possível, de uma forma descomplicada e otimizada, desenvolver usando todas as vantagens do Linux diretamente do Windows. Durante muito tempo preferi configurar meu computador com o dual boot, usava o Windows para jogos, e outras aplicações, e [Ubuntu](https://marquesfernandes.com/?s=ubuntu) para trabalhar e desenvolver no dia a dia. O ambiente Linux traz alguns benefícios para o desenvolvimento no dia a dia, desde um desempenho melhor com algumas aplicações e serviços, Docker, por exemplo, até sua poderosa linha de comando. Porém, a falta de alguns aplicativos muito utilizados e compatibilidade com games fazem com que o Windows ainda fosse necessário. Até que finalmente, na atualização 2004 do Windows, o WSL2 (Windows Subsytem for Linux) foi adicionado, permitindo agora uma integração mais nativa com alguns sistemas no linux, como por exemplo, o [Docker](https://marquesfernandes.com/conteineres-e-docker-o-que-e-e-para-que-serve/).

## O que é Subsistema Windows para Linux (Windows Subsystem for Linux – WSL2)?

O WSL é um recurso disponível no Windows 10 mediante habilitação, está presente desde a versão 1607, mas desde a versão 2004 a versão WSL 2 foi disponibilizada para todos. O WSL permite executar comandos em um distribuição Linux diretamente no Windows, sem precisar de uma máquina virtual ou dual boot.

O WSL permite que você instale diversas distribuições Linux populares na sua máquina, ele cria uma estrutura de arquivos isolada e independente do sistema principal mas também permite acessar arquivos da sua instalação do Windows.

![Windows Store - Linux](https://marquesfernandes.com/wp-content/uploads/2020/06/image-10-1-1024x560.jpg)

A documentação da Microsoft é bem didática e te ensina como habilitar e configurar o WSL em sua máquina, [confira aqui](https://docs.microsoft.com/pt-br/windows/wsl/install-win10).

## WSL2 e Docker

Como o Windows Subsystem para Linux WSL 2 introduz uma mudança arquitetural significativa, pois é um kernel completo do Linux, ele permite que os contêineres do Linux sejam executados nativamente sem emulação (Adeus Hyper-V).

Com o Docker Desktop em execução no WSL 2, os usuários podem aproveitar os espaços de trabalho do Linux e evitar a manutenção de scripts de compilação do Linux e do Windows. Além disso, o WSL 2 fornece aprimoramentos no compartilhamento do sistema de arquivos, no tempo de inicialização e permite acesso a alguns novos recursos interessantes para usuários do Docker Desktop.

O Docker Desktop usa o recurso de alocação de memória dinâmica no WSL 2 para melhorar bastante o consumo de recursos. Isso significa que o Docker Desktop usa apenas a quantidade necessária de CPU e recursos de memória de que precisa, além de permitir que as tarefas que demandam muita CPU e memória, como a construção de um contêiner, sejam executadas muito mais rapidamente.

Além disso, com o WSL 2, o tempo necessário para iniciar um daemon do Docker após uma partida a frio é significativamente mais rápido. Demora menos de 10 segundos para iniciar o daemon do Docker quando comparado a quase um minuto na versão anterior do Docker Desktop.

Um exemplo prático para os desenvolvedores de [nodejs e docker](https://marquesfernandes.com/desenvolvimento-otimizado-em-nodejs-com-typescript-docker-e-eslint/), é não precisar mais usar a flag `--legacy-watch` com o nodemon, as mudanças nos arquivos serão propagadas com a mesma velocidade e compatibilidade, afinal, elas estarão rodando no linux.

## Configurando o VS Code e Docker com o WSL2

Eu vou explicar o processo que fiz para o meu cenário, eu utilizo o editor VS Code (Pesquisei e vi que muitas outras ides tem suporte para WSL também), e desenvolvo praticamente todas minhas aplicações com Docker, aprenderemos como configurar ele para usar o WSL também.

A primeira coisa que precisamos entender é a maneira como vamos lidar com os arquivos, depois que você [habilitou o WSL e instalou a sua distro de Linux](https://docs.microsoft.com/pt-br/windows/wsl/install-win10) preferida, você terá agora dois ambientes, como se você tivesse uma máquina virtual com o seu próprio disco. Embora você consiga acessar os dados do Windows pela linha de comando do WSL, esse acesso não é nativo, ele usa uma ponta para compartilhar esses arquivos o que impacta na performance, então tudo que você quiser desenvolver no linux para aproveitar as melhorias, deverá ser criado na estrutura de dados direta do WSL.

Então se você estiver em uma pasta parecida com `/mnt/c/`, você está acessando os arquivos no Windows, não queremos isso para desenvolvimento.

### VS Code – Extensão WSL

Para configurar o seu VS Code para ter suporte ao WSL, basta instalar a extensão**[Remote WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)**, desenvolvida pela própria Microsfot, ela faz toda a mágica acontecer. Ela permite que você abra os arquivos diretamente do sistema Linux, e já integra o seu terminal com o terminal do Linux.

![Remote - WSL](https://marquesfernandes.com/wp-content/uploads/2020/06/image-5-1024x560.jpg)<figcaption>Remote – WSL</figcaption>

Depois de instalado e configurado, você precisará instalar as extensões do VS Code dentro do subsistema. Não se preocupe, é bem fácil, a extensão Remote – WSL já habilita uma opção para reinstalar as suas extensões:

![Instalar extensão do VS Code no WSL](https://marquesfernandes.com/wp-content/uploads/2020/06/image-10-1024x560.jpg)

### Docker e WSL 2

Configurar o Docker para utilizar o motor do WSL é bem simples também, basta ir nas suas configurações e encontrar a opção para habilitar o uso.

![Docker WSL 2](https://marquesfernandes.com/wp-content/uploads/2020/06/image-6-1024x560.jpg)

Depois de habilitado, você precisará habilitar a integração com a distro instalada:

![Docker WSL 2](https://marquesfernandes.com/wp-content/uploads/2020/06/image-7-1024x560.jpg)

Se tudo ocorrer conforme esperado, agora você pode utilizar o Docker direto da sua linha de comando no WSL:

![VS Code, Docker e WSL 2](https://marquesfernandes.com/wp-content/uploads/2020/06/image-9-1024x560.jpg)

### Otimizando o WSL 2

Logo depois que eu configurei e comecei a testar esse novo setup, notei que o consumo de memória era absurdo (chegava a topar 8GB de Ram) separados só para o WSL 2. Depois de uma pesquisa, vi que já existe uma [issue no github](https://github.com/microsoft/WSL/issues/4166) para adereçar o problema, aparentemente o WSL 2 guarda muitos arquivos de cache. Mas existe uma solução simples, limitar a quantidade de memória que o WSL pode consumir:

Basta criar um arquivo em `%UserProfile%\.wslconfig` com o seguinte conteúdo:

```
[wsl2]memory=4GB # Limita para 4GBswap=0localhostForwarding=true
```

E caso comece a consumir muito ainda, podemos executar o comando para limpar os caches:

`echo 1 | sudo tee /proc/sys/vm/drop_caches`

Espero que eles resolvam esse problema em breve, não é um impeditivo, mas com certeza atrapalha a experiência, pois limiar a quantidade de RAM pode causar comportamentos inesperados dentro do subsistema.

## Conclusão

Embora sim, existam problemas ainda nesse setup, ele se mostra bem promissor. Atualmente já desinstalei o dual boot da minha máquina e estou há 2 semanas trabalhando nessa estrutura e nada de impeditivo de reclamação. Faça um teste, veja se você se adapta a essa nova estrutura antes de desinstalar seu dual boot ou voltar totalmente para o Windows, se você encontrar algum problema ou tiver alguma dica, compartilha conosco!
