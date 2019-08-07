---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, provisioning, question, problem

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

# Risoluzione dei problemi di provisioning del programma di bilanciamento del carico
{: #load-balancer-provisioning-troubleshooting}

Questo argomento fornisce le informazioni sui problemi comuni che puoi riscontrare mentre crei una nuova istanza di {{site.data.keyword.loadbalancer_full}}.

## Indirizzi IP insufficienti nella tua sottorete
{: #insufficient-ip-addresses-in-your-subnet}

{{site.data.keyword.loadbalancer_full}} richiede almeno due indirizzi IP liberi nella sua sottorete privata. Inoltre, se il programma di bilanciamento del carico è un programma di bilanciamento del carico pubblico e non viene utilizzata l'opzione **IBM system pool**, saranno necessari almeno anche due indirizzi IP liberi nella tua sottorete pubblica.

Segui i passi riportati di seguito per controllare gli IP liberi in una sottorete.

1. Vai a [Customer Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://control.softlayer.com){:new_window} e spostati nella sezione delle sottoreti selezionando **Network > IP Management > Subnets**.

2. Fai clic sulla sottorete nella quale desideri controllare la presenza di IP liberi.

	<img src="images/subnet_list.png" alt="disegno" style="width: 600px;"/>

3. La pagina dei dettagli della sottorete selezionata mostra lo stato di tutti gli IP presenti in tale sottorete.

## Problemi con i firewall nelle VLAN pubbliche e private
{: #issues-with-firewalls-on-public-and-private-vlans}

Fai riferimento all'argomento [Intervalli IP di IBM Cloud](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges) per informazioni su come consentire intervalli IP attraverso il firewall.

## Visualizzazione dei messaggi di errore del programma di bilanciamento del carico
{: #viewing-load-balancer-error-messages}

Per visualizzare i messaggi di errore relativi al tuo programma di bilanciamento del carico, esegui la seguente procedura:

1. Fai clic sul programma di bilanciamento del carico dalla pagina di elenco per visualizzarne i dettagli.
2. Sposta il mouse sul simbolo di errore accanto allo stato del programma di bilanciamento del carico.

<img src="images/lbaas_error_message.png" alt="disegno" style="width: 500px;"/>

Se il programma di bilanciamento del carico si trova in uno stato di `ERROR`, non potrà essere ripristinato e dovrà essere eliminato.
