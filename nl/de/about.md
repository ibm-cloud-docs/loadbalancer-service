---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Produktinformation

Der IBM Cloud Load Balancer-Service unterstützt die Kunden beim Verbessern der Verfügbarkeit ihrer geschäftskritischen Anwendungen; dazu wird der Datenverkehr auf mehrere Anwendungsserverinstanzen verteilt und ausschließlich an ordnungsgemäß funktionierende Instanzen weitergeleitet.

## Übersicht über die Features
Der IBM Cloud Load Balancer-Service bietet die folgenden Features:

* Öffentliche Lastausgleichsfunktion (mit Internetverbindung)
	* Über vollständig qualifizierten Domänennamen (FQDN) öffentlich zugänglicher Service
	* Back-End-Serverinstanzen für private Teilnetze
* Interne Lastausgleichsfunktion
	* Über vollständig qualifizierten Domänennamen (FQDN) privat zugänglicher Service
	* Clientanforderungen werden über das private Netz umgeleitet
	* Back-End-Serverinstanzen für private Teilnetze
* Basislastausgleich
	* Verteilung des Datenverkehrs auf der Basis einer Anwendungsportinformation der Ebene 4 (Layer-4)
	* Unterstützung für HTTP-, HTTPS- und TCP-basierte Anwendungen 
	* Vielzahl an Lastausgleichsmethoden, zum Beispiel 'Round Robin' (RR), 'Weighted Round Robin' (WRR) und 'Least Connections'
	* Lastausgleich zwischen virtuellem Server und Bare-Metal-Recheninstanzen, die sich lokal im Rechenzentrum befinden
* Statusprüfungen für Server
	* Periodische Überwachung des Serverstatus, um sicherzustellen, dass der Datenverkehr nur an ordnungsgemäß funktionierende Server weitergeleitet wird 
	* Statusprüfungen der Ebene 4 (Layer-4) für TCP-Ports und Statusprüfungen der Ebene 7 (Layer-7) für HTTP-Port 
* SSL-Auslagerung
	* Terminierung des eingehenden SSL-Verkehrs (HTTPS) mit ungeschützter HTTP-Kommunikation mit Back-End-Servern
* Erweiterte Verwaltung des Datenverkehrs
	* Clientattraktivität (Sitzungspersistenz)
	* Maximale Verbindungen pro virtuellem Port
* Einfache Verwaltung durch intuitive grafische Schnittstelle und API
* Integrierte Zuverlässigkeit 
* Nutzungsorientierte Preisgestaltung 
* Überwachung
    * Überwacht Metriken für Durchsatz, aktive Verbindungen und Verbindungsrate für HTTP-, HTTPS- und TCP-Protokolle über bestimmte Zeitintervalle hinweg. Weitere Details finden Sie unter [Überwachungsmetriken](monitoring-metrics.html).
* Layer 7-Support
    * Der HTTP/HTTPS-Datenverkehr wird basierend auf dem HTTP-Header an verschiedene Back-End-Services weitergeleitet und wird mithilfe von Richtlinien und Regeln verarbeitet. Regeln dienen der Klassifizierung des Datenverkehrs und basieren auf den HTTP-Headerfeldern. Wenn der Datenverkehr mit allen Regeln übereinstimmt, wird eine durch die Richtlinie angegebene Aktion ausgeführt.     
