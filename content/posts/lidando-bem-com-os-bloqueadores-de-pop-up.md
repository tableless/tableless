---
title: Lidando bem com os bloqueadores de pop-up
author: Elcio Ferreira
type: post
date: 2007-12-06
url: /lidando-bem-com-os-bloqueadores-de-pop-up/
tweetbackscheck:
  - 1356413389
shorturls:
  - 'a:3:{s:9:"permalink";s:65:"http://tableless.com.br/lidando-bem-com-os-bloqueadores-de-pop-up";s:7:"tinyurl";s:26:"http://tinyurl.com/4xov5kp";s:4:"isgd";s:19:"http://is.gd/IeCJhA";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503021473
categories:
  - Artigos
  - Browsers
  - Técnicas e Práticas
tags:
  - Browsers
  - gmail firefox
  - konqueror
  - opera
  - popup
  - tecnicas

---
Todo mundo que já experimentou ama bloqueadores de pop-ups. Navegando há anos com [Opera][1] e [Konqueror][2] e usando [Firefox][3] para acessar o [Gmail][4], ainda me assusto quando preciso navegar no IE, seja num cybercafé ou na máquina de um amigo. Como é que as pessoas podem conviver com aquilo? Pop-ups são muito chatos, e se você não acha é porque ainda não experimentou viver sem eles tempo o suficiente.

Por outro lado, o advento dos bloqueadores de pop-up trouxe alguns desafios bastante específicos para o desenvolvedor. Por exemplo, o desafio de fazer sites compatíveis com qualquer navegador quando é obrigado a usar ferramentas de terceiros. É o caso, por exemplo, de alguns sistemas de pagamento nacionais, ferramentas essenciais para o desenvolvimento de qualquer e-commerce brasileiro. O fato é que muitos desses sistemas exigem dos seus usuários a exibição de um pop-up, seja em uma tela de pagamento ou, o que é mais comum, no recibo.

Para complicar, esses sistemas geralmente são submetidos a complexos e burocráticos processos de homologação, onde geralmente a pessoa que vai aprovar seu sistema usa Internet Explorer para Windows e não vai estar muito interessado em ouvir seus argumentos a respeito da inacessibilidade dos pop-ups. Vamos então criar uma solução para que o usuário de navegadores sem bloqueador de pop-ups possam ver normalmente seus pop-ups enquanto os que possuem bloqueador sejam servidos com um confortável link para o endereço do pop-up. Além disso, vamos fazer que aqueles que escolheram o gerenciamenteo inteligente de pop-ups possam ver um pop-up ao clicar no link, mantendo o layout do recibo como foi planejado pelo sistema de pagamento, e o que escolheu bloquear todos os pop-ups possa ver o conteúdo na mesma janela.

### Primeiro passo:

Telefonar e escrever para pessoal do sistema de pagamentos, avisando que pop-ups são uma solução ruim. Demonstre sua indignação pelo fato de o sistema deles precisar de uma ferramenta tão estúpida. De quebra, aproveite para perguntar como fazer o site deles, o módulo administrativo, ou o que mais eles tenham feito para que você e seu cliente acessem funcionar em seu navegador. Pergunte porque o manual fala sobre Internet Explorer e Netscape 4, mas não fala do Safari ou do Firefox. Apresente dessa maneira o Opera e o Mozilla. Se muitos de nós fizermos isso, eles vão ter que começar a considerar esses navegadores ao criar seus sistemas.

### Segundo passo:

Entender os fatos básicos. Agora que você já ajudou a tornar a web um lugar melhor, vamos resolver o problema imediato do nosso cliente. Primeiro vamos ver como criar um link de pop-up que seja acessível a quem não quer ou não pode exibir pop-ups. Links para pop-ups geralmente são criados assim:

<pre>&lt;a href="javascript:void(open('http://www.atipico.com.br','nova','width=800,height=600'))"&gt;Atípico&lt;/a&gt;</pre>

O problema é que quem não tem javascript em seu navegador ou bloqueou todos os pop-ups não pode acessar o link. Muita gente por aí tem usado assim:

<pre>&lt;a href="http://www.atipico.com.br" onclick="window.open(this.href,'nova','width=800,height=600');return false;"&gt;Atípico&lt;/a&gt;</pre>

