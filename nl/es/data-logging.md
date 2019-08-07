---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Registro de datos
{: #data-logging}

Los registros de datos y de comprobación de estado son útiles para fines de depuración y mantenimiento. Con la característica de registro de datos habilitada, IBM Load Balancer reenvía estos registros al [servicio IBM Cloud Log Analysis ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://logging.ng.bluemix.net){:new_window} de su cuenta.

Para habilitar o inhabilitar esta característica tiene dos opciones:

* Crear un nuevo equilibrador de carga y active esta característica.
* Utilizar la API: `enableOrDisableDataLogs`.

## Visualización de registros en el servicio IBM Cloud Logging Analysis
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

Inicie sesión en el [Servicio IBM Cloud Logging Analysis ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://logging.ng.bluemix.net){:new_window} con una cuenta de cliente de IBM Cloud. Los registros se pueden visualizar con Kibana. Consulte [este tema](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana) para obtener más información.

Sólo se envían registros de datos si las cuentas de Softlayer e IBM Cloud están enlazadas. Seleccione la cuenta de IBM Cloud asociada con su cuenta de Softlayer e inicie sesión en el panel de control de Kibana.
{: tip}

## Ejemplos de salida de registro
{: #log-output-examples}

La siguiente salida es un ejemplo de un registro de datos de {{site.data.keyword.loadbalancer_full}}:

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` es el nombre del equilibrador de carga y `dal09` es el centro de datos.
* `323698` es el ID de cuenta. `643866` es el ID del equilibrador de carga. `713576` es el ID de miembro.
* `xxx.xxx.xxx.xxx` es una IP pública que se ha enmascarado para GDPR.

La siguiente salida es un ejemplo de un registro de comprobación de estado dentro del servicio IBM Cloud Logging Analysis:

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` es la dirección IP del miembro.
* `682175` es el ID de miembro.
