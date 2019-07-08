---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: ssl, offload, cipher, suite

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

# Offload SSL con IBM Cloud Load Balancer
{: #ssl-offload-with-ibm-cloud-load-balancer}

Per tutte le connessioni HTTPS in entrata, il servizio del programma di bilanciamento del carico termina la connessione SSL e stabilisce una comunicazione HTTP di testo semplice con il server di backend. Gli handshake SSL con uso intensivo di CPU e le attività di crittografia/decrittografia sono stati spostati dai server di backend, consentendo loro di utilizzare i propri cicli di CPU per elaborare il traffico dell'applicazione.

Un certificato SSL è obbligatorio al programma di bilanciamento del carico per eseguire le attività offload SSL. Puoi utilizzare un certificato SSL preesistente o acquistarne uno nuovo e gestirlo con [IBM© Cloud Certificate Store ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}.

## Suite di cifratura SSL
{: #ssl-cipher-suites}

Il servizio del programma di bilanciamento del carico supporta TLS versione 1.2 con offload SSL.

Le seguenti cifrature SSL sono supportate dal tuo programma di bilanciamento del carico:

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

Se il tuo programma di bilanciamento del carico ha più di una porta dell'applicazione di frontend HTTPS (protocolli) configurata, per impostazione predefinita tutte le cifrature SSL predefinite saranno abilitate per il tuo programma di bilanciamento del carico.

Puoi scegliere di abilitare diverse cifrature SSL per il tuo programma di bilanciamento del carico se necessario.Per ulteriori informazioni, consulta [Seleziona una suite di cifratura preferita per la tua applicazione HTTPS](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application).
{: note}
