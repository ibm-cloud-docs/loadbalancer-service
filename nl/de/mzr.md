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

# Übersicht über MZR (Multi-Zone Region)
{: #multi-zone-region-mzr-overview}

Wenn Sie eine Lastausgleichsfunktion erstellen, geben Sie das Rechenzentrum an, in dem es erstellt werden soll. Wenn dieses Rechenzentrum Teil eines MZR (Multi-Zone Region) ist, werden die Knoten der Lastausgleichsfunktion in zwei verschiedenen Rechenzentren instanziiert. Beispiel: `us-south` ist ein MZR, das `dal10`, `dal12` und `dal13` enthält. Wenn ein Kunde eine Lastausgleichsfunktion im Rechenzentrum `dal13` erstellt, werden die Knoten in `dal13`, `dal10` oder `dal12` instanziiert. In der Regel sehen Sie keine offensichtlichen Änderungen im Datenverkehr. Die MZR-Unterstützung ist nützlich, wenn die Kommunikation mit einem Rechenzentrum unterbrochen wird. Die Lastausgleichsfunktion funktioniert weiterhin, da sich der andere Knoten in einem anderen Datencenter befindet.

Derzeit sind die folgenden Rechenzentren Teil von MZR:

| MZR-Name | Rechenzentren |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |


## MZR-Anforderungen
MRZs (Multi-Zone Region) haben die folgenden Anforderungen:
* Das von Ihnen ausgewählte Rechenzentrum sollte Teil eines MZR sein. In der Tabelle oben sind die Regionen und die Rechenzentren in jeder Region aufgelistet.
* Das VLAN-Spanning muss in Ihrem Konto aktiviert sein.
* Private Teilnetze müssen in Ihrem Konto in den Rechenzentren des MZR vorhanden sein. Die Erstellung von Recheneinheiten in Rechenzentren führt zur Instanziierung privater Subnetze.

Wenn das von Ihnen ausgewählte Rechenzentrum nicht Teil eines MZR ist oder VLAN-Spanning in Ihrem Konto nicht aktiviert ist, wird bei der Erstellung der Lastausgleichsfunktion standardmäßig das ursprüngliche Verhalten der Instanziierung aller Lastausgleichsfunktionsknoten des von Ihnen angegebenen Rechenzentrums verwendet. 
