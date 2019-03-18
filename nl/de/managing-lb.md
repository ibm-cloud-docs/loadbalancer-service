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

# Service überwachen und verwalten
{: #monitoring-and-managing-your-service}

Sie können Ihre Konfiguration bearbeiten oder Ihre Serviceleistung überwachen, indem Sie auf der Übersichtsseite der Lastausgleichsfunktion auf die URL des Servicenamens klicken. 

Die **Adresse des vollständig qualifizierten Domänennamens (FQDN)** Ihrer Lastausgleichs-Serviceinstanz wird direkt unter dem Servicenamen angezeigt. Ihre Endbenutzer können über diese FQDN-Adresse eine Verbindung zu Ihrer Anwendung herstellen. Beachten Sie, dass die öffentlichen und privaten IP-Adressen des Lastausgleichsservice nicht offengelegt werden. Nur die FQDN-Adresse wird verfügbar gemacht. 

<img src="images/fqdn-address.png" alt="Zeichnung" style="width: 300px;"/>

Die Registerkarte **Übersicht** enthält allgemeine Statusinformationen zu Ihrem Service. Sie zeigt den aktuellen Status Ihrer Anwendungsserver und der zugehörigen Ports an. Sie bietet außerdem eine kurze Zusammenfassung der Systemleistung durch Angabe des Durchsatzes, der Verbindungsrate, der gleichzeitig bestehenden Verbindungen usw. 

Navigieren Sie zur Registerkarte **Überwachung**, um Echtzeitdiagramme Ihrer Systemleistung anzuzeigen. Diese Diagramme können pro Anwendungsport und für verschiedene Zeitdauern angezeigt werden. 

<img src="images/monitor-lb.png" alt="Zeichnung" style="width: 300px;"/>

Sie können Ihre vorhandene Konfiguration auf den Registerkarten **Protokolle**, **Serverinstanzen** und **Statusprüfungen** bearbeiten. Navigieren Sie beispielsweise zur Registerkarte 'Protokolle', um zusätzliche Anwendungsports zu definieren oder um die SSL-Cipher-Liste anzupassen. 

<img src="images/protocols-monitor.png" alt="Zeichnung" style="width: 300px;"/>
