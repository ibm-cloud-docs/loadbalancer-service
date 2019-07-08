---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

keywords: load balancer, compare, explore

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
{:row-headers .row-headers}

# Exploración de equilibradores de carga de IBM
{: #explore}

IBM© Cloud ofrece varias soluciones de equilibrio de carga entre las que elegir. La siguiente tabla compara las distintas soluciones de equilibrio de carga para ayudarle a elegir la más adecuada para usted. Para obtener más información sobre una oferta, pulse sobre su nombre en la tabla.

Desplácese a la derecha para visualizar el resto de la tabla.
{: important}


|        | [IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started)| [Equilibrador de carga local](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (compartido)| [Equilibrador de carga local](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started) (dedicado)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (Estándar)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started) VPX/MPX (Platinum) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**VIP público**|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg) |
|**VIP privado**|![Icono de marca de selección](../../icons/checkmark-icon.svg)||![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg) |
|**Capa de 4 LB**|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg) |
|**Capa de 7 LB**|![Icono de marca de selección](../../icons/checkmark-icon.svg)|Persistencia de cookies|Persistencia de cookies|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg) |
|**Comprobaciones de estado**|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg) |
|**Escalado horizontal**|![Icono de marca de selección](../../icons/checkmark-icon.svg)|||| |
|**Descarga SSL**|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg)|![Icono de marca de selección](../../icons/checkmark-icon.svg) |
|**Gestión**|a través de IBM Portal|a través de IBM Portal|a través de IBM Portal|Auto-gestión (GUI del proveedor)|Auto-gestión (GUI del proveedor) |
|**Alta disponibilidad**|Integrada|Integrada|Opcional|Opcional|Opcional |
|**LB avanzado (optimización de TCP, compresión, almacenamiento en memoria caché, WAF)**||||Limitado|![Icono de marca de selección](../../icons/checkmark-icon.svg)|
|**LB global (GLB)**|||||![Icono de marca de selección](../../icons/checkmark-icon.svg) |
|**Precios**|Basado en uso|Tarifa mensual|Tarifa mensual|Tarifa mensual|Tarifa mensual |
{: row-headers}
{: class="comparison-table"}
{: caption="Comparación de las ofertas de equilibradores de carga de IBM" caption-side="top"}
{: summary="This table all of IBM's load balancer offerings, and provides links to their documentation."}
