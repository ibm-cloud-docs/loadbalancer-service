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

# Fehlerbehebung bei der Bereitstellung der Lastausgleichsfunktion
{: #load-balancer-provisioning-troubleshooting}

In diesem Abschnitt finden Sie Informationen zu gängigen Problemen, die beim Erstellen einer Instanz von IBM© Cloud Load Balancer auftreten können. 

## Unzureichend IP-Adressen in Ihrem Teilnetz
IBM Cloud Load Balancer erfordert mindestens zwei freie IP-Adressen in seinem privaten Teilnetz. Darüber hinaus werden auch aus Ihrem öffentlichen Teilnetz mindestens zwei freie IP-Adressen benötigt, wenn die Lastausgleichsfunktion eine öffentliche Lastausgleichsfunktion ist und wenn die Option **IBM Systempool** nicht verwendet wird. 

Führen Sie die folgenden Schritte aus, um nach freien IPs in einem Teilnetz zu suchen.

1. Öffnen Sie das [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com){:new_window} und navigieren Sie zum Abschnitt mit den Teilnetzen, indem Sie **Netz > IP-Verwaltung > Teilnetze** auswählen.

2. Klicken Sie auf das Teilnetz, in dem Sie nach freien IPs suchen möchten.

	<img src="images/subnet_list.png" alt="Zeichnung" style="width: 600px;"/>
		
3. Die Detailseite für das ausgewählte Teilnetz zeigt den Status aller IPs in diesem Teilnetz an.

## Probleme mit Firewalls in öffentlichen und privaten VLANs
Informationen zum Zulassen von IP-Bereichen in der Firewall finden Sie unter [IBM Cloud-IP-Bereiche](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges).
 
## Fehlernachrichten der Lastausgleichsfunktion anzeigen
Gehen Sie wie folgt vor, um Fehlernachrichten für Ihre Lastausgleichsfunktion anzuzeigen:

1. Klicken Sie auf der Listenseite auf die Lastausgleichsfunktion, um die zugehörigen Details anzuzeigen. 
2. Berühren Sie mit dem Mauscursor das Fehlersymbol neben dem Status der Lastausgleichsfunktion.

<img src="images/lbaas_error_message.png" alt="Zeichnung" style="width: 500px;"/>

Wenn die Lastausgleichsfunktion den Status `FEHLER` hat, kann sie nicht wiederhergestellt werden und muss gelöscht werden.
