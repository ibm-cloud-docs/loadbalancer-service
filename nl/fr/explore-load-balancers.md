---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Découverte des équilibreurs de charge

IBM Cloud offre plusieurs solutions d'équilibrage de charge. Le tableau ci-dessous compare les solutions d'équilibrage de charge afin de vous aider à faire le bon choix. Pour obtenir des renseignements supplémentaires sur une offre particulière, cliquez sur son nom dans le tableau. 

Faites défiler l'écran vers la droite pour visualiser la totalité du tableau !


|        | [Equilibreur de charge IBM Cloud](../../infrastructure/loadbalancer-service/getting-started.html#getting-started)| [Equilibreur de charge local](../../infrastructure/local-load-balancer/getting-started.html#getting-started) (partagé)| [Equilibreur de charge local](../../infrastructure/local-load-balancer/getting-started.html#getting-started) (dédié)| [Citrix NetScaler](../../infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX (Standard)| [Citrix NetScaler](../../infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX (Platinum) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**VIP public**|Oui|Oui|Oui|Oui|Oui |
|**VIP privé**|Oui|Non|Oui|Oui|Oui |
|**Couche 4 LB**|Oui|Oui|Oui|Oui|Oui |
|**Couche 7 LB**|Oui|Persistance des cookies|Persistance des cookies|Oui|Oui |
|**Contrôles de santé**|Oui|Oui|Oui|Oui|Oui |
|**Mise à l'échelle horizontale**|Oui|Non|Non|Non|Non |
|**Déchargement SSL**|Oui|Oui|Oui|Oui|Oui |
|**Gestion**|via le portail IBM|via le portail IBM|via le portail IBM|Auto-gestion (interface fournisseur)|Auto-gestion (interface fournisseur) |
|**Haute disponibilité**|Intégrée|Intégrée|En option|En option|En option |
|**LB avancé (optimisation TCP, compression, mise en cache, WAF)**|Non|Non|Non|Limité|Oui |
|**LB global (GLB)**|Non|Non|Non|Non|Oui |
|**Tarification**|Basée sur l'utilisation|Forfait mensuel|Forfait mensuel|Forfait mensuel|Forfait mensuel |
