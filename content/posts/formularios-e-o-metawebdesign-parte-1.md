---
title: Formulários e o Metawebdesign – Parte 1
author: Alysson Franklin
type: post
date: 2011-10-24
excerpt: Como montar formulários quando você é o responsável pelo código e design.
url: /formularios-e-o-metawebdesign-parte-1/
tweetbackscheck:
  - 1356448296
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4395";s:7:"tinyurl";s:26:"http://tinyurl.com/3njzcem";s:4:"isgd";s:19:"http://is.gd/DgzPgF";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503017121
categories:
  - Acessibilidade
  - Artigos
  - Código
  - CSS
  - HTML
  - JavaScript
  - JQuery
  - Mercado e Comportamento
  - Tecnologia e Tendências
tags:
  - design de interação
  - design de interface
  - metawebdesign

---
O front-end é uma profissão de uma amplitude imensa. Temos profissionais montando mockups/PSDs, especialistas em acessibilidade, usabilidade, arquitetura da informação, integração com aplicações, designers de interface, application developers. Tem até SEO.

O background do profissional neste momento não importa muito, apenas a afirmação que ele está trabalhando na camada de **front-end**. Só isso basta para confirmar os papéis acima.

Em muitas empresas o front-end é trabalhado de maneira criteriosa, com **separação de tarefas** em maior ou menor intensidade, de modo que o **processo** esteja sempre azeitado e atento aos **prazos** dos outros times que dependem da interface. Em algumas outras, o responsável pelo código é o unico responsável por fazer tudo isso acima. E isso acontece com **frequência**.

É o famigerado exército-de-um-homem-só, que em um projeto normalmente é responsável por:

  * **Pesquisa: **Fornece dados e insights para o desenvolvimento de todo o projeto – sobre o usuário, suas características, hábitos e necessidades. Apesar de orientada a um projeto específico, essa pesquisa também deve ser constante, oferecendo atualização e embasamento para a criação de novas experiências.
  * **Arquitetura da informação:** Organização de informação, entendendo o modelo mental do usuário, para que ele se reflita também no produto final.
  * **Design da interação: **Desenhar a interação de forma que ela seja consistente, fácil e auto-explicativa. Entende ros requisitos de usabilidade criados na fase de **pesquisa** e dominar os padrões de interação que a aplicação deve ter, além de saber lidar com a multiplicidade de devices e plataformas onde a interação ocorre.
  * **Design Visual: **Balanceando beleza e comunicação, domina tanto a direção de arte do produto que está sendo desenvolvido quanto o acabamento final dos pequenos detalhes da interface.
  * **Redação: **Expressar as ideias, simples ou complexas que o cliente passou para o desenvolvedor em palavras simples e que sejam facilmente entendidas pelos usuários do produto. Este conteúdo vem do cliente, mas não é difícil acontecer  do desenvolvedor ser responsável por criar algum conteúdo, seja transformando a linguagem do cliente dentro de um contexto web, deixando-a mais dinâmica e convidativa a leitura, seja pequenos conteúdos que devem ditar padrões visuais para interações do usuário.
  * **Prototipagem:  **Criação da UI. Isso serve tanto para o estágio inicial do projeto (com protótipos de papel, de baixa fidelidade) quanto para o estágio que precede o desenvolvimento, onde o produto já está mais amadurecido e mais próximo do final. Esta etapa pode ser a da criação das páginas em si, uma vez que os modelos de conceito e interação estão prontos e o design está criado ( sites tipicamente estáticos ou de menor porte ) ou pode ser a fase da criação dos protótipos que devem ir para a integração depois (back-end).**
  
** 
  * **Gerenciamento:** Garantir o funcionamento de todas as áreas de entrega da melhor e mais produtiva maneira possivel. E ainda ser o ponto focal com cliente e usuário, quando necessário.

Em um departamento multidisciplinar de UX, no melhor dos mundos, temos atribuições diferentes para diferentes profissionais. Muitas vezes, isso não acontece. Outros casos, não raros, a empresa não está interessada na matéria, ou apenas não tem profissionais que atuam nesta área que se preocupam com o código (e design) que entregam. Vai saber. Em empresas com atribuções de projeto mais estruturadas um departamento de UX conversa claramente com outros áreas, como Arquitetura, DBA, Requisitos, Integração, Testes e Gerência.

No [FrontInBH][1], conversando com os desenvolvedores no final do evento, e também em conversas com _devs_ de todos os cantos, é fácil perceber que empresas com equipes de desenvolvimento reduzidas (SMB, agências, pequenos portais) mantém um ou dois especialistas que acabam fazendo todo o serviço. E estes profissionais acabam por andar entre duas profissões distintas: **Designer de Interação e Interfaces** ou o **Desenvolvedor web**.

Vale lembrar que estas duas profissões tem backgrounds muito diferentes. Enquanto os designers lidam com **abstração**, _devs_ costumam lidar com a**objetividade** do código. Disciplinas que vão de **Teoria de Cores** à **Orientação a objetos** fazem parte do background destes profissionais, porém é com muito trabalho que são desenvolvidos as especialidades, devido a matérias tão antagônicas.

<div id="attachment_4473" style="width: 610px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2011/10/multidisciplinar.png"><img class="size-full wp-image-4473" src="http://tableless.com.br/uploads/2011/10/multidisciplinar.png" alt="" width="600" height="308" srcset="uploads/2011/10/multidisciplinar.png 600w, uploads/2011/10/multidisciplinar-300x154.png 300w" sizes="(max-width: 600px) 100vw, 600px" /></a>
  
  <p class="wp-caption-text">
    Algumas das disciplinas que um profissional de web hoje deve saber para atender demandas de projeto
  </p>
</div>

Essa diferença de backgrounds acaba por oferecer barreiras que fazem com que o desenvolvimento e a integração das disciplinas seja muito difícil. E com isso temos profissionais que desenham interfaces e interações lindas, mas que não podem funcionar sob conceitos de acessibilidade, ou ainda websites perfeitamente acessíves e fluídos, mas que não tem um design tão impactante.

Diante deste cenário tenho trabalhado para desenvolver um conceito que chamo de **[Metawebdesign][2]**. A proposta é justamente encurtar estes espaços, sem incomodar profissões importantíssimas e já consolidadas, mas que por razões diversas em algumas vezes acabam por ser a mesma coisa no organograma de uma empresa.

