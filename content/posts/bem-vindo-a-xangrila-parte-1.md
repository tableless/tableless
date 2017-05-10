---
title: Bem vindo a Xangri-lá – Parte 1
author: Alysson Franklin
type: post
date: 2010-11-25
excerpt: Progressive Enhancement, Graceful Degradation e um horizonte perdido que precisa ser encontrado no desenvolvimento web
url: /bem-vindo-a-xangrila-parte-1/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356412178
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/bem-vindo-a-xangrila-parte-1";s:7:"tinyurl";s:26:"http://tinyurl.com/3mvucsf";s:4:"isgd";s:19:"http://is.gd/0opGnH";}'
twittercomments:
  - 'a:9:{i:8314105995722752;s:7:"retweet";i:8306460765200384;s:7:"retweet";i:8206322717696001;s:6:"136226";i:7833959371112448;s:7:"retweet";i:7769885962674176;s:7:"retweet";i:19743364815523840;s:6:"136506";i:24662904502489088;s:7:"retweet";i:114520179832131585;s:7:"retweet";i:174582270278111233;s:7:"retweet";}'
tweetcount:
  - 9
dsq_thread_id: 503039773
categories:
  - Acessibilidade
  - Artigos
  - Browsers
  - Código
  - CSS
  - HTML
  - HTML5
  - Mobile
tags:
  - 2010
  - CSS
  - desenvolvimento web
  - Na Prática

---
Um dia desses eu estava no meio de muita gente boa em um treinamento em São Paulo – um dos melhores que já fiz – e no meio de uma discussão sobre abordagens de desenvolvimento de aplicações internet crossbrowser e a maravilha que era o HTML5, o Elcio &#8211; ele mesmo &#8211; da [Visie][1] disse que Progressive Enhancement e [Graceful Degradation][2] eram a _&#8220;mesma coisa&#8221;_. Eu discordava dele porém não continuei o assunto porque essa questão poderia ser abordada de maneira mais abrangente, e porque o momento era de HTML5, não de como temos que escrever código. Deixei em italico a afirmação porque eu tenho certeza do que ele estava querendo dizer. Quando olhamos rapidamente a afirmação ela parece ter um significado, mas analisando mais a fundo, encontramos o Eldorado.

Mas porque trazer essa discussão para o Tableless, de maneira muito mais abrangente? Porque o Elcio já usa PE em seus projetos (conseguir entregar o que a Visie entrega no tempo que entrega só mostra isso). Mas justamente por já desenvolver **pensando** orientado ao Progressive Enhancement, pra ele tanto faz uma abordagem ou uma metodologia pois as paginas dele ja tem um proposito que PE e Graceful Degradation perseguem: a garantia do maior número possivel de usuários tendo o **mesmo** tipo de experiência ou funcionalidade, independente do browser, tamanho de tela, dispositivo ou conexão. O novo site da <a title="Acessar o site da Brastemp" href="http://www.brastemp.com.br/" target="_blank">Brastemp</a>, que os caras da Visie entregaram a poucos dias mostra bem isso. Tente acessar esse website do seu browser preferido. A experiência nao é comprometida em nenhum momento. Agora tente acessar do seu mobile. Agora tente acessar do seu PSP. Agora tente acessar do seu PS3. Voce vai perceber que a experiencia é a mesma.

Sem muita delonga, vou direto as diferenças: **Graceful Degradation** parte da premissa que você vai desenvolver seu site com a melhor tecnologia disponível, plugins e tudo mais. E mesmo que seu cliente possua browsers que não renderizem efeitos/features utilizados, sua navegação vai acontecer “sem problemas”, porque uma vez que a funcionalidade esta OK em um browser, vamos efetuando mudancas no código até garantir que a funcionalidade rode em todos os browsers usados. Partimos da premissa que a experiência que o usuario terá em browsers mais modernos será suavemente degradada para funcionalidades mais simples em browsers mais antigos.

Dito isso, bem vindos ao Eldorado: **Progressive Enhancement** usa tecnologias web em “camadas” que permitem que todos os usuários, independente de browser e velocidade de conexão, tenham acesso as **funcionalidades básicas e conteúdo** de uma página. E quanto mais avançado for o browser do usuário e sua conexão, mais rica será sua experiência. Partindo de um baseline que **garantidamente funcione em todos os browsers**, vamos pouco a pouco adicionando funcionalidades que, após testadas, funcionarão **apenas** em browsers que a suportam.

Em outras palavras, Graceful Degradation parte do difícil, do bleeding edge. Uma vez que seu jQuery maneirão já esta funcionando bonitinho no Chrome, é hora de voce passar o final de semana namorando seu código e sua garrafa de café, para garantir que o bendito plugin também funcione no amado IE6. Progressive Enhancement vai na direção oposta. Partindo do simples, garantimos que uma funcionalidade roda no IE6 para só depois “perfumá-la” para o Chrome.

