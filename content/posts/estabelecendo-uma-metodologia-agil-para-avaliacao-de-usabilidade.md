---
title: Estabelecendo uma metodologia ágil para avaliação de usabilidade
author: Talita Pagani
type: post
date: 2011-01-05
excerpt: Como forma de estabelecer um processo ágil para testes de usabilidade, uma das abordagens mais viáveis é a avaliação heurística, um método onde os próprios especialistas da empresa avaliam a interface de acordo com as heurísticas de usabilidade.
url: /estabelecendo-uma-metodologia-agil-para-avaliacao-de-usabilidade/
tweetbackscheck:
  - 1356387438
shorturls:
  - 'a:3:{s:9:"permalink";s:88:"http://tableless.com.br/estabelecendo-uma-metodologia-agil-para-avaliacao-de-usabilidade";s:7:"tinyurl";s:26:"http://tinyurl.com/3kpcssp";s:4:"isgd";s:19:"http://is.gd/IBjCUa";}'
twittercomments:
  - 'a:11:{i:129659214552498176;s:7:"retweet";i:129588389711314944;s:7:"retweet";i:129588311747608577;s:7:"retweet";i:145288595719192576;s:7:"retweet";i:145121819203080192;s:7:"retweet";i:145089184846192641;s:7:"retweet";i:145085876530200576;s:7:"retweet";i:145085876349833216;s:7:"retweet";i:177064148977467394;s:7:"retweet";i:177046209507237892;s:7:"retweet";i:177043955714752513;s:7:"retweet";}'
tweetcount:
  - 18
dsq_thread_id: 503029170
categories:
  - Artigos
  - Geral
tags:
  - avaliação heurística
  - design de interface
  - usabilidade

---
O conjunto de técnicas de usabilidade aplicado ao desenvolvimento da interfaces visa proporcionar: a facilidade de realização de tarefas; analise e otimização do processo de aprendizado do sistema; eficiência de uso; facilidade de memorização, evitando que o usuário necessite reaprender os processos de interação; e, por fim, a baixa ocorrência de erros, evitando transtornos na realização de tarefas e obtendo satisfação do usuário ao interagir com a aplicação.

Para que estes critérios sejam cumpridos, é necessário estabelecer uma abordagem para aplicar e garantir a efetividade da usabilidade através de padrões concisos de interfaces e rotinas de avaliação próprias para mensurar os diversos quesitos de interação do usuário com o website.

O [Alysson Franklin][1] já havia detalhado em um [artigo aqui no Tableless][2] um plano de usabilidade que passa por diversas etapas. Embora seja a metodologia mais adequada, em muitos casos é preciso adotar procedimentos mais ágeis e que também sejam eficientes.

Como forma de estabelecer um processo ágil para avaliação de usabilidade, uma das abordagens mais viáveis é a **avaliação heurística**, um método de inspeção onde os próprios especialistas da empresa avaliam a interface de acordo com as heurísticas de usabilidade. Neste tipo de teste, não há a presença dos utilizadores reais do sistema.

### Checklist para avaliação heurística

Cada website irá demandar um roteiro mais específico de avaliação da usabilidade. [Bastien e Scapin (1993)][3] definiram 8 critérios ergonômicos para interfaces humano-computador: Condução; Carga de Trabalho; Controle Explícito; Adaptabilidade; Gestão de Erros; Homogeneidade; Significado de Códigos e Denominações; Compatibilidade.

Nem todos os projetos precisarão ser verificados em todos estes critérios. Sites corporativos que apresentam, em sua maioria, apenas textos e imagens têm uma avaliação diferente em aplicação web composta de diversas ações, formulários e requisições, mas alguns itens são elementares a qualquer tipo de website.

Abaixo apresento uma listagem de critérios que pode ser utilizados para avaliar desde websites estáticos a aplicações web, adaptado de um [artigo do TestingGeek][4]. É uma avaliação rápida e sobre questões mais triviais, mas se bem analisada e reportada pode ajudar a melhorar de forma considerável a interface com o usuário.

#### Cores

  * O site deve utilizar (aproximadamente) cores padrões de links. _Isto não significa utilizar links azuis, mas a cor e o estilo utilizados devem indicar que seja um hiperlink e necessitam permanecer consistentes._
  * Os botões devem estar um formato e tamanho padrão. _Se você utiliza botões em formatos ou estilos distintos para diferenciar a funcionalidade de cada grupo, garanta que cada botão esteja consistente em seu grupo e que os agrupamentos também estejam consistentes com o estilo geral utilizado no website._
  * O plano de fundo da página não pode ser propenso a distrair o usuário do foco do site.

