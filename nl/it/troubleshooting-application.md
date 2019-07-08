---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, problem, server, application

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

# Risoluzione dei problemi del server delle applicazioni
{: #application-server-troubleshooting}

Questo argomento fornisce le informazioni sui problemi comuni che puoi riscontrare mentre utilizzi il programma di bilanciamento del carico.

## Il server di backend non è integro
{: #the-back-end-server-is-unhealthy}
Se l'integrità del tuo server di backend è compromessa, utilizza il seguente elenco per provare a individuare il problema e risolverlo:

* La porta del protocollo di backend configurato corrisponde alla porta su cui è in ascolto la tua applicazione?
* Il controllo di integrità configurato contiene le informazioni corrette sul protocollo (TCP o HTTP), la porta e l'URL (per HTTP)? Per HTTP, assicurati che la tua applicazione risponda con `200 OK` per l'URL del controllo di integrità configurato.
* Il server di backend si trova in una sottorete diversa da quella del programma di bilanciamento del carico? Nel caso in cui non lo sia, assicurati che lo spanning delle VLAN sia abilitato.
* Il server di backend è un server virtuale con un gruppo di sicurezza abilitato? Se sì, assicurati che le regole del gruppo di sicurezza consentano il traffico tra il programma di bilanciamento del carico e il server virtuale.