Um exemplo?

<pre lang="HTML" line="1"><p>
  <a href="window.print()">Imprimir</a>
      
</p>
</pre>

Esse link funciona quando o JavaScript está disponível e habilitado e o browser suporta o comando de impressão. No entanto, se o JavaScript não estiver disponível (por exemplo, em alguns dispositivos móveis), o link não funcionará, criando um problema grande. Você, como o desenvolvedor do site, prometeu a seus visitantes uma funcionalidade que não funciona. Quando clicam no link e ele não funciona eles se sentem confusos, enganados e vão culpá-lo (com razão) por entregar uma experiência ruim ao usuário final.

Para resolver isso os Devs costumam usar Graceful Degradation: dizem ao usuário que o link pode não estar funcionando e qual a razão para isso, e talvez até sugiram uma solução alternativa para conseguir o que o usuário deseja fazer. Um truque comum é usar o elemento noscript.

<pre lang="HTML" line="1"><p>
  <a href="window.print()">Imprimir**</a>
      
</p>
    
      

<p class="scriptwarning">
  Para imprimir vc precisa do javascript habilitado. 
          Por favor, habilite-o em seu browser.
        
</p>
    
</pre>

Com isso explicamos que algo deu errado e como consertar o problema. Porém partimos da premissa que nosso usuário:

  * Sabe o que é javascript;
  * Sabe como habilitar(e desabilitar) javascript;
  * Tem permissões administrativas para mudar essa configuração;
  * Se sente confortável em habilitar o javascript apenas para imprimir um documento;

Ainda usando Graceful degradation, poderíamos ser mais gentis com o usuario:

<pre lang="HTML" line="1"><p>
  <a href="window.print()">Imprimir**</a>
      
</p>
    
      

<p class="scriptwarning">
  Impress&atilde;o do documento: 
          Selecione o bot&atilde;o imprimir/print no seu browser, ou no menu arquivo/file, selecione a op&ccedil;&atilde;o imprimir/print. Voc&ecirc; tamb&eacute;m pode tentar o atalho ctrl+p em seu teclado.
        
</p>
    
</pre>

Isso resolve vários problemas do dev, mas parte da premissa que a funcionalidade de impressao é a **mesma** em todos os browsers. E essa afirmacao não é correta.

Se fossemos fazer a funcionalidade acima usando PE, a primeira coisa seria descobrir como imprimir a página sem usar javascripts. Como sabemos que isso non ecziste, chegamos a primeira conclusão: **um link não é a melhor escolha de elemento HTML a se usar nesse caso**. Mas se mesmo assim você quer usar essa funcionalidade de impressão, você deve usar botões ao invés de scripts. Por definição <a title="Acessar o w3c" href="http://www.w3.org/TR/html401/interact/forms.html" target="_blank">botões existem para suportar scripts</a>.

> “Botões não têm um comportamento padrão. Cada botão pode ter um script client-side associando os atributos do elemento ao evento. Quando ocorre um evento (por exemplo, o usuário pressiona o botão), o script associado é acionado.”
> 
> * * *(w3c, 17.2.1 Control types)</p>

A segunda conclusão é não assumir que o javascript estará habilitado, ou que o browser possa imprimir. Ao invés disso, informamos que o usuário precisa imprimir sua página:

<pre lang="HTML" line="1"><p>
  Obrigado! Por favor imprima essa p&acute;gina para seus registros.
</p>
</pre>

Esse parágrafo com certeza funciona em **qualquer** browser. O resto é fácil.

<pre lang="HTML" line="1">(function(){
      if(document.getElementById){
        var pt = document.getElementById('printthis');
        if(pt && typeof window.print === 'function'){
          var but = document.createElement('input');
          but.setAttribute('type','button');
          but.setAttribute('value','Imprimir');
          but.onclick = function(){
            window.print();
          };
          pt.appendChild(but);
        }
      }
    })();
    
</pre>

Dê uma olhada no script, veja a abordagem usada. Não assumimos nada, tratamos caso a caso cada situação, e oferecemos a **mesma** funcionalidade a todas elas.

  * Colocando toda funcionalidade em uma função e a executando em seguida, não deixamos variáveis soltas na página.
  * Testamos o suporte a DOM e tentamos chegar no elemento que queremos para adicionar o botão a ele.
  * Após testar a existência do elemento, testamos se o browser suporta o objeto window e o método print
  * Se as duas condições passam, criamos um novo botão e aplicamos o window.print() no evento do clique.
  * Adicionamos o botão ao paragrafo.

Como disse lá em cima, isto irá funcionar para todos os usuários, independentemente do ambiente. Não prometemos ao usuário um elemento de interface que não funciona &#8211; em vez disso, apenas mostramos o feature quando ele funciona.

