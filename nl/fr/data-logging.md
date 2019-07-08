---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

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

# Consignation des données
{: #data-logging}

Les journaux de données et de diagnostic d'intégrité sont utiles à des fins de débogage et de maintenance. Lorsque la fonction de consignation est données est activée, IBM Load Balancer transmet les journaux au [service IBM Cloud Log Analysis![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://logging.ng.bluemix.net){:new_window} sous votre compte. 

Vous pouvez activer ou désactiver cette fonctionnalité en :

* créant un nouvel équilibreur de charge sur lequel définir la fonctionnalité ; 
* utilisant l'API `enableOrDisableDataLogs`.

## Affichage des journaux dans le service IBM Cloud Logging Analysis 
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

Connectez-vous au service [IBM Cloud Logging Analysis ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://logging.ng.bluemix.net){:new_window} à l'aide de votre compte client IBM Cloud. Les journaux sont consultables depuis Kibana. Pour plus d'informations, voir [cette rubrique](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana).

Les journaux de données sont envoyées uniquement si les comptes Softlayer et IBM Cloud sont liés. Sélectionnez le compte IBM Cloud associé à votre compte Softlayer puis connectez-vous au tableau de bord Kibana.
{: tip}

## Exemples de sortie de journal
{: #log-output-examples}

La sortie suivante est un exemple de journal de données IBM Cloud Load Balancer :

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` est le nom de l'équilibreur de charge et `dal09` le centre de données. 
* `323698` est l'ID compte. `643866` est l'ID équilibreur de charge. `713576` l'ID membre.
* `xxx.xxx.xxx.xxx` est une adresse IP publique masquée pour respecter le règlement général sur la protection des données. 

La sortie suivante est un exemple de journal de diagnostic d'intégrité dans le service IBM Cloud Logging Analysis :

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` est l'adresse IP du membre.
* `682175` l'ID membre.
