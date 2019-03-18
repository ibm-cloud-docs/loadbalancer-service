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

# Pool de couche 7
{: #layer-7-pool}

Un pool de couche 7 (L7) est un groupement logique de serveurs (membres) dédié au traitement de demandes entrantes.

La fonction d'équilibrage de charge de couche 7 peut diriger le trafic entrant vers différents pools de back end en fonction des politiques et des règles. Cette fonction est prise en charge en associant plusieurs pools L7 à un équilibreur de charge. Les pools de couche 7 sont utilisés avec les politiques de couche 7 dont l'action consiste à `rediriger vers un pool`.

Les pools L7 ne prennent en charge que HTTP comme protocole de back end.

## Persistance de session
La persistance de session peut être configurée pour chaque pool de couche 7. Pour plus d'informations, voir la  
[section sur le trafic avancé](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer).

## Membres de couche 7

Les serveurs de back end qui sont associés à un pool de couche 7 sont appelés membres de couche 7.

Le même serveur de back end peut être ajouté plusieurs fois à des pools L7, en spécifiant un numéro de port différent à chaque fois.

## Configuration des diagnostics d'intégrité
La définition de diagnostic d'intégrité est obligatoire pour chaque pool de couche 7. Le système préremplit une configuration de diagnostic d'intégrité par défaut pour les pools L7.

Vous pouvez personnaliser ces paramètres en fonction des besoins de votre application :

 * **Interval** : Intervalle exprimé en secondes entre deux tentatives de diagnostic d'intégrité consécutives
 * **Timeout** : Durée maximale pendant laquelle le système attend une réponse à une demande de diagnostic d'intégrité
 * **MaxRetries** : Nombre maximal de tentatives de diagnostic d'intégrité supplémentaires du système avant de déclarer un service comme défaillant
 * **UrlPath** : Chemin d'URL HTTP pour le diagnostic d'intégrité de couche 7
