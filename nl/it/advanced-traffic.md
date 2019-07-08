---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: traffic, management, connection, persistence

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

# Gestione del traffico avanzata con IBM Cloud Load Balancer
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

Questa sezione tratta di diverse funzioni di gestione del traffico avanzate disponibili con il servizio IBM Cloud Load Balancer.

## Numero massimo di connessioni
{: #max-connections}

Utilizza la configurazione ‘numero massimo di connessioni’ per limitare il numero massimo di connessioni contemporanee in una porta virtuale di frontend fornita. Per impostazione predefinita, non è specificato alcun limite. Il numero massimo di connessioni contemporanee in una porta virtuale di frontend fornita o per tutte le porta virtuali di frontend nel sistema è 15000.  

## Persistenza sessione
{: #session-persistence}

Il programma di bilanciamento del carico supporta la persistenza della sessione sulle porte VIP fornite che si basano sull'IP di origine (`source IP`) della connessione. Ad esempio, se la persistenza della sessione è abilitata per la porta 80 (HTTP), allora i successivi tentativi di connessione HTTP dallo stesso client (stesso IP di origine) vengono conservati nello stesso server di backend. Questa funzione è disponibile per tutti e tre i protocolli supportati (HTTP, HTTPS e TCP).

Il programma di bilanciamento del carico supporta un massimo di 10.000 voci di persistenza client. La data di scadenza per queste tre voci è 10 minuti. Ulteriori richieste ricevute dallo stesso client dopo 10 minuti possono venire inoltrate a un server di backend differente. Se la voce di persistenza della sessione non scade, ma la porta di backend è diventata non integra, viene selezionato un nuovo server per inoltrare tutte le seguenti connessioni client.  

## Keepalive HTTP
{: #http-keep-alive}
Il programma di bilanciamento del carico supporta `Keepalive HTTP` finché è abilitato sui server client e di backend. Il programma di bilanciamento del carico tenta di riutilizzare le connessioni lato server per aumentare l'efficienza della connessione e ridurre la latenza.

## Timeout di connessione
{: #connection-timeouts}
I seguenti valori di timeout vengono utilizzati dal programma di bilanciamento del carico. Questi valori non possono essere personalizzati in questo momento.

| Nome | Descrizione | Timeout |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | ------------------- |
| Tentativo di connessione lato server    | La finestra di tempo massimo che il programma di bilanciamento del carico può utilizzare per stabilire la connessione TCP con il server di backend. Se il tentativo di connessione ha esito negativo, il programma di bilanciamento del carico tenterà con il successivo server disponibile, in base al metodo di bilanciamento del carico che hai configurato. | 5 secondi   |
| Connessione inattiva lato client  | Il tempo di inattività massimo, dopo di cui il programma di bilanciamento del carico interrompe la connessione al client, se il client non è riuscito a chiudere la propria connessione correttamente.| 50 secondi  |
| Connessione inattiva lato server | Il tempo di inattività massimo (con la configurazione del protocollo di back-end di TCP), dopo di cui il programma di bilanciamento del carico chiude la connessione lato server. Con la configurazione del protocollo di back-end di HTTP, se il programma di il bilanciamento del carico non riesce a ricevere una risposta alla sua richiesta HTTP nella finestra di timeout di inattività, sarà restituito un messaggio di errore al client finale.                                | 50 secondi |
{: caption="Tabella 1. Valori di timeout del programma di bilanciamento del carico" caption-side="top"}

## Conservazione dell'indirizzo IP del client finale
{: #preserving-end-client-ip-address}

Il programma di bilanciamento del carico funziona come un proxy inverso, che termina il traffico in entrata dal client. Stabilisce una connessione separata all'istanza del server di backend, utilizzando il proprio indirizzo IP. Per le connessioni HTTP con i server di backend (per connessioni HTTPS o HTTP di frontend), il programma di bilanciamento del carico conserva l'indirizzo IP del client originale includendolo nell'intestazione `X-Forwarded-For HTTP`. Per le connessioni TCP, le informazioni IP del client originale non vengono conservate.
