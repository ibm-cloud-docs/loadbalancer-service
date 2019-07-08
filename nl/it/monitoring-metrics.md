---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, monitor, metrics, throughput, connection

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

# Monitoraggio delle metriche con IBM Cloud Load Balancer
{: #monitoring-metrics-with-ibm-cloud-load-balancer}

Il programma di bilanciamento del carico monitora le seguenti metriche:

* Velocità effettiva
* Connessioni attive
* Frequenza di connessione

Queste metriche vengono visualizzate come grafici che possono essere visualizzati selezionando la scheda **Monitoring**
e sono disponibili in modo programmatico come punti dati delle serie temporali utilizzando l'API `getListenerTimeSeriesData`.

Ogni punto dati contiene una data/ora con scadenza UNIX e il valore della metrica per tale intervallo temporale che finisce in tale data/ora. L'utente può specificare i protocolli e l'intervallo temporale in cui le metriche devono essere segnalate.

I protocolli supportati includono:

* HTTP
* HTTPS
* TCP

Specificare un protocollo che filtra la metrica per tale protocollo.

Ad esempio, se non viene specificato alcun protocollo e la metrica è *Velocità effettiva*,
viene segnalata la velocità effettiva totale per tutti i protocolli.

Se il protocollo è *HTTP*, viene segnalata solo la velocità effettiva per il traffico HTTP.

L'utente può inoltre specificare l'intervallo temporale in cui la metrica deve essere segnalata. Gli intervalli di tempo supportati sono:

* 1 ora
* 6 ore
* 12 ore
* 24 ore
* 1 settimana
* 2 settimane

Il numero di punti dati segnalati è più o meno lo stesso per ogni intervallo temporale.  
Ad esempio, se l'intervallo è 1 ora, ogni punto dati rappresenta 5 minuti di dati.

Se l'intervallo è 2 settimane, ogni punto dati rappresenta 24 ore di dati.

La seguente tabella mostra come i punti dati vengono ricavati dall'intervallo temporale:

| Intervallo temporale | Precisione punto dati | Numero di punti dati |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
| 1 ora    | 5 minuti | 12   |
| 6 ore   | 30 minuti | 12  |
| 12 ore  | 1 ora | 12 |
| 24 ore  | 2 ore | 12 |
| 1 settimana    | 12 ore | 12 |
| 2 settimane  | 24 ore | 12 |

## Come abilitare il monitoraggio delle metriche
{: #how-to-enable-metrics-monitoring}

Per poter richiamare le metriche di monitoraggio devi collegare il tuo account SoftLayer al tuo account IBM© Cloud. Fai riferimento a [questo argomento](/docs/account?topic=account-unifyingaccounts#link_accounts) per ulteriori informazioni.
