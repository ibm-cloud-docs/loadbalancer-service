---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Immetti le informazioni sul tuo dominio
Immetti le informazioni sul dominio che vuoi proteggere e per cui vuoi fornire il bilanciamento del carico globale.

1. Fai clic su **Overview** al lato sinistro della schermata Getting Started. Immetti il tuo nome dominio (o il nome del dominio secondario) e fai clic su **Add domain**. 
    
    <img src="images/Reliability3.png" alt="disegno" style="width: 300px;"/>
    
    **NOTA:** IBM Cloud Internet Service non è una funzione di registrazione DNS, per cui questo dominio (o dominio secondario) deve essere stato precedentemente creato.

    Nella sezione Service Details, riceverai una notifica che il dominio appena aggiunto sarà visualizzato inizialmente nello stato Pending. 

    <img src="images/Reliability4.png" alt="disegno" style="width: 300px;"/>    

2. Passa alla pagina di gestione del tuo dominio con la tua rispettiva funzione di registrazione DNS e delega il tuo dominio/dominio secondario ai server dei nomi IBM definendo i record NS.

Potresti dover attendere fino a 24 ore perché le tue informazioni vengano replicate nel database DNS. Come terminato, lo stato del tuo dominio sarà modificato con Active. 

<img src="images/Reliability5.png" alt="disegno" style="width: 300px;"/>    
