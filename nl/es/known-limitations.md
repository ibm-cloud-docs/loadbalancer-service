---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: limitations, problems, troubleshooting

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

# Problemas conocidos y limitaciones de {{site.data.keyword.loadbalancer_full}}
{: #known-issues-and-limitations-with-ibm-cloud-load-balancer}

Este tema contiene información sobre los problemas conocidos y las limitaciones actuales del servicio {{site.data.keyword.loadbalancer_full}}.

## Problemas conocidos
{: #known-issues}
El servicio {{site.data.keyword.loadbalancer_full}} presenta los siguientes problemas en estos momentos:

* Menor - El botón **Editar** en los separadores de las instancias de servidor y protocolos se aplica a todas las entradas y no se puede limitar a las filas seleccionadas utilizando un recuadro de selección.
* Menor - Durante la creación inicial del servicio del equilibrador de carga, la configuración de la comprobación de estado personalizada se pierde si se avanza y se retrocede entre pantallas.
* Menor - Es posible que se produzcan problemas al utilizar los exploradores Internet Explorer 11, Edge o Safari para administrar el servicio del equilibrador de carga. Como alternativa, utilice el explorador Firefox o Chrome.
* Cosmético - Durante la creación del servicio inicial, la lista desplegable de los centros de datos puede aparecer desviada. Pese a ello, es posible seleccionar el centro de datos deseado.
* Cosmético - La información sobre precios de la página de revisión se redondea con dos cifras decimales. Para corregir el precio, consulte el precio que se muestra en la página del plan.

## Limitaciones conocidas
{: #known-limits}
El servicio {{site.data.keyword.loadbalancer_full}} presenta las siguientes limitaciones en estos momentos:

* Número máximo de puertos/protocolos virtuales: 10
* Número máximo de servidores detrás del equilibrador de carga: 50
