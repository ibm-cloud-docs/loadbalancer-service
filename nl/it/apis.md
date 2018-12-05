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

# Riferimento API
L'API (Application Programming Interface) di SoftLayer® è un'interfaccia di sviluppo che fornisce agli sviluppatori e agli amministratori di sistema
interazione diretta con il sistema di backend di SoftLayer. 
{:shortdesc}

La SLAPI (SoftLayer API) rafforza molte delle funzioni nel portale clienti. In generale, se è possibile un'interazione nel portale clienti, può essere eseguita anche nell'API. Di conseguenza, poiché puoi programmaticamente interagire con tutte le parti dell'ambiente SoftLayer nell'API, puoi utilizzarla per le attività automatiche.

La SLAPI (SoftLayer API) è un sistema di chiamata di procedura remota. Ogni chiamata implica l'invio di dati verso un endpoint dell'API e la
ricezione dei dati strutturati come ritorno. Il formato utilizzato per inviare e ricevere i dati con la SLAPI dipende
da quale implementazione dell'API scegli. La SLAPI al momento utilizza SOAP, XML-RPC o REST per la trasmissione dei dati. 

Per ulteriori informazioni sull'API SoftLayer, sulle API del servizio IBM Cloud Load Balancer, consulta le seguenti risorse
nella rete di sviluppo SoftLayer:
* [Getting Started with the SoftLayer API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/article/getting-started){: new_window}
* [SoftLayer_Product_Package API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Product_Package){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_LoadBalancer){: new_window}
* [SoftLayer_Network_LBaaS_Listener API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Listener){: new_window}
* [SoftLayer_Network_LBaaS_Member API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Member){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_HealthMonitor){: new_window}
* [SoftLayer_Network_LBaaS_SSLCipher API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_SSLCipher){: new_window}
* [SoftLayer_Network_LBaaS_L7Policy API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Policy){: new_window}
* [SoftLayer_Network_LBaaS_L7Rule API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Rule){: new_window}
* [SoftLayer_Network_LBaaS_L7Pool API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Pool){: new_window}
* [SoftLayer_Network_LBaaS_L7Member API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Member){: new_window}

I seguenti esempi utilizzano Python con il client SOAP zeep.

## Creazione di un programma di bilanciamento del carico
### Richiama l'ID del pacchetto del prodotto e il prezzo elemento
```
from zeep import Client, xsd
import sys

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL per l'API SoftLayer_Product_Package
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Package?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Crea oggetti valore XSD
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

### Verifica l'ordine del programma di bilanciamento del carico
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# ID sottorete privata
privateSubnetId = '<Your subnet id>'

# Dettagli ordine
# ID pacchetto richiamato dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
lbaasPackageId = 805
# ID prezzo elemento dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
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

# WSDL per l'API SoftLayer_Product_Order
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Obbligatorio da quando LBaaS è un servizio orario
    useSystemPublicIpPool=True, # Facoltativo - Valore predefinito di "True" per assegnare gli IP pubblici del programma di bilanciamento del carico
                                # da un pool di sistema IBM, altrimenti "False" dalla VLAN pubblica
                                # nel tuo account. useSystemPublicIpPool si applica solo ai
                                # programmi di bilanciamento del carico pubblici
    isPublic=True               # Facoltativo - Valore predefinito di "True" per creare un programma di bilanciamento del carico pubblico.
                                # isPublic fa distinzione tra un programma di bilanciamento del carico pubblico ("True") e
                                # interno ("False")
)

# Effettua la chiamata SLAPI all'API SoftLayer_Product_Order::verifyOrder
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

### Inserisci l'ordine del programma di bilanciamento del carico
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apikey>'
# ID sottorete privata
privateSubnetId = '<Your subnet id>'

# Dettagli ordine
# ID pacchetto richiamato dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
lbaasPackageId = 805
# ID prezzo elemento dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
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

# WSDL per l'API SoftLayer_Product_Order
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Obbligatorio da quando LBaaS è un servizio orario
    useSystemPublicIpPool=True, # Facoltativo - Valore predefinito di "True" per assegnare gli IP pubblici del programma di bilanciamento del carico
                                # da un pool di sistema IBM, altrimenti "False" dalla VLAN pubblica
                                # nel tuo account. useSystemPublicIpPool si applica solo ai
                                # programmi di bilanciamento del carico pubblici
    isPublic=True               # Facoltativo - Valore predefinito di "True" per creare un programma di bilanciamento del carico pubblico.
                                # isPublic fa distinzione tra un programma di bilanciamento del carico pubblico ("True") e
                                # interno ("False")
)

# Effettua la chiamata SLAPI all'API SoftLayer_Product_Order::placeOrder
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

## Richiamo dei dettagli dei programmi di bilanciamento del carico
### Elenca tutti i programmi di bilanciamento del carico
```
from zeep import Client

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# Prepara autenticazione per l'intestazione SOAP
userauth = {'authenticate': {'username': username, 'apiKey': apiKey}}

