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


# Iniciación a IBM Cloud Load Balancer
{: #getting-started-with-ibm-cloud-load-balancer}

Para empezar a utilizar IBM© Cloud Load Balancer necesitará dos elementos principales:

* Una cuenta con IBM: [IBMid ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* Un servidor IBM, ya sea [nativo](/docs/bare-metal?topic=bare-metal-about) o [una instancia de servidor virtual (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

Si necesita ayuda para obtener una cuenta de **IBMid**, póngase en contacto con el [representante de ventas de IBM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} para obtener ayuda.

Si tiene una cuenta de IBM Cloud Infrastructure (SoftLayer) existente, puede [enlazar su cuenta](/docs/account?topic=account-unifyingaccounts) a su IBMid.

## Realizar un pedido de un equilibrador de carga

Para solicitar un servicio IBM Cloud Load Balancer, seleccione **Red > Equilibradores de carga > IBM Cloud Load Balancer**
en el [catálogo de IBM Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/infrastructure/load-balancer-group){:new_window}. Inicie la sesión o cree una cuenta nueva y, a continuación, realice el procedimiento siguiente:

1. Seleccione el centro de datos y revise el plan de servicio. Pulse **Siguiente**.
2. Seleccione la subred en la que desee desplegar el equilibrador de carga. La instancia del servicio de equilibrador de carga tendrá una de las interfaces de red en esta subred. Asegúrese de que los servidores de aplicaciones estén en esta subred o sean accesibles desde la misma. Si es necesario, habilite la expansión de VLAN. Pulse **Siguiente**.
3. Defina los parámetros de servicio básicos, como nombre, descripción, protocolos y puertos de aplicación frontal y back-end y método de equilibrio de carga.

	Puede definir un máximo de dos protocolos durante la creación inicial del servicio. Puede definir hasta diez protocolos después de haber creado el servicio. Además debe utilizar un puerto frontal exclusivo.

	Cuando termine, pulse **Siguiente**.

4. Ajuste los parámetros de la comprobación de estado si lo desea; de lo contrario, utilice los valores predeterminados. Pulse **Siguiente**.
5. Asocie una o más instancias de servidor detrás del equilibrador de carga. Solo verá las instancias del servidor local en su centro de datos. Pulse **Siguiente**.
6. Revise la página de resumen y luego pulse **Crear**.

	La página de resumen muestra la instancia del servicio de equilibrador de carga que se acaba de crear. Observe el campo **Estado**. El estado `Offline` significa que el equilibrador de carga no está en servicio. No se pueden crear configuraciones ni se puede proporcionar servicio de equilibrio de carga hasta que el estado cambie a `Online`. Puede que tenga que actualizar la pantalla para ver el estado actual.

	Al pulsar el nombre de servicio en la página, irá a la página de visión general del servicio. Puede desplazarse por los separadores **Protocolos**, **Comprobaciones de estado** e **Instancias de servidor** para editar la configuración.

Consulte [Cómo crear y utilizar IBM Cloud Load Balancer para el equilibrio de carga elástico del servidor](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing) para ver instrucciones de configuración paso a paso.
