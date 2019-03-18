---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"


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

# Configuration des paramètres de l'équilibreur de charge IBM Cloud Load Balancer
{: #configuring-ibm-cloud-load-balancer-parameters}

Une fois que vous avez créé un équilibreur de charge, vous pouvez le configurer pour l'équilibrage de charge élastique. Pour ce faire, procédez comme suit :

1. Nommez votre équilibreur de charge et, éventuellement, ajoutez une description.

	<img src="images/lb-config-basic.png" alt="drawing" style="width: 300px;"/>

2. Entrez les détails de votre profil d'application en identifiant les protocoles et les ports sur lesquels votre application est en mode écoute. Vous pouvez utiliser la même configuration pour le système de back end et le système de front end ou exposer un port de front end différent (pour des raisons de sécurité, par exemple).

3. La méthode d'équilibrage de charge par défaut est **Round Robin**. Vous pouvez la remplacer par **Round Robin pondéré** ou **Connexions minimum** dans la liste déroulante, selon les besoins de votre application.

4. Vous pouvez éventuellement activer l'option **Adhésion de session**. Si cette option est activée, toutes les demandes d'un utilisateur final spécifique (par exemple, un utilisateur ayant la même adresse IP source) sont acheminées vers le même serveur de back end pour une heure fixe définies par le système.

5. Vous pouvez également définir un **nombre maximal de connexions** pour votre application.

6. Cliquez sur **Ajouter un protocole** afin de spécifier des ports et des protocoles supplémentaires sur lesquels votre application pourra être en mode écoute. Assurez-vous que tous les ports de front end sont uniques. Vous pouvez choisir HTTP, HTTPS ou TCP comme protocole de front end.

	<img src="images/lb-add-protocol.png" alt="drawing" style="width: 300px;"/>

	Un nombre maximal de deux ports peut être défini lors de la configuration initiale. Des ports supplémentaires peuvent être ajoutés ultérieurement après la création de l'instance de service. Pour plus d'informations sur le nombre maximal de ports autorisés, voir [Limitations concernant le nombre de ports](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-).
{:note:}

7. L'équilibreur de charge IBM© termine des connexions HTTPS (HTTP sur SSL) entrantes et peut communiquer via un protocole HTTP en texte normal avec des serveurs d'application de back end, et décharge les tâches SSL exigeant d'importantes ressources processeur de vos serveurs si le protocole de back end sélectionné est HTTP. Si le protocole de back end sélectionné est HTTPS, le trafic sera chiffré entre l'équilibreur de charge et les serveurs de back end. Vous devez télécharger votre certificat SSL. Sélectionnez l'un des certificats disponibles dans la liste déroulante.  

	<img src="images/lb-ssl-cert.png" alt="drawing" style="width: 300px;"/>

	Si vous ne possédez pas de certificat, cliquez sur **Ajouter un nouveau certificat**. Vous accédez alors à un service de certificat IBM Cloud dans lequel vous pouvez acquérir un nouveau certificat ou télécharger un certificat existant. 
	
	Après avoir ajouté le certificat, revenez à la page de configuration de l'équilibreur de charge et cliquez sur l'icône d'actualisation située sous la liste déroulante Certificat SSL pour afficher et ajouter votre certificat nouvellement téléchargé.

	<img src="images/order-ssl-cert.png" alt="drawing" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="drawing" style="width: 300px;"/>

	**Remarque : ne supprimez jamais les certificats associés à des programmes d'écoute HTTPS car cela pourrait provoquer des problèmes de fonctionnalité.**

8. Cliquez sur **Suivant**.

## Configuration des diagnostics d'intégrité
La définition de diagnostic d'intégrité est obligatoire pour chacun de vos ports d'application. Il s'agit des ports de back end identifiés dans le précédent menu de configuration de base.

<img src="images/config-health-check.png" alt="drawing" style="width: 300px;"/>

Le système préremplit une configuration de diagnostic d'intégrité par défaut pour ces ports de back end. Vous pouvez personnaliser ces paramètres en fonction des besoins de votre application.

* **Interval** : Intervalle exprimé en secondes entre deux tentatives de diagnostic d'intégrité consécutives
* **Timeout** : Durée maximale pendant laquelle le système attend une réponse à une demande de diagnostic d'intégrité
* **Max Trials** : Nombre maximal de tentatives de diagnostic d'intégrité supplémentaires du système avant de déclarer un port comme défaillant
* **Path** : Chemin d'URL HTTP pour le diagnostic d'intégrité     

Cliquez sur **Suivant** pour activer l'option que vous avez choisie.

## Que faire ensuite ?
[Identifiez les ressources de votre application](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources), par exemple les pools d'origine et les mécanismes de diagnostic d'intégrité.