#### Conteúdo

  * Todas as fontes devem ser as mesmas. _Por exemplo, uma fonte escolhida para um subtítulo deve ser a mesma sempre na ocorrência deste tipo de texto e isto vale também para o estilo (negrito, itálico, etc)._
  * Os textos devem estar apropriadamente alinhados. _Evite também utilizar vários alinhamentos de texto no site, preferencialmente escolha apenas um. Evite centralizar corpo de texto._
  * Logo e textos de cabeçalho devem estar alinhados à esquerda. _Esta é uma questão da cultura de leitura e escrita. No ocidente utilizamos a leitura da esquerda para a direita mas isto varia em outras regiões._
  * Evitar o uso de caixa-alta em textos. _Utilizar com moderação e para casos (muito) específicos avaliando se não há dificuldade de leitura._

#### Imagens

  * Todas as imagens devem estar alinhadas apropriadamente.
  * Deve-se garantir que os botões que representam comandos estejam todos com tamanhos e formas similares, além de fonte e tamanho de fonte consistentes.
  * O formato dos banners (estilo, tamanhos e forma de exibição) devem ser os mesmos em todas as seções do site.
  * O texto deve se ajustar corretamente ao redor das imagens e possuir um espaçamento, para que não passe a impressão de estar &#8220;aglutinado&#8221; à imagem.
  * As páginas devem ser visualmente consistentes mesmo sem imagens.

#### Instruções

  * As mensagens de erro e os textos de ajuda nos campos de formulários devem estar grafadas corretamente.
  * Todos os campos e botões habilitados devem possuir texto de ajuda. _Isto pode ser através de um texto próximo ao campo, o value do campo do formulário ou o atributo title._
  * Mensagens de progresso devem estar presentes em ações que são dividas entre etapas durante várias páginas.

#### Navegação

  * Todos os campos desabilitados e somente leitura devem ser evitados na navegação entre os campos do formulário pela tecla TAB.
  * As barras de rolagem devem aparecer se necessário.
  * Deve haver um link para a página inicial em cada página.

#### Usabilidade

  * Todos os rótulos dos campos de formulário devem ser escritos corretamente e de maneira clara.
  * As fontes não devem ser muito grandes nem tampouco muito pequenas para ler.
  * Os nomes em botões de comando e caixas de opção não devem estar abreviados.
  * Garantir que caixas de opções, botões de opção e botões de comando estão logicamente agrupados em áreas de agrupamento claramente demarcadas.
  * As páginas devem ser impressas de modo legível sem cortar o texto.
  * O site deve possuir um visual consistente e claramente reconhecível.
  * Caso o site possua uma área de login, os usuários devem possuir a opção de efetuar login utilizando tanto um nome de usuário quanto um e-mail como ID.
  * O site deve se ajustar às resoluções de tela mais comuns.
  * A terminologia do site deve ser adequada aos usuários-alvo do site.

### Como pode ser aplicado

No meu TCC, utilizei heurísticas para avaliar a interface de intranet que havia desenvolvido. Como forma de mensurar quais critérios atendiam às recomendações, inseri as heurísticas em uma planilha separadas por categorias semelhante às descritas acima. Ao lado de cada heurística, eu atribuía a seguinte pontuação:

  * -1: não atende às recomendações
  * 0: atende parcialmente às recomendações
  * 1: atende completamente às recomendações

Os critérios que não atendem ou que atendem parcialmente às heurísticas devem ser analisados e reportados à equipe de desenvolvimento para montar um plano de melhoria e correção.

Se você deseja utilizar os critérios apresentados neste artigo, [disponibilizei esta planilha para download][5].

 [1]: http://tableless.com.br/?author=9
 [2]: http://tableless.com.br/vote-no-especialista-em-usabilidade-para-presidente
 [3]: http://www.labiutil.inf.ufsc.br/CriteriosErgonomicos/Abertura.html
 [4]: http://www.testinggeek.com/index.php/testing-templates/checklist-guidelines/78-web-application-ui-checklist
 [5]: http://tableless.com.br/uploads/2010/12/Avaliação-Heurística.xls