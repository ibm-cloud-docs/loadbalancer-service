---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# Iniciación a {{site.data.keyword.loadbalancer_full}}
{: #getting-started}

Para empezar a utilizar {{site.data.keyword.loadbalancer_full}} necesitará dos elementos principales:

* Una cuenta con IBM: [IBMid ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* Un servidor IBM, ya sea [nativo](/docs/bare-metal?topic=bare-metal-about) o [una instancia de servidor virtual (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

Si necesita ayuda para obtener una cuenta de **IBMid**, póngase en contacto con el [representante de ventas de IBM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} para obtener ayuda.

Si tiene una cuenta de IBM Cloud Infrastructure (SoftLayer) existente, puede [enlazar su cuenta](/docs/account?topic=account-unifyingaccounts) a su IBMid.

## Realizar un pedido de un equilibrador de carga
{: #ordering-a-load-balancer}

Para solicitar un servicio {{site.data.keyword.loadbalancer_full}}, seleccione **{{site.data.keyword.loadbalancer_full}}** en el [catálogo de IBM Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window}. A continuación, pulse **Crear** y complete el siguiente procedimiento:

1. Defina los parámetros de servicio básicos, como el nombre y la descripción.
2. Seleccione el centro de datos.
3. Seleccione el tipo de equilibrador de carga **Público**.
4. Seleccione la subred en la que desee desplegar el equilibrador de carga.

  La instancia del servicio de equilibrador de carga tendrá una de las interfaces de red en esta subred. Asegúrese de que los servidores de aplicaciones estén en esta subred o sean accesibles desde la misma. Si es necesario, habilite la expansión de VLAN.
  {: note}

5. Cree protocolos y puertos frontales y de fondo.

  Para obtener más información sobre esta configuración, consulte [Configuración de los parámetros de {{site.data.keyword.loadbalancer_full}}](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters).
  {: note}

6. Para habilitar la descarga SSL, establezca los protocolos frontales en HTTPS y los protocolos de fondo en HTTP. A continuación, seleccione su certificado SSL en el recuadro desplegable Certificado.

  Todos los certificados SSL existentes se gestionan a través del [Almacén de certificados de IBM Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}. Si no tiene un certificado SSL, puede crear uno aquí.

7. Ajuste los parámetros de la comprobación de estado si lo desea; de lo contrario, utilice los valores predeterminados.

  Para obtener más información sobre los parámetros de comprobación de estado, consulte [Parámetros de {{site.data.keyword.loadbalancer_full}}](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks).
  {: note}

8. Pulse **Adjuntar servidor** para asociar una o más instancias de servidor detrás del equilibrador de carga. Solo verá las instancias del servidor local en su centro de datos.
9. Revise la página, confirme el acuerdo de servicio y pulse **Crear**.

Se muestra la lista del equilibrador de carga con todas las instancias de servicio.

Al pulsar el nombre de servicio en la página, irá a la página de visión general del servicio. Puede desplazarse por los separadores **Protocolos**, **Comprobaciones de estado** e **Instancias de servidor** para editar la configuración.

Puede que el equilibrador de carga que acaba de crear no se muestre inmediatamente en esta lista. Al cabo de unos pocos minutos, se visualizará el nuevo equilibrador de carga de color gris, que indica que está en estado `Offline`. Después de otros pocos minutos, el nuevo equilibrador de carga estará de color verde, que indica que está `Online`. Puede que tenga que renovar la pantalla para ver estos cambios.
{: note}

Consulte [Cómo utilizar un {{site.data.keyword.loadbalancer_full}} para el equilibrio de carga elástico del servidor](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing) para obtener instrucciones paso a paso para configurar el nuevo Cloud Load Balancer.
