---
title: Medindo performance e latência com a Navigation Timing API
author: Talita Pagani
type: post
date: 2013-03-14
excerpt: A Navigation Timing API é uma nova especificação do W3C para lidar com aferição de performance de modo mais efetivo em páginas web.
url: /navigation-timing-api/
dsq_thread_id: 1136701493
categories:
  - Código
  - JavaScript
tags:
  - desempenho client-side
  - JavaScript
  - latência
  - navigation timing API
  - performance

---
Performance e latência são alguns dos requisitos de qualidade e experiência do usuário mais desafiadores em desenvolvimento web, especialmente quanto à [performance _client-side_][1].Sabemos como aplicar [técnicas que melhoram muito a performance da página][2], mas medir o desempenho adequadamente já não é tão trivial à nossa rotina de desenvolvimento. Pensando nisso, o W3C tem uma nova recomendação chamada [Navigation Timing API][3]. Com isso, é possível obter métricas e estatísticas detalhadas de modo nativo sobre tempo de carregamento, navegação entre páginas e carregamento de eventos.

A vantagem desta API sobre ferramentas externas e outras técnicas de aferição de latência via JavaScript é a quantidade de informações que podem ser obtidas sobre o tempo de carregamento da página em diferentes fases, proporcionando a medição em um escopo maior (_end-to-end_). Ferramentas como o [PageSpeed][4] e o [WebPageTest][5] já têm utilizado dados da Navigation Timing API na análise de carregamento de páginas.

## Suporte

Até o momento da escrita deste artigo, a [Navigation Timing é suportada][6] pelo Chrome 24.0+, Firefox 18.0+ e IE 9+. A especificação já é recomendação do W3C desde dezembro de 2012 e a versão 2 da API já está em desenvolvimento.

## Utilizando o objeto window.performance

Os parâmetros de carregamento da página são acessados através das propriedades **_navigation_** e **_timing_** do objeto **_[window.]performance_**. A propriedade _**navigation**_ contém informações sobre como o usuário chegou à página e a propriedade _**timing**_ apresenta as informações sobre carregamento da página.

É possível testar o _**window.performance**_ diretamente no console do navegador. Supondo que estamos utilizando o Chrome, basta abrir a Developer Tools > Console e digitar _**performance**_ no prompt. Abaixo, um exemplo do que você poderá obter. Note que o Chrome adiciona mais uma propriedade chamada _**memory**_, que pode ser acessada pelo _**performance.memory**_, apresentando informações sobre a utilização de memória pelo JavaScript.

<div id="attachment_15833" style="width: 413px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2013/03/Capturar.png"><img class="size-full wp-image-15833" alt="Detalhes das propriedades do Navigation Timing API" src="http://tableless.com.br/uploads/2013/03/Capturar.png" width="403" height="512" srcset="uploads/2013/03/Capturar.png 403w, uploads/2013/03/Capturar-132x168.png 132w, uploads/2013/03/Capturar-244x310.png 244w" sizes="(max-width: 403px) 100vw, 403px" /></a>
  
  <p class="wp-caption-text">
    Detalhes das propriedades do Navigation Timing API
  </p>
</div>

Cada uma destas propriedades do timing expressa o tempo de um determinado evento em milisegundos a partir das 00:00 do dia 1º de Janeiro de 1970 (UTC). Quando o valor de algum dos atributos é zero, significa que este evento não ocorreu.

## Os tipos de navegação ou “como cheguei até esta página?”

A _**window.performance.navigation**_ armazena dois atributos que pode ser utilizados para detectar como o usuário chegou à página atual, por exemplo, via um redirecionamento, botões de navegação do histórico do navegador ou entrada normal por URL na barra de endereço. Os atributos são:

  * **_redirectCount_****:** o número de redirecionamentos que ocorreram até que a página final fosse carregada;
  * **_type_****:** a forma como o usuário chegou à página.

