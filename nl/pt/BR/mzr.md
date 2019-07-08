---

copyright:
  years: 2017, 2018
lastupdated: "2019-01-11"

keywords: mzr, overview, data centers

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Visão geral da região multizona (MZR)
{: #multi-zone-region-mzr-overview}

Ao criar um balanceador de carga, você especificará o data center no qual ele deverá ser criado. Se esse data center for parte de uma região multizona (MZR), os nós do balanceador de carga serão instanciados em dois data centers diferentes. Por exemplo, `us-south` é uma MZR que contém `dal10`, `dal12`, `dal13`. Se um cliente criar um balanceador de carga no data center `dal13`, os nós serão instanciados em `dal13`, `dal10` ou `dal12`. Normalmente, você não verá nenhuma mudança óbvia no tráfego. O suporte a MZR é útil quando a comunicação com um data center é interrompida. O balanceador de carga continuará a funcionar, uma vez que o outro nó está localizado em um data center diferente.

Atualmente, os data centers a seguir fazem parte da MZR:

| Nome da MZR | Data centers |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |
| eu-gb | lon04, lon05, lon06 |
| eu-de | fra02, fra04, fra05 |
| jp-tok | tok02, tok04, tok05 |
| au-syd | syd01, syd04, syd05 |


## Requisitos da MZR
{: #mzr-requirements}
Regiões multizona incluem os requisitos a seguir:
* O data center selecionado deve fazer parte de uma MZR. A tabela acima lista as regiões e os data centers em cada região.
* A ampliação de VLAN ou VRF deve estar ativada em sua conta.
* As sub-redes privadas devem existir em sua conta nos data centers da MZR. A criação de dispositivos de cálculo nos data centers resulta na instanciação de sub-redes privadas.

Se o data center selecionado não for parte de uma MZR ou se a ampliação de VLAN ou VRF não
estiver ativada em sua conta, a criação do balanceador de carga será padronizada para o comportamento
original de instanciar todos os nós do balanceador de carga no data center especificado.
