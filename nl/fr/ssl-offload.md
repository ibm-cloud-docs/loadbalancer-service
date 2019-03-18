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

# Déchargement SSL avec l'équilibreur de charge IBM Cloud Load Balancer
{: #ssl-offload-with-ibm-cloud-load-balancer}

A chaque connexion HTTP entrante, le service Load Balancer met fin à la connexion SSL et établit une communication HTTP en texte en clair avec le serveur de back end. Les tâches de chiffrement/déchiffrement et d'établissement de liaison SSL sont déchargées des serveurs de back end, de sorte qu'ils peuvent utiliser l'intégralité de leur cycle d'unité centrale à des fins de traitement du trafic d'application. 

Un certificat SSL est nécessaire pour que l'équilibreur de charge procède aux tâches de déchargement SSL. Vous pouvez utiliser un certificat SSL préexistant ou en acheter un nouveau, et utiliser le [magasin de certificats IBM© Cloud ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://control.softlayer.com/security/sslcerts){:new_window} à des fins de gestion. 

## Suites de chiffrement SSL
Le service Load Balancer prend en charge la version TLS 1.2 avec déchargement SSL.

Les suites de chiffrement SSL suivantes sont prises en charge par votre équilibreur de charge :

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

Si au moins un port d'application de front end HTTPS (protocoles) est configuré votre équilibreur de charge, par défaut, toutes les suites de chiffrement SSL prédéfinies ci-dessus seront activées pour votre équilibreur de charge. 

**Remarque :** vous pouvez choisir d'activer d'autres suites de chiffrement SSL pour votre équilibreur de charge, si besoin. Pour plus d'informations, voir [Choix d'une suite de chiffrement préférée pour votre application HTTPS](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application).
