+++
authors = "Julio Carneiro"
categories = ["css", "javascript"]
date = "2018-07-30T08:00:00+00:00"
excerpt = "Como usar o Sass junto ao create-react-app, sem eject e apenas instalando a gem e fazendo rodar no nosso package.json."
image = "https://i.imgur.com/3mUSxrp.jpg"
publishdate = "2018-07-30T08:00:00+00:00"
tags = ["sass", "reactjs", "css"]
title = "Usando Sass com create-react-app (sem eject)"
type = "post"

+++
Em um tweet de abril do Dan Abramov, ele diz que o CRA (vou chamar create-react-app deste jeito para facilitar) está trabalhando para adicionar suporte nativo ao Sass em um futuro próximo. Bora ficar de olho porque depois deste lançamento o método ensinado aqui ficará obsoleto.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Opt-in Sass support without ejecting coming to Create React App <a href="https://t.co/HF4sVgSh3w">https://t.co/HF4sVgSh3w</a></p>&mdash; Dan Abramov (@dan_abramov) <a href="https://twitter.com/dan_abramov/status/985249038181289985?ref_src=twsrc%5Etfw">April 14, 2018</a></blockquote>

<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

O primeiro passo é instalar o Ruby na sua máquina. O Sass é uma dependência dele. O Ruby vem instalado por padrão no Mac e em algumas distribuições do Linux. Se você estiver usando Windows, pode usar o [Ruby Installer](https://rubyinstaller.org/) . Para instalar o Sass você pode executar o comando`gem install sass `no seu terminal.

### Não quero instalar o Ruby

Não é necessário instalar o Ruby para executar o Sass. Basta instalar o Sass globalmente com o npm(`npm i -g`) e vai funcionar tudo certinho conforme estamos ensinando. O método que estou te ensinando abaixo é o sugerido nos [docs](https://sass-lang.com/documentation/file.SASS_REFERENCE.html) do [Sass](https://sass-lang.com/documentation/file.SASS_REFERENCE.html) .

Após feito isso teremos o Sass instalado em nossa máquina, podemos então começar configurar nosso projeto react, creiar diretórios necessários e editar o package.json:

    # create-react-app projeto
    # cd projeto

**Alterações na estrutura do arquivo:**

    # nova pasta: src / styles 
    # nova pasta: src / styles / css 
    # nova pasta: src / styles / scss 
    # renomear / mover index.css: src / styles / scss / index.scss 
    # renomear / mover App.css: src / styles / scss / App.scss

Nossa `/src`deve ficar assim:

![](https://cdn-images-1.medium.com/max/800/1\*rkJxT61tRLhybm8DkcBK5w.png "estrutura diretórios no src")

Em seguida, atualizaremos nosso `src/index.js` para importar o`index.css`do local correto. Precisamos mudar a linha `import './index.css'`para `import './styles/css/index.css'`Nosso `index.js` deve ser semelhante a:

    import React from 'react';
    import ReactDOM from 'react-dom';
    import './styles/css/index.css';
    import App from './App';
    import registerServiceWorker from './registerServiceWorker';
    ReactDOM.render(<App />, document.getElementById('root'));
    registerServiceWorker();

Também podemos remover a seguinte linha de import de css no arquivo App.js:

    import ‘./App.css'

Como ainda não temos um arquivo .css na pasta em que criamos vai dar erro, mas calma que vamos chegar lá.

Vamos atualizar o `index.scss`. Por padrão, ele tem um pequeno bloco de `body,` eu prefiro mover isso para o `App.scs`, mas você pode criar um `Body.scss`e movê-lo para lá, caso queira. Esses são os estilos padrão fornecidos pelo CRA, e você provavelmente vai sobrescrever mais tarde. Nosso `index.scss` só precisa importar nossos outros arquivos Sass. Depois de mover o bloco de estilo para outro arquivo, nosso `index.scss` deve ter apenas `@import ‘App’`e `@import 'Body'`se você optou por criar esse arquivo.

Agora vamos usar o `watch` do Sass para ficar de olho em nossa pasta scss e compilar nossas folhas de estilo na pasta css conforme fazemos a edição. Para fazer isso, adicionaremos um script ao `package.json`.

    "sass" : "sass --watch src/styles/scss:src/styles/css"

O comando diz ao Sass para observar a pasta do scss e compilar a saída para a pasta do css. Agora nós simplesmente abrimos uma segunda aba no nosso terminal e rodamos o comando `yarn run sass`assim começamos a assistir / compilar nossos scss para o css.

Como a compilação do Sass é totalmente independente do ecosistema do CRA, ele não consegue identificar que estamos escrevendo o scss então, nao vai afetar o desenvolvimento do app. As vezes podemos esquecer de compilar nosso Sass então eu dei uma modificada no script de Build também, assim ele fará uma compilação única quando eu for rodar o npm run build.

`_"sass:build"_: "sass — update src/styles/scss:src/styles/css",`

Depois só atualizar o `build` para:  
`_"build"_: "yarn sass:build && react-scripts build",`

Isso vai fazer com que você tenha menos uma coisa pra se preocupar. Suas folhas de estilo serão automaticamente compiladas antes que o build ocorra.

Um último passo que eu recomendaria é adicionar o `.sass-cache`ao seu `.gitignore`. O Sass usa arquivos de cache locais para rastrear suas mudanças, e você provavelmente não os quer em seu repo.

É isso! Se você executar o comando`yarn start`, você deve ver a tela padrão do CRA mostrando nosso css como deveria ser mostrado. Se você quiser verificar novamente se seus arquivos Sass estão sendo compilados, não esqueça de executar `yarn run sass`e adicionar um `background-color`ao body.

Este post foi baseado no artigo do [Jeff Duke](https://hackernoon.com/@Jeff_Duke_io?source=post_header_lockup) para o hackernoon. Espero que tenham curtido, caso encontre uma solução melhor para fazer a mesma coisa vou dar um update neste post para que tenhamos um conteúdo sempre atualizado.