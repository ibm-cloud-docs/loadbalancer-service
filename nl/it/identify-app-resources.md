---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: resources, server, application, instance, configure

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}

# Identificazione delle tue risorse del server delle applicazioni
{: #identifying-your-application-server-resources}

Individua le tue **istanze del server** dalla tabella in basso e fai clic sul segno **+** per aggiungerle dietro il programma di bilanciamento del carico. Puoi scegliere da IBM© Cloud Virtual Server Instances (VSI) e Bare Metal Server nel tuo account.

Queste istanze del server devono essere locali nel data center in cui distribuisci il servizio del programma di bilanciamento del carico. Inoltre, possono essere aggiunte anche le istanze del server provenienti da data center vicini all'interno della stessa città (ad esempio se le prime tre lettere del nome del data center sono uguali).

<img src="images/locate-server-instance.png" alt="disegno" style="width: 300px;"/>

Fai clic su **Avanti**.

I **pesi** del server sono rilevanti solo quando si utilizza il metodo di bilanciamento del carico **Round Robin ponderato**. Il peso predefinito è 50 e l'intervallo è compreso tra 0 e 100. I pesi sono disabilitati con gli altri metodi di bilanciamento del carico.
{: note}

Consulta [Limitazioni per il numero di server delle applicazioni](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-) per ulteriori informazioni sul limite massimo per il numero di server delle applicazioni.
{: tip}

## Operazioni successive
{: #what-s-next-3}
[Esamina il contenuto](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order) del tuo ordine prima di inserirlo.
