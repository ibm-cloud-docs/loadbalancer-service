---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

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

# Registrazione dati
{: #data-logging}

I log di dati e di controllo dell'integrità sono preziosi per le attività di debug e manutenzione. Con la funzione di registrazione dati abilitata, IBM Load Balancer inoltra questi log al [servizio IBM Cloud Log Analysis ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://logging.ng.bluemix.net){:new_window} nel tuo account.

Puoi abilitare o disabilitare questa funzione:

* Creando un nuovo programma di bilanciamento del carico e impostando questa funzione su uno stato di attivo (on).
* Utilizzando l'API `enableOrDisableDataLogs`.

## Visualizzazione dei log nel servizio IBM Cloud Logging Analysis
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

Accedi al [servizio IBM Cloud Logging Analysis ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://logging.ng.bluemix.net){:new_window} con l'account IBM Cloud del cliente. I log possono essere visualizzati da Kibana. Fai riferimento a [questo argomento](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana) per ulteriori informazioni.

I log di dati vengono inviati solo se gli account Softlayer e IBM Cloud sono collegati. Seleziona l'account IBM Cloud associato al tuo account Softlayer ed esegui quindi l'accesso al dashboard Kibana.
{: tip}

## Esempi di output di log
{: #log-output-examples}

Il seguente output è un esempio di un log di dati IBM Cloud Load Balancer:

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` è il nome del programma di bilanciamento del carico e `dal09` è il data center.
* `323698` è l'ID account. `643866` è l'ID del programma di bilanciamento del carico. `713576` è l'ID membro.
* `xxx.xxx.xxx.xxx` è un IP pubblico che è stato mascherato per il GDPR.

Il seguente output è un esempio di log di controllo dell'integrità all'interno del servizio IBM Cloud Logging Analysis:

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` è l'indirizzo IP del membro.
* `682175` è l'ID membro.