Meu primeiro e segundo artigos sobre o assunto vão falar sobre **formulários**. Muito já foi falado, e não quero repetir o que já sabemos. Porém é importante mostrar como conceitos de **design da interação**, **arquitetura da informação** e **código** são usados para criar aplicações que oferecem uma experiência inesquecível para o usuário. Estes dois posts iniciais sobre o assunto se transformam em um toolkit muito útil aonde você poderá com a parte 1 e 2 escolher usando conceitos de design os melhores elementos de controle e depois entender como codificá-los de acordo com os padrões do W3C, mantendo usabilidade e acessibilidade.

## <a name="h.ce7pzpue3djo"></a>Aplicando o Metawebdesign a formulários: o design da interface

Cedo ou tarde, a aplicação que você esta criando vai precisar perguntar (ou pedir) ao usuário algum tipo de informação. E sob o ponto de vista do usuário, nesse momento a credibilidade de seu design de interação e código estarão em jogo, pois complexidade e simplicidade aqui separam o céu e o inferno.

Todos sabem como usar alguns <span class="c0">elementos de controle</span> como input texts, checkboxes, radio e dropdowns &#8211; e isso não somos nós desenvolvedores de aplicações web. Isso é consenso, domínio público: um <span class="c11">status quo </span>que todo usuário de computador aprendeu a identificar e saber operar. Mesmo novos usuários entendem estes elementos com uma rapidez impressionante. O problema é como agrupar todos eles em torno de um bem comum &#8211; o bem sucedido submit. Afinal de contas, fazer um formulário é simples, basta colocar um <span class="c11">bando </span>de informações ordenadas de maneira racional, colocá-las na página com alguma ordenação <span class="c8"><a href="http://en.wikipedia.org/wiki/Top%E2%80%93down_and_bottom%E2%80%93up_design">top-bottom</a></span> e é isso, correto?

Para começarmos a conversa, isso é o que os <span class="c0">usuários </span>esperam.

De acordo com o <span class="c8"><a href="http://www.w3.org/TR/html4/interact/forms.html#h-17.1">w3c</a></span>, um formulário HTML (form) é uma seção do documento HTML que pode conter <span class="c0">informação estática</span>, <span class="c0">elementos de controle</span> (os mesmos mecionados acima e alguns outros que vamos falar aqui) e <span class="c0">labels</span> que referenciam estes controles semanticamente. Tudo isso para permitir que o usuário possa responder (ou preencher) uma série de perguntas que a sua aplicação precisa para prosseguir com o fluxo. E o usuário interage com tudo isso <span class="c0">alterando</span> <span class="c0">elementos de controle</span>.

### <a name="h.vz2ra8bmzqo4"></a>Bons e maus exemplos:

Bons exemplos de formulário são fáceis: você mesmo deve conhecer vários; são aqueles que você usa diariamente sem gastar muito tempo ou que não entediam durante seu preenchimento. Maus exemplos são fáceis e estão por todos os cantos da internet, não é difícil encontrar um (na verdade não precisamos nem procurar). Só que não é ético questionar o trabalho de ninguém sem saber as variáveis que levaram aquela implementação. Sendo assim, olha que “bonito” esse <span class="c8"><a href="http://developer.apple.com/internet/webcontent/examples/bad_form.html">formulário que está no site da Apple como exemplo de um mau form</a></span>.

<div id="attachment_4401" style="width: 789px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2011/10/image04.png"><img class="size-full wp-image-4401" src="http://tableless.com.br/uploads/2011/10/image04.png" alt="" width="779" height="266" srcset="uploads/2011/10/image04.png 779w, uploads/2011/10/image04-300x102.png 300w" sizes="(max-width: 779px) 100vw, 779px" /></a>
  
  <p class="wp-caption-text">
    Acredite: foi difícil até colocar tudo isso em um espaço visível. E ainda nao ficou bom.
  </p>
</div>

&nbsp;

Antes de entrarmos de cabeça nos elementos e como formulários devem ser criados, precisamos entender alguns principios básicos de um design de form:

## <a name="h.1a8j29a5szsl"></a>Form Design &#8211; O básico:

<ol start="1">
  <li>
    <strong>Tenha certeza que o usuário entende o que e o porque você está pedindo ou perguntando algo;</strong><br /> Escreva labels com palavras que seus usuários possam entender facilmente independente de serem usuários frequentes ou novos usuários, tenha cuidado com os jargões ou acrônimos utilizados. Se necessário, <span class="c11">desenhe </span>para o usuário.
  </li>
  <ul>
    <li>
      <strong>exemplo 1 : </strong>antes de um grande formulário, tome algum espaço da tela para explicar como ele funciona e o porque você precisa de todas aquelas informações.
    </li>
    <li>
      <strong>exemplo 2: </strong>Se você precisa colocar um controle na tela que não é imediatamente óbvio dentro de um fluxo da tela, use uma tooltip ou outro tipo de ajuda que mostre ao usuário o que ele deve fazer em seguida.
    </li>
  </ul>
  
  <li>
    <strong>Se puder, evite a redundância;<br /> </strong>Antes de colocar os campos em uma tela, analise a informação e o contexto de cada um deles e se possível, agrupe informações para minimizar o numero de campos a serem preenchidos. Mesmo no melhor dos cenários, gastar tempo preenchendo caixas de texto não é algo divertido.
  </li>
  <ul>
    <li>
      <strong>exemplo 1: </strong>se o usuário já preencheu o endereço de entrega no formulário de checkout, você pode reutilizar esta informação para o endereço de cobrança. Basta adicionar um checkbox perguntando se o endereço de entrega e cobrança são os mesmos que em caso de positivo, você já atendeu aos requisitos.
    </li>
    <li>
      <strong>exemplo 2:</strong> Se 80% dos seus usuários estão no Brasil, 15% estão na Argentina e 3% nos Estados Unidos, você pode usar um <select> ao invés de uma <input type=”text”> para atender os requisitos de país. As opções seriam Brasil, Argentina, USA e logo após teríamos lista com a ordenação alfabética.
    </li>
    <li>
      <strong>exemplo 3:</strong> Para endereços no Brasil, no <fieldset> de localização, perguntando apenas o CEP podemos recuperar endereço, bairro, cidade e estado. Com isso faz sentido perguntar primeiramente o CEP, recuperar o valor via webservice e após o sucesso automaticamente preencher estes campos para o usuário.
    </li>
    <li>
      <strong>Existem também exceções:</strong> A <span class="c0">segurança</span> deve ser levada em conta ao ponderar sobre recursos de auto-completion. Não seria ético tampouco legal recuperar os dados do cartão de crédito do usuário para onerá-lo da tarefa de inputar seus dados bancários, uma das partes mais tediosas e passíveis de erro durante a transação de um checkout.
    </li>
    <li>
      <strong><br /> </strong>
    </li>
  </ul>
  
  <li>
    <strong>Informações de conhecimento público normalmente são mais acuradas que informações de conhecimento pessoal;</strong> Quando perguntamos algo ao usuário, temos que ter em mente que eles podem mentir (<span class="c8 c11"><a href="http://www.youtube.com/watch?v=nNOExDrsdbg">everybody lies</a></span>) ou mesmo errar. Podemos minimizar isso reduzindo problemas. O sistema de <span class="c11">auto-completion</span> com o CEP mencionado acima é um exemplo claro. Um erro simples de digitação pode causar um problemão na hora da entrega: a rua <span class="c0">Roda dos Ventos</span> pode virar rua <span class="c0">Rosa dos Ventos</span> em um clique. Probabilidade altíssima de problemas futuros que <span class="c0">você </span>pode evitar usando este tipo de abordagem.
  </li>
  <li>
    <strong>Tenha cuidado ao transformar os requisitos de design em forms;</strong><br /> A maioria dos forms é criada para manipular transações feitas com o banco de dados ou alterar objetos de uma tela. Explore as dependências entre os elementos, procure por similaridades que possam ser agrupadas graficamente, como <span class="c0">campos de endereço</span> ou i<span class="c0">nformações pessoais</span>. O exemplo do endereço de entrega versus o endereço de cobrança mencionado na regra #2 pode ser repetido aqui. Porque não habilitar em um form de inserir produto um drag-n-drop para definir a ordenação das imagens de descrição deste produto ao invés de subir as imagens em uma ordem pré definida ou ainda primeiro subir as imagens para só depois ordenar?<br /> <strong><br /> </strong>
  </li>
  <li>
    <strong>Teste, teste novamente e quando achar que está tudo ok, teste de novo;</strong> Por alguma razão que nunca vamos descobrir, é incrivelmente fácil desenvolvedores e usuários terem idéias completamente diferentes quando o assunto é preencher um formulário. O <span class="c0">mesmo</span> form! Isso pode acontecer pelos mais variados modos:
  </li>
  <ul>
    <li>
      conhecimento prévio com interações passadas,
    </li>
    <li>
      respostas possíveis,
    </li>
    <li>
      fluxo de página que depende de um contexto que o usuário pode entender de maneira diferente dependo de variáveis externas.
    </li>
  </ul>
