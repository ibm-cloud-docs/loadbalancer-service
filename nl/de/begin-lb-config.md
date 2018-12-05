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

# IBM Cloud Load Balancer-Parameter konfigurieren
Nachdem Sie eine Lastausgleichsfunktion erstellt haben, können Sie sie für den elastischen Lastausgleich konfigurieren. Gehen Sie dazu wie folgt vor: 

1. Benennen Sie Ihre Lastausgleichsfunktion und fügen Sie optional eine Beschreibung hinzu. 

	<img src="images/lb-config-basic.png" alt="Zeichnung" style="width: 300px;"/>

2. Geben Sie die Details Ihres Anwendungsprofils ein, indem Sie die Protokolle und Ports, an denen Ihre Anwendung empfangsbereit ist, angeben. Sie können dieselbe Konfiguration sowohl für das Front-End als auch für das Back-End verwenden oder einen anderen Front-End-Port bereitstellen (z. B. aus Sicherheitsgründen). 

3. Die Standardmethode für den Lastausgleich ist **Round Robin**. Sie können dies in der Dropdown-Liste zu **Weighted Round Robin** oder **Least Connections** ändern, abhängig von Ihren Anwendungsanforderungen. 

4. Optional können Sie die **Sitzungsattraktivität** aktivieren. Ist diese Option aktiviert, werden alle Anforderungen eines bestimmten Endbenutzers (z. B. einem mit derselben Quellen-IP) für einen im System definierten Zeitraum an denselben Back-End-Server geleitet. 

5. Sie können für Ihre Anwendung auch ein **Maximales Verbindungslimit** festlegen. 

6. Klicken Sie auf **Protokoll hinzufügen**, um zusätzliche Protokolle und Ports, an denen Ihre Anwendung empfangsbereit sein könnte, anzugeben. Stellen Sie sicher, dass alle Front-End-Ports eindeutig sind. Sie können HTTP, HTTPS oder TCP als Front-End-Protokoll auswählen.  

	<img src="images/lb-add-protocol.png" alt="Zeichnung" style="width: 300px;"/>

	Es können maximal 2 Ports zum Zeitpunkt der Erstkonfiguration definiert werden. Weitere Ports können später hinzugefügt werden, nachdem die Serviceinstanz erstellt wurde. Weitere Informationen zur maximal zulässigen Anzahl von Ports finden Sie unter [Limits für die Anzahl von Ports](faqs.html#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-). {:note:}

7. Der IBM Cloud Load Balancer beendet eingehende HTTPS-Verbindungen (HTTP over SSL), kommuniziert in Klartext-HTTP mit den Back-End-Anwendungsservern und lagert prozessorintensive SSL-Tasks von Ihren Servern aus. Sie müssen Ihr SSL-Zertifikat hochladen. Wählen Sie in der Dropdown-Liste eines Ihrer verfügbaren Zertifikate aus.   

	<img src="images/lb-ssl-cert.png" alt="Zeichnung" style="width: 300px;"/>

	Wenn Sie über kein Zertifikat verfügen, klicken Sie auf **Neues Zertifikat hinzufügen**. Sie werden an einen IBM Cloud-Zertifikatsservice weitergeleitet, wo Sie entweder ein neues Zertifikat erwerben oder ein vorhandenes Zertifikat hochladen können. 
	
	Nachdem Sie das Zertifikat hinzugefügt haben, kehren Sie zur Konfigurationsseite der Lastausgleichsfunktion zurück und klicken auf das Aktualisierungssymbol unter der Dropdown-Liste 'SSL-Zertifikat', um das neu hochgeladene Zertifikat anzuzeigen und hinzuzufügen. 

	<img src="images/order-ssl-cert.png" alt="Zeichnung" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="Zeichnung" style="width: 300px;"/>

	**HINWEIS**: Löschen Sie niemals Zertifikate, die HTTPS-Listenern zugeordnet sind, da dies zu Funktionalitätsproblemen führen kann. 

8. Klicken Sie auf **Weiter**.

## Statusprüfungen konfigurieren
Die Konfiguration von Statusprüfungen ist für jeden Anwendungsport obligatorisch. Dies sind die Back-End-Ports, die im vorherigen Basiskonfigurationsmenü angegeben wurden. 

<img src="images/config-health-check.png" alt="Zeichnung" style="width: 300px;"/>

Das System füllt eine Standardkonfiguration für die Statusprüfung für diese Back-End-Ports aus. Sie können diese Einstellungen an Ihre Anwendungsanforderungen anpassen. 

* **Intervall**: Intervall in Sekunden zwischen zwei aufeinander folgenden Statusprüfungsversuchen. 
* **Zeitlimit**: Maximale Zeit, während der das System auf eine Antwort für eine Anforderung einer Statusprüfung wartet. 
* **Max. Versuche**: Maximale Anzahl zusätzlicher Statusprüfungsversuche, die das System ausführt, bevor ein Port als fehlerhaft deklariert wird. 
* **Pfad**: Der HTTP-URL-Pfad für die Statusprüfung.      

Klicken Sie auf **Weiter**, um Ihre Auswahl zu aktivieren. 

## Weitere Schritte
[Geben Sie Ihre Anwendungsressourcen an](identify-app-resources.html), z. B. Ursprungspools und Mechanismen für die Statusprüfung. 
