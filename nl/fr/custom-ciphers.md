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

# Choix d'une suite de chiffrement préférée pour votre application HTTPS
{: #choosing-a-preferred-cipher-suite-for-your-https-application}

Algorithmes de chiffrement qui permettent à l'équilibreur de charge IBM© Cloud d'établir des connexions sécurisées avec ses clients HTTP. 

IBM offre une suite de chiffrements approuvés que vous pouvez sélectionner afin de sécuriser la communication entre votre équilibreur de charge et vos clients.

Vous pouvez choisir une suite de chiffrements préférés pour un équilibreur de charge existant ou vous pouvez concevoir des chiffrements lorsque vous créez un nouvel équilibreur de charge. 

## Choix de chiffrements pour un équilibreur de charge existant
Pour choisir une configuration de suites de chiffrement pour un équilibreur de charge existant, accédez à votre écran d'équilibreur de charge dans le portail client, puis cliquez sur l'onglet Protocoles.  Si HTTPS n'est pas sélectionné comme protocole de front end, vous ne verrez pas la liste de suites de chiffrement.

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="drawing" style="width: 700px;"/>
  
Sélectionnez HTTPS pour votre protocole de front end ; les suites de chiffrement disponibles s'affichent sous les détails de l'équilibreur de charge. 

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="drawing" style="width: 600px;"/>
  
Le tableau de chiffrements est éditable et vous permet de sélectionner vos suites de chiffrement souhaitées pour l'établissement de liaison SSL. Cliquez sur **Editer**, sélectionnez les chiffrements que vous souhaitez implémenter, puis cliquez sur **Sauvegarder**.
  
**Remarque :** pour obtenir une liste de chiffrements pris en charge, voir [Déchargement SSL](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).

## Choix de chiffrements lors de la création d'un nouvel équilibreur de charge

Pour choisir la suite de chiffrement lors de la création d'un nouvel équilibreur de charge :

1. Suivez les instructions de [création d'un équilibreur de charge](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-an-ibm-cloud-load-balancer#creating-an-ibm-cloud-load-balancer).
  
2. La configuration de suite de chiffrement s'applique uniquement au protocole de front end HTTPS. Lorsque vous atteignez les étapes de configuration pour la section **Ajouter un protocole**, choisissez **Protocole HTTPS**.

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="drawing" style="width: 500px;"/>
  
3. Un ensemble de chiffrements par défaut est déjà sélectionné dans la configuration, mais ne vous pourrez les éditer que lorsque vous aurez fini de configurer l'équilibreur de charge. 
  
	Terminez la configuration de l'équilibreur de charge en suivant les instructions décrites dans la rubrique. Lorsque vous avez terminé, la liste de chiffrements par défaut apparaît dans l'onglet **Protocoles** sous **Détails de l'équilibreur de charge**.

	<img src="images/View-CustomCiphers.png" alt="drawing" style="width: 600px;"/>
  
4. Le tableau de chiffrements est éditable et vous permet de sélectionner vos suites de chiffrement souhaitées pour l'établissement de liaison SSL. Cliquez sur **Editer**, sélectionnez les chiffrements que vous souhaitez implémenter, puis cliquez sur **Sauvegarder**.
	
	**Remarque :** pour obtenir une liste de chiffrements pris en charge, voir [Déchargement SSL](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).
