---
title: Não tenho versão mobile, faço ou não faço?
authors: Diego Eis
type: post
date: 2014-01-06
excerpt: Ainda tem dúvidas se deve ou não fazer a versão mobile do seu produto ou site? Saia dessa...
url: /nao-tenho-versao-mobile-faco-ou-nao-faco/
dsq_thread_id: 2092785496
categories:
  - CSS
  - Mobile
tags:
  - 2014
  - adaptive web design
  - awd
  - design mobile
  - mobile
  - responsive web design
  - rwd
  - web mobile

---
Estamos fazendo uma reestruturação no [framework da firma][1]. A primeira versão do projeto tinha como objetivo iniciar uma estruturação e uniformização de comportamento e design dos layouts de cada produto, melhorando o código front-end gerado, automatizando algumas tarefas e uniformizando o design e a expediência de uso. Não havíamos planejado nessa primeira versão qualquer tipo de compatibilidade com dispositivos móveis.

Nessa reestruturação, o objetivo principal é produzir um novo código mais legível e escalável possível, de forma que não apenas nossa equipe de front-end consiga usar componentes, mas também que os back-ends possam montar painéis inteiros, como um quebra-cabeças, sem a necessidade de um front-end para tarefas básicas.

O outro objetivo, tão importante quanto, é implementar uma versão mobile dos painéis. Logo, produzimos um código permitir que o layout seja responsivo e também cada elemento está sendo reformulado, se tornando um elemento adaptativo.

Estamos usando o método de Mobile First para criar e produzir os elementos e a estrutura de layout. Isto por si só está sendo uma experiência de travar o cérebro. Mas algo que estamos discutindo muito é: nós não temos nenhum tipo de dado para justificar todo o trabalho para produzir e priorizar a versão mobile nos produtos. Não há resultados para mostrar indicativos que temos mais visitantes usando dispositivos mobile do que desktops. Não há estatísticas dos nossos produtos mostrando alguma tendência positiva de uso de mobiles nos painéis. Não temos nada disso simplesmente por que não tínhamos versão mobile.

Várias e várias vezes criamos uma solução perfeita para desktops, mas que não é possível &#8220;migrar&#8221; a mesma experiência na versão mobile, logo, descartamos essa solução desktop para fazer algo mais homogêneo entre as duas plataformas. Como vamos justificar uma atitude dessa? O motivo disso é óbvio: não temos provas por que simplesmente não havia versão mobile até então. Só saberemos se todo esse trabalho vai valer a pena ou não apenas depois, quando terminarmos tudo. Aí sim saberemos exatamente o que dá certo, o que pode melhorar, o que teremos que matar sem choradeira&#8230; Até lá, temos apenas um feeling.

## Dúvida sobre versão mobile

Ter dúvidas se o trabalho de fazer uma versão mobile ou responsiva vale a pena é normal. Como no nosso caso, até pouco tempo ninguém pensava nessa coisa toda.

Algumas empresas decidem implementar uma versão mobile paliativa, com menos informação ou menos features, para não dar muito trabalho apenas com a intenção de testar a adesão dos usuários. Não recomendo essa abordagem. Se a versão mobile for feita pela metade, o usuário não encontrará valor real na versão mobile. Obviamente o uso dessa versão não será frequente, gerando maus resultados. Logo a versão mobile acaba não saindo, já que não houve adesão dos usuários.

Se você quer saber se a versão mobile vai dar certo ou não faça-o perfeito. Pense num projeto decente, com tudo o que o usuário precisa para usufruir da melhor experiência possível quando estiver em um dispositivo móvel. Assim você terá dados reais para decidir se vale ou não a pena.

## Medir, medir e medir

Depois de feito o trabalho para a versão mobile, você precisa medir a utilização do usuário. Há pelo menos 3 meios para obtermos dados de utilização importantes: podemos usar o Analytics, extraindo dados via dashboards customizados. Ainda no Analytics, podemos implementar os Track Events para saber se os módulos adaptados da versão mobile estão sendo usados. E por último, mas não menos importantes, há a possibilidade de fazer testes de usabilidade, pedindo para usuários reais testar a versão em seus aparelhos. É legal selecionar usuários que já demonstraram algum interesse nesse tipo de versão. 

Eu uso um dashboard customizado bem bacana que filtra dados da utilização mobile do seu site feito pelo pessoal da [Agência Mestre][2]. Para usar, <a href="https://www.google.com/analytics/web/template?uid=_0Bifw1MQRiRKY7RDhQIww”>clique nesse link</a>. Certifique-se antes que você está logado em sua conta do analtytics.

## Linha de corte dos Aparelhos

Eu acho que você não quer passar pelos menos problemas de compatibilidade de browser e versões específicas que assombram a todos no desktop, na sua versão mobile. Há uma gama de aparelhos de todos os tamanhos, com densidades de pixels, resoluções e tamanhos de telas totalmente diferentes. É por esse motivo que você precisa de uma linha de corte.

Geralmente a galera inclui smartphones como iPhone e aparelhos com as duas versões mais atuais do Android: a última versão e a anterior. Isso te dá uma margem de boa para aproveitar as novidades sem perder a sanidade. Esqueça aparelhos com versões antigas dos Androids. Quem tem problemas com a versão 2.5 sabe do que eu estou falando. Existem muitos aparelhos que são ótimos, mas rodam uma versão muito antiga do Android. Isso é um equivalente pior do que tentar forçar que seu site funcione no IE6 sem perder qualidade nos outros browsers.

Não quero que você me entenda mal aqui. Não importa qual seja sua linha de corte, contanto que você saiba as consequências e o que você está abrindo mão ao escolher uma linha de corte muito baixa, contemplando aparelhos ruins. Entenda: ninguém precisa agradar a TODOS.

## Concluindo

Acho que você entendeu que não é possível ter resultados de verdade se você não tiver algo para testar. Se você não tem uma versão responsiva/adaptativa do seu site, experimente fazer só para depois decidir se vale ou não a pena manter essa versão.

O Luke Wroblewski tem <a href="https://www.lukew.com/ff/entry.asp?1841”>um post interessante</a> que mostra alguns dados da utilização movie de grandes websites.
  
Mais da metade dos consumidores da Amazon compram usando um dispositivo móvel durante a temporada de final de ano (<a href="https://phx.corporate-ir.net/phoenix.zhtml?c=176060&p=irol-newsArticle&ID=1886961&highlight=“>fonte</a>).
  
101 milhões de americanos usam o facebook diariamente via mobile. Isso equivale a 78% da visitação diária americana, que tem o total de 128 milhões ([fonte][3]).
  
47.4 milhões de pessoas visitaram a versão mobile da ESPN em Setembro de 2013. Esta foi a primeira vez que o site mobile teve mais visitas únicas que o site desktop ([fonte][4]).

Mais do que provado que você deve prestar atenção nessa papagaiada toda, não?

 [1]: https://locaweb.github.io/locawebstyle
 [2]: https://www.agenciamestre.com/
 [3]: https://techcrunch.com/2013/08/13/facebook-mobile-user-count/
 [4]: https://espnmediazone.com/us/press-releases/2013/10/espn-digital-media-sets-sports-category-record-in-september/