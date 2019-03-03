---
title: Medindo corretamente a latência dos seus serviços
authors: Breno Panzolini
type: post
date: 2019-03-03
excerpt: Se você sempre utilizou a média como medida de latência, você não está fazendo isso da melhor forma.
categories:
  - Tecnologia e Tendências
tags:
  - DevOps
image: https://tudosobrehospedagemdesites.com.br/site/wp-content/uploads/2018/04/como-medir-latencia-servidor_topo-728x273.png
---

Para de usar a média como medida de latência dos seus serviços.

Sim, pode até parecer radical (não me entendam errado), mas se você utiliza apenas a média como medida de latência você pode estar deixando muita informação valiosa escapar. Digo isso por experiência própria, pois eu mesmo mal conhecia outras métricas muito valiosas.

# O que é latência?

Latência é uma métrica muito importante em qualquer sistema, ela é a diferença entre o estímulo e a resposta, resumindo: quanto "a coisa" demora para acontecer.

Quando digo "a coisa", isso vai depender do tipo de sistema que se está querendo medir. Em um banco de dados, por exemplo, a latência pode ser medida através do tempo que uma consulta demora para ser processada. Já em uma API ela geralmente é medida entre o tempo de *request* e *response*.

Quanto menor for a latência, mais rápido nossas operações vão ser executadas, e hoje em dia com os sistemas distribuídos e de altas disponibilidades, ter uma latência baixa é quase que mandatório.

# Qual o problema com as média?
