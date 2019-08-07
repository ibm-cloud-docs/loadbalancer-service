---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, policies, rules, pools

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Equilibrio de carga de capa 7
{: #layer-7-load-balancing}

El servicio {{site.data.keyword.loadbalancer_full}} distribuye el tráfico entre varias instancias del servidor, incluidas instancias de servidor nativo y virtual, utilizando datos de capa 7 (capa de aplicación).

 * El tráfico de datos que se va a distribuir se clasifica mediante políticas y reglas.
 * Las políticas definen qué acción se debe realizar cuando el tráfico de datos coincide con todas reglas asociadas a la política.
 * El equilibrio de carga de capa 7 (L7) solo recibe soporte para el tráfico HTTP y HTTPS.

## Políticas y reglas de capa 7
{: #layer-7-policies-and-rules}
Una política de capa 7 está asociada a un puerto de aplicación frontal. Se pueden asociar varias políticas a un puerto frontal.

 * Estas políticas se evalúan por orden, en función de la prioridad asignada a cada política.
 * Se emprende una acción asociada cuando se coincide con la política.
 * Cada regla L7 está asociada a una política.
 * Si todas las reglas asociadas a la política se evalúan como `true` significa que la política se coincide, por lo que se emprende la acción asociada.

Consulte [Política y reglas de L7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-policy) para ver más información.

## Agrupaciones de capa 7
{: #layer-7-pools}
Cada agrupación de equilibrador de carga de capa 7 contiene una o varias instancias de servidor lógico.

 * Cada instancia de servidor lógico se identifica mediante una dirección IP y un número de puerto.
 * Cada agrupación tiene un supervisor de estado asociado, que supervisa el estado de todos los servidores de la agrupación.
 * Se puede configurar una agrupación para la persistencia de sesiones.
 * Utilice la dirección IP de origen del cliente para configurar la persistencia de sesiones.

Consulte [Agrupaciones de L7](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-pool) para ver más información.
