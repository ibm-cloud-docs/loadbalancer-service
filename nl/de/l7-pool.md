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

# Layer 7-Pool
{: #layer-7-pool}

Ein Layer 7-Pool (L7) ist eine logische Gruppierung der Server (Mitglieder) für die Bearbeitung eingehender Anforderungen.

Die Layer 7-Lastausgleichsfunktion kann den eingehenden Datenverkehr basierend auf den Richtlinien und Regeln an verschiedene Back-End-Pools leiten. Diese Funktion wird unterstützt durch die Zuordnung mehrerer L7-Pools zu einer Lastausgleichsfunktion. Layer 7-Pools werden mit den Layer 7-Richtlinien verwendet, deren Aktion `Umleiten an einen Pool` lautet.

L7-Pools unterstützen nur HTTP als Back-End-Protokoll.

## Sitzungspersistenz
Sitzungspersistenz kann für jeden Layer 7-Pool konfiguriert werden. Weitere Details finden Sie im Abschnitt zum  
[erweiterten Datenverkehr](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer).

## Layer 7-Mitglieder

Back-End-Server, die einem Layer 7-Pool zugeordnet sind, werden als Layer 7-Mitglieder bezeichnet.

Derselbe Back-End-Server kann mehrfach zu L7-Pools hinzugefügt werden, indem jedes Mal eine andere Portnummer angegeben wird.

## Statusprüfungen konfigurieren
Die Definition von Statusprüfungen ist für jeden Layer 7-Pool obligatorisch. Das System füllt eine Standardkonfiguration für die Statusprüfung für L 7-Pools aus.

Sie können diese Einstellungen an Ihre Anwendungsanforderungen anpassen:

 * **Intervall**: Intervall in Sekunden zwischen zwei aufeinander folgenden Statusprüfungsversuchen.
 * **Zeitlimit**: Maximale Zeit, während der das System auf eine Antwort für eine Anforderung einer Statusprüfung wartet.
 * **Max. Neuversuche**: Maximale Anzahl zusätzlicher Statusprüfungsversuche, die das System ausführt, bevor der Service als fehlerhaft deklariert wird.
 * **URL-Pfad**: Der HTTP-URL-Pfad für die Layer 7-Statusprüfung.