</ol>

Por isso é importante montar o formulário e se certificar que <span class="c0">todas </span>as possibilidades de interação do usuário com os elementos da tela estão garantidas:

  * preenchimento de campos;
  * clique/toque em botões e objetos de tela;
  * entrada de dados validados para atender requisitos de design da aplicação;
  * condições especiais de uso e interação do form.

Isso nos dá **evidência empírica** do que funciona e o que nao funciona em sua aplicação, além de claramente indicar o caminho a seguir no caso de identificar um problema.

<ol class="c12" start="1">
  <li>
    <strong>Escolha sabiamente os elementos de controle:</strong> eles impactam a expectativa do usuário sobre o que ele está sendo perguntado e como deve responder a isso:
  </li>
</ol>

  * Os usuários tendem a associar o tamanho e forma física dos campos a o que eles <span class="c0">imaginam </span>que seja o que estamos perguntando. Só depois desta associação é que os usuários lêem o que o label de um campo está pedindo.
  * Uma única radio button vai ser algo <span class="c11">ditatorial</span> pois sugere a existência de pelo menos <span class="c0">duas </span>opções na tela.
  * Após você estar acostumado com o processo de compra de sua loja online e seu formulário, automaticamente você irá suavizar sua atenção por não ser uma tarefa nova e sim uma repetição (e daí entendemos o porque a estrada para para erramos um formulário que preenchemos “todo dia” é tão curta)

### <a name="h.bxu0ugomhbvf"></a>Escolhendo elementos de controle

Quando estamos montando o design do nosso form temos que nos ater a algumas situações que impactam diretamente todo o formulário:

<ol class="c13" start="1">
  <li>
    <strong>Espaço disponível na tela: </strong>não precisamos falar nada sobre isso. Cada pixel conta e sabemos disso muito bem, então escolha sabiamente como usar os elementos para tirar total proveito da sua área de exibição.
  </li>
  <li>
    <strong>Sofisticação no formulário deve respeitar uso geral dos forms: </strong><input type=”text”> é algo que todos os usuários estão familiarizados a usar e vão fazê-lo bem, mas nem todo mundo estará confortável em usar um slider de range, com acionamento duplo.
  </li>
  <li>
    <strong>O form deve respeitar o conhecimento público nos domínios da sua app:</strong> É aceitável você usar um <input type=”text”> para um campo que aceita valores entre 0 e 1000. Mas isso iria requerer uma validação para certificar que numeros maiores ou negativos fossem inputados. Se a maior base dos seus usuários está confortável com esta regra, não existe o motivo de usarmos o mesmo slider de range mencionado acima, por todos os problemas de implementação, tempo, acessibilidade e principalmente, dificuldade de uso.
  </li>
  <li>
    <strong>Elementos externos criam expectativas que podem ser erradas:</strong> Temos o conhecimento que <span class="c0">negrito</span>, <span class="c11">itálico</span><span class="c11 c0"> </span>e <span class="c10">sublinhado</span><span class="c0"> </span>são iconografias que foram criadas para dar um destaque a alguma palavra. Fica fora de contexto utilizarmos estas formas para exibir labels por exemplo.<br /> <a href="http://tableless.com.br/uploads/2011/10/image05.png"><img class="alignnone size-full wp-image-4402" src="http://tableless.com.br/uploads/2011/10/image05.png" alt="" width="196" height="28" /></a><br /> <span class="c6 c0">Olha o fast-food “encostando uma arma na sua cabeça” ao perguntar o que é mais saudável.</span>
  </li>
  <li>
    <span class="c0">Tecnologia disponível: </span>o HTML e suas APIs oferecem suporte a muitos elementos de controle, e para os que não são suportados nativamente, existe uma grande gama de toolkits e frameworks que vai te ajudar a implementar aparência e controle em situações específicas.
  </li>
</ol>

### <a name="h.2g3v8mmslxxw"></a>Elementos de controle de Formulários

