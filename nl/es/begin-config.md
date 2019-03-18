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

# Iniciar la configuración del equilibrador de carga global
Empiece a configurar el equilibrador de carga global.

1. En la sección **Fiabilidad**, seleccione **Equilibrador de carga global**. 
    
    <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>

2. Desplácese a la sección Comprobaciones de estado. 

   **NOTA:** Esta configuración es opcional. Si no define ninguna comprobación de estado personalizada, el sistema utilizará "/" como la vía de acceso de comprobación de estado predeterminada. 

3. Pulse el botón **Crear comprobación de estado** para definir una comprobación de estado personalizada.   

   Proporcione la vía de acceso en la que desea realizar las comprobaciones de estado. Puede utilizar protocolos HTTP o HTTPS para las comprobaciones de estado. 
   
4. En **Opciones avanzadas**, puede personalizar otros parámetros como, por ejemplo, el intervalo de comprobación de estado, el número de reintentos, el método de solicitud y el cuerpo de respuesta. 
   
   <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>
   
5. Pulse **Suministro de recursos** para completar la configuración de la comprobación de estado. 