Assim, o link passa a ser um link HTML comum. Para quem tem javascript disponível, o evento onclick vai abrir o popup e o **return false** ao final vai cancelar o click, fazendo com que a página seja aberta apenas no pop-up, e não na janela atual. Apesar da beleza e da simplicidade, este código tem dois problemas. O primeiro é que o Internet Explorer 5.0, em algumas situações, não lida muito bem com comandos separados por ponto-e-vírgula em atributos HTML. O segundo, mais sério, é que navegadores como Konqueror e Firefox não interrompem um script ao bloquear um pop-up. Então, se o Konqueror estiver configurado para bloquear todos os pop-ups, o pop-up não vai aparecer, e o **return false** vai ser executado, fazendo com que o link também não seja carregado na janela atual.

De fato, o código acima era muito usado antes do advento dos bloqueadores de pop-up, para manter o site acessível en navegadores sem javascript. Ele funciona muito bem se não houver javascript disponível, mas falha em alguns navegadores se houver javascript e o bloqueador de pop-ups estiver habilitado.

Para entender mais de perto a problemática vamos verificar como os navegadores se comportam ao bloquear um popup. Para isso vamos usar o seguinte código:

<pre>&lt;script&gt;
    alert("passo 1")
    window.open("http://www.atipico.com.br","nova","width=800,height=600")
    alert("passo 2")
&lt;/script&gt;
&lt;script&gt;
    alert("passo 3")
&lt;/script&gt;</pre>

Fazendo o teste com este script você pode notar como os navegadores se comportam de maneira diferente ao bloquear um pop-up. Testei no Opera 7.52, no Firefox 0.8 e no Konqueror 3.2.2, todos em Linux. O Mozilla e o Konqueror exibem os três alerts. Ou seja, o pop-up é bloqueado mas o script segue sua execução normal. No Opera são exibidos os alerts 1 e 3. O Opera, portanto, interrompe a execução de um script ao bloquear um pop-up, mas executa normalmente outros scripts na mesma página. O Internet Explorer com a [Google Toolbar][5] se comportou de maneira idêntica ao Mozilla e ao Konqueror.

### Terceiro passo:

Vamos manter nosso pop-up automático, e inserir um link para abrir pop-up que poderá ser usado por quem usa bloqueadores (ou mesmo por alguém que tenha fechado o pop-up por engano):

<pre>&lt;script&gt;
    pagina="http://www.atipico.com.br"

    function abrir(){
        newWindow=window.open(pagina,"nova","width=800,height=600")
        if(newWindow)return false
    }

    abrir()
&lt;/script&gt;
&lt;a href='http://www.atipico.com.br' onclick='return abrir()'&gt;Abrir&lt;/a&gt;</pre>

Aqui criamos uma função, abrir, que abre o popup. Em seguida a executamos. Se não houver bloqueadores o pop-up será exibido automaticamente neste passo. Exibimos então um link &#8220;Abrir&#8221; que executa novamente a função quando clicado. Aqui está toda a mágica, o **onclick** do link contém **return abrir()**, ou seja, o evento será tratado de acordo com o retorno da função. O click somente será cancelado se a função retornar false.

Agora note que a função tem duas linhas. Na primeira abrimos a nova janela (pop-up) e armazenamos o resultado na variável **newWindow**. Na segunda linha testamos o valor de newWindow, se existir retornamos false. Assim, acompanhe nosso programa em três situações diferentes: primeiro, se não houver bloqueadores de pop-ups ou se o bloqueador estiver configurado em **smart policy**, ou seja, permitir os pop-ups requisitados por você. Neste caso, a primeira linha da função abre a janela e armazena o objeto na variável newWindow. A segunda linha testa o valor de newWindow, que existe, e retorna false, cancelando o click. Neste caso o usuário verá o pop-up e nada acontece com a janela original, perfeito. O segundo caso é o de bloqueadores de pop-ups que não permitem pop-up algum, mas não interrompem a execução do script. Neste caso, o pop-up não será aberto. Ao chegar à segunda linha da função, new Window é testada, e não existe. A função não retornará valor (na verdade retornará undefined, mas isso é outro assunto). O click não será cancelado e o usuário verá a página solicitada na janela original. A terceira situação é o caso dos bloqueadores de pop-up que interrompem a execução do script. Nestes o script sequer chegará à segunda linha da função, o javascript será interrompido e o evento não será cancelado, uma vez que o script sequer chegou a retornar algum valor. O resultado será idêntico ao segundo caso.

