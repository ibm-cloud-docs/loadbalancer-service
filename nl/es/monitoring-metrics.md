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

# Supervisión de métricas

El equilibrador de carga supervisa las métricas siguientes: 

* Rendimiento
* Conexiones activas
* Velocidad de conexión

Estas métricas se visualizan como gráficos que se pueden ver seleccionando el separador **Supervisión** y están disponibles programáticamente como puntos de datos de serie temporal utilizando la API `getListenerTimeSeriesData`.

Cada punto de datos contiene una indicación de fecha y hora en tiempo de época de UNIX y el valor de métrica para dicho intervalo de tiempo que finaliza en esa indicación de fecha y hora. El usuario puede especificar los protocolos y el intervalo de tiempo sobre el que se debe informar sobre las métricas. 

Los protocolos soportados son:

* HTTP
* HTTPS
* TCP

La especificación de un protocolo filtra la métrica por ese protocolo.

Por ejemplo, si no se especifica ningún protocolo y la métrica es *Rendimiento*, se notifica el rendimiento total de todos los protocolos.

Si el protocolo es *HTTP*, sólo se informa del rendimiento del tráfico HTTP.

El usuario también puede especificar el intervalo de tiempo sobre el que se debe informar sobre la métrica. Los intervalos de tiempo soportados son: 

* 1 hora
* 6 horas
* 12 horas
* 24 horas
* 1 semana
* 2 semanas

El número de puntos de datos notificados es aproximadamente el mismo para cada intervalo de tiempo.  
Por ejemplo, si el intervalo es de 1 hora, cada punto de datos representa 5 minutos de datos.

Si el intervalo es de 2 semanas, cada punto de datos representa 24 horas de datos.

La tabla siguiente muestra cómo se obtienen los puntos de datos a partir del intervalo de tiempo:

| Intervalo de tiempo | Precisión del punto de datos | Número de puntos de datos |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
| 1 hora    | 5 minutos | 12   |
| 6 horas   | 30 minutos | 12  |
| 12 horas  | 1 hora | 12 |
| 24 horas  | 2 horas | 12 |
| 1 semana    | 12 horas | 12 |
| 2 semanas  | 24 horas | 12 |

# Cómo habilitar la supervisión de métricas

Para recuperar las métricas de supervisión, debe enlazar la cuenta de SoftLayer con la cuenta de IBM Cloud. Consulte [este tema ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") ](/docs/account/softlayerlink.html#link_user_account) para obtener más información.