Para fazer o design de uma tela de formulário, precisamos de elementos de controle. No jargão do HTML, seriam elementos HTML, que nada mais é que o conteúdo que está dentro de uma tag, podendo inclusive ter outros elementos filho caso seja do interesse. Dito isso, fica muito mais fácil entender como o design trabalha com elementos de controle. Após escolher seus elementos na tabela abaixo, tudo que você precisa é codificá-los seguindo os padrões que já conhecemos.

Montar uma tela de formulário não é complicado. Estamos acostumados a fazer isso todos os dias. Porém existem mais coisas entre o céu e a terra do que pode imaginar a nossa vã filosofia. O tópico acima mostra algumas variáveis que as vezes podem passar desapercebido e podem ajudar &#8211; e muito na hora de montar o design da sua tela. Você consegue se imaginar trabalhando orientado ao <span class="c8"><a href="http://tableless.com.br/introducao-ao-responsive-web-design/">Responsive Webdesign</a></span> sem utilizar os conceitos básicos mostrados acima? Pode parecer óbvio, mas é importante manter isso em mente ao utilizar a tabela abaixo:

Elementos de controle em um formulário são divididos em:

<table id="tblMain" class="tblGenFixed" style="font-size: 10px !important;font-family: verdana !important" border="0" cellspacing="2" cellpadding="2">
  <tr>
    <td class="s0">
      <h3>
        Causa
      </h3>
    </td>
    
    <td class="s1">
      <h3>
        Tipo de interação
      </h3>
    </td>
    
    <td class="s2">
      <h3>
        Elementos aceitáveis
      </h3>
    </td>
    
    <td class="s1">
      <h3>
        Prós
      </h3>
    </td>
    
    <td class="s1">
      <h3>
        Contras
      </h3>
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolhas binárias
    </td>
    
    <td class="s5">
      Checkbox
    </td>
    
    <td class="s6">
      Simples e pouco espaço utilizado na tela
    </td>
    
    <td class="s6">
      Checkbox podem ser usadas para múltiplas escolhas, coisa que usuários já estão acostumados ao visualizá-las. Isso pode levar ao erro, uma vez que é necessário entender que este checkbox único compreende uma escolha sim/não
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolhas binárias
    </td>
    
    <td class="s5">
      Radio button
    </td>
    
    <td class="s6">
      Duas opções visíveis. Fácil entendimento do usuário
    </td>
    
    <td class="s6">
      Espaço de tela usado maior que checkboxes únicas
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolhas binárias
    </td>
    
    <td class="s5">
      Dropdown
    </td>
    
    <td class="s6">
      Duas opções visíveis. Pouco espaço utilizado na tela. Permite expansão para múltiplas opções facilmente utilizando pouco espaço da tela
    </td>
    
    <td class="s6">
      Apenas uma opção é visualizada por vez. Requer alguma destreza no uso de formulários. Pode oferecer desafios de acessibilidade a pessoas com deficiência ou que preferem navegação pelo teclado.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolhas binárias
    </td>
    
    <td class="s5">
      Toggle Buttons Iconográficos
    </td>
    
    <td class="s6">
      Mesmos prós do checkbox, desde que a opção seja mostrada como ícone visual
    </td>
    
    <td class="s6">
      Mesmos contras o checkbox, além do fato que não é uma opção padrão para seleção de texto como checkboxes.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolhas binárias
    </td>
    
    <td class="s5">
      Menu com Radio button
    </td>
    
    <td class="s6">
      Espaço mínimo utilizado na tela uma vez que o menu é encontrado em barras ocultas de menu ou lightboxes.
    </td>
    
    <td class="s6">
      Requer muita destreza para encontrá-los e utilizá-los. Necessitam de indicações para que sejam fáceis de ser encontrados em uma tela.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Escolha 1 de N para poucas opções
    </td>
    
    <td class="s5">
      Radio button
    </td>
    
    <td class="s6">
      Todas as opções estão sempre disponíveis na tela.
    </td>
    
    <td class="s6">
      Utiliza um espaço considerável na tela.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Escolha 1 de N para poucas opções
    </td>
    
    <td class="s5">
      Dropdown
    </td>
    
    <td class="s6">
      Pouco espaço utilizado na tela.
    </td>
    
    <td class="s6">
      Enquanto o menu nao está expandido, mostra apenas uma das opções. Novamente requer alguma destreza para operá-lo e pode tambem oferecer desafios de acessibilidade.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Escolha 1 de N para poucas opções
    </td>
    
    <td class="s5">
      Toggle Buttons Iconográficos
    </td>
    
    <td class="s6">
      Pouco espaço utilizado na tela. Todas as opções estão visíveis na tela.
    </td>
    
    <td class="s6">
      Os ícones podem precisar de tooltips para descrição, uma vez que a imagem pode não ser de fácil entendimento para todos os usuários.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Escolha 1 de N para poucas opções
    </td>
    
    <td class="s5">
      Menu com Radio button
    </td>
    
    <td class="s6">
      Espaço mínimo utilizado na tela uma vez que o menu é encontrado em barras ocultas de menu ou lightboxes.
    </td>
    
    <td class="s6">
      Requer muita destreza para encontrá-los e utilizá-los. Necessitam de indicações para que sejam fáceis de ser encontrados em uma tela.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Escolha 1 de N para poucas opções
    </td>
    
    <td class="s5">
      Listbox
    </td>
    
    <td class="s6">
      Muitas opções podem ser visíveis. O frame de seleção pode ser reduzido para até 3 items, permitindo scroll
    </td>
    
    <td class="s6">
      Espaço de tela usado maior que dropdowns ou spinners. Necessita aplicação de padrões de seleção, permitindo seleção única apenas.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Escolha 1 de N para poucas opções
    </td>
    
    <td class="s5">
      Spinner
    </td>
    
    <td class="s6">
      Pouco espaço utilizado na tela.
    </td>
    
    <td class="s6">
      Apenas uma opção é visualizada por vez. Requer muita destreza no uso de formulários e conhecimento deste elemento, pouco utilizado até o lançamento dos novos input types no HTML5. Pode oferecer desafios de acessibilidade a pessoas com deficiência, que preferem navegação pelo teclado ou ainda usuários com ponteiros (mouse) já que a área de clique é mínima.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha 1 de N para muitas opções
    </td>
    
    <td class="s5">
      Dropdown
    </td>
    
    <td class="s6">
      Pouco espaço utilizado na tela.
    </td>
    
    <td class="s6">
      Apenas uma opção é visualizada por vez. Requer muita destreza no uso de formulários. Pode oferecer desafios de acessibilidade a pessoas com deficiência, que preferem navegação pelo teclado ou ainda usuários com ponteiros (mouse) já que a área de scroll é mínima.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha 1 de N para muitas opções
    </td>
    
    <td class="s5">
      Listbox
    </td>
    
    <td class="s6">
      Muitas opções podem ser visíveis. O frame de seleção pode ser reduzido para alguns items de modo a ganhar espaço (permitindo scroll)
    </td>
    
    <td class="s6">
      Espaço de tela usado maior que dropdowns. Necessita aplicação de padrões de seleção, permitindo seleção única apenas.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha 1 de N para muitas opções
    </td>
    
    <td class="s5">
      Treeview
    </td>
    
    <td class="s6">
      Muitas opções visíveis inicialmente, pode oferecer facilidades na cognição já que seus items estarão categorizados por níveis ou tipos (pastas)
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela. Requer muita destreza no uso de formulários.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha N de N para muitas opções
    </td>
    
    <td class="s5">
      Array de checkboxes
    </td>
    
    <td class="s6">
      Todas as opções estão sempre disponíveis na tela.
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha N de N para muitas opções
    </td>
    
    <td class="s5">
      Array de Toggle Buttons Iconográficos
    </td>
    
    <td class="s6">
      Pouco espaço utilizado na tela. Todas as opções estão visíveis na tela.
    </td>
    
    <td class="s6">
      Os ícones podem precisar de tooltips para descrição, uma vez que a imagem pode não ser de fácil entendimento para todos os usuários.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha N de N para muitas opções
    </td>
    
    <td class="s5">
      Menus com Checkboxes
    </td>
    
    <td class="s6">
      Espaço mínimo utilizado na tela uma vez que o menu é encontrado em barras ocultas de menu ou lightboxes.
    </td>
    
    <td class="s6">
      Requer muita destreza para encontrá-los e utilizá-los. Necessitam de indicações para que sejam fáceis de ser encontrados em uma tela.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha N de N para muitas opções
    </td>
    
    <td class="s5">
      Listbox
    </td>
    
    <td class="s6">
      Muitas opções podem ser visíveis. O frame de seleção pode ser reduzido para alguns items de modo a ganhar espaço (permitindo scroll)
    </td>
    
    <td class="s6">
      Todas as opções não estão disponíveis na tela, requerendo scroll. Usuário precisa de indicações de que a caixa permite múltiplas seleções. Requer muita destreza no uso de formulários. Pode oferecer desafios de acessibilidade.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha N de N para muitas opções
    </td>
    
    <td class="s5">
      Treeview
    </td>
    
    <td class="s6">
      Muitas opções visíveis inicialmente, pode oferecer facilidades na cognição já que seus items estarão categorizados por níveis ou tipos (pastas)
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela. Requer muita destreza no uso de formulários.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Escolha N de N para muitas opções
    </td>
    
    <td class="s5">
      Listbuilder
    </td>
    
    <td class="s6">
      Items selecionados são de fácil visualização. Pode permitir fácil expansão para escolha e ordenação de items. Lida facilmente com grandes listas.
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela. Funciona bem para grandes listas com poucas seleções. Muitas seleções oferecem dificuldades na visualização.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Criando listas não ordenadas
    </td>
    
    <td class="s5">
      Caixa com botão de adição/novo
    </td>
    
    <td class="s6">
      Ação de adicionar registro é visível e óbvia para o usuário
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela. Visualmente bagunçado quando usuário insere muitos items.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Criando listas não ordenadas
    </td>
    
    <td class="s5">
      Caixa com edição in-place
    </td>
    
    <td class="s6">
      Menor uso de tela. A adição é feita in-place, dentro da caixa
    </td>
    
    <td class="s6">
      Ação de adição não é tão óbvia quanto a caixa com botão de adição
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s7" bgcolor="#fef2f3">
      Criando listas não ordenadas
    </td>
    
    <td class="s5">
      Caixa com edição drag-n-drop
    </td>
    
    <td class="s6">
      Visualmente elegante e de fácil entendimento, uma vez que arrastar é uma ação intuitiva
    </td>
    
    <td class="s6">
      Necessita de indicações que mostram que na caixa existe uma área de arrastar.
    </td>
  </tr>
  
  <tr>
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Criando listas ordenadas
    </td>
    
    <td class="s5">
      Caixa com botões acima/abaixo para ordenação
    </td>
    
    <td class="s6">
      Ações de rearranjo sempre visíveis na página.
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s3" bgcolor="#ff0000">
      Seleções e listas
    </td>
    
    <td class="s4" bgcolor="#facacb">
      Criando listas ordenadas
    </td>
    
    <td class="s5">
      Caixa com drag-n-drop de items
    </td>
    
    <td class="s6">
      Visualmente elegante e de fácil entendimento, uma vez que arrastar é uma ação intuitiva
    </td>
    
    <td class="s6">
      Necessita de indicações que mostram que na caixa existe uma área de arrastar.
    </td>
  </tr>
  
  <tr>
    <td class="s8" bgcolor="#3c78d8">
      Texto
    </td>
    
    <td class="s9" bgcolor="#a4c2f4">
      Inputs para uma linha de texto
    </td>
    
    <td class="s6">
      Textbox
    </td>
    
    <td class="s6">
      &#8212;
    </td>
    
    <td class="s6">
      &#8212;
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s8" bgcolor="#3c78d8">
      Texto
    </td>
    
    <td class="s10" bgcolor="#dfecf8">
      Múltiplas linhas de texto não formatado
    </td>
    
    <td class="s6">
      Textarea
    </td>
    
    <td class="s6">
      &#8212;
    </td>
    
    <td class="s6">
      &#8212;
    </td>
  </tr>
  
  <tr>
    <td class="s8" bgcolor="#3c78d8">
      Texto
    </td>
    
    <td class="s9" bgcolor="#a4c2f4">
      Múltiplas linhas de texto formatado
    </td>
    
    <td class="s6">
      Textarea que permite tags inline
    </td>
    
    <td class="s6">
      Usuários avançados podem evitar o uso da toolbar inputando as tags diretamente
    </td>
    
    <td class="s6">
      Não é realmente um editor WYSIWYG
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s8" bgcolor="#3c78d8">
      Texto
    </td>
    
    <td class="s9" bgcolor="#a4c2f4">
      Múltiplas linhas de texto formatado
    </td>
    
    <td class="s6">
      Editor Rich text
    </td>
    
    <td class="s6">
      Texto inputado já serve de preview.
    </td>
    
    <td class="s6">
      Nao permite edição apenas pelo teclado. É necessário o uso da toolbar para adicionar as tags necessárias.
    </td>
  </tr>
  
  <tr>
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s12" bgcolor="#fff2cc">
      Números com qualquer tipo de formato
    </td>
    
    <td class="s6">
      Textbox com máscaras
    </td>
    
    <td class="s6">
      Visualmente elegante e permite qualquer tipo/formato de tipos de dado
    </td>
    
    <td class="s6">
      Requer validação no back-end.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s12" bgcolor="#fff2cc">
      Números com qualquer tipo de formato
    </td>
    
    <td class="s6">
      Textbox estruturado e com máscaras
    </td>
    
    <td class="s6">
      Formato dos dados é explícito, facilitando preenchimento e entendimento do usuário
    </td>
    
    <td class="s6">
      Pode requerer grande espaço na tela. Também não permite inputs diferentes dos previstos, mesmo que o usuário deseje isso.
    </td>
  </tr>
  
  <tr>
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s12" bgcolor="#fff2cc">
      Números com qualquer tipo de formato
    </td>
    
    <td class="s6">
      Spinner
    </td>
    
    <td class="s6">
      Permite input sem o uso de teclado caso deseje o usuário
    </td>
    
    <td class="s6">
      Apenas uma opção é visualizada por vez. Requer muita destreza no uso de formulários e conhecimento deste elemento, pouco utilizado até o lançamento dos novos input types no HTML5. Pode oferecer desafios de acessibilidade a pessoas com deficiência, que preferem navegação pelo teclado ou ainda usuários com ponteiros (mouse) já que a área de clique é mínima.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s13" bgcolor="#ffd966">
      Números dentro de um limite pre-definido
    </td>
    
    <td class="s6">
      Slider
    </td>
    
    <td class="s6">
      Metáfora óbvia, valor é mostrado de acordo com a posição do marcador. Usuário não pode inputar números fora deste range
    </td>
    
    <td class="s6">
      Pode requerer grande espaço na tela. Labels muito grandes podem se transformar em um problema também
    </td>
  </tr>
  
  <tr>
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s13" bgcolor="#ffd966">
      Números dentro de um limite pre-definido
    </td>
    
    <td class="s6">
      Spinner
    </td>
    
    <td class="s6">
      Pouco espaço utilizado na tela, permite inputs direto pelo teclado e tambem via clique
    </td>
    
    <td class="s6">
      Não é familiar para todos os usuários. Pode oferecer desafios de acessibilidade a pessoas com deficiência, que preferem navegação pelo teclado ou ainda usuários com ponteiros (mouse) já que a área de clique é mínima. Requer validação no back-end.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s13" bgcolor="#ffd966">
      Números dentro de um limite pre-definido
    </td>
    
    <td class="s6">
      Textbox com validação pós-input
    </td>
    
    <td class="s6">
      Familiar ao usuário, pouco espaço utilizado na tela, acesso via teclado.
    </td>
    
    <td class="s6">
      Requer validação no back-end. Range não é visível para o usuário, requer indicações dos limites para input.
    </td>
  </tr>
  
  <tr>
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s13" bgcolor="#ffd966">
      Números dentro de um limite pre-definido
    </td>
    
    <td class="s6">
      Slider com textbox
    </td>
    
    <td class="s6">
      Permite inputs visuais(slide) e numéricos(input manual)
    </td>
    
    <td class="s6">
      Complexo, requer validação dos inputs no textbox.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s12" bgcolor="#fff2cc">
      Criando um subrange dentro de um range maior
    </td>
    
    <td class="s6">
      Slider duplo
    </td>
    
    <td class="s6">
      Menor uso de tela quando comparado com 2 sliders.
    </td>
    
    <td class="s6">
      Não é familiar para a maioria dos usuários. Problemas graves de acessibilidade porque não permite inputs via teclado.
    </td>
  </tr>
  
  <tr>
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s12" bgcolor="#fff2cc">
      Criando um subrange dentro de um range maior
    </td>
    
    <td class="s6">
      2 Sliders
    </td>
    
    <td class="s6">
      Utilização mais fácil que um slider duplo.
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela. Problemas graves de acessibilidade porque não permite acesso via teclado.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s12" bgcolor="#fff2cc">
      Criando um subrange dentro de um range maior
    </td>
    
    <td class="s6">
      2 Spinners
    </td>
    
    <td class="s6">
      Pouco espaço utilizado na tela, permite inputs direto pelo teclado e tambem via clique
    </td>
    
    <td class="s6">
      Não é familiar para todos os usuários. Requer validação no back-end. Não permite visualização do range maior.
    </td>
  </tr>
  
  <tr>
    <td class="s11" bgcolor="#ff9900">
      Números
    </td>
    
    <td class="s12" bgcolor="#fff2cc">
      Criando um subrange dentro de um range maior
    </td>
    
    <td class="s6">
      Textbox com validação pós-input
    </td>
    
    <td class="s6">
      Familiar para o usuário, ocupa menos espaço que sliders
    </td>
    
    <td class="s6">
      Requer validação e é necessário informar o range de alguma maneira para o usuário.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s14" bgcolor="#6aa84f">
      Data / Horário
    </td>
    
    <td class="s6">
      &#8212;
    </td>
    
    <td class="s6">
      Textbox com máscaras
    </td>
    
    <td class="s6">
      Visualmente simples, permite amplo range de formatos. Permite acesso via teclado
    </td>
    
    <td class="s6">
      Requer validação back-end. Pode causar confusão no formato data/hora por não haver indicações explicitas.
    </td>
  </tr>
  
  <tr>
    <td class="s14" bgcolor="#6aa84f">
      Data / Horário
    </td>
    
    <td class="s6">
      &#8212;
    </td>
    
    <td class="s6">
      Textbox estruturado e com máscaras
    </td>
    
    <td class="s6">
      Formato dos dados é explícito, facilitando preenchimento e entendimento do usuário
    </td>
    
    <td class="s6">
      Pode requerer grande espaço na tela. Também não permite inputs diferentes dos previstos, mesmo que o usuário deseje isso.
    </td>
  </tr>
  
  <tr bgcolor="#eee">
    <td class="s14" bgcolor="#6aa84f">
      Data / Horário
    </td>
    
    <td class="s6">
      &#8212;
    </td>
    
    <td class="s6">
      Datepicker
    </td>
    
    <td class="s6">
      Metáfora óbvia, calendário é exibido e a seleção do valor faz o input
    </td>
    
    <td class="s6">
      Grande espaço utilizado na tela. Pode oferecer problemas de acessibilidade caso não se permita acesso via teclado.
    </td>
  </tr>
