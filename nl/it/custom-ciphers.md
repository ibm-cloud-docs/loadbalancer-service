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

# Seleziona una suite di cifratura preferita per la tua applicazione HTTPS
Gli algoritmi di cifratura di supporto a IBM Cloud Load Balancer stabiliscono connessioni sicure con i suoi client HTTP.

IBM ti offre una suite di cifrature approvate da cui scegliere in modo che tu possa proteggere la comunicazione tra il tuo programma di bilanciamento del carico e i tuoi client.

Puoi scegliere una suite di cifratura preferita per un programma di bilanciamento del carico esistente oppure designarla quando ne crei uno nuovo.  

## Scelta delle cifrature per un programma di bilanciamento del carico esistente
Per scegliere una configurazione della suite di cifratura per un programma di bilanciamento del carico esistente, vai alla schermata del tuo programma di bilanciamento del carico nel portale clienti e fai clic sulla scheda relativa ai protocolli. Se HTTPS non è selezionato come il tuo protocollo di frontend, non vedrai l'elenco delle suite di cifratura. 

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="disegno" style="width: 700px;"/>
  
Seleziona HTTPS per il tuo protocollo di frontend e le suite di cifratura disponibili verranno visualizzate nei dettagli del programma di bilanciamento del carico.  

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="disegno" style="width: 600px;"/>
  
La tabella Cipher è modificabile e ti consente di selezionare le suite di cifratura desiderate per l'handshake SSL. Fai clic su **Edit**, seleziona le cifrature che desideri implementare e fai clic su **Save**.
  
**NOTA:** per un elenco delle cifrature supportate, vedi [Offload SSL](ssl-offload.html).

## Scelta delle cifrature quando si crea un nuovo programma di bilanciamento del carico

Per scegliere la suite di cifratura quando si crea un nuovo programma di bilanciamento del carico:

1. Segui le istruzioni per [creare un programma di bilanciamento del carico](create-load-balancer.html).
  
2. La configurazione della suite di cifratura è applicabile solo con il protocollo di frontend HTTPS. Quando raggiungi i passi di configurazione per la sezione **Add protocol**, scegli **HTTPS Protocol**.

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="disegno" style="width: 500px;"/>
  
3. Nella configurazione è già selezionata una suite predefinita di cifrature, ma potrai modificarle solo dopo che avrai terminato la configurazione del programma di bilanciamento del carico.  
  
	Completa la configurazione del programma di bilanciamento del carico seguendo le istruzioni presenti nell'argomento. Una volta terminato, puoi vedere l'elenco delle cifrature predefinite nella **scheda Protocols** in **Load Balancer Details**.

	<img src="images/View-CustomCiphers.png" alt="disegno" style="width: 600px;"/>
  
4. La tabella Cipher è modificabile e ti consente di selezionare le suite di cifratura desiderate per l'handshake SSL. Fai clic su **Edit**, seleziona le cifrature che desideri implementare e fai clic su **Save**.
	
	**NOTA:** per un elenco delle cifrature supportate, vedi [Offload SSL](ssl-offload.html).
