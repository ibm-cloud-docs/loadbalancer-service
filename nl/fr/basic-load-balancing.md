---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: basics, load balancing

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

# Notions de base d'exécution de l'équilibreur de charge {{site.data.keyword.loadbalancer_full}}
{: #performing-ibm-cloud-load-balancer-basics}

Le service {{site.data.keyword.loadbalancer_full}} répartit le trafic entre plusieurs instances de serveurs (bare metal et virtuel) installées en local, au sein du même centre de données.

## Equilibreur de charge public
{: #public-load-balancer}

Un nom de domaine complet, accessible publiquement, est affecté à votre instance de service d'équilibreur de charge. Vous devez utiliser ce nom de domaine pour accéder à vos applications hébergées derrière le service Load Balancer. Vous pouvez enregistrer ce nom de domaine avec une ou plusieurs adresses IP publiques. Les adresses IP publiques et le nombre d'adresses IP publiques peuvent évoluer au fil du temps en fonction des activités de maintenance et de mise à l'échelle, qui sont transparentes pour l'utilisateur final. Les instances de calcul de back end qui hébergent votre application doivent être installées sur un réseau privé IBM Cloud.

Nous vous recommandons d'utiliser vos serveurs de back au format "privé uniquement" à moins que ceux-ci ne requièrent une connectivité publique directe. Cette pratique aide à obtenir une meilleure sécurité et conserve votre adresse IP publique. Les applications hébergées sur ces serveurs de back end restent accessibles sur le réseau public par le biais de l'équilibreur de charge.
{: note}  

Vous pouvez choisir d'allouer des adresses IP publiques d'équilibrage de charge à partir d'un pool de systèmes IBM (par défaut) ou d'un VLAN public de votre compte lors de la création de votre instance d'équilibrage de charge.

## Equilibreur de charge interne
{: #internal-load-balancer}

L'équilibreur de charge interne n'est accessible que dans le réseau privé IBM Cloud.

Comme pour un équilibreur de charge public, votre instance de service d'équilibreur de charge interne se voit également affecter un nom de domaine complet. Toutefois, ce nom de domaine est enregistré avec une ou plusieurs adresses IP publiques.

Comme pour un équilibreur de charge public, les adresses IP privées et leur nombre peuvent évoluer au fil du temps en fonction des activités de maintenance et de mise à l'échelle, qui sont transparentes pour l'utilisateur final.

Les instances de calcul de back end qui hébergent votre application doivent également figurer sur le réseau privé IBM Cloud.
{: note}

## Ports/protocoles d'applications de front end et de back end
{: #front-end-and-back-end-application-ports-protocols}

Vous pouvez choisir jusqu'à dix ports (protocoles) d'applications de front end et les mapper à leurs ports (protocoles) respectifs sur les serveurs d'applications de back end. Le nom de domaine complet qui est affecté à votre instance de service Load Balancer et les ports d'applications de front end sont exposés au monde extérieur. Les demandes d'utilisateur entrantes sont reçues sur ces ports.

En revanche, les ports de back end ne sont connus qu'en interne. Les ports de back end peuvent être, ou non, identiques à ceux de front end. Par exemple, l'équilibreur de charge peut être configuré de manière à recevoir le trafic HTTP/web entrant sur le port de front end 80, tandis que les serveurs de back end écoutent sur le port personnalisé 81.

Les ports/protocoles de front end pris en charge sont HTTP, HTTPS et TCP. Les ports/protocoles de back end pris en charge sont également HTTP, HTTPS et TCP. Le trafic HTTP entrant doit être arrêté au niveau de l'équilibreur de charge pour autoriser la communication HTTP en texte en clair avec le serveur de back end. Si le protocole de back end est HTTPS, le trafic sera chiffré entre l'équilibreur de charge et les serveurs de back end.

### Remarques
{: #considerations}

* Lors de la configuration initiale, vous pouvez définir jusqu'à deux ports de front end. Lorsqu'un équilibreur de charge a été créé, vous pouvez modifier la configuration du port de manière à définir des ports supplémentaires, dans la limite de dix.
* Les dix ports de front end doivent être mappés au même ensemble d'instances de serveurs de back end.
* Le nombre maximal d'instances de serveurs pouvant être placées derrière un équilibreur de charge est 50.
* La plage de ports comprise entre 56500 et 56520 est réservée à des fins de gestion et ne peut pas être utilisée comme valeurs de ports de front end.
* Le port TCP 56501 est utilisé à des fins de gestion. Si vous choisissez d'allouer des adresses IP publiques d'équilibreur de charge à partir de votre VLAN public, assurez-vous que le trafic vers ce port de gestion et les ports de l'application ne sont pas bloqués par des pare-feux déployés sur vos réseaux locaux virtuels (VLAN). Cela est inutile si vous choisissez l'option Pool de systèmes IBM pour allouer les adresses IP publiques d'équilibrage de charge.

## Méthodes d'équilibrage de charge
{: #load-balancing-methods}

Les trois méthodes d'équilibrage de charge ci-dessous peuvent être utilisées pour répartir le trafic entre les serveurs d'applications de back end :

* **Round Robin :** Il s'agit de la méthode d'équilibrage de charge par défaut. Avec cette méthode, l'équilibreur de charge achemine les connexions client entrantes de façon circulaire vers les serveurs de back end. Chaque serveur de back end reçoit ainsi un nombre équivalent de connexions client.

* **Round Robin Pondéré :** Avec cette méthode, l'équilibreur de charge achemine les connexions client entrantes vers les serveurs de back end au prorata du nombre de connexions affectées à ces serveurs. Chaque serveur reçoit une pondération par défaut de 50 connexions, qui peut être personnalisée sur n'importe quelle valeur comprise entre 0 et 100.

	Prenons l'exemple de trois serveurs d'applications A, B et C dont la pondération a été définie sur 60, 60 et 30. Les serveurs A et B reçoivent le même nombre de connexions tandis que le serveur C en reçoit moitié moins.


	Le fait de redéfinir la pondération d'un serveur sur la valeur ‘0’ signifie qu'aucune nouvelle connexion n'est acheminée vers ce serveur, mais que le trafic existant continue à circuler tant qu'il reste actif. Une pondération ‘0’ peut aider à arrêter naturellement un serveur et à le retirer de la rotation de service.
	{: note}

	Les valeurs de pondération des serveurs ne sont applicables qu'avec la méthode "Round Robin Pondéré". Elles sont ignorées avec les méthodes d'équilibrage de charge "Round Robin" et "Connexions minimum".
	{: note}

* **Connexions minimum :** Avec cette méthode, l'instance de serveur qui prend en charge le plus petit nombre de connexions, à un moment donné, reçoit la connexion suivante.

## Mise à l'échelle horizontale
{: #horizontal-scaling}

L'équilibreur de charge ajuste automatiquement sa capacité en fonction de la charge. Lorsque cela se produit, vous pouvez remarquer un changement au niveau du nombre d'adresses IP associées au nom DNS de l'équilibreur de charge.
