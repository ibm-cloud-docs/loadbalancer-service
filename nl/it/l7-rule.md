---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, rules, traffic

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}
{:tip: .tip}

# Regole L7
{: #layer-7-rules}

Le regole L7 definiscono una parte del traffico in entrata che deve soddisfare valori specifici.

* Se il traffico in entrata soddisfa il valore specificato di una regola, la regola viene valutata come `true`.
* Le regole L7 sono sempre associate a una politica L7. Più regole L7 possono essere associate alla stessa politica L7.
* Se più regole sono associate a una politica, ciascuna regola verrà valutata come `true` o `false`.
* Se tutte le regole associate a una politica sono valutate come `true`, l'azione della politica verrà applicata alla richiesta. In caso contrario, il programma di bilanciamento del carico valuta la politica successiva.

Le regole hanno tipi che possono essere:

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

Questi indicano la parte del traffico L7 che deve soddisfare la regola.

Tipo      |  Campo da estrarre e valutare
----------| -----------------------
`HOST_NAME` | La parte nome host dell'URL (ad esempio, `api.my_company.com`)
`FILE_TYPE` | La fine dell'URL che rappresenta il tipo di file (ad esempio, `jpg`)
HEADER    | Un campo nell'intestazione HTTP
COOKIE    | Un cookie denominato nell'intestazione HTTP
PATH      | La parte dell'URL che segue il nome host (ad esempio, `/index.html`)

Le regole hanno anche un tipo di confronto che indica in che modo vengono valutate. 
Le regole possono avere i seguenti tipi di confronto:

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

Tipo di confronto |  Tipo di valutazione
----------------|---------------------
`REGEX`           |  Mette in corrispondenza il campo estratto (ad esempio, `hostname`) con l'espressione regolare fornita
`STARTS_WITH`     |  Verifica se il campo estratto inizia con la stringa fornita
`ENDS_WITH`       |  Verifica se il campo estratto termina con la stringa fornita
`CONTAINS`        |  Verifica se il campo estratto contiene la stringa fornita
`EQUAL_TO`        |  Verifica se il campo estratto è identico alla stringa fornita

Non tutti i tipi di regole supportano tutti i tipi di confronto. Ad esempio, se stai utilizzando `FILE_TYPE`, è meglio utilizzare i tipi di confronto `REGEX` e `ENDS_WITH`.
{: tip}

## Proprietà della regola L7
{: #layer-7-rule-properties}

Proprietà  | Descrizione
------------- | -------------
Tipo | Specifica il tipo di regola. I tipi di regole possono essere `HOST_NAME` (il nome dell'host), `FILE_TYPE` (il tipo del file), `HEADER` (l'intestazione), `COOKIE` (il cookie) o `PATH` (il percorso).
Tipo di confronto | I tipi di confronto vengono utilizzati insieme al tipo di regola, alla chiave e al valore per definire una regola e classificare il traffico. I tipi di confronto possono essere: `REGEX`, `STARTS_WITH`, `ENDS_WITH`, `CONTAINS` e `EQUAL_TO`.
Chiave | La chiave di descrizione per i tipi di regola `HEADER` e `COOKIE`.
Valore |  Per i tipi di regola `HEADER` e `COOKIE`, il valore viene confrontato con la chiave.
Invert | Se imposti il valore su 1, il valore di questo confronto della regola L7 viene impostato su `true` quando la regola specificata non viene soddisfatta.
ID politica L7 | L'identificativo univoco della politica a cui vengono collegate le regole.
