---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

keywords: load balancer, compare, explore

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
{:row-headers .row-headers}

# Découverte des équilibreurs de charge IBM
{: #explore}

IBM© Cloud propose plusieurs solutions d'équilibrage de charge. Le tableau ci-dessous compare les solutions d'équilibrage de charge afin de vous aider à faire le bon choix. Pour obtenir des renseignements supplémentaires sur une offre particulière, cliquez sur son nom dans le tableau.

Faites défiler l'écran vers la droite pour visualiser la totalité du tableau !
{: important}


|        | [Equilibreur de charge IBM Cloud](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started)| [Equilibreur de charge local](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (partagé)| [Equilibreur de charge local](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (dédié)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (Standard)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (Platinum) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**VIP public**|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg) |
|**VIP privé**|![Icône de coche](../../icons/checkmark-icon.svg)||![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg) |
|**Couche 4 LB**|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg) |
|**Couche 7 LB**|![Icône de coche](../../icons/checkmark-icon.svg)|Persistance des cookies|Persistance des cookies|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg) |
|**Diagnostics d'intégrité**|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg) |
|**Mise à l'échelle horizontale**|![Icône de coche](../../icons/checkmark-icon.svg)|||| |
|**Déchargement SSL**|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg)|![Icône de coche](../../icons/checkmark-icon.svg) |
|**Gestion**|via le portail IBM|via le portail IBM|via le portail IBM|Auto-gestion (interface fournisseur)|Auto-gestion (interface fournisseur) |
|**Haute disponibilité**|Intégrée|Intégrée|En option|En option|En option |
|**LB avancé (optimisation TCP, compression, mise en cache, WAF)**||||Limité|![Icône de coche](../../icons/checkmark-icon.svg)|
|**LB global (GLB)**|||||![Icône de coche](../../icons/checkmark-icon.svg) |
|**Tarification**|Basée sur l'utilisation|Forfait mensuel|Forfait mensuel|Forfait mensuel|Forfait mensuel |
{: row-headers}
{: class="comparison-table"}
{: caption="Comparaison des offres d'équilibreur de charge d'IBM" caption-side="top"}
{: summary="This table all of IBM's load balancer offerings, and provides links to their documentation."}
