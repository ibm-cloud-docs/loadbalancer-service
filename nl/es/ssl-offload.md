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

# Descarga SSL

Para todas las conexiones HTTPS entrantes, el servicio del equilibrador de carga finaliza la conexión SSL y establece una comunicación HTTP de texto sin formato con el servidor back-end. Los reconocimientos SSL y las tareas de cifrado/descifrado de CPU se desplazan de los servidores back-end, lo que les permite utilizar todos sus ciclos de CPU para procesar el tráfico de aplicaciones. 

Se necesita un certificado SSL para que el equilibrador de carga pueda realizar tareas de descarga SSL. Puede utilizar un certificado SSL preexistente o adquirir uno y gestionarlo desde el [almacén de certificados de IBM Cloud](https://control.softlayer.com/security/sslcerts). 

# Suites de cifrado SSL
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

**NOTA:** puede optar por habilitar cifrados SSL distintos para su equilibrador de carga, si es necesario. Para obtener más información, consulte [Elegir una suite de cifrado preferida para la aplicación HTTPS](custom-ciphers.html).
