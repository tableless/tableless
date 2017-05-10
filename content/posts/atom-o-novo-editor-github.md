---
title: 'Atom: o novo editor by Github'
author: Diego Eis
type: post
date: 2014-02-27
excerpt: Algumas informações sobre o Atom, o novo editor do Github.
url: /atom-o-novo-editor-github/
dsq_thread_id: 2331936699
categories:
  - Editores
  - Notícias
tags:
  - atom
  - editor
  - github
  - sublime

---
É quase impossível não comparar o Atom com o Sublime. O Sublime cravou um padrão com seus shortcuts, sua interface e sua coleção de comandos que é muito difícil ignorar. O Atom tem a cara do Sublime. Diferente do Brackets, que é bem diferente tanto na interface quanto nos shortcuts. Estou usando o Brackets para algumas coisas e estou gostando bastante. Mas a curva de aprendizado, quando acostumado com o Sublime, é muito grande. Com o Atom você já vai conhecer meia dúzia de shortcuts, facilitando muito a migração.

Sinceramente eu não me lembro quando o Sublime tomou conta de tudo. Um dia, todo mundo acordou com o Sublime instalado, sabendo todos os atalhos e as manhas do editor. Não teve tempo de aprendizado. Ninguém mais fica brigando qual editor é melhor&#8230; Todo mundo sabe que VIM é coisa de louco e Sublime coisa de gente normal (brincadeira). É inegável que o Sublime entendeu como digitávamos código, retirando tudo que era ruído e deixando apenas o que interessava. Isso começa pela interface e termina na forma com que executamos e manipulamos comandos.

O Atom seguiu o mesmo caminho. Ele pegou tudo que era bom do Sublime e ainda teve ideias originais e geniais para facilitar ainda mais a nossa vida. É como se o Atom fosse uma nova versão do Sublime. É difícil até de pensar o que o Sublime mudaria para melhorar e até concorrer com o Atom.

Essa similaridade entre os editores não é ruim. Mas o que vai importar mesmo são as features extras que cada um pode trazer no futuro. Descrevi algumas features legais que me chamaram mais a atenção e que se diferenciam totalmente do Sublime.

<img src="http://tableless.com.br/uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31.png" alt="Atom editor github" class="alignnone size-full wp-image-41283" srcset="uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31.png 1216w, uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31-177x168.png 177w, uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31-327x310.png 327w, uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31-400x378.png 400w" sizes="(max-width: 1216px) 100vw, 1216px" />

## Aparência e themes

Não há muito o que falar sobre aparência geral do editor. Ele é bem parecido com o Sublime Text, só que com uma vantagem: você consegue customizar praticamente QUALQUER COISA usando CSS.

Seguindo o menu **Atom > Open Your Stylesheet**, o Atom abre um arquivo CSS onde você customiza o que quiser na tela. Muda cor de texto, font, background, margin, padding, TUDO.

<img src="http://tableless.com.br/uploads/2014/02/Screen-Shot-2014-02-27-at-14.42.08.png" alt="Screen Shot 2014-02-27 at 14.42.08" class="alignnone size-full wp-image-41287" srcset="uploads/2014/02/Screen-Shot-2014-02-27-at-14.42.08.png 1442w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.42.08-210x168.png 210w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.42.08-388x310.png 388w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.42.08-400x319.png 400w" sizes="(max-width: 1442px) 100vw, 1442px" />

Aí vem a pergunta: Mas como vou saber os elementos que devo formatar? Simples, abra um Inspector. Siga o menu **View > Developer > Toggle Developer Tools**. O Inspector que se abre é o padrão do Webkit.

<img src="http://tableless.com.br/uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31.png" alt="Atom editor github" class="alignnone size-full wp-image-41283" srcset="uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31.png 1216w, uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31-177x168.png 177w, uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31-327x310.png 327w, uploads/2014/02/Screen-Shot-2014-02-27-at-13.56.31-400x378.png 400w" sizes="(max-width: 1216px) 100vw, 1216px" />

Desse jeito fica muito, muito fácil personalizar o visual do editor e até criar um novo tema para compartilhar por aí.

Um detalhe: você pode escrever CSS puro ser quiser, sem problema, mas para os mais ousados, fique à vontade para escrever em LESS. Muito útil se quiser fazer um tema para o editor.

### Styleguide

Indo para o menu **Packages > Styleguide > Show**, o Atom te mostra um guia de estilo do tema atual. Ele mostra o markup do HTML e também o CSS que faz esse HTML ficou bonitão. Isso serve para ajudar os criadores de temas a revisarem seus estilos e como eles se comportam nos elementos do editor.

<img src="http://tableless.com.br/uploads/2014/02/Screen-Shot-2014-02-27-at-17.35.28.png" alt="Screen Shot 2014-02-27 at 17.35.28" class="alignnone size-full wp-image-41289" srcset="uploads/2014/02/Screen-Shot-2014-02-27-at-17.35.28.png 1394w, uploads/2014/02/Screen-Shot-2014-02-27-at-17.35.28-263x168.png 263w, uploads/2014/02/Screen-Shot-2014-02-27-at-17.35.28-486x310.png 486w, uploads/2014/02/Screen-Shot-2014-02-27-at-17.35.28-400x254.png 400w" sizes="(max-width: 1394px) 100vw, 1394px" />

