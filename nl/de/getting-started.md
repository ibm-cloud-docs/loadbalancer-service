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


# Einführung in IBM Cloud Load Balancer
{: #getting-started-with-ibm-cloud-load-balancer}

Für den Einstieg in die Verwendung von IBM© Cloud Load Balancer benötigen Sie zwei Dinge:

* Ein Konto bei IBM: [IBMid ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* Einen IBM Server, entweder einen [Bare-Metal-Server](/docs/bare-metal?topic=bare-metal-about) oder eine [virtuelle Serverinstanz (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers#getting-started-with-virtual-servers).

Falls Sie Unterstützung bei der Beschaffung eines Kontos mit **IBMid** benötigen, setzen Sie sich mit Ihrem [IBM Vertriebsbeauftragten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} in Verbindung.

Falls Sie bereits über ein vorhandenes Konto für die IBM Cloud-Infrastruktur (SoftLayer) verfügen, können Sie Ihre IBMid [mit Ihrem Konto verknüpfen](/docs/account?topic=account-unifyingaccounts).

## Lastausgleichsfunktion bestellen

Wählen Sie zum Bestellen des IBM Cloud Load Balancer-Service **Netz > Lastausgleichsfunktionen > IBM Cloud Load Balancer** im [IBM Cloud-Katalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/infrastructure/load-balancer-group){:new_window} aus. Melden Sie sich an oder erstellen Sie ein neues Konto, und führen Sie anschließend die folgende Prozedur aus:

1. Wählen Sie Ihr Rechenzentrum aus und überprüfen Sie den Serviceplan. Klicken Sie auf **Weiter**.
2. Wählen Sie das Teilnetz aus, in dem Sie die Lastausgleichsfunktion bereitstellen möchten. Die Instanz des Service für die Lastausgleichsfunktion verfügt über eine der Netzschnittstellen in diesem Teilnetz. Stellen Sie sicher, dass die Anwendungsserver entweder in diesem Teilnetz oder aus diesem Teilnetz erreichbar sind. Aktivieren Sie bei Bedarf das VLAN-Spanning. Klicken Sie auf **Weiter**.
3. Definieren Sie die Basisserviceparameter, wie zum Beispiel Name, Beschreibung, Protokolle und Ports für Front-End- und Back-End-Anwendungen oder die Lastausgleichsmethode. 

	Während der erstmaligen Serviceerstellung können Sie maximal zwei Protokolle definieren. Sie können bis zu zehn Protokolle definieren, wenn der Service erstellt ist. Sie müssen auch einen eindeutigen Front-End-Port verwenden. 
	
	Wenn Sie damit fertig sind, klicken Sie auf **Weiter**.
	
4. Passen Sie bei Bedarf die Parameter für die Statusprüfung an; verwenden Sie andernfalls die Standardeinstellungen. Klicken Sie auf **Weiter**.
5. Ordnen Sie mindestens eine Serverinstanz hinter der Lastausgleichsfunktion zu. Es werden nur Serverinstanzen angezeigt, die sich lokal im Rechenzentrum befinden. Klicken Sie auf **Weiter**.
6. Überprüfen Sie die Übersichtsseite und klicken Sie auf **Erstellen**.

	Auf der Übersichtsseite wird die Instanz des Service für die Lastausgleichsfunktion angezeigt, die Sie soeben erstellt haben. Beachten Sie das Feld **Status**. Die Statusangabe `Offline` gibt an, dass die Lastausgleichsfunktion nicht aktiv ist. Es können erst neue Konfigurationen vorgenommen und ein Service für die Lastausgleichsfunktion bereitgestellt werden, wenn sich der Status in `Online` geändert hat. Möglicherweise müssen Sie die Anzeige aktualisieren, um den aktuellen Status anzuzeigen.

	Wenn Sie auf den Servicenamen auf dieser Seite klicken, wechseln Sie zur Übersichtsseite des Service. Sie können zu den Registerkarten **Protokolle**, **Statusprüfungen** und **Serverinstanzen** navigieren, um die Ihre Konfiguration weiter zu bearbeiten.

Eine schrittweisen Konfigurationsanleitung feinden Sie unter [Vorgehensweise zum Erstellen und Verwenden einer IBM Cloud Load Balancer-Instanz für einen elastischen Serverlastausgleich](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing).
