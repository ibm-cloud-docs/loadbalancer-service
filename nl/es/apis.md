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

# Referencia de API
La API de SoftLayer® es la interfaz de desarrollo que permite a los desarrolladores y administradores del sistema interactuar directamente con el sistema de fondo de SoftLayer. 
{:shortdesc}

La API de SoftLayer (SLAPI) ofrece muchas de las características del Portal de clientes. Por lo general, si una interacción es posible en el Portal de clientes, también lo es en la API. Por lo tanto, puesto que se puede interactuar mediante programación con todos los componentes del entorno de SoftLayer dentro de la API, es posible utilizar la API para automatizar tareas.

La API de SoftLayer (SLAPI) es un sistema de llamadas de procedimiento remoto. Cada llamada implica el envío de datos a un punto final de API y la recepción de datos estructurados. El formato utilizado para enviar y recibir datos con la SLAPI depende de qué implementación de la API utilice. Actualmente la SLAPI utiliza SOAP, XML-RPC o REST para la transmisión de datos. 

Para obtener más información sobre la API SoftLayer, las API del servicio IBM Cloud Load Balancer, consulte los siguientes recursos en la red de despliegue de SoftLayer:
* [Iniciación a la API de SoftLayer ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/article/getting-started){: new_window}
* [SoftLayer_Product_Package API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Product_Package){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_LoadBalancer){: new_window}
* [SoftLayer_Network_LBaaS_Listener API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Listener){: new_window}
* [SoftLayer_Network_LBaaS_Member API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Member){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_HealthMonitor){: new_window}
* [API SoftLayer_Network_LBaaS_SSLCipher ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_SSLCipher){: new_window}
* [API SoftLayer_Network_LBaaS_L7Policy ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Policy){: new_window}
* [API SoftLayer_Network_LBaaS_L7Rule ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Rule){: new_window}
* [API SoftLayer_Network_LBaaS_L7Pool ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Pool){: new_window}
* [API SoftLayer_Network_LBaaS_L7Member ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Member){: new_window}

Los siguientes ejemplos utilizan Python con el cliente zeep SOAP.

## Creación de un equilibrador de carga
### Recuperación del ID de paquete de producto y del precio del artículo
```
from zeep import Client, xsd
import sys

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL for SoftLayer_Product_Package API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Package?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

lbaasPackage = None
result = client.service.getAllObjects(_soapheaders=[userAuthValue])
productPackages = result['body']['getAllObjectsReturn']
for package in productPackages:
    if package.name == 'Load Balancer As A Service (LBaaS)':
        lbaasPackage = package
        print 'LBaaS product package id: %s' % lbaasPackage.id
        break

if lbaasPackage is None:
    print 'LBaaS product package cannot be found!'
    sys.exit()

xsdObjectInitPar = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_Product_PackageInitParameters',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}id', xsd.String())
    ])
)

objectInitParValue = xsdObjectInitPar(id=lbaasPackage.id)
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

objectMaskValue = xsdObjectMask(mask='mask[id;item.description]')

result = client.service.getItemPrices(_soapheaders=[userAuthValue,objectInitParValue,objectMaskValue])
itemPrices = result['body']['getItemPricesReturn']
for itemPrice in itemPrices:
    if itemPrice.locationGroupId is None:
        print 'Item Price Id: %s' % itemPrice.id
```
{: codeblock}

### Verificación del orden del equilibrador de carga
```
desde el cliente zeep import, xsd
desde zeep.exceptions import Fault

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# Private subnet id
privateSubnetId = '<Your subnet id>'

# Order details
# Package id retrieved from SoftLayer_Product_Package API
# (example provided above)
lbaasPackageId = 805
# ItemPrice id retrieved from SoftLayer_Product_Package API
# (example provided above)
lbaasItemPrices = [{'id':199447}, {'id':199467}, {'id':205839}, {'id':205907}]
name = 'MyLoadBalancer'
subnets = [{'id': privateSubnetId}]
protocolConfigurations = [{
    'frontendProtocol':'HTTP',
    'frontendPort':80,
    'backendProtocol':'HTTP',
    'backendPort':8080,
    'loadBalancingMethod':'ROUNDROBIN',
    'maxConn':1000
}]

# WSDL for SoftLayer_Product_Order API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Required since LBaaS is an hourly service
    useSystemPublicIpPool=True, # Optional - Default is "True" to allocate load balancer public IPs
                                # from an IBM system pool, otherwise "False" from the public VLAN
                                # under your account. useSystemPublicIpPool is only applicable to
                                # public load balancers
    isPublic=True               # Optional - Default is "True" to create a public load balancer.
                                # isPublic distinguishes between public ("True") and
                                # internal ("False") load balanacer
)

# Make SLAPI call to SoftLayer_Product_Order::verifyOrder API
try:
    result = client.service.verifyOrder(
        _soapheaders=[userAuthValue],
        orderData=orderDataValue
    )   

    print 'The order is valid!'

except Fault as exp:
    print 'The order is INVALID!\r\n>>> %s' % exp
```
{: codeblock}