</table>

<ol start="1">
  <li>
    Seleções e listas:
  </li>
</ol>

  * Seleções binárias: sim/não, ativo/inativo, etc;
  * Escolha de <span class="c0">UM</span> item para <span class="c0">N</span> com poucas e muitas opções;
  * Escolha de <span class="c0">N </span>items para <span class="c0">N </span>com poucas e muitas opções;
  * Listas não-ordenadas;
  * Listas ordenadas.

<ol start="2">
  <li>
    Texto:
  </li>
</ol>

  * uma linha de texto;
  * múltiplas linhas de texto não formatados e formatados

<ol start="3">
  <li>
    Números:
  </li>
</ol>

  * com qualquer formato;
  * dentro de um range (limite);
  * subrange (sublimite);

<ol start="4">
  <li>
    Data e hora.
  </li>
</ol>

Use a tabela acima para escolher os melhores elementos de tela de acordo com sua necessidade. Você perceberá que as opções cobrem todas as necessidades atuais, alinhadas ao HTML5.

### <a name="h.n0zdn6aco879"></a>Padrões para Elementos de Controle

Os elementos de controle acima necessitam de padrões de funcionamento. Estes padrões mostram:

<ol class="c13" start="1">
  <li>
    Como combinar elementos;
  </li>
  <li>
    definir relações estruturais entre elementos;
  </li>
  <li>
    controlar mudanças de valores e como estes valores são alterados
  </li>
