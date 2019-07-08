---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, monitor, metrics, throughput, connection

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

# Surveillance des métriques avec l'équilibreur de charge IBM Cloud Load Balancer
{: #monitoring-metrics-with-ibm-cloud-load-balancer}

L'équilibreur de charge surveille les métriques suivantes :

* Débit
* Connexions actives
* Taux de connexion

Ces métriques sont affichées sous forme de graphiques accessibles au moyen de l'onglet **Surveillance** et sont disponibles à l'aide d'un programme sous forme de points de données de séries temporelles au moyen de l'API `getListenerTimeSeriesData`.

Chaque point de données contient un horodatage au format époque UNIX, la valeur de métrique pour cet intervalle de temps se terminant à cet horodatage. L'utilisateur peut spécifier les protocoles et l'intervalle de temps pour lesquels les métriques seront communiquées.

Les protocoles pris en charge sont les suivants :

* HTTP
* HTTPS
* TCP

La spécification d'un protocole permet de filtrer les métriques en fonction de celui-ci.

Par exemple, si aucun protocole n'est spécifié et que la métrique est *Débit*, le débit total pour tous les protocoles est communiqué.

Si le protocole est *HTTP*, seul le débit pour le trafic HTTP est communiqué.

L'utilisateur peut spécifier l'intervalle de temps pour lequel la métrique sera communiquée. Les intervalles de temps pris en charge sont les suivants :

* 1 heure
* 6 heures
* 12 heures
* 24 heures
* 1 semaine
* 2 semaines

Le nombre de points de données communiqué est à peu près le même pour chaque intervalle de temps.  
Par exemple, si l'intervalle correspond à 1 heure, chaque point de données représente 5 minutes de données.

Si l'intervalle correspond à 2 semaines, chaque point de données représente 24 heures de données.

Le tableau ci-dessous indique la façon dont les points de données sont dérivés de l'intervalle de temps :

| Intervalle de temps | Précision de point de données | Nombre de points de données |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
| 1 heure    | 5 minutes | 12   |
| 6 heures   | 30 minutes | 12  |
| 12 heures  | 1 heure | 12 |
| 24 heures  | 2 heures | 12 |
| 1 semaine    | 12 heures | 12 |
| 2 semaines  | 24 heures | 12 |

## Procédure d'activation des métriques de surveillance
{: #how-to-enable-metrics-monitoring}

Pour extraire les métriques de surveillance, vous devez lier votre compte SoftLayer à votre compte IBM© Cloud. Pour plus d'informations, voir [cette rubrique](/docs/account?topic=account-unifyingaccounts#link_accounts).
