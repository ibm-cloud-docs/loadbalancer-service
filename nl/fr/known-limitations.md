---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: limitations, problems, troubleshooting

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Problèmes connus et limitations concernant l'équilibreur de charge {{site.data.keyword.loadbalancer_full}}
{: #known-issues-and-limitations-with-ibm-cloud-load-balancer}

La présente section fournit des informations sur les problèmes et limitations du service {{site.data.keyword.loadbalancer_full}}.

## Problèmes connus
{: #known-issues}
Les problèmes connus du service {{site.data.keyword.loadbalancer_full}} sont les suivants :

* Mineur - Le bouton **Editer** sur les onglets des protocoles et des instances de serveur s'applique à l'ensemble des entrées et pas seulement aux lignes dont la case a été sélectionnée.
* Mineur - Lors de la création initiale du service Load Balancer, vos paramètres personnalisés de diagnostic d'intégrité sont perdus si vous passez d'un écran à l'autre.
* Mineur - Vous pouvez rencontrer des problèmes lorsque vous utilisez les navigateurs Internet Explorer 11, Edge ou Safari pour administrer le service Load Balancer. Préférez Firefox ou Chrome.
* Cosmétique - Lors de la création initiale du service, la liste déroulante des centres de données risque d'être décalée. Vous pouvez tout de même sélectionner le centre de données de votre choix.
* Cosmétique - Les informations de tarification présentées sur la page de révision sont arrondies à deux chiffres après la virgule. Pour connaître le prix exact, consultez la page de plan.

## Limitations connues
{: #known-limits}
Les limitations connues du service {{site.data.keyword.loadbalancer_full}} sont les suivantes :

* Nombre maximal de ports/protocoles virtuels - 10
* Nombre maximal de serveurs derrière l'équilibreur de charge - 50
