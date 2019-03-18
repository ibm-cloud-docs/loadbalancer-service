---

copyright:
  years: 2017, 2018
lastupdated: "2019-01-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Visão geral da região multizona (MZR)
{: #multi-zone-region-mzr-overview}

Ao criar um balanceador de carga, você especificará o data center no qual ele deverá ser criado. Se esse data center for parte de uma região multizona (MZR), os nós do balanceador de carga serão instanciados em dois data centers diferentes. Por exemplo, `us-south` é uma MZR que contém `dal10`, `dal12`, `dal13`. Se um cliente criar um balanceador de carga no data center `dal13`, os nós serão instanciados em `dal13`, `dal10` ou `dal12`. Normalmente, você não verá nenhuma mudança óbvia no tráfego. O suporte a MZR é útil quando a comunicação com um data center é interrompida. O balanceador de carga continuará a funcionar, uma vez que o outro nó está localizado em um data center diferente.

Atualmente, os data centers a seguir fazem parte da MZR:

| Nome da MZR | Data centers |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |


## Requisitos da MZR
Regiões multizona incluem os requisitos a seguir:
* O data center selecionado deve fazer parte de uma MZR. A tabela acima lista as regiões e os data centers em cada região.
* A ampliação de VLAN deve estar ativada em sua conta.
* As sub-redes privadas devem existir em sua conta nos data centers da MZR. A criação de dispositivos de cálculo nos data centers resulta na instanciação de sub-redes privadas.

Se o data center selecionado não fizer parte de uma MZR ou se a ampliação de VLAN não estiver ativada em sua conta, a criação do balanceador de carga será padronizada com o comportamento original de instanciação de todos os nós do balanceador de carga no data center que você especificar.
