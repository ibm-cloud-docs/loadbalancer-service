---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Tareas básicas de IBM Cloud Load Balancer
{: #performing-ibm-cloud-load-balancer-basics}

El servicio del equilibrador de carga de IBM© Cloud distribuye el tráfico entre varias instancias de servidor (desde el servidor nativo y el servidor virtual) residentes en el sistema local, dentro del mismo centro de datos. 

## Equilibrador de carga pública 
Se asigna un nombre de dominio totalmente calificado y de acceso público a la instancia de servicio del equilibrador de carga. Debe utilizar este nombre de dominio para acceder a las aplicaciones alojadas detrás del servicio del equilibrador de carga. Este nombre de dominio se puede registrar con una o más direcciones IP públicas. Las direcciones IP públicas y el número de direcciones IP públicas puede cambiar con el tiempo, en función de las actividades de mantenimiento y escalado, que son transparentes para los usuarios finales. Las instancias de cálculo de fondo que alojan la aplicación deben estar en una red privada de IBM Cloud. 

Se recomienda, como buena práctica, que se suministren los servidores de fondo solo para uso privado a menos que necesiten conectividad pública directa. Esta práctica mejora la seguridad y protege su dirección IP pública. Las aplicaciones alojadas en estos servidores de fondo siguen siendo accesibles a través de la red pública mediante el uso del equilibrador de carga.
{:note}  

Puede elegir asignar direcciones IP públicas del equilibrador de carga desde una agrupación de sistemas de IBM (predeterminado) o una VLAN pública bajo su cuenta al crear la instancia de servicio del equilibrador de carga.

## Equilibrador de carga interno
El equilibrador de carga interno sólo es accesible dentro de la red privada de IBM Cloud. 

Al igual que un equilibrador de carga público, también se asigna un nombre de dominio completo a la instancia de servicio del equilibrador de carga interno. Sin embargo, este nombre de dominio se registra con una o varias direcciones IP privadas. 

De forma similar a un equilibrador de carga público, las direcciones IP privadas y sus números pueden cambiar con el tiempo en función de las actividades de mantenimiento y de escalado, que son transparentes para los usuarios finales. 

Las instancias de cálculo de fondo que alojan la aplicación también deben estar en la red privada de IBM Cloud.
{:note}

## Puertos/Protocolos de aplicaciones frontales y de fondo
Puede definir hasta diez puertos (protocolos) de aplicación frontal y asignarlos a sus puertos (protocolos) respectivos en los servidores de aplicaciones de fondo. El nombre de dominio totalmente calificado asignado a la instancia de servicio del equilibrador de carga y los puertos de la aplicación frontal están expuestos al mundo exterior. Las solicitudes de usuario entrantes se reciben en estos puertos. 

Por otra parte, los puertos de fondo solo se conocen internamente. Estos puertos de fondo pueden o no ser los mismos que los puertos frontales. Por ejemplo, el equilibrador de carga se puede configurar para recibir tráfico web/HTTP entrante en el puerto 80 frontal mientras los servidores de fondo escuchan en el puerto personalizado 81. 

Los protocolos/puertos frontales soportados son HTTP, HTTPS y TCP. Los protocolos/puertos de fondo admitidos son HTTP, HTTPS y TCP. El tráfico HTTPS entrante debe finalizar en equilibrador de carga para permitir la comunicación HTTP de texto sin formato con el servidor de fondo. Si el protocolo de fondo es HTTPS, se cifrará el tráfico entre el equilibrador de carga y los servidores de fondo.

### Aspectos importantes

* Durante la configuración inicial, solo se pueden definir dos puertos frontales como máximo. Una vez creado el equilibrador de carga, podrá editar la configuración de puerto para definir un máximo de diez puertos adicionales.
* Los diez puertos frontales deben asignarse al mismo conjunto de instancias de servidor de fondo.
* El número máximo de instancias de servidor que se puede colocar tras un equilibrador de carga es de 50.
* El rango de puerto de 56500 a 56520 está reservado para finalidades de gestión y no se puede utilizar como puertos virtuales frontales. 
* El puerto TCP 56501 se utiliza para la gestión. Si elige asignar direcciones IP públicas del equilibrador de carga desde una VLAN pública, asegúrese de que el tráfico a este puerto de gestión, así como los puertos de su aplicación, no estén bloqueados por ningún cortafuegos que haya podido desplegar en sus VLAN públicas. Esto no es obligatorio si elige la opción de agrupación de sistemas de IBM para asignar las direcciones IP públicas del equilibrador de carga.

## Métodos de equilibrio de carga
Los siguientes tres métodos de equilibrio de carga están disponibles para distribuir el tráfico entre los servidores de aplicaciones de fondo:

* **Round Robin:** Round Robin es el método de equilibrio de carga predeterminado. Con este método, el equilibrador de carga reenvía las conexiones entrantes del cliente de forma rotativa a los servidores de fondo. En consecuencia, todos los servidores de fondo reciben aproximadamente el mismo número de conexiones de cliente.

* **Round Robin ponderado:** con este método, el equilibrador de carga reenvía las conexiones entrantes del cliente a los servidores de fondo en proporción al peso asignado a estos servidores. Cada servidor tiene asignado un peso predeterminado de 50, valor que se puede personalizar del 0 al 100. 

	Por ejemplo, si hay tres servidores de aplicaciones A, B y C y se personalizan sus pesos a 60, 60 y 30 respectivamente, entonces los servidores A y B recibirán un número idéntico de conexiones, mientras que el servidor C, la mitad. 


	Si se restablece el peso de un servidor a ‘0’, dejarán de reenviarse conexiones nuevas al servidor en cuestión, pero el tráfico existente seguirá fluyendo mientras esté activo. Al asignar el valor ‘0’ al peso, se puede desactivar un servidor fácilmente y eliminarlo de la rotación de servicio. 
	{:note}
	
	Los valores de peso de servidor solo se aplican cuando se utiliza el método 'round robin ponderado'. Estos valores se omitirán al utilizar los métodos de equilibrio de carga 'round robin' y 'menos conexiones'. 
	{:note}

* **Menos conexiones** con este método, la instancia de servidor que sirve el menor número de conexiones en un momento dado recibe la siguiente conexión de cliente. 


## Escalado horizontal
El equilibrador de carga ajusta su capacidad automáticamente en función de la carga. Cuando esto ocurre, puede cambiar el número de direcciones IP asociadas al nombre DNS del equilibrador de carga.
