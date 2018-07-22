---
title: 'webpack Code Splitting: separando seus módulos para uma performance incrível'
authors: William Martins
type: post
date: 2018-04-30
excerpt: 'Aprenda como podemos utilizar o webpack para melhorar o carregamento
de aplicações e melhorando a experiência dos usuários'
image: https://images.unsplash.com/photo-1505739679850-7adc7776516b?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=406ab6486b411f24df33813b08c4b4cd&auto=format&fit=crop&w=1350&q=80
categories:
    - Browsers
    - Javascript
    - Na prática
    - Ferramentas
tags:
    - Performance
    - webpack
---

O webpack é uma ferramenta incrível. Com ela podemos focar em escrever o código
"de negócio" e não nos preocuparmos muito com a configuração dos *builds*, nos
permitindo focar no que é importante. Adicionalmente, quando necessário, podemos
personalizá-lo de acordo com nossas necessidades.

Uma dessas personalizações nos permite melhorarmos o carregamento em geral da
aplicação, simplesmente dividindo o código. Alguns aspectos que devemos cuidar e
que podemos fazer facilmente com o webpack são:

* Divisão de código, onde o usuário só precisa carregar o código que
  potencialmente será executado (por exemplo: não faz sentido o usuário carregar
  a *feature* `X` sendo que ele somente utiliza a *feature* `Y`)
* Organização de módulos *common/vendor*, que são utilizados de forma
  compartilhada na aplicação
* Cache de JavaScript que "muda pouco". Por exemplo, não é necessário
  fazer o usuário carregar o `React` inteiro novamente quando for feita uma
  alteração no código da aplicação
* Carregamento de múltiplos arquivos em paralelo, de forma a usufruir o máximo
  da rede e evitar deixar o usuário esperando

Os processos de minificação de código e compressão também ajudam na performance.
Junto com a divisão de código, podemos dar uma experiência melhor no
carregamento da aplicação para nossos usuários.

**Importante:** estaremos utilizando o webpack na versão `4.6.0` para este
artigo. As versões das *libraries* são irrelevantes nesse caso.

## Conceitos Básicos

Para esse artigo, precisamos entender alguns conceitos básicos, de forma a nos
familirizarmos com a nomenclatura utilizada daqui pra frente.

### *Bundle*

É o código "produzido" da nossa aplicação. Este código conterá os arquivos que
foram interpretados e, potencialmente, transformados pelo webpack. Uma aplicação
pode ter mais de um *bundle*.

### *Library*

Algum módulo externo utilizado na aplicação, normalmente instalado via um
*package manager* (`npm`, `yarn`, etc.). Exemplos: `moment`, `lodash`.

### *Entry*

É o arquivo que é informado ao webpack como "ponto de entrada" da aplicação. Na
prática, o webpack "olha" para esse arquivo para resolver toda a árvore de
dependências, realizando o carregamento e a compilação delas.

### *Build*

É a execução do processo de transformação.

## Aplicação Prática

Vamos para um cenário prático de forma a ilustrar como podemos explorar a
funcionalidade de `Code Splitting` do webpack. Imagine uma aplicação de
agendamento de viagens, onde temos dois perfis de usuário:

