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

# API-Referenz
Die API (Application Programming Interface) von SoftLayer® ist die Entwicklungsschnittstelle, die Entwicklern und Systemadministratoren die direkte Interaktion mit dem SoftLayer-Back-End-System ermöglicht. 
{:shortdesc}

Die SoftLayer-API (SLAPI) unterstützt viele Funktionen im Kundenportal. Im Allgemeinen kann eine Interaktion, die im Kundenportal möglich ist, auch in der API ausgeführt werden. Da Sie mit allen Teilen der SoftLayer-Umgebung in der API programmgesteuert interagieren können, können Sie die API zum Automatisieren von Tasks verwenden.

Die SoftLayer-API (SLAPI) ist ein Remote Procedure Call-System. Bei jedem Aufruf werden Daten zum API-Endpunkt gesendet und anschließend strukturierte Daten empfangen. Welches Format zum Senden und Empfangen der Daten mit der SLAPI verwendet wird, hängt von der jeweils ausgewählten Implementierung der API ab. Von der SLAPI werden derzeit SOAP, XML-RPC und REST für die Datenübertragung verwendet. 

Weitere Informationen zur SoftLayer-API und zu den IBM Cloud Load Balancer Service-APIs finden Sie in den folgenden Ressourcen
im SoftLayer Development Network:
* [Einführung in die SoftLayer-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/article/getting-started){: new_window}
* [SoftLayer_Product_Package-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Product_Package){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_LoadBalancer){: new_window}
* [SoftLayer_Network_LBaaS_Listener-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Listener){: new_window}
* [SoftLayer_Network_LBaaS_Member-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Member){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_HealthMonitor){: new_window}
* [SoftLayer_Network_LBaaS_SSLCipher-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_SSLCipher){: new_window}
* [SoftLayer_Network_LBaaS_L7Policy-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Policy){: new_window}
* [SoftLayer_Network_LBaaS_L7Rule-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Rule){: new_window}
* [SoftLayer_Network_LBaaS_L7Pool-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Pool){: new_window}
* [SoftLayer_Network_LBaaS_L7Member-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_L7Member){: new_window}

In den folgenden Beispielen wird Python mit einem Zeep-SOAP-Client verwendet.

## Lastausgleichsfunktion erstellen
### Produktpaket-ID und Artikelpreis abrufen
```
from zeep import Client, xsd
import sys

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Your username>'
apiKey = '<Ihr API-Schlüssel>'

# WSDL für SoftLayer_Product_Package-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Package?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# XSD-Wertobjekte erstellen
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

### Bestellung der Lastausgleichsfunktion überprüfen
```
from zeep import Client, xsd
from zeep.exceptions import Fault

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# Private Teilnetz-ID
privateSubnetId = '<Your subnet id>'

# Bestellungsdetails
# Von SoftLayer_Product_Package-API abgerufene Paket-ID
# (Beispiel siehe oben)
lbaasPackageId = 805
# Von SoftLayer_Product_Package-API abgerufene Artikelpreis-ID
# (Beispiel siehe oben)
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

# WSDL für SoftLayer_Product_Package-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Erforderlich, da LBaaS ein stündlicher Service ist
    useSystemPublicIpPool=True, # Optional - Standardwert ist "True" zum Zuordnen der öffentlichen IPs der Lastausgleichsfunktion
                                # von einem IBM Systempool, andernfalls "False" vom öffentlichen VLAN
                                # in Ihrem Konto. useSystemPublicIpPool ist nur anwendbar auf
                                # öffentliche Lastausgleichsfunktionen
    isPublic=True               # Optional - Standardwert ist "True" zum Erstellen einer öffentlichen Lastausgleichsfunktion
                                # isPublic unterscheidet zwischen öffentlicher ("True") und
                                # interner ("False") Lastausgleichsfunktion
)

# SLAPI-Aufruf an SoftLayer_Product_Order::verifyOrder-API ausführen
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

### Bestellung für Lastausgleichsfunktion aufgeben
```
from zeep import Client, xsd
from zeep.exceptions import Fault

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# Private Teilnetz-ID
privateSubnetId = '<Your subnet id>'

# Bestellungsdetails
# Von SoftLayer_Product_Package-API abgerufene Paket-ID
# (Beispiel siehe oben)
lbaasPackageId = 805
# Von SoftLayer_Product_Package-API abgerufene Artikelpreis-ID
# (Beispiel siehe oben)
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

# WSDL für SoftLayer_Product_Package-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Erforderlich, da LBaaS ein stündlicher Service ist
    useSystemPublicIpPool=True, # Optional - Standardwert ist "True" zum Zuordnen der öffentlichen IPs der Lastausgleichsfunktion
                                # von einem IBM Systempool, andernfalls "False" vom öffentlichen VLAN
                                # in Ihrem Konto. useSystemPublicIpPool ist nur anwendbar auf
                                # öffentliche Lastausgleichsfunktionen
    isPublic=True               # Optional - Standardwert ist "True" zum Erstellen einer öffentlichen Lastausgleichsfunktion
                                # isPublic unterscheidet zwischen öffentlicher ("True") und
                                # interner ("False") Lastausgleichsfunktion
)

# SLAPI-Aufruf für SoftLayer_Product_Order::placeOrder-API ausführen
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

## Details der Lastausgleichsfunktionen abrufen
### Alle Lastausgleichsfunktionen auflisten
```
from zeep import Client

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'