**Em tempo:** Tecnicamente não há nenhuma necessidade de um botao &#8220;imprimir&#8221;, mas para entender, mantive o exemplo simples.

## Navegando nas águas dos browsers

Grande parte dos desenvolvedores mantém em sua máquina de desenvolvimento um IE8, talvez um IETester, Firefox 2, Firefox 3.6 e Firefox 4. Normalmente os contratos rezam sobre esses browsers, e quando isso representa a maior fatia da internet (73% do mercado), faz sentido. **Mas faz sentido apenas até o ponto aonde essa afirmação não atinge consumidores em potencial.** E não podemos desconsiderar o poder de 500 milhões de potenciais compradores. Com os browsers mencionados acima voce garante o _grosso da internet_ e isso aí é o **minimo** que desenvolvedores como nós pode oferecer.

Analizamos os numeros abaixo, a situação fica mais visivel. Em outubro, os numeros* foram:

  1. Firefox: A raposinha tem 44,1% do mercado, ou quase **870 milhões** de browsers instalados
  2. IE: Em franca decadência desde a sangrenta batalha com a Netscape, hoje tem **580 milhões** de browsers instalados &#8211; 29,7%
  3. Chrome: Como tudo do Google, o crescimento espantoso graças a estrategia de marketing que eles usam já garantem quase **380 milhões** de usuarios, com 19,2%
  4. Safari / Opera: Juntos, os dois simpáticos browsers tem quase **120 milhões** de usuários &#8211; 3,9% e 2,2% respectivamente
  5. O resto: temos pouco mais de **17 milhões** de pessoas que navegam com outros browsers, a lista é “infinita”

<p style="font-size: 9px">
  <img alt="391de7d2-f315-11df-b15d-000255111976" src="http://www-958.ibm.com/me/files/thumbnails/391de7d2-f315-11df-b15d-000255111976.png?size=600x494" style="border: 0px solid #6898C8;margin: 0;padding-top: 10px;padding-bottom: 3px" /><br /> Essa comparação gerou uma visualizacao no manyeyes. Você pode vê-la <a title="Acessar o many Eyes para ver a guerra de browsers versao 1" href="http://www-958.ibm.com/software/data/cognos/manyeyes/visualizations/browser-wars-2" target="_blank">aqui</a> e <a title="Acessar o many Eyes para ver a guerra de browsers versao 2" href="http://www-958.ibm.com/software/data/cognos/manyeyes/visualizations/browser-wars-v2" target="_blank">aqui</a>.
</p>

Considerando que estamos cobrindo 73% do mercado, deixamos fora da festa a considerável quantia de mais de **500 milhões de usuários** que fazem uso de outro browser. Voce realmente quer perder ou deixar de lado essa audiência? Você não poderia desenvolver seus websites de uma maneira que uma fatia maior de usuários possa usar sem problemas a sua aplicação? Quer deixar essa equação mais difícil ainda? Estamos falando de números para browsers que hoje estão em sua maioria em **desktops**. O problema deve aumentar expoencialmente a medida que novos dispositivos comecarem a acessar seus websites.

O cenário caminha para o completo caos se pensarmos que nossos clientes normalmente pedem seus websites em um timeframe muito pequeno. Cobrir todas as áreas do desenvolvimento web em um mês normalmente e ainda garantir que a aplicação vai rodar em 5 diferentes browsers (IE6/7/8/9, FFox 2/3.6/4, Safari4, Opera11, Seamonkey, Chrome) é muita tarefa para o exército-de-um-developer-só. E é ai que entra o PE. Usar uma abordagem diferente para trabalhar é a chave do negocio. Chegou um novo projeto?

  1. Separe conteúdo da forma. Isso facilitará o passo 3
  2. Defina um baseline de funcionalidades **básicas** da aplicação. Pesquise na documentação se estas funcionalidades rodam OK no browser **mais antigo** que o seu contrato pede no desenvolvimento. Se não funciona nele, esta não é uma funcionalidade básica. Redefina e pesquise até chegar a um denominador comum. Se o projeto for HTML5, recomendo partir do <a title="Acessar o HTML5 Boilerplate" href="http://html5boilerplate.com" target="_blank">HTML5 Boilerplate</a>
  3. Escreva um HTML **semântico** aonde depois você vai encapsular o conteúdo. Nada de javascripts, nada de CSS. Apenas o HTML nesse momento. Valide o template, veja se tudo esta ok antes do próximo passo.
  4. Aplique o CSS para o HTML desenhado, teste nos browsers que você precisa cobrir no desenvolvimento. Garanta a mesma experiência ao usuário em todos eles.
  5. Aplique o javascript. Faça modificações, teste novamente em todos os browsers. Ao implementar, tenha em mãos uma <a href="http://www.quirksmode.org/dom/events/index.html" target="_blank" title="Acessar o quirksmode.org">lista de objetos e métodos aceitos pelo browser</a>
  6. Seja feliz e tenha certeza que ao entregar o seu produto, seu celular não vai tocar no final de semana porque o plugin de código de barras não funciona no cliente que tenta deseperadamente imprimir um boleto de compra usando IE7.

