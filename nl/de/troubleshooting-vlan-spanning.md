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

# Fehlerbehebung beim VLAN-Spanning der Lastausgleichsfunktion
{: #load-balancer-vlan-spanning-troubleshooting}

In diesem Abschnitt finden Sie Informationen zu gängigen Problemen, die auftreten können, wenn sich die Lastausgleichsfunktion und die damit verbundenen Recheninstanzen in unterschiedlichen Teilnetzen befinden. Für die Lastausgleichsfunktion muss VLAN-Spanning aktiviert sein, damit sie mit den Recheninstanzen in einem anderen Teilnetz kommunizieren und Anforderungen an diese weiterleiten kann.

1. Melden Sie sich beim [Kundenportal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com){:new_window} an, navigieren Sie zu **Netz > IP-Verwaltung** und klicken Sie dann auf **VLANs**.

2. Schalten Sie das **VLAN-Spanning** **ein**.

<img src="images/vlan-spanning.png" alt="Zeichnung" style="width: 500px;"/>

Dadurch wird die Kommunikation zwischen der Lastausgleichsfunktion und den zugehörigen Recheninstanzen geöffnet.
