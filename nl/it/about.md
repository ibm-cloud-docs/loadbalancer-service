---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

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

# Informazioni

Il servizio IBM Cloud Load Balancer aiuta i clienti a migliorare la disponibilità delle proprie applicazioni critiche per il business distribuendo il traffico tra più istanze del server dell'applicazione e inoltrando il traffico solo alle istanze integre.

## Panoramica sulle funzioni
Il servizio IBM Cloud Load Balancer offre le seguenti funzioni:

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
    * Monitora le metriche Velocità effettiva, Connessioni attive e Frequenza di connessione per i protocolli HTTP, HTTPS e TCP negli intervalli di tempo specificati dall'utente. Fai riferimento a [Monitoraggio delle metriche](monitoring-metrics.html) per ulteriori dettagli.
* Supporto L7
    * Il traffico HTTP/HTTPS viene instradato a servizi di backend diversi in base all'intestazione HTTP e utilizzando politiche e regole. Le regole vengono utilizzate per classificare il traffico e si basano sui campi di intestazione HTTP. Quando il traffico soddisfa tutte le regole, viene eseguita un'azione specificata dalla politica.     
