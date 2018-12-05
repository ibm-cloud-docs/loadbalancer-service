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

# Acerca de

El servicio IBM Cloud Load Balancer ayuda a los clientes a mejorar la disponibilidad de las aplicaciones importantes para la empresa mediante la distribución del tráfico entre varias instancias del servidor de aplicaciones y el reenvío de tráfico solo a instancias en buen estado.

## Visión general de las características
El servicio IBM Cloud Load Balancer ofrece las siguientes características:

* Equilibrador de carga público (con acceso a Internet)
	* Servicio de acceso público a través de su nombre de dominio totalmente calificado (FQDN)
	* Instancias de servidor back-end en subredes privadas
* Equilibrador de carga interno
	* Servicio de acceso privado a través de su nombre de dominio totalmente calificado (FQDN)
	* Las solicitudes de cliente se direccionan a través de la red privada
	* Instancias de servidor back-end en subredes privadas
* Equilibrio de carga básica
	* Distribución del tráfico basada en información de puerto de aplicación de capa 4
	* Soporte para aplicaciones basadas en HTTP, HTTPS y TCP 
	* Variedad de métodos de equilibrio de carga tales como round robin (RR), round robin ponderado y menos conexiones
	* Equilibrio de carga entre las instancias de cálculo del servidor virtual y del servidor nativo residentes en el sistema local dentro de un centro de datos
* Comprobaciones del estado del servidor
	* Supervisión periódica del estado del servidor para garantizar que el tráfico se envíe solo a servidores en buen estado 
	* Comprobaciones de estado de capa 4 para puertos TCP y de capa 7 para puertos HTTP 
* Descarga SSL
	* Finalización del tráfico SSL entrante (HTTPS) utilizando comunicación HTTP en texto sin formato con servidores back-end
* Gestión de tráfico avanzada
	* Retención de cliente (persistencia de sesión)
	* Número máximo de conexiones por puerto virtual
* Gestión fácil con interfaz gráfica intuitiva y API
* Fiabilidad incorporada 
* Precio basado en uso 
* Supervisión
    * Supervisa las métricas de rendimiento, conexiones activas y tasa de conexión para los protocolos HTTP, HTTPS y TCP sobre intervalos de tiempo especificados por el usuario. Consulte [Supervisión de métricas](monitoring-metrics.html) para obtener detalles adicionales.
* Soporte de capa 7
    * El tráfico HTTP/HTTPS se direcciona a diferentes servicios de fondo en función de la cabecera HTTP y se realiza utilizando políticas y reglas. Las reglas se utilizan para clasificar el tráfico y se basan en los campos de cabecera HTTP. Cuando el tráfico coincide con todas las reglas, se toma una acción especificada por la política.    
