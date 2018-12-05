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

# Crear un IBM Cloud Load Balancer
Para crear un servicio IBM Cloud Load Balancer, siga el siguiente procedimiento:

1. En el navegador, abra el [Portal de clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://control.softlayer.com/){: new_window} e inicie sesión en su cuenta.

2. Pulse **Catálogo** y, desde la sección Infraestructura, vaya a **Red > Equilibradores de carga**.

	<img src="images/catalog-load-balancer.png" alt="dibujo" style="width: 600px;"/>

3. Seleccione el **IBM Cloud Load Balancer** (selección predeterminada) y pulse **Crear**. 

	Si ve **Actualizar** en lugar de **Crear**, tiene que enlazar con su cuenta de la infraestructura de IBM Cloud (Softlayer) siguiendo [estos pasos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/account/softlayerlink.html#link_customer_accounts)

	<img src="images/create-load-balancer.png" alt="dibujo" style="width: 600px;"/>

4. Seleccione el centro de datos que desee en el menú desplegable **Centro de datos**, revise la información y luego pulse **Siguiente**.

	<img src="images/select-datacenter.png" alt="dibujo" style="width: 600px;"/>

5. Especifique el tipo de equilibrador de carga.

	Para las aplicaciones de cara a Internet que necesitan acceso a la Internet pública, seleccione **Público (conectado a internet)**.

	<img src="images/select-lb-type.png" alt="dibujo" style="width: 600px;"/>
	
	De forma predeterminada, el equilibrador de carga público recibe una dirección IP pública exclusiva global de la agrupación de direcciones globales de IBM. Sin embargo, si desea asignar direcciones públicas de su propia agrupación de direcciones o desea desplegarlo detrás de un servicio de cortafuegos dentro de su cuenta, compruebe si su subred pública tiene [suficientes direcciones IP](troubleshooting-provisioning.html) y seleccione **Asignar desde una subred pública en la cuenta**.

	Solo para las aplicaciones internas que no necesitan acceso a Internet público, seleccione el tipo **Interno (privado)**.

	<img src="images/lb-type-private.png" alt="dibujo" style="width: 500px;"/>

	Tanto para el tipo de equilibrador conectado a Internet como para el interno, elija una de las subredes privadas de la cuenta en la que desea desplegar el equilibrador de carga. Los servidores de aplicaciones deben ser accesibles desde esta subred. Si es necesario, habilite la expansión de VLAN para garantizar una conectividad de red adecuada.

	Si no ve ninguna subred privada, pulse **Anterior** y luego seleccione otro centro de datos con subredes privadas.

6. Pulse **Siguiente** para finalizar la configuración.

## A continuación
Configure el equilibrador de carga con [parámetros básicos](begin-lb-config.html).
