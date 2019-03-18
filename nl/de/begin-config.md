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

# Konfiguration der globalen Lastausgleichsfunktion starten
Starten Sie die Konfiguration der globalen Lastausgleichsfunktion.

1. Wählen Sie im Abschnitt **Zuverlässigkeit** die Auswahlmöglichkeit **Global Load Balancer** aus. 
    
    <img src="images/Reliability6.png" alt="Zeichnung" style="width: 300px;"/>

2. Blättern Sie nach unten zum Abschnitt 'Statusprüfungen'. 

   **HINWEIS:** Diese Konfiguration ist optional. Falls Sie keine angepassten Statusprüfungen definieren, wird vom System "/" als Standardpfad für die Statusprüfung verwendet. 

3. Klicken Sie auf die Schaltfläche **Statusprüfung erstellen**, um eine angepasste Statusprüfung zu definieren.   

   Geben Sie den gewünschten Pfad zu den Statusprüfungen an. Sie müssen entweder HTTP- oder HTTPS-Protokolle für die Statusprüfungen verwenden. 
   
4. Unter **Erweiterte Optionen** können Sie weitere Parameter anpassen, zum Beispiel das Intervall für die Statusprüfungen, die Anzahl der Neuversuche, die Anforderungsmethode und den Antworthauptteil. 
   
   <img src="images/Reliability6.png" alt="Zeichnung" style="width: 300px;"/>
   
5. Klicken Sie auf **Ressourcen bereitstellen**, um die Konfiguration für die Statusprüfungen abzuschließen. 
