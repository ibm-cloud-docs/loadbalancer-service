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

# Statusprüfungen mit IBM Cloud Load Balancer durchführen
{: #performing-health-checks-with-ibm-cloud-load-balancer}

Die Definitionen der Statusprüfungen sind für jeden der Back-End-Anwendungsports obligatorisch. Der Port und das Protokoll, die in der Konfiguration für die Statusprüfung definiert sind, müssen mit dem definierten Back-End-Port und -Protokoll identisch sein; andernfalls wird die Konfiguration abgelehnt. 

Von der Lastausgleichsfunktion werden regelmäßige Statusprüfungen zur Überwachung des Status der Back-End-Ports ausgeführt und der Clientdatenverkehr wird entsprechend an diese weitergeleitet. Wenn festgestellt wird, dass der Port eines bestimmten Back-End-Servers nicht ordnungsgemäß funktioniert, werden keine neuen Verbindungen an diesen Port weitergeleitet. Der Status dieser nicht ordnungsgemäß funktionierenden Ports wird von der Lastausgleichsfunktion weiterhin überwacht; ein solcher Port wird wieder verwendet, wenn durch das erfolgreiche Übergeben von zwei aufeinander folgenden Statusprüfungsversuchen festgestellt wird, dass der Port wieder ordnungsgemäß funktioniert. 

Statusprüfungen für HTTP- und TCP-Ports werden wie folgt ausgeführt:

* **HTTP:** Eine Anforderung des Typs `HTTP GET` für eine vorab angegebene URL wird an den Back-End-Server-Port gesendet. Der Server-Port wird beim Empfang der Antwort `200 OK` als ordnungsgemäß funktionierend markiert. Der Standardwert für die `GET`-URL in der grafischen Benutzerschnittstelle ist '/' und kann angepasst werden. 

* **TCP:** Von der Lastausgleichsfunktion wird versucht, eine TCP-Verbindung mit dem Back-End-Server an einem bestimmten TCP-Port zu öffnen. Der Server-Port wird als ordnungsgemäß funktionierend markiert, wenn die Verbindung erfolgreich ist; die Verbindung wird anschließend geschlossen. 

	**HINWEIS:** Der Standardwert für das Statusprüfungsintervall beträgt 5 Sekunden, das Standardzeitlimit für eine Statusprüfungsanforderung beträgt 2 Sekunden und die Standardanzahl für die Anzahl der Wiederholungen beträgt 2 Wiederholungen. 
