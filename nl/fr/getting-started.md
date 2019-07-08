---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# Initiation à l'équilibreur de charge IBM Cloud Load Balancer
{: #getting-started}

Pour commencer à utiliser le service IBM© Cloud Load Balancer, vous aurez besoin des deux éléments essentiels suivants :

* Un compte IBM : [IBMid ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* Un serveur IBM (il peut s'agir d'un serveur [Bare Metal](/docs/bare-metal?topic=bare-metal-about) ou d'une [instance de serveur virtuel](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)).

Si vous avez besoin d'aide pour obtenir un compte **IBMid**, contactez votre [commercial IBM![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} pour obtenir des conseils supplémentaires.

Si vous disposez d'un compte IBM Cloud Infrastructure (SoftLayer), vous pouvez [lier votre compte](/docs/account?topic=account-unifyingaccounts) à votre IBMid.

## Commande d'un équilibreur de charge
{: #ordering-a-load-balancer}

Pour commander un service IBM Cloud Load Balancer, sélectionnez **IBM Cloud Load Balancer** dans le [catalogue IBM Cloud ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window}. Cliquez ensuite sur **Créer** et exécutez la procédure suivante :

1. Définissez les paramètres de service de base, tels que le nom et la description.
2. Sélectionnez votre centre de données.
3. Sélectionnez un type d'équilibreur de charge **Public**.
4. Sélectionnez le sous-réseau où vous souhaitez déployer votre équilibreur de charge.

  L'une des interfaces réseau de votre instance de service Load Balancer se trouvera sur ce sous-réseau. Assurez-vous que vos serveurs d'applications sont installés sur ce sous-réseau et sont accessibles à partir de celui-ci. Si nécessaire, activez la superposition VLAN.
  {: note}

5. Créez des ports et protocoles d'application de front end et de back end.

  Pour plus d'informations sur cette configuration, voir [Configuration des paramètres de l'équilibreur de charge IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters).
  {: note}

6. Pour activer le déchargement SSL, définissez les protocoles de front end sur HTTPS, et ceux de back end sur HTTP. Sélectionnez ensuite votre certificat SSL dans la zone déroulante Certificat. 

  Tous les certificats SSL existants sont gérés via le [magasin de certificats IBM Cloud![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}. Si vous ne disposez pas d'un certificat SSL, c'est là que vous pouvez en créer un.

7. Ajustez les paramètres de diagnostic d'intégrité si besoin, ou utilisez les paramètres par défaut.

  Pour plus d'informations sur les paramètres de diagnostic d'intégrité, voir [Configuration des paramètres de l'équilibreur de charge IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks).
  {: note}

8. Cliquez sur **Connecter un serveur** pour associer une ou plusieurs instances de serveur derrière votre équilibreur de charge. Seules les instances de serveur locales sur votre centre de données seront affichées.
9. Vérifiez la page, confirmez le contrat de service, puis cliquez sur **Créer**.

La liste des équilibreurs de charge s'affiche, avec toutes vos instances de service.

Lorsque vous cliquez sur le nom du service sur cette page, la page de présentation du service s'ouvre. Vous pouvez accéder aux onglets **Protocoles**, **Diagnostics d'intégrité** et **Instances de serveur ** pour éditer davantage votre configuration.

L'équilibreur de charge que vous venez de créer peut ne pas s'afficher immédiatement dans la liste. Après quelques minutes, il apparaît en grisé, ce qui correspond au statut hors ligne (`Offline`). Patientez encore quelques minutes et il s'affiche en vert, indiquant qu'il est en ligne (`Online`). Vous devrez peut-être actualiser votre écran pour voir ces changements.
{: note}

Pour des instructions pas à pas sur la configuration de votre nouvel équilibreur de charge Cloud Load Balancer, voir [Utilisation d'un équilibreur de charge IBM Cloud Load Balancer pour l'équilibrage de charge de serveur élastique](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing).
