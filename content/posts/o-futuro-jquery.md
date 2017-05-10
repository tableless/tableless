---
title: O futuro do jQuery
author: Dave Arel
type: post
date: 2014-02-28
excerpt: Você já pensou no futuro do jQuery?
url: /o-futuro-jquery/
dsq_thread_id: 2336134935
categories:
  - JQuery
  - Traduções
tags:
  - JavaScript
  - JQuery

---
Desde quando o jQuery foi lançado em 2006, ele se tornou extremamente indispensável no dia-a-dia do desenvolvimento web. Ele é usado em pelo menos 60% dos websites mais visitados e sem dúvida é uma das bibliotecas client-side mais usadas hoje em dia.

O jQuery se tornou tão popular por uma razão: ele é limpo e sua API é fácil de usar porque abstrai a complexidade de scripts cross-browser, principalmente nos browsers antigos. Logo, conforme nos aproximamos de uma era na Web, onde os browsers estão se tornando rapidamente algo do passado, é compreensível o aumento da necessidade em utilizar tais APIs, mas pensando também na questão do futuro do jQuery.

Mas antes que você pense qualquer coisa, vamos considerar uma alternativa.

## API nativa

Embora o jQuery tenha adicionando um tremendo valor na web com o passar dos anos, ele criou uma densa camada entre desenvolvedores e o DOM. Muitos dos desenvolvedores não entendem exatamente o que está acontecendo por trás daquele sinal de dólar ($). Enquanto isso, todos os comandos nativos equivalentes são fáceis de usar.

Isto não significa que precisamos evitar o jQuery. Nós precisamos considerar o jQuery como uma ferramenta ao invés de uma exigência. Avaliando o [código fonte do jQuery][1], podemos encontrar [muito valor e algumas ideias][2] sobre o que estamos usando. Há também [muito][3] o que [conversar][4] quando comparamos a sintaxe do jQuery com as alternativas nativas. Estas comparações são uma boa base para entender o que está acontecendo pro trás da cortina e é um grande passo para entender o DOM. Entretanto, é importante entender também que os browsers estão inclinados a terem bugs. Na verdade, [o estado do jQuery em 2013][5] afirma-se que o &#8220;jQuery 2.0 agora tem mais patches e correções para o Chrome, Safari e Firefox do que para o Internet Explorer&#8221;. Todo cuidado é pouco, seja cuidadoso quando abandonar o uso de uma biblioteca altamente testada e largamente utilizada como o jQuery.

<blockquote class="twitter-tweet" lang="en" xml:lang="en">
  <p>
    You Might Not Need jQuery! … assuming you&#39;ll address these bugs in your hand-written code: <a href="https://t.co/j2hrG2nCpX">https://t.co/j2hrG2nCpX</a>
  </p>
  
  <p>
    &mdash; Paul Irish (@paul_irish) <a href="https://twitter.com/paul_irish/statuses/431584056883429376">February 7, 2014</a>
  </p>
</blockquote>



## A sintaxe, a abstração

Frameworks server-side como Ruby on Rails ou frameworks client-sides como Ember e Angular são largamente usadas por conveniência. Conveniência é economia de tempo, e tempo é dinheiro.

jQuery === $ #amiright?

Cada linha de código que é escrita nestes frameworks são vistos por milhões de olhos. Erros são capturados e bugs são encontrados.

Nós também valorizamos um código limpo, curto, proficiente e rápido. Tamanho de arquivo desnecessário, features dispensáveis e condicionais são algo que precisamos considerar. Especialmente dado ao aumento de visitantes mobile. Isto pode ser resolvido com gerenciamento de dependências modulares.

<blockquote class="twitter-tweet" lang="en" xml:lang="en">
  <p>
    “YOU MIGHT NOT NEED <a href="https://twitter.com/jquery">@jquery</a>” Bullshit, we need granular dependency management for modular libraries.
  </p>
  
  <p>
    &mdash; Stephan Bönnemann (@boennemann) <a href="https://twitter.com/boennemann/statuses/429214761122021376">January 31, 2014</a>
  </p>
</blockquote>



