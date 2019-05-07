---
title: Core do Linux no Windows com WSL2
authors: Diego Eis
type: post
date: 2019-05-07
image: https://i.imgur.com/0FplOdR.png
excerpt: Windows usará kernel do Linux para rodar software binário do Linux no Windows
categories:
  - Notícias
tags:
  - Windows
  - Linux
  - mercado
---

Já durante muito tempo a Microsoft tem se transformando. Saiu da mais odiada empresa de software de todos os tempos para uma das mais inovadoras, valiosas e inteligentes de todas as eras. Com suas transformações, mostrou que aprendeu com o passado e tem evoluído todos os dias um pouco mais em diversas frentes de trabalho, uma dessas frentes é o Open Source. 

Poucas pessoas sabem, mas a Microsoft tem projetos [Open Source desde 2004](http://robmensching.com/blog/posts/2004/4/5/windows-installer-xml-wix-toolset-has-released-as-open-source-on-sourceforge.net/), ainda de maneira bem timida. Mas conforme o mundo foi evoluindo, e as guerras entre softwares e sistemas operacionais em geral foi se distanciando e encontrando seus reais públicos, a Microsoft se sentiu muito à vontade para evoluir esse assunto. Evoluiu tanto de uns anos para cá, que hoje a Microsoft publicou que criou um negócio chamado WSL - Windows Subsystem for Linux.

![](https://i.imgur.com/Fx9n29N.png)

O anúncio foi feito pelo Jack Hammons, Gerente de Programa da Microsoft. "Beginning with Windows Insiders builds this Summer, we will include an in-house custom-built Linux kernel to underpin the newest version of the Windows Subsystem for Linux (WSL)," Jack disse no [post publicado no blog de desenvolvimento da empresa](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/).

> "WSL 2 is a new version of the architecture that powers the Windows Subsystem for Linux to run ELF64 Linux binaries on Windows." - Craig Loewen

O WSL basicamente é uma máquina virtual, que roda o core do Linux no Windows, e que permitia desde uns anos atrás instalarmos algumas instancias customizadas do [Ubuntu](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab), Fedora e [SUSE](https://www.microsoft.com/en-us/p/suse-linux-enterprise-server-12/9p32mwbh6cns?activetab=pivot:overviewtab) no Windows. Com essa nova versão do WSL, programas feitos para rodar em Linux poderão rodar em Windows como se fossem apps normais.

![](https://devblogs.microsoft.com/commandline/wp-content/uploads/sites/33/2019/05/runwsl.gif) 

Além de tudo, a nova versão virtualizada do kernel do Linux trará um aumento grande de performance, como aumentando 20 vezes a performance do WSL2 em relação ao WSL1 quando descompactar arquivos tarabll, e de 2 a 5 vezes em comandos como git clone e outros tipos de tarefas cotidianas no mundo do desenvolvimento.

> "WSL 2 uses the latest and greatest in virtualization technology to run its Linux kernel inside of a lightweight utility virtual machine (VM). However, WSL 2 will NOT be a traditional VM experience. When you think of a VM, you probably think of something that is slow to boot up, exists in a very isolated environment, consumes lots of computer resources and requires your time to manage it." - [Craig Loewen](https://twitter.com/craigaloewen) - Program Manager, Windows Developer Platform

Incrivelmente isso quebra várias barreiras. Muitos desenvolvedores preferiam Mac porque era uma junção do Windows e Linux, quase que o melhor dos dois mundos, porque era possível rodar sem gambiarras programas comuns em Windows com o Photoshop, Illustrator e afins, além de ter as facilidades de instalar stacks dos projetos mais facilmente e parecidas com o Linux dado a basae do Mac ser Unix. Contudo, há empresas que usam servidores e stack em Linux para rodar seus sistemas, mas os devs não tem escolha a não ser usar Windows no seu dia a dia. Agora, esse problema estará, talvez, totalmente resolvido.

Para leituras mais aprofundadas:
- [Announcing WSL 2](https://devblogs.microsoft.com/commandline/announcing-wsl-2/)
- [Shipping a Linux Kernel with Windows](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/)
- [Windows 10 will soon ship with a full, open source, GPLed Linux kernel](https://arstechnica.com/gadgets/2019/05/windows-10-will-soon-ship-with-a-full-open-source-gpled-linux-kernel/)
- [Windows 10 is getting a Microsoft-built Linux kernel](https://www.zdnet.com/article/windows-10-is-getting-a-microsoft-built-linux-kernel/)
- [Microsoft will ship a full Linux kernel in Windows 10](https://www.theverge.com/2019/5/6/18534687/microsoft-windows-10-linux-kernel-feature)