</ol>

Alguns elementos de controle possuem requisitos de funcionamento que já estão aplicados ao elemento em si (spinners ou datepickers já possuem seu comportamento nativo no elemento graças ao HTML5). Outros necessitam de programação no back-end, seja para validação, seja para a criação de ranges, seja para outras necessidades específicas. Quanto mais versátil o elemento, maior a possibilidade de usá-los. Um bom exemplo seriam input type=”text” que com frequência possuem funcionalidades específicas, alem de aceitar <span class="c11">qualquer coisa textual.</span>

  * **Máscaras:**

Máscaras permitem texto em qualquer formato ou sintaxe, fazendo com que o input do usuário seja interpretado de maneira inteligente, a medida que é digitado no campo.

Máscaras são usadas quando sua interface necessita de dados que usuários podem inputar usando qualquer tipo específico de conteúdo, porém não possuem a obrigação de conhecer estes formatos automaticamente:

<ol class="c9" start="1">
  <li>
    remover espaços,
  </li>
  <li>
    inserir apenas números (ou texto),
  </li>
  <li>
    texto sempre em caixa alta (ou caixa baixa),
  </li>
  <li>
    abreviações, etc.
  </li>
</ol>

<p class="c4 c5">
  Usuários querem que a ação (submeter o formulário) aconteça, não querem (nem devem) se preocupar com formatos corretos e interfaces complexas. Jacob Nielsen já dizia que “Usabilidade na web passa pelo fato de que como desenvolvedores de interface, não podemos deixar o usuário pensar demais para fazer uma ação. Ele simplesmente tem que fazê-la de maneira cognitiva”. Máscaras podem inclusive remover a necessidade de <span class="c0">dicas no input</span> ou <span class="c0">dicas no prompt</span>.
