---

copyright:
  years: 2017, 2018
lastupdated: "2019-02-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Actualizaciones recientes de IBM Cloud Load Balancer
{: #recent-updates-for-ibm-cloud-load-balancer}

Descubra las características nuevas y actualizadas de IBM© Cloud Load Balancer.

## Diciembre de 2018
### Cifrado de datos de fondo y reenvío de registros de datos
Ahora IBM Cloud Load Balancer da soporte al cifrado de fondo y a la posibilidad de reenviar sus registros de datos. El cifrado de fondo permite cifrar el tráfico de datos de extremo a extremo, incluido el tráfico entre el equilibrador de carga y los servidores de fondo. El reenvío de registros de datos le permite enviar registros de datos de los equilibradores de carga al servicio de análisis de registros de IBM Bluemix.

## Agosto de 2018
### Soporte de capa 7
IBM Cloud Load Balancer ahora da soporte al equilibrio de carga de capa 7. Con el soporte de capa 7 (L7), el tráfico se puede redirigir a un URL, rechazar o distribuir a los miembros de la agrupación L7, incluidas las instancias de servidores nativos y virtuales. El tráfico de datos de entrada se clasifica mediante políticas y reglas de capa 7. Las políticas definen qué acción se debe realizar cuando el tráfico de datos coincide con las reglas asociadas.

Consulte [Equilibrio de carga de capa 7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing) para obtener detalles adicionales.

## Abril de 2018
### Escalado horizontal
La capacidad de IBM Cloud Load Balancer ahora aumenta automáticamente cuando la carga aumenta y se reduce cuando la carga disminuye. Cuando crea el equilibrador de carga, empieza con dos dispositivos, pero el número de dispositivos puede aumentar hasta 16 (en el momento de escribir este documento) a medida que el sistema de supervisión detecta un incremento en la carga. Las direcciones IP de cada uno de los dispositivos activos se añaden como registros A DNS al nombre de dominio completo (FQDN) del equilibrador de carga.

### Equilibrador de carga interno
Ya está disponible una versión "interna" muy solicitada de nuestro IBM Cloud Load Balancer. Este equilibrador de carga no está expuesto públicamente, pero se puede seguir utilizando para equilibrar las aplicaciones dentro de sus redes privadas de IBM Cloud (en un despliegue de varios niveles, por ejemplo, tal como se muestra en la imagen).

![Equilibrador de carga interno](./images/InternalLB.png)

Es seguro y coherente con las versiones anteriores de IBM Cloud Load Balancer de la parte pública.

### Supervisión de métricas
Ahora puede optimizar el servicio "IBM Cloud Monitoring" para supervisar las siguientes medidas de rendimiento asociadas con el equilibrador de carga y la aplicación:

* Rendimiento
* Velocidad de conexión
* Conexiones activas

![Supervisión de métricas](./images/Metrics.png)

La interfaz de usuario web del equilibrador de carga recopila y muestra hasta dos semanas de ejemplos. Los datos también se pueden visualizar en el portal del servicio IBM Cloud Monitoring. Si requiere datos de más de dos semanas, en función del volumen de otras métricas de nube que esté enviando a la instancia de Cloud Monitoring, es posible que deba actualizar su plan de supervisión. Consulte [Supervisión de métricas](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer) para obtener detalles adicionales.

Esta característica requiere que se enlacen las cuentas de IaaS y PaaS de IBM Cloud mediante unos pocos [pasos sencillos](/docs/account?topic=account-unifyingaccounts).

### Personalización de las suites de cifrado
Ahora puede personalizar las suites de cifrado que se utilizan cuando el equilibrador de carga está configurado para terminación SSL.

Cuando habilita la terminación SSL en IBM Cloud Load Balancer (seleccionando **HTTPS** como protocolo frontal), se habilita un conjunto predeterminado y cuidadosamente seleccionado de suites de cifrado que se ajustan a las prácticas recomendadas de seguridad. IBM sigue de cerca las nuevas vulnerabilidades que se puedan descubrir y actualiza la lista en consecuencia. Esto, junto con las actualizaciones de seguridad de componentes de software y hardware, ayuda a mantener las aplicaciones seguras en todo momento.

Consulte el tema sobre la [Suite de cifrado personalizado](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application) para obtener más información.
