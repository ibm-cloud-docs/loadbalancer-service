---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Layer 7-Lastausgleich
{: #layer-7-load-balancing}

Vom IBM© Cloud Load Balancer-Service wird der Datenverkehr unter Verwendung von Layer 7-Daten (Anwendungsebene) auf mehrere Serverinstanzen verteilt, darunter Bare-Metal-Server und virtuelle Server.  

 * Der zu verteilende Datenverkehr wird mithilfe von Richtlinien und Regeln klassifiziert. 
 * Richtlinien definieren, welche Aktion ausgeführt werden soll, wenn der Datenverkehr mit allen Regeln übereinstimmt, die einer Richtlinie zugeordnet sind.
 * Layer 7-Lastausgleich (L7) wird nur für HTTP- und HTTPS-Datenverkehr unterstützt.

## Layer 7-Richtlinien und -Regeln 
Eine Layer 7-Richtlinie ist einem Front-End-Anwendungsport zugeordnet. Einem Front-End-Port können mehrere Richtlinien zugeordnet sein. 

 * Diese Richtlinien werden in der Reihenfolge ihrer Priorität ausgewertet. 
 * Wenn die Richtlinie übereinstimmt, wird eine zugeordnete Aktion ausgeführt.
 * Jede L7-Regel ist einer Richtlinie zugeordnet. 
 * Wenn alle Regeln, die der Richtlinie zugeordnet sind, zu `true` ausgewertet werden, stimmt die Richtlinie überein und es wird die zugeordnete Aktion ausgeführt.

Weitere Details finden Sie unter [L7-Richtlinie und -Regeln](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy).

## Layer 7-Pools
Jeder Layer 7-Lastausgleichspool enthält mindestens eine logische Serverinstanz. 

 * Jede logische Serverinstanz ist durch eine IP-Adresse und eine Portnummer angegeben. 
 * Jedem Pool ist eine Statusüberwachung zugeordnet, die den Status aller Server im Pool überwacht.
 * Ein Pool kann für Sitzungspersistenz konfiguriert werden. 
 * Verwenden Sie die Quellen-IP-Adresse des Clients, um Sitzungspersistenz zu konfigurieren.

Weitere Details finden Sie unter [L7-Pools](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool).
