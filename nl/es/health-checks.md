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

# Ejecución de comprobaciones de estado con IBM Cloud Load Balancer
{: #performing-health-checks-with-ibm-cloud-load-balancer}

Las definiciones de comprobaciones de estado son obligatorias para todos los puertos de aplicación back-end. El puerto y el protocolo de la configuración de la comprobación de estado deben coincidir con los definidos; de lo contrario, se rechazará la configuración. 

El equilibrador de carga lleva a cabo comprobaciones de estado periódicas para supervisar el estado de los puertos back-end y reenviarles tráfico de clientes en consecuencia. Si se detecta un puerto de servidor back-end en mal estado, no se le reenvían más conexiones nuevas. El equilibrador de carga sigue supervisando el estado de dichos puertos y reanuda su uso cuando recobran el buen estado y superan dos intentos de comprobación de estado. 

Las comprobaciones de estado con puertos HTTP y TCP se llevan a cabo de la siguiente manera:

* **HTTP:** se envía una solicitud `HTTP GET` con un URL especificado previamente al puerto del servidor back-end. Se marca que el puerto del servidor se encuentra en buen estado tras haber recibido una respuesta `200 OK`. El URL `GET` predeterminado es “/” a través de la GUI y se puede personalizar. 

* **TCP:** el equilibrador de carga intenta abrir una conexión con el servidor back-end en un puerto TCP especificado. Se marca que el puerto del servidor se encuentra en buen estado si la conexión finaliza correctamente y, a continuación, se cierra. 

	**NOTA:** el intervalo entre comprobaciones de estado es de 5 segundos, el tiempo de espera predeterminado con una solicitud de comprobación de estado es de 2 segundos y el número predeterminado de intentos es de 2. 
