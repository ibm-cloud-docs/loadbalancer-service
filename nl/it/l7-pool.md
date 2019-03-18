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

# Pool L7
{: #layer-7-pool}

Un pool L7 è un raggruppamento logico di server (membri) per la gestione delle richieste in entrata.

La funzione di bilanciamento del carico L7 può indirizzare il traffico in entrata a pool di backend diversi in base alle
politiche e alle regole. Questa funzione viene supportata associando più pool L7 a un programma di bilanciamento del carico. I pool L7 vengono utilizzati con le politiche L7 la cui azione è `redirect to pool`.

I pool L7 supportano solo HTTP come protocollo di backend.

## Persistenza sessione
La persistenza sessione può essere configurata per ciascun pool L7. Per ulteriori dettagli, esamina la  
[sezione di traffico avanzata](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer).

## Membri L7

I server di backend associati a un pool L7 sono denominati Membri L7.

Lo stesso server di backend può essere aggiunto più volte ai pool L7 specificando ogni volta un numero di porta diverso.

## Configura i controlli di integrità
La definizione di controllo di integrità è obbligatoria per ciascun pool L7. Il sistema pre-popola una configurazione del controllo di integrità predefinita per i pool L7.

Puoi personalizzare queste impostazioni per soddisfare le esigenze della tua applicazione:

 * **Interval**: l'intervallo, in secondi, tra due tentativi di controllo di integrità consecutivi.
 * **Timeout**: il tempo massimo di attesa di una risposta ad una richiesta di controllo di integrità da parte del sistema.
 * **MaxRetries**: il numero massimo di tentativi di controllo di integrità che verranno eseguiti dal sistema prima di dichiarare il servizio non integro.
 * **UrlPath**: il percorso URL HTTP per il controllo di integrità L7.
