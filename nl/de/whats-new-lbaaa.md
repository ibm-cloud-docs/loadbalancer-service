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


# Neuerungen

Informieren Sie sich über neue und aktualisierte Funktionen in IBM Cloud Load Balancer.

## August 2018
### Layer 7-Support
IBM Cloud Load Balancer unterstützt jetzt den Layer 7-Lastausgleich. Dank Layer 7-Support (L7) kann Datenverkehr an eine URL umgeleitet, abgelehnt oder an L7-Poolmitglieder verteilt werden, einschließlich Bare-Metal- und virtueller Serverinstanzen. Eingehender Datenverkehr wird mithilfe von Layer 7-Richtlinien und -Regeln klassifiziert. Die Richtlinien definieren, welche Aktion ausgeführt werden soll, wenn der Datenverkehr mit den Regeln übereinstimmt, die ihnen zugeordnet sind. 

Weitere Details finden Sie unter [Layer 7-Lastausgleich](l7-explained.html). 

## April 2018
### Horizontale Skalierung
IBM Cloud Load Balancer skaliert jetzt automatisch, wenn die Last zunimmt oder abnimmt. Wenn Sie eine Lastausgleichsfunktion erstellen, startet sie mit zwei Appliances, die Anzahl der Appliances kann jedoch (derzeit) auf 16 erhöht werden, wenn vom Überwachungssystem eine Zunahme der Last erkannt wird. Die IP-Adressen der einzelnen aktiven Appliances werden als DNS A-Datensätze zum vollständig qualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) der Lastausgleichsfunktion hinzugefügt.

### Interne Lastausgleichsfunktion
Jetzt ist die stark nachgefragte "interne" Version von IBM Cloud Load Balancer verfügbar. Diese Lastausgleichsfunktion ist nicht öffentlich zugänglich, kann aber trotzdem dazu verwendet werden, die Last von Anwendungen in ihren privaten IBM Cloud-Netzen auszugleichen (wie in der Abbildung zum Beispiel in einer mehrschichtigen Umgebung).  

![Interne Lastausgleichsfunktion](./images/InternalLB.png)

Sie ist sowohl sicher als auch mit den vorherigen Versionen von IBM Cloud Load Balancer auf der öffentlichen Seite konsistent. 

### Überwachungsmetriken
Mit dem Service "IBM Cloud Monitoring" können Sie jetzt die folgenden Leistungsmetriken überwachen, die der Lastausgleichsfunktion und der Anwendung zugeordnet sind:

* Durchsatz
* Verbindungsrate
* Aktive Verbindungen

![Überwachungsmetriken](./images/Metrics.png)

Von der Webbenutzerschnittstelle der Lastausgleichsfunktion werden bis zu zwei Wochen Stichproben erfasst und angezeigt. Die Daten können auch im Serviceportal von IBM Cloud Monitoring angezeigt werden. Falls Sie Daten für mehr als zwei Wochen benötigen, müssen Sie abhängig von der Menge anderer Cloudmetriken, die Sie eventuell an die Cloud Monitoring-Instanz senden, unter Umständen ein Upgrade für den Überwachungsplan durchführen. Weitere Details finden Sie unter [Überwachungsmetriken](monitoring-metrics.html). 

Damit diese Funktion genutzt werden kann, müssen die IaaS- und PaaS-Konten von IBM Cloud über einige [einfache Schritte ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/account/softlayerlink.html#link_user_account) verknüpft werden.  

### Anpassung der Cipher-Suite
Sie können jetzt die Cipher-Suites anpassen, die verwendet werden, wenn die Lastausgleichsfunktion für die SSL-Terminierung konfiguriert wird. 

Wenn Sie die SSL-Terminierung für IBM Cloud Load Balancer aktivieren (durch Auswählen von **HTTPS** als Front-End-Protokoll), wird eine sorgfältig ausgewählte Standardgruppe aus Cipher-Suites aktiviert, die den besten Sicherheitsverfahren entsprechen. IBM überwacht genauestens auf neue Sicherheitslücken; falls solche erkannt werden, wird die Liste entsprechend aktualisiert. Dies trägt zusammen mit der nahtlosen Aktualisierung von Sicherheitsinformationen für Software- und Hardwarekomponenten zu einem durchgehenden Schutz der Anwendungen bei. 

Weitere Details finden Sie unter [Angepasste Cipher-Suite](custom-ciphers.html). 
