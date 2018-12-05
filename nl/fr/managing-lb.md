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

# Surveillance et gestion de votre service
Vous pouvez éditer votre configuration ou surveiller les performances de votre service en cliquant sur l'URL de nom de service sur la page de récapitulatif de l'équilibreur de charge.  

L'**adresse de nom de domaine complet** de votre instance de service d'équilibreur de charge se trouve juste au-dessous du nom de service. Vos utilisateurs finaux peuvent se connecter à votre application via cette adresse de nom de domaine complet. Notez que les adresses IP publiques et privée du service d'équilibreur de charge ne sont pas exposées au monde extérieur ; seule l'adresse de nom de domaine complet est exposée.  

<img src="images/fqdn-address.png" alt="drawing" style="width: 300px;"/>

L'onglet **Présentation** fournit des informations d'état de haut niveau concernant votre service. Il affiche l'état actuel de vos serveurs d'application et de leurs ports. Il contient également un bref récapitulatif des performances du système (débit, taux de connexion, connexions simultanées, etc.) . 

Accédez à l'onglet **Surveillance** pour visualiser les graphiques en temps réel des performances de votre système. Ces graphiques peuvent être visualisés par port d'application et pour différentes durées.  

<img src="images/monitor-lb.png" alt="drawing" style="width: 300px;"/>

Vous pouvez éditer votre configuration existante en accédant aux onglets **Protocoles**, **Instances de serveur** et **Diagnostics d'intégrité**. Par exemple, accédez à l'onglet Protocoles pour définir d'autres ports d'application ou pour personnaliser la liste de chiffrements SSL.  

<img src="images/protocols-monitor.png" alt="drawing" style="width: 300px;"/>
