---
title: Princípios para escrever CSS de forma consistente
author: Zeno Rocha
type: post
date: 2012-02-14
excerpt: Pra você que não aguenta mais ver código bagunçado
url: /principios-para-escrever-css-de-forma-consistente/
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6294";s:7:"tinyurl";s:26:"http://tinyurl.com/bqs46u5";s:4:"isgd";s:19:"http://is.gd/7iSXRH";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 725958034
categories:
  - CSS3

---
Um problema muito comum quando trabalhamos em equipe é a inconsistência no estilo de codificação. Uns preferem colocar as propriedades do CSS em uma única linha, outros não. Uns gostam de colocar espaço depois dos dois-pontos, outros não. No fim, acaba tudo uma zona. São muitos desenvolvedores, escrevendo de formas totalmente distintas, o que prejudica qualquer tipo de manutenção ou evolução do código. 

Por isso, tenho notado um movimento cada vez maior de empresas buscando padronizar seu estilo de código. Google, Github e muitas outras já disponibilizaram publicamente seus guias de estilo:

  * [Google HTML/CSS Style Guide][1]
  * [Github CSS/JS/Ruby Style Guide][2]

Pensando nisso, Nicolas Gallagher ([@necolas][3]), funcionário do Twitter, criador do [Normalize.css][4] e um dos líderes do [HTML5 Boilerplate][5], resolveu criar um guia chamado [Idiomatic CSS &#8211; Princípios para escrever CSS de forma consistente e idiomática][6]. Baseado em um projeto semelhante, porém com foco em JavaScript, o [idiomatic.js][7].

O que eu irei apresentar hoje é uma pequena adaptação da [tradução oficial][8], feita por mim, desse documento vivo e aberto para contribuições através do [Github][9].

O guia a seguir não pretende ser prescritivo e também não busca impor as preferências do autor no código de outras pessoas. Entretanto, estas orientações incentivam fortemente o uso de padrões já existentes, comuns e sensatos.

## 1. Princípios gerais

Todo código em qualquer aplicação deve parecer como se tivesse sido escrito por uma única pessoa, independentemente de quantas pessoas tenham contribuído. Faça cumprir rigorosamente o estilo acordado.

## 2. Espaços em branco

Novamente, apenas um estilo deve existir em todo o projeto. Seja sempre consistente na utilização de espaços em branco. Use espaços em branco para melhorar a legibilidade.

  * _Nunca_ misture espaços e tabs para indentação.
  * Escolha entre indentação suave (espaços) ou tabulação. Atenha-se à sua escolha sem falhar. (Preferência: espaços)
  * Se usar espaços, escolha o número de caracteres usados por nível de indentação. (Preferência: 4 espaços)

Dica: configure seu editor para “mostrar invisíveis”. Isso irá permitir que você elimine espaços em branco da quebra de linha, elimine espaços em branco de linhas vazias sem indentação e evite commits poluídos.

## 3. Comentários

Código bem comentado é extremamente importante. Tire tempo para descrever componentes, como eles funcionam, suas limitações e o modo como são construídos. Não deixe outros no time adivinharem o propósito de códigos incomuns ou não óbvios.

Estilo de comentário deve ser simples e consistente dentro de uma única base de código.

  * Coloque comentários em uma nova linha acima do seu assunto.
  * Evite comentários no fim da linha.
  * Mantenha o comprimento da linha a um máximo sensível, por exemplo, 80 colunas.
  * Faça o uso liberal de comentários para quebrar o código CSS em seções distintas.
  * Use comentários com iniciais maiúsculas e indentação de texto consistente.

Dica: configure seu editor para lhe prover com atalhos a geração do padrão de comentários acordado.

#### Exemplo com CSS:

[cc lang=&#8221;css&#8221;]
  
/* ==========================================================================
  
Bloco de comentário de seção
  
========================================================================== */

/* Bloco de comentário de sub-seção
  
========================================================================== */

/*
  
* Bloco de comentário de grupo
  
* Ideal para explicações em múltiplas linhas e documentação.
  
*/

/\* Comentário básico \*/
  
[/cc]

#### Exemplo com SCSS:

[cc lang=&#8221;css&#8221;]
  
// ==========================================================================
  
// Bloco de comentário de seção
  
// ==========================================================================

// Bloco de comentário de sub-seção
  
// ==========================================================================

//
  
// Bloco de comentário de grupo
  
// Ideal para explicações em múltiplas linhas e documentação.
  
//

// Comentário básico
  
[/cc]

## 4. Formatação

O formato de código escolhido deve garantir que o código seja: fácil de ler; fácil de comentar claramente; minimize a chance de introduzir erros acidentalmente; e resulte em úteis visualizações de diferença.

  1. Um seletor discreto por linha em um conjunto de regras com multi-seletores.
  2. Um único espaço antes da abertura das chaves em um conjunto de regras.
  3. Uma única declaração por linha em um bloco de declarativo.
  4. Um nível de indentação para cada declaração.
  5. Um único espaço depois dos dois pontos de uma declaração.
  6. Sempre inclua um ponto-e-vírgula no fim da última declaração em um bloco declarativo.
  7. Coloque o fechamento das chaves na mesma coluna que o primeiro caracter do conjunto de regras.
  8. Separe cada conjunto de regras por uma linha em branco.

[cc lang=&#8221;css&#8221;]
  
.seletor-1,
  
.seletor-2,
  
.seletor-3 {
	  
-webkit-box-sizing: border-box;
	  
-moz-box-sizing: border-box;
	  
box-sizing: border-box;
	  
display: block;
	  
color: #333;
	  
background: #fff;
  
}[/cc]

#### Ordem de declaração

Declarações devem ser ordenadas segundo um único princípio. Minha preferência é por propriedades relacionadas para serem agrupadas e por propriedades estruturalmente importantes (por exemplo, posicionamento e box-model) para serem declaradas antes de propriedades tipográficas, fundo ou cor.

[cc lang=&#8221;css&#8221;]
  
.seletor {
	  
position: relative;
	  
display: block;
	  
width: 50%;
	  
height: 100px;
	  
padding: 10px;
	  
border: 0;
	  
margin: 10px;
	  
color: #fff
	  
background: #000;
  
}[/cc]

Ordenação alfabética também é popular, mas a desvantagem é que ela separa as propriedades relacionadas. Por exemplo, deslocamentos de posição não são mais agrupados e propriedades do box-model podem acabar propagando ao longo de um bloco de declaração.

#### Exceções e ligeiros desvios

Grandes blocos de declarações individuais podem atuar de forma diferente, através da formatação de linha única. Nesse caso, um espaço deve ser considerado depois da abertura das chaves e antes do fechamento das chaves.

[cc lang=&#8221;css&#8221;]
  
.seletor-1 { width: 10%; }
  
.seletor-2 { width: 20%; }
  
.seletor-3 { width: 30%; }
  
[/cc]

Longos valores de propriedades separados por vírgula &#8211; como coleções de degradês ou sombras &#8211; podem ser organizados em várias linhas em um esforço para melhorar a legibilidade e produz visualizações de diferença mais úteis. Existem vários formatos que poderiam ser usados; um exemplo é mostrado abaixo.

[cc lang=&#8221;css&#8221;]
  
.seletor {
	  
box-shadow:
		  
1px 1px 1px #000,
		  
2px 2px 1px 1px #ccc inset;
	  
background-image:
		  
linear-gradient(#fff, #ccc),
		  
linear-gradient(#f3c, #4ec);
  
}[/cc]

#### Miscelânea

Use valores hexadecimais em letras minúsculas, por exemplo: [cc lang=&#8221;css&#8221;]#aaa[/cc]
  
Use aspas simples ou duplas de forma consistente. Preferência por aspas duplas, por exemplo: [cc lang=&#8221;css&#8221;]content: &#8220;&#8221;[/cc]
  
Sempre coloque aspas em valores de atributos nos seletores, por exemplo: \[cc lang=&#8221;css&#8221;]input[type=&#8221;checkout&#8221;\]\[/cc\]
  
_Onde permitido_, evite especificar unidades para valores-zero, por exemplo: [cc lang=&#8221;css&#8221;]margin: 0[/cc]

### Pré-processadores: considerações de formatação adicionais

Diferentes pré-processadores de CSS possuem diferentes características, funcionalidades e sintaxe. Suas convenções devem ser extendidas para acomodar as particularidades de qualquer pré-processador em uso. As seguintes diretrizes são em referência ao Sass.

  * Limite o aninhamento a 1 nível de profundidade. Reavalie qualquer aninhamento que tenha mais de 2 níveis de profundidade. Isso impede que existam seletores CSS muito específicos.
  * Evite um grande número de regras aninhadas. Quebre-os para quando a legibilidade começar a ser afetada. Preferência por evitar aninhamentos que se espalhem por mais de 20 linhas.
  * Sempre coloque as declarações **@extend** nas primeiras linhas de um bloco declarativo.
  * Quando possível, agrupe declarações **@include** no topo de blocos declarativos, depois de qualquer declaração **@extend**.
  * Considere funções customizadas para prefixos com **x-** ou qualquer namespace. Isso ajuda a evitar qualquer potencial confusão na sua função com a função de CSS nativo ou de colidir com funções de bibliotecas.

[cc lang=&#8221;css&#8221;]
  
.seletor-1 {
	  
@extend .other-rule;
	  
@include clearfix();
	  
@include box-sizing(border-box);
	  
width: x-grid-unit(1);
	  
// outras declarações
  
}[/cc]

## 5. Nomeando

Você não é um compilador/compressor de código humano, então não tente ser.

Use nomes claros e previdentes para classes HTML. Escolha um padrão de nomes compreensível e consistente que faça sentido para arquivos HTML e arquivos CSS.

[cc lang=&#8221;css&#8221;]
  
/\* Exemplo de código com nomes ruins \*/

.s-scr {
	  
overflow: auto;
  
}

.cb {
	  
background: #000;
  
}

/\* Exemplo de código com bons nomes \*/

.is-scrollable {
	  
overflow: auto;
  
}

.column-body {
	  
background: #000;
  
}[/cc]

## 6. Exemplo prático

Um exemplo de várias convenções.

[cc lang=&#8221;css&#8221;]
  
/* ==========================================================================
  
Grid layout
  
========================================================================== */

/*
   
* Exemplo de HTML:
   
*
   
* 

<div class="grid">
  * </p> 
  
  <div class="cell cell-5">
  </div>
  
  <p>
    *
  </p>
  
  <div class="cell cell-5">
  </div>
  
  <p>
    *
  </p>
</div>

*/

.grid {
	  
overflow: visible;
	  
height: 100%;
	  
white-space: nowrap;
	  
font-size: 0;
  
}

.cell {
	  
box-sizing: border-box;
	  
position: relative;
	  
overflow: hidden;
	  
width: 20%;
	  
height: 100%;
	  
padding: 0 10px;
	  
border: 2px solid #333;
	  
vertical-align: top;
	  
white-space: normal;
	  
font-size: 16px;
  
}

/\* Células &#8211; Estados \*/

.cell.is-animating {
	  
background-color: #fffdec;
  
}

/* Células &#8211; Dimensões
  
========================================================================== */

.cell-1 { width: 10%; }
  
.cell-2 { width: 20%; }
  
.cell-3 { width: 30%; }
  
.cell-4 { width: 40%; }
  
.cell-5 { width: 50%; }

/* Células &#8211; Modificadores
  
========================================================================== */

.cell–detail,
  
.cell–important {
	  
border-width: 4px;
  
}
  
[/cc]

## 7. Organização

Organização de código é uma importante parte de qualquer base de código CSS, e crucial para grandes bases de código.

  * Separar logicamente distintas partes do código.
  * Usar arquivos separados (concatenados por um processo de build) para ajudar a dividir código para componentes distintos.
  * Se estiver usando um pré-processador, abstrair partes comuns de código em variáveis para cor, tipografia, etc.

## 8. Build e deploy

Os projetos devem sempre tentar incluir alguns meios genéricos pelos quais sua fonte possa ser avaliada, testada, comprimida e versionada em preparação para uso em produção. Para essa tarefa, o [grunt][10] por Ben Alman é uma excelente ferramenta.

## Conclusão

Independemente de você ter concordado ou não com o guia de estilo proposto, o importante é entender como uma padronização no estilo do código pode ajudar você e sua equipe. Pense nisso.

 [1]: http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml
 [2]: https://github.com/styleguide/
 [3]: https://twitter.com/#!/necolas
 [4]: http://necolas.github.com/normalize.css/
 [5]: http://html5boilerplate.com/
 [6]: https://github.com/zenorocha/idiomatic-css
 [7]: https://github.com/rwldrn/idiomatic.js
 [8]: https://github.com/zenorocha/idiomatic-css/tree/master/translations/pt-BR
 [9]: https://github.com/necolas/idiomatic-css
 [10]: https://github.com/cowboy/grunt