# WSDL für SoftLayer_Network_LBaaS_LoadBalancer-API
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# Authentifizierung für SOAP-Header vorbereiten
userauth = {'authenticate': {'username': username, 'apiKey': apiKey}}

# Alle Objekte der Lastausgleichsfunktion abrufen
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

### Details einer bestimmten Lastausgleichsfunktion abrufen
```
from zeep import Client, xsd 

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der Lastausgleichsfunktion
uuid = '<Your load balancer uuid>'

# WSDL für SoftLayer_Network_LBaaS_LoadBalancer-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners, healthMonitors]')

# Bestimmtes Objekt einer Lastausgleichsfunktion abrufen (mit Objektmaske zum Abrufen von "Listenern")
loadbalancer = client.service.getLoadBalancer(_soapheaders=[userAuthValue,objectMaskValue], uuid=uuid)
print 'Name: %s' % loadbalancer.name
print 'Address: %s' % loadbalancer.address
print 'OperatingStatus: %s' % loadbalancer.operatingStatus
print 'ProvisioningStatus: %s' % loadbalancer.provisioningStatus
print 'Listeners: %s' % loadbalancer.listeners
print 'HealthMonitors: %s\r\n' % loadbalancer.healthMonitors
```
{: codeblock}

## Lastausgleichsfunktion aktualisieren
### Mitglied hinzufügen
```
from zeep import Client, xsd 

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der zu aktualisierenden Lastausgleichsfunktion
uuid = '<Your load balancer uuid>'
# Hinzuzufügende Back-End-Server
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

# WSDL für SoftLayer_Network_LBaaS_Member-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Member?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[members]')

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_Member::addLoadBalancerMember-API ausführen
result = client.service.addLoadBalancerMembers(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, serverInstances=serverInstances
)
print result
```
{: codeblock}

### Protokoll hinzufügen
```
from zeep import Client, xsd 

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der Lastausgleichsfunktion
uuid = '<Your load balancer UUID>'
# Neues Protokoll, das hinzugefügt werden soll
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

# WSDL für SoftLayer_Network_LBaaS_Listener-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Listener?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners]')

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_Listener::updateLoadBalancerProtocols-API ausführen
result = client.service.updateLoadBalancerProtocols(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, protocolConfigurations=protocolConfigurations
)
listeners = result['listeners']
print listeners
```
{: codeblock}

## Lastausgleichsfunktion abbrechen
```
from zeep import Client, xsd
from zeep.exceptions import Fault

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der Lastausgleichsfunktion, die abgebrochen werden soll
uuid = '<Your load balancer uuid>'

# WSDL für SoftLayer_Network_LBaaS_LoadBalancer-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_LoadBalancer::cancelLoadBalancer-API ausführen
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

## Überwachungsmetriken von Lastausgleichsfunktionen anzeigen
### Durchsatz des HTTP-Datenverkehrs abrufen
```
from zeep import Client

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der Lastausgleichsfunktion
uuid = '<Your load balancer UUID>'
# Der Name der Metrik. 
# Optionen sind Throughput, ActiveConnections und ConnectionRate
nameOfMetric = 'Throughput'
# Das Zeitintervall, mit dem die Metrik gemessen werden soll
# Optionen sind 1hour, 6hours, 12hours, 24hour, 1week, and 2weeks
timeInterval = '1hour' 
# UUID des Protokolls, dessen Durchsatz Sie anfordern
protocolUuid = '<UUID of the protocol>'

# WSDL für SoftLayer_Network_LBaaS_LoadBalancer-API
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Durchsatz des HTTP-Verkehrs für ein bestimmtes Objekt einer Lastausgleichsfunktion
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

