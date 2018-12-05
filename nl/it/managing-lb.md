---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Monitoraggio e gestione del tuo servizio
Puoi modificare la tua configurazione o monitorare le tue prestazioni di servizio facendo clic sull'URL del nome del servizio nella pagina di riepilogo del programma di bilanciamento del carico.  

Puoi vedere l'**indirizzo FQDN (fully-qualified domain name)** della tua istanza di servizio del programma di bilanciamento del carico sotto il nome del servizio. Gli utenti finali possono connettersi alla tua applicazione tramite questo indirizzo FQDN. Tieni presente che gli indirizzi IP pubblico e privato del servizio del programma di bilanciamento del carico non vengono esposti all'esterno, viene esposto solo l'indirizzo FQDN.  

<img src="images/fqdn-address.png" alt="disegno" style="width: 300px;"/>

La scheda **Overview** fornisce le informazioni sullo stato di livello superiore del tuo servizio. Visualizza l'integrità corrente dei tuoi server delle applicazioni e delle loro porte. Fornisce anche un riepilogo rapido delle prestazioni di sistema - velocità di elaborazione, frequenza di connessione, connessioni simultanee ecc.  

Vai alla scheda **Monitoring** per visualizzare i grafici in tempo reale delle tue prestazioni di sistema. Questi grafici possono essere visualizzati per ogni singola porta dell'applicazione e per diversi periodi di tempo.  

<img src="images/monitor-lb.png" alt="disegno" style="width: 300px;"/>

Puoi modificare la tua configurazione esistente andando alle schede **Protocols**, **Server Instances** e **Health Checks**. Ad esempio, vai alla scheda Protocols per definire le porte dell'applicazione aggiuntive o per personalizzare l'elenco di cifrature SSL.  

<img src="images/protocols-monitor.png" alt="disegno" style="width: 300px;"/>
