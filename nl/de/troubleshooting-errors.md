---

copyright:
  years: 2018
lastupdated: "2018-11-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Fehlerbehebung bei Fehlernachrichten
{: #error-message-troubleshooting}

In diesem Abschnitt finden Sie Informationen zu gängigen Fehlernachrichten, die beim Erstellen/Aktualisieren einer Instanz von {{site.data.keyword.loadbalancer_full}} ausgegeben werden können. 

| Fehler | Erläuterung  | Lösung  |
| ------------- | ------------- | ----- |
| `Die maximale Anzahl von Lastausgleichsfunktionen, `n`, wurde erreicht.`| Pro Konto sind nur 50 Lastausgleichsfunktionsinstanzen zulässig. | Stellen Sie sicher, dass Sie höchstens über 50 Lastausgleichsfunktionsinstanzen pro Konto verfügen. |
| `Die maximale Anzahl von angegebenen Protokollen, `n`, in einer Produktbestellung von Lastausgleichsfunktionen wurde erreicht.` | Während der Bereitstellung einer Lastausgleichsfunktion können nur zwei Protokolle hinzugefügt werden.  | Wenn Sie mehr Protokolle benötigen, können Sie nach der Bereitstellung bis zu zehn davon auf der Registerkarte **Protokolle** im Verwaltungsablauf der Lastausgleichsfunktion hinzufügen. Weitere Informationen finden Sie im Abschnitt zum [Überwachen und Verwalten Ihres Service](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `Die maximale Anzahl von angegebenen Serverinstanzen, `n`, in einer Produktbestellung von Lastausgleichsfunktionen wurde erreicht.` | Während der Bereitstellung einer Lastausgleichsfunktion können nur zehn Server hinzugefügt werden. | Wenn Sie zusätzliche Server benötigen, können Sie nach der Bereitstellung bis zu 50 davon auf der Registerkarte **Serverinstanzen** im Verwaltungsablauf der Lastausgleichsfunktion hinzufügen. Weitere Informationen finden Sie im Abschnitt zum [Überwachen und Verwalten Ihres Service](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `Der Name der Lastausgleichsfunktion muss eine 1 - 40 Zeichen lange Zeichenfolge sein.` | Der Name der Lastausgleichsfunktion muss angegeben werden. Verwenden Sie nur alphanumerische Zeichen (oder die Sonderzeichen '-' und '.') in dem Namen. Der Name darf nicht mit einem Sonderzeichen beginnen oder enden und er darf höchstens 40 Zeichen lang sein. | Geben Sie einen eindeutigen Namen für die Lastausgleichsfunktion ein. Beispiel: 'ui-servers' oder 'backend-servers'.|
| `Formatfehler im angegebenen Namen einer Lastausgleichsfunktion gefunden.` | Der Name der Lastausgleichsfunktion muss angegeben werden. Verwenden Sie nur alphanumerische Zeichen (oder die Sonderzeichen '-' und '.') in dem Namen. Der Name darf nicht mit einem Sonderzeichen beginnen oder enden und er darf höchstens 40 Zeichen lang sein. | Geben Sie einen eindeutigen Namen für die Lastausgleichsfunktion ein. Beispiel: 'ui-servers' oder 'backend-servers'.|
| `Es gibt bereits eine Lastausgleichsfunktion mit diesem Namen (Groß-/Kleinschreibung wird nicht berücksichtigt).` | Es gibt bereits eine Lastausgleichsfunktion mit diesem Namen. | Geben Sie einen eindeutigen Namen für die Lastausgleichsfunktion ein, um fortzufahren. Beispiel: "ui-servers" oder "backend-servers". |
| `Die Beschreibung der Lastausgleichsfunktion muss eine höchstens 255 Zeichen lange Zeichenfolge sein.` | Die Beschreibung der Lastausgleichsfunktion muss eine Zeichenfolge mit höchstens 255 Zeichen sein. | Beschränken Sie die Beschreibung auf 255 Zeichen. |
| `Der Frontend-Port 80 wird bereits verwendet.` | Möglicherweise haben Sie einen Front-End-Port eingegeben, der bereits verwendet wird. | Geben Sie einen eindeutigen Front-End-Port ein. |
| `Der Back-End-Port muss eine ganze Zahl sein.` | Möglicherweise haben Sie einen ungültigen Back-End-Portwert eingegeben. | Geben Sie eine Back-End-Portnummer zwischen 1 und 65535 ein. |
| `Da das Protokoll und der Port nicht in der Statusüberwachung bearbeitet werden können, kann dieser Fehler nicht über die Benutzerschnittstelle behoben werden.`| Ihr privates Teilnetz ist kein Standardtyp und kann nicht zum Erstellen der Lastausgleichsfunktion verwendet werden. | Wenden Sie sich an den IBM Support. |
| `Das private Teilnetz `xyz` muss mindestens `n` freie IP-Adressen haben.` | Das ausgewählte private Teilnetz hat keine freien IP-Adressen. |Weitere Informationen finden Sie in diesen [Schritten zur Fehlerbehebung](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting).|
| `Das angegebene private Teilnetz-VLAN liegt am Router `xyz`. Es wurde jedoch kein öffentliches VLAN mit `n` freien IPs auf demselben Router gefunden.` |Dies passiert, wenn Sie während der Bereitstellung die Option **Aus öffentlichem Teilnetz von diesem Konto zuordnen** ausgewählt haben.| Wählen Sie stattdessen **Aus IBM Systempool zuordnen** aus, oder wenden Sie sich an dem IBM Support.|
| `Das angegebene private Teilnetz-VLAN liegt am Router `xyz`. Es wurde jedoch kein öffentliches Teilnetz mit `n` freien IPs mit einem VLAN auf demselben Router gefunden.`| Dies passiert, wenn Sie während der Bereitstellung die Option **Aus öffentlichem Teilnetz von diesem Konto zuordnen** ausgewählt haben.| Wählen Sie stattdessen **Aus IBM Systempool zuordnen** aus, oder wenden Sie sich an dem IBM Support.|
| `Die angegebene neue Beschreibung muss eine Zeichenfolge sein.`| Möglicherweise haben Sie eine ungültige Beschreibung eingegeben. | Geben Sie eine gültige Beschreibung der Lastausgleichsfunktion ein, die nicht länger als 255 Zeichen ist. |
| `Eine Rechnungsposition ist erforderlich, um eine Kündigung für die Lastausgleichsfunktion mit der UUID aaaa-bbbb-cccc-dddd zu verarbeiten.` | Die Abrechnungsdaten fehlen oder sind für Ihr Konto ungültig, und die Lastausgleichsfunktion kann nicht abgebrochen werden. | Wenden Sie sich an den IBM Support. |
| `Interner Fehler. Daten konnten nicht abgerufen werden.` | Metrikdaten können nicht abgerufen werden. | Laden Sie die Seite erneut. Wenn das Problem weiterhin auftritt, wenden Sie sich an den IBM Support. |
| `Der Front-End-Port muss eine ganze Zahl zwischen 1 und 65535 sein, mit Ausnahme des Bereichs 56500-56520.` | Möglicherweise haben Sie einen Front-End-Port zwischen 56500 und 56520 angegeben. | Geben Sie eine eindeutige Portnummer zwischen 1 und 65535 ein, jedoch mit Ausnahme des Bereichs von 56500 bis 56520. |
| `Der Back-End-Port muss eine ganze Zahl sein.` | Möglicherweise haben Sie einen ungültigen Back-End-Portwert eingegeben. | Geben Sie eine Back-End-Portnummer zwischen 1 und 65535 ein. |
| `Der Back-End-Port muss eine ganze Zahl zwischen 1 und 65535 sein, mit Ausnahme des Bereichs 56500-56520.` | Möglicherweise haben Sie einen Back-End-Port zwischen 56500 und 56520 eingegeben.| Geben Sie eine Back-End-Portnummer zwischen 1 und 65535 ein, jedoch mit Ausnahme des Bereichs von 56500 bis 56520. |
| `Das Back-End-Protokoll HTTP ist mit dem Front-End-Protokoll TCP nicht kompatibel.` | Sie haben möglicherweise eine inkompatible Kombination von Back-End-Protokoll und Front-End-Protokoll ausgewählt. | Wählen Sie eine gültige Kombination aus Front-End- und Back-End-Protokoll in der folgenden Form aus: `<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Die Mitgliedsgewichtung <some value> wird für das Mitglied abcd-xxxx-yyyy-2222 angegeben. Der zulässige Gewichtungswert liegt zwischen 0 und 100 `| Möglicherweise haben Sie eine ungültige Gewichtung eingegeben. | Geben Sie einen Gewichtungswert zwischen 0 und 100 ein. |
| `Beim Abrufen der Server ist ein Fehler aufgetreten.` | Ursache können Zeitlimitüberschreitungen im Netz sein. | Laden Sie die Seite erneut. Wenn das Problem weiterhin auftritt, wenden Sie sich an den IBM Support.|
