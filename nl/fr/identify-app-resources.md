---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: resources, server, application, instance, configure

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}

# Identification de vos ressources de serveur d'application
{: #identifying-your-application-server-resources}

Localisez vos **instances de serveur** dans le tableau au bas de l'écran et cliquez sur **+** pour les ajouter derrière l'équilibreur de charge. Vous pouvez effectuer une sélection parmi les instances de serveur virtuel IBM© Cloud et les serveurs bare metal de votre compte.

Ces instances de serveur doivent être installées localement sur le centre de données où vous déployez le service d'équilibreur de charge. De plus, les instances de serveur des centres de données voisins au sein de la même ville peuvent être ajoutées (par exemple, si les trois premières lettres du nom des centres de données sont les mêmes).

<img src="images/locate-server-instance.png" alt="drawing" style="width: 300px;"/>

Cliquez sur **Suivant**.

Les **pondérations** de serveur ne sont pertinentes que lorsque la méthode d'équilibrage de charge **Round Robin Pondéré** est utilisée. La pondération par défaut est 50 et les valeurs de pondération admises sont comprises entre 0 et 100. Les pondérations sont grisées avec d'autres méthodes d'équilibrage de charge.
{: note}

Pour plus d'informations sur le nombre maximal de serveurs d'application autorisés, voir [Limitations concernant le nombre de serveurs d'application](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-).
{: tip}

## Que faire ensuite ?
{: #what-s-next-3}
[Examinez le contenu](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order) de votre commande avant de la passer.
