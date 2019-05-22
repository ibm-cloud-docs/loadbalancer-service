---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Introduzione a IBM Cloud Load Balancer
{: #getting-started}

Per iniziare ad utilizzare IBM© Cloud Load Balancer, avrai bisogno di due elementi principali:

* Un account con IBM: [IBMid ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* Un server IBM, [Bare Metal](/docs/bare-metal?topic=bare-metal-about) o [VSI (Virtual Server Instance)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

Se hai bisogno di assistenza per ottenere un account **IBMid**, contatta il tuo [rappresentante delle vendite IBM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} per ulteriori indicazioni.

Se hai un account dell'infrastruttura IBM Cloud (SoftLayer) esistente, puoi [collegare il tuo account](/docs/account?topic=account-unifyingaccounts) al tuo ID IBM.

## Ordine di un programma di bilanciamento del carico

Per ordinare un servizio IBM Cloud Load Balancer, seleziona **Network > Load Balancers > IBM Cloud Load Balancer** dal [Catalogo IBM Cloud  ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/infrastructure/load-balancer-group){:new_window}. Accedi o crea un nuovo account ed esegui la seguente procedura:

1. Seleziona il tuo data center e controlla il piano di servizio. Fai clic su **Avanti**.
2. Seleziona la sottorete a cui vuoi distribuire il tuo programma di bilanciamento del carico. Il tuo programma di bilanciamento del carico avrà una delle proprie interfacce di rete in questa sottorete. Assicurati i tuoi server dell'applicazione siano su questa sottorete o raggiungibili da essa. Se necessario, abilita lo spanning delle VLAN. Fai clic su **Next**.
3. Definisci i tuoi parametri del servizio di base, come il nome, la descrizione, le porte e i protocolli dell'applicazione di backend e frontend e il metodo di bilanciamento del carico.

	Puoi definire un massimo di due protocolli durante la creazione del servizio iniziale. Puoi definire fino a dieci protocolli dopo aver creato il servizio. Devi inoltre utilizzare una porta di frontend univoca.

	Una volta terminato, fai clic su **Avanti**.

4. Modifica i tuoi parametri del controllo di integrità se lo desideri, altrimenti utilizza le impostazioni predefinite. Fai clic su **Next**.
5. Associa una o più istanze del server dietro il tuo programma di bilanciamento del carico. Devi visualizzare soltanto le istanze del server locali nel tuo data center. Fai clic su **Next**.
6. Controlla la pagina di riepilogo, quindi fai clic su **Create**.

	La pagina di riepilogo visualizza l'istanza del servizio del programma di bilanciamento del carico che hai appena creato. Prendi nota del campo **Stato**. Uno stato di `Offline` implica che il programma di bilanciamento del carico non è nel servizio. Non può essere effettuata alcuna nuova configurazione e non può essere eseguito il provisioning di alcun servizio di bilanciamento del carico finché lo stato non viene modificato in `Online`. Potresti dover aggiornare la tua schermata per visualizzare lo stato corrente.

	Facendo clic sul nome del servizio su questa pagina ti sposti alla pagina della panoramica del servizio. Puoi passare alle schede **Protocolli**, **Controlli di integrità** e **Istanze del server** per modificare ulteriormente la tua configurazione.

Consulta [Come creare e utilizzare un IBM Cloud Load Balancer per il bilanciamento del carico elastico](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing) per istruzioni di configurazione dettagliate.
