# React Native: Build release android

## Passo 1 :
### Gerando uma chave de assinatura
Você pode gerar uma chave de assinatura privada usando o `keytool`
 ```sh
$ $ keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
```

## passo 2: 

Coloque o arquivo `my-release-key.keystore`
no diretório `android/app` do seu projeto

## Passo 3
### Configurando as váriaveis do gradle

1.  Coloque o `my-release-key.keystore` arquivo no `android/app`diretório da pasta do seu projeto.
2.  Edite o arquivo `~/.gradle/gradle.properties`ou `android/gradle.properties` e inclua o seguinte (substitua `*****`pela senha do keystore, alias e senha de chave),

```sh
  MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
  MYAPP_RELEASE_KEY_ALIAS=my-key-alias
  MYAPP_RELEASE_STORE_PASSWORD=**
  MYAPP_RELEASE_KEY_PASSWORD=*****
```

# Passo 4: 
Edite o arquivo `android/app/build.gradle` na pasta do seu projeto e adicione a configuração de assinatura:

```sh
...
android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_RELEASE_STORE_FILE')) {
                storeFile file(MYAPP_RELEASE_STORE_FILE)
                storePassword MYAPP_RELEASE_STORE_PASSWORD
                keyAlias MYAPP_RELEASE_KEY_ALIAS
                keyPassword MYAPP_RELEASE_KEY_PASSWORD
            }
        }
      }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}
...
```
## Passo 5
Gerar o apk
Basta executar o seguinte no terminal
```sh
$ cd android
$ ./gradlew assembleRelease
```
O APK gerado pode ser encontrado em  `android/app/build/outputs/apk/app-release.apk`, e está pronto para ser distribuído.

Para testar o app, conecte seu dispositivo android via usb ao computador, na pasta do projeto execute o comando

```sh
$ react-native run-android --variant=release
```

obs: garanta que seu dispositivo esteja com o modo de depuração ligado. 

*Para mais informações acesse:
https://facebook.github.io/react-native/docs/signed-apk-android.html*
