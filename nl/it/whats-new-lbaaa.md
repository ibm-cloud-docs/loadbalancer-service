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


# Novità

Scopri ulteriori informazioni su funzioni nuove e aggiornate in IBM Cloud Load Balancer.

## Agosto 2018
### Supporto L7
IBM Cloud Load Balancer ora supporta il bilanciamento del carico L7. Con il supporto L7 (Livello 7), il traffico può essere reindirizzato a un URL, rifiutato o distribuito ai membri del pool L7, inclusi bare-metal e VSI (virtual-server instances). Il traffico dati in entrata viene classificato utilizzando le politiche e le regole L7. Le politiche definiscono quale azione eseguire quando il traffico dati soddisfa le regole associate ad esse. 

Fai riferimento a [Bilanciamento del carico L7](l7-explained.html) per ulteriori dettagli.

## Aprile 2018
### Scalabilità orizzontale
IBM Cloud Load Balancer viene ora aumentato quando il suo carico cresce e ridotto quando decresce. Quando crei un programma di bilanciamento del carico, viene avviato con due applicazioni, ma il numero delle applicazioni può essere aumentato a 16 (fino a questo momento) mentre il sistema di monitoraggio rileva un aumento nel carico. Gli indirizzi IP di ogni applicazione attiva vengono aggiunti come A-Record DNS al nome di dominio completo (FQDN) del programma di bilanciamento del carico.

### Programma di bilanciamento del carico interno
È ora disponibile una versione “interna” molto richiesta del nostro IBM Cloud Load Balancer. Questo programma di bilanciamento del carico non è esposto pubblicamente, ma può ancora essere utilizzato per bilanciare le applicazioni nella loro rete privata IBM Cloud (in una distribuzione a più livelli, per istanza, come mostrato nella figura).  

![Programma di bilanciamento del carico interno](./images/InternalLB.png)

È sia sicuro che coerente con le versioni precedenti di IBM Cloud Load Balancer sul lato pubblico 

### Metriche di monitoraggio
Puoi ora utilizzare il servizio “IBM Cloud Monitoring” per monitorare le seguenti metriche delle prestazioni associate al tuo programma di bilanciamento del carico e alla tua applicazione:

* Velocità effettiva
* Frequenza di connessione
* Connessioni attive

![Metriche di monitoraggio](./images/Metrics.png)

Vengono raccolte e visualizzate fino a due settimane di esempi dalla IU web del programma di bilanciamento del carico. I dati possono essere visualizzati anche nel portale del servizio IBM Cloud Monitoring. Se hai bisogno dei dati per più di due settimane, a seconda del volume delle altre metriche cloud che potresti dover inviare alla tua istanza di monitoraggio cloud, potresti aver bisogno di aggiornare il tuo piano di monitoraggio. Fai riferimento a [Monitoraggio delle metriche](monitoring-metrics.html) per ulteriori dettagli

Questa funzione richiede che i tuoi account IBM Cloud IaaS e PaaS siano collegati, con alcuni [semplici passi ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/account/softlayerlink.html#link_user_account). 

### Personalizzazione della suite di cifratura
Puoi ora personalizzare le suite di cifratura che vengono utilizzate quando il programma di bilanciamento del carico viene configurato per la terminazione SSL. 

Quando abiliti la terminazione SSL su IBM Cloud Load Balancer (selezionando **HTTPS** come protocollo di frontend), abilitiamo una serie di suite di cifratura predefinita attentamente selezionata che è conforme alle migliori procedure di sicurezza. IBM mantiene sotto stretto controllo ogni nuova vulnerabilità che può venire rilevata e aggiorna l'elenco di conseguenza. Questo, insieme agli aggiornamenti di sicurezza continui dei componenti software e hardware, consente di mantenere le tue applicazioni sempre sicure.

Fai riferimento a [Personalizza suite di cifratura](custom-ciphers.html) per ulteriori dettagli. 