### Colocación del orden del equilibrador de carga
```
desde el cliente zeep import, xsd
desde zeep.exceptions import Fault

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apikey>'
# Private subnet id
privateSubnetId = '<Your subnet id>'

# Order details
# Package id retrieved from SoftLayer_Product_Package API
# (example provided above)
lbaasPackageId = 805 
# ItemPrice id retrieved from SoftLayer_Product_Package API
# (example provided above)
lbaasItemPrices = [{'id':199447}, {'id':199467}, {'id':205839}, {'id':205907}]
name = 'MyLoadBalancer'
subnets = [{'id': privateSubnetId}]
protocolConfigurations = [{
    'frontendProtocol':'HTTP',
    'frontendPort':80,
    'backendProtocol':'HTTP',
    'backendPort':8080,
    'loadBalancingMethod':'ROUNDROBIN',
    'maxConn':1000
}]

# WSDL for SoftLayer_Product_Order API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Required since LBaaS is an hourly service
    useSystemPublicIpPool=True, # Optional - Default is "True" to allocate load balancer public IPs
                                # from an IBM system pool, otherwise "False" from the public VLAN
                                # under your account. useSystemPublicIpPool is only applicable to
                                # public load balancers
    isPublic=True               # Optional - Default is "True" to create a public load balancer.
                                # isPublic distinguishes between public ("True") and
                                # internal ("False") load balanacer
)

# Make SLAPI call to SoftLayer_Product_Order::placeOrder API
try:
    result = client.service.placeOrder(
        _soapheaders=[userAuthValue],
        orderData=orderDataValue,
        saveAsQuote=False
    )   

    print 'Order has been accepted.'

except Fault as exp:
    print 'Place order failed:\r\n>>> %s' % exp
```
{: codeblock}

## Recuperación de detalles en equilibradores de carga
### Lista de todos los equilibradores de carga
```
desde el cliente zeep import

# Username and apikey SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# Prepare auth for SOAP header
userauth = {'authenticate': {'username': username, 'apiKey': apiKey}}

# Retrieve all load balancer objects
result = client.service.getAllObjects(_soapheaders=userauth)
loadbalancers = result['body']['getAllObjectsReturn']
for loadbalancer in loadbalancers:
    print 'UUID: %s' % loadbalancer.uuid
    print 'Name: %s' % loadbalancer.name
    print 'Address: %s' % loadbalancer.address
    print 'OperatingStatus: %s' % loadbalancer.operatingStatus
    print 'ProvisioningStatus: %s\r\n' % loadbalancer.provisioningStatus
```
{: codeblock}

### Recuperación de detalles de un equilibrador de carga específico
```
desde el cliente zeep import, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of the load balancer
uuid = '<Your load balancer uuid>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners, healthMonitors]')

# Retrieve a specific load balancer object (with objectMask to retrieve "listeners")
loadbalancer = client.service.getLoadBalancer(_soapheaders=[userAuthValue,objectMaskValue], uuid=uuid)
print 'Name: %s' % loadbalancer.name
print 'Address: %s' % loadbalancer.address
print 'OperatingStatus: %s' % loadbalancer.operatingStatus
print 'ProvisioningStatus: %s' % loadbalancer.provisioningStatus
print 'Listeners: %s' % loadbalancer.listeners
print 'HealthMonitors: %s\r\n' % loadbalancer.healthMonitors
```
{: codeblock}

