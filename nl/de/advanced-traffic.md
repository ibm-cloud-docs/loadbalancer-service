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

# Erweiterte Verwaltung des Datenverkehrs mit {{site.data.keyword.loadbalancer_full}}
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

In diesem Abschnitt werden erweiterte Funktionen der Datenverkehrsverwaltung besprochen, die mit dem Service für die Lastausgleichsfunktion verfügbar sind.

## Maximale Verbindungen

Verwenden Sie die Konfiguration 'Maximale Verbindungen', um die maximale Anzahl der gleichzeitig bestehenden Verbindungen für einen bestimmten Front-End-Port zu begrenzen. Standardmäßig ist kein Grenzwert festgelegt. Der maximale Wert für gleichzeitig bestehende Verbindungen für einen bestimmten Front-End-Port oder systemweit für alle Front-End-Ports beträgt 15.000.  

## Sitzungspersistenz

Von der Lastausgleichsfunktion wird die Sitzungspersistenz für einen bestimmten VIP-Port abhängig von der `Quellen-IP` der Verbindung unterstützt. Beispiel: Wenn die Sitzungspersistenz für Port 80 (HTTP) aktiviert ist, sind die nachfolgenden HTTP-Verbindungsversuche von demselben Client (derselben Quellen-IP) auf demselben Back-End-Server persistent. Diese Funktion steht für alle drei unterstützten Protokolle (HTTP, HTTPS und TCP) zur Verfügung.

Von der Lastausgleichsfunktion werden maximal 10.000 Clientpersistenzeinträge unterstützt. Die Ablaufzeit für diese Einträge beträgt 10 Minuten. Weitere Anforderungen, die von demselben Client nach 10 Minuten empfangen werden, können an einen anderen Back-End-Server weitergeleitet werden. Falls der Eintrag für die Sitzungspersistenz nicht abgelaufen ist, der Back-End-Port jedoch nicht mehr ordnungsgemäß funktioniert, wird ein neuer Server zum Weiterleiten aller nachfolgenden Clientverbindungen ausgewählt.  

## HTTP-Keep-Alive
Von der Lastausgleichsfunktion wird `HTTP-Keep-Alive` unterstützt, falls diese Funktion sowohl auf dem Client als auch auf dem Back-End-Server aktiviert ist. Von der Lastausgleichsfunktion wird versucht, die serverseitigen HTTP-Verbindungen erneut zu verwenden, um die Verbindungseffizienz zu erhöhen und die Latenz zu reduzieren.

## Verbindungszeitlimits
Von der Lastausgleichsfunktion werden die folgenden Zeitlimitwerte verwendet. Diese Werte können zurzeit nicht angepasst werden.

| Name | Beschreibung | Zeitlimit |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | ------------------- |
| Serverseitiger Verbindungsversuch    | Das maximale Zeitfenster, das der Lastausgleichsfunktion zur Verfügung steht, um eine TCP-Verbindung zum Back-End-Server aufzubauen. Falls der Verbindungsversuch nicht erfolgreich ist, wird von der Lastausgleichsfunktion gemäß der konfigurierten Lastausgleichsfunktion der nächste verfügbare Server versucht. | 5 Sekunden   |
| Inaktive clientseitige Verbindung  | Die maximale Leerlaufzeit, nach der die clientseitige Verbindung von der Lastausgleichsfunktion geschlossen wird, falls das ordnungsgemäße Schließen der Verbindung durch den Client fehlgeschlagen ist.| 50 Sekunden  |
| Inaktive serverseitige Verbindung | Die maximale Leerlaufzeit (mit TCP-Back-End-Protokollkonfiguration), nach der die serverseitige Verbindung von der Lastausgleichsfunktion geschlossen wird. Wenn bei einer HTTP-Back-End-Protokollkonfiguration das Empfangen einer Antwort auf eine HTTP-Anforderung innerhalb des Fensters für die Leerlaufzeit fehlschlägt, wird eine Fehlernachricht an den Endclient zurückgegeben.                                | 50 Sekunden |
{: caption="Tabelle 1. Zeitlimitwerte der Lastausgleichsfunktion" caption-side="top"} 

## Beibehalten der IP-Adresse des Endclients 

Die Lastausgleichsfunktion fungiert als Reverse Proxy, von dem der eingehende Datenverkehr vom Client terminiert wird. Dabei wird unter Verwendung der eigenen IP-Adresse eine separate Verbindung zur Back-End-Server-Instanz hergestellt. Bei HTTP-Verbindungen zu Back-End-Servern (bei Front-End-HTTP- oder HTTPS-Verbindungen) behält die Lastausgleichsfunktion die ursprüngliche IP-Adresse des Clients durch Einschließen dieser Adresse in den Header `X-Forwarded-For HTTP` bei. Bei TCP-Verbindungen werden die ursprünglichen IP-Informationen des Clients nicht beibehalten.
