---
title: 'Experimentando flexbox hoje: topo alinhado sem muito esforço'
authors: Alan Marcos
type: post
date: 2015-11-25
excerpt: Com poucas linhas de código é possível posicionar elementos facilmente para páginas responsivas
url: /experimentando-flexbox-hoje-topo-alinhado-sem-muito-esforco/
categories:
  - CSS3
tags:
  - bootstrap
  - CSS3
  - flexbox

---
Como muitos desenvolvedores web, gosto de experimentar _features_ novas ocasionalmente. Uma das coisas que costumava fazer em todo projeto é deixar o menu alinhado horizontalmente à logo, como no exemplo abaixo:

[<img class="alignnone wp-image-52030 size-full" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2015/11/print.png" alt="Exemplo de topo com logo e links" width="1175" height="78" />][1]

Só que nunca foi tão fácil assim: para deixar eles alinhados verticalmente, precisamos adicionar `margin` ou `padding` à logo ou ao menu. E com a popularização do site responsivo, os tamanhos dessas propriedades não eram os únicos problemas: tanto a logo quanto o espaçamento entre os links poderiam diminuir ou aumentar conforme o tamanho da tela e daria um grande trabalho (criar vários _media queries_ com vários ajustes em cada resolução) para conseguirmos alinhar em todos os dispositivos.

É aí que entra o **_flexbox_**. Se você usa <a href="https://getbootstrap.com/" target="_blank">Bootstrap</a>, sua sintaxe do topo deve ser similar à esta:

{{< codepen 
  hash="xwmWOV"
  user="alanmarcos"
  author="Alan Marcos"
>}}

### Solução

Costumo criar uma classe para esse tipo de alinhamento:

<pre class="lang-css">.row-centered {
   display: flex;
   align-items: center;
}
</pre>

E com só duas linhas de código, temos um topo alinhado horizontalmente sem muito esforço!

{{< codepen 
  hash="epbMgY"
  user="alanmarcos"
  author="Alan Marcos"
>}}

### Compatibilidade

A <a href="https://caniuse.com/flexbox" target="_blank">compatibilidade do flexbox</a> hoje já é bem alta, ou seja, você também pode usar nos seus projetos, lembrando que você pode utilizar o <a href="https://modernizr.com/" target="_blank">Modernizr</a> para detectar essa _feature_ e usar um _fallback_ quando necessário.

### Conclusão

Pode parecer um problema pequeno, mas estas duas linhas acabaram resolvendo muitos problemas nos meus projetos mais recentes. Como o _flexbox_ ainda não é uma _feature_ &#8220;100% _bulletproof&#8221;_, recomendo usar em pequenos ajustes como o deste post.

 [1]: https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2015/11/print.png