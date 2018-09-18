---
title: Algoritmos de ordenação e o seu JavaScript
authors: Marcelo Galvão
type: post
date: 2017-09-04
excerpt: Insert sort, selection sort, quick sort, etc. Legal, mas onde esses algoritmos são aplicados de fato no seu JavaScript?
categories:
  - Javascript
  - Na Prática
image: https://i.imgur.com/sZptluM.jpg
---

<span style="display: block; text-align: center">
	<span style="display:inline-block; width: 280px;">
	![](https://cdn-images-1.medium.com/max/800/1*nOVvqQbsxxrbURDH_JeXoA.gif)
	</span>
	<br>
	*gif insertion sort — Wikipedia*
</span>

[Insert sort](https://pt.wikipedia.org/wiki/Insertion_sort), [selection
sort](https://pt.wikipedia.org/wiki/Selection_sort), [quick
sort](https://pt.wikipedia.org/wiki/Quicksort), etc. Legal, mas onde esses
algoritmos são aplicados de fato no seu JavaScript?

Enquanto estudava estrutura de dados e afins, me deparei com esses conceitos de
programação e meu questionamento ficou sem resposta. Eu queria ver de fato a
implementação de uma linguagem de programação usando esses conceitos, ué. haha

Esses dias precisei ordenar um array em JavaScript e me deparei com o método
[sort()](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
e fui estudá-lo. Afinal, como algumas coisas em JS, ele nem sempre funciona bem
como esperado #aiMeuJavascript .

### Sort()

Esse método classifica os valores como string e os ordena em ordem ascendente.
Ou seja, se seu array for de valores numéricos ele não terá a ordenação que você
deseja. Pois o valor será interpretado como uma string e aí sim ordenado.

    var ar = [40, 10, 101, 20];
    ar.sort();
    // [10, 101, 20, 40]

### Solução

    // passe uma função de comparação como parâmetro

    var ar = [40, 10, 101, 20];
    ar.sort( function(a, b){
       return a — b;
    });
    // [10, 20, 40, 101]
    
    /*
	Observe que isso também é útil para ordenar um array de objetos. Ordenando 
	com base em um valor numérico de um determinado atributo. (exe.: idade, peso).
	*/


### Por trás do Sort()

Durante o estudo resolvi observar os loops de comparação e percebi algo
semelhante a grandeza encontrada no insertion sort (nesse caso, 5x). Que não é o
melhor algoritmo, mas trabalha bem com pequenos vetores numéricos.

Graças ao mundo open source podemos dar uma olhada no código fonte de algumas
engines JavaScript utilizada nos navegadores, escritas em C/C++.

### V8

Olhando o código da engine JavaScript V8 — utilizada no Chrome — podemos
observar menções ao quick sort (linha 768), insertion sort (linha 734), entre
outros algoritmos e suas implementações :)

![](https://cdn-images-1.medium.com/max/800/1*A8Q5N7Pkc_rZ50aVCfDIGA.png)

[https://github.com/v8/v8/blob/fe598532ec1317e8b85343133be9fb708e07bd2e/src/js/array.js#L768](https://github.com/v8/v8/blob/fe598532ec1317e8b85343133be9fb708e07bd2e/src/js/array.js#L768)

E o seguinte comentário:

> For short (length <= 10) arrays, insertion sort is used for efficiency.

### WebKit

No WebKit podemos ver sua implementação em C++ para os tratamentos com array.

![](https://cdn-images-1.medium.com/max/800/1*73WlWhS26dVbLvek14_rSQ.png)

[https://trac.webkit.org/browser/trunk/Source/JavaScriptCore/runtime/JSArray.cpp?rev=138530#L972](https://trac.webkit.org/browser/trunk/Source/JavaScriptCore/runtime/JSArray.cpp?rev=138530#L972)

### SpiderMonkey

No SpiderMonkey, engine JavaScript utilizada no Firefox.

![](https://cdn-images-1.medium.com/max/800/1*Z5E8ALSb8mS4vgkQoGLl8g.png)

[https://hg.mozilla.org/mozilla-central/file/28be8df0deb7/js/src/jsarray.cpp](https://hg.mozilla.org/mozilla-central/file/28be8df0deb7/js/src/jsarray.cpp)

### C++

No código fonte do navegador, como esperado, muitas vezes simplesmente chama-se
a implementação do próprio C++, por exemplo o quick sort.

![](https://cdn-images-1.medium.com/max/800/1*4sdtKW2_XviENzCqvq4h7w.png)

[https://en.cppreference.com/w/cpp/algorithm/qsort](https://en.cppreference.com/w/cpp/algorithm/qsort)

### Discussão antiga

Quando pesquisava sobre o Firefox encontrei esse thread aberta a 14 anos atrás
(!) onde o pessoal discute sobre o assunto, inclusive o próprio **Brendan Eich,
**aparentemente ainda com cara de jovem 😛 <br>
[https://bugzilla.mozilla.org/show_bug.cgi?id=224128#c8](https://bugzilla.mozilla.org/show_bug.cgi?id=224128#c8)<br>
Na ocasião, ele explica porque usa quick sort.

![](https://cdn-images-1.medium.com/max/800/1*YDEXZUZkgosHA-r2cgzXow.png)

### Conclusão

Existem vários algoritmos de busca e ordenação. Cada um com sua importância,
particularidade e propósito. Seja para números, string, etc. É interessante ver
casos como o do V8, que faz um tratamento e usa o mais adequado a
necessidade. **Mas o mais interessante mesmo foi ver que eles realmente
estão lá :P**

*Ps.: Não entrei no detalhe das implementações em C++ porque não tenho
conhecimento na linguagem. Se você possui e tem algo a acrescentar, por favor,
sinta-se convidado!*