# Richiama tutti gli oggetti del programma di bilanciamento del carico
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

### Richiama i dettagli di un programma di bilanciamento del carico specifico
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico
uuid = '<Your load balancer uuid>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners, healthMonitors]')

# Richiama un oggetto del programma di bilanciamento del carico specifico (con objectMask per richiamare "listeners")
loadbalancer = client.service.getLoadBalancer(_soapheaders=[userAuthValue,objectMaskValue], uuid=uuid)
print 'Name: %s' % loadbalancer.name
print 'Address: %s' % loadbalancer.address
print 'OperatingStatus: %s' % loadbalancer.operatingStatus
print 'ProvisioningStatus: %s' % loadbalancer.provisioningStatus
print 'Listeners: %s' % loadbalancer.listeners
print 'HealthMonitors: %s\r\n' % loadbalancer.healthMonitors
```
{: codeblock}

## Aggiornamento di un programma di bilanciamento del carico
### Aggiungi un membro
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apikey>'
# UUID del programma di bilanciamento del carico da aggiornare
uuid = '<Your load balancer uuid>'
# Server di backend da aggiungere
serverInstances = [
    {
        'privateIpAddress': '10.121.220.141', #aggiorna con l'IP corretto
        'weight': 80 #weight is only applicable to Weight Round Robin listeners
    },
    {
        'privateIpAddress': '10.121.220.142'  #aggiorna con l'IP corretto
        # utilizza peso predefinito
    }   
]

# WSDL per l'API SoftLayer_Network_LBaaS_Member
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Member?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[members]')

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_Member::addLoadBalancerMember
result = client.service.addLoadBalancerMembers(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, serverInstances=serverInstances
)
print result
```
{: codeblock}

### Aggiungi un protocollo
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico
uuid = '<Your load balancer UUID>'
# Nuovo protocollo da aggiungere
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

# WSDL per l'API SoftLayer_Network_LBaaS_Listener
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Listener?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners]')

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_Listener::updateLoadBalancerProtocols
result = client.service.updateLoadBalancerProtocols(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, protocolConfigurations=protocolConfigurations
)
listeners = result['listeners']
print listeners
```
{: codeblock}

## Annullamento di un programma di bilanciamento del carico
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico da annullare
uuid = '<Your load balancer uuid>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_LoadBalancer::cancelLoadBalancer
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

## Visualizzazione delle metriche di monitoraggio dei programmi di bilanciamento del carico
### Ottieni la velocità effettiva del traffico HTTP
```
from zeep import Client

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico
uuid = '<Your load balancer UUID>'
# Il nome della metrica. 
# Le opzioni sono Throughput, ActiveConnections e ConnectionRate
nameOfMetric = 'Throughput'
# L'intervallo di tempo in cui ogni metrica deve essere misurata
# Le opzioni sono 1hour, 6hours, 12hours, 24hour, 1week e 2weeks
timeInterval = '1hour' 
# L'UUID del protocollo della velocità effettiva che stai richiedendo
protocolUuid = '<UUID of the protocol>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Richiama la velocità effettiva del traffico http di un oggetto del programma di bilanciamento del carico specifico
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

