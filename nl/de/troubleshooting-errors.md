---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Fehlerbehebung bei Fehlernachrichten
In diesem Abschnitt finden Sie Informationen zu gängigen Fehlernachrichten, die beim Erstellen/Aktualisieren einer Instanz von IBM Cloud Load Balancer ausgegeben werden können. 

| Fehler | Erläuterung | Lösung  |
| ------------- | ------------- | ----- |
| `Die maximale Anzahl von Lastausgleichsfunktionen, `n`, wurde erreicht.`| Pro Konto sind nur 50 Lastausgleichsfunktionsinstanzen zulässig. | Stellen Sie sicher, dass Sie höchstens über 50 Lastausgleichsfunktionsinstanzen pro Konto verfügen. |
| `Die maximale Anzahl von angegebenen Protokollen, `n`, in einer Produktbestellung von Lastausgleichsfunktionen wurde erreicht.` | Während der Bereitstellung einer Lastausgleichsfunktion können nur zwei Protokolle hinzugefügt werden. | Wenn Sie mehr Protokolle benötigen, können Sie nach der Bereitstellung bis zu zehn davon auf der Registerkarte **Protokolle** im Verwaltungsablauf der Lastausgleichsfunktion hinzufügen. Weitere Informationen finden Sie im Abschnitt zum [Überwachen und Verwalten Ihres Service](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service). |
| `Die maximale Anzahl von angegebenen Serverinstanzen, `n`, in einer Produktbestellung von Lastausgleichsfunktionen wurde erreicht.` | Während der Bereitstellung einer Lastausgleichsfunktion können nur zehn Server hinzugefügt werden. | Wenn Sie zusätzliche Server benötigen, können Sie nach der Bereitstellung bis zu 50 davon auf der Registerkarte **Serverinstanzen** im Verwaltungsablauf der Lastausgleichsfunktion hinzufügen. Weitere Informationen finden Sie im Abschnitt zum [Überwachen und Verwalten Ihres Service](/docs/infrastructure/loadbalancer-service/managing-lb.html#monitoring-and-managing-your-service). |
| `Der Name der Lastausgleichsfunktion muss eine 1 - 40 Zeichen lange Zeichenfolge sein.` | Der Name der Lastausgleichsfunktion muss angegeben werden. Verwenden Sie nur alphanumerische Zeichen (oder die Sonderzeichen '-' und '.') in dem Namen. Der Name darf nicht mit einem Sonderzeichen beginnen oder enden und er darf höchstens 40 Zeichen lang sein. | Geben Sie einen eindeutigen Namen für die Lastausgleichsfunktion ein. Beispiel: 'ui-servers' oder 'backend-servers'. |
| `Formatfehler im angegebenen Namen einer Lastausgleichsfunktion gefunden.`  Der Name der Lastausgleichsfunktion muss angegeben werden. Verwenden Sie nur alphanumerische Zeichen (oder die Sonderzeichen '-' und '.') in dem Namen. Der Name darf nicht mit einem Sonderzeichen beginnen oder enden und er darf höchstens 40 Zeichen lang sein. | Geben Sie einen eindeutigen Namen für die Lastausgleichsfunktion ein. Beispiel: 'ui-servers' oder 'backend-servers'. |
| Es gibt bereits eine Lastausgleichsfunktion mit diesem Namen (Groß-/Kleinschreibung wird nicht berücksichtigt). | Es gibt bereits eine Lastausgleichsfunktion mit diesem Namen. | Geben Sie einen eindeutigen Namen für die Lastausgleichsfunktion ein, um fortzufahren. Beispiel: 'ui-servers', 'backend-servers' usw. |
| Die Beschreibung der Lastausgleichsfunktion muss eine höchstens 255 Zeichen lange Zeichenfolge sein. | Die Beschreibung der Lastausgleichsfunktion muss eine höchstens 255 Zeichen lange Zeichenfolge sein. | Geben Sie eine gültige Beschreibung der Lastausgleichsfunktion mit höchstens 255 Zeichen ein. |
| Der Front-End-Port `80` wird bereits verwendet. | Möglicherweise haben Sie einen Front-End-Port eingegeben, der bereits verwendet wird. | Geben Sie einen eindeutigen Front-End-Port ein. |
| Der Back-End-Port muss eine ganze Zahl sein. | Möglicherweise haben Sie einen ungültigen Back-End-Portwert eingegeben. | Geben Sie einen gültigen Back-End-Port zwischen 1 und 65535 ein. |
|Da das Protokoll und der Port nicht in der Statusüberwachung bearbeitet werden können, kann dieser Fehler nicht über die Benutzerschnittstelle behoben werden.|Das private Teilnetz `xyz` hat nicht den Standardtyp und kann deshalb nicht zum Erstellen einer Lastausgleichsfunktion verwendet werden.|Wenden Sie sich an den IBM Support.|
|Das private Teilnetz `xyz` muss mindestens `n` freie IP-Adressen haben.|Das ausgewählte private Teilnetz hat keine freien IP-Adressen.|Weitere Details finden Sie in diesen [Schritten zur Fehlerbehebung](/docs/infrastructure/loadbalancer-service/troubleshooting-provisioning.html#insufficient-ip-addresses-in-your-subnet).|
|Das angegebene private Teilnetz-VLAN liegt am Router `xyz`. Es wurde jedoch kein öffentliches VLAN mit `n` freien IPs auf demselben Router gefunden.|Dies passiert, wenn Sie während der Bereitstellung die Option 'Aus öffentlichem Teilnetz von diesem Konto zuordnen' ausgewählt haben.|Wählen Sie die Option 'Aus IBM Systempool zuordnen' aus oder wenden Sie sich an den IBM Support.|
|Das angegebene private Teilnetz-VLAN liegt am Router `xyz`. Es wurde jedoch kein öffentliches Teilnetz mit `n` freien IPs mit einem VLAN auf demselben Router gefunden.|Dies passiert, wenn Sie während der Bereitstellung die Option 'Aus öffentlichem Teilnetz von diesem Konto zuordnen' ausgewählt haben.|Wählen Sie die Option 'Aus IBM Systempool zuordnen' aus oder wenden Sie sich an den IBM Support.|
|Die angegebene neue Beschreibung muss eine Zeichenfolge sein.|Möglicherweise haben Sie eine ungültige Beschreibung eingegeben.|Geben Sie eine gültige Beschreibung der Lastausgleichsfunktion mit höchstens 255 Zeichen ein.|
|Eine Rechnungsposition ist erforderlich, um eine Kündigung für die Lastausgleichsfunktion mit der UUID `aaaa-bbbb-cccc-dddd` zu verarbeiten.| |Wenden Sie sich an den IBM Support.|
|Interner Fehler. Daten konnten nicht abgerufen werden.|Metrikdaten können nicht abgerufen werden.|Laden Sie die Seite erneut. Wenn das Problem weiterhin auftritt, wenden Sie sich an den IBM Support.|
|Der Front-End-Port muss eine ganze Zahl zwischen 1 und 65535 sein, mit Ausnahme des Bereichs 56500-56520.|Möglicherweise haben Sie einen Front-End-Port zwischen 56500 und 56520 eingegeben.|Geben Sie einen beliebigen anderen eindeutigen Port zwischen 1 und 65535 ein, mit Ausnahme des Bereichs 56500-56520.|
|Der Back-End-Port muss eine ganze Zahl sein.|Möglicherweise haben Sie einen ungültigen Back-End-Portwert eingegeben.|Geben Sie einen gültigen Back-End-Port zwischen 1 und 65535 ein.|
|Der Back-End-Port muss eine ganze Zahl zwischen 1 und 65535 sein, mit Ausnahme des Bereichs 56500-56520.|Möglicherweise haben Sie einen Back-End-Port zwischen 56500 und 56520 eingegeben.|Geben Sie einen beliebigen anderen gültigen Port zwischen 1 und 65535 ein, mit Ausnahme des Bereichs 56500-56520.|
|Das Back-End-Protokoll `HTTP` ist mit dem Front-End-Protokoll `TCP` nicht kompatibel.|Sie haben möglicherweise eine inkompatible Kombination von Back-End-Protokoll und Front-End-Protokoll ausgewählt.|Wählen Sie eine gültige Kombination von Front-End-Protokoll und Back-End-Protokoll aus: <br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP|
|Die Mitgliedsgewichtung `<beliebiger_wert>` wird für das Mitglied `abcd-xxxx-yyyy-2222` angegeben. Der zulässige Gewichtungswert liegt zwischen 0 und 100.|Möglicherweise haben Sie eine ungültige Gewichtung eingegeben.|Geben Sie eine Gewichtung zwischen 0 und 100 ein.|
|Beim Abrufen der Server ist ein Fehler aufgetreten.|Ursache können Zeitlimitüberschreitungen im Netz sein.|Laden Sie die Seite erneut. Wenn das Problem weiterhin auftritt, wenden Sie sich an den IBM Support.|
