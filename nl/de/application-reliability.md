---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Zuverlässigkeit und Skalierbarkeit von Anwendungen mit globalem Lastausgleich von IBM Cloud Internet Services verbessern
Wenn Sie über eine E-Commerce-Site verfügen oder eine Anwendung hosten, die für Ihre Endbenutzer jederzeit zugänglich sein muss, sind Sie wahrscheinlich darauf bedacht, dass die Verfügbarkeit und Leistung Ihrer Anwendung rund um die Uhr sichergestellt ist. 

Die Funktionen des globalen Lastausgleichs, die von IBM Cloud Internet Services (CIS) bereitgestellt werden, können dazu beitragen, die Zuverlässigkeit und Skalierbarkeit Ihrer Anwendung zu verbessern, und bieten gleichzeitig die bestmögliche Endbenutzererfahrung. In diesem Handbuch wird die Konfiguration des globalen Lastausgleichs erläutert.  

## Lernziele

In dieser schrittweisen Anleitung lernen Sie, wie Sie eine Konfiguration einrichten, die der nachfolgend beschriebenen ähnelt.

<img src="images/Reliability1.png" alt="Zeichnung" style="width: 300px;"/>

Im folgenden Beispiel werden die Anwendungsressourcen an zwei Rechenzentrumsstandorten bereitgestellt, einer im Westen und einer im Osten der USA. Die Endbenutzer können aus der ganzen Welt auf diese Anwendung zugreifen. 

Task  | Beschreibung
------------- | -------------
[CIS-Instanz erstellen](create-cis.html) | Beginnen Sie mit der Erstellung einer Instanz von IBM Cloud Internet Services (CIS) im IBM
Kundenportal.
[Informationen zu Domäne eingeben](input-domain.html) | Geben Sie Informationen zu der Domäne ein, die Sie schützen und für die Sie einen globale Lastausgleich bereitstellen möchten.
[Konfiguration der globalen Lastausgleichsfunktion starten](begin-config.html) | Starten Sie die Konfiguration der globalen Lastausgleichsfunktion.
[Anwendungsressourcen angeben](identify-app-resources.html) | Geben Sie die Anwendungsressourcen an, zum Beispiel Ursprungspools und Mechanismen für die Statusprüfung.
[Globale Lastausgleichsfunktion definieren](define-global-lb.html) | Definieren Sie die Konfiguration der globalen Lastausgleichsfunktion durch Angeben eines Hostnamens, Hinzufügen und Anpassen der Ursprungspools und Definieren zusätzlicher Regeln zum Steuern des Datenverkehrs zu den Clients.
