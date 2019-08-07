---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: about, load balancer, overview, features

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Informazioni su {{site.data.keyword.loadbalancer_full}}
{: #about-ibm-cloud-load-balancer}

Il servizio {{site.data.keyword.loadbalancer_full}} aiuta i clienti a migliorare la disponibilità delle proprie applicazioni critiche per il business distribuendo il traffico tra più istanze del server dell'applicazione e inoltrando il traffico solo alle istanze integre.

## Panoramica sulle funzioni
{: #overview-of-features}

Il servizio {{site.data.keyword.loadbalancer_full}} offre le seguenti funzioni:

* Programma di bilanciamento del carico (verso internet) pubblico
	* Servizio accessibile pubblicamente tramite il proprio nome di dominio completo (FQDN)
	* Istanze del server di backend su sottoreti private
* Programma di bilanciamento del carico interno
	* Servizio accessibile privatamente tramite il proprio nome di dominio completo (FQDN)
	* Le richieste client vengono instradate sulla rete privata
	* Istanze del server di backend su sottoreti private
* Bilanciamento del carico di base
	* Distribuzione del traffico in base alle informazioni sulla porta dell'applicazione di livello 4
	* Supporto per le applicazioni basate su TCP, HTTP e HTTPS
	* Vari metodi di bilanciamento del carico come round robin (RR), round robin ponderato e numero minimo di connessioni
	* Bilanciamento del carico tra il server virtuale e le istanze di calcolo bare metal presenti localmente in un data center
* Controlli di integrità del server
	* Monitoraggio periodico dell'integrità del server per garantire che il traffico venga inoltrato solo ai server integri
	* Controlli di integrità di livello 4 per le porte TCP e di livello 7 per la porta HTTP
* Offload SSL
	* Terminazione del traffico (HTTPS) SSL in entrata utilizzando la comunicazione HTTP di testo semplice con i server di backend
* Gestione del traffico avanzata
	* Persistenza client (persistenza sessione)
	* Numero di connessioni massimo per porta virtuale
* Facile gestione utilizzando un'interfaccia grafica intuitiva e un'API
* Affidabilità integrata
* Prezzi basati sull'utilizzo
* Monitoraggio
    * Monitora le metriche Velocità effettiva, Connessioni attive e Frequenza di connessione per i protocolli HTTP, HTTPS e TCP negli intervalli di tempo specificati dall'utente. Fai riferimento a [Monitoraggio delle metriche](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer) per ulteriori dettagli.
* Supporto L7
    * Il traffico HTTP/HTTPS viene instradato a servizi di backend diversi in base all'intestazione HTTP e utilizzando politiche e regole. Le regole vengono utilizzate per classificare il traffico e si basano sui campi di intestazione HTTP. Quando il traffico soddisfa tutte le regole, viene eseguita un'azione specificata dalla politica.
* Supporto regione multizona (o MZR, Multi-Zone Region)
    * I nodi del programma di bilanciamento del carico vengono istanziati in diversi data center di una MZR. Fai riferimento a [Panoramica della regione multizona (o MZR, Multi-Zone Region)](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview) per ulteriori informazioni.
* Log di dati
    * Con i log di dati abilitati, i log del programma di bilanciamento del carico verranno inoltrati al [servizio IBM Cloud Log Analysis ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}. I clienti possono visualizzare i loro log di dati utilizzando il [servizio IBM Cloud Log Analysis ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}.