1) Funcionário: pode agendar viagens para os clientes. Nesse agendamento, é
feito um cálculo de datas utilizando a *library*
[`moment`](https://www.npmjs.com/package/moment).

2) Administrador: acompanha detalhes das viagens agendadas em um *dashboard*.
Esse dashboard utiliza a *library* [`d3`](https://www.npmjs.com/package/d3) para
exibir belos gráficos.

**Ambos** utilizam a *library* [`lodash`](https://www.npmjs.com/package/lodash)
para terem algumas funções auxiliares.

Na prática, o funcionário **nunca** precisará carregar a *library* `d3`, assim
como o administrador **nunca** precisará carregar a *library* `moment`.

### Estrutura do Projeto

```
.
├── package.json
├── package-lock.json
├── src
│   └── scripts
│       ├── administrador.js
│       ├── funcionario.js
│       └── index.js
└── webpack.config.js
```

### Conteúdo dos Arquivos

#### `funcionario.js`

```javascript
const lodash = require('lodash');
const moment = require('moment');

module.exports = () => {
    console.log('Utilizando lodash e moment para calcular datas', lodash, moment);
};
```

#### `administrador.js`

```javascript
const lodash = require('lodash');
const d3 = require('d3');

module.exports = () => {
    console.log('Montando o dashboard com lodash e d3', lodash, d3);
};
```

#### `index.js`

```javascript
const funcionario = require('./funcionario');
const administrador = require('./administrador');

funcionario();
administrador();
```

#### `webpack.config.js`

**Importante:** a propriedade `optimization.splitChunks` vem com um valor
default, porém, para fins de demonstração, ela será desabilitada por padrão,
sendo habilitada posteriormente.

```javascript
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');

const path = require('path');

module.exports = {
    context: path.resolve(__dirname, 'src'),

    mode: 'production',

    entry: './scripts/index.js',

    output: {
        filename: '[name].[chunkhash].js',
    },

    plugins: [
        new HtmlWebpackPlugin(),
    ],

    optimization: {
        // Deixaremos false por enquanto para propósitos de demonstração
        splitChunks: false,
    },
};
```

### Executando o Build

Ao executarmos esse *build*, podemos ver o que está acontecendo, além de
recebermos um *hint* do webpack. Vejamos:

```
Hash: ce292e499aa9d76225aa
Version: webpack 4.6.0
Time: 32007ms
Built at: 2018-04-30 16:59:34
                       Asset       Size  Chunks                    Chunk Names
main.c5d5bb71748040f842c8.js    537 KiB       0  [emitted]  [big]  main
                  index.html  201 bytes          [emitted]
Entrypoint main [big] = main.c5d5bb71748040f842c8.js
[126] ./scripts/administrador.js 168 bytes {0} [built]
[127] ./scripts/funcionario.js 189 bytes {0} [built]
[128] ../node_modules/d3/index.js + 502 modules 518 KiB {0} [built]
      |    503 modules
[129] ../node_modules/moment/locale sync ^\.\/.*$ 2.91 KiB {0} [optional] [built]
[131] ./scripts/index.js 449 bytes {0} [built]
    + 127 hidden modules

WARNING in asset size limit: The following asset(s) exceed the recommended size limit (244 KiB).
This can impact web performance.
Assets:
  main.c5d5bb71748040f842c8.js (537 KiB)

WARNING in entrypoint size limit: The following entrypoint(s) combined asset size exceeds the recommended limit (244 KiB). This can impact web performance.
Entrypoints:
  main (537 KiB)
      main.c5d5bb71748040f842c8.js


WARNING in webpack performance recommendations:
You can limit the size of your bundles by using import() or require.ensure to lazy load some parts of your application.
For more info visit https://webpack.js.org/guides/code-splitting/
Child html-webpack-plugin for "index.html":
     1 asset
    Entrypoint undefined = index.html
       4 modules
```

![Resultado do build sem nenhuma otimização](https://i.imgur.com/PJ2lpvb.jpg)

Podemos ver que o arquivo gerado `main.js` está com um tamanho considerável (537
KiB). O que aconteceu aqui foi que **todas** as dependências e código escrito
foram parar dentro desse arquivo. Não é isso o que queremos. Vamos então
otimizar esse build para melhorarmos essas questões.

### Otimização 1: Divisão de Código

Um dos problemas do nosso código é que tanto o código para o Funcionário quanto
o código para o Administrador estão no mesmo arquivo. É "tentador" adicionar um
`if (role === "funcionario") { const funcionario = require('./funcionario.js');
}`, e `if (role === "administrador") { const administrador =
require('./administrador.js'); }`, porém, isso **não** vai funcionar. O webpack
analiza o código como um todo para produzir os *bundles*, portanto, esse código,
mesmo com `if`, ainda assim conterá **todo** o código da aplicação.

Para resolvermos isso da maneira correta, temos que "avisar" o webpack que um
determinado módulo pode ser carregado de forma dinâmica. Podemos usar a sintaxe
`import('<NOME-DO-MODULO>').then(modulo => {});` para carregar o módulo. Assim,
alteramos o arquivo `index.js`:

```javascript
const CONDICAO_FUNCIONARIO = true;
const CONDICAO_ADMINISTRADOR = true;

if (CONDICAO_FUNCIONARIO) {
    import(
        /* webpackChunkName: "funcionario" */
        './funcionario'
    ).then(funcionario => {
        funcionario.default();
    });
}

if (CONDICAO_ADMINISTRADOR) {
    import(
        /* webpackChunkName: "administrador" */
        './administrador'
    ).then(administrador => {
        administrador.default();
    });
}
```

**Importante:** O comentário `/* webpackChunkName */` serve apenas para
indicarmos para o webpack o nome do *chunk*, não sendo uma propriedade
obrigatória, sendo utilizado por questões de organização.  Os métodos importados
estarão localizados na propriedade `default` devido ao padrão de carregamento de
módulos executado pelo webpack.

Verificando o build, podemos ver que agora temos mais arquivos, porém, com
tamanhos menores:

```
Hash: eb3d6846a22cb3db7fc6
Version: webpack 4.6.0
Time: 5104ms
Built at: 2018-04-30 17:06:02
                                Asset       Size  Chunks                    Chunk Names
administrador.fd372788b906c0aef63c.js    312 KiB       0  [emitted]  [big]  administrador
  funcionario.e41d5111d4ecbe55cde7.js    293 KiB       1  [emitted]  [big]  funcionario
         main.5d7893d814fcf51dec05.js   1.97 KiB       2  [emitted]         main
                           index.html  201 bytes          [emitted]
Entrypoint main = main.5d7893d814fcf51dec05.js
  [0] ./scripts/index.js 441 bytes {2} [built]
  [1] ./scripts/administrador.js 168 bytes {0} [built]
  [2] ./scripts/funcionario.js 189 bytes {1} [built]
[130] ../node_modules/d3/index.js + 502 modules 518 KiB {0} [built]
      |    503 modules
[131] ../node_modules/moment/locale sync ^\.\/.*$ 2.91 KiB {1} [optional] [built]
    + 127 hidden modules

WARNING in asset size limit: The following asset(s) exceed the recommended size limit (244 KiB).
This can impact web performance.
Assets:
  administrador.fd372788b906c0aef63c.js (312 KiB)
  funcionario.e41d5111d4ecbe55cde7.js (293 KiB)
```

![Resultado após fazermos o split do código](https://i.imgur.com/Nn78ULg.jpg)

### Otimização 2: Criação de *common/vendor Chunks*

Como podemos ver na imagem anterior, foi criado um *bundle* para cada um
dos arquivos que separamos (`funcionario.js` e `administrador.js`), porém,
podemos notar que o módulo `lodash` está duplicado nos dois arquivos. Isso
acontece pois desabilitamos a opção
[`optimization.splitChunks`](https://webpack.js.org/plugins/split-chunks-plugin/).
Podemos habilitá-la com os valores *default* apenas removendo a propriedade
`splitChunks: false`:

```javascript
module.exports = {
    /* Restante do arquivo */

    optimization: {
    },

    /* Restante do arquivo */
};
```

Caso queiramos utilizar as opções *default*, a propriedade `optimization` pode
ser removida por completo:

```javascript
module.exports = {
    /* Arquivo sem a propriedade `optimization` */
};
```

Com isso, podemos consultar o resultado do *build* novamente:

```
Hash: 238b9bc020cedb1be248
Version: webpack 4.6.0
Time: 7368ms
Built at: 2018-04-30 17:41:51
                                                    Asset       Size  Chunks             Chunk Names
vendors~administrador~funcionario.bc461d536e0696784589.js   69.4 KiB       0  [emitted]  vendors~administrador~funcionario
              vendors~funcionario.ba33f1b641ba56b39d74.js    221 KiB       1  [emitted]  vendors~funcionario
            vendors~administrador.b1331b1609f1429987ae.js    243 KiB       2  [emitted]  vendors~administrador
                    administrador.f49190da31cf3a0c8b4a.js  186 bytes       3  [emitted]  administrador
                      funcionario.5ea0dde0ccc5d666453f.js   3.48 KiB       4  [emitted]  funcionario
                             main.e8c3806c88c392e72bba.js   2.19 KiB       5  [emitted]  main
                                               index.html  201 bytes          [emitted]
Entrypoint main = main.e8c3806c88c392e72bba.js
  [0] ./scripts/index.js 441 bytes {5} [built]
  [1] ./scripts/administrador.js 168 bytes {3} [built]
  [2] ./scripts/funcionario.js 189 bytes {4} [built]
[129] ../node_modules/d3/index.js + 502 modules 518 KiB {2} [built]
      |    503 modules
[130] ../node_modules/moment/locale sync ^\.\/.*$ 2.91 KiB {4} [optional] [built]
    + 127 hidden modules
Child html-webpack-plugin for "index.html":
     1 asset
    Entrypoint undefined = index.html
       4 modules
```

![Resultado de ativarmos o plugin para split de
chunks](https://i.imgur.com/ZUWHAPY.jpg)

Nesse momento, o webpack produziu um arquivo *vendor* para cada um dos nossos
módulos. Nesse caso, o arquivo `vendors~administrador~funcionario` contém as
dependências de ambos `administrador.js` e `funcionario.js`.
`vendors~administrador` contém somente as dependências de `administrador.js` e
`vendors~funcionario` contém as dependências de `funcionario.js`.

Isso aconteceu por conta dos valores *default* de `optimization.splitChunks`:

```
splitChunks: {
    chunks: "async",
    minSize: 30000,
    minChunks: 1,
    maxAsyncRequests: 5,
    maxInitialRequests: 3,
    automaticNameDelimiter: '~',
    name: true,
    cacheGroups: {
        vendors: { /* Os bundles vendor foram gerados por conta dessa regra */
            test: /[\\/]node_modules[\\/]/,
            priority: -10
        },
        default: {
            minChunks: 2,
            priority: -20,
            reuseExistingChunk: true
        }
    }
}
```

Esse nível de otimização já nos traz vários ganhos de performance, porém,
dependendo do cenário, podemos ir um pouco mais além. Dificilmente mudaremos as
versões das *libraries*, portanto, podemos juntá-las todas em um *bundle* só.
Assim, o usuário baixará esse *bundle* uma vez e, somente quando a versão de
alguma *library* mudar, o usuário terá que baixar novamente. Portanto, ao invés
de fazer 3 requests para baixar as dependências, podemos fazer somente um.
Também podemos limitar para que somente sejam inclusas nesse arquivo as
*libraries* que tenham um tamanho acima de 50Kb. Conseguimos isso através da
seguinte configuração:

```
module.exports = {
    /* Restante do arquivo */

    optimization: {
        splitChunks: {
            cacheGroups: {
                test: /node_modules/,
                minSize: 50000,
                name: 'vendors',
            },
        },
    },

    /* Restante do arquivo */
};
```

Podemos ver que há uma redução no tamanho dos arquivos "de negócio", e um
crescimento no arquivo de *vendor*. Além disso, novamente o *webpack* nos dá um
*warning* sobre o tamanho do arquivo *vendor*. Porém, dependendo do cenário, fazer
dessa maneira pode ser melhor. Por exemplo, se as dependências **nunca** vão mudar,
"pagar" o preço de um primeiro carregamento demorado pode valer a pena, visto
que dali em diante aquele arquivo provavelmente estará no cache do usuário.

```
Hash: 93807a9054a94919eb35
Version: webpack 4.6.0
Time: 3644ms
Built at: 2018-04-30 18:41:15
                                Asset       Size  Chunks                    Chunk Names
      vendors.76efdab6264ba70c5152.js    533 KiB       0  [emitted]  [big]  vendors
administrador.043a7ce5527f336989a2.js  186 bytes       1  [emitted]         administrador
  funcionario.559dd4868c9984b13bb8.js   3.48 KiB       2  [emitted]         funcionario
         main.bcfe1dbdb7dfe91b18a7.js   2.11 KiB       3  [emitted]         main
                           index.html  201 bytes          [emitted]
Entrypoint main = main.bcfe1dbdb7dfe91b18a7.js
  [0] ./scripts/index.js 649 bytes {3} [built]
  [1] ./scripts/administrador.js 168 bytes {1} [built]
  [2] ./scripts/funcionario.js 189 bytes {2} [built]
[129] ../node_modules/d3/index.js + 502 modules 518 KiB {0} [built]
      |    503 modules
[130] ../node_modules/moment/locale sync ^\.\/.*$ 2.91 KiB {2} [optional] [built]
    + 127 hidden modules

WARNING in asset size limit: The following asset(s) exceed the recommended size limit (244 KiB).
This can impact web performance.
Assets:
  vendors.76efdab6264ba70c5152.js (533 KiB)
Child html-webpack-plugin for "index.html":
     1 asset
    Entrypoint undefined = index.html
       4 modules
```

![Resultado de melhorarmos o plugin para split de
chunks](https://i.imgur.com/m8USukr.jpg)

## Finalizando

Existem várias possibilidades e vários *trade offs* quando se trata de
otimização de performance. Vale aprender as possibilidades que o webpack traz e
utilizá-las ao seu favor para grantir uma melhor experiências para os usuários.

## Links Relacionados

- [React Loadable](https://github.com/jamiebuilds/react-loadable)
- [webpack Code Splitting](https://webpack.js.org/guides/code-splitting/)
- [Code Splitting](https://survivejs.com/webpack/building/code-splitting/)
- [webpack-bundle-analyzer](https://www.npmjs.com/package/webpack-bundle-analyzer)