## Actualización de un equilibrador de carga
### Adición de un miembro
```
desde el cliente zeep import, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apikey>'
# UUID of load balancer to be updated
uuid = '<Your load balancer uuid>'
# Backend servers to be added
serverInstances = [ 
    {
        'privateIpAddress': '10.121.220.141', #update with the correct IP
        'weight': 80 #weight is only applicable to Weight Round Robin listeners
    },  
    {
        'privateIpAddress': '10.121.220.142'  #update with the correct IP
        # use default weight
    }   
]

# WSDL for SoftLayer_Network_LBaaS_Member API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Member?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[members]')

# Make SLAPI call to SoftLayer_Network_LBaaS_Member::addLoadBalancerMember API
result = client.service.addLoadBalancerMembers(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, serverInstances=serverInstances
)
print result
```
{: codeblock}

### Adición de un protocolo
```
desde el cliente zeep import, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of load balancer
uuid = '<Your load balancer UUID>'
# New protocol to add
protocolConfigurations = [ 
    {   
        'frontendProtocol': 'TCP',
        'frontendPort': 90, 
        'backendProtocol': 'TCP',
        'backendPort': 9090,
        'loadBalancingMethod': 'WEIGHTED_RR',
        'maxConn': 2000
    }   
]

# WSDL for SoftLayer_Network_LBaaS_Listener API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Listener?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners]')

# Make SLAPI call to SoftLayer_Network_LBaaS_Listener::updateLoadBalancerProtocols API
result = client.service.updateLoadBalancerProtocols(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, protocolConfigurations=protocolConfigurations
)
listeners = result['listeners']
print listeners
```
{: codeblock}

## Cancelación de un equilibrador de carga
```
desde el cliente zeep import, xsd
desde zeep.exceptions import Fault

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of the load balancer to be cancelled
uuid = '<Your load balancer uuid>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_LoadBalancer::cancelLoadBalancer API
try:
    result = client.service.cancelLoadBalancer(
        _soapheaders=[userAuthValue],
        uuid=uuid
    )   

    if True:
        print 'The cancellation request is accepted.'

except Fault as exp:
    print 'Failed to cancel load balancer:\r\n>>> %s' % exp
```
{: codeblock}

## Visualización de la supervisión de métricas de equilibradores de carga
### Obtención del rendimiento del tráfico HTTP
```
desde el cliente zeep import

# Username and apikey SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of load balancer
uuid = '<Your load balancer UUID>'
# The name of the metric. 
# Options are Throughput, ActiveConnections, and ConnectionRate
nameOfMetric = 'Throughput'
# The time interval over which the metric is to be measured
# Options are 1hour, 6hours, 12hours, 24hour, 1week, and 2weeks
timeInterval = '1hour' 
# UUID of the protocol whose throughput your requesting
protocolUuid = '<UUID of the protocol>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Retrieve throughput of hhtp traffic for a specific load balancer object
timeSeriesDataValues = client.service.getListenerTimeSeriesData(
        _soapheaders=[userAuthValue],
        loadBalancerUuid=uuid,
        metricName=nameOfMetric,
        timeRange=timeInterval,
        listenerUuid=protocolUuid
)
for timeSeriesDataValue in timeSeriesDataValues:
    print 'EpochTimeStamp: %d' % timeSeriesDataValue.epochTimestamp
    print 'Value: %f' % timeSeriesDataValue.value
```
{: codeblock}

### Obtención del rendimiento de un equilibrador de carga
```
desde el cliente zeep import, xsd 

# Username and apikey SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of load balancer
uuid = '<Your load balancer UUID>'
# The name of the metric. 
# Options are Throughput, ActiveConnections, and ConnectionRate
nameOfMetric = 'Throughput'
# The time interval over which the metric is to be measured
# Options are 1hour, 6hours, 12hours, 24hour, 1week, and 2weeks
timeInterval = '6hours' 
# If no protocol is specified the throughput of all protocols is returned.
# protocolUuid = '<UUID of the protocol>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Retrieve throughput of hhtp traffic for a specific load balancer object
timeSeriesDataValues = client.service.getListenerTimeSeriesData(
        _soapheaders=[userAuthValue],
        loadBalancerUuid=uuid,
        metricName=nameOfMetric,
        timeRange=timeInterval
)
for timeSeriesDataValue in timeSeriesDataValues:
    print 'EpochTimeStamp: %d' % timeSeriesDataValue.epochTimestamp
    print 'Value: %f' % timeSeriesDataValue.value
```
{: codeblock}

