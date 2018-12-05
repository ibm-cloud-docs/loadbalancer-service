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

# Diagnostics d'intégrité

Les définitions de contrôle de santé sont obligatoires pour chacun des ports d'application de back end. Le port/protocole sélectionné dans la configuration du contrôle de santé doit correspondre au port/protocole de back end, faute de quoi la configuration est rejetée. 

L'équilibreur de charge effectue des contrôles de santé réguliers pour surveiller la santé des ports de back end, puis achemine le trafic client en conséquence. Si un port de back end donné n'est pas intègre, aucune nouvelle connexion ne lui est envoyée. L'équilibreur de charge continue à surveiller ce port et reprend son utilisation au bout de deux contrôles successifs sans irrégularités. 

Les contrôles de santé des ports TCP et HTTP sont réalisés de la manière suivante :

* **HTTP :** Une demande `HTTP GET` fondée sur une URL prédéfinie est envoyée au port du serveur de back end. Le port est marqué comme intègre lorsqu'il reçoit une réponse `200 OK`. L'adresse URL `GET` par défaut est “/” via l'interface graphique, mais elle est personnalisable. 

* **TCP :** L'équilibreur de charge tente d'établir une connexion TCP au serveur de back end sur un port TCP spécifique. Le port du serveur est marqué comme intègre si la tentative de connexion aboutit, puis la connexion est fermée. 

	**Remarque :** L'intervalle de contrôle de santé par défaut est 5 secondes, le délai d'attente par défaut pour une demande de contrôle de santé est 2 secondes et le nombre de tentatives par défaut est 2. 
