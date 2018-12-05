---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Risoluzione dei problemi dello spanning delle VLAN del programma di bilanciamento del carico
Questo argomento fornisce le informazioni sui problemi comuni che puoi riscontrare quando il programma di bilanciamento del carico e le istanze di calcolo connesse ad esso si trovano in sottoreti diverse. È necessario che lo spanning delle VLAN sia abilitato affinché il programma di bilanciamento del carico possa comunicare e inoltrare le richieste alle istanze di calcolo residenti in una sottorete diversa. 

1. Accedi al [Customer Portal](https://control.softlayer.com), spostati in **Network > IP Management**, quindi fai clic su **VLANs**.

2. Passa **VLAN Spanning** su **On**.

<img src="images/vlan-spanning.png" alt="disegno" style="width: 500px;"/>

Quest'azione apre la comunicazione tra il programma di bilanciamento del carico e le sue istanze di calcolo. 
