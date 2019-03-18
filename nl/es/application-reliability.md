---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Mejora de la fiabilidad y la escalabilidad de las aplicaciones con el Equilibrio de carga global de IBM Cloud Internet Services
Si tiene un sitio web de comercio electrónico o aloja una aplicación que necesita ser accesible para los usuarios finales en todo momento, es probable que le preocupe la disponibilidad 24/7 y el rendimiento de su aplicación. 

Las funciones globales de equilibrio de carga disponibles con IBM Cloud Internet Services (CIS) pueden ayudar a mejorar la fiabilidad y la escalabilidad de las aplicaciones a la vez que ofrecen la mejor experiencia de usuario final posible. Esta guía proporciona una guía paso a paso de la configuración de equilibrio de carga global.  

## Lo que va a lograr

En esta guía paso a paso, aprenderá a configurar una configuración similar a la que se muestra a continuación.

<img src="images/Reliability1.png" alt="drawing" style="width: 300px;"/>

En este ejemplo, los recursos de aplicación se despliegan en dos ubicaciones de centro de datos, una en el Oeste de EE. UU. y otra en la Costa Este de EE.UU. Es posible que los usuarios finales estén accediendo a esta aplicación desde todo el mundo. 

Tarea  | Descripción
------------- | -------------
[Crear una instancia de CIS](create-cis.html) | Empiece por crear la instancia de IBM Cloud Internet Services (CIS) utilizando el Portal
de clientes de IBM.
[Especificar información sobre su dominio](input-domain.html) | Especifique información sobre el dominio que desea proteger y proporcionarle equilibrio de carga global.
[Iniciar la configuración del equilibrador de carga global](begin-config.html) | Empiece a configurar el equilibrador de carga global.
[Identificar los recursos de la aplicación](identify-app-resources.html) | Identifique los recursos de la aplicación, como las agrupaciones de origen y los mecanismos de comprobación de estado.
[Definir el equilibrador de carga global](define-global-lb.html) | Defina la configuración del equilibrador de carga global especificando un nombre de host, añadiendo y ajustando las agrupaciones de origen y definiendo reglas adicionales para controlar cómo se sirve el tráfico a los clientes.
