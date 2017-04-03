---
title: Arquitetura CSS – Anotações da palestra Rafael Rinaldi
author: Diego Eis
type: post
date: 2014-12-08
excerpt: Anotações que fiz sobre a palestra do Rafael Rinaldi no Seminário Locaweb que houve em SP.
url: /arquitetura-css-anotacoes-da-palestra-rafael-rinaldi/
categories:
  - Geral

---
Estas foram as minhas anotações da palestra que o [Rafael Rinaldi][1] fez no Seminário Locaweb do dia 05/12 em São Paulo. Você pode [encontrar todas as palestras que ocorreram nesse dia aqui][2], gratuitamente. Os [slides da palestra se encontram aqui][3].



Rafael falou sobre as várias arquiteturas CSS que você encontra hoje no mercado. Um ponto que achei interessante na palestra foi que ele enfatizou que cada uma dessas arquiteturas (SMACSS, BEM, SUIT etc) surgiram por necessidades de equipes ou empresas. 

Até agora eu não encontrei ninguém que usasse exclusivamente uma dessas arquiteturas, mas normalmente o que eu encontro são equipes que fizeram uma mistura entre as características de cada arquitetura. É até melhor dessa forma, geralmente você não gosta da solução inteira. Eu gosto bastante da parte de estados do SMACSS e odeio muito os duplos hífens e underscores do BEM.

Abaixo, seguem as anotações:

## Arquitetura CSS

  * O que é culpa do CSS e o que é nossa culpa?
  * O que pode ser culpa do CSS? - Não é muito expressivo - Ordem de definição de dependências.  - Especificidade - Cheio de truques
  * E o que é nossa culpa? - Falta de conhecimento sobre o próprio projeto; - Caos na estrutura; - Documentação inexistente ou muito ruim - Não analisar o que já existe antes de criar algo do zero
  * Desenvolver interfaces é um trabalho complexo
  * Ao desenvolver você tem uma camada para cada objetivo. Isso é bom porque é organizada.
  * Técnicas são diferentes de frameworks/bibliotecas
  * **OOCSS &#8211; Object Oriented CSS**  
      * O OOCSS foi influenciado pelo paradigma da orientação a objetos 
      * Nessa técnica você categoriza os elementos na página como CSS Object. É um padrão visual que se repete e que pode ser abstraído em um contexto próprio 
      * Qualquer padrão visual que pode ser encaixado a outros elementos na página são objetos. 
      * A ideia é separar a estrutura de marcação de obrigações visuais. Separar o conteúdo do contexto.
  * **SMACSS**  
      * Feito para resolver problemas específicos do Yahoo! Mail. 
      * Você define regras padrões de estilo no base. São coisas que não estão atreladas a algum elemento específico. Um reset, o background padrão do body, border dos inputs, etc… 
      * A camada de layout são utilizados em elementos fixos na aplicação. Eles terão um seletor único e não reutilizável 
      * Os modelos são trechos de código reutilizáveis. 
      * Os estados cuidado de como os módulos irão se apresentar em estados específicos. Eles são representados por classes com o prefixo **is**: .button.is-disabled
  * **BEM &#8211; Block, Element, Modifier**
	  
     </p> 
      * Foi desenvolvido por Russos para resolver problemas específicos da Yandex.
      * A camada de bloco é definida como um bloco que pode conter vários elementos. Uma caixa que contém com título, parágrafo e botão, é um bloco por exemplo. Um grupo de elementos forma um bloco.
      * Um **element** nunca existe sem um bloco. Ele é uma parte que forma um bloco.
      * O **modifier** é o que controlar o estado dos elementos.
      * A nomenclatura do BEM usa hífen para separar palavras em nomes longos. Underscore duplo para separar um bloco de um elemento.
     
    
      * A forma de nomear no BEM é um dos motivos de estranhamento pelos devs.
  * **SUIT**  
      * Criador por desenvolvedores do Twitter numa tentativa de focar numa arquitetura baseada em componentes. 
      * A nomenclatura do SUIT utiliza camelCase para nomes longos. 
      * Utilitários são feitos com classes genéricas para controlar o uma característica do elemento. Exemplo: transformar um elemento em bloco ou linha. Flutuar para esquerda ou direita.
  * **itcss &#8211; Inverted Triangle CSS**  
      * Abordagem que vista escrever CSS baseado na ordem de especificidade 
      * Settings: variáveis e configurações 
      * Tools: mixins e funções 
      * Generic: resiste, configuração de box sizings 
      * Base: estilos atrelados a tags, sem o uso de classes 
      * Objects, Components, Trumps 
      * Evita redundância na descrição de regras de estilos 
      * Elimina problemas com especificidade 
      * Estrutura granular 
      * Elimina a necessidade de escrever CSS para remover CSS
  * O Bootstrap foi um framework a frente do seu tempo. Ele popularizou uma série de iniciativas e métodos de arquitetura de CSS que utilizamos hoje
  * **Várias vantagens**  
      * O Fato de pensar numa arquitetura de CSS, JS e etc, faz com que o time fale a mesma língua 
      * Nesse ponto não importa o gosto pessoal, importa o que foi decidido juntamente com o time 
      * Facilita o uso de ferramentas e a criação de um guia de estilo 
      * Torna realmente possível o desenvolvimento de interfaces baseada em componentes 
      * Evita depender de como o maria está estruturado no momento de criar estilos 
      * Força uma análise contextual [e crítica] da interface. 
      * Maior flexibilidade na hora de lidar com design responsivo
  * Não existe bala de prata

 [1]: https://twitter.com/rafaelrinaldi
 [2]: https://www.eventials.com/locaweb/groups/4o-seminario-locaweb-desenvolvimento-sao-paulo/
 [3]: https://speakerdeck.com/rafaelrinaldi/arquitetura-css