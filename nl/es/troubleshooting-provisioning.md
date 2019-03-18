---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Resolución de problemas de suministro de equilibrador de carga
{: #load-balancer-provisioning-troubleshooting}

En este tema se proporciona información sobre los problemas comunes que puede encontrar cuando cree una nueva instancia de IBM© Cloud Load Balancer.

## Direcciones IP insuficientes en la subred
IBM Cloud Load Balancer necesita al menos dos direcciones IP libres en su subred privada. Además, si el equilibrador de carga es un equilibrador de carga público y no se utiliza la opción **Agrupación de sistemas IBM**, también se necesitan al menos dos direcciones IP libres de su subred pública. 

Siga los pasos que se indican a continuación para comprobar si hay IP libres en una subred.

1. Vaya al [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com){:new_window} y vaya a la sección de subredes seleccionado **Red > Gestión de IP > Subredes**.

2. Pulse en la subred en la que desea comprobar si hay IP libres.

	<img src="images/subnet_list.png" alt="dibujo" style="width: 600px;"/>
		
3. La página de detalles de la subred seleccionada muestra el estado de todas las IP de dicha subred.

## Problemas con cortafuegos en las VLAN públicas y privadas
Consulte el tema [Rangos de IP de IBM Cloud](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges) para obtener información sobre cómo permitir rangos de IP a través del cortafuegos.
 
## Visualización de los mensajes de error del equilibrador de carga
Para ver los mensajes de error del equilibrador de carga, siga el siguiente procedimiento:

1. Pulse el equilibrador de carga en la página de lista para ver sus detalles. 
2. Mueva el cursor sobre el símbolo de error que hay junto al estado del equilibrador de carga.

<img src="images/lbaas_error_message.png" alt="dibujo" style="width: 500px;"/>

Si el equilibrador de carga está en un estado `ERROR`, no se puede recuperar y se debe suprimir.
