+++
authors = "Umbler"
canonical = ""
categories = ["publieditorial"]
date = "2018-11-25T21:29:44-02:00"
excerpt = "Entenda a diferença entre uma hospedagem que usa disco SSD e HDD."
image = "https://i.imgur.com/4gR3t2a.png"
publishdate = "2018-11-25T00:00:00-02:00"
tags = ["hospedagem"]
title = "Hospedagem com SSD vs HDD: diferenças, comparativos e os benefícios reais"
type = "post"
sponsor = "kinghost"
+++
Nos últimos anos, pudemos observar uma transição na indústria de computadores pessoais deixando de lado a utilização de discos rígidos (HDD, ou _hard drives disk_) para optar por armazenamentos sólidos (SSD, _solid state drives_).

Notavelmente mais caros quando o assunto é custo por gigabyte de armazenamento, os SSDs trazem consigo inúmeras vantagens sobre os discos comuns utilizados desde a década de 1950: performance, durabilidade e segurança muito superiores são apenas alguns exemplos. Uma das grandes evoluções se dá pelo fato de que SSDs não possuem partes móveis e armazenam as informações em microchips, ao contrário dos HDDs que utilizam um braço mecânico (agulha semelhante a um toca discos de vinil) para ler/escrever as informações em uma espécie de prato (por isso, uma queda ou simples batida que cause vibração interior pode inutilizar um HDD por completo).

