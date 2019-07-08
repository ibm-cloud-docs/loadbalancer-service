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

# Visión general de la región multizona (MZR)
{: #multi-zone-region-mzr-overview}

Cuando cree un equilibrador de carga, especificará el centro de datos en el que se va a crear. Si dicho centro de datos forma parte de una región multizona (MZR), se crean instancias de los nodos del equilibrador de carga en dos centros de datos diferentes. Por ejemplo, `us-south` es una MZR que contiene `dal10`, `dal12`, `dal13`. Si un cliente crea un equilibrador de carga en el centro de datos `dal13`, se crean instancias de los nodos en `dal13`, en `dal10` o en `dal12`. Por lo general, no observará ningún cambio evidente en el tráfico. El soporte de MZR resulta útil cuando se interrumpe la comunicación con un centro de datos. El equilibrador de carga continuará funcionando, ya que el otro nodo se encuentra en otro centro de datos.

Actualmente, los siguientes centros de datos forman parte de la MZR:

| Nombre de MZR | Centros de datos |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |
| eu-gb | lon04, lon05, lon06 |
| eu-de | fra02, fra04, fra05 |
| jp-tok | tok02, tok04, tok05 |
| au-syd | syd01, syd04, syd05 |


## Requisitos de MZR
{: #mzr-requirements}
Las regiones multizona tienen los requisitos siguientes:
* El centro de datos que seleccione debe formar parte de una MZR. En la tabla anterior se muestran las regiones y los centros de datos de cada región.
* Su cuenta debe tener habilitada expansión de VLAN o bien VRF.
* Las subredes privadas deben existir en su cuenta en los centros de datos de la MZR. Si se crean dispositivos de cálculo en centros de datos, se crean instancias de subredes privadas.

Si el centro de datos que selecciona no forma parte de una MZR o si no tiene habilitada la expansión de VLAN o VRF en la cuenta, la creación del equilibrador de carga adopta de forma predeterminada el comportamiento original consistente en crear instancias de todos los nodos del equilibrador de carga en el centro de datos que especifique.
