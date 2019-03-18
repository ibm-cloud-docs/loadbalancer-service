---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Gestión avanzada de tráfico con IBM Cloud Load Balancer
{: #advanced-traffic-management-with-ibm-cloud-load-balancer}

En esta sección, se abordan varias características de gestión de tráfico avanzada disponibles con el servicio de equilibrador de carga.

## Número máx. de conexiones

Utilice la configuración Número máx. de conexiones para limitar el número máximo de conexiones simultáneas con un puerto virtual frontal determinado. De forma predeterminada, no se especifica ningún límite. El número máximo permitido de conexiones simultáneas con un puerto virtual frontal determinado o con todos los puertos virtuales frontales del sistema es de 15.000.  

## Persistencia de sesión

El equilibrador de carga soporta la persistencia de sesión en un puerto VIP determinado basado en la dirección `source IP` de la conexión. Por ejemplo, si se habilita la persistencia de sesión para el puerto 80 (HTTP), entonces los intentos de conexión HTTP posteriores desde el mismo cliente (misma IP de origen) serán persistentes en el mismo servidor back-end. Esta característica está disponible para los tres protocolos soportados (HTTP, HTTPS y TCP).

El equilibrador de carga soporta un máximo de 10.000 entradas de persistencia de cliente. La hora de caducidad de estas entradas es de 10 minutos. Las solicitudes adicionales que se reciban del mismo cliente después de 10 minutos, se reenviarán a otro servidor back-end. Si la entrada de persistencia de sesión no ha caducado, pero el puerto es erróneo, se seleccionará otro servidor para reenviar posibles conexiones de cliente posteriores.  

## Estado activo de HTTP
El equilibrador de carga soporta el modo `HTTP keep alive` siempre que esté habilitado tanto en el cliente como en los servidores back-end. El equilibrador de carga intenta reutilizar las conexiones HTTP del lado del servidor para mejorar la eficiencia de conexión y reducir la latencia.

## Tiempos de espera de conexión
El equilibrador de carga utiliza los siguientes valores de tiempo de espera. Actualmente no se pueden personalizar estos valores.

| Nombre | Descripción | Tiempo de espera |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | ------------------- |
| Intento de conexión de lado del servidor    | Ventana de tiempo máximo que puede utilizar el equilibrador de carga para establecer una conexión TCP con el servidor back-end. Si el intento de conexión no es satisfactorio, el equilibrador de carga lo intentará con el siguiente servidor disponible siguiendo el método de equilibrio de carga configurado por el usuario. | 5 segundos   |
| Conexión inactiva del lado del cliente  | El tiempo máximo de inactividad, transcurrido el cual el equilibrador de carga desactiva la conexión del lado del cliente si este no ha podido cerrar correctamente la conexión.| 50 segundos  |
| Conexión inactiva del lado del servidor | El tiempo máximo de inactividad (con configuración de protocolo back-end de TCP), transcurrido el cual el equilibrador de carga cierra la conexión del lado del servidor. Si el equilibrador de carga, con la configuración de protocolo back-end de HTTP, no puede recibir una respuesta a la solicitud HTTP enviada en la ventana de tiempo de espera de inactividad, devolverá un mensaje de error al cliente final.                                | 50 segundos |
{: caption="Tabla 1. Valores de tiempo de espera del equilibrador de carga" caption-side="top"} 

## Conservación de la dirección IP del cliente final 

El equilibrador de carga funciona como proxy inverso, finalizando el tráfico entrante desde el cliente. Establece una conexión independiente a la instancia de servidor back-end mediante el uso de una dirección IP propia. Para las conexiones HTTP con servidores back-end (con conexiones HTTP o HTTPS frontales), el equilibrador de carga conserva la dirección IP del cliente original incluyéndola en la cabecera `X-Forwarded-For HTTP`. Para las conexiones TCP, la información de la IP de cliente original no se conserva.