</p>

  * **Formato estruturado:**

Estruturar um campo de input significa quebrar um campo em vários outros, de modo a facilitar o entendimento do que é esperado que o usuário faça. Um bom exemplo seria quebrar um campo <span class="c0">único</span> de CEP por exemplo em dois campos, um para os primeiros 5 números, e outro campo para os 3 restantes. Outros exemplos podem ser mencionados: <span class="c0">números de telefone</span>, <span class="c0">numeros de cartão de crédito</span> (cartões AMEX tem um numero de caracteres diferente de cartões VISA por exemplo).

[<img class="alignnone size-full wp-image-4407" src="http://tableless.com.br/uploads/2011/10/image10.png" alt="" width="180" height="42" />][3]

  * **Fill-in-the-blanks:** Combine um ou mais campos de modo a permitir que o usuário possa categorizar o que está inputando, facilitando a ação do usuário. Um bom exemplo seria um formulário de pesquisa em uma loja virtual:

[<img class="alignnone size-full wp-image-4404" src="http://tableless.com.br/uploads/2011/10/image07.png" alt="" width="534" height="169" srcset="uploads/2011/10/image07.png 534w, uploads/2011/10/image07-300x94.png 300w" sizes="(max-width: 534px) 100vw, 534px" />][4]

Usar esta abordagem faz com que a interface seja auto-explicável. Ajuda ao usuário entender o que está acontecendo e o que foi pedido para ele.

  * **Dicas no input:** As dicas no input são importantes para fornecer um guideline ao usuário de como ele deve inputar valores dentro de um campo. O exemplo abaixo, retirado de um form do site dos correios para rastreamento de objetos ilustra bem isso.<span class="c0"><a href="http://tableless.com.br/uploads/2011/10/image08.png"><img class="alignnone size-full wp-image-4405" src="http://tableless.com.br/uploads/2011/10/image08.png" alt="" width="315" height="98" srcset="uploads/2011/10/image08.png 315w, uploads/2011/10/image08-300x93.png 300w" sizes="(max-width: 315px) 100vw, 315px" /></a><br /> </span>
  * **Placeholder no input:** O placeholder é um texto adicionado <span class="c0">dentro</span> do input e que automaticamente desaparece quando o usuário posiciona o cursor da tela dentro do campo. Um bom exemplo pode ser visto no form de busca das páginas do portal globo.com.<span class="c0"><a href="http://tableless.com.br/uploads/2011/10/image01.png"><img class="alignnone size-full wp-image-4398" src="http://tableless.com.br/uploads/2011/10/image01.png" alt="" width="464" height="93" srcset="uploads/2011/10/image01.png 464w, uploads/2011/10/image01-300x60.png 300w" sizes="(max-width: 464px) 100vw, 464px" /></a><br /> </span>
  * **Auto complete:** O nome é auto-explicativo. A medida que o usuário vai digitando caracteres, os termos são auto-completados, fazendo com que o input seja mais rápido caso o resultado esteja disponível no índice usado. Veja o form de search no site do google.com.br<span class="c0"><a href="http://tableless.com.br/uploads/2011/10/image01.png"><img class="alignnone size-full wp-image-4398" src="http://tableless.com.br/uploads/2011/10/image01.png" alt="" width="464" height="93" srcset="uploads/2011/10/image01.png 464w, uploads/2011/10/image01-300x60.png 300w" sizes="(max-width: 464px) 100vw, 464px" /></a><br /> </span>
  * **Dropdown chooser:** Dropdowns podem ser usadas para acomodar seleções que podem utilizar um grande espaço na tela quando expandidas, porém não tem a necessidade direta de deixar todas as opções disponíveis (que usualmente são muitas). Um bom exemplo é a dropdown de seleção de cores no Google Docs.<span class="c0"><a href="http://tableless.com.br/uploads/2011/10/image09.png"><img class="alignnone size-full wp-image-4406" src="http://tableless.com.br/uploads/2011/10/image09.png" alt="" width="214" height="291" /></a><br /> </span>
  * **Seleção ilustrada:** Em alguns casos descrever a opção não é suficiente. É necessário ilustrá-la com uma imagem para facilitar a seleção do usuário. Um bom exemplo é esta dropdown de seleção de papel de parede disponível no site do livro Designing with Progressive Enhancement.<span class="c0"><a href="http://tableless.com.br/uploads/2011/10/image03.png"><img class="alignnone size-full wp-image-4400" src="http://tableless.com.br/uploads/2011/10/image03.png" alt="" width="199" height="210" /></a><br /> </span>
  * **List Builder:** Quando você precisa criar uma lista de items oriundos de uma outra lista, o listbuilder é o padrão ideal a ser usado. Duas textareas e programação fazem com que valores possam ser adicionados ou removidos, além de também poderem ser ordenados facilmente. Veja este exemplo de listbuilder para a configuração de uma toolbar:

