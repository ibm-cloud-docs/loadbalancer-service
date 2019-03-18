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

# Agrupación de capa 7
{: #layer-7-pool}

Una agrupación de capa 7 (L7) es una agrupación lógica de los servidores (miembros) para gestionar las solicitudes entrantes.

La característica de equilibrio de carga de capa 7 puede dirigir el tráfico de entrada a diferentes agrupaciones de fondo basándose en políticas y reglas. Esta característica recibe soporte mediante la asociación de varias agrupaciones L7 con un equilibrador de carga. Las agrupaciones de capa 7 se utilizan con las políticas de capa 7 cuya acción consiste en `redirigir a la agrupación`.

Las agrupaciones L7 solo dan soporte a HTTP como protocolo de fondo.

## Persistencia de sesión
La persistencia de sesión se puede configurar para cada agrupación de capa 7. Para obtener más detalles, consulte la  
[sección sobre tráfico avanzado](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer).

## Miembros de capa 7

Los servidores de fondo que están asociados a una agrupación de capa 7 se denominan Miembros de capa 7.

El mismo servidor de fondo se puede añadir varias veces a agrupaciones L7, especificando un número de puerto distinto cada vez.

## Configurar comprobaciones de estado
La definición de comprobaciones de estado es obligatoria para cada agrupación de capa 7. El sistema implementa una configuración de comprobación de estado predeterminada para las agrupaciones L7.

Puede personalizar estos valores para que se ajusten a las necesidades de la aplicación:

 * **Interval**: el intervalo en segundos entre dos intentos consecutivos de comprobación de estado.
 * **Timeout**: el intervalo máximo de tiempo que el sistema esperará una respuesta a la solicitud de comprobación de estado.
 * **MaxRetries**: el número máximo de intentos adicionales de comprobación de estado que realizará el sistema antes de declarar que el servicio no está en buen estado.
 * **UrlPath**: la vía de acceso de HTTP URL correspondiente a la comprobación de estado de capa 7.
