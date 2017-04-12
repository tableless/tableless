---
title: Utilizando navigator.language
author: Leonardo Lima
type: post
date: 2014-12-15
excerpt: |
  |
    Vamos entender como funciona o navigator.language, com um pouco de teoria e prática.
url: /utilizando-navigator-language/
categories:
  - JavaScript

---
Quando desenvolvemos um aplicativo web, normalmente desenvolvemos incluindo o trabalho de internacionalização. Mas não basta apenas criar arquivos para cada país, pois o aplicativo pode ser acessado por diversos países que você não contemplou. Pensando nesses problemas o Yahoo Presentation Technologies (YPT) e com a ajuda de [Andy Earnshaw][1] e [Norbert Lindenberg][2] criaram a biblioteca [Formatjs][3]. Vamos mostrar um pouco sobre essa biblioteca logo abaixo, com um exemplo bem simples:

<pre class="lang-javascript">var messages = {
   en: {
       GREETING: 'Hello {name}'
   },
   fr: {
       GREETING: 'Bonjour {name}'
   }
};
</pre>

## Qual o local language do usuário

A melhor forma de você servir um idioma para o usuário, é descobrindo o idioma que ele usa no browser. Geralmente o idioma do browser é igual ao idioma do sistema operacional, logo, é o idioma nativo do usuário ou o idioma que o usuário se sente mais confortável para usar. 

Então, vamos descobrir qual é esse idioma usado pelo usuário. Para tanto, precisamos utilizar um desses comandos `(navigator.language || navigator.browserLanguage)` para entregar o conteúdo no idioma correto. Para essa verificação, podemos utilizar vários métodos, um deles é fazendo com que o usuário clique em um botão e nesse momento rodamos o código que vai descobrir o idioma.

Um exemplo de como identificar o idioma do browser do usuário pode ser feito assim:

<pre class="lang-javascript">//variável que vai retornar uma string com language preferida do usuario
var lang = navigator.language ;
//verificamos o momento do click no botao
$("#lang").on('click',function () {
    //identificamos a language
    if(lang === 'en-US'){
        //apresentamos uma mensagem ao usuario
        alert("Your language is:"+lang);
    }
});
</pre>

## Parâmetros do navigator.language

A string “lang” representando as versões de linguagens, está definida em [RFC 4646][4].
  
Exemplos de códigos de linguagens validos inclui &#8220;en-US&#8221;, &#8220;fr&#8221;, &#8220;es-ES&#8221;, etc. 

## Maneiras de verificar o language

Podemos utilizar duas maneiras de identificação: uma retorna apenas a language que o usuário está utilizando no browser e o outro verifica alguns códigos de languages que são suportados.

Exemplos:

<pre class="lang-javascript">navigator.language  //"en-US"
navigator.languages //["en-US", "zh-CN", "ja-JP"]
</pre>

## Como seria na prática

Na prática quando o usuário for acessar o site, não será preciso selecionar o país de origem para entregarmos o conteúdo no seu idioma. Com todos os idiomas prontos, só vamos precisar criar um script que verifique qual idioma o browser está utilizando. 

## Analisando o código fonte

No código fonte abaixo, cada linha tem uma explicação: 

<pre class="lang-javascript">//esconder os formularios
$(".form").hide();
$(".form2").hide();

//ao clicar vamos descobrir o language
$("#lang").on('click',function () {

//variavel que vai retornar uma string com language preferida do usuario
var lang = navigator.language;    

//aqui realizamos uma identificação do language 
if(lang === 'en-US'){
//entregamos para o usuário o form correto
        alert("Your language is:"+lang);
        $(".form2").show('slow', function(){});        
    }

   //aqui realizamos uma identificação do language 
if(lang === 'pt-BR'){
     //entregamos para o usuário o form correto
        alert("Your language is:"+lang);
        $(".form").show('slow', function(){});        
    }    
});
</pre>

Link para o exemplo no [JSFiddle][5]

## Propriedades

A interface `NavigatorLanguage` não herda qualquer propriedade.
  
O [NavigatorLanguage.language][6] retorna uma [DOMString][7] representando o idioma de preferência do usuário, geralmente o idioma da interface do usuário do navegador. O valor null é devolvido quando este é desconhecido.

[NavigatorLanguage.languages][8]
  
Retorna um array de [DOMString][7] representando os idiomas conhecidos para o usuário, por ordem de preferência. 

## Referências

[NavigatorLanguage.languages][8]

[NavigatorLanguage][9]

## Browsers compatíveis (Desktop)

A tabela e a lista de browsers compativeis foi retirada do site [Developer Mozilla][10]. 

  * **Chrome**=> Sim. Returns the browser UI language, not the value of the Accept-Language [HTTP header][11].
  * **Firefox(Gecko)**=>1.0 (1.7 or earlier)
  
    Prior to Gecko 2.0 (Firefox 4 / Thunderbird 3.3 / SeaMonkey 2.1), this property&#8217;s value was also part of the user agent string, as reported by [navigator.userAgent][12].
  
    Starting in Gecko 5.0 (Firefox 5.0 / Thunderbird 5.0 / SeaMonkey 2.2), this property&#8217;s value is based on the value of the Accept-Language [HTTP header][11].
  * **Internet Explorer**=> Closest available (non-standard) properties are [userLanguage][13] and [browserLanguage][14]. IE11 provides navigator.language but it is unclear how many prior versions support it. Old versions are not available to me, at the moment.
  * **Opera**=> Sim.
  * **Safari**=>Sim.

## Browsers compatíveis (Mobile)

Essa é a lista dos browsers mobile que suportam o **navigator.language**: 

  * **Android**=>Sim.
  * **Firefox Mobile(Gecko)**=>1.0 (1.0)
  * **IE Mobile**=>Não suporta. Closest available (non-standard) properties are [userLanguage][13] and [browserLanguage.][14]
  * **Opera Mobile**=>Sim.
  * **Safari Mobile**=>Sim.

## Conclusão

Todo o conteúdo utilizado foi retirado do site developer.mozilla.org, pois lá tem bastante material sobre o assunto. Você pode utilizar o navigator.language por enquanto nos dois principais browsers Firefox e Chrome, mas isso não impede você de testar nos outros também. Eu espero que este material sirva como um auxílio para encorajar outros web developer a utilizarem mais o navigator.language.

 [1]: https://github.com/andyearnshaw
 [2]: http://norbertlindenberg.com
 [3]: http://formatjs.io/
 [4]: http://tools.ietf.org/html/rfc4646
 [5]: http://jsfiddle.net/leonardo403/f9f70vgh/10/
 [6]: https://developer.mozilla.org/en-US/docs/Web/API/NavigatorLanguage.language
 [7]: https://developer.mozilla.org/en-US/docs/Web/API/DOMString
 [8]: https://developer.mozilla.org/en-US/docs/Web/API/NavigatorLanguage.languages
 [9]: https://developer.mozilla.org/en-US/docs/Web/API/NavigatorLanguage
 [10]: http://developer.mozilla.org
 [11]: https://developer.mozilla.org/en/HTTP/Headers
 [12]: https://developer.mozilla.org/en-US/docs/Web/API/window.navigator.userAgent
 [13]: http://msdn.microsoft.com/en-us/library/ie/ms534713.aspx
 [14]: http://msdn.microsoft.com/en-us/library/ie/ms533542.aspx