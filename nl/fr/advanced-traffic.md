---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: traffic, management, connection, persistence

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

# Gestion avancée du trafic avec l'équilibreur de charge {{site.data.keyword.loadbalancer_full}}
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

Cette section présente les différentes fonctionnalités de gestion de trafic avancée disponibles dans le service {{site.data.keyword.loadbalancer_full}}. 

## Nombre max. de connexions
{: #max-connections}

Utilisez la configuration "Nombre max. de connexions" pour limiter le nombre maximal de connexions simultanées sur un port virtuel de front end donné. Par défaut, aucune limite n'est définie. Le nombre maximal de connexions simultanées possibles sur un port virtuel de front end ou au niveau du système est 15 000.  

## Persistance de session
{: #session-persistence}

L'équilibreur de charge prend en charge la persistance de session sur des ports VIP donnés en fonction de l'`IP source` de la connexion. Par exemple, si la persistance de session est activée sur le port 80 (HTTP), toutes les tentatives ultérieures de connexion HTTP provenant du même client (même IP source) sont persistantes sur le même serveur de back end. Cette fonction est disponible pour les trois protocoles pris en charge (HTTP, HTTPS et TCP).

L'équilibreur de charge prend en charge jusqu'à 10 000 entrées de persistance client. Le délai d'expiration de ces entrées est 10 minutes. Toutes les demandes provenant de ce même client à l'issue des 10 minutes sont transférées vers un autre serveur de back end. Si l'entrée de persistance de session n'est pas arrivée à expiration, mais que le port de back end n'est plus viable, un nouveau serveur est sélectionné pour le transfert des connexions client suivantes.  

## HTTP Keep Alive
{: #http-keep-alive}
L'équilibreur de charge prend en charge `HTTP keep alive` à condition qu'il soit activé sur le client et les serveurs de back end. L'équilibreur de charge tente de réutiliser les connexions HTTP afin d'en accroître l'efficacité et de réduire le temps d'attente.

## Délais de connexion
{: #connection-timeouts}
Les valeurs de délai suivantes sont utilisées par l'équilibreur de charge. Ces valeurs ne sont pas personnalisables pour le moment.

| Nom | Description | Délai d'attente |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | ------------------- |
| Tentative de connexion côté serveur    | Fenêtre de temps maximum pouvant être utilisée par l'équilibreur de charge pour établir une connexion HTTP au serveur de back end. Si la tentative de connexion échoue, l'équilibreur de charge contacte le prochain serveur disponible, en fonction de la méthode d'équilibrage choisie. | 5 secondes   |
| Connexion inactive côté client  | Délai d'inactivité maximum, à l'issue duquel l'équilibreur de charge met fin à la connexion côté client, si le client n'a pas correctement fermé la connexion.| 50 secondes  |
| Connexion inactive côté serveur | Délai maximal d'inactivité (avec configuration du protocole back end sur TCP), à l'issue duquel l'équilibreur de charge met fin à la connexion côté serveur. Lorsque le protocole back end est configuré sur HTTP, si l'équilibreur de charge ne reçoit pas de réponse à sa demande HTTP dans le délai d'inactivité imparti, il envoie un message d'erreur au client final.                                | 50 secondes |
{: caption="Tableau 1. Valeurs de délai de l'équilibreur de charge" caption-side="top"}

## Conservation des adresses IP du client final
{: #preserving-end-client-ip-address}

L'équilibreur de charge fonctionne comme un proxy inverse, ce qui signifie qu'il met fin au trafic entrant du client. Il établit une connexion séparée à l'instance de serveur de back end à l'aide de sa propre adresse IP. Dans le cas des connexions HTTP aux serveurs de back end (par rapport aux connexions HTTP ou HTTPS de front end), l'équilibreur de charge conserve l'adresse IP du client en l'incluant dans l'en-tête `X-Forwarded-For HTTP`. Dans le cas des connexions TCP, les informations relatives à l'adresse IP du client d'origine ne sont pas conservées.
