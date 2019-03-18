---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Définition du chiffrement de back end
{: #setting-backend-encryption}

Le chiffrement de back end est pris en charge pour autoriser le chiffrement du trafic de données. Non seulement le trafic entre l'équilibreur de charge et le client est chiffré, mais également celui entre l'équilibreur de charge et le serveur de back end.

Pour activer le chiffrement de back end :

* Si vous ajoutez un nouveau protocole HTTPS, définissez le front end et le back end sur **HTTPS**.
* Pour des protocoles HTTPS existants, définissez le back end sur **HTTPS**.
