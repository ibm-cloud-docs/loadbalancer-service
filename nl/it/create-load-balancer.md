---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: create, new, load balancer

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

# Creazione di un {{site.data.keyword.loadbalancer_full}}
{: #creating-an-ibm-cloud-load-balancer}

Per creare un servizio {{site.data.keyword.loadbalancer_full}}, esegui la seguente procedura:

1. Dal tuo browser, apri il [Customer Portal ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://control.softlayer.com/){: new_window} e accedi al tuo account.

2. Fai clic su **Catalog** e quindi, dalla sezione Infrastructure, vai a **Network > Load Balancers**.

	<img src="images/catalog-load-balancer.png" alt="disegno" style="width: 600px;"/>

3. Seleziona **{{site.data.keyword.loadbalancer_full}}** (selezione predefinita) e fai clic su **Create**.

	Se vedi **Upgrade** invece di **Create**, devi collegare il tuo account dell'infrastruttura IBM Cloud (SoftLayer) seguendo [questi passi](/docs/account?topic=account-unifyingaccounts)

	<img src="images/create-load-balancer.png" alt="disegno" style="width: 600px;"/>

4. Seleziona il tuo data center dall'elenco a discesa **Data Center**, esamina le informazioni, quindi fai clic su **Next**.

	<img src="images/select-datacenter.png" alt="disegno" style="width: 600px;"/>

5. Specifica il tipo di programma di bilanciamento del carico.

	Per le applicazioni verso Internet che devono accedere a Internet pubblico, seleziona **Public (Internet-facing)**.

	<img src="images/select-lb-type.png" alt="disegno" style="width: 600px;"/>

	Per impostazione predefinita, il programma di bilanciamento del carico pubblico riceve un indirizzo IP pubblico globalmente univoco dal pool di indirizzi globali IBM. Se, tuttavia, desideri assegnargli indirizzi pubblici provenienti dal tuo pool di indirizzi oppure se desideri distribuirlo dietro un servizio di firewall all'interno del tuo account, controlla se la tua sottorete pubblica dispone di [indirizzi IP sufficienti](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting) e seleziona **Allocate from a public subnet in your account**.

	Per le applicazioni soltanto interne che non necessitano di accesso a internet pubblico, scegli il tipo **Internal (Private)**.

	<img src="images/lb-type-private.png" alt="disegno" style="width: 500px;"/>

	Sia per i tipi di programma di bilanciamento del carico interni che per quelli verso internet, seleziona una delle sottoreti private all'interno dell'account a cui desideri distribuire il tuo programma di bilanciamento del carico. I tuoi server delle applicazioni devono essere raggiungibili da questa sottorete. Se necessario, abilita lo spanning delle VLAN per garantire la connettività di rete appropriata.

	Se non vedi sottoreti private, fai clic su **Previous**, quindi seleziona un data center diverso con sottoreti private.

6. Fai clic su **Next** per terminare la configurazione.

## Operazioni successive
{: #whats-next-2}
Configura il tuo programma di bilanciamento del carico con i [parametri di base](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters).
