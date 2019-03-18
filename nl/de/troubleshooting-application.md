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

# Fehlerbehebung für den Anwendungsserver
{: #application-server-troubleshooting}

In diesem Abschnitt finden Sie Informationen zu gängigen Problemen, die beim Verwenden der Lastausgleichsfunktion auftreten können.

## Der Back-End-Server ist fehlerhaft.
Wenn der Status Ihres Back-End-Servers fehlerhaft ist, arbeiten Sie die folgende Liste ab, um dies zu beheben:

* Stimmt der Port des konfigurierten Back-End-Protokolls mit dem Port überein, an dem Ihre Anwendung empfangsbereit ist?
* Hat die konfigurierte Statusprüfung die richtigen Informationen zu Protokoll (TCP oder HTTP), Port und URL (für HTTP)? Stellen Sie für HTTP sicher, dass Ihre Anwendung mit `200 OK` für die konfigurierte Statusprüfungs-URL antwortet.
* Befindet sich der Back-End-Server in einem anderen Teilnetz als die Lastausgleichsfunktion? Ist dies nicht der Fall, stellen Sie sicher, dass das VLAN-Spanning aktiviert ist.
* Ist der Back-End-Server ein virtueller Server mit einer aktivierten Sicherheitsgruppe? Ist dies der Fall, stellen Sie sicher, dass die Sicherheitsgruppenregeln Datenverkehr zwischen der Lastausgleichsfunktion und dem virtuellen Server zulassen.
