---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: ssl, offload, cipher, suite

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

# Descarga de SSL con {{site.data.keyword.loadbalancer_full}}
{: #ssl-offload-with-ibm-cloud-load-balancer}

Para todas las conexiones HTTPS entrantes, el servicio del equilibrador de carga finaliza la conexión SSL y establece una comunicación HTTP de texto sin formato con el servidor back-end. Los reconocimientos SSL y las tareas de cifrado/descifrado de CPU se desplazan de los servidores back-end, lo que les permite utilizar todos sus ciclos de CPU para procesar el tráfico de aplicaciones.

Se necesita un certificado SSL para que el equilibrador de carga pueda realizar tareas de descarga SSL. Puede utilizar un certificado SSL preexistente o adquirir uno nuevo y gestionarlo a través de [Almacén de certificados de IBM© Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}.

## Suites de cifrado SSL
{: #ssl-cipher-suites}

El servicio de equilibrador de carga soporta TLS versión 1.2 con descarga SSL.

Los siguientes cifrados SSL están soportados por el equilibrador de carga:

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

Si el equilibrador de carga tiene uno o varios puertos de aplicación frontales HTTPS (protocolos) configurados, de forma predeterminada se habilitarán todos los cifrados SSL predefinidos anteriores para el equilibrador de carga.

Puede optar por habilitar cifrados SSL distintos para su equilibrador de carga, si es necesario. Para obtener más información, consulte [Elegir una suite de cifrado preferida para la aplicación HTTPS](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application).
{: note}
