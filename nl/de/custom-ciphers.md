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

# Bevorzugte Cipher-Suite für Ihre HTTPS-Anwendung auswählen
{: #choosing-a-preferred-cipher-suite-for-your-https-application}

Verschlüsselungsalgorithmen, die {{site.data.keyword.loadbalancer_full}} beim Erstellen sicherer Verbindungen mit den zugehörigen HTTP-Clients unterstützen. 

IBM bietet ein Portfolio von genehmigten Verschlüsselungen an, aus dem Sie auswählen können, um die Kommunikation zwischen Ihrer Lastausgleichsfunktion und Ihren Clients zu sichern.

Sie können eine bevorzugte Cipher-Suite für eine vorhandene Lastausgleichsfunktion auswählen oder sie zuordnen, wenn Sie eine neue Lastausgleichsfunktion erstellen. 

## Verschlüsselungen für eine vorhandene Lastausgleichsfunktion auswählen
Um eine Cipher-Suite-Konfiguration für eine vorhandene Lastausgleichsfunktion auszuwählen, navigieren Sie zur Anzeige Ihrer Lastausgleichsfunktion im Kundenportal und klicken Sie auf die Registerkarte 'Protokolle'.  Wenn HTTPS nicht als Front-End-Protokoll ausgewählt ist, wird die Liste der Cipher-Suites nicht angezeigt.

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="Zeichnung" style="width: 700px;"/>
  
Wählen Sie HTTPS als Ihr Front-End-Protokoll aus, und die verfügbaren Cipher-Suites werden unter den Details zu der Lastausgleichsfunktion angezeigt. 

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="Zeichnung" style="width: 600px;"/>
  
Die Tabelle mit den Verschlüsselungen kann bearbeitet werden, und Sie können Ihre gewünschten Cipher-Suites für den SSL-Handshake auswählen. Klicken Sie auf **Bearbeiten**, wählen Sie die Verschlüsselungen aus, die Sie implementieren möchten, und klicken Sie auf **Speichern**.
  
**HINWEIS:** Eine Liste der unterstützten Verschlüsselungen finden Sie unter [SSL-Auslagerung](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).

## Verschlüsselungen beim Erstellen einer neuen Lastausgleichsfunktion auswählen

Gehen Sie wie folgt vor, um die Cipher-Suite auszuwählen, wenn Sie eine neue Lastausgleichsfunktion erstellen:

1. Befolgen Sie die Anweisungen zum [Erstellen einer Lastausgleichsfunktion](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-an-ibm-cloud-load-balancer#creating-an-ibm-cloud-load-balancer).
  
2. Die Cipher-Suite-Konfiguration ist nur mit dem HTTPS-Front-End-Protokoll anwendbar. Wenn Sie zu den Konfigurationsschritten im Abschnitt **Protokoll hinzufügen** kommen, wählen Sie **HTTPS-Protokoll** aus.

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="Zeichnung" style="width: 500px;"/>
  
3. Eine Standardgruppe von Verschlüsselungen ist bereits in der Konfiguration ausgewählt, aber Sie können sie erst bearbeiten, wenn Sie die Konfiguration der Lastausgleichsfunktion abgeschlossen haben. 
  
	Schließen Sie die Konfiguration der Lastausgleichsfunktion entsprechend den Anweisungen ab. Sobald das geschehen ist, können Sie die Liste mit Standardverschlüsselungen auf der Registerkarte **Protokolle** unter den **Details zu Lastausgleichsfunktion** sehen.

	<img src="images/View-CustomCiphers.png" alt="Zeichnung" style="width: 600px;"/>
  
4. Die Tabelle mit den Verschlüsselungen kann bearbeitet werden, und Sie können Ihre gewünschten Cipher-Suites für den SSL-Handshake auswählen. Klicken Sie auf **Bearbeiten**, wählen Sie die Verschlüsselungen aus, die Sie implementieren möchten, und klicken Sie auf **Speichern**.
	
	**HINWEIS:** Eine Liste der unterstützten Verschlüsselungen finden Sie unter [SSL-Auslagerung](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).
