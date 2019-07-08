---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: vlan, troubleshooting, problems, questions

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Traitement des incidents liés au spanning VLAN d'équilibreur de charge
{: #load-balancer-vlan-spanning-troubleshooting}

Cette rubrique fournit des informations sur les problèmes qui peuvent se produire couramment lorsque l'équilibreur de charge et les instances de calcul qui lui sont connectées se trouvent dans des sous-réseaux différents. Le spanning VLAN doit être activé pour que l'équilibreur de charge puisse communiquer et envoyer des demandes aux instances de calcul qui se trouvent sur un autre sous-réseau.

1. Connectez-vous au [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com){:new_window}, accédez à **Réseau > Gestion IP**, puis cliquez sur **VLAN**.

2. Activez **Spanning VLAN** (**On**).

<img src="images/vlan-spanning.png" alt="drawing" style="width: 500px;"/>

Cela ouvre la communication entre l'équilibreur de charge et ses instances de calcul.
