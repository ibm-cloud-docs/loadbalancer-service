---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: faq, questions, load balancer, dns, port, traffic, connection, health check, vmware, tls, ssl

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:faq: data-hd-content-type='faq'}
{:note: .note}
{:important: .important}

# FAQ per IBM Cloud Load Balancer
{: #faqs-for-ibm-cloud-load-balancer}

Questa sezione contiene le risposte ad alcune domande frequenti sul servizio IBM© Cloud Load Balancer.

## Quante opzioni di bilanciamento del carico sono disponibili in {{site.data.keyword.BluSoftlayer_notm}}?
{: faq}

Per un confronto dettagliato delle offerte del programma di bilanciamento del carico di IBM, fai riferimento a [Esplora i programmi di bilanciamento del carico](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-explore).

## Posso utilizzare un nome DNS differente per il mio programma di bilanciamento del carico?
{: faq}

Mentre il nome DNS assegnato automaticamente al programma di bilanciamento del carico non è personalizzabile, puoi aggiungere un record del nome canonico (CNAME) che faccia puntare il tuo nome DNS preferito al nome DNS del programma di bilanciamento del carico assegnato automaticamente.

Ad esempio, se il tuo numero di account è 123456, il tuo programma di bilanciamento del carico viene distribuito nel data center `dal09` e il suo nome è `myapp`, il nome DNS del programma di bilanciamento del carico assegnato automaticamente è `myapp-123456-dal09.lb.bluemix.net`. Il tuo nome DNS preferito è `www.myapp.com`. Puoi aggiungere un record CNAME (tramite il provider DNS che utilizzi per gestire myapp.com) che faccia puntare `www.myapp.com` al nome DNS del programma di bilanciamento del carico myapp-12345-dal09.lb.bluemix.net`.

## Qual'è il numero massimo di porte virtuali che posso definire con il mio servizio del programma di bilanciamento del carico?
{: faq}

Mentre si tenta di creare un nuovo servizio del programma di bilanciamento del carico, puoi definire fino a due porte virtuali. Puoi definire ulteriori porte dopo aver creato il servizio. Il numero massimo di porte virtuali è 10.

## Qual'è il numero massimo di istanze di calcolo che posso associare al mio programma di bilanciamento del carico?
{: faq}

50.

## Le mie istanze di calcolo di backend possono trovarsi su una sottorete diversa da quella del programma di bilanciamento del carico?
{: faq}

Sì, il programma di bilanciamento del carico e le istanze di calcolo connesse ad esso possono trovarsi su sottoreti diverse, ma lo **spanning delle VLAN** deve essere abilitato affinché il programma di bilanciamento del carico possa comunicare e inoltrare le richieste all'istanza di calcolo. Fai riferimento a [Risoluzione dei problemi dello spanning delle VLAN](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-vlan-spanning-troubleshooting) per ulteriori informazioni.

## Quali sono le impostazioni predefinite e i valori consentiti per i vari parametri del controllo di integrità?
{: faq}

Le impostazioni predefinite e i valori consentiti sono elencati di seguito:

* **Intervallo controllo di integrità:** il valore predefinito è 5 secondi, l'intervallo è 2 – 60 secondi
* **Timeout risposta controllo di integrità:** il valore predefinito è 2 secondi, l'intervallo è 1 – 59 secondi
* **Numero massimo di tentativi:** il valore predefinito di tentativi è 2 e l'intervallo è da 1 a 10 tentativi

Il valore del timeout della risposta del controllo di integrità deve sempre essere inferiore al valore dell'intervallo del controllo di integrità.
{: note}

## Posso utilizzare le istanze di calcolo che risiedono nei data center remoti con questo servizio?
{: faq}

Ti raccomandiamo che il tuo servizio del programma di bilanciamento del carico e le tue istanze di calcolo risiedano localmente nello stesso data center. La GUI (graphical interface) del servizio del programma di bilanciamento del carico non visualizzerà le istanze di calcolo da altri data center remoti. Tuttavia, la GUI includerà le istanze di calcolo da altri data center nella stessa città (ad esempio, i data center i cui nomi condividono le prime tre lettere come DALxx). Puoi comunque utilizzare l'interfaccia API per aggiungere le istanze di calcolo da qualsiasi data center remoto.

## Quale versione TLS è supportata con l'offload SSL?
{: faq}

Il servizio Cloud Load Balancer supporta TLS 1.2 con terminazione SSL.

Il seguente elenco mostra le cifrature supportate (elencate in ordine di precedenza):  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## Qual'è il numero massimo di istanze del servizio Load Balancer che posso creare nel mio account?
{: faq}

Al momento, puoi creare fino a 50 istanze del servizio. Se hai bisogno di più istanze, contatta il supporto IBM.

## Il servizio IBM Cloud Load Balancer può essere utilizzato con VMWare?
{: faq}

Le macchine virtuali VMWare assegnate agli indirizzi privati portatili SoftLayer possono essere specificate come server di backend al programma di bilanciamento del carico. Questa funzione è al momento disponibile solo utilizzando l'API e non la IU web (GUI). Gli IP privati portatili aggiunti utilizzando l'API vengono visualizzati come "Sconosciuti" nella GUI, poiché non sono assegnati da SoftLayer. Tieni presente che questo tipo di configurazione può essere utilizzato anche con altri hypervisor come Xen e KVM.

Le macchine virtuali VMWare assegnate a indirizzi non SoftLayer (come le reti VMWare NSX) non possono essere aggiunte direttamente come server di backend al programma di bilanciamento del carico. Tuttavia, a seconda della tua configurazione, può essere possibile configurare un intermediario, come un gateway NSX, che dispone di un indirizzo privato SoftLayer come server di backend al programma di bilanciamento del carico (con i server attuali che sono VM collegate alle reti gestite da VMware NSX).

## Se scelgo di utilizzare una VLAN pubblica nel mio account per distribuire il mio programma di bilanciamento del carico e ho un firewall distribuito sulla mia VLAN pubblica, quali configurazioni sono necessarie per il mio firewall in modo che funzioni con il mio servizio del programma di bilanciamento del carico?
{: faq}

La porta TCP 56501 viene utilizzata per la gestione. Assicurati che il traffico a questa porta, così come alle porte della tua applicazione, non sia bloccato dal tuo firewall, altrimenti il provisioning del programma di bilanciamento del carico non funzionerà.

## Cosa devo fare se non riesco a vedere le metriche di monitoraggio di un programma di bilanciamento del carico esistente dopo aver collegato il mio account Softlayer a IBM Cloud?
{: faq}

Le metriche di monitoraggio non saranno disponibili per i programmi di bilanciamento del carico esistenti dopo il collegamento degli account. Devi ricreare i programmi di bilanciamento del carico oppure contattare il supporto. Le metriche di monitoraggio per i programmi di bilanciamento del carico appena creati saranno disponibili.

## Gli indirizzi IP del programma di bilanciamento del carico sono fissi?
{: faq}

Non possiamo garantire che gli indirizzi IP del programma di bilanciamento del carico rimangano costanti a causa dell'elasticità integrata nel servizio. Poiché aumenta o diminuisce, vedrai cambiamenti negli IP disponibili associati al FQDN della tua istanza.

Devi utilizzare FQDN e non gli indirizzi IP memorizzati nella cache.
{: note}

## Se ho un firewall distribuito sulla mia VLAN privata, quali configurazioni sono necessarie affinché funzioni con il mio servizio del programma di bilanciamento del carico?
{: faq}

Fai riferimento all'argomento [Intervalli IP di IBM Cloud](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges) per informazioni su come consentire intervalli IP attraverso il firewall.

## Perché non posso vedere la mia configurazione L7 nell'interfaccia utente?
{: faq}

Al momento, il supporto L7 è disponibile solo tramite API pubbliche, ma la funzionalità sarà presto disponibile nell'interfaccia utente. Fai riferimento alla sezione L7 della [Documentazione API](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-api-reference) per ulteriori informazioni.

## Di quali informazioni ho bisogno per inviare un ticket di supporto?
{: faq}

Per inviare un ticket di supporto, specifica il nome prodotto ("IBM Cloud Load Balancer"), l'UUID del tuo programma di bilanciamento del carico (se possibile) e il tuo numero di account Softlayer. Puoi trovare l'UUID nell'URL dopo esserti spostato alla pagina di panoramica di un determinato programma di bilanciamento del carico.
