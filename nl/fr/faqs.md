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
{:faq: data-hd-content-type='faq'}

# Foire aux questions concernant l'équilibreur de charge IBM Cloud Load Balancer
{: #faqs-for-ibm-cloud-load-balancer}

La présente section apporte des réponses aux questions les plus fréquemment posées au sujet du service IBM© Cloud Load Balancer.

## Combien d'options d'équilibrage de charge sont disponibles dans {{site.data.keyword.BluSoftlayer_notm}} ?
{:faq}

Pour une comparaison détaillée des offres Equilibreur de charge d'IBM, voir [Découverte des équilibreurs de charge](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-explore).

## Puis-je utiliser un nom DNS différent pour mon équilibreur de charge ?
{:faq}

Bien que le nom DNS affecté automatiquement à l'équilibreur de charge ne soit pas personnalisable, vous avez la possibilité d'ajouter un enregistrement CNAME (nom canonique) qui fasse pointer le nom DNS de votre choix vers le nom DNS affecté automatiquement. 

Par exemple, si votre numéro de compte est 123456, votre équilibreur de charge est déployé dans le centre de données `dal09` sous le nom `myapp` et le nom DNS affecté automatiquement à l'équilibreur de charge est `myapp-123456-dal09.lb.bluemix.net` et vous souhaitez utiliser le nom DNS `www.myapp.com`, vous pouvez ajouter un enregistrement CNAME (via le fournisseur DNS utilisé pour gérer myapp.com) qui fasse pointer `www.myapp.com` sur le nom DNS d'équilibreur de charge 'myapp-12345-dal09.lb.bluemix.net'.

## Quel est le nombre maximal de ports virtuels que je peux définir avec mon service Load Balancer ?
{:faq}

Lors de la création d'un service Load Balancer, vous pouvez définir jusqu'à deux ports virtuels. Vous pouvez définir des ports virtuels supplémentaires une fois le service créé. La limite autorisée est alors de 10 ports virtuels.

## Quel est le nombre maximal d'instances de calcul que je peux associer à mon équilibreur de charge ?
{:faq}

50.

## Mes instances de calcul de back end peuvent-elles être installées sur un autre sous-réseau que le celui de l'équilibreur de charge ?
{:faq}

Oui, l'équilibreur de charge et les instances de calcul qui lui sont connectées peuvent se trouver dans des sous-réseaux différents, mais le **spanning VLAN** doit être activé pour que l'équilibreur de charge puisse communiquer et envoyer des demandes à l'instance de calcul. Pour plus d'informations, voir [Traitement des incidents liés au spanning VLAN](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-vlan-spanning-troubleshooting).

## Quels sont les paramètres par défaut et les valeurs autorisées pour les différents paramètres de diagnostic d'intégrité ?
{:faq}

Vous trouverez ci-dessous la liste des paramètres par défaut et des valeurs autorisées :

* **Intervalle de diagnostic d'intégrité :** La valeur par défaut est 5 secondes et la plage autorisée est comprise entre 2 et 60 secondes
* **Délai de réponse du diagnostic d'intégrité :** La valeur par défaut est 2 secondes et la plage autorisée est comprise entre 1 et 59 secondes
* **Nombre maximal de tentatives :** La valeur par défaut est 2 tentatives et la plage autorisée est comprise entre 1 et 10 tentatives

**Remarque :** La valeur du délai de réponse du diagnostic d'intégrité doit toujours être inférieure à la valeur d'intervalle de diagnostic d'intégrité.

## Puis-je utiliser des instances de calcul situées dans des centres de données distants avec ce service ?
{:faq}

Il est recommandé d'installer votre service Load Balancer et vos instances de calcul en local dans le même centre de données. L'interface graphique du service Load Balancer n'affiche pas les instances de calcul des autres centres de données distants. Cependant, les instances de calcul des autres centres de données d'une même ville (à savoir, les centres de données dont le nom commence par les mêmes 3 premières lettres, telles que DALxx). Vous pouvez utiliser l'API pour ajouter des instances de calcul de n'importe quel centre de données distant.

## Quelle est la version TLS compatible avec le déchargement SSL ?
{:faq}

Le service IBM Cloud Load Balancer prend en charge la version TLS 1.2 avec terminaison SSL.

La liste ci-dessous répertorie les différents chiffrements pris en charge (par ordre de priorité) :  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## Combien d'instances de service Load Balancer maximum puis-je créer dans mon compte ?
{:faq}

Actuellement, vous pouvez créer jusqu'à 50 instances de service. Si vous avez besoin de plus d'instances, contactez le support IBM. 

## Le service IBM Cloud Load Balancer peut-il être utilisé avec VMWare ?
{:faq}

Les machines virtuelles VMWare auxquelles des adresses privées portables SoftLayer sont affectées peuvent être spécifiées en tant que serveurs de back end pour l'équilibreur de charge. Cette fonctionnalité est actuellement disponible uniquement à l'aide de l'API et non via l'interface graphique (GUI) Web. Les adresses IP privées portables qui sont ajoutées à l'aide de l'API apparaissent comme étant "inconnues" dans l'interface graphique, car elles ne sont pas affectées par SoftLayer. Notez que ce type de configuration peut être utilisé avec d'autres hyperviseurs, tels que Xen et KVM.

Les machines virtuelles VMWare auxquelles des adresses autres que SoftLayer (par exemple, des réseaux VMware NSX) sont affectées ne peuvent pas être ajoutées directement en tant que serveurs de back end à l'équilibreur de charge. Toutefois, selon votre configuration, il peut être possible de configurer un intermédiaire, tel qu'une passerelle NSX, doté d'une adresse privée SoftLayer en tant que serveur de back end pour l'équilibreur de charge (avec les serveurs réels associés virtuellement (VM) aux réseaux gérés par VMware NSX).

## Si je choisis d'utiliser un VLAN public sous mon compte pour déployer mon équilibreur de charge et qu'un pare-feu est déployé sur mon VLAN public, quelles sont les exigences requises sur le pare-feu pour pouvoir utiliser le service Load Balancer ?
{:faq}

Le port TCP 56501 est utilisé à des fins de gestion. Assurez-vous que le trafic vers ce port, et vers les ports de l'application, n'est pas bloqué par votre pare-feu, faute de quoi la mise à disposition de l'équilibreur de charge risque d'échouer.

## Que se passe-t-il si je ne vois pas les métriques de surveillance d'un équilibreur de charge existant après avoir lié à mon compte softlayer à IBM Cloud ? 
{:faq}

Les métriques de surveillance ne seront pas disponibles pour les équilibreurs de charge existants une fois les comptes liés. Vous devez recréer les équilibreurs de charge ou contacter le support. Les métriques de surveillance pour les équilibreurs de charge nouvellement créés seront disponibles.

## Les adresses IP d'équilibreur de charge sont-elles fixes ?
{:faq}

Nous ne pouvons pas garantir que les adresses IP d'équilibreur de charge resteront constantes en raison de l'élasticité qui est générée dans le service. A mesure qu'il s'agrandit ou qu'il diminue, vous verrez les modifications apportées aux adresses IP libres qui sont associées au nom de domaine complet de votre instance.

**Remarque :** vous devez utiliser un nom de domaine complet et non des adresses IP mises en cache.

## Si je possède un pare-feu déployé sur mon VLAN privé, quelles sont les configurations requises pour qu'il fonctionne avec mon service d'équilibrage de charge ?
{:faq}

Pour savoir comment autoriser le passage d'adresses IP via le pare-feu, voir [Plages d'adresses IP IBM Cloud](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges).

## Pour quelle raison ma configuration de couche 7 n'est-elle pas visible dans l'interface utilisateur ?
{:faq}

Actuellement, la prise en charge de la couche 7 est disponible uniquement via des API publiques ; cette fonctionnalité sera prochainement disponible dans l'interface utilisateur. Pour plus d'informations, voir la section sur la couche 7 dans la [documentation des API](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-api-reference).

## Quelles sont les informations nécessaires pour créer un ticket de demande de service ?
{:faq}

Pour créer un ticket de demande de service, indiquez le nom du produit ("IBM Cloud Load Balancer"), l'identificateur unique universel de votre équilibreur de charge (si possible) et votre numéro de compte Softlayer. Vous trouverez l'identificateur unique universel dans l'URL après avoir accédé à la page de présentation de l'équilibreur de charge concerné.
