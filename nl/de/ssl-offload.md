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

# SSL-Auslagerung mit IBM Cloud Load Balancer
{: #ssl-offload-with-ibm-cloud-load-balancer}

Für alle ankommenden HTTPS-Verbindungen beendet die Lastausgleichsfunktion die SSL-Verbindung und baut eine ungeschützte HTTP-Kommunikation mit dem Back-End-Server auf. CPU-intensive SSL-Handshakes sowie Verschlüsselungs- und Entschlüsselungstasks werden von den Back-End-Servern ausgelagert, sodass sie alle CPU-Zyklen für die Verarbeitung des Anwendungsdatenverkehrs verwenden können. 

Ein SSL-Zertifikat ist erforderlich, damit von der Lastausgleichsfunktion SSL-Auslagerungstasks durchgeführt werden können. Sie können ein bereits vorhandenes SSL-Zertifikat verwenden oder ein neues kaufen und dieses über den [IBM© Cloud-Zertifikatsspeicher ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com/security/sslcerts){:new_window} verwalten. 

## SSL-Cipher-Suites
Von der Lastausgleichsfunktion wird TLS 1.2 mit SSL-Auslagerung unterstützt.

Von der Lastausgleichsfunktion werden folgende SSL-Verschlüsselungen unterstützt:

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

Wenn für die Lastausgleichsfunktion mindestens ein HTTPS-Front-End-Anwendungsport (Protokoll) konfiguriert ist, sind standardmäßig alle oben vordefinierten SSL-Verschlüsselungen für die Lastausgleichsfunktion aktiviert. 

**HINWEIS:** Sie können bei Bedarf auch andere SSL-Verschlüsselungen für die Lastausgleichsfunktion aktivieren. Weitere Informationen finden Sie unter [Bevorzugte Cipher-Suite für Ihre HTTPS-Anwendung auswählen](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application).
