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

# Elección de una suite de cifrado preferida para la aplicación HTTPS
{: #choosing-a-preferred-cipher-suite-for-your-https-application}

Algoritmos de cifrado que ayudan a IBM© Cloud Load Balancer a formar conexiones seguras con sus clientes HTTP.

IBM ofrece una suite de cifrados aprobados entre los que puede elegir, para proteger la comunicación entre el equilibrador de carga los clientes.

Puede elegir una suite de cifrado preferida para un equilibrador de carga existente, o designarla cuando cree uno nuevo. 

## Elección de cifrados para un equilibrador de carga existente
Para elegir una configuración de la suite de cifrado para un equilibrador de carga existente, vaya a la pantalla del equilibrador de carga en el portal de clientes y pulse el separador Protocolos.  Si HTTPS no está seleccionado como su protocolo frontal, no verá la lista de suites de cifrado.

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="dibujo" style="width: 700px;"/>
  
Seleccione HTTPS para el protocolo frontal y verá las suites de cifrado disponibles bajo Detalles de equilibrador de carga. 

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="dibujo" style="width: 600px;"/>
  
La tabla de cifrado se puede editar y le permite seleccionar las suites de cifrado deseadas para el reconocimiento SSL. Pulse **Editar**, seleccione los cifrados que desea implementar y pulse **Guardar**.
  
**NOTA:** para obtener una lista de los cifrados admitidos, consulte [Descarga de SSL](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).

## Elección de cifrados al crear un nuevo equilibrador de carga

Para elegir la suite de cifrado al crear un nuevo equilibrador de carga:

1. Siga las instrucciones para [crear un equilibrador de carga](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-an-ibm-cloud-load-balancer#creating-an-ibm-cloud-load-balancer).
  
2. La configuración de la suite de cifrado solo se aplica con el protocolo frontal HTTPS. Cuando llegue a los pasos de configuración de la sección **Añadir protocolo**, seleccione **Protocolo HTTPS**.

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="dibujo" style="width: 500px;"/>
  
3. Ya hay un conjunto predeterminado de cifrados seleccionado en la configuración, pero solo podrá editarlo cuando haya terminado de configurar el equilibrador de carga. 
  
	Finalice la configuración del equilibrador de carga, siguiendo las instrucciones del tema. Cuando termine, verá la lista de cifrados en el separador **Protocolos** bajo **Detalles del equilibrador de carga**.

	<img src="images/View-CustomCiphers.png" alt="dibujo" style="width: 600px;"/>
  
4. La tabla de cifrado se puede editar y le permite seleccionar las suites de cifrado deseadas para el reconocimiento SSL. Pulse **Editar**, seleccione los cifrados que desea implementar y pulse **Guardar**.
	
	**NOTA:** para obtener una lista de los cifrados admitidos, consulte [Descarga de SSL](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).