## API de capa 7

### Creación de varias políticas L7 y reglas L7
```
desde el cliente zeep import, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of listener
uuid = '<Your listener UUID>'

# WSDL for SoftLayer_Network_LBaaS_L7Policy API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Policy?wsdl'
client = Client(wsdl)

factory = client.type_factory('ns0')
l7Rule1 = factory.SoftLayer_Network_LBaaS_L7Rule(type = "HEADER", comparisonType = "EQUAL_TO", key = "headerkey", value = "header_key3", invert = 0)
l7Rule2 = factory.SoftLayer_Network_LBaaS_L7Rule(type = "PATH", comparisonType = "STARTS_WITH", value = "/secret_key", invert = 0)
l7RuleArray1 = factory.SoftLayer_Network_LBaaS_L7RuleArray([l7Rule1, l7Rule2])

# Bulk policies and rules configuration
policiesRulesConfiguration = [
   {"l7Policy":
        {
            "name": "traf_test1",
            "action": "REDIRECT_URL",
            "priority":101,
            "redirectUrl": "http://example.com"
        },
     "l7Rules": l7RuleArray1
    }
]

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Policy::addL7Policies API
result = client.service.addL7Policies(
    _soapheaders=[userAuthValue],
    listenerUuid=uuid, policiesRules=policiesRulesConfiguration
)
print result
```
{: codeblock}

### Actualización de la política de capa 7
```
desde el cliente zeep import, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL for SoftLayer_Network_LBaaS_L7Policy API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Policy?wsdl'
client = Client(wsdl)

# Update policy configuration by specifying the variable name and value
policyConfiguration =  {"<name>": "<value>"}

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD for L7Policy Init Parameters
xsdObjectIdElem = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_Network_LBaaS_L7PolicyInitParameters',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}id', xsd.Int())
    ])
)

# Pass the id of the policy object
xsdObjectId = xsdObjectIdElem(<id>)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Policy::addL7Policies API
result = client.service.editObject(
    _soapheaders=[userAuthValue, xsdObjectId],
    templateObject=policyConfiguration
)
print result
```
{: codeblock}

### Adición de reglas a la política de capa 7 
```
desde el cliente zeep import, xsd

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of the Layer 7 policy
policyUuid = '<UUID of the L7 policy to which the rules being created are to be attached>'
# New rules to add
ruleConfigurations = [
   {  
       "type": "FILE_TYPE",
       "comparisonType": "CONTAINS",
       "value": "some_value",
       "invert": 1
   },  
   {  
            "type": "PATH",
            "comparisonType": "EQUAL_TO",
            "value": "some_value",
            "invert": 0
   } 
]

# WSDL for SoftLayer_Network_LBaaS_L7Rule API
wsdl = "https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Rule?wsdl"
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
   "{http://api.softlayer.com/soap/v3/}authenticate",
   xsd.ComplexType([
       xsd.Element("{http://api.softlayer.com/soap/v3/}username", xsd.String()),
       xsd.Element("{http://api.softlayer.com/soap/v3/}apiKey", xsd.String())
   ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Rule::addL7Rules API
try:
   result = client.service.addL7Rules(_soapheaders=[userAuthValue],
   policyUuid=policyUuid, rules=ruleConfigurations
   )
except Exception as e:
   print "Encountered exception: ", str(e)
   exit()

print result
```
{: codeblock}

### Actualización de varias reglas de capa 7 adjuntas a la misma política de capa 7 
```
desde el cliente zeep import, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of the Layer 7 policy
policyUuid = '<UUID of the L7 policy to which the rules being updated are attached to>'
# Rules to update
ruleConfigurations = [ 
    {   
        'uuid':'<UUID of the L7 Rule being updated>',
        'type': 'FILE_TYPE',
        'comparisonType': 'CONTAINS',
        'value': 'some_newvalue',
        'invert': 1
    },  
    {   
        'uuid':'<UUID of the L7 Rule being updated>',
        'type': 'PATH',
        'comparisonType': 'EQUAL_TO',
        'value': 'some_newvalue2',
        'invert': 0
    } 
]

# WSDL for SoftLayer_Network_LBaaS_L7Rule API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Rule?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Rule::updateL7Rules API
result = client.service.updateL7Rules(
    _soapheaders=[userAuthValue],
    policyUuid=policyUuid, rules=ruleConfigurations
)
print result
```
{: codeblock}

