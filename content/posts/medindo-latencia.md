---
title: Medindo corretamente a latência dos seus serviços
authors: Breno Panzolini
type: post
date: 2019-03-04
excerpt: Se você sempre utilizou a média como medida de latência, você não está fazendo isso da melhor forma.
categories:
  - Tecnologia e Tendências
tags:
  - DevOps
image: https://tudosobrehospedagemdesites.com.br/site/wp-content/uploads/2018/04/como-medir-latencia-servidor_topo-728x273.png
---

Para de usar a média como medida de latência dos seus serviços.

Sim, pode até parecer radical (não me entendam errado), mas se você utiliza apenas a média como medida de latência você pode estar deixando muita informação valiosa escapar. Digo isso por experiência própria, pois eu mesmo mal conhecia outras métricas.

# O que é latência?

Latência é uma métrica muito importante em qualquer sistema, ela é a diferença entre o estímulo e a resposta, resumindo: quanto "a coisa" demora para acontecer.

Quando digo "a coisa", isso vai depender do tipo de sistema que se está querendo medir. Em um banco de dados, por exemplo, a latência pode ser medida através do tempo que uma consulta demora para ser processada. Já em uma API ela geralmente é medida entre o tempo de *request* e *response*, em um sistema web ela pode ser medida como o tempo que sua página demora para ser carregada, e assim por diante.

Quanto menor for a latência, mais rápido nossas operações vão ser executadas, e hoje em dia com os sistemas distribuídos e de altas disponibilidades, ter uma latência baixa é quase que mandatório.

# Qual o problema com a média?

A maioria das pessoas (e eu me coloco nessa lista), está acostumado a utilizar a média ou mediana para medir a latência nos seus sistemas, porém essa maneira pode trazer alguns probleminhas.

A melhor forma de mostrar é através de um exemplo.

Imagine que você tem o seguinte conjunto de amostras da latência do carregamento da página de login do seu sistema (medidas em milisegundos):

[70, 60, 30, 800, 50, 900, 40, 20]

Fazendo a média chegamos no valor de **246ms**, mas olhando as amostras fica claro que esse valor não representa a realidade da latência do sistema. O que temos, na verdade, é que a maioria dos nossos usuários estão tendo uma experiência bem rápida (menor que 100ms), enquanto alguns uma experiência demorada (mais que 800ms).

O pior de tudo isso é que a nossa média está dando 246ms e isso não representa a realidade de nenhum dos nossos usuários, nem dos que estão tendo a melhor performance, muito menos daqueles que estão tendo uma pior experiência.

Resumindo, usar a média como medida de latência pode te enganar e dar uma sensação que não é a que está sendo sentida na prática.

# Bem-vindo percentil

Na estatística, existe uma medida chamada [percentil](https://pt.wikipedia.org/wiki/Percentil), e resumindo, ela consiste em ordenar uma amostra de forma crescente e dividir ela em 100 partes, cada uma com uma porcentagem dos dados aproximadamente igual.

Talvez a teoria soa um pouco complicado, mas na prática é muito mais fácil do que parece, vamos ao exemplo.

Vou tomar como base o mesmo conjunto de amostras anterior, a única coisa que vou fazer é ordenar os valores de forma crescente para facilitar os entendimentos posteriores:

[20, 30, 40, 50, 60, 70, 800, 900]

Dado a amostra acima, uma boa métrica de latência para começarmos analisar é o **P50** e **P90**.

- **P50**: descartamos 50% (em ordem) dos valores da amostra e recuperamos o primeiro valor que "sobra", ou seja, nosso P50 = **60ms**
- **P90**: descartamos 90% (em ordem) dos valores da amostra e recuperamos o primeiro valor que "sobra", no caso o P90 = **900ms**

## Quais as vantagens?

Algumas das vantagens que podemos observar quando utilizamos percentis:

1. Eles não são afetados por *outliers* (dados que se diferenciam drasticamente de todos os outros), como acontece com as médias.
2. Cada percentil aponta, de fato, para a experiência que o nosso usuário está tendo no nosso sistema

Os números mais comuns para a medição da latência nos sistemas, utilizando os percentis, são: P50, P75, P90, P95 e P90.

![percentile](https://user-images.githubusercontent.com/14098361/39696912-81b75bb8-51ef-11e8-8e8b-420b6d85c7f3.png)

## Como interpretar o percentil corretamente?

Quando analisamos o valor do **P99**, por exemplo, significa saber que temos 1% das nossas amostras que vão estar acima desse valor e todo o restante estará abaixo.

Por isso, se temos um P99 = 10ms, sabemos que apenas 1% dos nossos usuários estão tendo um valor acima disso e todo o restante está abaixo desse valor.

# Conclusão

Esse post foi bem simples e curto, porém direto ao ponto, pois queria fazer com que mais pessoas saibam uma melhor forma de medir a latência nos seus sistemas.

Outra coisa que queria deixar claro é que apesar de ter mostrado um pouco da estatística por trás das métricas, você não precisa se preocupar com a parte chata, a maioria dos sistemas já tem esses cálculos prontos para serem utilizados (DataDog, NewRelic, Grafana, etc).