[<img class="alignnone size-full wp-image-4399" src="http://tableless.com.br/uploads/2011/10/image02.png" alt="" width="541" height="209" srcset="uploads/2011/10/image02.png 541w, uploads/2011/10/image02-300x115.png 300w" sizes="(max-width: 541px) 100vw, 541px" />][5]

  * **Mensagens de erro:**
  
    Quando o usuário faz algo correto ele recebe um feedback de sucesso, informando que o formulario foi submetido sem problemas. Mas também é necessário informar de maneira clara quando algo dá errado. Mensagens de erro podem ser customizadas de modo a evitar deixar o usuário “no escuro” quando algum erro acontece. Campos obrigatórios precisam de validação (agora mais simples com o atributo <span class="c0">required </span>presente no HTML5), mas podem acontecer outros erros que necessitam de feedback claro para indicar quais os próximos passos a seguir.

[<img class="alignnone size-full wp-image-4403" src="http://tableless.com.br/uploads/2011/10/image06.png" alt="" width="262" height="174" />][6]

Você pode usar o poster abaixo como referência para criar suas interfaces. Clique na imagem para vê-la em uma maior resolução.

[<img class="alignnone size-full wp-image-4411" src="http://tableless.com.br/uploads/2011/10/elementos-de-controleSMALL.png" alt="" width="600" height="447" srcset="uploads/2011/10/elementos-de-controleSMALL.png 600w, uploads/2011/10/elementos-de-controleSMALL-300x223.png 300w" sizes="(max-width: 600px) 100vw, 600px" />][7]

**Na próxima semana, com a Parte 2, a abstração dá o lugar ao código para saber como montar os items que você selecionou para montar seus formulários, transformando os dois posts em um toolkit para o dia-a-dia. Namastê!**

### <span class="c0 c17">Referências</span>

<ol class="c13" start="1">
  <li>
    Metawebdesign &#8211; Quando o Front-end se encontra com a experiência do usuário: <a href="http://www.slideshare.net/AlyssonFranklin/metawebdesign-frontend">http://www.slideshare.net/AlyssonFranklin/metawebdesign-frontend</a>
  </li>
  <li>
    O Metawebdesign &#8211; <a href="http://metawebdesign.org">http://metawebdesign.org</a>
  </li>
  <li>
    Designing Interfaces &#8211; Second Edition (Jenifer Tidwell- O&#8217;Reilly books) <a href="http://designinginterfaces.com/">http://designinginterfaces.com/</a>
  </li>
  <li>
    Top-down e bottom-up design:  <span class="c8"><a href="http://en.wikipedia.org/wiki/Top%E2%80%93down_and_bottom%E2%80%93up_design">http://en.wikipedia.org/wiki/Top%E2%80%93down_and_bottom%E2%80%93up_design</a></span>
  </li>
  <li>
    Everybody lies, uma frase do House: <span class="c8"><a href="http://www.youtube.com/watch?v=nNOExDrsdbg">http://www.youtube.com/watch?v=nNOExDrsdbg</a></span>
  </li>
  <li>
    W3C sobre formulários: <span class="c8"><a href="http://www.w3.org/TR/html4/interact/forms.html#h-17.1">http://www.w3.org/TR/html4/interact/forms.html#h-17.1</a></span>
  </li>
  <li>
    <span class="c8"><a href="http://www.mhavila.com.br/topicos/web/controles.html">http://www.mhavila.com.br/topicos/web/controles.html</a></span>
  </li>
  <li>
    Spinner: <span class="c8"><a href="http://www.jgeppert.com/jquery-spinner/">http://www.jgeppert.com/jquery-spinner/</a></span>
  </li>
  <li>
    A Form of madness: <span class="c8"><a href="http://diveintohtml5.org/forms.html">http://diveintohtml5.org/forms.html</a></span>
  </li>
  <li>
    Responsive webdesign: <span class="c8"><a href="http://www.alistapart.com/articles/responsive-web-design/">http://www.alistapart.com/articles/responsive-web-design/</a></span>
  </li>
  <li>
    Composição de um time multidisciplinar de UX &#8211; <a href="http://itweb.com.br/blogs/a-composicao-de-um-time-multidisciplinar-de-ux/">http://itweb.com.br/blogs/a-composicao-de-um-time-multidisciplinar-de-ux/</a>
  </li>
  <li>
    UX Team of One &#8211; <a href="http://www.slideshare.net/ugleah/how-to-be-a-ux-team-of-one">http://www.slideshare.net/ugleah/how-to-be-a-ux-team-of-one</a>
  </li>
</ol>

 [1]: http://frontinbh.com.br/blog/
 [2]: http://metawebdesign.org
 [3]: http://tableless.com.br/uploads/2011/10/image10.png
 [4]: http://tableless.com.br/uploads/2011/10/image07.png
 [5]: http://tableless.com.br/uploads/2011/10/image02.png
 [6]: http://tableless.com.br/uploads/2011/10/image06.png
 [7]: http://tableless.com.br/uploads/2011/10/elementos-de-controleBIG.png