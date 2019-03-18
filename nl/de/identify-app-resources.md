---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Anwendungsserverressourcen angeben
{: #identifying-your-application-server-resources}

Suchen Sie nach Ihren **Serverinstanzen** in der unten angezeigten Tabelle und klicken Sie auf **+**, um sie hinter der Lastausgleichsfunktion hinzuzufügen. Sie können aus den IBM© Cloud Virtual Server Instances (VSIs) und den Bare-Metal-Servern in Ihrem Konto auswählen. 

Diese Serverinstanzen müssen lokal in dem Rechenzentrum vorhanden sein, in dem Sie den Lastausgleichsservice bereitstellen. Darüber hinaus können auch Serverinstanzen aus den benachbarten Rechenzentren innerhalb derselben Stadt hinzugefügt werden (z. B. wenn die ersten drei Buchstaben des Namens des Rechenzentrums identisch sind).

<img src="images/locate-server-instance.png" alt="Zeichnung" style="width: 300px;"/>

Klicken Sie auf **Weiter**.

**HINWEISE:** 

1. Server**gewichtungen** sind nur relevant, wenn Sie die Lastausgleichsmethode **Weighted Round Robin** verwenden. Die Standardgewichtung ist 50 und der Bereich liegt zwischen 0 und 100. Die Gewichtungen sind für andere Lastausgleichsmethoden abgeblendet.
2. Weitere Informationen zur maximal zulässigen Anzahl von Anwendungsservern finden Sie unter [Limits für die Anzahl von Anwendungsservern](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-).

## Weitere Schritte
[Überprüfen Sie den Inhalt](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order) Ihrer Bestellung, bevor Sie sie aufgeben.