## Settings

Essa parte é sensacional. O Sublime não tem uma área para controlar as configurações do editor. Você muda essas preferências direto no arquivos de configuração do editor. Isso é genial na primeira vez, mas depois você sente alguma falta de apertar botões, saber que tudo tá funcionando, ter certeza de que não alterou nada que vá destruir seus shortcuts, tema e outras configurações. Já o Atom tem a famosa tela de configurações, como qualquer outro programa. Nele você gerencia os packages (plugins), temas e shortcuts.

<img src="http://tableless.com.br/uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.28.png" alt="Screen Shot 2014-02-27 at 14.41.28" class="alignnone size-full wp-image-41286" srcset="uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.28.png 1442w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.28-210x168.png 210w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.28-388x310.png 388w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.28-400x319.png 400w" sizes="(max-width: 1442px) 100vw, 1442px" />

As vezes, quando você precisa fazer algo muito personalizado é legal editar os arquivos de configuração do próprio editor, aí o Atom, como no Sublime Text, permite que você modifique as configurações personalizadas em arquivos específicos. Você pode gravar scripts, customizar seus próprios shortcuts, snippets etc.

### Keybindings

Logo de cara você já tem a listagem dos shortcuts do editor, com um search decente que te ajuda a encontrar os comandos. No Sublime Text você ficava vasculhando no arquivo de configuração ou procurando no Google. Não era difícil, mas era pouco confortável.

## Tudo são módulos

O Atom chama seus plugins de Packages. Estes packages fazem parte das configurações do editor ou são apenas plugins que estendem as funcionalidades já existentes. Todos estes packages são módulos independentes e todos eles estão no Github, prontos para serem forkados, compartilhados e etc&#8230;

<img src="http://tableless.com.br/uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.13.png" alt="Atom editor github" class="alignnone size-full wp-image-41285" srcset="uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.13.png 1442w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.13-210x168.png 210w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.13-388x310.png 388w, uploads/2014/02/Screen-Shot-2014-02-27-at-14.41.13-400x319.png 400w" sizes="(max-width: 1442px) 100vw, 1442px" />

Outro detalhe importante é que ele mostra quantos milisegundos a mais o Atom demorará para iniciar com aquele módulo habilitado. Nunca mais você vai deixar seu editor pesado sem saber o motivo.

Como não podia faltar, ele já vem com um search para encontrar novos packages. Basta procurar, clicar em Install e pronto. No Sublime, você precisa instalar o Package Control.

### Timecop

A ideia do Atom é que você domine totalmente o editor. Para isso, é legal saber o que exatamente está rodando nele. O Atom ajuda você a manter o controle com uma feature chamada Timecop. 

O Timecop mostra quanto de tempo cada package demora para carregar. Isso permite descartar aqueles packages que não usamos tanto, mas que estão fazendo nosso editor ficar uma carroça.

<img src="http://tableless.com.br/uploads/2014/02/Screen-Shot-2014-02-27-at-17.27.38.png" alt="Screen Shot 2014-02-27 at 17.27.38" class="alignnone size-full wp-image-41288" srcset="uploads/2014/02/Screen-Shot-2014-02-27-at-17.27.38.png 1138w, uploads/2014/02/Screen-Shot-2014-02-27-at-17.27.38-215x168.png 215w, uploads/2014/02/Screen-Shot-2014-02-27-at-17.27.38-397x310.png 397w, uploads/2014/02/Screen-Shot-2014-02-27-at-17.27.38-400x312.png 400w" sizes="(max-width: 1138px) 100vw, 1138px" />

### Comandos básicos e atalhos

Aqui não tem nenhum segredo porque é tudo muito parecido com o Sublime Text: aperte **cmd+shift+p** e procure o comando desejado. Dá para encontrar ali seus shortcuts/keybindings customizados também.

Com o atalho **cmd+t** você consegue procurar um determinado arquivo no seu projeto. Igual ao Sublime, nem precisa decorar.

### Adicionando, movendo e deletando arquivos

Para manipular os arquivos direto pela tree view, basta selecionar o arquivo e apertar a tecla **a** para adicionar um novo arquivo, **m** para mover e **delete** para deletar o arquivo/pasta.

## Review em vídeo

O [Zeno][1] fez um vídeo, está em inglês, sobre o Atom. Dá uma olhada aí:



## Conclusão

Eu já sai do Sublime e fui pro Atom. Ainda vou continuar acompanhando o Brackets. Existem coisas nele que prometem nos ajudar demais, como essa feature matadora do vídeo abaixo:



Você pode tratar o Atom como um Sublime melhorado&#8230; você não estaria errado. Mas acho que o futuro dele promete e talvez o Sublime não será mais onipresente como hoje.

 [1]: http://zenorocha.com/