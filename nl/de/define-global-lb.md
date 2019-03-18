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

# Globale Lastausgleichsfunktion definieren

Definieren Sie die Konfiguration der globalen Lastausgleichsfunktion durch Angeben eines Hostnamens, Hinzufügen und Anpassen der Ursprungspools und Definieren zusätzlicher Regeln zum Steuern des Datenverkehrs zu den Clients.

1. Erstellen Sie die globale Lastausgleichsfunktion durch Klicken auf die Schaltfläche zum Erstellen einer Lastausgleichsfunktion auf der rechten Seite.  

2. Geben Sie den Hostnamen für die Domäne an und passen Sie den TTL-Wert bei Bedarf an (Standardwert ist 60 Sekunden) und fügen Ihre Ursprungspools mithilfe von **Pool hinzufügen** hinzu. 

   <img src="images/Reliability11.png" alt="Zeichnung" style="width: 300px;"/>
   
   **HINWEIS:** Normalerweise bestehen die vollständig qualifizierten Domänenname für Ihre Anwendung aus einer Kombination von Hostnamen und Domänennamen. Die Endbenutzer stellen die Verbindung zu Ihrer Anwendung über diesen vollständig qualifizierten Domänennamen her. 
   
3. Passen Sie die relativen Prioritäten der Ursprungspools durch Klicken auf die Aufwärts- und Abwärtspfeile auf der linken Seite des Pools an. Die Anwendungsanforderungen der Endbenutzer werden von diesen Ursprungspools im Umlaufverfahren verarbeitet. 
   
   <img src="images/Reliability12.png" alt="Zeichnung" style="width: 300px;"/>   
   
4. Optional können Sie weitere Regeln definieren, um zu steuern, wie der Datenverkehr von den unterschiedlichen geografischen Regionen zu den Clients bedient wird. Im folgenden Beispiel werden Clients aus der südlichen Region Südamerikas an den Ursprungspool an der Westküste der USA weitergeleitet. Sie können diese Regeln dazu verwenden, um Clients zu ihrer nächstmöglichen Region weiterzuleiten. Wenn die Verbindung zu einer dieser Regionen fehlschlägt, werden die Anforderungen zu anderen verfügbaren Standorten in einwandfreiem Zustand weitergeleitet, damit die Endbenutzer nicht durch Ausfallzeiten beeinträchtigt werden. 

   <img src="images/Reliability13.png" alt="Zeichnung" style="width: 300px;"/>   
   
5. Klicken Sie auf **Ressourcen bereitstellen**, um die Konfiguration der globalen Lastausgleichsfunktion abzuschließen. 
6. Überprüfen Sie zum Schluss die Verbindung zur Anwendung durch Eingeben von `FQDN URL` im Fenster eines mobilen Browsers. Falls die Verbindung hergestellt werden kann, wird eine Willkommensnachricht angezeigt.
