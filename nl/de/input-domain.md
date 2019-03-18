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

# Informationen zur Domäne eingeben
Geben Sie Informationen zu der Domäne ein, die Sie schützen und für die Sie einen globale Lastausgleich bereitstellen möchten.

1. Klicken Sie auf der linken Seite der Anzeige 'Einführung' auf **Übersicht**. Geben Sie den Domänennamen (oder Unterdomänennamen) ein und klicken Sie auf **Domäne hinzufügen**. 
    
    <img src="images/Reliability3.png" alt="Zeichnung" style="width: 300px;"/>
    
    **HINWEIS:** Da IBM Cloud Internet Services kein DNS-Registrator ist, muss diese Domäne (bzw. Unterdomäne) bereits vorher erstellt worden sein.

    Im Abschnitt mit den Servicedetails wird angezeigt, dass sich die neu hinzugefügte Domäne zunächst im Wartestatus befindet. 

    <img src="images/Reliability4.png" alt="Zeichnung" style="width: 300px;"/>    

2. Navigieren Sie zur Verwaltungsseite für die Domäne mit der entsprechenden DNS-Registrierungsstelle und delegieren Sie die Domäne bzw. Unterdomäne an die IBM Namensserver durch Definieren von Namensservereinträgen.

Es kann sein, dass Sie bis zu 24 Stunden warten müssen, bis die Informationen in der DNS-Datenbank repliziert werden. Sobald dies geschehen ist, wechselt der Domänenstatus zu 'Aktiv'. 

<img src="images/Reliability5.png" alt="Zeichnung" style="width: 300px;"/>    
