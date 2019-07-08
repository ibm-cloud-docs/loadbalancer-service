---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: about, load balancer, overview, features

subcollection: loadbalancer-service

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

# A propos de l'équilibreur de charge IBM Cloud Load Balancer
{: #about-ibm-cloud-load-balancer}

Le service IBM© Cloud Load Balancer aide les clients à améliorer la disponibilité des applications critiques pour l'activité de leur entreprise en répartissant le trafic entre plusieurs instances de serveur et en réacheminant le trafic vers des instances viables seulement.

## Présentation des fonctionnalités
{: #overview-of-features}

Le service IBM Cloud Load Balancer offre les fonctionnalités suivantes :

* Equilibreur de charge public (Internet)
	* Service accessible au public via son nom de domaine complet
	* Instances de serveur de back end sur des sous-réseaux privés
* Equilibreur de charge interne
	* Service accessible en privé via son nom de domaine complet
	* Demandes client acheminées sur le réseau privé
	* Instances de serveur de back end sur des sous-réseaux privés
* Equilibrage de charge de base
	* Répartition du trafic basée sur les informations du port d'application à 4 couches
	* Support des applications HTTP, HTTPS et TCP
	* Large choix de méthodes d'équilibrage de charge, par exemple, le mode circulaire, le mode circulaire pondéré et le nombre minimal de connexions
	* Equilibrage de charge entre le serveur virtuel et les instances de calcul bare metal installé localement dans un centre de données
* Diagnostics d'intégrité du serveur
	* Surveillance périodique de la santé du serveur afin de garantir le transfert du trafic vers des serveurs sains uniquement
	* Diagnostics d'intégrité à 4 couches pour les ports TCP et 7 couches pour les ports HTTP
* Déchargement SSL
	* Arrêt du trafic SSL entrant (HTTPS) à l'aide d'une communication HTTP en texte en clair avec les serveurs de back end
* Gestion de trafic avancée
	* Adhésion client (persistance de session)
	* Nombre de connexions maximum par port virtuel
* Gestion aisée grâce à une interface graphique et une interface de programmation intuitives
* Fiabilité intégrée
* Tarification basée sur l'utilisation
* Surveillance
    * Surveille les métriques Débit, Connexions actives et Taux de connexion pour les protocoles HTTP, HTTPS et TCP au cours des intervalles de temps spécifiés par l'utilisateur. Pour plus d'informations, voir [Métriques de surveillance](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer).
* Prise en charge de couche 7
    * Le trafic HTTP/HTTPS est acheminé vers différents services de back end sur l'en-tête HTTP, à l'aide de politiques et de règles. Les règles sont utilisées pour classifier le trafic et sont basés sur les zones d'en-tête HTTP. Lorsque le trafic correspond à toutes les règles, une action spécifiée par la politique est exécutée.
* Prise en charge de MZR (Multi-Zone Region)
    * Les noeuds de l'équilibreur de charge sont instanciés dans différents centres de données d'une région multizone (MZR). Pour plus d'informations, voir [Présentation de MZR (Multi-Zone Region)](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).
* Journaux de données
    * Lorsque les journaux de données sont activés, les journaux de l'équilibreur de charge sont transmis au [service IBM Cloud Log Analysis ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}. Les clients peuvent consulter leurs journaux de données via le [service IBM Cloud Log Analysis![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}.
