---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, policies, rules, pools

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Bilanciamento del carico L7 (Livello 7)
{: #layer-7-load-balancing}

Il servizio {{site.data.keyword.loadbalancer_full}} distribuisce il traffico tra più istanze server, inclusi bare-metal e VSI, utilizzando i dati L7 (livello applicazione).

 * Il traffico dati da distribuire viene classificato utilizzando politiche e regole.
 * Le politiche definiscono quale azione eseguire quando il traffico dati soddisfa tutte le regole associate a una politica.
 * Il bilanciamento del carico L7 (Livello 7) è supportato solo per il traffico HTTP e HTTPS.

## Politiche e regole L7
{: #layer-7-policies-and-rules}
Una politica L7 è associata a una porta dell'applicazione di frontend. Più politiche possono essere associate a una porta di frontend.

 * Queste politiche vengono valutate in ordine, in base alla priorità assegnata a ciascuna politica.
 * Un'azione associata viene eseguita quando la politica viene soddisfatta.
 * Ciascuna regola L7 è associata a una politica.
 * Se tutte le regole associate alla politica vengono valutate come `true`, la politica viene soddisfatta e quindi viene eseguita l'azione associata.

Fai riferimento a [Politica e regole L7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy) per ulteriori dettagli.

## Pool L7
{: #layer-7-pools}
Ciascun pool del programma di bilanciamento del carico L7 contiene una o più istanze del server logico.

 * Ciascuna istanza del server logico viene identificata da un indirizzo IP e da un numero di porta.
 * Ciascun pool ha un monitoraggio dell'integrità ad esso associato che monitora l'integrità di tutti i server nel pool.
 * Un pool può essere configurato per la persistenza della sessione.
 * Utilizza l'indirizzo IP di origine del client per configurare la persistenza della sessione.

Fai riferimento a [Pool L7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool) per ulteriori dettagli.
