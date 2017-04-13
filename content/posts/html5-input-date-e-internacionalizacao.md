---
title: Campo input date do HTML5 e internacionalização
author: rogerio dias moreira
type: post
date: 2015-09-30
url: /html5-input-date-e-internacionalizacao/
categories:
  - HTML5
  - JavaScript

---
Alguns navegadores como Chrome, Edge e Safari já começaram a suportar o elemento <input type=&#8221;date&#8221;> com sua nova propriedade valueAsDate. Ao invés de utilizar bibliotecas para exibição de calendário e até mesmo para tratamento de datas com internacionalização, sugiro adotar estes novos recursos HTML5 com pequenos fallbacks para navegadores que não suportam.

<h3 style="text-align: left;">
  Elemento <input type=&#8221;date&#8221;>
</h3>

Este novo elemento dispensa apresentação. Sua grande vantagem é a excelente usabilidade e internacionalização automática. Veja como fica a apresentação deste elemento no Android 5:

[<img class="  wp-image-50884 aligncenter" src="http://tableless.com.br/uploads/2015/08/inputdateandroid.png" alt="inputdateandroid" width="198" height="352" />][1]

<h3 style="text-align: left;">
  <strong>Propriedade valueAsDate:</strong>
</h3>

Esta propriedade é a grande sacada para não termos que fazer o parse manual do texto digitado para convertê-lo para objeto Date. Caso o texto digitado ou selecionado através do calendário seja uma data válida, esta propriedade irá retornar a data num objeto e caso o texto não seja uma data a propriedade irá retornar o valor null.

Está fácil demais, é só usar o elemento input com tipo Date e obter ou setar o valor da data pela propriedade valueAsDate. Nem preciso me preocupar com internacionalização, que já é oferecida pelo próprio navegador compatível com ECMAScript Internationalization API(ECMA 402)&#8230; é quase isso&#8230; &#8220;Rapadura é doce mas não é mole&#8221; por dois motivos:

Motivo 1) O objeto Date do JavaScript pode representar datas tanto no formato GMT quanto UTC;

Motivo 2) ECMA 402 é bem recente sendo suportada navegadores superiores a &#8220;Chome 24, Firefox 29, IE 11, Opera 15&#8221; ;

Ambos os problemas podem ser solucionados com um pequeno entendimento de como o objeto Date trabalha, assim como pequenos fallbacks para navegadores que não suportam ECMA 402.

<h3 style="text-align: left;">
  Date &#8211; GMT e UTC
</h3>

Quando executamos a operação new Date() ou trabalhamos com serialização e desserialização (JSON.parse() e JSON.stringify()), o padrão é GMT (com timezone). Quando usamos o método Date.UTC() conseguimos construir um objeto no padrão UTC (sem timezone). Então qual é a encrenca? Vamos usar tudo com timezone (inclusive no banco para não dar zica) e esqueço que existe este tal de método Date.UTC(). O problema, não consegui entender o motivo ainda, é que quando obtenho o valor do objeto valueAsDate ele vem no formato UTC (karaka véi!&#8230;.). O modo mais simples para tratar isso é continuar setando a propriedade valueAsDate com Date GMT, e ao recuperar o valor, construir um novo objeto Date para que ele esteja no formato GMT.

<pre>Ex: 
dataGMT = new Date(dataUTC.getFullYear(),dataUTC.getMonth(),dataUTC.getDate())</pre>

Criei uma pequena demo com código fonte completo demonstrando esta operação em: <a href="http://codepen.io/rogeriodegoiania/pen/OVGWry" target="_blank">http://codepen.io/rogeriodegoiania/pen/OVGWry</a>

<h3 style="text-align: left;">
  Método toLocaleDateString()
</h3>

Este método faz mágica: ele consegue formatar uma data no formato local (Internacionalização)

<pre>console.log(new Date().toLocaleDateString())</pre>

Para navegadores que não suportam este método podemos criar este pequeno fallback

<pre>var isDateInvert = (function(){
  var lang = window.navigator.userLanguage || window.navigator.language;
  if (lang.substring(0,2) === "en"){
    return true;
  }
  else{
    return false;
  }
})();
 
if (Date.prototype.toLocaleDateString === undefined){
  Date.prototype.toLocaleDateString = function(){
    if (isDateInvert){
      return (this.getUTCMonth() + 1) + "/" + this.getUTCDate() + "/" + this.getFullYear();
    }
    else{
      return this.getUTCDate() + "/" + (this.getUTCMonth() + 1) + "/" + this.getFullYear();
    }
  }
}
 
if (Date.prototype.toLocaleString === undefined){
  Date.prototype.toLocaleString = function(){
    return this;
  }
}</pre>

<pre style="text-align: center;"></pre>

<h3 style="text-align: left;">
  <strong>Propriedade valueAsDate com defineProperty:</strong>
</h3>

Para navegadores que não suportam a propriedade valueAsDate podemos criar um pequeno fallback através do método defineProperty suportado até pelo IE8. Para saber mais veja: <https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty>

&nbsp;

<pre>var dataProperty = {
  set : function (value) {
    var dia, mes, ano;
    if (value){
      dia = value.getDate().toString();
      if (dia.length === 1){
        dia = "0" + dia;
      }
      mes = (value.getMonth() + 1).toString();
      if (mes.length === 1){
        mes = "0" + mes;
      }
      ano = value.getFullYear().toString();</pre>

<pre>if (isDateInvert){
        this.value = mes + "/" + dia + "/" + ano;
      }
      else{
        this.value = dia + "/" + mes + "/" + ano;
      }
    }
    else{
      this.value = "";
    }
  },
  get : function () {
    var valueV;
    var valueTimeStamp;
    var dia, mes, ano;
    try{
      valueV = this.value.trim().split("/");
      if(valueV.length === 3){
        if (isDateInvert){
          dia = valueV[1];
          mes = valueV[0];
          ano = valueV[2]; 
        }
        else{
          dia = valueV[0];
          mes = valueV[1];
          ano = valueV[2];
        }
 
        if (dia.length === 1){
          dia = "0" + dia;
        }
        if (mes.length === 1){
          mes = "0" + mes;
        }
        valueTimeStamp = Date.parse(ano + '-' + mes + '-' + dia);
        if (isNaN(valueTimeStamp)){
          return null;
        }
        else{
          return new Date(parseInt(ano), (parseInt(mes) - 1), parseInt(dia));
        }
      }
      else{
        return null;
      }
    }
    catch(err){
      return null;
    }
  }
}
 
if (HTMLInputElement.prototype.valueAsDate === undefined){
  Object.defineProperty(HTMLInputElement.prototype, 'valueAsDate', dataProperty);
}</pre>

Uma última atenção a ser tomada é em relação ao método Date.parse(). Dependendo do navegador, se o dia ou o mês não estiver no formato com duas casas o parse não é feito.

Acredito que já seja possível utilizar os novos recursos da **especificação** de internacionalização HTML5 em alguns projetos, com pequenos fallbacks, ao invés de utilizar bibliotecas específicas de internacionalização, como globalize.js e moment.js.

 [1]: http://tableless.com.br/uploads/2015/08/inputdateandroid.png