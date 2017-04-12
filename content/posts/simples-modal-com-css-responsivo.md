---
title: Simples modal com CSS responsivo
author: Palloi Hofmann
type: post
date: 2015-01-21
excerpt: Continuando com os artigos, vamos utilizar novamente os seletores de css para exibir nosso modal.
url: /simples-modal-com-css-responsivo/
categories:
  - Código
  - CSS
  - CSS3
  - HTML
  - Responsive Web Design (RWD)
  - Técnicas e Práticas
tags:
  - CSS3
  - html
  - modal
  - responsive
  - tecnicas

---
Continuando com os artigos, vamos utilizar novamente os seletores de css para exibir nosso modal.

Se você chegou aqui e não viu os posts anteriores, para conhecer a estrutura inicial acesse os links:
  
<a href="http://tableless.com.br/header-responsivo-somente-com-css/" target="_blank">Header responsivo somente com css</a>
  
<a href="http://tableless.com.br/destaques-responsivos/" target="_blank">Destaques responsivos</a>

De uma maneira bem simples veja como preparar seu html e css.

## O LABEL

Com os destaques responsivos, vamos adicionar abaixo da descrição um label que terá a função de marcar o checkbox e por css iremos exibir o modal.

<pre class="lang-html">&lt;div class="highlights"&gt;
&nbsp; &lt;input type="radio" id="radio-img1" name="highlights" checked="checked" /&gt;
&nbsp; &lt;div class="highlights-item"&gt;
&nbsp; &nbsp; &lt;img src="assets/images/chaves.jpg" /&gt;
&nbsp; &nbsp; &lt;p&gt;Olha o Chaves sorrindo&lt;/p&gt;
&nbsp; &nbsp; &lt;label class="highlights-button" for="modal-chaves"&gt;Ver fotos do Chaves&lt;/label&gt;
&nbsp; &lt;/div&gt;
&nbsp;&nbsp;
&nbsp; ...
&lt;/div&gt;</pre>

## O CSS DO BOTÃO

Vamos formatar o label para ser o nosso botão, lembrando que sempre precisamos usar a propriedade &#8220;for&#8221; para marcar o checkbox.

<pre class="lang-css">.highlights-button {
  display: inline-block;
  padding: 10px 15px 8px;
  cursor: pointer;
  border-radius: 3px;
  border: 1px solid #ccc;
  background-color: #ececec;
  -webkit-transition: background-color 300ms ease-in-out, border-color 300ms ease-in-out;
  transition: background-color 300ms ease-in-out, border-color 300ms ease-in-out;
}
</pre>

Adicionando o hover:

<pre class="lang-css">.highlights-button:hover {
  border: 1px solid #ececec;
  background-color: #ccc;
}
</pre>

## O HTML DO MODAL

Para um melhor resultado vamos adicionar html antes do &#8220;body&#8221;, mas se quiser aplicar dentro da section sem problemas. Ao aplicar &#8220;position: fixed&#8221; o elemento ignora o &#8220;position&#8221; do pai e respeita o tamanho da janela.

<pre class="lang-html">&lt;input type="checkbox" id="modal_chaves" /&gt;
&lt;div class="modal"&gt;
  &lt;div class="modal-content"&gt;
    &lt;h4&gt;Foto Grande do Chaves&lt;/h4&gt;
    &lt;img src="assets/images/chaves-fotos-raras-4.jpg" /&gt;
  &lt;/div&gt;
  &lt;label class="modal-close" for="modal_chaves"&gt;&lt;/label&gt;
&lt;/div&gt;</pre>

No resultado final poderá ver as modais aplicados dentro e fora da section.

## O CSS DO MODAL

<pre class="lang-css">.modal {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10;
  opacity: 0;
  visibility: hidden;
  -webkit-transition: all 0.5s 0.5s ease-in-out;
  transition: all 0.5s 0.5s ease-in-out;
}

.modal-content {
  padding: 10px;
  max-width: 600px;
  min-width: 360px;
  max-height: 85%;
  overflow: auto;
  position: absolute;
  top: 5%;
  left: 50%;
  z-index: 2;
  opacity: 0;
  border-radius: 3px;
  background: #fff;
  -webkit-transform: translate(-50%, 0);
  -ms-transform: translate(-50%, 0);
  transform: translate(-50%, 0);
  -webkit-transition: all 0.5s ease-in-out;
  transition: all 0.5s ease-in-out;
}

.modal-content img {
  display: block;
  width: 100%;
  margin: 10px 0 0;
}

.modal-content p {
  padding-top: 10px;
  text-align: justify;
}</pre>

Agora formatando a cortina e o botão de fechar que é o label que colocamos depois do conteúdo do modal.

<pre class="lang-css">.modal-close {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: rgba(0,0,0,0.5);
}

.modal-close:after {
  content: "X";
  float: right;
  margin: 5px 5px 0 0;
  width: 30px;
  height: 30px;
  position: relative;
  z-index: 3;
  text-align: center;
  line-height: 30px;
  cursor: pointer;
  background-color: rgba(255,255,255,0.8);
  border-radius: 20px;
  box-shadow: 0 0 3px #000;
}</pre>

Agora vamos esconder o checkbox e fazer nosso modal aparecer com &#8220;:checked&#8221; do css3.
  
Um pequeno truque ao usar fixed e 50% para top, faz que o checkbox sempre fique no meio da janela evitando rolar a página ao ser selecionado. Se realizar um teste usando o inspect removendo o top: 50% e clicar no terceiro botão irá simular a rolagem.

<pre class="lang-css">input[id*="modal_"] {
  position: fixed;
  left: -9999px;
  top: 50%;
  opacity: 0;
}

input[id*="modal_"]:checked + div.modal {
  opacity: 1;
  visibility: visible;
  -webkit-transition-delay: 0s;
  -ms-transition-delay: 0s;
  transition-delay: 0s;
}

input[id*="modal_"]:checked + div.modal .modal-content {
  opacity: 1;
  -webkit-transform: translate(-50%, 0);
  -ms-transform: translate(-50%, 0);
  transform: translate(-50%, 0);
  -webkit-transition-delay: 0.5s;
  -ms-transition-delay: 0.5s;
  transition-delay: 0.5s;
}</pre>

Praticamente nosso css já está responsivo, mas vamos adaptar para resoluções menores que 768px.

<pre class="lang-css">@media screen and (max-width: 767px) {
  .modal-content {
    padding: 10px 5%;
    min-width: 88%;
  }
}</pre>

## PRONTO

Temos um modal responsivo e seu conteúdo pode ser adaptado para qualquer tamanho, desde que faça isso acontecer.

<a title="Veja como ficou o resultado final" href="http://palloi.github.io/responsive-header-only-css/responsive-modal.html" target="_blank">Veja como ficou o resultado final</a>.

<a title="código completo no github" href="https://github.com/palloi/responsive-header-only-css" target="_blank">Veja o código completo no github</a>.

## CONCLUINDO

Podemos aplicar de várias formas e uma delas é usando o &#8220;:target&#8221;, porém quando temos uma tela muito grande e ao fechar precisamos adicionar o &#8220;#&#8221;, isso faz que a página role para o topo.
  
Agora com sua imaginação pode fazer diversas animações para exibir seu modal. 

Espero ter ajudado com a criação de modais só com css.

Obrigado