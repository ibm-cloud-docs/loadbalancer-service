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

# Ebene 7-Richtlinie

Eine Ebene 7-Richtlinie (Layer 7, L7) wird verwendet, um den Datenverkehr zu klassifizieren, indem die zugehörigen L7-Informationen mit L7-Regeln abgeglichen werden. Falls die Regeln übereinstimmen, werden im Anschluss bestimmte Aktionen ausgeführt.  

* Eine Richtlinie wird auf einen Front-End-Anwendungsport (Protokoll) angewendet.  
* Es können mehrere Richtlinien auf dasselbe Protokoll angewendet werden. 

Da mehrere Richtlinien auf ein Protokoll angewendet werden können, ist jeder Richtlinie eine Priorität zugeordnet.  

* Richtlinien mit der niedrigsten Priorität werden zuerst ausgewertet.  
* Wenn die Regeln, die der Richtlinie zugeordnet sind, nicht mit dem Datenverkehr übereinstimmen, wird die Richtlinie mit der nächstniedrigsten Priorität ausgewertet.  

Wenn der Datenverkehr mit keiner der Richtlinienregeln übereinstimmt, wird er an einen Standardpool zurückgeleitet. Dies ist der Pool, der bei der Bereitstellung der Basislastausgleichsfunktion konfiguriert wurde. 

Jede Richtlinie ist einer Aktion zugeordnet, die ausgeführt wird, wenn alle Regeln in der Richtlinie mit dem Datenverkehr übereinstimmen. 

Dies können die folgenden Aktionen sein: 

- Ablehnen 
- Umleiten an eine URL
- Umleiten an einen Pool 

Richtlinien, für die `Ablehnen` festgelegt ist, werden zuerst ausgewertet, unabhängig von ihrer Priorität. 

Anschließend werden Richtlinien ausgewertet, für die `Umleiten an eine URL` festgelegt ist. 

Und schließlich werden Richtlinien ausgewertet, für die `Umleiten an einen Pool` festgelegt ist. 

Innerhalb jeder Aktionskategorie werden die Richtlinien in aufsteigender Prioritätsfolge (niedrigste bis höchste Priorität) ausgewertet. 

## Ebene 7-Richtlinieneigenschaften

Eigenschaft  | Beschreibung
------------- | -------------
Name | Der Name der Richtlinie. Jede Richtlinie muss einen eindeutigen Namen haben .
Aktion | Die Aktion, die ausgeführt werden soll, wenn die Regeln übereinstimmen. Die Aktionen sind `REJECT`, `REDIRECT_URL` und `REDIRECT_POOL`. Eine Richtlinie, deren Aktion `REJECT` ist, wird immer zuerst ausgewertet, unabhängig von ihrer Priorität. Richtlinien, deren Aktion `REDIRECT_URL` ist, werden als Nächstes ausgewertet, gefolgt von Richtlinien, deren Aktion `REDIRECT_POOL` ist .
Priorität | Richtlinien werden basierend auf der aufsteigenden Prioritätsfolge ausgewertet. 
Umleitungs-URL | Die URL, an die der Datenverkehr umgeleitet wird, wenn die Aktion `REDIRECT_URL` lautet .
Umleitungs-L7-Pool | Der Pool, an den der Datenverkehr gesendet wird, wenn die Aktion `REDIRECT_POOL` lautet .
Protokoll | Der Front-End-Anwendungsport, auf den die Richtlinie angewendet wird .

# Ebene 7-Regel
Ebene 7-Regeln definieren einen Teil des eingehenden Datenverkehrs, der mit bestimmten Werten abgeglichen werden soll. 

* Falls der eingehende Datenverkehr mit dem angegebenen Wert einer Regel übereinstimmt, wird die Regel zu `true` ausgewertet. 
* Ebene 7-Regeln sind immer einer Ebene 7-Richtlinie zugeordnet. Mehrere Ebene 7-Regeln können derselben Ebene 7-Richtlinie zugeordnet sein. 
* Wenn einer Richtlinie mehrere Regeln zugeordnet sind, wird jede einzelne Regel zu `true` oder `false` ausgewertet.  
* Wenn alle Regeln, die einer Richtlinie zugeordnet sind, zu `true` ausgewertet werden, wird die Richtlinienaktion auf die Anforderung angewendet. Andernfalls wertet die Lastausgleichsfunktion die nächste Richtlinie aus. 

Regeln können folgende Typen haben:  

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

Diese geben den Teil des Ebene 7-Datenverkehrs an, der mit der Regel abgeglichen werden soll. 

Typ      |  Feld, das extrahiert und ausgewertet werden soll
----------| -----------------------
`HOST_NAME` | Der Hostnamenteil der URL (z. B. `api.my_company.com`)
`FILE_TYPE` | Das Ende der URL, das den Dateityp darstellt (z. B. `jpg`) .
HEADER    | Ein Feld im HTTP-Header. r
COOKIE    | Ein benanntes Cookie im HTTP-Header. 
PATH      | Der Pfad der URL, der auf den Hostnamen folgt (z. B. `/index.html`. )

Regeln haben auch einen Vergleichstyp, der angibt, wie sie ausgewertet werden sollen. Regeln können folgende Vergleichstypen aufweisen:  

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

Vergleichstyp |  Art der Auswertung
----------------|---------------------
`REGEX`           |  Abgleichen des extrahierten Felds (z. B. `HOSTNAME`) mit dem bereitgestellten regulären Ausdruck. 
`STARTS_WITH`     |  Überprüfen, ob das extrahierte Feld mit der bereitgestellten Zeichenfolge beginnt.
`ENDS_WITH`       |  Überprüfen, ob das extrahierte Feld auf die bereitgestellte Zeichenfolge endet.
`CONTAINS`        |  Überprüfen, ob das extrahierte Feld die bereitgestellte Zeichenfolge enthält.
`EQUAL_TO`        |  Überprüfen, ob das extrahierte Feld mit der bereitgestellten Zeichenfolge identisch ist.

**HINWEIS**: Nicht alle Regeltypen unterstützen alle Vergleichstypen. Wenn Sie z. B. `FILE_TYPE` verwenden, ist es am besten, die Vergleichstypen `REGEX` und `ENDS_WITH` zu verwenden. 

## Ebene 7-Regeleigenschaften

Eigenschaft  | Beschreibung
------------- | -------------
Typ | Gibt den Typ der Regel an. Regeltypen können `HOST_NAME` (der Name des Hosts), `FILE_TYPE` (der Dateityp), `HEADER` (der Header), `COOKIE` (das Cookie) oder `PATH` (der Pfad) sein.
Vergleichstyp | Vergleichstypen werden in Verbindung mit dem Regeltyp, dem Schlüssel und dem Wert verwendet, um eine Regel zu definieren und den Datenverkehr zu klassifizieren. Vergleichstypen können `REGEX`, `STARTS_WITH`, `ENDS_WITH`, `CONTAINS` und `EQUAL_TO` sein.
Schlüssel | Der Beschreibungsschlüssel für die Regeltypen `HEADER` und `COOKIE`. 
Wert |  Für die Regeltypen `HEADER` und `COOKIE` wird der Wert mit dem Schlüssel verglichen.
Invertieren | Wenn Sie den Wert auf 1 setzen, wird der Wert dieses L7-Regelvergleichs auf `true` gesetzt, wenn die angegebene Regel nicht übereinstimmt.
Ebene 7-Richtlinien-ID | Die eindeutige ID der Richtlinie, an die die Regeln angehängt sind.
