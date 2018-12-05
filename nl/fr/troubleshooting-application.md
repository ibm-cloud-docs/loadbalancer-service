---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Traitement des incidents liés au serveur d'application
Cette rubrique fournit des informations sur les problèmes courants liés à l'utilisation de l'équilibreur de charge. 

## Le serveur de back end est défectueux
Si la santé de votre serveur de back end est défaillante, vérifiez la liste suivante pour essayer d'y remédier :

* Le port du protocole de back end configuré correspond-il au port sur lequel votre application est en mode écoute ?
* Le diagnostic d'intégrité configuré possède-t-il les informations de protocole (TCP ou HTTP), de port et d'URL (pour HTTP) appropriées ? Pour HTTP, assurez-vous que votre application répond avec le message `200 OK` pour l'URL de diagnostic d'intégrité configurée. 
* Le serveur de back end se trouve-t-il sur un sous-réseau différent de celui de l'équilibreur de charge ? Si tel n'est pas le cas, assurez-vous que le spanning VLAN est activé. 
* Le serveur de back end est-il un serveur virtuel avec un groupe de sécurité activé ? Si tel est le cas, assurez-vous que les règles de groupe de sécurité autorisent le trafic entre l'équilibreur de charge et le serveur virtuel.
