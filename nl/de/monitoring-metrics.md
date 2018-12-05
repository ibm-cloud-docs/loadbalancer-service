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

# Überwachungsmetriken

Von der Lastausgleichsfunktion werden folgende Metriken überwacht: 

* Durchsatz
* Aktive Verbindungen
* Verbindungsrate

Diese Metriken werden in Form von Diagrammen dargestellt, die durch Auswählen der Registerkarte **Überwachung** angezeigt werden können;
sie sind über das Programm als Zeitreihendatenpunkte bei Verwendung der API `getListenerTimeSeriesData` verfügbar.

Jeder Datenpunkt enthält eine Zeitmarke in der UNIX-Epochenzeit und den Metrikwert für dieses Zeitintervall, das an dieser Zeitmarke endet. Der Benutzer kann die Protokolle und das Zeitintervall angeben, für die die Metriken dokumentiert werden sollen. 

Folgende Protokolle werden unterstützt:

* HTTP
* HTTPS
* TCP

Wenn ein Protokoll angegeben wird, wird die Metrik nach diesem Protokoll gefiltert.

Beispiel: Wenn kein Protokoll angegeben wird und als Metrik *Durchsatz* ausgewählt ist, wird der gesamte Durchsatz für alle Protokolle dokumentiert.

Falls das Protokoll *HTTP* verwendet wird, wird nur der Durchsatz für den HTTP-Datenverkehr dokumentiert.

Der Benutzer kann auch das Zeitintervall angeben, für das die Metrik dokumentiert werden soll. Unterstützt werden folgende Zeitintervalle: 

* 1 Stunde
* 6 Stunden
* 12 Stunden
* 24 Stunden
* 1 Woche
* 2 Wochen

Die Anzahl der dokumentierten Datenpunkte ist für jedes Zeitintervall annähernd identisch.  
Beispiel: Falls das Intervall eine Stunde beträgt, stellt jeder Datenpunkt fünf Minuten der Daten dar.

Falls das Intervall zwei Wochen beträgt, stellt jeder Datenpunkt 24 Stunden der Daten dar.

In der folgenden Tabelle wird veranschaulicht, wie die Datenpunkte aus dem Zeitintervall abgeleitet werden:

| Zeitintervall | Datenpunktgenauigkeit | Anzahl der Datenpunkte |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
| 1 Stunde    | 5 Minuten | 12   |
| 6 Stunden   | 30 Minuten | 12  |
| 12 Stunden  | 1 Stunde | 12 |
| 24 Stunden  | 2 Stunden | 12 |
| 1 Woche    | 12 Stunden | 12 |
| 2 Wochen  | 24 Stunden | 12 |

# Verwendungshinweise zum Aktivieren der Überwachung der Metriken

Zum Abrufen von Überwachungsmetriken müssen Sie mit Ihrem IBM Cloud-Konto eine Verbindung zu Ihrem SoftLayer-Konto herstellen. Weitere Informationen finden Sie [hier ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/account/softlayerlink.html#link_user_account). 
