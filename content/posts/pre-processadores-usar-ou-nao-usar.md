---
title: 'Pré-processadores: usar ou não usar?'
author: Diego Eis
type: post
date: 2013-07-22
excerpt: Meus dois centavos sobre a utilização de pré processadores de CSS.
url: /pre-processadores-usar-ou-nao-usar/
dsq_thread_id: 1518177974
categories:
  - Artigos
  - CSS
  - CSS3
  - HTML
  - HTML5

---
Faz tempo que estou tentando escrever um post sobre pré processadores de CSS. Sempre que eu digo que sou meio contra a utilização deles pra alguém, ouço a inevitável pergunta: por quê?

O [Miller Medeiros][1] escreveu um ótimo artigo com o nome de [The problem with CSS pre-processors][2]. Lá ele cita alguns pontos interessantes, que pra mim já são suficientes para não usar.

Mas como eu disse: sou **meio** contra. Isso quer dizer que eu admito, sim, que em alguns casos, muito específicos eles podem nos ajudar muito. Eu sempre fico em dúvida em utilizá-los ou não em meus projetos. Um desses casos: eu participo [de um projeto][3] onde o usuário pode fazer vários painéis de cores diferentes. Usamos SASS para fazer essa parte de gerenciamento de cores. Se não fosse ele certamente nos perderíamos depois de um tempo.

Pré processadores podem ajudar como também podem maltratar bastante. Basta um escorregão para que seu projeto vire um inferno. Por isso, mesmo que eu seja contra, eu incentivo que você experimente e tire suas próprias conclusões. Nas próximas linhas dou meus dois centavos sobre o assunto.

## Curva de aprendizado de novos integrantes

É comum recebermos novos integrantes na equipe. Pessoas vem e vão. Isso é normal em qualquer time. O problema é que sempre que alguém novo chega, esse alguém precisa aprender, de preferência o mais rápido possível, os detalhes do projeto. Pra facilitar essa curva de aprendizado, as equipes podem manter um manual explicando as boas práticas de escrita de código, scrum e tudo isso aí ajudam. Mas não importa quantas reuniões você faça, o cabra só vai conseguir conhecer mesmo o tamanho do projeto quando colocar a mão na massa.

Quando o código foi escrito sem nenhum pré processador, a curva de aprendizado é muito menor. Ele não precisa aprender os costumes da equipe quanto às preferências do uso das features do pré processador escolhido. Se a equipe estiver usando SASS, por exemplo, podem existir uma série de regras de mixins e extends que pode demorar para fazer sentido. Sem comentar o aninhamento (nesting) de seletores para evitar o repetimento de elementos. Já é difícil de entender todas as relações de elementos e suas formatações na maneira normal, imagine usando indentação para hierarquizar os seletores.

Isso pode prejudicar bastante a manutenção, principalmente se a manutenção for feita por um novato no projeto, que por não conhecer os miúdos do código, pode acabar alterando algum valor que é reutilizadao em vários mixins/extends e seus correlatos.

Para evitar problemas assim, a documentação deveria ser muito bem atualizada, apontando todas as relações de mixins, extends, variáveis e etc. E se você já tentou manter uma simples documentação dentro de uma equipe sabe que é quase impossível ter 100% de comprometimento para atualizar os mínimos detalhes. Principalmente detalhes que mudam o tempo inteiro.

## Difícil voltar

Quando decidimos usar um pré processador é um caminho sem volta.

Até onde pesquisei, uma vez que seu projeto foi escrito sob as regras de um pré processador, não há como voltar atrás, a não ser que você utilize a versão já processada desse código. Mas aí entramos em outro problema: geralmente pré processadores escrevem mais código do que você escreveria manualmente. Duas opções: corrigir o excesso de código do projeto inteiro na mão ou ignorar e seguir em frente.

Há equipes que se arrependem e decidem que deste ponto em diante escreverão CSS puro, sem utilizar as features do pré processador.

## Nunca será como se fosse feito manualmente

Como já citamos, o código gerado pelo pré processador nunca será como o código escrito por você. Nunca vi nada que tente gerar código automaticamente fazer algo que não fosse duvidoso.

Veja um exemplo simples de uso do **mixin** do SASS:

<pre class="lang-sass">@mixin alert {
    color: red;
    border: 2px solid red;
}

.alert-default {
    @include alert;
}

.alert-special {
    @include alert;
    background-color: gray;
}
</pre>

Resultado:

<pre class="lang-css">.alert-default {
  color: red;
  border: 2px solid red;
}

.alert-special {
  color: red;
  border: 2px solid red;
  background-color: gray;
}
</pre>

Entende a duplicação código de border e color das duas propriedades? Claro, no exemplo acima seria muito melhor ter usado um **extend** em vez de **mixin**. Mas e se um desavisado cometer esse erro?

Com o extend, fica assim:

<pre class="lang-sass">.alert {
    color: red;
    border: 2px solid red;
}

.alert-default {
    @extend alert;
}

.alert-special {
    @extend alert;
    background-color: gray;
}
</pre>

Que já ser compilado para:

<pre class="lang-css">.alert, .alert-default, .alert-special {
    color: red;
    border: 2px solid red;
}

.alert-special {
    background-color: gray;
}
</pre>

Legal, ele agrupou os seletores que tem a mesma formatação. Ficou mais perto do que talvez faríamos na vida real. Mas aí alguém usa isso em trilhões de lugares diferentes.
  
Lembra que [algumas versões IE tem um limite para a quantidade de seletores][4] agrupados?
  
O código também vai ficar bem complicado de se manter com tantas dependências. Quem vai lembrar de atualizar a documentação, como já havíamos comentado.

## Cedo ou tarde o CSS vai amadurecer

O W3C tem trabalhado bastante para oficializar o mais rápido possível as novidades do CSS. Os fabricantes de browsers também tem se esforçado para manter seus navegadores atualizados, trazendo sempre novidades para experimentarmos e usarmos em projetos hoje, agora. Cedo ou tarde o CSS vai ter features como as dos pré processadores para nos ajudar com a manutenção e economia de código. Não é algo imediato, claro, mas sabemos que virá.

Com certeza vai ser bem melhor do que temos hoje em vários sentidos. Por isso que eu prefiro esperar pra ver.

## Conclusão

Esses são os motivos pelos quais eu ainda não aderi de vez aos pré processadores. Como disse eu uso aqui e ali pra tentar usufruir das vantagens, mas ainda fico com uma sensação de que essas vantagens realmente não valem tanto a pena quanto parecem.

Você já usou ou usa em algum projeto? O que acha?

 [1]: http://blog.millermedeiros.com/about/
 [2]: http://blog.millermedeiros.com/the-problem-with-css-pre-processors/
 [3]: http://github.com/locaweb/locawebstyle/
 [4]: https://www.google.com.br/search?q=ie+limit+css+selectors&ie=UTF-8&oe=UTF-8&hl=en