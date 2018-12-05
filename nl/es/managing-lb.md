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

# Supervisión y gestión del servicio
Puede editar la configuración o supervisar el rendimiento del servicio pulsando el URL del nombre de servicio en la página de resumen del equilibrador de carga. 

La **dirección del nombre completo del dominio (FQDN)** de la instancia de servicio del equilibrador de carga se encuentra justo debajo del nombre de servicio. Los usuarios finales pueden conectarse a su aplicación a través de esta dirección FQDN. Tenga en cuenta que las direcciones IP públicas y privadas del servicio equilibrador de carga no están expuestas al mundo exterior; solo se expone la dirección FQDN. 

<img src="images/fqdn-address.png" alt="dibujo" style="width: 300px;"/>

El separador **Visión general** proporciona información de estado de alto nivel de servicio. Muestra el estado actual de los servidores de aplicaciones y sus puertos. También proporciona un resumen rápido del rendimiento del sistema: rendimiento, velocidad de conexión, conexiones concurrentes, etc. 

Vaya al separador **Supervisión** para ver los diagramas en tiempo real del rendimiento del sistema. Estos gráficos se pueden consultar por puerto de aplicación individual y para distintos periodos de tiempo. 

<img src="images/monitor-lb.png" alt="dibujo" style="width: 300px;"/>

Puede editar la configuración existente desde los separadores **Protocolos**, **Instancias de servidor** y **Comprobaciones de estado**. Por ejemplo, vaya al separador Protocolos para definir puertos de aplicación adicionales o para personalizar la lista de cifrado SSL. 

<img src="images/protocols-monitor.png" alt="dibujo" style="width: 300px;"/>