### Durchsatz einer Lastausgleichsfunktion abrufen
```
from zeep import Client, xsd 

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der Lastausgleichsfunktion
uuid = '<Your load balancer UUID>'
# Der Name der Metrik. 
# Optionen sind Throughput, ActiveConnections und ConnectionRate
nameOfMetric = 'Throughput'
# Das Zeitintervall, mit dem die Metrik gemessen werden soll
# Optionen sind 1hour, 6hours, 12hours, 24hour, 1week, and 2weeks
timeInterval = '6hours' 
# Falls kein Protokoll angegeben ist, wird der Durchsatz aller Protokolle zurückgegeben.
# protocolUuid = '<UUID des Protokolls>'

# WSDL für SoftLayer_Network_LBaaS_LoadBalancer-API
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Durchsatz des HTTP-Verkehrs für ein bestimmtes Objekt einer Lastausgleichsfunktion
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

## Layer 7-APIs

### Mehrere L7-Richtlinien und L7-Regeln erstellen
```
from zeep import Client, xsd 

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID von Listener
uuid = '<Ihre Listener-UUID>'

# WSDL für SoftLayer_Network_LBaaS_L7Policy-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Policy?wsdl'
client = Client(wsdl)

factory = client.type_factory('ns0')
l7Rule1 = factory.SoftLayer_Network_LBaaS_L7Rule(type = "HEADER", comparisonType = "EQUAL_TO", key = "headerkey", value = "header_key3", invert = 0)
l7Rule2 = factory.SoftLayer_Network_LBaaS_L7Rule(type = "PATH", comparisonType = "STARTS_WITH", value = "/secret_key", invert = 0)
l7RuleArray1 = factory.SoftLayer_Network_LBaaS_L7RuleArray([l7Rule1, l7Rule2])

# Massenkonfiguration von Richtlinien und Regeln
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

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Policy::addL7Policies-API ausführen
result = client.service.addL7Policies(
    _soapheaders=[userAuthValue],
    listenerUuid=uuid, policiesRules=policiesRulesConfiguration
)
print result
```
{: codeblock}

### Layer 7-Richtlinie aktualisieren
```
from zeep import Client, xsd 

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'

# WSDL für SoftLayer_Network_LBaaS_L7Policy-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Policy?wsdl'
client = Client(wsdl)

# Richtlinienkonfiguration aktualisieren durch Angabe des Variablennamens und -werts
policyConfiguration =  {"<Name>": "<Wert>"}

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD für L7Policy-Init-Parameter
xsdObjectIdElem = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_Network_LBaaS_L7PolicyInitParameters',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}id', xsd.Int())
    ])
)

# ID des Richtlinienobjekts übergeben
xsdObjectId = xsdObjectIdElem(<id>)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Policy::addL7Policies-API ausführen
result = client.service.editObject(
    _soapheaders=[userAuthValue, xsdObjectId],
    templateObject=policyConfiguration
)
print result
```
{: codeblock}

### Regeln zu einer Layer-7-Richtlinie hinzufügen 
```
from zeep import Client, xsd

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der Layer 7-Richtlinie
policyUuid = '<UUID der L7-Richtlinie, an die die erstellten Regeln angehängt werden sollen>'
# Neue Regeln, die hinzugefügt werden sollen
ruleConfigurations = [
   {  
       "type": "FILE_TYPE",
       "comparisonType": "CONTAINS",
       "value": "beliebiger_wert",
       "invert": 1
   },  
   {  
            "type": "PATH",
            "comparisonType": "EQUAL_TO",
            "value": "beliebiger_wert",
            "invert": 0
   } 
]

