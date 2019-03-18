---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Traitement des incidents liés à la mise à disposition d'équilibreur de charge
{: #load-balancer-provisioning-troubleshooting}

Cette rubrique fournit des informations sur les problèmes courants liés à la création d'une nouvelle instance d'équilibreur de charge IBM© Cloud Load Balancer. 

## Adresses IP insuffisantes dans votre réseau
L'équilibreur de charge IBM Cloud Load Balancer requiert au moins deux adresses IP libres issues de son sous-réseau privé. En outre, si l'équilibreur de charge est un équilibreur de charge public et que l'option **Pool de systèmes IBM** n'est pas utilisée, au moins deux adresses IP libres issues de votre réseau public sont également requises. 

Procédez comme suit pour rechercher les adresses IP libres dans un sous-réseau :

1. Accédez au [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com){:new_window}, puis à la section des sous-réseaux en sélectionnant **Réseau > Gestion IP > Sous-réseaux**.

2. Cliquez sur le sous-réseau pour lequel vous souhaitez rechercher des adresses IP libres.

	<img src="images/subnet_list.png" alt="drawing" style="width: 600px;"/>
		
3. La page des détails du sous-réseau sélectionné indique le statut de toutes les adresses IP qu'il contient.

## Problèmes liés aux pare-feu sur les VLAN publics et privés
Pour savoir comment autoriser le passage d'adresses IP via le pare-feu, voir [Plages d'adresses IP IBM Cloud](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges).
 
## Affichage des messages d'erreur liés à l'équilibreur de charge
Pour afficher les messages d'erreur liés à votre équilibreur de charge, procédez comme suit :

1. Cliquez sur l'équilibreur de charge dans la page de liste pour afficher les détails le concernant. 
2. Déplacez la souris au-dessus du symbole d'erreur en regard de l'état de l'équilibreur de charge.

<img src="images/lbaas_error_message.png" alt="drawing" style="width: 500px;"/>

Si l'équilibreur de charge est à l'état `ERROR`, il ne peut pas être récupéré et doit être détruit.
