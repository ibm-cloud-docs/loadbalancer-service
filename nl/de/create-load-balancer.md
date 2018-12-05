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

# IBM Cloud Load Balancer erstellen
Gehen Sie wie folgt vor, um einen IBM Cloud Load Balancer-Service zu erstellen: 

1. Öffnen Sie im Browser das [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com/){: new_window} und melden Sie sich an Ihrem Konto an.

2. Klicken Sie auf **Katalog** und navigieren Sie dann im Abschnitt 'Infrastruktur' zu **Netz > Load Balancer-Services**. 

	<img src="images/catalog-load-balancer.png" alt="Zeichnung" style="width: 600px;"/>

3. Wählen Sie **IBM Cloud Load Balancer** (Standardauswahl) aus und klicken Sie auf **Erstellen**.  

	Wenn statt **Erstellen** die Option **Upgrade** angezeigt wird, müssen Sie Ihr IBM Cloud Infrastructure-Konto (Softlayer) verknüpfen, indem Sie [diese Schritte ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/account/softlayerlink.html#link_customer_accounts) ausführen. 

	<img src="images/create-load-balancer.png" alt="Zeichnung" style="width: 600px;"/>

4. Wählen Sie Ihr bevorzugtes Rechenzentrum im Dropdown **Rechenzentrum** aus, überprüfen Sie die Informationen und klicken Sie dann auf **Weiter**. 

	<img src="images/select-datacenter.png" alt="Zeichnung" style="width: 600px;"/>

5. Geben Sie den Typ Ihrer Lastausgleichsfunktion an. 

	Für mit dem Internet verbundene Anwendungen, die Zugriff auf das öffentliche Internet benötigen, wählen Sie **Öffentlich (mit Internetverbindung)** aus. 

	<img src="images/select-lb-type.png" alt="Zeichnung" style="width: 600px;"/>
	
	Standardmäßig empfängt die öffentliche Lastausgleichsfunktion eine global eindeutige öffentliche IP-Adresse aus dem globalen IBM Adressenpool. Wenn Sie ihr jedoch öffentliche Adressen aus Ihrem eigenen Adressenpool zuweisen oder die hinter einem Firewall-Service in Ihrem Konto bereitstellen möchten, prüfen Sie, ob Ihr öffentliches Teilnetz über [ausreichend IP-Adressen](troubleshooting-provisioning.html) verfügt, und wählen Sie **Aus öffentlichem Teilnetz in Ihrem Konto zuordnen** aus. 

	Für interne Anwendungen, die keinen Zugriff auf das öffentliche Internet benötigen, wählen Sie den Typ **Intern (privat)** aus. 

	<img src="images/lb-type-private.png" alt="Zeichnung" style="width: 500px;"/>

	Wählen Sie sowohl für mit dem Internet verbundene als auch für interne Lastausgleichsfunktionen eines der privaten Teilnetze in dem Konto aus, in dem Sie Ihre Lastausgleichsfunktion bereitstellen möchten. Ihre Anwendungsserver müssen aus diesem Teilnetz erreichbar sein. Aktivieren Sie bei Bedarf VLAN-Spanning, um die entsprechende Netzkonnektivität sicherzustellen. 

	Wenn Sie keine privaten Teilnetze sehen, klicken Sie auf **Zurück** und wählen Sie dann ein anderes Rechenzentrum mit privaten Teilnetzen aus. 

6. Klicken Sie auf **Weiter**, um die Konfiguration fertigzustellen. 

## Weitere Schritte
Konfigurieren Sie Ihre Lastausgleichsfunktion mit [Basisparametern](begin-lb-config.html). 