O atributo type é uma constante do tipo enumerada e pode apresentar os seguintes valores:

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top" width="157">
      <b>Constante</b>
    </td>
    
    <td valign="top" width="48">
      <b>Valor</b>
    </td>
    
    <td valign="top" width="376">
      <b>Descrição</b>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="157">
      <code>TYPE_NAVIGATENEXT</code>
    </td>
    
    <td valign="top" width="48">
    </td>
    
    <td valign="top" width="376">
      Navegação iniciada por click em um link, entrada de URL na barra de endereço do navegador, submissão de formulário ou por uma operação de script.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="157">
      <code>TYPE_RELOAD</code>
    </td>
    
    <td valign="top" width="48">
      1
    </td>
    
    <td valign="top" width="376">
      Recarregamento de página (por botão de <i>refresh</i> ou location.reload()).
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="157">
      <code>TYPE_BACK_FORWARD</code>
    </td>
    
    <td valign="top" width="48">
      2
    </td>
    
    <td valign="top" width="376">
      Navegação através dos botões de avançar/voltar do navegador ou por operações de navegação no histórico através de script (ex.: history.back()).
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="157">
      <code>TYPE_UNDEFINED</code><code></code>
    </td>
    
    <td valign="top" width="48">
      255
    </td>
    
    <td valign="top" width="376">
      Qualquer tipo de navegação que não se enquadre nos valores acima.
    </td>
  </tr>
</table>

## Os atributos de tempo de carregamento

A propriedade _**window.performance.timing**_ armazena os dados relevantes sobre o tempo de carregamento desde o momento em que o navegador dispara a requisição para obter a página até o momento em que o carregamento de todo o documento é finalizado. A tabela abaixo mostra uma breve descrição destes eventos na ordem em que eles ocorrem:

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top" width="90">
      <b>Estágio</b>
    </td>
    
    <td valign="top" width="222">
      <b>Atributo</b>
    </td>
    
    <td valign="top" width="269">
      <b>Descrição</b>
    </td>
  </tr>
  
  <tr>
    <td rowspan="11" width="90">
      <p align="center">
        Rede
      </p>
    </td>
    
    <td valign="top" width="222">
      navigationStart
    </td>
    
    <td valign="top" width="269">
      Tempo depois de o documento anterior ter iniciado o evento de <i>unload</i>.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      unloadEventStart
    </td>
    
    <td valign="top" width="269">
      Tempo imediatamente antes do evento de unload ser disparado.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      unloadEventEnd
    </td>
    
    <td valign="top" width="269">
      Tempo após o documento anterior ter completado o unload, ou seja, ter sido descarregado para que o próximo documento seja carregado.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      redirectStart
    </td>
    
    <td valign="top" width="269">
      Tempo da busca que iniciou o redirecionamento.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      redirectEnd
    </td>
    
    <td valign="top" width="269">
      Tempo após a ocorrência do último redirecionamento.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      fetchStart
    </td>
    
    <td valign="top" width="269">
      Tempo em que o recurso começa a ser buscado.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      domainLookupStart
    </td>
    
    <td valign="top" width="269">
      Tempo imediatamente antes de iniciar a resolução de nome do domínio.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      domainLookupEnd
    </td>
    
    <td valign="top" width="269">
      Tempo após finalizar a resolução de nome do domínio.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      connectStart
    </td>
    
    <td valign="top" width="269">
      Tempo imediatamente antes de iniciar a conexão com o servidor para solicitar o recurso.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      connectEnd
    </td>
    
    <td valign="top" width="269">
      Tempo em que a conexão com o servidor é finalizada.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      secureConnectionStart
    </td>
    
    <td valign="top" width="269">
      Para os browsers onde este atributo existe (o IE não o possui no momento), ele retorna o tempo em que foi iniciada uma conexão HTTPS.
    </td>
  </tr>
  
  <tr>
    <td rowspan="3" width="90">
      <p align="center">
        Servidor
      </p>
    </td>
    
    <td valign="top" width="222">
      requestStart
    </td>
    
    <td valign="top" width="269">
      Tempo imediatamente antes da requisição do documento ao servidor.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      responseStart
    </td>
    
    <td valign="top" width="269">
      Tempo imediatamente após o recebimento do primeiro byte de resposta do servidor.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      responseEnd
    </td>
    
    <td valign="top" width="269">
      Tempo após a finalização da resposta (recebimento do último byte) ou conexão com o servidor.
    </td>
  </tr>
  
  <tr>
    <td rowspan="7" width="90">
      <p align="center">
        Browser
      </p>
    </td>
    
    <td valign="top" width="222">
      domLoading
    </td>
    
    <td valign="top" width="269">
      Tempo em que o status do documento passa a ser “loading”.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      domInteractive
    </td>
    
    <td valign="top" width="269">
      Tempo em que o status do documento passa a ser “interactive” (DOM completamente interpretado pelo <i>parser</i> do <i>user agent</i>).
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      domContentLoadedEventStart
    </td>
    
    <td valign="top" width="269">
      Tempo em que o evento DOMContentLoaded é disparado no documento.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      domContentLoadedEventEnd
    </td>
    
    <td valign="top" width="269">
      Tempo após finalizar o evento DOMContentLoaded.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      domComplete
    </td>
    
    <td valign="top" width="269">
      Tempo em que o status do documento passa a ser “complete”. O status “complete” difere do “interactive” pois engloba a execução de scripts.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      loadEventStart
    </td>
    
    <td valign="top" width="269">
      Tempo em que inicia a execução do evento de <i>load</i> da página.
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="222">
      loadEventEnd
    </td>
    
    <td valign="top" width="269">
      Tempo em que finaliza a execução do evento de <i>load</i> da página.
    </td>
  </tr>
