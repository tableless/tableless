---
title: As muitas faces do Mobile First
author: Will Sales
type: post
date: 2013-01-25
excerpt: Quando você perde 80% do seu espaço na tela, todo o conteúdo irrelevante ao design de telas grandes não parece mais tão atrativo ou necessário.
url: /as-muitas-faces-do-mobile-first/
dsq_thread_id: 1050076537
categories:
  - Mobile
  - Traduções
tags:
  - desenvolvimento mobile
  - mobile
  - mobile first

---
<img class="alignleft" alt="" src="http://bradfrostweb.com/uploads/2012/03/luke1-650x487.jpg" />

Vemos a frase &#8220;mobile-first&#8221; em todos os lugares. <a href="http://lukew.com/" target="_blank">Luke Wroblewski</a> definitivamente atingiu uma veia quando cunhou este termo há alguns anos, e criou um importante grito de guerra a medida que entramos neste futuro multi-screen.

<a href="http://www.lukew.com/ff/entry.asp?933" target="_blank">A definição mobile-first de Luke</a> consiste em três componentes principais:

1. O crescimento do mobile é, mais do que nunca, uma grande oportunidade de atingir as pessoas;

2. As restrições do meio mobile nos força a focar no que realmente importa;

3. As capacidades do mobile criam oportunidades inovadoras.

Entretanto, às vezes alguns termos evoluem além das suas definições iniciais, tornando-se algo genérico a uma ideia ou noção geral (<a href="http://bradfrostweb.com/blog/mobile/beyond-media-queries-anatomy-of-an-adaptive-web-design/" target="_blank">recentemente falei sobre isso</a>, relacionando ao web design responsivo). Esta generalização certamente aconteceu com o &#8220;mobile first&#8221;, e como resultado vemos o termo ser utilizado de inúmeras maneiras. Aqui estão os vários prismas que tenho me deparado, em decorrência do mobile first.

## CULTURA

A população mobile-first acessa o mundo digital principalmente (ou apenas) através de seus dispositivos mobile. O mobile atinge <a href="http://mobithinking.com/mobile-marketing-tools/latest-mobile-stats/a#subscribers" target="_blank">87% da população mundial</a>, e é mais difusivo que qualquer outro meio de massa.  Na verdade, as pessoas tem acessado celulares mais que qualquer outra coisa. Usuários do mobile-first estão em alta também. <a href="http://www.pewinternet.org/Reports/2012/Cell-Internet-Use-2012/Key-Findings/Overview.aspx" target="_blank">31% dos cidadãos americanos usam dispositivos mobile como sua maneira principal de acessar a web</a>, e este número é muito, muito maior em outras regiões.

O termo &#8220;mobile only&#8221; também está surgindo como algo cultural, e descreve quando o dispositivo mobile é a única janela para o mundo conectado.

<img class="alignleft" alt="" src="http://bradfrostweb.com/uploads/2012/03/babies-with-mobile-650x650.jpg" />

_Uma geração mobile-first_

&#8220;Mobile first&#8221; no sentido cultural também pode ser uma referência, ao fato que, para muitas pessoas – especialmente bebês e crianças pequenas – um dispositivo mobile é por muitas vezes o primeiro dispositivo conectado que ele interage e se familiariza. Esta mentalidade mobile-first molda como eles interagem com o mundo e criam expectativas para tudo a sua volta. Incluindo dispositivos non-touch ou <a href="http://www.youtube.com/watch?v=aXV-yaFmQNk" target="_blank">objetos inanimados</a>, touch-friendly e sempre conectados.  Estas mentes mobile-first são livres dos modelos mentais do passado da computação, e como resultado certamente moldarão o que esperamos mais a frente do nosso &#8220;mundo conectado&#8221;.

## ESTRATÉGIA

Pelo fato de todas as estradas estarem levando ao mobile, muitas empresas estão gritando &#8220;mobile first!!!&#8221; em alto e bom som em suas organizações. O que isto significa? Tipicamente, significa **tornar o mobile uma prioridade em vez de uma reflexão tardia, a fim de capitalizar o crescimento e as capacidades do meio**.

Histórias de mobile-first de sucesso como o Instagram desencadearam muitas startups, produtos e serviços a contribuírem com apps e produtos mobile, em vez de tratarem o mobile apenas como uma melhoria ou aderência. Organizações acreditam que focando no mobile terão uma oportunidade de estarem atualizadas e não ficarem pra trás.

O &#8220;Mobile first&#8221; no sentido estratégico é também usado incorretamente no contexto do <a href="http://bradfrostweb.com/blog/post/native-vs-web-is-total-bullshit/" target="_blank">debate &#8220;nativo vs web&#8221;</a>. Que estratégia digital deveria conduzir uma organização: Um app mobile ou um website? Neste contexto, o &#8220;Mobile first&#8221; é sinônimo de &#8220;Native first&#8221;. Este debate cria uma falsa dicotomia entre duas plataformas diferentes que fazem coisas diferentes, pois ambas são de fato acessadas pelo mobile.

