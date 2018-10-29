---
title: CSS3 – Sombras em textos e elementos
authors: Diego Eis
type: post
date: 2011-06-16
excerpt: Sombras em elementos e textos. O CSS3 nos trouxe essa possibilidade. Saiba como funciona as propriedades text-shadow e box-shadow.
url: /css3-sombras-em-textos-e-elementos/
categories:
  - CSS
  - CSS3
  - HTML
tags:
  - 2011
  - CSS3
  - desenvolvimento web
  - html5
  - Na Prática
  - tecnicascss

---
Uma das vantagens mais interessantes que o CSS3 nos dá é a possibilidade de cada vez menos abrirmos o Photoshop. Não precisamos mais abrir o Photoshop para criar bordas arredondadas, gradientes e agora até mesmo sombras. Agora temos a possibilidade de inserirmos sombras em textos e em elementos. As propriedades tem nomes diferentes mas a mesma sintaxe. Veja abaixo:

[cc lang=&#8221;html&#8221;]
  
p {
      
text-shadow: 5px 5px 5px rbga(0,0,0,0.5);
      
box-shadow: 5px 5px 5px rgba(0,0,0,0.5);
  
}
  
[/cc]

Esqueça agora o nome da propriedade e entenda melhor seus parâmetros: colocamos 3 números e por último a cor. Na cor utilizamos RGBA para termos controle sobre o canal de transparência da cor. Você pode ver um [artigo sobre RGBA neste link][1].

Agora vamos entender o significado dos números: os dois primeiros números se referem a posição da sombra: o primeiro número é referente a posição vertical começando pelo topo e o segundo número é referente a posição horizontal, começando pela esquerda. 

O terceiro número se refere ao Blur. Sua sombra pode ser rígida ou &#8220;esfumaçada&#8221;. Isso depende do design que você criou o pegou para implementar. Você controla a rigidez da sombra por este número. 

Praticamente todo o controle de sombra que você tem no Illustrator, você agora tem com o CSS3.

Na minha opinião pessoal há ainda algumas features que poderiam ser incluídas nessa especificação como por exemplo a possibilidade de colocarmos sombras apenas nos lados que quisermos e termos o controle individual das sombras. Mais ou menos como temos na propriedade border, onde podemos inserir borda apenas de um lado do objeto e podemos controlar as características dessa borda.

Você [pode ver um exemplo em nosso Github][2]. Lembre-se que codificar é de graça&#8230; Faça um teste agora, antes de deixar este post de lado. 😉

---

Apoio: Com o [NET Combo](https://www.telefonenet.com.br/net/net-combo/) você pode obter muitos descontos ao invés de contratar os serviços de forma isolada. Acesse e conheça todos os planos e saiba os descontos que pode obter com a operadora!

---


 [1]: https://tableless.com.br/css3-breve-introducao-a-rgba "Entenda como funciona o RGBA"
 [2]: https://tableless.github.com/exemplos/css3-shadow.html "Exemplo de sombra com CSS3"