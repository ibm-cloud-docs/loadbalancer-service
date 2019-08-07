---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Allgemeine Schritte für {{site.data.keyword.loadbalancer_full}} ausführen
{: #performing-ibm-cloud-load-balancer-basics}

Vom {{site.data.keyword.loadbalancer_full}}-Service wird der Datenverkehr auf mehrere Serverinstanzen (Bare-Metal-Server und virtuelle Server) verteilt, die sich lokal in demselben Rechenzentrum befinden. 

## Öffentliche Lastausgleichsfunktion 
Der Instanz des Service für die Lastausgleichsfunktion wird ein öffentlicher und vollständig qualifizierter Domänenname zugewiesen. Sie müssen diesen Domänennamen für den Zugriff auf die Anwendungen verwenden, die hinter dem Service für die Lastausgleichsfunktion gehostet werden. Dieser Domänenname kann für mindestens eine öffentliche IP-Adresse registriert werden. Die öffentlichen IP-Adressen und die Anzahl der öffentlichen IP-Adressen können sich im Lauf der Zeit aufgrund von Wartungs- und Skalierungsaktivitäten ändern, die für die Endbenutzer transparent sind. Die Back-End-Recheninstanzen, auf denen die Anwendung gehostet wird, müssen sich in einem privaten Netz in einer IBM Cloud befinden. 

Es wird empfohlen, Back-End-Server ausschließlich privat bereitzustellen, sofern nicht eine direkte öffentliche Verbindung erforderlich ist. Dies sorgt für eine bessere Sicherheit und Ihre öffentliche IP-Adresse wird beibehalten. Die Anwendungen, die auf diesen Back-End-Servern gehostet werden, sind mithilfe der Lastausgleichsfunktion weiterhin über das öffentliche Netz verfügbar.
{:note}  

Bei der Erstellung der Load Balancer-Serviceinstanz können Sie öffentliche IP-Adressen für die Lastausgleichsfunktion entweder aus einem IBM Systempool (Standardeinstellung) oder aus einem öffentlichen VLAN unter Ihrem Konto zuordnen.

## Interne Lastausgleichsfunktion
Auf die interne Lastausgleichsfunktion kann nur im privaten IBM Cloud-Netz zugegriffen werden. 

Analog zur öffentlichen Lastausgleichsfunktion wird auch der Instanz eines internen Lastenausgleichsservice ein vollständig qualifizierter Domänenname zugeordnet. Dieser Domänenname ist jedoch für mindestens eine private IP-Adresse registriert. 

Ähnlich wie bei einer öffentlichen Lastausgleichsfunktion können sich die privaten IP-Adressen und die Anzahl der privaten IP-Adressen im Lauf der Zeit aufgrund von Wartungs- und Skalierungsaktivitäten ändern, die für die Endbenutzer transparent sind. 

Die Back-End-Recheninstanzen, auf denen die Anwendung gehostet wird, müssen sich ebenfalls in dem privaten Netz in einer IBM Cloud befinden.
{:note}

## Ports bzw. Protokolle von Front-End- und Back-End-Anwendungen
Sie können bis zu zehn Ports (bzw. Protokolle) für Front-End-Anwendungen definieren und diese den entsprechenden Ports (bzw. Protokollen) auf den Back-End-Anwendungsservern zuordnen. Der vollständig qualifizierte Domänenname, der der Serviceinstanz für den Lastausgleich zugewiesen ist, und die Ports der Front-End-Anwendung sind öffentlich zugänglich. An diesen Ports werden die eingehenden Benutzeranforderungen empfangen. 

Die Back-End-Ports sind dagegen nur intern bekannt. Diese Back-End-Ports können mit den Front-End-Ports identisch sein, können aber auch abweichen. Beispiel: Die Lastausgleichsfunktion kann so konfiguriert sein, dass von ihr eingehender Web- bzw. HTTP-Datenverkehr an Front-End-Port 80 empfangen wird, die Back-End-Server sind jedoch am angepassten Port 81 empfangsbereit. 

Unterstützte Front-End-Ports bzw. -Protokolle sind HTTP, HTTPS und TCP. Unterstützte Back-End-Ports bzw. -Protokolle sind HTTP, HTTPS und TCP. Eingehender HTTPS-Datenverkehr muss an der Lastausgleichsfunktion terminiert werden, damit eine ungeschützte HTTP-Kommunikation mit dem Back-End-Server möglich ist. Wenn es sich bei dem Back-End-Protokoll um HTTPS handelt, wird der Datenverkehr zwischen Load Balancer und Back-End-Servern verschlüsselt.

### Hinweise

* Während der Erstkonfiguration können Sie nur maximal zwei Front-End-Ports definieren. Sobald eine Lastausgleichsfunktion erstellt ist, können Sie die Portkonfiguration bearbeiten, um zusätzliche Ports hinzuzufügen; das Maximum liegt bei 10 Ports.
* Alle zehn Front-End-Ports müssen denselben Back-End-Serverinstanzen zugeordnet sein.
* Die maximale Anzahl an Serverinstanzen, die sich hinter einer Lastausgleichsfunktion befinden können, beträgt 50.
* Der Portbereich von 56.500 bis 56.520 für Verwaltungszwecke reserviert und kann nicht für virtuelle Front-End-Ports verwendet werden. 
* TCP-Port 56501 wird zur Verwaltung verwendet. Wenn Sie öffentliche IP-Adressen für die Lastausgleichsfunktion aus dem öffentlichen VLAN zuordnen, müssen Sie sicherstellen, dass der Datenverkehr an diesem Verwaltungsport und an den Ports Ihrer Anwendung nicht durch Firewalls blockiert wird, die möglicherweise für Ihre öffentlichen VLANs eingerichtet sind. Wenn Sie öffentliche IP-Adressen für die Lastausgleichsfunktion aus dem IBM Systempool zuordnen, ist dies nicht erforderlich.

## Lastausgleichsmethoden
Zum Verteilen des Datenverkehrs auf die Back-End-Anwendungsserver stehen die drei folgenden Lastausgleichsmethoden zur Verfügung:

* **Round Robin:** 'Round Robin' ist die Standardmethode für den Lastausgleich. Bei Verwendung dieser Methode leitet die Lastausgleichsfunktion eingehende Clientverbindungen im Umlaufverfahren an die Back-End-Server weiter. Dies hat zur Folge, dass allen Back-End-Servern ungefähr dieselbe Anzahl an Clientverbindungen zugewiesen wird.

* **Weighted Round Robin:** Bei Verwendung dieser Methode werden an die Back-End-Server die Anteile der eingehenden Clientverbindungen weitergeleitet, die der Gewichtung dieser Server entsprechen. Jedem Server wird eine Standardgewichtung von 50 zugewiesen, die auf einen Wert zwischen 0 und 100 geändert werden kann. 

	Beispiel: Es gibt die drei Anwendungsserver A, B und C, deren Gewichtung jeweils auf 60, 60 und 30 angepasst wurde; die Server A und B erhalten in diesem Fall dieselbe Anzahl an Verbindungen, während Server C die Hälfte der Verbindungen eines dieser Server erhält. 


	Wenn für die Gewichtung eines Servers der Wert '0' eingestellt wird, hat dies zur Folge, dass keine neuen Verbindungen an diesen Server weitergeleitet werden, der vorhandene Datenverkehr fließt jedoch weiter, so lange er aktiv ist. Durch die Einstellung von '0' kann ein Server sanft heruntergefahren werden und als Ziel für die Services entfernt werden. 
	{:note}
	
	Werte für die Gewichtung der Server können nur bei Verwendung der Methode 'Weighted Round Robin' angewendet werden. Sie werden bei Verwendung der Lastausgleichsmethoden 'Round Robin' und 'Least Connections' ignoriert. 
	{:note}

* **Least Connections:** Bei Verwendung dieser Methode erhält die Serverinstanz, von der zu einem bestimmten Zeitpunkt die wenigsten Verbindungen verarbeitet werden, die nächste Clientverbindung. 


## Horizontale Skalierung
Die Lastausgleichsfunktion passt ihre Kapazität automatisch an die Workload an. Dabei ändert sich möglicherweise die Anzahl der IP-Adressen, die dem DNS-Namen der Lastausgleichsfunktion zugeordnet sind.