Isso significa que Graceful Degradation é o fim do mundo, técnica _capenga_ de desenvolvimento quando comparado ao Progressive Enhancement? Não, de maneira alguma. Graceful Degradation também tem seus benefícios &#8211; principalmente em projetos que já estão em produção &#8211; mas se você vai escrever um projeto **do zero**, use Progressive Enhancement. Não complique. Progressive Enhancement é mais sofisticado e mais estável que GD, mas se você não tem uma metodologia de trabalho ja definida, PE pode tomar mais tempo. **Se você ainda não tem uma metodologia de trabalho, desenvolva-a.** Se você vai trabalhar em um projeto que já está rodando, se vai mudar uma funcionalidade que já está no ar, você pode usar Graceful Degradation, atuando como um “patch” para um produto ja existente, uma vez que o tempo de desenvolvimento sera menor que desenhar uma solução do zero usando Progressive Enhancement. É, pensando bem, dá pra usar os dois pra achar o Eldorado, é só ter cuidado ao criar novos sites, e guardar seu canivete-suiço de soluções ninja para fazer tudo funcionar em todos os browsers para os momentos aonde esse skill sera exaustivamente colocado a prova. Mãos a obra!

Uma vez apresentado, é hora de mergulhar fundo no Progressive Enhancement, mas isso é assunto para o próximo post. Um abraço!

<small>*Os percentuais eu retirei do w3schools, os milhoes de um calculo que so foi possivel gracas ao excelente livro Designing with Progressive Enhancement, do pessoal do Filament group, aos numeros do Internet World stats, e algumas xicaras de cafe. Todavia, recomendo fortemente a leitura do livro.</small>

<small>** Bons olhos James! Obrigado pelo toque, o wordpress remove o javascript: da minha chamada automaticamente, deve ter algo a ver com a tag pre. Assim que resolvido, o código estará corrigido.</small>

## Referências:

  * <a href="http://www.w3schools.com/browsers/browsers_stats.asp" target="_blank" title="Acessar o site de referencia">Browser stats</a>
  * <a href="http://en.wikipedia.org/wiki/List_of_web_browsers" target="_blank" title="Acessar o site de referencia">Lista de browsers</a>
  * <a href="http://upload.wikimedia.org/wikipedia/commons/7/74/Timeline_of_web_browsers.svg" target="_blank" title="Acessar o site de referencia">timeline dos browsers</a>
  * <a href="http://upload.wikimedia.org/wikipedia/commons/5/55/Layout_engine_usage_share-2009-01-07.svg" target="_blank" title="Acessar o site de referencia">browser engine share usados</a>
  * <a href="http://filamentgroup.com/" target="_blank" title="Acessar o site de referencia">Filament group</a>
  * <a href="http://filamentgroup.com/lab/announcing_our_book_designing_with_progressive_enhancement/" target="_blank" title="Acessar o site de referencia">Designing with PE</a>
  * <a href="http://www.internetworldstats.com/stats.htm" target="_blank" title="Acessar o site de referencia">Internet World Stats</a>
  * <a href="http://craigmdennis.com/web-design/graceful-degradation-vs-progressive-enhancement/" target="_blank" title="Acessar o site de referencia">Graceful Degradation vs Progressive Enhancement</a>
  * <a href="http://en.wikipedia.org/wiki/Progressive_enhancement" target="_blank" title="Acessar o site de referencia">Progressive Enhancement no Wikipedia</a>
  * <a href="http://www.digital-web.com/articles/fluid_thinking/" target="_blank" title="Acessar o site de referencia">Fluid Thinking</a>
  * <a href="http://dev.opera.com/articles/view/graceful-degradation-progressive-enhance/" target="_blank">Graceful Degradation vs Progressive Enhancement by Opera Curriculum</a>
  * <a href="http://www.w3.org/TR/html401/interact/forms.html#push-button" target="_blank" title="Acessar o site de referencia">Buttons: howto by w3c</a>
  * <a href="http://en.wikipedia.org/wiki/Browser_wars" target="_blank" title="Acessar o site de referencia">A Guerra dos Browsers</a>
  * <a href="http://gs.statcounter.com/" target="_blank" title="Acessar o site de referencia">Statcounter</a>

 [1]: http://visie.com.br/
 [2]: http://tableless.com.br/graceful-degradation-e-tudo-sobre-acessibilidade