### Ottieni la velocità effettiva di un programma di bilanciamento del carico
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico
uuid = '<Your load balancer UUID>'
# Il nome della metrica. 
# Le opzioni sono Throughput, ActiveConnections e ConnectionRate
nameOfMetric = 'Throughput'
# L'intervallo di tempo in cui ogni metrica deve essere misurata
# Le opzioni sono 1hour, 6hours, 12hours, 24hour, 1week e 2weeks
timeInterval = '6hours' 
# Se non viene specificato alcun protocollo, viene restituita la velocità effettiva di tutti i protocolli.
# protocolUuid = '<UUID del protocollo>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Richiama la velocità effettiva del traffico http di un oggetto del programma di bilanciamento del carico specifico
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

## API L7

### Crea più politiche e regole L7
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del listener
uuid = '<Your listener UUID>'

# WSDL per l'API SoftLayer_Network_LBaaS_L7Policy
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Policy?wsdl'
client = Client(wsdl)

factory = client.type_factory('ns0')
l7Rule1 = factory.SoftLayer_Network_LBaaS_L7Rule(type = "HEADER", comparisonType = "EQUAL_TO", key = "headerkey", value = "header_key3", invert = 0)
l7Rule2 = factory.SoftLayer_Network_LBaaS_L7Rule(type = "PATH", comparisonType = "STARTS_WITH", value = "/secret_key", invert = 0)
l7RuleArray1 = factory.SoftLayer_Network_LBaaS_L7RuleArray([l7Rule1, l7Rule2])

# Configurazione di politiche e regole in blocco
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

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Policy::addL7Policies
result = client.service.addL7Policies(
    _soapheaders=[userAuthValue],
    listenerUuid=uuid, policiesRules=policiesRulesConfiguration
)
print result
```
{: codeblock}

### Aggiorna la politica L7
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL per l'API SoftLayer_Network_LBaaS_L7Policy
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Policy?wsdl'
client = Client(wsdl)

# Aggiorna la configurazione della politica specificando il nome e il valore della variabile
policyConfiguration =  {"<name>": "<value>"}

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD per i parametri L7Policy Init
xsdObjectIdElem = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_Network_LBaaS_L7PolicyInitParameters',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}id', xsd.Int())
    ])
)

# Passa l'id dell'oggetto della politica
xsdObjectId = xsdObjectIdElem(<id>)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Policy::addL7Policies
result = client.service.editObject(
    _soapheaders=[userAuthValue, xsdObjectId],
    templateObject=policyConfiguration
)
print result
```
{: codeblock}

### Aggiungi le regole a una politica L7 
```
from zeep import Client, xsd

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID della politica L7
policyUuid = '<UUID della politica L7 a cui vengono collegate le regole che vengono create>'
# Nuove regole da aggiungere
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

# WSDL per l'API SoftLayer_Network_LBaaS_L7Rule
wsdl = "https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Rule?wsdl"
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
   "{http://api.softlayer.com/soap/v3/}authenticate",
   xsd.ComplexType([
       xsd.Element("{http://api.softlayer.com/soap/v3/}username", xsd.String()),
       xsd.Element("{http://api.softlayer.com/soap/v3/}apiKey", xsd.String())
   ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Rule::addL7Rules
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

### Aggiorna più regole L7 collegate alla stessa politica L7 
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID della politica L7
policyUuid = '<UUID della politica L7 a cui vengono collegate le regole che vengono aggiornate>'
# Regole da aggiornare
ruleConfigurations = [
    {   
        'uuid':'<UUID della regola L7 che viene aggiornata>',
        'type': 'FILE_TYPE',
        'comparisonType': 'CONTAINS',
        'value': 'some_newvalue',
        'invert': 1
    },  
    {   
        'uuid':'<UUID della regola L7 che viene aggiornata>',
        'type': 'PATH',
        'comparisonType': 'EQUAL_TO',
        'value': 'some_newvalue2',
        'invert': 0
    } 
]

# WSDL per l'API SoftLayer_Network_LBaaS_L7Rule
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Rule?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Rule::updateL7Rules
result = client.service.updateL7Rules(
    _soapheaders=[userAuthValue],
    policyUuid=policyUuid, rules=ruleConfigurations
)
print result
```
{: codeblock}

