---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Identifique os recursos do servidor de aplicativos
Localize suas **instâncias do servidor** na tabela na parte inferior e clique em **+** para incluí-las atrás do balanceador de carga. É possível selecionar no IBM Cloud Virtual Server Instances (VSIs) e no Bare Metal Servers em sua conta.

Essas instâncias do servidor devem ser locais para o data center no qual você implementará o serviço do balanceador de carga. Além disso, as instâncias do servidor dos data centers vizinhos dentro da mesma cidade também podem ser incluídas (por exemplo, se as três primeiras letras do nome do data center forem iguais).

<img src="images/locate-server-instance.png" alt="drawing" style="width: 300px;"/>

Clique em **Avançar**.

**NOTAS:** 

1. Os **pesos** do servidor são relevantes apenas ao usar o método de balanceamento de carga **Round-robin ponderado**. O peso padrão é 50 e o intervalo é de 0 a 100. Os pesos ficam esmaecidos com outros métodos de balanceamento de carga.
2. Consulte [Limitações no número de servidores de aplicativos](faqs.html#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-) para obter mais informações sobre o limite máximo para o número de servidores de aplicativos.

## O que vem a seguir
[Revise o conteúdo](order-lb.html) de seu pedido antes de fazê-lo.