![](https://i.imgur.com/u7ZPPIF.jpg)

_Imagem: HDD de 10Mb dos anos 60 vs SSD 128Gb moderno_

A título de comparação, atualmente SSDs superam, de longe, a quantidade de IOPS de HDDs. IOPS (Input/Output per Second, ou operações de entrada e saída por segundo) indicam quantas operações de leitura e escrita o dispositivo é capaz de realizar por segundo e essa quantidade impacta diretamente na performance.

Na tabela abaixo podemos ver a comparação de um SSD com diversos HDDs com armazenamentos semelhantes e velocidades de rotação diferentes (15K, 10K e 7K RPM). Em todos os resultados (A, B e C) podemos observar uma quantidade absurdamente maior de IOPS que o SSD pode apresentar contra os HDDs utilizados.

![](https://i.imgur.com/aDkN6AJ.jpg)  
É coerente dizer, então, que HDDs serão em breve coisa do passado. Isso porque os SSDs vieram para ficar e, apesar do custo maior, os ganhos de performance e durabilidade compensam muito.

Mas, como falamos no início, isso se refere a indústria da computação pessoal.

E quando falamos de **hospedagem web**, como é o cenário SSD vs HDD?

Você sabe se a hospedagem que utiliza armazena as informações em SSDs? O custo maior por escolher uma hospedagem SSD compensa?

Seus sites, aplicações, banco de dados e emails _precisam_ de uma estrutura em SSD para que atinjam a máxima performance, ou o usuário final (aquele que requisita a informação) não conseguirá distinguir a diferença?

Pensando em esclarecer questões como essa trouxemos Diego Voltz, VP de Tecnologia da **Umbler**, startup de hospedagem cloud.

**1. Quando a utilização de uma hospedagem SSD faz diferença de forma notável?**

De forma resumida e simplificada, qualquer site que não seja estático ou que tenha mais de uma dezena de requisições simultâneas irá se beneficiar do ganho de performance ao utilizar uma hospedagem SSD. Ou seja, se estamos falando de uma loja online em WordPress, por exemplo, é altamente recomendável que esteja hospedada em uma estrutura com SSD. Tanto em situações comuns de pouco tráfego como em eventos temporários como a BlackFriday (onde picos de acesso são esperados), os diferenciais em termos de velocidade pela utilização do SSD já seriam sentidos pelos visitantes do site. Em testes internos, pudemos observar um ganho de velocidade de carregamento de 4x se compararmos uma instalação limpa do WordPress em uma estrutura utilizando SSD vs estrutura utilizando HDD.

A recomendação pelo uso de uma hospedagem SSD fica ainda mais forte se estivermos falando de aplicações que fazem consulta à bancos de dados de forma muito constante. Nesses casos, as velocidades em média **20x menores de I/O** (Input/Output) e leitura/gravação de um HDD ficam evidentes na experiência de uso da aplicação, tornando a opção por SSD obrigatória.

**2. Quais são as principais vantagens de uma hospedagem SSD? Existe diferença entre empresas de hospedagem que usam parcialmente combinando com HDDs ou tem sua infraestrutura toda com SSDs?**

Empresas de hospedagem costumam utilizar diversas táticas para melhorar a performance de estruturas que utilizam HDDs e SSDs em conjunto. É comum, por exemplo, que os bancos de dados funcionem em SSDs enquanto que arquivos estáticos são servidos a partir de HDDs. Load balance, sistemas de cache, proxy e CDNs também contribuem para um ganho de performance quando HDDs ainda são utilizados, principalmente se estivermos falando de hospedagens compartilhadas. Nada de errado nesse aspecto visto que as empresas buscam oferecer a melhor solução com o custo mais baixo para sí e seus clientes. Porém, não há como comparar a performance de estruturas mistas HDD/SSD, mesmo que otimizadas, com estruturas 100% SSD.

Recentemente a Umbler estreou, após investimento milionário, novos servidores com estrutura 100% SSD. Arquivos estáticos, sites, aplicações, emails, bancos de dados e containers rodam na máxima performance possível com SSDs de última geração, tanto em servidores compartilhados como em servidores dedicados.

As vantagens da utilização de uma [hospedagem SSD](https://www.umbler.com/br/hospedagem-ssd?utm_source=tableless&utm_medium=ssdvshdd) não ficam restritas ao ganho de performance na velocidade de carregamento de sites ou aplicações. É possível, por exemplo, criar novos ambientes de hospedagem, bem como expandir, reduzir ou replicá-los de forma muito mais rápida. Um dos aspectos mais importantes de uma hospedagem de sites, a estabilidade, também é beneficiada pelo uso de uma estrutura 100% SSD, uma vez que a tarefa de replicar ambientes torna-se muito mais rápida, e o tempo de downtime, quando há, é reduzido de forma significativa. Logicamente, a criação e restauração de backups também levam menos tempo para serem feitos do que em ambientes que utilizam HDDs.

**3. Enxergando além da velocidade: experiência do usuário e dinheiro**

Por fim, chegamos a um ponto crucial onde as vantagens da utilização de uma hospedagem SSD se tornam imbatíveis.

O Google vem, há muitos anos, dando sinais sobre a importância da velocidade de carregamento dos sites como fator de rankeamento e influência direta na experiência do usuário. Porém, a partir de fevereiro de 2017, retomou com força o tema publicando um report completo com benchmarks¹ sobre a velocidade de carregamento e seus impactos em diversos verticais de negócios.

A imagem abaixo resume muito bem a relação entre tempo de carregamento de uma página e a probabilidade de _bounce_ (rejeição, quando um visitante simplesmente sai da página sem concluir a ação ou continuar a navegação). Quanto maior o tempo de carregamento, maior a probabilidade do visitante evadir.

![](https://i.imgur.com/ji1K1K8.png)

Mas foi no apagar das luzes de 2018 que, novamente, vimos o gigante das buscas retomar o assunto de forma mais contundente, publicando uma nova versão da famosa ferramenta Page Speed Insights, agora com relatórios muito mais detalhados.

Mais do que nunca em 2019 será necessário cuidado próximo e otimização constante do tempo de carregamento para estar de acordo com as diretrizes, satisfazer usuários e não deixar dinheiro sobre a mesa.

Se você quiser ter certeza que está fazendo todo o possível para ter seu site ou aplicação sendo servido com a máxima velocidade, comece escolhendo uma [hospedagem 100% SSD](https://www.umbler.com/br/hospedagem-ssd?utm_source=tableless&utm_medium=ssdvshdd) e, de preferência, em um ambiente dedicado.

A [Umbler](https://www.umbler.com/br?utm_source=tableless&utm_medium=ssdvshdd) possui um dos custos mais baixos do mercado e não cobra nada a mais para hospedar o que você precisar em estruturas 100% SSD. Além disso, ao criar sua conta, você recebe créditos grátis que permitem testar todos os planos de hospedagem sem limite de tempo (e sem precisar inserir cartão de crédito). [**Crie sua conta**](https://app.umbler.com/account/register?utm_source=tableless&utm_medium=ssdvshdd) agora e coloque a prova nossa hospedagem SSD!

¹[https://www.thinkwithgoogle.com/marketing-resources/data-measurement/mobile-page-speed-new-industry-benchmarks/](https://www.thinkwithgoogle.com/marketing-resources/data-measurement/mobile-page-speed-new-industry-benchmarks/ "https://www.thinkwithgoogle.com/marketing-resources/data-measurement/mobile-page-speed-new-industry-benchmarks/")