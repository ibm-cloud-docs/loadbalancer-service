---

copyright:
  years: 2017, 2018
lastupdated: "2019-01-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Présentation de MZR (Multi-Zone Region)
{: #multi-zone-region-mzr-overview}

Lors de la création d'un équilibreur de charge, vous indiquez le centre de données où il doit être créé. Si le centre de données fait partie d'une région multi-zone (MZR, Multi-Zone Region), les noeuds de l'équilibreur de charge sont instanciées dans deux centres de données différents. Par exemple, `us-south` est une région MZR qui contient `dal10`, `dal12`, `dal13`. Si un client crée un équilibreur de charge dans un centre de données `dal13`, les noeuds sont instanciés dans `dal13`, `dal10` ou `dal12`. Normalement, aucun changement évident n'est visible au niveau du trafic. La prise en charge de MZR s'avère utile lorsque la communication avec un centre de données est interrompue. L'équilibreur de charge continue à fonctionner car l'autre noeud se trouve dans un autre centre de données.

Les centres de données suivants font actuellement partie d'une région MZR :

| Nom de la région MZR | Centres de données |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |


## Exigences liées à MZR
Les régions multi-zone (MZR) doivent répondre aux exigences suivantes :
* Le centre de données sélectionné doit faire partie d'une région MZR. Le tableau ci-dessus répertorie les régions et les centres de données de chaque région.
* Le spanning VLAN doit être activé dans votre compte.
* Votre compte doit comporter des sous-réseaux privés dans le centre de données de la région MZR. La création de dispositifs de calcul dans des centres de données entraîne l'instanciation de sous-réseaux privés.

Si le centre de données sélectionné ne fait pas partie d'une région MZR ou si le spanning VLAN n'est pas activé dans votre compte, la création de l'équilibreur de charge instancie par défaut tous les noeuds d'équilibreur de charge dans le centre de données indiqué.
