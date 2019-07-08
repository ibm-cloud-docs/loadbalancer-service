---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: parameters, load balancing, configure, protocol, health check

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

# Configurazione dei parametri di IBM Cloud Load Balancer
{: #configuring-ibm-cloud-load-balancer-parameters}

Una volta che hai [creato un programma di bilanciamento del carico](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started), puoi configurarlo per il bilanciamento del carico elastico. Per eseguire tale operazione:

1. Assegna un nome al tuo programma di bilanciamento del carico e, facoltativamente, aggiungi una descrizione.

	<img src="images/lb-config-basic.png" alt="disegno" style="width: 300px;"/>

2. Immetti i dettagli del tuo profilo dell'applicazione identificando i protocolli e le porte su cui è in ascolto la tua applicazione. Puoi utilizzare la stessa configurazione sia per il frontend che per il backend oppure esporre una porta di frontend diversa (ad esempio, per scopi di sicurezza).

3. Il metodo di bilanciamento del carico predefinito è **Round Robin**. Puoi cambiarlo in **Round Robin ponderato** o **Numero minimo di connessioni** dall'elenco a discesa a seconda delle esigenze della tua applicazione.

4. Facoltativamente, puoi abilitare **Session stickiness**. Se abilitato, tutte le richieste provenienti da un determinato utente finale (ad esempio, un utente con lo stesso IP di origine) verranno indirizzate allo stesso server di backend per un tempo "permanente (sticky)" definito dal sistema.

5. Puoi anche impostare il valore di **Maximum connection limit** in base alla tua applicazione.

6. Fai clic su **Add Protocol** per specificare le porte e i protocolli aggiuntivi su cui può essere in ascolto la tua applicazione. Assicurati che tutte le porte di frontend siano univoche. Come protocollo di frontend puoi scegliere HTTP, HTTPS o TCP.

	<img src="images/lb-add-protocol.png" alt="disegno" style="width: 300px;"/>

	Al momento della configurazione iniziale possono essere definite massimo due porte. Dopo aver creato l'istanza di servizio possono essere aggiunte altre porte. Consulta [Limitazioni per il numero di porte virtuali](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-) per ulteriori informazioni sul numero massimo di porte consentite.
{:note:}

7. IBM© Cloud Load Balancer termina le connessioni HTTPS (HTTP over SSL) in entrata e può comunicare in HTTP di testo semplice con i server delle applicazioni di backend e le attività SSL di offload intensive del processore provenienti dai tuoi server se il protocollo di backend viene selezionato come HTTP. Se il protocollo di backend selezionato è HTTPS, il traffico verrà crittografato tra il programma di bilanciamento del carico e i server di backend. Devi caricare il tuo certificato SSL. Seleziona uno dei tuoi certificati disponibili dall'elenco a discesa.  

	<img src="images/lb-ssl-cert.png" alt="disegno" style="width: 300px;"/>

	Se non hai un certificato esistente, fai clic su **Add a new Certificate**. Questa opzione ti porta ad un servizio certificati IBM Cloud in cui puoi acquistare un nuovo certificato o caricarne uno esistente.

	Una volta aggiunto il certificato, ritorna alla pagina di configurazione del programma di bilanciamento del carico e fai clic sull'icona di aggiornamento nell'elenco a discesa del certificato SSL per visualizzare e aggiungere il certificato che hai appena caricato.

	<img src="images/order-ssl-cert.png" alt="disegno" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="disegno" style="width: 300px;"/>

	Non devi mai eliminare i certificati associati ai listener HTTPS poiché tale operazione può causare problemi con la funzionalità.
  {: note}

8. Fai clic su **Next**.

## Configura i controlli di integrità
{: #configure-health-checks}

La definizione di controllo di integrità è obbligatoria per ciascuna delle porte dell'applicazione. Queste sono porte di backend identificate nel menu di configurazione di base precedente.

<img src="images/config-health-check.png" alt="disegno" style="width: 300px;"/>

Il sistema pre-popola una configurazione del controllo di integrità predefinita per queste porte di backend. Puoi personalizzare queste impostazioni per soddisfare le esigenze della tua applicazione.

* **Interval**: l'intervallo, in secondi, tra due tentativi di controllo di integrità consecutivi
* **Timeout**: il tempo massimo di attesa di una risposta ad una richiesta di controllo di integrità da parte del sistema
* **Max Trials**: il numero massimo di tentativi di controllo di integrità che verranno eseguiti dal sistema prima di dichiarare una porta non integra
* **Path**: il percorso URL HTTP per il controllo di integrità     

Fai clic su **Next** per abilitare la tua scelta.

## Operazioni successive
{: #what-s-next}

[Identifica le risorse della tua applicazione](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources), ad esempio i pool di origine e i meccanismi del controllo di integrità.
