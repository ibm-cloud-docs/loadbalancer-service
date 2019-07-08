---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: resources, server, application, instance, configure

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}

# Identificando recursos do servidor de aplicativos
{: #identifying-your-application-server-resources}

Localize suas **instâncias do servidor** na tabela na parte inferior e clique em **+** para incluí-las atrás do balanceador de carga. É possível selecionar nas
Instâncias de Servidor Virtual (VSIs) do IBM© Cloud e nos Servidores Bare Metal em sua conta.

Essas instâncias do servidor devem ser locais para o data center no qual você implementará o serviço do balanceador de carga. Além disso, as instâncias do servidor dos data centers vizinhos dentro da mesma cidade também podem ser incluídas (por exemplo, se as três primeiras letras do nome do data center forem iguais).

<img src="images/locate-server-instance.png" alt="drawing" style="width: 300px;"/>

Clique em **Avançar**.

Os **pesos** do servidor são relevantes apenas ao usar o método de balanceamento de carga **Round-robin ponderado**. O peso padrão é 50 e o intervalo é de 0 a 100. Os pesos ficam esmaecidos com outros métodos de balanceamento de carga.
{: note}

Consulte [Limitações no número de servidores de aplicativos](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-) para obter mais informações sobre o limite máximo para o número de servidores de aplicativos.
{: tip}

## O que vem a seguir
{: #what-s-next-3}
[Revise o conteúdo](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order) de seu pedido antes de fazê-lo.
