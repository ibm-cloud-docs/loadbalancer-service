---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Equilibrage de charge de couche 7
Le service IBM Cloud Load Balancer répartit le trafic entre plusieurs instances de serveur, y compris les instances de serveur virtuel et bare metal, en utilisant des données de couche 7 (couche d'application).  

 * Le trafic de données à répartir est classifié à l'aide de politiques et de règles. 
 * Les règles définissent l'action à effectuer lorsque le trafic de données correspond à toutes les règles associées à une politique.
 * L'équilibrage de charge de couche 7 (L7) est pris en charge pour le trafic HTTP et HTTPS uniquement. 

## Politiques et règles de couche 7 
Une politique de couche 7 est associée à un port d'application frontal. Plusieurs politiques peuvent être associées à un port frontal. 

 * Ces politiques sont évaluées dans l'ordre, en fonction de la priorité affectée à chacune d'elles.  
 * Une action associée est exécutée lorsqu'il existe une correspondance pour la politique. 
 * Chaque règle L7 est associée à une politique.  
 * Si toutes les règles associées à la politique ont pour résultat `true`, la politique est mise en correspondance, par conséquent, l'action associée à la politique est exécutée. 

Pour plus d'informations, voir [Politique et règles L7](l7-policy.html). 

## Pools de couche 7
Chaque pool d'équilibreurs de charge de couche 7 contient une ou plusieurs instances de serveur logique.  

 * Chaque instance de serveur logique est identifiée par une adresse IP et un numéro de port. 
 * A chaque pool est associé un moniteur de santé, qui surveille la santé de tous les serveurs inclus dans le pool.
 * Un pool peut être configuré pour la persistance de session.  
 * Utilisez l'adresse IP source du client pour configurer la persistance de session. 

Pour plus d'informations, voir [Pools L7](l7-pool.html). 
