---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: create, new, load balancer

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

# Création d'un équilibreur de charge IBM Cloud Load Balancer
{: #creating-an-ibm-cloud-load-balancer}

Pour créer un service d'équilibreur de charge IBM© Cloud, procédez comme suit :

1. A partir de votre navigateur, ouvrez le [portail client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com/){: new_window} et connectez-vous à votre compte.

2. Cliquez sur **Catalogue**, puis à partir de la section Infrastructure, accédez à **Réseau > Equilibreurs de charge**.

	<img src="images/catalog-load-balancer.png" alt="drawing" style="width: 600px;"/>

3. Sélectionnez **Equilibreur de charge IBM Cloud** (sélection par défaut) et cliquez sur **Créer**.

	Si l'option **Mettre à niveau** est affichée au lieu de l'option **Créer**, vous devez lier votre compte IBM Cloud Infrastructure (SoftLayer) en suivant [cette procédure](/docs/account?topic=account-unifyingaccounts)

	<img src="images/create-load-balancer.png" alt="drawing" style="width: 600px;"/>

4. Sélectionnez votre centre de données préféré dans la liste déroulante **Centre de données**, passez en revue les informations, puis cliquez sur **Suivant**.

	<img src="images/select-datacenter.png" alt="drawing" style="width: 600px;"/>

5. Spécifiez votre type d'équilibreur de charge.

	Pour les applications accessibles sur Internet qui doivent accéder à l'Internet public, sélectionnez **Public (accessible sur Internet)**.

	<img src="images/select-lb-type.png" alt="drawing" style="width: 600px;"/>

	Par défaut, l'équilibreur de charge public reçoit une adresse IP publique unique au niveau global provenant du pool d'adresses global d'IBM. Si, toutefois, vous souhaitez lui affecter des adresses publiques issues de votre propre pool d'adresses ou si vous souhaitez le déployer derrière un service de pare-feu au sein de votre compte, vérifiez si votre sous-réseau public comporte [suffisamment d'adresses IP](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting) et sélectionnez **Allocate from a public subnet in your account**.

	Pour les applications internes uniquement qui n'ont pas besoin d'accéder à l'Internet public, sélectionnez le type **Interne (privé)**.

	<img src="images/lb-type-private.png" alt="drawing" style="width: 500px;"/>

	Pour les types d'équilibreur de charge accessibles sur Internet et internes, sélectionnez l'un des sous-réseaux privés dans le compte où vous souhaitez déployer votre équilibreur de charge. Vos serveurs d'application doivent être accessibles à partir de ce sous-réseau. Si nécessaire, activez le spanning VLAN pour garantir la connectivité réseau appropriée.

	Si vous ne voyez pas de sous-réseaux privés, cliquez sur **Précédent**, puis sélectionnez un autre centre de données avec des sous-réseaux privés.

6. Cliquez sur **Suivant** pour terminer la configuration.

## Que faire ensuite ?
{: #whats-next-2}
Configurez votre équilibreur de charge avec des [paramètres de base](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters).
