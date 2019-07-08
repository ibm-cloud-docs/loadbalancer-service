---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

keywords: encryption, security

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Impostazione della crittografia di backend
{: #setting-backend-encryption}

La crittografia di backend è supportata per consentire la crittografia del traffico dati end-to-end. Non solo è il traffico tra il programma di bilanciamento del carico e il client crittografato, ma è anche il traffico tra il programma di bilanciamento del carico e il server di backend.

Per abilitare la crittografia di backend:

* Se stai aggiungendo un nuovo protocollo HTTPS, imposta il frontend e il backend su **HTTPS**.
* Per i protocolli HTTPS esistenti, imposta il backend su **HTTPS**.
