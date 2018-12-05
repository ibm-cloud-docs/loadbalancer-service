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
{:faq: data-hd-content-type='faq'}

# Preguntas más frecuentes

Esta sección contiene respuestas a algunas preguntas frecuentes sobre el servicio de equilibrador de carga de IBM Cloud.

## ¿Cuántas opciones de equilibrio de carga hay disponibles en {{site.data.keyword.BluSoftlayer_notm}}?
{:faq}

Para obtener una comparación detallada de las ofertas de equilibradores de carga de IBM, consulte [Explorar los equilibradores de carga](/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers).

## ¿Puedo utilizar un nombre DNS distinto para mi equilibrador de carga?
{:faq}

Aunque el nombre DNS auto-asignado para el equilibrador de carga no es personalizable, puede añadir un registro CNAME (nombre canónico) que apunte a su nombre DNS preferido para el nombre DNS del equilibrador de carga auto-asignado. 

Por ejemplo, si su número de cuenta es 123456, su equilibrador de carga se despliega en el centro de datos `dal09` y su nombre es `myapp`, el nombre DNS del equilibrador de carga autoasignado es `myapp-123456-dal09.lb.bluemix.net`. Su nombre DNS preferido es `www.myapp.com`. Puede añadir un registro CNAME (a través del proveedor de DNS que utilice para gestionar myapp.com) que apunte `www.myapp.com` al nombre DNS del equilibrador de carga myapp-12345-dal09.lb.bluemix.net`.

## ¿Cuál es el número máximo de puertos virtuales que puedo definir con mi servicio de equilibrador de carga?
{:faq}

Al crear un nuevo servicio de equilibrador de carga, puede definir hasta dos puertos virtuales. Puede definir puertos virtuales adicionales después de haber creado el servicio. El número máximo de puertos virtuales permitido es de 10.

## ¿Cuál es el número máximo de instancias de cálculo que puedo asociar con mi equilibrador de carga?
{:faq}

50.

## ¿Pueden mis instancias de cálculo de fondo estar instaladas en una subred distinta de la subred del equilibrador de carga?
{:faq}

Sí, el equilibrador de carga y las instancias de cálculo conectadas al equilibrador de carga pueden estar en subredes diferentes, pero la **expansión de VLAN** debe estar habilitado para que el equilibrador de carga se comunique y reenvíen las solicitudes a la instancia de cálculo. Consulte [Resolución de problemas de expansión de VLAN](troubleshooting-vlan-spanning.html) para obtener más información.

## ¿Cuáles son los valores predeterminados y los permitidos para los distintos parámetros de comprobación de estado?
{:faq}

Los valores predeterminados y los permitidos se enumeran a continuación:

* **Intervalo de comprobación de estado:** el valor predeterminado es de 5 segundos, el rango oscila entre 2 y 60 segundos
* **Tiempo de espera de respuesta de la comprobación de estado:** el valor predeterminado es de 2 segundos, el rango oscila entre 1 y 59 segundos
* **Número máximo de reintentos:** El valor predeterminado es de 2 reintentos y el rango oscila de 1 a 10 reintentos

**NOTA:** el valor de tiempo de espera de la respuesta de comprobación de estado siempre debe ser inferior al valor del intervalo de la comprobación de estado.

## ¿Puedo utilizar instancias de cálculo que residan en centros de datos remotos con este servicio?
{:faq}

Le recomendamos que el servicio de equilibrador de carga y las instancias de cálculo residan localmente en el mismo centro de datos. La interfaz gráfica de usuario (GUI) del servicio de equilibrador de carga no muestra las instancias de cálculo de otros centros de datos remotos. Con todo, la GUI puede incluir instancias de cálculo de otros centros de datos de la misma ciudad (por ejemplo, centros de datos cuyos nombres compartan las tres primeras letras, como DALxx). Se puede utilizar la interfaz de la API para añadir instancias de cálculo desde cualquier centro de datos remoto.

## ¿Qué versión de TLS se soporta con la descarga SSL?
{:faq}

El servicio Cloud Load Balancer soporta TLS 1.2 con terminación de SSL.

En la siguiente lista, se enumeran los cifrados soportados (listados en orden de precedencia):  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## ¿Cuál es el número máximo de instancias de servicio del equilibrador de carga que puedo crear en mi cuenta?
{:faq}

Actualmente, puede crear un máximo de 50 instancias de servicio. Si necesita más instancias, póngase en contacto con el soporte de IBM. 

## ¿Puede utilizarse el servicio de equilibrador de carga de IBM Cloud con VMware?
{:faq}

Las máquinas virtuales VMware que tienen asignadas direcciones privadas portátiles de SoftLayer se pueden especificar como servidores de fondo en el equilibrador de carga. Esta característica actualmente solo está disponible utilizando la API, y no por la interfaz de usuario web (GUI). Las IP privadas portátiles añadidas mediante la API aparecen como "Desconocidas" en la GUI, ya que no han sido asignadas por SoftLayer. Tenga en cuenta que esta clase de configuración se puede utilizar con otros hipervisores, como Xen y KVM.

Las direcciones no SoftLayer asignadas por máquinas virtuales VMware (como con las redes VMware NSX) no se pueden añadir directamente como servidores de fondo al equilibrador de carga. Sin embargo, en función de su configuración, es posible configurar un intermediario, como una pasarela NSX, que tenga una dirección privada de SoftLayer como el servidor de fondo para el equilibrador de carga (con los servidores reales siendo máquinas virtuales conectadas a red(es) gestionadas por VMware NSX).

## Si elijo utilizar una VLAN pública bajo mi cuenta para desplegar mi equilibrador de carga y tengo un cortafuegos desplegado en mi VLAN pública, ¿qué configuraciones requiere mi cortafuegos para que funcione con el servicio de equilibrador de carga?
{:faq}

El puerto TCP 56501 se utiliza para la gestión. Asegúrese de que el tráfico a este puerto, así como los puertos de su aplicación, no estén bloqueados por su cortafuegos, de lo contrario el suministro del equilibrador de carga fallará.

## ¿Qué pasa si no puedo ver las métricas de supervisión de un equilibrador de carga existente después de enlazar mi cuenta de Softlayer con IBM Cloud? 
{:faq}

Las métricas de supervisión no estarán disponibles para los equilibradores de carga existentes después de enlazar las cuentas. Debe volver a crear los equilibradores de carga o ponerse en contacto con el equipo de soporte. Las métricas de supervisión de los equilibradores de carga recién creados estarán disponibles.

## ¿Son fijas las direcciones IP de equilibrador de carga?
{:faq}

No podemos garantizar que las direcciones IP de equilibrador de carga permanezcan constantes debido a la elasticidad que conlleva el servicio. A medida que su capacidad aumenta o se reduce, verá cambios en las IP disponibles asociadas al FQDN de su instancia.

**NOTA:** debe utilizar FQDN y no direcciones IP almacenadas en memoria caché.

## Si tengo un cortafuegos desplegado en mi VLAN pública, ¿qué configuraciones se necesitan para que funcione con el servicio de equilibrador de carga?
{:faq}

Consulte el tema [Rangos de IP de IBM Cloud](/docs/infrastructure/hardware-firewall-dedicated/ips.html#ibm-cloud-ip-ranges) para obtener información sobre cómo permitir rangos de IP a través del cortafuegos.

## ¿Por qué no puedo ver la configuración de capa 7 en la interfaz de usuario?
{:faq}

Actualmente, el soporte de capa 7 solo está disponible a través de API públicas, pero esta funcionalidad estará disponible en la interfaz de usuario pronto. Consulte la sección sobre la capa 7 de la [documentación de las API](apis.html) para obtener más información.

## ¿Qué información necesito para presentar una incidencia de soporte?
{:faq}

Para presentar una incidencia de soporte, proporcione el nombre del producto ("IBM Cloud Load Balancer"), el UUID del equilibrador de carga (si es posible) y el número de su cuenta de Softlayer. Encontrará el UUID en el URL después de ir a la página de visión general del equilibrador de carga determinado.
