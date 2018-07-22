---
title: 'Fontes customizadas no React-Native'
authors: Julio Carneiro
type: post
publishdate: 2018-01-25
date: 2018-01-14
excerpt: como você pode fazer para usar fontes customizadas no seu projeto React-Native.
image: https://cdn-images-1.medium.com/max/2000/1*i6wjMxUd9IBwah_12Y5UBw.jpeg
categories:
  - Javascript
tags:
  - reactjs
  - javascript
  - front-end
---


## Como utilizar a fonte que você quiser em seu projeto react-native

Fala pessoalzinho tranquilo? Espero que sim!<br> Neste post vou explicar bem
rapidamente **como você pode fazer para usar fontes customizadas no seu projeto
React-Native**.

A um tempo eu estava querendo escrever sobre RN (**que é com o que estou
trabalhando atualmente**) porém, eu devo um post sobre **React **e me achava na
obrigação de terminar ele primeiro. Enfim, isso mudou e eu **decidi escrever
sobre RN** hahaha.

Estou escrevendo alguns posts básicos sobre o RN, o primeiro era **como começar
os projetos** mas eu terminei este post primeiro e decidi publicar. Então pra
você entender ele seria legal você manjar o básico ok?

### Nomeação de fontes

Para garantir que as fontes sejam lidas pelo **Android **e pelo **iOS
**precisamos primeiro garantir que o nome da nossa fonte seja **o mesmo que
consta no arquivo da fonte**.

Por exemplo, eu escolhi a **Open Sans** para realizar o exemplo então vou clicar
com o direito nela > **Propriedades **> **Detalhes **e ver a propriedade
**Título**, o nome do arquivo de fonte deve ser **o mesmo nome do Título**.

![](https://cdn-images-1.medium.com/max/800/1*_wXPRumzhuuTR4_Ko0fwHQ.png)

No meu caso mudei de **OpenSans-Regular.ttf** para **Open Sans.ttf**, assim vou
garantir que funcione em ambos os sistemas pois o **Android **le o arquivo pelo
nome e o **iOS **pela propriedade de nome.

### Adicionando fontes

Agora vamos fazer uma pasta na raiz do nosso projeto “**/assets/fonts**” e jogar
todas as nossas fontes lá.

![](https://cdn-images-1.medium.com/max/800/1*RzBbg78JM-GIe3pQdZhDSg.png)

### Package.json

Agora precisamos nos comunicar com o RN e dizer pra ele que criamos duas pastas
novas e temos arquivos dentro de** **“**/fonts**”, vamos fazer isso usando o
**rnpm**, onde vamos fornecer o caminho dos arquivos:

    "rnpm":{
      "assets":["./assets/fonts/"]
    },

Depois disso vamos linkar nossas modificações com o RN utilizando o **LINK**:

    react-native link

Isso deve adicionar as referências de fonte no seu arquivo **Info.plist** para
**iOS **e, no **Android**, em “**android/app/src/main/assets/fonts**”.

Você pode verificar se realmente foram atualizadas no **iOS **abrindo o**
Info.plist** no seu editor de texto e procurar pela key “ **UIAppFonts**”:

![](https://cdn-images-1.medium.com/max/800/1*u4SkiGwIeXrPhPmgd_bZJg.png)

No Android procurando pela pasta “**android/app/src/main/assets/fonts**” e
verificando se os arquivos estão lá.

![](https://cdn-images-1.medium.com/max/800/1*Enwc-4CUr7utslp8boEFzw.png)

### Adicionando estilos

Com suas fontes em seu devido lugar e referenciadas, agora é só adicioná-las aos
seus styles. Basta adicionar uma propriedade **fontFamily **com o nome da fonte:

    import React, { Component } from 'react';
    import {StyleSheet,Text,View} from 'react-native';

    export default 
     App 
     Component<{}> {
      render() {
        return (
          <View style={styles.container}>
            <Text style={styles.welcome}>Júlio Carneiro</Text>
            <Text style={styles.instructions}>Custom fonts in React-Native</Text>
          </View>
        );
      }
    }

     styles = StyleSheet.create({
      container: {
          flex: 1,
          justifyContent: 'center',
          alignItems: 'center',
          backgroundColor: '#F5FCFF',
      },
      welcome: {
        fontSize: 20,
        textAlign: 'center',
        margin: 10,
        fontFamily: 'Open Sans',
        fontWeight:'800',
      },

      instructions: {
        textAlign: 'center',
        color: '#333333',
        marginBottom: 5,
        fontFamily: 'Open Sans',
      },
    });

#### Captura de tela do Android

![](https://cdn-images-1.medium.com/max/800/1*qf-ICSWMhVfjNCE_9SK4ZQ.png)

#### Captura de tela do iOS

![](https://cdn-images-1.medium.com/max/800/1*z6-nY28OMrMsQLs1WO4gaQ.png)

#### Código fonte

Você pode encontrar o código-fonte deste tutorial no [**Github**](https://github.com/juliocarneiro/react-native-custom-fonts):
