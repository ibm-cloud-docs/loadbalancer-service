---

copyright:
  years: 2018
lastupdated: "2018-11-21"

keywords: error, message, troubleshooting, problems

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

# Risoluzione dei problemi per i messaggi di errore
{: #error-message-troubleshooting}

Questo argomento fornisce le informazioni sui messaggi di errore comuni che puoi riscontrare mentre crei/aggiorni un'istanza di {{site.data.keyword.loadbalancer_full}}.

| Errore | Spiegazione  | Soluzione  |
| ------------- | ------------- | ----- |
| `È stato raggiunto il numero massimo di `n` programmi di bilanciamento del carico.`| Consentiamo solo 50 istanze del programma di bilanciamento del carico per account. | Assicurati di avere massimo 50 istanze del programma di bilanciamento del carico per account. |
| `È stato raggiunto il numero massimo di `n` determinati protocolli nell'ordine del prodotto del programma di bilanciamento del carico.` | Possono essere aggiunti solo due protocolli durante il provisioning di un programma di bilanciamento del carico.  | Se hai bisogno di più protocolli, dopo il provisioning puoi aggiungerne fino a dieci dalla scheda **Protocols** nel flusso di gestione del programma di bilanciamento del carico. Per ulteriori informazioni, consulta [monitoraggio e gestione del tuo servizio](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `È stato raggiunto il numero massimo di `n` determinate istanze del server nell'ordine del prodotto del programma di bilanciamento del carico.` | Possono essere aggiunti solo dieci server durante il provisioning di un programma di bilanciamento del carico. | Se hai bisogno di altri server, dopo il provisioning puoi aggiungerne fino a 50 dalla scheda **Server Instances** nel flusso di gestione del programma di bilanciamento del carico. Per ulteriori informazioni, consulta [monitoraggio e gestione del tuo servizio](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `Il nome del programma di bilanciamento del carico deve essere una stringa e deve contenere da un minimo di 1 a un massimo di 40 caratteri.` | Il nome del programma di bilanciamento del carico è obbligatorio. Utilizza solo caratteri alfanumerici (o i caratteri speciali '-' e '.') per il nome. Il nome non deve iniziare o terminare con un carattere speciale e deve avere una lunghezza massima di 40 caratteri. | Immetti un nome univoco del programma di bilanciamento del carico. Ad esempio, "ui-servers" o "backend-servers".|
| `Rilevato errore di formato in un determinato nome del programma di bilanciamento del carico.` | Il nome del programma di bilanciamento del carico è obbligatorio. Utilizza solo caratteri alfanumerici (o i caratteri speciali '-' e '.') per il nome. Il nome non deve iniziare o terminare con un carattere speciale e deve avere una lunghezza massima di 40 caratteri. | Immetti un nome univoco del programma di bilanciamento del carico. Ad esempio, "ui-servers" o "backend-servers".|
| `Esiste già un programma di bilanciamento del carico con lo stesso nome (non sensibile al maiuscolo/minuscolo).` | Esiste un programma di bilanciamento del carico con lo stesso nome. | Immetti un nome del programma di bilanciamento del carico univoco per proseguire, ad esempio, "ui-servers" o "backend-servers". |
| `La descrizione del programma di bilanciamento del carico deve essere una stringa e non deve superare 255 caratteri.` | La descrizione del programma di bilanciamento del carico deve essere una stringa e non deve superare 255 caratteri. | Limita la descrizione a 255 caratteri. |
| `La porta di frontend 80 è già utilizzata.` | Puoi aver immesso una porta di frontend già in uso. | Immetti una porta di frontend univoca. |
| `La porta di backend deve essere un numero intero.` | Puoi aver immesso un valore di porta di backend non valido. | Immetti un numero di porta di backend compreso tra 1 e 65535. |
| `Poiché il protocollo e la porta non sono modificabili nel monitoraggio dell'integrità, questo errore non è possibile nell'interfaccia utente.`| La tua sottorete privata non è di tipo standard e non può essere utilizzata per creare il programma di bilanciamento del carico. | Contatta il supporto IBM. |
| `La sottorete privata `xyz` deve avere almeno `n` indirizzi IP liberi.` | La sottorete privata selezionata non ha indirizzi IP liberi. | Controlla questi [passi per la risoluzione dei problemi](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting) per ulteriori informazioni. |
| `La VLAN della sottorete privata specificata si trova sul router `xyz`. Tuttavia, non sono state trovate VLAN pubbliche con `n` IP liberi sullo stesso router.` | Ciò si verifica perché hai selezionato l'opzione **Allocate from public subnet from this account** durante il provisioning. | Seleziona invece **Allocate from IBM System Pool** oppure contatta il supporto IBM.|
| `La VLAN della sottorete privata specificata si trova sul router `xyz`. Tuttavia, non sono state trovate sottoreti pubbliche con `n` IP liberi con la VLAN sullo stesso router.` | Ciò si verifica perché hai selezionato l'opzione **Allocate from public subnet from this account** durante il provisioning. | Seleziona invece **Allocate from IBM System Pool** oppure contatta il supporto IBM.|
| `La nuova descrizione fornita deve essere una stringa.`| Puoi aver immesso una descrizione non valida. | Immetti una descrizione valida del programma di bilanciamento del carico che non superi 255 caratteri. |
| `È necessario un elemento di fatturazione per elaborare un annullamento per il programma di bilanciamento del carico uuid=aaaa-bbbb-cccc-dddd.` | Le informazioni di fatturazione sono mancanti o non sono valide per il tuo account e il programma di bilanciamento del carico non può essere annullato. | Contatta il supporto IBM.|
| `Si è verificato un errore interno. I dati non possono essere richiamati.` | I dati delle metriche non possono essere richiamati | Ricarica la pagina. Se il problema persiste, contatta il supporto IBM. |
| `La porta di frontend deve essere un numero intero compreso tra 1 e 65535 escluso l'intervallo 56500-56520.` | Puoi aver immesso un numero di porta di frontend compreso tra 56500 e 56520. | Immetti un numero di porta univoco compreso tra 1 e 65535, escludendo però l'intervallo da 56500 a 56520. |
| `La porta di backend deve essere un numero intero.` | Puoi aver immesso un valore di porta di backend non valido. | Immetti un numero di porta di backend compreso tra 1 e 65535. |
| `La porta di backend deve essere un numero intero compreso tra 1 e 65535 escluso l'intervallo 56500-56520.` | Puoi aver immesso una porta di backend compresa tra 56500 e 56520.| Immetti un numero di porta di backend compreso tra 1 e 65535, escludendo però l'intervallo da 56500 a 56520. |
| `Il protocollo di backend HTTP non è compatibile con il protocollo di frontend TCP.` | Puoi aver selezionato una combinazione di protocollo di backend e di protocollo di frontend incompatibile. | Seleziona una combinazione di protocollo di backend e di frontend valida, nel formato: `<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Il peso membro <some value> è stato fornito per il membro abcd-xxxx-yyyy-2222. Il valore di peso consentito è 0-100 `| Puoi aver immesso un peso non valido. | Immetti un peso valido compreso tra 0 e 100. |
| `Si è verificato un problema nel recupero dei server.` | Può verificarsi a causa di problemi di timeout di rete. | Ricarica la pagina. Se il problema persiste, contatta il supporto IBM.|
