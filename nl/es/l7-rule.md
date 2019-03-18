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

# Reglas de capa 7
{: #layer-7-rules}

Las reglas de capa 7 definen una parte del tráfico de entrada que se va a comparar con valores específicos.

* Si el tráfico de entrada coincide con el valor especificado de una regla, la regla se evalúa como `true`.
* Las reglas de capa 7 siempre están asociadas a una política de capa 7. Se pueden asociar varias reglas de capa 7 con la misma política de capa 7.
* Si se asocian varias reglas con una política, cada regla se evaluará como `true` o `false`. 
* Si todas las reglas asociadas a una política se evalúan en `true`, la acción de política se aplicará a la solicitud. De lo contrario, el equilibrador de carga evalúa la siguiente política.

Las reglas tienen tipos, que pueden ser: 

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

Estos indican la parte del tráfico de capa 7 que se va a comparar con la regla.

Tipo      |  Campo que se va a extraer y evaluar
----------| -----------------------
`HOST_NAME` | La parte de nombre de host del URL (por ejemplo, `api.my_company.com`)
`FILE_TYPE` | El final del URL, que representa el tipo de archivo (por ejemplo, `jpg`)
HEADER    | Un campo de la cabecera HTTP
COOKIE    | Una cookie nombrada en la cabecera HTTP 
PATH      | La parte del URL que va después del nombre de host (por ejemplo, `/index.html`)

Las reglas también tienen un tipo de comparación, que indica cómo se deben evaluar. 
Las reglas pueden tener los siguientes tipos de comparación: 

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

Tipo de comparación |  Tipo de evaluación
----------------|---------------------
`REGEX`           |  Comparar el campo extraído (por ejemplo, `hostname`) con la expresión regular suministrada
`STARTS_WITH`     |  Verificar si el campo extraído comienza por la serie proporcionada
`ENDS_WITH`       |  Verificar si el campo extraído termina por la serie proporcionada
`CONTAINS`        |  Verificar si el campo extraído contiene la serie proporcionada
`EQUAL_TO`        |  Verificar si el campo extraído es idéntico a la serie proporcionada

**NOTA**: no todos los tipos de regla dan soporte a todos los tipos de comparación. Por ejemplo, si utiliza `FILE_TYPE`,
es mejor utilizar los tipos de comparación `REGEX` y `ENDS_WITH`.

## Propiedades de regla de capa 7

Propiedad  | Descripción
------------- | -------------
Tipo | Especifica el tipo de regla. Los tipos de regla pueden ser `HOST_NAME` (el nombre del host), `FILE_TYPE` (el tipo de archivo), `HEADER` (la cabecera), `COOKIE` (la cookie) o `PATH` (la vía de acceso).
Tipo de comparación | Los tipos de comparación se utilizan junto con el tipo de regla, la clave y el valor para definir una regla y clasificar el tráfico. Los tipos de comparación pueden ser: `REGEX`, `STARTS_WITH`, `ENDS_WITH`, `CONTAINS` y `EQUAL_TO`.
Clave | La clave de descripción para los tipos de regla `HEADER` y `COOKIE`. 
Valor |  En el caso de los tipos de regla `HEADER` y `COOKIE`, el valor se compara con la clave.
Invertir | Si establece el valor en 1, el valor de esta comparación de regla L7 se establece en `true` siempre que la regla especificada no coincide.
ID de política de capa 7 | El identificador exclusivo de la política a la que se adjuntan las reglas.