</table>

Conforme a developer [Kasia explica em um artigo de seu blog][7], os eventos de Rede envolvem tudo que acontecem antes do browser enviar a requisição do documento e pode ajudar a medir latência de rede; os eventos de Servidor são referentes aos tempos de requisição e resposta do documento, ajudando a medir quanto tempo o servidor leva para processar a página; por fim, os eventos do Browser ocorrem a partir do momento que o documento é criado até o momento em que o evento de _**onload**_ é disparado, auxiliando a medir de fato a performance **_client-side_**.

Na timeline abaixo, [retirada da documentação da API][8], é possível ver o fluxo de execução destes eventos.****

&nbsp;

<div style="width: 576px" class="wp-caption aligncenter">
  <a href="http://www.w3.org/TR/navigation-timing/timing-overview.png"><img class="   " alt="Modelo de Processo da Navigation Timing API" src="http://www.w3.org/TR/navigation-timing/timing-overview.png" width="566" height="338" /></a>
  
  <p class="wp-caption-text">
    Modelo de Processo da Navigation Timing API
  </p>
</div>

## Como utilizar todos estes dados para extrair as informações que nos interessam?

Depois de toda esta fundamentação teórica, chegamos de fato no ponto que nos interessa, o pulo do gato: como utilizar estes dados para obter as métricas de performance. Geralmente, a forma de obter estas informações se dá pelo cálculo da diferença entre alguns atributos.

Compilando alguns exemplos apresentados pelo [Sam Dutton do HTML5Rocks][9], [Colin Ihrig do SitePoint][10] e a [documentação de JS da Mozilla][11], temos as seguintes combinações (mas é possível obter muito mais):

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top" width="234">
      <b>Informação</b>
    </td>
    
    <td valign="top" width="342">
      <b>Cálculo</b>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo total de latência de rede
    </td>
    
    <td valign="top" width="342">
      responseEnd &#8211; fetchStart
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo de carregamento da página a partir do momento que a página é retornada do servidor
    </td>
    
    <td valign="top" width="342">
      loadEventEnd &#8211; responseEnd
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo total de carregamento da página
    </td>
    
    <td valign="top" width="342">
      loadEventEnd &#8211; navigationStart
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo de resposta a uma requisição feita ao servidor
    </td>
    
    <td valign="top" width="342">
      responseEnd &#8211; requestStart
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo de redirecionamento
    </td>
    
    <td valign="top" width="342">
      redirectEnd &#8211; redirectStart
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo de resolução do DNS
    </td>
    
    <td valign="top" width="342">
      domainLookupEnd &#8211; domainLookupStart
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo de conexão com o servidor
    </td>
    
    <td valign="top" width="342">
      connectEnd &#8211; connectStart
    </td>
  </tr>
