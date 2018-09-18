---
title: 'Media queries simples com rupture'
authors: Guilherme Bayer
type: post
image: https://i.imgur.com/Wl1JzuY.png
date: 2017-07-07
excerpt: Torne o desenvolvimento do seu código Stylus mais divertido e produtivo conhecendo um pouco mais sobre o rupture, uma pequena lib para media queries.
categories:
  - Código
  - CSS
  - Pré-processadores
tags:
  - front-end
  - pre-processadores
  - Stylus
---

Hoje em dia, contamos com diversos frameworks, libs e utilitários para facilitar nosso desenvolvimento e também o tornando mais ágil. Nessa ideia surgiu o rupture, um utilitário portado para Stylus que promete tornar o uso de media queries mais simples, com sua sintaxe simplificada.

## Porque devo experimentar?
Antes de conhecer o rupture, eu tinha o trabalho de criar mixins para minhas media queries que nem sempre me satisfaziam, até que o conheci. Com uma documentação bacana, em poucos minutos já estava tendo uma excelente produtividade, então se você já usa Stylus, use o rupture que é sucesso.

## Mão na massa
Você pode encontrá-lo e instalá-lo seja com o [npm](https://www.npmjs.com/package/rupture) ou [yarn](https://yarnpkg.com/pt-BR/package/rupture).

```sh
npm install rupture --save-dev

yarn add rupture
```

A forma mais simples de rodarmos o rupture junto ao Stylus é:

```sh
stylus -u rupture -c arquivo.styl
```

## Scale
Trata-se de um conceito baseado em régua, onde você define seus breakpoints onde um intervalo pode ser representado apenas por uma letra, tornando seu uso bastante simples e também gerando uma padronização de breakpoints em todo seu código.

```styl
rupture.scale       =   0       768px       1024px
rupture.scale-names =      'm'         't'          'd'
```

Nessa especificação acima, nosso breakpoints de mobile poderiam ser utilizados apenas através da string "m" assim como os breakpoints de tablet utilizando o "t" em nossos mixins.

## Mixins
Irei mostrar alguns dos principais mixins do rupture, pelos menos os que mais utilizo no meu dia-a-dia.

```styl
+below(medida)
+above(medida)
+between(medida, medida)
```

Há também o grupo de mixins abaixo, que faz referência direta ao scale.

```styl
+mobile()
+table()
+desktop()
```

Abaixo mostro um pequeno exemplo de código utilizando mixins e as configurações de breakpoints do scale.

```styl
.button
  background $green
  padding 10px 25px
  display block
  
  +below('m')
    padding 15px 40px  
    
  +between('m', 'w')
    padding 15px 80px
```

Esse simples código acima irá gerar isso.

```css
.button {
  background: #02b875;
  padding: 10px 25px;
  display: block;
}

@media screen and (max-width: 768px) {
  .button {
    padding: 15px 40px;
  }
}

@media only screen and (min-width: 769px) and (max-width: 1023px) {
  .button {
    padding: 15px 80px;
  }
}
```

## Acho que é isso
A ideia era apenas mostrar algumas das facilidades que o rupture trás. Convido você a dar uma [olhadinha no repositório](https://github.com/jescalan/rupture) que lá você encontra muitos outros mixins e recursos interessantes.
