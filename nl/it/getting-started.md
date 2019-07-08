---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
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
{: #ordering-a-load-balancer}

Per ordinare un servizio IBM Cloud Load Balancer, seleziona **IBM Cloud Load Balancer** dal [catalogo IBM Cloud ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window}. Fai quindi clic su **Create** ed esegui la seguente procedura:

1. Definisci i tuoi parametri del servizio di base, come il nome r la descrizione.
2. Seleziona il tuo data center.
3. Seleziona un tipo di programma di bilanciamento del carico **Public**.
4. Seleziona la sottorete a cui vuoi distribuire il tuo programma di bilanciamento del carico.

  Il tuo programma di bilanciamento del carico avrà una delle proprie interfacce di rete in questa sottorete. Assicurati i tuoi server dell'applicazione siano su questa sottorete o raggiungibili da essa. Se necessario, abilita lo spanning delle VLAN.
  {: note}

5. Crea le porte e i protocolli dell'applicazione front-end e back-end.

  Per ulteriori informazioni su questa configurazione, consulta [Configurazione dei parametri di IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters).
  {: note}

6. Per abilitare l'offload SSL, imposta i protocolli front-end su HTTPS e i protocolli di back-end su HTTP. Seleziona quindi il tuo certificato SSL dalla casella a discesa Certificato.

  Tutti i certificati SSL esistenti sono gestiti tramite l'[IBM Cloud Certificate Store  ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}. Se non hai un certificato SSL, puoi crearne uno qui.

7. Modifica i tuoi parametri del controllo di integrità se lo desideri, altrimenti utilizza le impostazioni predefinite.

  Per ulteriori informazioni sui parametri di controllo dell'integrità, consulta [Parametri di IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks).
  {: note}

8. Fai clic su **Attach Server** per associare una o più istanze del server dietro il tuo programma di bilanciamento del carico. Devi visualizzare soltanto le istanze del server locali nel tuo data center.
9. Esamina la pagina, conferma l'accordo di servizio e fai quindi clic su **Create**.

Viene visualizzato l'elenco dei programmi di bilanciamento del carico, che mostra tutte le tue istanze del servizio.

Facendo clic sul nome del servizio su questa pagina ti sposti alla pagina della panoramica del servizio. Puoi passare alle schede **Protocolli**, **Controlli di integrità** e **Istanze del server** per modificare ulteriormente la tua configurazione.

Il tuo programma di bilanciamento del carico appena creato potrebbe non essere visualizzato immediatamente in questo elenco. Dopo qualche minuto, il nuovo programma di bilanciamento del carico verrà visualizzato in grigio, a indicare che il suo stato è `Offline`. Dopo qualche altro minuto, il nuovo programma di bilanciamento del carico verrà visualizzato in verde, a indicare che è `Online`. Potresti dover aggiornare la tua schermata per vedere queste modifiche.
{: note}

Consulta [Come utilizzare un IBM Cloud Load Balancer per il bilanciamento elastico del carico del server](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing) per istruzioni dettagliate sulla configurazione del tuo nuovo Cloud Load Balancer.
