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

# Panoramica della regione multizona (o MZR, Multi-Zone Region)
{: #multi-zone-region-mzr-overview}

Quando crei un programma di bilanciamento del carico, specificherai il data center in cui deve essere creato. Se tale data center fa parte di una regione multizona (MZR), i nodi del programma di bilanciamento del carico vengono istanziati in due data center diversi. Ad esempio, `us-south` è una MZR che contiene `dal10`, `dal12`, `dal13`. Se un cliente crea un programma di bilanciamento del carico nel data center `dal13`, i nodi vengono istanziati in `dal13`, `dal10` o `dal12`. Di norma, non vedrai cambiamenti ovvi nel traffico. Il supporto MZR è utile quando la comunicazione con un data center viene interrotta. Il programma di bilanciamento del carico continuerà a funzionare poiché l'altro nodo si trova in un data center diverso.

Al momento, i data center che fanno parte della MZR sono:

| Nome MZR | Data center |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |
| eu-gb | lon04, lon05, lon06 |
| eu-de | fra02, fra04, fra05 |
| jp-tok | tok02, tok04, tok05 |
| au-syd | syd01, syd04, syd05 |


## Requisiti della MZR
{: #mzr-requirements}
I requisiti delle regioni multizona (MZR) sono:
* Il data center che hai selezionato deve fare parte di una MZR. La tabella sopra riportata elenca le regioni e i data center presenti in ciascuna regione.
* Lo spanning delle VLAN o VRF deve essere abilitato nel tuo account.
* Le sottoreti private devono essere presenti nel tuo account nei data center della MZR. La creazione di dispositivi di calcolo nei data center provoca l'istanziazione delle sottoreti private.

Se il data center che hai selezionato non fa parte di una MZR oppure se lo spanning delle VLAN o VRF non è abilitato nel tuo account, alla creazione del programma di bilanciamento del carico verrà applicata l'impostazione predefinita del comportamento originale che consiste nell'istanziare tutti i nodi del programma di bilanciamento del carico nel data center che hai specificato