# WSDL für SoftLayer_Network_LBaaS_L7Rule-API
wsdl = "https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Rule?wsdl"
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
   "{http://api.softlayer.com/soap/v3/}authenticate",
   xsd.ComplexType([
       xsd.Element("{http://api.softlayer.com/soap/v3/}username", xsd.String()),
       xsd.Element("{http://api.softlayer.com/soap/v3/}apiKey", xsd.String())
   ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Rule::addL7Rules-API ausführen
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

### Mehrere Layer 7-Regeln, die an dieselbe Layer 7-Richtlinie angehängt sind, aktualisieren 
```
from zeep import Client, xsd 

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = '<Ihr Benutzername>'
apiKey = '<Ihr API-Schlüssel>'
# UUID der Layer 7-Richtlinie
policyUuid = '<UUID der L7-Richtlinie, an die die zu aktualisierenden Regeln angehängt sind>'
# Regeln, die aktualisiert werden sollen
ruleConfigurations = [
    {   
        'uuid':'<UUID der L7-Regel, die aktualisiert wird>',
        'type': 'FILE_TYPE',
        'comparisonType': 'CONTAINS',
        'value': 'beliebiger_neuer_wert',
        'invert': 1
    },  
    {   
        'uuid':'<UUID der L7-Regel, die aktualisiert wird>',
        'type': 'PATH',
        'comparisonType': 'EQUAL_TO',
        'value': 'beliebiger_neuer_wert2',
        'invert': 0
    } 
]

# WSDL für SoftLayer_Network_LBaaS_L7Rule-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Rule?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Rule::updateL7Rules-API ausführen
result = client.service.updateL7Rules(
    _soapheaders=[userAuthValue],
    policyUuid=policyUuid, rules=ruleConfigurations
)
print result
```
{: codeblock}

### Layer 7-Pool mit Servern, Statusüberwachung und Sitzungsaffinität erstellen
```
from zeep import Client, xsd

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = ''
apiKey = ''
# UUID der Lastausgleichsfunktion, die aktualisiert werden soll
uuid = 'a3e466e0-5cc3-4efb-bb56-07ad63988b16'

# Layer 7-Pool, der hinzugefügt werden soll
l7Pool = {
    'name': 'image_pool',
    'protocol': 'HTTP',  # unterstützt nur HTTP
    'loadBalancingAlgorithm': 'ROUNDROBIN'
}

# Layer 7-Back-End-Server, die hinzugefügt werden sollen
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

# Layer 7-Statusüberwachung, die hinzugefügt werden soll
l7HealthMonitor = {
    'interval': 10,
    'timeout': 5,
    'maxRetries': 3,
    'urlPath': '/'
}

# Layer 7-Sitzungsaffinität, die hinzugefügt werden soll. Derzeit nur Unterstützung für SOURCE_IP
l7SessionAffinity = {
    'type': 'SOURCE_IP'
}

# WSDL für SoftLayer_Network_LBaaS_L7Pool-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Pool?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Pool::createL7Pool-API ausführen
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

### Layer 7-Pool zusammen mit Statusüberwachung und Sitzungsaffinität aktualisieren
```
from zeep import Client, xsd

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = ''
apiKey = ''
# UUID des L7-Pool, der aktualisiert werden soll
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Neue Layer 7-Pool-Werte, die aktualisiert werden sollen
l7Pool = {
    'loadBalancingAlgorithm': 'LEASTCONNECTION'
}

# Neue Layer 7-Statusüberwachungswerte, die aktualisiert werden sollen
l7HealthMonitor = {
    'urlPath': '/index'
}

# Neue Layer 7-Sitzungsaffinitätswerte, die aktualisiert werden sollen
# Wenn nichts angegeben, wird die vorhandene Sitzungsaffinität gelöscht.
# Wenn angegeben und die Sitzungsaffinität ist nicht vorhanden, wird eine erstellt.
l7SessionAffinity = {
    'type': 'SOURCE_IP'
}

# WSDL für SoftLayer_Network_LBaaS_L7Pool-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Pool?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Pool::updateL7Pool-API
result = client.service.updateL7Pool(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid,
    l7Pool=l7Pool,
    l7HealthMonitor=l7HealthMonitor,  # optional
    l7SessionAffinity=l7SessionAffinity  # optional, aber wenn nicht angegeben, wird die vorhandene Sitzungsaffinität gelöscht.
)
print result
```
{: codeblock}

### Server zu einem Layer 7-Pool hinzufügen
```
from zeep import Client, xsd

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = ''
apiKey = ''
# UUID des L7-Pools, dem Mitglieder hinzugefügt werden sollen
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Back-End-Server, die hinzugefügt werden sollen
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

# WSDL für SoftLayer_Network_LBaaS_L7Member-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Member?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Member::addL7PoolMembers-API ausführen
result = client.service.addL7PoolMembers(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid, memberInstances=memberInstances
)
print result
```
{: codeblock}

### Server aktualisieren, die zu einem Layer 7-Pool gehören
```
from zeep import Client, xsd

# Benutzername und API-Schlüssel für SLAPI-Aufruf
username = ''
apiKey = ''
# UUID des L7-Pools, dessen Mitglied aktualisiert werden soll
l7PoolUuid = '095a9033-d127-4c95-8c0c-67af8c970a3a'

# Back-End-Server, die hinzugefügt werden sollen
members = [
    {
        'uuid': '1e433123-ceae-4bbd-a4e3-2539ceb8b46f',  # UUID des Mitglieds, das aktualisiert werden soll
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

# WSDL für SoftLayer_Network_LBaaS_L7Member-API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_L7Member?wsdl'
client = Client(wsdl)

# XSD für Authentifizierung
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD für Objektmaske
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# XSD-Wertobjekte erstellen
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# SLAPI-Aufruf für SoftLayer_Network_LBaaS_L7Member::addL7PoolMembers-API
result = client.service.updateL7PoolMembers(
    _soapheaders=[userAuthValue],
    l7PoolUuid=l7PoolUuid, members=members
)
print result
```
