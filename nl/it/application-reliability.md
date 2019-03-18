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

# Miglioramento dell'affidabilità e della scalabilità dell'applicazione con il bilanciamento del carico globale da IBM Cloud Internet Services
Se hai un sito web di e-commerce o stai ospitando un'applicazione che deve essere accessibile ai tuoi utenti finali in qualsiasi momento, è probabile che tu sia interessato alla disponibilità e alle prestazioni 24*7 della tua applicazione. 

Le funzionalità di bilanciamento del carico globale disponibili con IBM Cloud Internet Services (CIS) possono migliorare l'affidabilità e la scalabilità delle tue applicazioni mentre viene offerta l'esperienza migliore possibile all'utente finale. Questa guida fornisce una procedura per la configurazione del bilanciamento del carico globale.  

## Cosa otterrai

In questa guida dettagliata imparerai come eseguire una configurazione simile a quella illustrata di seguito.

<img src="images/Reliability1.png" alt="disegno" style="width: 300px;"/>

In questo esempio, le risorse dell'applicazione vengono distribuite in due ubicazioni di data center, una in Stati Uniti Ovest e una in Stati Uniti Costa Est. Gli utenti finali possono accedere a questa applicazione da tutto il mondo. 

Attività  | Descrizione
------------- | -------------
[Crea un'istanza CIS](create-cis.html) | Inizia creando la tua istanza di IBM Cloud Internet Services (CIS) utilizzando il IBM
Customer Portal.
[Immetti le informazioni sul tuo dominio](input-domain.html) | Immetti le informazioni sul dominio che vuoi proteggere e per cui vuoi fornire il bilanciamento del carico globale.
[Avvia la configurazione del programma di bilanciamento del carico globale](begin-config.html) | Avvia la configurazione del tuo programma di bilanciamento del carico globale.
[Identifica le tue risorse dell'applicazione](identify-app-resources.html) | Identifica le risorse della tua applicazione, come i pool di origine e i meccanismi di controllo dell'integrità.
[Definisci il programma di bilanciamento del carico globale](define-global-lb.html) | Definisci la configurazione del tuo programma di bilanciamento del carico globale specificando un nome host, aggiungendo e modificando i tuoi pool di origine e definendo ulteriori regole per controllare come viene servito il traffico ai client.