</table>

Acrescento também alguns testes que fiz com outros cálculos:

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top" width="234">
      <b>Informação</b>
    </td>
    
    <td valign="top" width="342">
      <b>Cálculo</b>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo para renderizar o DOM (realizar a interpretação – <i>parser</i> – de todo o HTML)
    </td>
    
    <td valign="top" width="342">
      domInteractive &#8211; domLoading
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo total para carregar a página, incluindo a requisição de todos os arquivos externos, principalmente scripts
    </td>
    
    <td valign="top" width="342">
      domComplete &#8211; domLoading
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="234">
      Tempo de carregamento de scripts no evento <i>onload</i>
    </td>
    
    <td valign="top" width="342">
      loadEventEnd &#8211; loadEventStart
    </td>
  </tr>
</table>

## Exemplos

No site [Web Timing Demo][12] é possível ter uma prévia de como estes dados podem ser visualizados graficamente. Além disso, a aplicação mostra o valor de todas as propriedades da _**window.performance**_ para aquela página.

Outra aplicação mais completa é o [bookmarket desenvolvido pela Kasia][13], citada anteriormente neste artigo. Basta arrastá-lo para a barra de favoritos do browser e clicar nele em qualquer página que deseja analisar.

## Referências e mais recursos

Can I Use… **Navigation Timing API**. Disponível em: <http://caniuse.com/#feat=nav-timing>

Colin Ihrig. **Profiling Page Loads with the Navigation Timing API**. Disponível em: <http://www.sitepoint.com/profiling-page-loads-with-the-navigation-timing-api/>

Internet Explorer Developer Center. **Navigation timing (Windows)**. Disponível em: <http://msdn.microsoft.com/en-us/library/ie/hh673552(v=vs.85).aspx>

Kasia Drzyzga. Breaking Down OnLoad Event – Performance Bookmarklet. Disponível em: <http://66.7percentangel.com/2011/12/breaking-down-onload-event-performance-bookmarklet/>

Leigh Shevchik. **It’s All in the Timing: How to Use the Navigation Timing Specification to Improve Web Performance**. Disponível em: <http://blog.newrelic.com/2012/05/16/its-all-in-the-timing-how-to-use-the-navigation-timing-specification-to-improve-web-performance/>

Microsoft MSDN. **performanceTiming object**. Disponível em: <http://msdn.microsoft.com/en-us/library/ff975075>

Mozilla Developer Network. **Navigation Timing**. Disponível em: <https://developer.mozilla.org/en-US/docs/Navigation_timing>

Sam Dutton. **Measuring Page Load Speed with Navigation Timing**. Disponível em: <http://www.html5rocks.com/en/tutorials/webperformance/basics/>

W3C. **HTML5: A vocabulary and associated APIs for HTML and XHTML**. Disponível em: <http://www.w3.org/TR/html5/syntax.html>

W3C. **Navigation Timing**. Disponível em: <http://www.w3.org/TR/navigation-timing/>

&nbsp;

 [1]: http://tableless.com.br/performance-frontend-parte1/#.UTYrNTDFSSo
 [2]: http://tableless.com.br/como-perder-peso-no-browser/#.UT4quRzFSSo
 [3]: http://www.w3.org/TR/navigation-timing/
 [4]: https://developers.google.com/speed/pagespeed/insights
 [5]: http://www.webpagetest.org/
 [6]: http://caniuse.com/#feat=nav-timing
 [7]: http://66.7percentangel.com/2011/12/breaking-down-onload-event-performance-bookmarklet/
 [8]: http://www.w3.org/TR/navigation-timing/#processing-model
 [9]: http://www.html5rocks.com/en/tutorials/webperformance/basics/
 [10]: http://www.sitepoint.com/profiling-page-loads-with-the-navigation-timing-api/
 [11]: https://developer.mozilla.org/en-US/docs/Navigation_timing
 [12]: http://webtimingdemo.appspot.com/
 [13]: http://kaaes.github.com/timing/