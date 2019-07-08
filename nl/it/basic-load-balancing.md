---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: basics, load balancing

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

# Esecuzione dei principi di base di IBM Cloud Load Balancer
{: #performing-ibm-cloud-load-balancer-basics}

Il servizio IBM© Cloud load balancer distribuisce il traffico tra più istanze server (server virtuale e bare metal) che risiedono localmente, nello stesso data center.

## Programma di bilanciamento del carico pubblico
{: #public-load-balancer}

Viene assegnato un nome di dominio completo e accessibile pubblicamente alla tua istanza del servizio del programma di bilanciamento del carico. Devi utilizzare questo nome dominio per accedere alle tue applicazioni ospitate dietro il servizio del programma di bilanciamento del carico. Questo nome dominio potrebbe essere registrato con uno o più indirizzi IP pubblici. Gli indirizzi IP pubblici e il numero di indirizzi IP pubblici potrebbero cambiare nel tempo in base alle attività di manutenzione e ridimensionamento, che sono trasparenti agli utenti finali. Le istanze di calcolo di backend che ospitano la tua applicazione devono essere su una rete privata cloud IBM.

Ti raccomandiamo di eseguire il provisioning dei tuoi server di backend come ‘solo privato’, a meno che non richiedano la connettività pubblica diretta. Questa procedura ti aiuta ad avere una migliore protezione e a conservare il tuo indirizzo IP pubblico. Le applicazioni ospitate in questi server di backend sono ancora accessibili sulla rete pubblica utilizzando il programma di bilanciamento del carico.
{: note}  

Puoi scegliere di assegnare gli indirizzi IP pubblici del programma di bilanciamento del carico da un pool di sistema IBM (predefinito) o da una VLAN pubblica nel tuo account durante la creazione della tua istanza del servizio del programma di bilanciamento del carico.

## Programma di bilanciamento del carico interno
{: #internal-load-balancer}

Il programma di bilanciamento del carico interno è accessibile solo all'interno della rete privata IBM Cloud.

Proprio come a un programma di bilanciamento del carico pubblico, alla tua istanza del servizio del programma di bilanciamento del carico interno viene assegnato anche un nome di dominio completo. Tuttavia, questo nome dominio viene registrato con uno o più indirizzi IP privati.

In modo simile a un programma di bilanciamento del carico pubblico, gli indirizzi IP privati e il loro numero potrebbero cambiare nel tempo in base alle attività di manutenzione e ridimensionamento, che sono trasparenti agli utenti finali.

Anche le istanze di calcolo di backend che ospitano la tua applicazione devono essere sulla rete privata IBM Cloud.
{: note}

## Protocolli/Porte applicazione di backend e frontend
{: #front-end-and-back-end-application-ports-protocols}

Puoi definire fino a dieci porte (protocolli) dell'applicazione di frontend e associarle alle rispettive porte (protocolli) nei server dell'applicazione di backend. Il nome di dominio completo assegnato alla tua istanza del servizio del programma di bilanciamento del carico e le porte dell'applicazione di frontend sono esposti con il mondo esterno. Le richieste utente in entrata vengono ricevute su queste porte.

D'altra parte, le porte di backend sono conosciute solo internamente. Queste porte di backend potrebbero non essere le stesse delle porte di frontend. Ad esempio, il programma di bilanciamento del carico può essere configurato per ricevere il traffico web/HTTP in entrata su nella porta di frontend 80, mentre i server di backend sono in ascolto sulla porta personalizzata 81.

Le porte/protocolli di frontend supportate sono HTTP, HTTPS e TCP. Le porte/protocolli di backend supportate sono anche HTTP, HTTPS e TCP. Il traffico HTTPS in entrata deve essere terminata nel programma di bilanciamento del carico per consentire la comunicazione HTTP di testo semplice con il server di backend. Se il protocollo di backend è HTTPS, il traffico verrà crittografato tra il programma di bilanciamento del carico e i server di backend.

### Considerazioni
{: #considerations}

* Durante la configurazione iniziale, puoi possibile definire solo fino a due porte di frontend. Quando un programma di bilanciamento del carico viene creato, puoi modificare la configurazione della porta per definire ulteriori porte, fino al massimo di dieci porte.
* Tutte le dieci porte di frontend devono essere associate alla stessa serie di istanze del server di backend.
* Il numero massimo di istanze del server che possono essere posizionate dietro a un programma di bilanciamento del carico è 50.
* L'intervallo di porte compreso tra 56500 e 56520 è riservato per scopi di gestione e non può essere utilizzato come porte virtuali di frontend.
* La porta TCP 56501 viene utilizzata per la gestione. Se scegli di assegnare gli indirizzi IP pubblici del programma di bilanciamento del carico dalla tua VLAN pubblica, assicurati che il traffico a questa porta di gestione così come alle porte della tua applicazione non sia bloccato da alcun firewall che puoi aver distribuito alle tue VLAN pubbliche. Questo non è obbligatorio se scegli l'opzione del pool di sistema IBM per assegnare gli indirizzi IP pubblici del programma di bilanciamento del carico.

## Metodi di bilanciamento del carico
{: #load-balancing-methods}

I seguenti tre metodi di bilanciamento del carico sono disponibili per la distribuzione del traffico tra i server dell'applicazione di backend:

* **Round Robin:** Round Robin è il metodo di bilanciamento del carico predefinito. Con questo metodo, il programma di bilanciamento del carico inoltra le connessioni client in entrata in modalità round robin ai server di backend. Di conseguenza, tutti i server di backend ricevono all'incirca un numero uguale di connessioni client.

* **Round Robin ponderato:** con questo metodo, il programma di bilanciamento del carico inoltra le connessioni client in entrata ai server di backend in base al peso assegnato a tali server. Ad ogni server viene assegnato un peso predefinito di 50, che può essere personalizzato con qualsiasi valore compreso tra 0 e 100.

	Ad esempio, se ci sono tre applicazioni server A, B e C, e i loro pesi sono personalizzati con 60, 60 e 30 rispettivamente, i server A e B riceveranno lo stesso numero di connessioni, mentre il server C ne riceverà la metà.


	Reimpostare il peso su ‘0’ significa che nessuna nuova connessione sarà inoltrata a tale server, ma tutto il traffico esistente continuerà a fluire finché rimane attivo. L'utilizzo di un peso di ‘0’ può aiutare a terminare un server correttamente e a rimuoverlo dalla rotazione del servizio.
	{: note}

	Il valori del peso del server sono applicabili solo con il metodo 'round robin ponderato'. Vengono ignorati con i metodi di bilanciamento del carico 'round robin' e 'numero minimo di connessioni'.
	{: note}

* **Numero minimo di connessioni:** con questo metodo, l'istanza del server che inoltra il numero minimo di connessioni a un ora specificata riceve la successiva connessione client.

## Scalabilità orizzontale
{: #horizontal-scaling}

Il programma di bilanciamento del carico modifica la propria capacità automaticamente in base al carico. Quando questo si verifica, potresti visualizzare un cambiamento nel numero di indirizzi IP associati al nome DNS del programma di bilanciamento del carico.
