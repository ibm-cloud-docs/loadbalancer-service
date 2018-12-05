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

# Resolución de problemas del servidor de aplicaciones
En este tema se proporciona información sobre los problemas comunes que puede encontrar cuando utilice el equilibrador de carga.

## El servidor de fondo no está en buen estado
Si el estado del servidor de fondo no es bueno, intente verificar la siguiente lista para intentar solucionarlo:

* ¿El puerto del protocolo de programa de fondo configurado coincide con el puerto en el que está escuchando la aplicación?
* ¿Tiene la comprobación de estado configurada el protocolo (TCP o HTTP), el puerto y la información de URL (para HTTP) correctos? En el caso de HTTP, asegúrese de que la aplicación responde con `200 OK` para el URL de comprobación de estado configurado.
* ¿Está el servidor de fondo en una subred distinta que el equilibrador de carga? Si no es así, asegúrese de que la expansión de VLAN está habilitada.
* ¿Es el servidor de fondo un servidor virtual con un grupo de seguridad habilitado? Si es así, asegúrese de que las reglas del grupo de seguridad permitan el tráfico entre el equilibrador de carga y el servidor virtual.