Enquanto o futuro do jQuery seja incerto, uma coisa é clara, ele não vai a lugar nenhum. E mesmo que o código do jQuery continue pequeno e seu código legado continue sendo removido, ainda assim iremos continuar usando apenas uma fração de toda a biblioteca disponível. Nós não precisamos incluir toda a biblioteca apenas para usar uma parte dela.

O futuro do jQuery é o gerenciamento modular de dependencias (eu espero).

## Javascript modular

[Browserify][6] e [RequireJS][7] são dois métodos para [escrever Javascript de forma modular][8]. Ambas as ferramentas tem construído scripts no qual incluem apenas os módulos que são necessários pela aplicação. Se o jQuery for modularizado dessa forma, partes do jQuery que você não usa não serão compiladas em produção. Você não precisa recompilar manualmente seu jQuery toda vez que quiser incluir uma nova feature. Você também nunca precisa se preocupar sobre remover features do jQuery caso não as utilize mais. Em desenvolvimento, estes módulos devem estar disponíveis para você, mas não devem ser publicados em produção a menos que eles sejam necessários em sua aplicação.

No jQuery 1.9, o [código fonte][9] já foi modularizado. A curto prazo, isso permitiu a criação de um [script que constrói um jQuery customizado][10]. [Muitas][11] [bibliotecas][12] já tem implementado este tipo de coisa. A longo prazo, entretanto, isso pode permitir que o uso em um carregador AMD-compliant.

## Conclusão

jQuery é uma biblioteca poderosa, bem testada e muito utilizada. Mesmo que ainda faça sentido incluir o jQuery na maioria das suas aplicações web, é importante entender que o DOM não é um lugar assustador. O jQuery pode te ajudar a desviar de bugs e complicações, mas não deve substituir nosso conhecimento ou habilidade para manipular o DOM de forma efetiva e significante.

O que você acha sobre o futuro do jQuery? [Me envie uma mensagem via twitter @davearel][13].

**Atualização (27 de Fevereiro de 2014):**

Se você nunca considerou uma implementação modular de dependências usando uma biblioteca como o jQuery, você irá entender que isto não é simples.

Especialmente dado ao tamanho do código fonte do jQuery. Se você está interessado em contribuir para a discussão sobre como arquitetar algo assim, fale agora: <https://gist.github.com/davearel/9254418>

&#8212;

_Artigo traduzido por **[Diego Eis][14]** e [escrito originalmente em inglês][15] pelo [Dave Arel][16] para o blog [Belly][17]._

Se encontrar algum erro ou tem uma sugestão para melhorar a tradução, por favor, [nos avise][18]!

 [1]: http://github.com/jquery/jquery "/a> quando comparamos a sintaxe do jQuery com as alternativas nativas. Estas comparações são uma boa base par"
 [2]: http://www.paulirish.com/2010/10-things-i-learned-from-the-jquery-source/ "á acontecendo pro trás da cortina e é um grande passo para entender o DOM. Entretanto, é importante entender "
 [3]: http://youmightnotneedjquery.com/ "inados a terem bugs. Na verdade, <a href="http://blog.jquery.com/2013/01/14/the-state-of-jquery-2013/" title="
 [4]: http://toddmotto.com/is-it-time-to-drop-jquery-essentials-to-learning-javascript-from-a-jquery-background/ "hes e correções para o Chrome, Safari e Firefox do que para o Internet Explorer">o estado do jQuery em 2013</"
 [5]: http://blog.jquery.com/2013/01/14/the-state-of-jquery-2013/ "jQuery 2.0 agora tem mais patches e correções para o Chrome, Safari e Firefox do que para o Internet Explorer"
 [6]: http://browserify.org/
 [7]: http://requirejs.org/
 [8]: http://addyosmani.com/writing-modular-js/]
 [9]: https://github.com/jquery/jquery
 [10]: https://github.com/jquery/jquery#how-to-build-your-own-jquery
 [11]: http://zeptojs.com/#modules
 [12]: http://lodash.com/custom-builds
 [13]: http://twitter.com/davearel
 [14]: http://medium.com/@diegoeis
 [15]: https://tech.bellycard.com/blog/the-future-of-jquery/
 [16]: https://tech.bellycard.com/team/dave-arel/
 [17]: https://tech.bellycard.com/
 [18]: http://tableless.com.br/contato/