Embora, em última análise, possa fazer sentido desenvolver um app mobile nativo ou criar um produto ou serviço específico ao mobile, um mal-entendido do &#8220;mobile first&#8221; pode levar a uma estratégia míope, o que pode causar às organizações perda do panorama geral e de oportunidades futuras.

## DESIGN

Como Luke habilmente descreve em seu livro <a href="http://www.abookapart.com/products/mobile-first" target="_blank">Mobile First</a>, as restrições aos mobile designers os levam a dar foco no que realmente importa ao produto ou serviço. Quando você perde 80% do seu espaço na tela, todo o conteúdo irrelevante ao design de telas grandes não parece mais tão atrativo ou necessário. O mobile oferece uma grande oportunidade de reavaliar qual conteúdo/funcionalidade é necessário, e nos dá uma oportunidade de arrancar toda a &#8220;sujeira&#8221; existente. Essas restrições também incentivam a facilidade de uso, intuição e velocidade como ingredientes essenciais a uma boa experiência do usuário.

Essa mentalidade na estratégia do design inicial por small screens, envolve dos wireframes ao photoshop e protótipos. Determinar como uma experiência, criada para mobile, pode ser traduzida para telas maiores, pode ser mais lógico do que tentar amontoar um grande e complexo projeto desktop no mobile.

## DESENVOLVIMENTO

O desenvolvimento mobile-first é de grande abrangência, e na web o termo é frequentemente discutido no contexto <a href="http://bradfrostweb.com/blog/web/mobile-first-responsive-web-design/" target="_blank">mobile first no web design responsivo</a>. A ideia básica é que em vez de codificar a experiência inicialmente para telas maiores, e depois incluir o código adicional para ser trabalhado em small screens, faz mais sentido desenvolver primeiro uma leve fundação semântica de código, para só então ir melhorando progressivamente essa experiência.

<img class="alignleft" alt="" src="http://bradfrostweb.com/uploads/2012/03/43-650x487.png" />

### Estrutura

Ter uma <a href="http://www.slideshare.net/stephenhay/structured-content-first" target="_blank">estrutura content-first</a> significa criar uma base central que priorize a clareza, semântica e performance, que será utilizada como base a qual o restante da experiência se espelhará. Em vez de incluir grandes módulos, e ter que escondê-los ou desabilitá-los mais tarde ao desenvolver para small screens, uma base mobile-first tornará possível elementos apropriados para telas maiores posteriormente, enquanto continua a oferecer uma experiência totalmente acessível.

### Estilo

Um estilo mobile-first significa determinar os estilos CSS primeiro, introduzindo estilos específicos para telas maiores somente quando apropriado. Aqui um rápido exemplo de meu <a href="http://www.html5rocks.com/en/mobile/responsivedesign/" target="_blank">tutorial mobile-first no web design responsivo</a>. Primeiro, a abordagem desktop comum que queremos evitar:

    
    /*Large screen styles first - Avoid*/
    .feature {
        width: 50%;
        float: left;
    }
    
    @media screen and (max-width: 40.5em) {
         .feature {
              width: auto;
              float: none;
        }
    }
    
    

Basicamente, o que nós fizemos foi escrever regras específicas ao layout, que seriam desfeitas somente em small screens. Isto adiciona uma complexidade desnecessária, então vamos conseguir esse mesmo resultado do jeito mobile-first:

    
    @media screen and (min-width: 40.5em) {
         .product-img {
              width: 50%;
              float: left;
         }
    }
    
    

Em vez de criar regras para serem substituídas somente em small screens, faz mais sentido inserir regras no layout quando elas se aplicam. Estilos no mobile-first resultam em um código mais fácil de ler e manter.

## E VEM MAIS POR AÍ

A ascensão do mobile já reformulou o mundo, abriu novas dimensões de interação e nos obrigou a repensar como criamos produtos digitais. Isto é incrível, e é só o começo. E do jeito que o &#8216;mobile-first&#8217; cada vez mais permeia os aspectos da cultura e do design, e só uma questão de tempo para tornar-se um modelo padrão.

Obrigado Luke!

—

_Traduzido com autorização de <a href="http://bradfrostweb.com/about/" target="_blank">Brad Frost</a>._

_Artigo original escrito por <a href="http://bradfrostweb.com/about/" target="_blank">Brad Frost</a>._

_Acesse o artigo original em <a href="http://bradfrostweb.com/blog/mobile/the-many-faces-of-mobile-first/" target="_blank">Brad Frost Web</a> – The Many Faces of ‘Mobile First’ – 13 de agosto de 2012._