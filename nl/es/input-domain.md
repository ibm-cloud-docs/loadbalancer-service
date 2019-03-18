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

# Especificar información sobre su dominio
Especifique información sobre el dominio que desea proteger y proporcionarle equilibrio de carga global.

1. Pulse **Visión general** en el lado izquierdo de la pantalla Cómo empezar. Especifique el nombre de dominio (o el nombre de subdominio) y pulse **Añadir dominio**. 
    
    <img src="images/Reliability3.png" alt="drawing" style="width: 300px;"/>
    
    **NOTA:** IBM Cloud Internet Services no es un registrador de DNS, de modo que este dominio (o subdominio) debe haberse creado previamente.

    En la sección Detalles de servicio, observará que el dominio recién añadido se mostrará inicialmente con un estado Pendiente. 

    <img src="images/Reliability4.png" alt="drawing" style="width: 300px;"/>    

2. Vaya a la página de administración del dominio con el registrador de DNS respectivo y delegue el dominio/subdominio a los servidores de nombres de IBM definiendo los registros NS.

Es posible que tenga que esperar hasta 24 horas para que su información se replique en la base de datos de DNS. Una vez lo haga, el estado del dominio cambiará a Activo. 

<img src="images/Reliability5.png" alt="drawing" style="width: 300px;"/>    
