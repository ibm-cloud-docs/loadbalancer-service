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

# Identification de vos ressources de serveur d'application
Localisez vos **instances de serveur** dans le tableau au bas de l'écran et cliquez sur **+** pour les ajouter derrière l'équilibreur de charge. Vous pouvez effectuer une sélection parmi les instances de serveur virtuel IBM Cloud et les serveurs bare metal de votre compte. 

Ces instances de serveur doivent être installées localement sur le centre de données où vous déployez le service d'équilibreur de charge. De plus, les instances de serveur des centres de données voisins au sein de la même ville peuvent être ajoutées (par exemple, si les trois premières lettres du nom des centres de données sont les mêmes). 

<img src="images/locate-server-instance.png" alt="drawing" style="width: 300px;"/>

Cliquez sur **Suivant**.

**Remarques :** 

1. Les **pondérations** de serveur ne sont pertinentes que lorsque la méthode d'équilibrage de charge **Round Robin Pondéré** est utilisée. La pondération par défaut est 50 et les valeurs de pondération admises sont comprises entre 0 et 100. Les pondérations sont grisées avec d'autres méthodes d'équilibrage de charge. 
2. Pour plus d'informations sur le nombre maximal de serveurs d'application autorisés, voir [Limitations concernant le nombre de serveurs d'application](faqs.html#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-). 

## Que faire ensuite ?
[Examinez le contenu](order-lb.html) de votre commande avant de la passer. 