Há ainda uma quarta situação, a dos navegadores que não possuem javascript habilitado. Neste caso o link vai se comportar como um link normal, sem nenhum problema para o usuário (embora eu duvide que alguém sem javascript consiga usar qualquer sistema de pagamento eletrônico disponível no Brasil.)

### Quarto passo:

Pra quê um quarto passo? O código anterior já funciona muito bem, resolvendo nosso problema. Bom talvez você seja curioso o suficiente para querer complicar um pouco as coisas. A questão agora é: como exibir conteúdo de acordo com o status do pop-up. Isto é, por exemplo, se não houver bloqueador de pop-up não exibir o link &#8220;Abrir&#8221;, uma vez que o usuário verá o pop-up automaticamente. Pois bem, vamos lá:

<pre>&lt;script&gt;
    pagina="http://www.atipico.com.br"

    abriu=false

    function abrir(){
        newWindow=window.open(pagina,"nova","width=800,height=600")
        if(newWindow){
            abriu=true
            return false
        }
    }

    abrir()

&lt;/script&gt;
&lt;script&gt;
if(!abriu)document.write("&lt;a href='http://www.atipico.com.br' onclick='return abrir()'&gt;Abrir&lt;/a&gt;")
&lt;/script&gt;</pre>

Agora usamos uma variável, **abriu**, para guardar o status do pop-up. Começamos o script atribuindo false a esta variável. Depois, dentro do if que testa o pop-up, setamos seu valor para true. Se o pop-up for aberto o valor de abriu será true, caso contrário será mantido o false original.

No segundo bloco script testamos o valor de abriu. Se o pop-up não foi aberto, escrevemos no documento o link para abrí-lo. Colocamos esta linha em um segundo bloco script para que seja executada mesmo que o bloqueador interrompa o primeiro script ao cancelar o pop-up.

O script já faz o que propusemos, exibe o link apenas se o pop-up não for aberto automaticamente. Mas agora ele falha em navegadores sem suporte a javascript. Iso é fácil de resolver, basta colocar, depois dos scripts:

<pre>&lt;noscript&gt;
    &lt;a href="http://www.atipico.com.br"&gt;Abrir&lt;/a&gt;
&lt;/noscript&gt;</pre>

### Palavras finais:

Como você viu, lidar com bloqueadores de pop-up é tarefa trivial, e você pode oferecer conteúdo ao seu usuário no formato que ele escolheu ver, pop-ups para quem não se importa com eles, ou mesmo para quem os deseja, e links comuns para quem escolheu não ver pop-ups. Claro, continuamos achando que pop-ups não são uma boa ferramenta, mas como você não pode trabalhar sempre sozinho, isto pode lhe ser útil ao lidar com código de terceiros, como os citados sistemas de e-commerce.

O código nesse artigo foi escrito apenas para estudo. É claro, quando for para valer, você deve escrever código melhor que o meu. Seus links precisam ter um atributo **title** que descreva bem seu destino, e &#8220;Abrir&#8221; não é um bom texto para se colocar em um link. Você sabe também que, neste último exemplo, depois de **if(!abriu)** você pode fazer o que quiser, e também deve saber que não é bom escrever scripts assim, no meio do seu HTML, e que document.write não é uma boa maneira de se exibir conteúdo. Esperamos que estas idéias lhe sejam úteis. Se você desenvolver algo útil com isso [conte pra gente][6].

 [1]: http://www.opera.com/ "A melhor experiência de internet"
 [2]: http://www.konqueror.org/ "Konqueror - Web Browser, File Manager - and more!"
 [3]: http://www.mozilla.org/products/firefox/ "Firefox - The Browser, Reloaded"
 [4]: http://gmail.google.com "Email com gosto de Google"
 [5]: http://toolbar.google.com/ "Google Toolbar"
 [6]: mailto:elciof+artigopopup@gmail.com "Email para o Elcio"