---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Exploración de equilibradores de carga de IBM
{: #explore}

IBM© Cloud ofrece varias soluciones de equilibrio de carga entre las que elegir. La siguiente tabla compara las distintas soluciones de equilibrio de carga para ayudarle a elegir la más adecuada para usted. Para obtener más información sobre una oferta, pulse sobre su nombre en la tabla. 

Desplácese a la derecha para visualizar el resto de la tabla.


|        | [IBM Cloud Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started-with-ibm-cloud-load-balancer)| [Equilibrador de carga local](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started-with-local-load-balancer#getting-started-with-local-load-balancer) (compartido)| [Equilibrador de carga local](/docs/infrastructure/local-load-balancer?topic=local-load-balancer-getting-started-with-local-load-balancer#getting-started-with-local-load-balancer) (dedicado)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started-with-citrix-netscaler-vpx-software-appliance#getting-started-with-citrix-netscaler-vpx-software-appliance) VPX/MPX (Estándar)| [Citrix NetScaler](/docs/infrastructure/citrix-netscaler-vpx?topic=citrix-netscaler-vpx-getting-started-with-citrix-netscaler-vpx-software-appliance#getting-started-with-citrix-netscaler-vpx-software-appliance) VPX/MPX (Platinum) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**VIP público**|Sí|Sí|Sí|Sí|Sí |
|**VIP privado**|Sí|No|Sí|Sí|Sí |
|**Capa de 4 LB**|Sí|Sí|Sí|Sí|Sí |
|**Capa de 7 LB**|Sí|Persistencia de cookies|Persistencia de cookies|Sí|Sí |
|**Comprobaciones de estado**|Sí|Sí|Sí|Sí|Sí |
|**Escalado horizontal**|Sí|No|No|No|No |
|**Descarga SSL**|Sí|Sí|Sí|Sí|Sí |
|**Gestión**|a través de IBM Portal|a través de IBM Portal|a través de IBM Portal|Auto-gestión (GUI del proveedor)|Auto-gestión (GUI del proveedor) |
|**Alta disponibilidad**|Integrada|Integrada|Opcional|Opcional|Opcional |
|**LB avanzado (optimización de TCP, compresión, almacenamiento en memoria caché, WAF)**|No|No|No|Limitado|Sí |
|**LB global (GLB)**|No|No|No|No|Sí |
|**Precios**|Basado en uso|Tarifa mensual|Tarifa mensual|Tarifa mensual|Tarifa mensual |
