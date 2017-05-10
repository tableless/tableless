---
title: Design de Aplicativos para Android – Parte 2
author: Dani Guerrato
type: post
date: 2014-02-05
excerpt: Conheça os pixels independentes e as pilhas de resoluções, aprenda a criar e organizar entregáveis de design e descubra ferramentas úteis para criar seus próprios aplicativos Android.
url: /design-de-aplicativos-para-android-parte-2/
dsq_thread_id: 2223844130
categories:
  - Design
  - Mobile
tags:
  - android
  - design de aplicativos
  - mobile

---
No [primeiro artigo desta série][1], conversamos um pouco sobre a anatomia de um App Android e no que ele difere de outros sistemas operacionais. Hoje vamos nos aprofundar nos aspectos mais técnicos do design de aplicativos. Busque seu café e boa leitura!

## O que é um pixel?

Um pixel é o menor ponto físico em um dispositivo. É uma combinação espertinha de duas palavras pix (como em &#8220;picture&#8221;) e el (como em &#8220;element&#8221;). Ou seja, um pixel é o elemento pelo qual as imagens são criadas.

### Sobre pixels e relatividade

O pixel parece uma unidade fixa quando você escreve códigos CSS, mas na realidade o tamanho físico do pixel varia de acordo com o dispositivo. Isto significa que 1px aqui no meu monitor é diferente do mesmo 1px do seu. Mas não é só o tamanho do pixel que pode mudar de aparelho para aparelho. A quantidade de pixels que cabem em uma mesma área também varia. Como o assunto é meio denso, vamos usar uma metáfora. Imagine pegar uma régua e desenhar com um marcador permanente (É só imaginação. Não vá dizer que eu mandei fazer isto, hein?) um quadrado de 1 polegada em um iPhone 3GS. Agora desenhe o mesmo quadrado em um iPhone 4 que possui tela de alta resolução (que a galera do marketing da Maça resolveu chamar de Retina). Embora os quadrados imaginários sejam do mesmo tamanho, como a densidade de pixels de um monitor HD é maior, temos mais pixels apertadinhos em um mesmo espaço. Esta maravilha da tecnologia permite imagens muito mais bonitas, nítidas e detalhadas… Mas, como tudo tem um preço, o designer de iOS terá que criar duas imagens: uma para a densidade &#8220;base&#8221; e outra para a densidade dobrada.

iOS? Este artigo não é sobre Android? Pois é, amigo, tenho uma má notícia. Os celulares da Apple são todos padronizados então se fossemos separar todos os iPhones do mundo de acordo com a resolução só existiriam duas pilhas: normal e retina (HD). Como o Android é um sistema aberto e democrático existem diversas marcas, cada uma criando aparelhos com a densidade de pixels que está na moda no momento e… Moral da história: existem 6 pilhas de densidade para Android. Cada uma engloba uma determinada faixa de pontos por polegada e é rotulada com uma sigla charmosa. Parece bem mais trabalhoso a princípio. Mas nem tudo está perdido. O segredo para criar um layout que vai manter a consistência em diferentes aparelhos está nos pixels virtuais.

<img class="alignnone size-full wp-image-40536" alt="densidade-de-pixels" src="http://tableless.com.br/uploads/2014/01/densidade-de-pixels.jpg" width="660" height="400" srcset="uploads/2014/01/densidade-de-pixels.jpg 660w, uploads/2014/01/densidade-de-pixels-277x168.jpg 277w, uploads/2014/01/densidade-de-pixels-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Pilhas de densidade

Para simplificar agrupamos as densidade de pixels mais comuns, medidas em DPI (quantidade de pontos por polegadas), em categorias com nomes mais amigáveis. A coluna em negrito é a resolução base (MDPI).

| &nbsp;                        | LDPI   | MDPI             | HDPI   | XHDPI      | XXHDPI           | XXXHDPI                |
| ----------------------------- | ------ | ---------------- | ------ | ---------- | ---------------- | ---------------------- |
| Resolução                     | baixa  | **média (base)** | alta   | extra-alta | extra-extra-alta | extra-extra-extra-alta |
| Densidade                     | 120dpi | **160dpi**       | 240dpi | 320dpi     | 480dpi           | 640dpi                 |
| Escala em relação a base      | 0.75x  | **1x**           | 1.5x   | 2x         | 3x               | 4x                     |
| Distribuição entre aparelhos* | 9.3%   | **23.4%**        | 34.0%  | 21.0%      | 10.6%            | 1.7%                   |

*De acordo com [pesquisa][2] realizada em Janeiro de 2014.

Estas são as categorias ou pilhas de densidade. Nem todos os dispositivos se encaixam perfeitamente em uma destas categorias, por isto devemos sempre arredondar para o valor mais próximo. Por exemplo: um aparelho de 242dpi ainda seria classificado como HDPI.

Eu acrescentei o LDPI nesta tabela para vocês conhecerem, mas o sistema redimensiona os assets para ela automaticamente a partir do HDPI.

## E os tais pixels virtuais?

DP (também chamado de DIP) é uma sigla para Density-independent Pixels, ou seja, Pixel Independente de Resolução. É uma unidade de medida abstrata baseada na densidade da tela e fundamental para criarmos apps para Android. 1dp corresponde a 1px em uma tela de resolução de 160dpi (o MDPI da nossa tabelinha, também conhecido como Resolução Base). Utilizar dp como medida é garantir que os elementos do layout tenham o mesmo tamanho físico independente da resolução. Não importa se no mesmo quadrado cabem 4px ou apenas 1, eles sempre terão o mesmo tamanho físico.

Vamos para um exemplo prático. Se você tiver um ícone em PNG de 32dp (ou 32px na resolução base MDPI) vai precisar das seguintes versões para atender as outras resoluções: 48px (HDPI), 64px (XHDPI), 96px (XXHDPI) e 128px (XXXHDPI). Mas, como vocês podem notar através da tabela, a grande maioria dos usuários (78.4%) se concentra entre as resoluções MDPI-XDHPI. Ou seja, se você tiver que priorizar se concentre nestas três faixas.

<img class="alignnone size-full wp-image-40541" alt="icones-de-acao" src="http://tableless.com.br/uploads/2014/01/icones-de-acao.jpg" width="660" height="400" srcset="uploads/2014/01/icones-de-acao.jpg 660w, uploads/2014/01/icones-de-acao-277x168.jpg 277w, uploads/2014/01/icones-de-acao-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Lembre-se na hora de converter as medidas de sempre arredondar o número se aparecerem casas decimais. Se você partir do pressuposto que 1px é a menor unidade de medida possível não existe meio pixel.

## Qual tamanho devo usar para o artboard do layout?

É aqui que a coisa pega! Por mais que você crie assets em diferentes resoluções utilizando DP, o cliente (e o desenvolvedor) querem ver um mockup ou pelo menos um wireframe simulando o aplicativo final. É preciso escolher um tamanho de canvas para a criação do seu layout. Para isto vamos analisar algumas resoluções comuns.

| MDPI      | HDPI      | XHDPI      | XXHDPI      | XXXHDPI     |
| --------- | --------- | ---------- | ----------- | ----------- |
| 360x640px | 540x960px | 720x1280px | 1920x1080px | 1440x2160px |

Se o seu aplicativo for específico para smartphones podemos nos concentrar nas densidades MDPI, HDPI e XDPI. Você pode começar na resolução MDPI e aumentar seus assets (lembre-se de utilizar vetores para este caso) mas eu, pessoalmente, prefiro começar com um arquivo maior em XDPI (**720x1280px**) e depois criar versões menores dos mesmos assets (75% menor para HDPI e 50% menor para MDPI). Vale ainda acrescentar as barras e botões padrões do Android para ficar mais fácil de visualizar o resultado final.

Se você está criando um aplicativo que servirá também para tablets é importante criar um layout que atenda as demais densidades também. Neste caso comece pelo XXXDPI (1440x2160px).

Atenção: estes tamanhos são apenas generalizações para facilitar o processo criativo e não correspondem necessariamente a dispositivos reais. Existe uma quantidade imensa de tamanhos e formatos de smartphones e tablets e projetar um mock-up para todos seria inviável. Estes formatos são apenas amostras para que você possa visualizar o resultado do projeto. Por isto lembre-se de projetar pensando nos valores em dp.

## Ritmo

A ponta do dedo de uma pessoa tem por volta por volta de 9mm, o que corresponde a cerca de 48dp. Este deve ser portanto o tamanho base dos objetos tocáveis do seu layout para que a interface funcione de maneira confortável e os ícones e botões sejam fáceis de tocar com precisão. Uma margem de 8dp deve ser acrescentada para garantir a separação dos objetos e evitar erros.

48dp é um tamanho legal para definir como grid horizontal do seu layout.

[<img class="alignnone size-full wp-image-40549" alt="ritmo" src="http://tableless.com.br/uploads/2014/01/ritmo.jpg" width="660" height="400" srcset="uploads/2014/01/ritmo.jpg 660w, uploads/2014/01/ritmo-277x168.jpg 277w, uploads/2014/01/ritmo-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][3]

## Tipografia

A família tipográfica padrão do Android 4.4 é a Roboto. A fonte pode ser baixada gratuitamente através do [Google Fonts][4] e vem com uma série de pesos diferentes: thin, light, regular, medium, bold e black e versões condensadas.

[<img class="alignnone size-full wp-image-40546" alt="roboto-font" src="http://tableless.com.br/uploads/2014/01/roboto-font.jpg" width="660" height="400" srcset="uploads/2014/01/roboto-font.jpg 660w, uploads/2014/01/roboto-font-277x168.jpg 277w, uploads/2014/01/roboto-font-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][5]

### SP

A tipografia do seu layout deve seguir uma outra medida: o SP (scaled pixel). Um SP corresponde a 1 dp em escala 100%. Parece a mesma coisa, mas não é. A vantagem do SP é que ele é redimensionável. Ou seja, o usuário poderá aumentar e diminuir o tamanho do texto em SP de acordo com suas preferências. 10sp seriam correspondentes a 11dp se o tamanho do texto estivesse em escala 110%. Esta flexibilidade é uma questão de acessibilidade já que poder redimensionar o texto é fundamental para pessoas com dificuldade de visão.

Para resumir o drama das unidades de medida:
  
&#8211; SP para tipografia.
  
&#8211; DP para todo o resto.
  
&#8211; Fim.

Para garantir a legibilidade a documentação oficial recomenda alguns tamanhos para texto:

<img class="alignnone size-full wp-image-40538" alt="escala-roboto" src="http://tableless.com.br/uploads/2014/01/escala-roboto.jpg" width="660" height="400" srcset="uploads/2014/01/escala-roboto.jpg 660w, uploads/2014/01/escala-roboto-277x168.jpg 277w, uploads/2014/01/escala-roboto-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Lembre-se que, se você tiver usando o Photoshop deve converter o tamanho de acordo com a densidade que escolheu trabalhar. Vamos supor que o seu artboard seja o XDPI (720x1280px). Isto significa 1sp = 2px. Ou seja, o texto de 22sp vai valer 44px e assim por diante.

É possível também implementar fontes customizadas através de um arquivo ttf. Mas esta opção pode deixar o seu app um pouco mais pesado.

## Ícones

[<img class="alignnone size-full wp-image-40542" alt="icones" src="http://tableless.com.br/uploads/2014/01/icones1.jpg" width="660" height="400" srcset="uploads/2014/01/icones1.jpg 660w, uploads/2014/01/icones1-277x168.jpg 277w, uploads/2014/01/icones1-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][6]

### Launcher

Este é o ícone de inicialização do aplicativo a partir da Home. Como este é o primeiro contato que o público terá com a sua marca é interessante incorporar conceitos da sua identidade visual como formas, cores ou até mesmo utilizar o seu logotipo. É importante testar se o ícone permanece visível em diversos tipos de background já que o usuário pode trocar o papel de parede da Home pela imagem que desejar. O launcher icon pode ser utilizando também ao longo da barra de ação em todas as telas do aplicativo.
  
Além das versão padrão de 48dp, é importante criar um Launcher no tamanho 512x512px para ser utilizado na Google Play.

### Ícones de ação

Os ícones da barra de ação precisam ter 32dp. O estilo destes ícones é sólido, sem muitos detalhes, representando claramente uma ação única e ocupando uma área focal de 24dp. A grossura dos traços e espaços negativos deve ter ao menos 2dp. Já existem ícones pré-definidos para diversas ações comuns como compartilhar um conteúdo ou enviar um e-mail, portanto, antes de criar o seu, verifique se não existe um [padrão do sistema][7].

### Ícones contextuais

São ícones pequenos utilizados ao longo do App que servem para mostrar ações secundárias e status de itens. As estrelinhas em e-mails importantes no Gmail são um exemplo de ícone contextual. O estilo deve ser neutro, flat e simples. Prefira formas preenchidas e cores sólidas. Tamanho 16dp e área focal 12dp.

### Ícones de notificação

Utilizados na barra de status para indicar novas notificações para o seu App. Devem ter 24dp, sendo que a área focal deve ser 22dp. A recomendação para estilo é que sejam sólidos, brancos e simples. Procure utilizar uma versão simplificada do símbolo do launcher para facilitar a associação entre a notificação e o seu aplicativo.

### Tabela de conversão

Para facilitar o calculo, consulte esta tabela para descobrir o tamanho de cada tipo de item em pixels.

<table>
  <tr>
    <th>
      Launcher
    </th>
    
    <th>
      Action Icon
    </th>
    
    <th>
      Pequeno / Contextual
    </th>
    
    <th>
      Notificação
    </th>
  </tr>
  
  <tr>
    <td>
      mdpi
    </td>
    
    <td>
      48x48px
    </td>
    
    <td>
      32x32px
    </td>
    
    <td>
      16x16px
    </td>
    
    <td>
      24x24px
    </td>
  </tr>
  
  <tr>
    <td>
      hdpi
    </td>
    
    <td>
      72x72px
    </td>
    
    <td>
      48x48px
    </td>
    
    <td>
      24x24px
    </td>
    
    <td>
      36x36px
    </td>
  </tr>
  
  <tr>
    <td>
      xhdpi
    </td>
    
    <td>
      96x96px
    </td>
    
    <td>
      64x64px
    </td>
    
    <td>
      32x32px
    </td>
    
    <td>
      48x48px
    </td>
  </tr>
  
  <tr>
    <td>
      xxhdpi
    </td>
    
    <td>
      144x144px
    </td>
    
    <td>
      96x96px
    </td>
    
    <td>
      48x48px
    </td>
    
    <td>
      72x72px
    </td>
  </tr>
</table>

## Organizando os assets

### Convenções de nomenclatura

Existem alguns padrões para nomear os assets que são úteis na hora de encontrar o arquivo que você precisa dentro de uma pasta. Estes são alguns dos prefixos comuns:

| Tipo de asset             | Prefixo             | Exemplo                     |
| ------------------------- | ------------------- | --------------------------- |
| Ícone                     | ic_                 | ic_estrela.png              |
| Launcher                  | ic_launcher         | ic\_launcher\_nomedoapp.png |
| Ícones da action bar      | ic_menu             | ic\_menu\_busca.png         |
| Ícones da barra de status | ic\_stat\_notificar | ic\_stat\_notificar_msg.png |
| Ícones das tabs           | ic_tab              | ic\_tab\_recente.png        |
| Ícones de dialogo         | ic_dialog           | ic\_dialog\_info.png        |

### Estrutura de diretório

Separe os ícones em pastas de acordo com a densidade. Lembre-se de utilizar o mesmo nome para as diferentes versões do mesmo ícone para facilitar na hora de encontrar o asset que você precisa.

<img class="alignnone size-full wp-image-40539" alt="estritura-de-pastas" src="http://tableless.com.br/uploads/2014/01/estritura-de-pastas.jpg" width="660" height="400" srcset="uploads/2014/01/estritura-de-pastas.jpg 660w, uploads/2014/01/estritura-de-pastas-277x168.jpg 277w, uploads/2014/01/estritura-de-pastas-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Branding

Além dos ícones e do seu logotipo existe um grande espaço para você reforçar o branding dentro de um aplicativo. Elementos da interface como checkboxes, radio buttons, barras de progresso, abas e sliders podem ser personalizados para refletir a identidade visual da sua marca.

### Botões

Para botões formados apenas por imagens não é necessario utilizar um background. O mesmo vale para botões formados por texto. Uma frase demonstrando a ação claramente (como &#8220;Iniciar&#8221; ou &#8220;Login&#8221;) juntamente como cores, peso ou tipografia diferente já é suficiente para sinalizar ao usuário que é possível interagir com o objeto.

A recomendação da [documentação oficia][8]l é evitar utilizar backgrounds para os botões já que a aparência deles tende a deixar o visual do app mais pesado. O ideal é deixar um ou dois no máximo para os seguintes casos: call to action (ex: cadastrar), decisão chave (ex: aceitar ou rejeitar) ou ação significativa (ex: comprar agora, deletar).

## Entregáveis

1. Wireframe ou mock-up na resolução de tela e densidade de pixels de sua preferência. Se desejar inclua também versões retrato e paisagens e um layout alternativo para tablets.
  
2. Imagens bitmap recortadas em tamanhos diferentes para todas as densidades que você decidir atender (no mínimo três versões: MDPI, HDPI e XDPI). Arquivos transparentes devem estar em png.
  
3. Especificações de tamanhos de itens e espaçamento (na unidade DP), tipografia (tamanhos em SP), cores e variações dos itens para comportamentos ativo, inativo, no momento de toque, etc. Esta documentação pode ser em um arquivo de texto organizadinho, anotações nas imagens do layout ou até mesmo um [Guia de Estilos][9] completo.

## Ferramentas

Seguindo estas etapas seu trabalho está concluído!  Abaixo eu separei algumas ferramentas úteis para auxiliar cada processo. Para mais dicas não esqueça de consultar a [documentação oficial][10]. Até a próxima!

### Android Downloads

A seção [Android Downloads][11] da documentação oficial conta com diversos itens úteis: kit de stencils para wireframes, ícones de ação em formato vetor e bitmap, paleta de cores e guia sobre a fonte Roboto. Vale a sua visita!

[<img class="alignnone size-full wp-image-40531" alt="android-developers-downloads" src="http://tableless.com.br/uploads/2014/01/android-developers-downloads.jpg" width="660" height="400" srcset="uploads/2014/01/android-developers-downloads.jpg 660w, uploads/2014/01/android-developers-downloads-277x168.jpg 277w, uploads/2014/01/android-developers-downloads-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][12]

### Android UI Design Kit for Photoshop

O kit [Android UI][13] em formato Photoshop tem versões dos elementos da user interface do Android 4.4 prontinho para você utilizar. São barrinhas, campos de formulário, abas, botões do sistema, enfim, uma série de recursos super úteis para você desenvolver o layout do seu aplicativo. O arquivo é sempre atualizado para máxima compatibilidade com a última versão do sistema operacional.

[<img class="alignnone size-full wp-image-40533" alt="android-ui-design-kit" src="http://tableless.com.br/uploads/2014/01/android-ui-design-kit.jpg" width="660" height="400" srcset="uploads/2014/01/android-ui-design-kit.jpg 660w, uploads/2014/01/android-ui-design-kit-277x168.jpg 277w, uploads/2014/01/android-ui-design-kit-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][14]

### Android Developers

Se você prefere assistir vídeo aulas, dê uma olhada no canal do Youtube [Android Developers][15], principalmente na série Design Bytes. São vídeo curtos e gratuitos que dão uma série de pinceladas úteis sobre as melhores práticas. A maior parte dos vídeos está em inglês, mas alguns já estão sendo nacionalizados.

[<img class="alignnone size-full wp-image-40532" alt="android-developers" src="http://tableless.com.br/uploads/2014/01/android-developers.jpg" width="660" height="400" srcset="uploads/2014/01/android-developers.jpg 660w, uploads/2014/01/android-developers-277x168.jpg 277w, uploads/2014/01/android-developers-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][16]

### Conversores de densidade

Se você ficou meio perdido para converter medidas de pixel para dp, dê uma olhada nestas calculadoras online. Basta definir um valor em pixel para obter as medidas proporcionais em MDPI, HDPI e XHDPI. Mais fácil do que falar mal do IE6.

[Teehanlax Density Converter][17]
  
[Android DPI Calculator][18]

[<img class="alignnone size-full wp-image-40537" alt="density-converter" src="http://tableless.com.br/uploads/2014/01/density-converter.jpg" width="660" height="400" srcset="uploads/2014/01/density-converter.jpg 660w, uploads/2014/01/density-converter-277x168.jpg 277w, uploads/2014/01/density-converter-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][19]

### Android App Icon Template

O [App Icon Template][20] é um arquivo de Photoshop com smart objects para que você possa criar e visualizar seu launcher icon renderizado na tela inicial do Android. O pacote ainda acompanha texturas, linhas guias e actions para automatizar o processo de exportar o ícone para diversas densidades de tela. Existe também uma versão do mesmo template para iOS.

[<img class="alignnone size-full wp-image-40534" alt="app-icon-template" src="http://tableless.com.br/uploads/2014/01/app-icon-template.jpg" width="660" height="400" srcset="uploads/2014/01/app-icon-template.jpg 660w, uploads/2014/01/app-icon-template-277x168.jpg 277w, uploads/2014/01/app-icon-template-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][21]

### Android Asset Studio

Se você é um desenvolvedor e não entende nada de design o [Android Asset Studio][22] pode ser útil para você. A ferramenta é um kit com diversos geradores para criar os assets básicos de interfaces Android. Basta customizar as cores, definir um estilo para os itens e baixar os arquivos. O kit de ferramentas conta ainda com um gerador de ícones, gaveta de navegação e frames de smartphones para apresentar o seu layout. Não dá para criar nada especialmente genial, mas é um bom ponto de partida se você deseja criar uma aplicação simples.

[<img class="alignnone size-full wp-image-40535" alt="asset-studio" src="http://tableless.com.br/uploads/2014/01/asset-studio.jpg" width="660" height="400" srcset="uploads/2014/01/asset-studio.jpg 660w, uploads/2014/01/asset-studio-277x168.jpg 277w, uploads/2014/01/asset-studio-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][23]

### Fluid UI

Esta ferramenta é bem interessante para criar wireframes e fluxogramas online. O [No [primeiro artigo desta série][1], conversamos um pouco sobre a anatomia de um App Android e no que ele difere de outros sistemas operacionais. Hoje vamos nos aprofundar nos aspectos mais técnicos do design de aplicativos. Busque seu café e boa leitura!

## O que é um pixel?

Um pixel é o menor ponto físico em um dispositivo. É uma combinação espertinha de duas palavras pix (como em &#8220;picture&#8221;) e el (como em &#8220;element&#8221;). Ou seja, um pixel é o elemento pelo qual as imagens são criadas.

### Sobre pixels e relatividade

O pixel parece uma unidade fixa quando você escreve códigos CSS, mas na realidade o tamanho físico do pixel varia de acordo com o dispositivo. Isto significa que 1px aqui no meu monitor é diferente do mesmo 1px do seu. Mas não é só o tamanho do pixel que pode mudar de aparelho para aparelho. A quantidade de pixels que cabem em uma mesma área também varia. Como o assunto é meio denso, vamos usar uma metáfora. Imagine pegar uma régua e desenhar com um marcador permanente (É só imaginação. Não vá dizer que eu mandei fazer isto, hein?) um quadrado de 1 polegada em um iPhone 3GS. Agora desenhe o mesmo quadrado em um iPhone 4 que possui tela de alta resolução (que a galera do marketing da Maça resolveu chamar de Retina). Embora os quadrados imaginários sejam do mesmo tamanho, como a densidade de pixels de um monitor HD é maior, temos mais pixels apertadinhos em um mesmo espaço. Esta maravilha da tecnologia permite imagens muito mais bonitas, nítidas e detalhadas… Mas, como tudo tem um preço, o designer de iOS terá que criar duas imagens: uma para a densidade &#8220;base&#8221; e outra para a densidade dobrada.

iOS? Este artigo não é sobre Android? Pois é, amigo, tenho uma má notícia. Os celulares da Apple são todos padronizados então se fossemos separar todos os iPhones do mundo de acordo com a resolução só existiriam duas pilhas: normal e retina (HD). Como o Android é um sistema aberto e democrático existem diversas marcas, cada uma criando aparelhos com a densidade de pixels que está na moda no momento e… Moral da história: existem 6 pilhas de densidade para Android. Cada uma engloba uma determinada faixa de pontos por polegada e é rotulada com uma sigla charmosa. Parece bem mais trabalhoso a princípio. Mas nem tudo está perdido. O segredo para criar um layout que vai manter a consistência em diferentes aparelhos está nos pixels virtuais.

<img class="alignnone size-full wp-image-40536" alt="densidade-de-pixels" src="http://tableless.com.br/uploads/2014/01/densidade-de-pixels.jpg" width="660" height="400" srcset="uploads/2014/01/densidade-de-pixels.jpg 660w, uploads/2014/01/densidade-de-pixels-277x168.jpg 277w, uploads/2014/01/densidade-de-pixels-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Pilhas de densidade

Para simplificar agrupamos as densidade de pixels mais comuns, medidas em DPI (quantidade de pontos por polegadas), em categorias com nomes mais amigáveis. A coluna em negrito é a resolução base (MDPI).

| &nbsp;                        | LDPI   | MDPI             | HDPI   | XHDPI      | XXHDPI           | XXXHDPI                |
| ----------------------------- | ------ | ---------------- | ------ | ---------- | ---------------- | ---------------------- |
| Resolução                     | baixa  | **média (base)** | alta   | extra-alta | extra-extra-alta | extra-extra-extra-alta |
| Densidade                     | 120dpi | **160dpi**       | 240dpi | 320dpi     | 480dpi           | 640dpi                 |
| Escala em relação a base      | 0.75x  | **1x**           | 1.5x   | 2x         | 3x               | 4x                     |
| Distribuição entre aparelhos* | 9.3%   | **23.4%**        | 34.0%  | 21.0%      | 10.6%            | 1.7%                   |

*De acordo com [pesquisa][2] realizada em Janeiro de 2014.

Estas são as categorias ou pilhas de densidade. Nem todos os dispositivos se encaixam perfeitamente em uma destas categorias, por isto devemos sempre arredondar para o valor mais próximo. Por exemplo: um aparelho de 242dpi ainda seria classificado como HDPI.

Eu acrescentei o LDPI nesta tabela para vocês conhecerem, mas o sistema redimensiona os assets para ela automaticamente a partir do HDPI.

## E os tais pixels virtuais?

DP (também chamado de DIP) é uma sigla para Density-independent Pixels, ou seja, Pixel Independente de Resolução. É uma unidade de medida abstrata baseada na densidade da tela e fundamental para criarmos apps para Android. 1dp corresponde a 1px em uma tela de resolução de 160dpi (o MDPI da nossa tabelinha, também conhecido como Resolução Base). Utilizar dp como medida é garantir que os elementos do layout tenham o mesmo tamanho físico independente da resolução. Não importa se no mesmo quadrado cabem 4px ou apenas 1, eles sempre terão o mesmo tamanho físico.

Vamos para um exemplo prático. Se você tiver um ícone em PNG de 32dp (ou 32px na resolução base MDPI) vai precisar das seguintes versões para atender as outras resoluções: 48px (HDPI), 64px (XHDPI), 96px (XXHDPI) e 128px (XXXHDPI). Mas, como vocês podem notar através da tabela, a grande maioria dos usuários (78.4%) se concentra entre as resoluções MDPI-XDHPI. Ou seja, se você tiver que priorizar se concentre nestas três faixas.

<img class="alignnone size-full wp-image-40541" alt="icones-de-acao" src="http://tableless.com.br/uploads/2014/01/icones-de-acao.jpg" width="660" height="400" srcset="uploads/2014/01/icones-de-acao.jpg 660w, uploads/2014/01/icones-de-acao-277x168.jpg 277w, uploads/2014/01/icones-de-acao-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Lembre-se na hora de converter as medidas de sempre arredondar o número se aparecerem casas decimais. Se você partir do pressuposto que 1px é a menor unidade de medida possível não existe meio pixel.

## Qual tamanho devo usar para o artboard do layout?

É aqui que a coisa pega! Por mais que você crie assets em diferentes resoluções utilizando DP, o cliente (e o desenvolvedor) querem ver um mockup ou pelo menos um wireframe simulando o aplicativo final. É preciso escolher um tamanho de canvas para a criação do seu layout. Para isto vamos analisar algumas resoluções comuns.

| MDPI      | HDPI      | XHDPI      | XXHDPI      | XXXHDPI     |
| --------- | --------- | ---------- | ----------- | ----------- |
| 360x640px | 540x960px | 720x1280px | 1920x1080px | 1440x2160px |

Se o seu aplicativo for específico para smartphones podemos nos concentrar nas densidades MDPI, HDPI e XDPI. Você pode começar na resolução MDPI e aumentar seus assets (lembre-se de utilizar vetores para este caso) mas eu, pessoalmente, prefiro começar com um arquivo maior em XDPI (**720x1280px**) e depois criar versões menores dos mesmos assets (75% menor para HDPI e 50% menor para MDPI). Vale ainda acrescentar as barras e botões padrões do Android para ficar mais fácil de visualizar o resultado final.

Se você está criando um aplicativo que servirá também para tablets é importante criar um layout que atenda as demais densidades também. Neste caso comece pelo XXXDPI (1440x2160px).

Atenção: estes tamanhos são apenas generalizações para facilitar o processo criativo e não correspondem necessariamente a dispositivos reais. Existe uma quantidade imensa de tamanhos e formatos de smartphones e tablets e projetar um mock-up para todos seria inviável. Estes formatos são apenas amostras para que você possa visualizar o resultado do projeto. Por isto lembre-se de projetar pensando nos valores em dp.

## Ritmo

A ponta do dedo de uma pessoa tem por volta por volta de 9mm, o que corresponde a cerca de 48dp. Este deve ser portanto o tamanho base dos objetos tocáveis do seu layout para que a interface funcione de maneira confortável e os ícones e botões sejam fáceis de tocar com precisão. Uma margem de 8dp deve ser acrescentada para garantir a separação dos objetos e evitar erros.

48dp é um tamanho legal para definir como grid horizontal do seu layout.

[<img class="alignnone size-full wp-image-40549" alt="ritmo" src="http://tableless.com.br/uploads/2014/01/ritmo.jpg" width="660" height="400" srcset="uploads/2014/01/ritmo.jpg 660w, uploads/2014/01/ritmo-277x168.jpg 277w, uploads/2014/01/ritmo-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][3]

## Tipografia

A família tipográfica padrão do Android 4.4 é a Roboto. A fonte pode ser baixada gratuitamente através do [Google Fonts][4] e vem com uma série de pesos diferentes: thin, light, regular, medium, bold e black e versões condensadas.

[<img class="alignnone size-full wp-image-40546" alt="roboto-font" src="http://tableless.com.br/uploads/2014/01/roboto-font.jpg" width="660" height="400" srcset="uploads/2014/01/roboto-font.jpg 660w, uploads/2014/01/roboto-font-277x168.jpg 277w, uploads/2014/01/roboto-font-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][5]

### SP

A tipografia do seu layout deve seguir uma outra medida: o SP (scaled pixel). Um SP corresponde a 1 dp em escala 100%. Parece a mesma coisa, mas não é. A vantagem do SP é que ele é redimensionável. Ou seja, o usuário poderá aumentar e diminuir o tamanho do texto em SP de acordo com suas preferências. 10sp seriam correspondentes a 11dp se o tamanho do texto estivesse em escala 110%. Esta flexibilidade é uma questão de acessibilidade já que poder redimensionar o texto é fundamental para pessoas com dificuldade de visão.

Para resumir o drama das unidades de medida:
  
&#8211; SP para tipografia.
  
&#8211; DP para todo o resto.
  
&#8211; Fim.

Para garantir a legibilidade a documentação oficial recomenda alguns tamanhos para texto:

<img class="alignnone size-full wp-image-40538" alt="escala-roboto" src="http://tableless.com.br/uploads/2014/01/escala-roboto.jpg" width="660" height="400" srcset="uploads/2014/01/escala-roboto.jpg 660w, uploads/2014/01/escala-roboto-277x168.jpg 277w, uploads/2014/01/escala-roboto-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Lembre-se que, se você tiver usando o Photoshop deve converter o tamanho de acordo com a densidade que escolheu trabalhar. Vamos supor que o seu artboard seja o XDPI (720x1280px). Isto significa 1sp = 2px. Ou seja, o texto de 22sp vai valer 44px e assim por diante.

É possível também implementar fontes customizadas através de um arquivo ttf. Mas esta opção pode deixar o seu app um pouco mais pesado.

## Ícones

[<img class="alignnone size-full wp-image-40542" alt="icones" src="http://tableless.com.br/uploads/2014/01/icones1.jpg" width="660" height="400" srcset="uploads/2014/01/icones1.jpg 660w, uploads/2014/01/icones1-277x168.jpg 277w, uploads/2014/01/icones1-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][6]

### Launcher

Este é o ícone de inicialização do aplicativo a partir da Home. Como este é o primeiro contato que o público terá com a sua marca é interessante incorporar conceitos da sua identidade visual como formas, cores ou até mesmo utilizar o seu logotipo. É importante testar se o ícone permanece visível em diversos tipos de background já que o usuário pode trocar o papel de parede da Home pela imagem que desejar. O launcher icon pode ser utilizando também ao longo da barra de ação em todas as telas do aplicativo.
  
Além das versão padrão de 48dp, é importante criar um Launcher no tamanho 512x512px para ser utilizado na Google Play.

### Ícones de ação

Os ícones da barra de ação precisam ter 32dp. O estilo destes ícones é sólido, sem muitos detalhes, representando claramente uma ação única e ocupando uma área focal de 24dp. A grossura dos traços e espaços negativos deve ter ao menos 2dp. Já existem ícones pré-definidos para diversas ações comuns como compartilhar um conteúdo ou enviar um e-mail, portanto, antes de criar o seu, verifique se não existe um [padrão do sistema][7].

### Ícones contextuais

São ícones pequenos utilizados ao longo do App que servem para mostrar ações secundárias e status de itens. As estrelinhas em e-mails importantes no Gmail são um exemplo de ícone contextual. O estilo deve ser neutro, flat e simples. Prefira formas preenchidas e cores sólidas. Tamanho 16dp e área focal 12dp.

### Ícones de notificação

Utilizados na barra de status para indicar novas notificações para o seu App. Devem ter 24dp, sendo que a área focal deve ser 22dp. A recomendação para estilo é que sejam sólidos, brancos e simples. Procure utilizar uma versão simplificada do símbolo do launcher para facilitar a associação entre a notificação e o seu aplicativo.

### Tabela de conversão

Para facilitar o calculo, consulte esta tabela para descobrir o tamanho de cada tipo de item em pixels.

<table>
  <tr>
    <th>
      Launcher
    </th>
    
    <th>
      Action Icon
    </th>
    
    <th>
      Pequeno / Contextual
    </th>
    
    <th>
      Notificação
    </th>
  </tr>
  
  <tr>
    <td>
      mdpi
    </td>
    
    <td>
      48x48px
    </td>
    
    <td>
      32x32px
    </td>
    
    <td>
      16x16px
    </td>
    
    <td>
      24x24px
    </td>
  </tr>
  
  <tr>
    <td>
      hdpi
    </td>
    
    <td>
      72x72px
    </td>
    
    <td>
      48x48px
    </td>
    
    <td>
      24x24px
    </td>
    
    <td>
      36x36px
    </td>
  </tr>
  
  <tr>
    <td>
      xhdpi
    </td>
    
    <td>
      96x96px
    </td>
    
    <td>
      64x64px
    </td>
    
    <td>
      32x32px
    </td>
    
    <td>
      48x48px
    </td>
  </tr>
  
  <tr>
    <td>
      xxhdpi
    </td>
    
    <td>
      144x144px
    </td>
    
    <td>
      96x96px
    </td>
    
    <td>
      48x48px
    </td>
    
    <td>
      72x72px
    </td>
  </tr>
</table>

## Organizando os assets

### Convenções de nomenclatura

Existem alguns padrões para nomear os assets que são úteis na hora de encontrar o arquivo que você precisa dentro de uma pasta. Estes são alguns dos prefixos comuns:

| Tipo de asset             | Prefixo             | Exemplo                     |
| ------------------------- | ------------------- | --------------------------- |
| Ícone                     | ic_                 | ic_estrela.png              |
| Launcher                  | ic_launcher         | ic\_launcher\_nomedoapp.png |
| Ícones da action bar      | ic_menu             | ic\_menu\_busca.png         |
| Ícones da barra de status | ic\_stat\_notificar | ic\_stat\_notificar_msg.png |
| Ícones das tabs           | ic_tab              | ic\_tab\_recente.png        |
| Ícones de dialogo         | ic_dialog           | ic\_dialog\_info.png        |

### Estrutura de diretório

Separe os ícones em pastas de acordo com a densidade. Lembre-se de utilizar o mesmo nome para as diferentes versões do mesmo ícone para facilitar na hora de encontrar o asset que você precisa.

<img class="alignnone size-full wp-image-40539" alt="estritura-de-pastas" src="http://tableless.com.br/uploads/2014/01/estritura-de-pastas.jpg" width="660" height="400" srcset="uploads/2014/01/estritura-de-pastas.jpg 660w, uploads/2014/01/estritura-de-pastas-277x168.jpg 277w, uploads/2014/01/estritura-de-pastas-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Branding

Além dos ícones e do seu logotipo existe um grande espaço para você reforçar o branding dentro de um aplicativo. Elementos da interface como checkboxes, radio buttons, barras de progresso, abas e sliders podem ser personalizados para refletir a identidade visual da sua marca.

### Botões

Para botões formados apenas por imagens não é necessario utilizar um background. O mesmo vale para botões formados por texto. Uma frase demonstrando a ação claramente (como &#8220;Iniciar&#8221; ou &#8220;Login&#8221;) juntamente como cores, peso ou tipografia diferente já é suficiente para sinalizar ao usuário que é possível interagir com o objeto.

A recomendação da [documentação oficia][8]l é evitar utilizar backgrounds para os botões já que a aparência deles tende a deixar o visual do app mais pesado. O ideal é deixar um ou dois no máximo para os seguintes casos: call to action (ex: cadastrar), decisão chave (ex: aceitar ou rejeitar) ou ação significativa (ex: comprar agora, deletar).

## Entregáveis

1. Wireframe ou mock-up na resolução de tela e densidade de pixels de sua preferência. Se desejar inclua também versões retrato e paisagens e um layout alternativo para tablets.
  
2. Imagens bitmap recortadas em tamanhos diferentes para todas as densidades que você decidir atender (no mínimo três versões: MDPI, HDPI e XDPI). Arquivos transparentes devem estar em png.
  
3. Especificações de tamanhos de itens e espaçamento (na unidade DP), tipografia (tamanhos em SP), cores e variações dos itens para comportamentos ativo, inativo, no momento de toque, etc. Esta documentação pode ser em um arquivo de texto organizadinho, anotações nas imagens do layout ou até mesmo um [Guia de Estilos][9] completo.

## Ferramentas

Seguindo estas etapas seu trabalho está concluído!  Abaixo eu separei algumas ferramentas úteis para auxiliar cada processo. Para mais dicas não esqueça de consultar a [documentação oficial][10]. Até a próxima!

### Android Downloads

A seção [Android Downloads][11] da documentação oficial conta com diversos itens úteis: kit de stencils para wireframes, ícones de ação em formato vetor e bitmap, paleta de cores e guia sobre a fonte Roboto. Vale a sua visita!

[<img class="alignnone size-full wp-image-40531" alt="android-developers-downloads" src="http://tableless.com.br/uploads/2014/01/android-developers-downloads.jpg" width="660" height="400" srcset="uploads/2014/01/android-developers-downloads.jpg 660w, uploads/2014/01/android-developers-downloads-277x168.jpg 277w, uploads/2014/01/android-developers-downloads-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][12]

### Android UI Design Kit for Photoshop

O kit [Android UI][13] em formato Photoshop tem versões dos elementos da user interface do Android 4.4 prontinho para você utilizar. São barrinhas, campos de formulário, abas, botões do sistema, enfim, uma série de recursos super úteis para você desenvolver o layout do seu aplicativo. O arquivo é sempre atualizado para máxima compatibilidade com a última versão do sistema operacional.

[<img class="alignnone size-full wp-image-40533" alt="android-ui-design-kit" src="http://tableless.com.br/uploads/2014/01/android-ui-design-kit.jpg" width="660" height="400" srcset="uploads/2014/01/android-ui-design-kit.jpg 660w, uploads/2014/01/android-ui-design-kit-277x168.jpg 277w, uploads/2014/01/android-ui-design-kit-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][14]

### Android Developers

Se você prefere assistir vídeo aulas, dê uma olhada no canal do Youtube [Android Developers][15], principalmente na série Design Bytes. São vídeo curtos e gratuitos que dão uma série de pinceladas úteis sobre as melhores práticas. A maior parte dos vídeos está em inglês, mas alguns já estão sendo nacionalizados.

[<img class="alignnone size-full wp-image-40532" alt="android-developers" src="http://tableless.com.br/uploads/2014/01/android-developers.jpg" width="660" height="400" srcset="uploads/2014/01/android-developers.jpg 660w, uploads/2014/01/android-developers-277x168.jpg 277w, uploads/2014/01/android-developers-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][16]

### Conversores de densidade

Se você ficou meio perdido para converter medidas de pixel para dp, dê uma olhada nestas calculadoras online. Basta definir um valor em pixel para obter as medidas proporcionais em MDPI, HDPI e XHDPI. Mais fácil do que falar mal do IE6.

[Teehanlax Density Converter][17]
  
[Android DPI Calculator][18]

[<img class="alignnone size-full wp-image-40537" alt="density-converter" src="http://tableless.com.br/uploads/2014/01/density-converter.jpg" width="660" height="400" srcset="uploads/2014/01/density-converter.jpg 660w, uploads/2014/01/density-converter-277x168.jpg 277w, uploads/2014/01/density-converter-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][19]

### Android App Icon Template

O [App Icon Template][20] é um arquivo de Photoshop com smart objects para que você possa criar e visualizar seu launcher icon renderizado na tela inicial do Android. O pacote ainda acompanha texturas, linhas guias e actions para automatizar o processo de exportar o ícone para diversas densidades de tela. Existe também uma versão do mesmo template para iOS.

[<img class="alignnone size-full wp-image-40534" alt="app-icon-template" src="http://tableless.com.br/uploads/2014/01/app-icon-template.jpg" width="660" height="400" srcset="uploads/2014/01/app-icon-template.jpg 660w, uploads/2014/01/app-icon-template-277x168.jpg 277w, uploads/2014/01/app-icon-template-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][21]

### Android Asset Studio

Se você é um desenvolvedor e não entende nada de design o [Android Asset Studio][22] pode ser útil para você. A ferramenta é um kit com diversos geradores para criar os assets básicos de interfaces Android. Basta customizar as cores, definir um estilo para os itens e baixar os arquivos. O kit de ferramentas conta ainda com um gerador de ícones, gaveta de navegação e frames de smartphones para apresentar o seu layout. Não dá para criar nada especialmente genial, mas é um bom ponto de partida se você deseja criar uma aplicação simples.

[<img class="alignnone size-full wp-image-40535" alt="asset-studio" src="http://tableless.com.br/uploads/2014/01/asset-studio.jpg" width="660" height="400" srcset="uploads/2014/01/asset-studio.jpg 660w, uploads/2014/01/asset-studio-277x168.jpg 277w, uploads/2014/01/asset-studio-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][23]

### Fluid UI

Esta ferramenta é bem interessante para criar wireframes e fluxogramas online. O][24] conta com diversos elementos comuns de uma interface Android em um esquema drag and drop para você criar rascunhos com velocidade. O plano gratuito permite criar até 10 telas, mas existem outros planos pagos ilimitados.

[<img class="alignnone size-full wp-image-40540" alt="fluidui" src="http://tableless.com.br/uploads/2014/01/fluidui.jpg" width="660" height="400" srcset="uploads/2014/01/fluidui.jpg 660w, uploads/2014/01/fluidui-277x168.jpg 277w, uploads/2014/01/fluidui-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />][25]

### Saiba mais

[Documentação oficial][10]
  
[How to design for Android Devices][26]

 [1]: http://tableless.com.br/design-de-aplicativos-para-android-parte-1/ "Design de Aplicativos para Android – Parte 1"
 [2]: http://developer.android.com/about/dashboards/index.html "Developer Android - Dashboards"
 [3]: http://developer.android.com/design/style/metrics-grids.html
 [4]: http://www.google.com/fonts/specimen/Roboto "Roboto - Google Fonts"
 [5]: http://developer.android.com/design/style/typography.html
 [6]: http://developer.android.com/design/style/iconography.html
 [7]: http://developer.android.com/design/style/iconography.html "Developer Android - Iconography"
 [8]: http://developer.android.com/design/building-blocks/buttons.html "Android Developer - Buttons"
 [9]: http://tableless.com.br/guia-de-estilos/ "Guia de Estilos"
 [10]: http://developer.android.com/design "Android Developer - Design"
 [11]: http://developer.android.com/design/downloads/index.html "Android Developer - Downloads"
 [12]: http://developer.android.com/design/downloads/index.html
 [13]: http://androiduiux.com/2014/01/10/android-ui-design-kit-for-photoshop-4-4-free-download/ "Android UI"
 [14]: http://androiduiux.com/2014/01/10/android-ui-design-kit-for-photoshop-4-4-free-download/
 [15]: https://www.youtube.com/user/androiddevelopers "Android Developers"
 [16]: https://www.youtube.com/user/androiddevelopers
 [17]: http://www.teehanlax.com/blog/density-converter/ "Teehanlax density converter"
 [18]: http://coh.io/adpi/ "Android DPI Calculator"
 [19]: http://www.teehanlax.com/blog/density-converter/
 [20]: http://appicontemplate.com/android "Android App Icon Template"
 [21]: http://appicontemplate.com/android
 [22]: http://android-ui-utils.googlecode.com/hg/asset-studio/dist/index.html "Android Asset Studio"
 [23]: http://android-ui-utils.googlecode.com/hg/asset-studio/dist/index.html
 [24]: https://www.fluidui.com/ "Fluid UI"
 [25]: https://www.fluidui.com/
 [26]: http://blog.mengto.com/how-to-design-for-android-devices/ "How to design for Android devices"