### Creación de una agrupación de capa 7 con servidores, supervisión de estado y afinidad de sesiones
```
desde el cliente zeep import, xsd

# Username and apikey for SLAPI call
username = ''
apiKey = ''
# UUID of load balancer to be updated
uuid = 'a3e466e0-5cc3-4efb-bb56-07ad63988b16'

# Layer 7 pool to be added
l7Pool = {
    'name': 'image_pool',
    'protocol': 'HTTP',  # only supports HTTP
    'loadBalancingAlgorithm': 'ROUNDROBIN'
}

# Layer 7 Backend servers to be added
l7Members = [
    {
        'address': '10.73.67.83',
        'port': 80,
        'weight': 10
    },
    {
        'address': '10.73.67.83',
        'port': 81,
        'weight': 11
    }
]

# Layer 7 Health monitor to be added
l7HealthMonitor = {
    'interval': 10,
    'timeout': 5,
    'maxRetries': 3,
    'urlPath': '/'
}

# Layer 7 session affinity to be added. Only supports SOURCE_IP as of now
l7SessionAffinity = {
    'type': 'SOURCE_IP'
}

# WSDL for SoftLayer_Network_LBaaS_L7Pool API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Pool?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Pool::createL7Pool API
result = client.service.createL7Pool(
    _soapheaders=[userAuthValue],
    loadBalancerUuid=uuid,
    l7Pool=l7Pool,
    l7Members=l7Members,  # optional
    l7HealthMonitor=l7HealthMonitor,  # optional
    l7SessionAffinity=l7SessionAffinity  # optional
)
print result
```
{: codeblock}

### Actualización de una agrupación de capa 7 con supervisión de estado y afinidad de sesiones
```
desde el cliente zeep import, xsd

# Username and apikey for SLAPI call
username = ''
apiKey = ''
# UUID of L7 pool to be updated
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# New Layer 7 pool values to be updated
l7Pool = {
    'loadBalancingAlgorithm': 'LEASTCONNECTION'
}

# New Layer 7 Health monitor values to be updated
l7HealthMonitor = {
    'urlPath': '/index'
}

# New Layer 7 session affinity values to be updated.
# If not given it deletes the existing session affinity
# If given and session affinity doesn't exist, it creates one.
l7SessionAffinity = {
    'type': 'SOURCE_IP'
}

# WSDL for SoftLayer_Network_LBaaS_L7Pool API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Pool?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Pool::updateL7Pool API
result = client.service.updateL7Pool(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid,
    l7Pool=l7Pool,
    l7HealthMonitor=l7HealthMonitor,  # optional
    l7SessionAffinity=l7SessionAffinity  # optional, but if not given this deletes existing session affinity.
)
print result
```
{: codeblock}

### Adición de servidores a una agrupación de capa 7
```
desde el cliente zeep import, xsd

# Username and apikey for SLAPI call
username = ''
apiKey = ''
# UUID of the L7 pool to which members should be added.
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Backend servers to be added
memberInstances = [
    {
        'address': '10.73.67.84',
        'port': 80,
        'weight': 10
    },
    {
        'address': '10.73.67.84',
        'port': 81,
        'weight': 11
    }
]

# WSDL for SoftLayer_Network_LBaaS_L7Member API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Member?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Member::addL7PoolMembers API
result = client.service.addL7PoolMembers(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid, memberInstances=memberInstances
)
print result
```
{: codeblock}

### Actualización de los servidores que pertenecen a una agrupación de capa 7
```
desde el cliente zeep import, xsd

# Username and apikey for SLAPI call
username = ''
apiKey = ''
# UUID of the L7 pool who's member we need to update
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Backend servers to be added
members = [
    {
        'uuid': '1e433123-ceae-4bbd-a4e3-2539ceb8b46f',  # UUID of the member to be updated.
        'address': '10.73.67.83',
        'port': 90,
        'weight': 10
    },
    {
        'uuid': 'bd3524db-26c8-4662-982e-04a68a420fba',
        'address': '10.73.67.83',
        'port': 91,
        'weight': 11
    }
]

# WSDL for SoftLayer_Network_LBaaS_L7Member API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Member?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_L7Member::addL7PoolMembers API
result = client.service.updateL7PoolMembers(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid, members=members
)
print result
```
