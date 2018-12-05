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

# Configurar parámetros de IBM Cloud Load Balancer
Una vez que se crea un equilibrador de carga, puede configurarlo para el equilibrio de carga elástico. Para hacerlo:

1. Asigne un nombre a su equilibrador de carga y, si lo desea, añada una descripción.

	<img src="images/lb-config-basic.png" alt="dibujo" style="width: 300px;"/>

2. Especifique los detalles del perfil de la aplicación identificando los protocolos y puertos en los que escucha la aplicación. Puede utilizar la misma configuración para el extremo frontal y de fondo, o puede exponer un puerto frontal diferente (por ejemplo, por motivos de seguridad).

3. El método de equilibrio de carga predeterminado es **Round robin**. Puede cambiarlo por **Round robin ponderado** o por **Conexiones mínimas** en la lista desplegable, en función de las necesidades de la aplicación.

4. Si lo desea, puede habilitar **Retención de sesiones**. Si está habilitado, todas las solicitudes procedentes de un determinado usuario final (por ejemplo, uno con la misma IP de origen) van al mismo servidor de fondo durante un tiempo de "retención" definido por el sistema.

5. También puede establecer el **Límite máximo de conexiones** en la aplicación.

6. Pulse **Añadir protocolo** para especificar puertos y protocolos adicionales en los que la aplicación puede estar a la escucha. Asegúrese de que todos los puertos frontales sean exclusivos. Puede elegir HTTP, HTTPS o TCP como protocolo de componente frontal.  

	<img src="images/lb-add-protocol.png" alt="dibujo" style="width: 300px;"/>

	Se pueden definir un máximo de dos puertos en el momento de la configuración inicial. Luego se pueden añadir más puertos, después de crear la instancia de servicio. Consulte [Limitaciones en el número de puertos](faqs.html#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-) para
obtener más información sobre el número máximo de puertos permitidos.
{:note:}

7. IBM Cloud Load Balancer termina las conexiones HTTPS (HTTP sobre SSL) de entrada, se comunica en HTTP de texto sin formato con los servidores de aplicaciones de fondo y descarga las tareas SSL que requieren un uso intensivo de procesador de los servidores. Debe cargar el certificado SSL. Seleccione uno de los certificados disponibles en la lista desplegable.  

	<img src="images/lb-ssl-cert.png" alt="dibujo" style="width: 300px;"/>

	Si no dispone de un certificado existente, pulse ** Añadir un certificado nuevo**. Esto le lleva a un servicio de certificados de IBM Cloud donde puede adquirir un nuevo certificado o cargar uno existente. 
	
	Después de añadir el certificado, vuelva a la página de configuración del equilibrador de carga y pulse el icono de renovación que hay bajo la lista desplegable Certificado SSL para ver y añadir el certificado que acaba de cargar.

	<img src="images/order-ssl-cert.png" alt="dibujo" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="dibujo" style="width: 300px;"/>

	**NOTA**: nunca suprima ningún certificado asociado con escuchas HTTPS, ya que esto puede provocar problemas con la funcionalidad.

8. Pulse **Siguiente**.

## Configurar comprobaciones de estado
La definición de comprobaciones de estado es obligatoria para cada puerto de aplicación. Son los puertos de fondo identificados en el menú de configuración básica anterior.

<img src="images/config-health-check.png" alt="dibujo" style="width: 300px;"/>

El sistema implementa una configuración de comprobación de estado predeterminada para estos puertos de fondo. Puede personalizar estos valores para que se ajusten a las necesidades de la aplicación.

* **Interval**: el intervalo en segundos entre dos intentos consecutivos de comprobación de estado
* **Timeout**: el intervalo máximo de tiempo que el sistema esperará una respuesta a la solicitud de comprobación de estado
* **Max Trials**: el número máximo de intentos adicionales de comprobación de estado que realizará el sistema antes de declarar que el puerto no está en buen estado
* **Path**: la vía de acceso de HTTP URL correspondiente a la comprobación de estado     

Pulse **Siguiente** para habilitar su elección.

## A continuación
[Identifique los recursos de la aplicación](identify-app-resources.html), como por ejemplo las agrupaciones de origen y los mecanismos de comprobación de estado.
