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

# Règles de couche 7
{: #layer-7-rules}

Les règles de couche 7 définissent une portion du trafic entrant qui doit correspondre à des valeurs spécifiques.

* Si le trafic entrant correspond à la valeur spécifiée pour une règle, celle-ci a pour résultat `true`.
* Les règles de couche 7 sont toujours associées à une politique de couche 7. Plusieurs règles de couche 7 peuvent être associées à la même politique de couche 7.
* Si plusieurs règles sont associées à une politique, chaque règle aura pour résultat `true` ou `false`. 
* Si toutes les règles associées à une politique ont pour résultat `true`, l'action associée à la politique sera appliquée à la demande. Dans le cas contraire, l'équilibreur de charge évaluera la politique suivante.

Les types de règle possibles sont les suivants : 

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

Elles indiquent la portion du trafic de couche 7 qui doit correspondre à la règle.

Type      |  Zone à extraire et à évaluer
----------| -----------------------
`HOST_NAME` | Partie nom d'hôte de l'URL (par exemple, `api.my_company.com`)
`FILE_TYPE` | Fin de l'URL, représentant le type de fichier (par exemple, `jpg`)
HEADER    | Zone dans l'en-tête HTTP
COOKIE    | Cookie nommé dans l'en-tête HTTP 
PATH      | Partie de l'URL située après le nom d'hôte (par exemple, `/index.html`)

Les règles comportent également un type de comparaison, qui indique comment elles doivent être évaluées.
Les types de comparaison possibles pour les règles sont les suivants : 

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

Type de comparaison |  Type d'évaluation
----------------|---------------------
`REGEX`           |  Faire correspondre la zone extraite (par exemple, `hostname`) avec l'expression régulière fournie
`STARTS_WITH`     |  Vérifier si la zone extraite commence par la chaîne fournie
`ENDS_WITH`       |  Vérifier si la zone extraite se termine par la chaîne fournie
`CONTAINS`        |  Vérifier si la zone extraite contient la chaîne fournie
`EQUAL_TO`        |  Vérifier si la zone extraite est identique à la chaîne fournie

**Remarque** : toutes les règles ne prennent pas en charge tous les types de comparaison. Par exemple, si vous utilisez `FILE_TYPE`, il est préférable d'utiliser les types de comparaison `REGEX` et `ENDS_WITH`.

## Propriétés de règle de couche 7

Propriété  | Description
------------- | -------------
Type | Spécifie le type de règle. Les types de règle peuvent être `HOST_NAME` (nom de l'hôte), `FILE_TYPE` (type du fichier), `HEADER` (en-tête), `COOKIE` (cookie) ou `PATH` (chemin).
Type de comparaison | Les types de comparaison sont utilisés conjointement au type de règle, à la clé et à la valeur pour définir une règle et classifier le trafic. Les types de comparaison possibles sont `REGEX`, `STARTS_WITH`, `ENDS_WITH`, `CONTAINS` et `EQUAL_TO`.
Key | Clé de description pour les types de règle `HEADER` et `COOKIE`. 
Value |  Pour les types de règle `HEADER` et `COOKIE`, la valeur est comparée à la clé.
Invert | Si vous affectez la valeur 1 à cette propriété, la valeur de cette comparaison de règle L7 est `true` à chaque fois que la règle spécifiée n'a pas de correspondance.
Layer 7 Policy ID | Identificateur unique de la politique à laquelle les règles sont associées.
