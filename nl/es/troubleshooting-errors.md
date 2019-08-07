---

copyright:
  years: 2018
lastupdated: "2018-11-21"

keywords: error, message, troubleshooting, problems

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Resolución de problemas de mensajes de error
{: #error-message-troubleshooting}

En este tema se proporciona información sobre los mensajes de error comunes que puede encontrar cuando cree o actualice una instancia de {{site.data.keyword.loadbalancer_full}}.

| Error | Explicación  | Solución  |
| ------------- | ------------- | ----- |
| `Se ha alcanzado el número máximo de equilibradores de carga `n`.`| Solo permitimos 50 instancias de equilibrador de carga por cuenta. | Asegúrese de que tiene 50 instancias o menos de equilibrador de carga por cuenta. |
| `Se ha alcanzado el número máximo de protocolos dados `n` en la solicitud del producto equilibrador de carga.` | Solo se pueden añadir dos protocolos al suministrar un equilibrador de carga.  | Si necesita más protocolos, después del suministro puede añadir un máximo de diez desde el separador **Protocolos** del flujo de gestión del equilibrador de carga. Para obtener más información, consulte el apartado sobre [supervisión y gestión del servicio](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `Se ha alcanzado el número máximo de instancias del servidor `n` en la solicitud del producto equilibrador de carga.` | Solo se pueden añadir diez servidores al suministrar un equilibrador de carga. | Si necesita más servidores, después del suministro puede añadir un máximo de 50 desde el separador **Instancias de servidor** del flujo de gestión del equilibrador de carga. Para obtener más información, consulte el apartado sobre [supervisión y gestión del servicio](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service). |
| `El nombre del equilibrador de carga debe ser una serie y debe tener al menos 1 y un máximo de 40 caracteres.` | El nombre del equilibrador de carga es obligatorio. Utilice solo caracteres alfanuméricos (o los caracteres especiales '-' y '.') para el nombre. El nombre no puede empezar o terminar con un carácter especial y su longitud debe limitarse a 40 caracteres. | Especifique un nombre de equilibrador de carga exclusivo. Por ejemplo, "ui-servers" o "backend-servers".|
| `Se ha encontrado un error de formato en el nombre del equilibrador de carga determinado.` | El nombre del equilibrador de carga es obligatorio. Utilice solo caracteres alfanuméricos (o los caracteres especiales '-' y '.') para el nombre. El nombre no puede empezar o terminar con un carácter especial y su longitud debe limitarse a 40 caracteres. | Especifique un nombre de equilibrador de carga exclusivo. Por ejemplo, "ui-servers" o "backend-servers".|
| `Ya existe un equilibrador de carga con el mismo nombre (no distingue entre mayúsculas y minúsculas).` | Ya existe un equilibrador de carga con este nombre. | Especifique un nombre de equilibrador de carga exclusivo para continuar, como por ejemplo "ui-servers" o "backend-servers". |
| `La descripción del equilibrador de carga debe ser una serie y no puede tener más de 255 caracteres.` | La descripción del equilibrador de carga debe ser una serie y no puede tener más de 255 caracteres. | Limite la descripción a 255 caracteres. |
| `El puerto frontal 80 ya se está utilizando.` | Es posible que haya especificado un puerto frontal que ya se esté utilizando. | Especifique un puerto frontal exclusivo. |
| `El puerto de fondo debe ser un entero.` | Es posible que haya especificado un valor de puerto de fondo no válido. | Especifique un número de puerto de fondo comprendido entre 1 y 65535. |
| `Puesto que el protocolo y el puerto no se pueden editar en el supervisor de estado, este error no se puede solucionar desde la interfaz de usuario.`| Su subred privada no es de tipo estándar y no se puede utilizar para crear el equilibrador de carga. | Póngase en contacto con el servicio de soporte técnico de IBM. |
| `La subred privada `xyz` debe tener como mínimo `n` direcciones IP libres.` | La subred privada seleccionada no tiene ninguna dirección IP libre. | Consulte estos [pasos de resolución de problemas](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting) para obtener más información. |
| `La VLAN de subred privada especificada está en el direccionador `xyz`. Sin embargo, no se ha encontrado ninguna VLAN pública con `n` IP libres en el mismo direccionador.` | Esto ocurre porque ha seleccionado la opción **Asignar desde una subred pública de esta cuenta** durante el suministro. | Seleccione **Asignar desde la agrupación del sistema IBM** o póngase en contacto con el servicio de soporte técnico de IBM.|
| `La VLAN de subred privada especificada está en el direccionador `xyz`. Sin embargo, no se ha encontrado ninguna subred pública
con `n` IP libres con VLAN en el mismo direccionador.` | Esto ocurre porque ha seleccionado la opción **Asignar desde una subred pública de esta cuenta** durante el suministro. | Seleccione **Asignar desde la agrupación del sistema IBM** o póngase en contacto con el servicio de soporte técnico de IBM.|
| `La nueva descripción debe ser una serie.`| Es posible que haya especificado una descripción no válida. | Especifique una descripción de equilibrador de carga válida que no supere los 255 caracteres. |
| `Se necesita un elemento de facturación para procesar una cancelación para el equilibrador de carga uuid=aaaa-bbbb-cccc-dddd.` | Falta información de facturación o no es válida para la cuenta y no se puede cancelar el equilibrador de carga. | Póngase en contacto con el servicio de soporte técnico de IBM.|
| `Se ha producido un error interno. No se han podido recuperar los datos.` | No se pueden recuperar los datos de métricas | Vuelva a cargar la página. Si el problema continúa, póngase en contacto con el servicio de soporte de IBM. |
| `El puerto frontal debe ser un entero comprendido entre 1 y 65535, sin incluir el rango 56500-56520.` | Es posible que haya especificado un número puerto frontal comprendido entre 56500 y 56520. | Especifique un número de puerto exclusivo comprendido entre 1 y 65535, pero sin incluir el rango comprendido entre 56500 y 56520. |
| `El puerto de fondo debe ser un entero.` | Es posible que haya especificado un valor de puerto de fondo no válido. | Especifique un número de puerto de fondo comprendido entre 1 y 65535. |
| `El puerto de fondo debe ser un entero comprendido entre 1 y 65535, sin incluir el rango 56500-56520.` | Es posible que haya especificado un puerto de fondo comprendido entre 56500 y 56520.| Especifique un número de puerto de fondo comprendido entre 1 y 65535, pero sin incluir el rango comprendido entre 56500 y 56520. |
| `El protocolo de fondo HTTP no es compatible con el protocolo TCP del protocolo frontal.` | Es posible que haya seleccionado una combinación de protocolo de fondo y protocolo frontal incompatible. | Seleccione una combinación válida de protocolo de componente frontal y de fondo con el siguiente formato: `<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `Se ha proporcionado la ponderación de miembro <some value> para el miembro abcd-xxxx-yyyy-2222. Los valores de ponderación permitidos son los comprendidos entre 0 y 100 `| Es posible que haya especificado una ponderación no válida. | Especifique un valor de ponderación comprendido entre 0 y 100. |
| `Se ha producido un problema al captar los servidores.` | Esto puede deberse a problemas de tiempo de espera excedido en la red. | Vuelva a cargar la página. Si el problema continúa, póngase en contacto con el servicio de soporte de IBM.|
