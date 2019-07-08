---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: resources, server, application, instance, configure

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}

# Identificación de los recursos del servidor de aplicaciones
{: #identifying-your-application-server-resources}

Localice las **instancias del servidor** en la tabla de la parte inferior y pulse **+** para añadirlas detrás del equilibrador de carga. Puede seleccionar entre las instancias de servidor virtual de IBM© Cloud (VSI) y los servidores nativos de su cuenta.

Estas instancias de servidor deben ser locales para el centro de datos en el que se despliega el servicio de equilibrador de carga. Además, las instancias de servidor de los centros de datos vecinos dentro de la misma ciudad también se pueden añadir (por ejemplo, si las tres primeras letras del nombre del centro de datos son las mismas).

<img src="images/locate-server-instance.png" alt="dibujo" style="width: 300px;"/>

Pulse **Siguiente**.

Las **ponderaciones** del servidor solo son relevantes cuando se utiliza el método de equilibrio de carga **Round robin ponderado**. La ponderación predeterminada es 50 y el rango es de 0 a 100. Las ponderaciones están en gris en los otros métodos de equilibrio de carga.
{: note}

Consulte [Limitaciones en el número de servidores de aplicaciones](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-) para obtener más información sobre el límite máximo para el número de servidores de aplicaciones.
{: tip}

## A continuación
{: #what-s-next-3}
[Revise el contenido](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order) de su pedido antes de instalarlo.
