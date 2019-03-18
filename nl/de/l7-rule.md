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

# Ebene 7-Regeln
{: #layer-7-rules}

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

Regeln haben auch einen Vergleichstyp, der angibt, wie sie ausgewertet werden sollen. 
Regeln können folgende Vergleichstypen aufweisen: 

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