### Crea un pool L7 con server, monitoraggio dell'integrità e affinità di sessione
```
from zeep import Client, xsd

# Nome utente e chiave api per la chiamata SLAP
username = ''
apiKey = ''
# UUID del programma di bilanciamento del carico da aggiornare
uuid = 'a3e466e0-5cc3-4efb-bb56-07ad63988b16'

# Pool L7 da aggiungere
l7Pool = {
    'name': 'image_pool',
    'protocol': 'HTTP',  # supporta solo HTTP
    'loadBalancingAlgorithm': 'ROUNDROBIN'
}

# Server di backend L7 da aggiungere
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

# Monitoraggio dell'integrità L7 da aggiungere
l7HealthMonitor = {
    'interval': 10,
    'timeout': 5,
    'maxRetries': 3,
    'urlPath': '/'
}

# Affinità di sessione L7 da aggiungere. Al momento supporta solo SOURCE_IP
l7SessionAffinity = {
    'type': 'SOURCE_IP'
}

# WSDL per l'API SoftLayer_Network_LBaaS_L7Pool
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Pool?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Pool::createL7Pool
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

### Aggiorna un pool L7 insieme al monitoraggio dell'integrità e all'affinità di sessione
```
from zeep import Client, xsd

# Nome utente e chiave api per la chiamata SLAP
username = ''
apiKey = ''
# UUID del pool L7 da aggiornare
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Nuovi valori del pool L7 da aggiornare
l7Pool = {
    'loadBalancingAlgorithm': 'LEASTCONNECTION'
}

# Nuovi valori del monitoraggio dell'integrità L7 da aggiornare
l7HealthMonitor = {
    'urlPath': '/index'
}

# Nuovi valori dell'affinità di sessione L7 da aggiornare.
# Se non vengono forniti, l'affinità di sessione esistente viene eliminata
# Se vengono forniti e l'affinità di sessione non esiste, ne viene creata una.
l7SessionAffinity = {
    'type': 'SOURCE_IP'
}

# WSDL per l'API SoftLayer_Network_LBaaS_L7Pool
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Pool?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Pool::updateL7Pool
result = client.service.updateL7Pool(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid,
    l7Pool=l7Pool,
    l7HealthMonitor=l7HealthMonitor,  # facoltativo
    l7SessionAffinity=l7SessionAffinity  # facoltativo, ma se non viene fornito, l'affinità di sessione esistente viene eliminata.
)
print result
```
{: codeblock}

### Aggiungi i server a un pool L7
```
from zeep import Client, xsd

# Nome utente e chiave api per la chiamata SLAP
username = ''
apiKey = ''
# UUID del pool L7 a cui devono essere aggiunti i membri.
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Server di backend da aggiungere
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

# WSDL per l'API SoftLayer_Network_LBaaS_L7Member
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Member?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Member::addL7PoolMembers
result = client.service.addL7PoolMembers(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid, memberInstances=memberInstances
)
print result
```
{: codeblock}

### Aggiorna i server che appartengono a un pool L7
```
from zeep import Client, xsd

# Nome utente e chiave api per la chiamata SLAP
username = ''
apiKey = ''
# UUID del pool L7 di cui dobbiamo aggiornare il membro
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Server di backend da aggiungere
members = [
    {
        'uuid': '1e433123-ceae-4bbd-a4e3-2539ceb8b46f',  # UUID del membro da aggiornare.
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

# WSDL per l'API SoftLayer_Network_LBaaS_L7Member
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Member?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_L7Member::addL7PoolMembers
result = client.service.updateL7PoolMembers(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid, members=members
)
print result
```
