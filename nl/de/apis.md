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
{: #api-reference}

Die API (Application Programming Interface) von SoftLayer® ist die Entwicklungsschnittstelle, die Entwicklern und Systemadministratoren die direkte Interaktion mit dem SoftLayer-Back-End-System ermöglicht.
{:shortdesc}

Die SoftLayer-API (SLAPI) unterstützt viele Funktionen im Kundenportal. Im Allgemeinen kann eine Interaktion, die im Kundenportal möglich ist, auch in der API ausgeführt werden. Da Sie mit allen Teilen der SoftLayer-Umgebung in der API programmgesteuert interagieren können, können Sie die API zum Automatisieren von Tasks verwenden.

Die SoftLayer-API (SLAPI) ist ein Remote Procedure Call-System. Bei jedem Aufruf werden Daten zum API-Endpunkt gesendet und anschließend strukturierte Daten empfangen. Welches Format zum Senden und Empfangen der Daten mit der SLAPI verwendet wird, hängt von der jeweils ausgewählten Implementierung der API ab. Von der SLAPI werden derzeit SOAP, XML-RPC und REST für die Datenübertragung verwendet.

Weitere Informationen zur SoftLayer-API und zu den {{site.data.keyword.loadbalancer_full}} Service-APIs finden Sie in den folgenden Ressourcen im SoftLayer Development Network:
* [Einführung in die SoftLayer-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/article/getting-started/){: new_window}
* [SoftLayer_Product_Package-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Product_Package/){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_LoadBalancer/){: new_window}
* [SoftLayer_Network_LBaaS_Listener-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Listener/){: new_window}
* [SoftLayer_Network_LBaaS_Member-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Member/){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_HealthMonitor/){: new_window}
* [SoftLayer_Network_LBaaS_SSLCipher-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_SSLCipher/){: new_window}
* [SoftLayer_Network_LBaaS_L7Policy-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Policy/){: new_window}
* [SoftLayer_Network_LBaaS_L7Rule-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Rule/){: new_window}
* [SoftLayer_Network_LBaaS_L7Pool-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Pool/){: new_window}
* [SoftLayer_Network_LBaaS_L7Member-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Member/){: new_window}

Die folgenden Beispiele verwenden den Client [softlayer-python ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/softlayer/softlayer-python){: new_window}.

Legen Sie für jedes Beispiel einen API-Benutzernamen und einen API-Schlüssel fest, falls Sie keine Datei `~/.softlayer` in Ihrer Umgebung konfiguriert haben.

```py
client = SoftLayer.Client(username='set me', api_key='set me')
```

## Lastausgleichsfunktion erstellen
Im folgenden Beispiel werden die Paket-ID, Teilnetz-ID und die Preise für das Paket "Load Balancer As A Service (LBaaS)" abgerufen, die Bestelldaten erstellen und die Bestellung platziert/überprüft.

```py
import SoftLayer
from pprint import pprint

class LBaaSExample():
    def __init__(self):
        self.client = SoftLayer.Client()

    def get_package_id(self, pkg_name):
        """Gibt die PackageId für LBaaS zurück"""
        _filter = {"name":{"operation": pkg_name}}

        pkg_list = self.client['Product_Package'].getAllObjects(filter=_filter)

        return pkg_list[0]['id']


    def get_item_prices(self, pkg_id):
        """Gibt die Standardpreise zurück"""

        item_list = self.client['Product_Package'].getItems(id=pkg_id)
        prices = []

        for item in item_list:
            price_id = [p['id'] for p in item['prices']
                            if not p['locationGroupId']][0]
            prices.append(price_id)

        return prices

    def get_subnet_id(self, datacenter):
        """Sucht das erste Teilnetz im Rechenzentrum und gibt es zurück"""

        _filter = {"privateSubnets": {
                        "networkVlan": {
                            "primaryRouter": {
                                "datacenter": {
                                    "regions": { "keyname": { "operation": datacenter}}
                                }
                            },
                            "type": { "keyName": { "operation": "STANDARD" } }
                        },
                        "routingTypeKeyName": {"operation": "PRIMARY" }
                    }
                }

        subnets = self.client['Account'].getPrivateSubnets(filter=_filter)

        return subnets[0]['id']

    def order_lbaas(self, pkg_name, datacenter, name, desc, protocols,
                    subnet_id=None, public=False, verify=False):
        """Ermöglicht das Anfordern einer Lastausgleichsfunktion"""

        package_id = self.get_package_id(pkg_name)
        prices = self.get_item_prices(package_id)

        # Teilnetz-ID suchen und auswählen, falls keine angegeben.
        if subnet_id is None:
            subnet_id = self.get_subnet_id(datacenter)

        # Konfiguration der Bestellung erstellen
        orderData = {
            'complexType': 'SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService',
            'name': name,
            'description': desc,
            'location': datacenter,
            'packageId': package_id,
            'useHourlyPricing': True,       # Erforderlich, da LBaaS ein stündlicher Service ist
            'prices': [{'id': price_id} for price_id in prices],
            'protocolConfigurations': protocols,
            'subnets': [{'id': subnet_id}]
        }

        try:
            # Bei verify=True wird Ihre Bestellung auf Fehler überprüft.
            # LBaaS wird bestellt, wenn False.
            if verify:
                response = self.client['Product_Order'].verifyOrder(orderData)
            else:
                response = self.client['Product_Order'].placeOrder(orderData)

            return response
        except SoftLayer.SoftLayerAPIError as e:            
            print("Unable to place the order: %s, %s" % (e.faultCode, e.faultString))


if __name__ == "__main__":
    lbaas = LBaaSExample()

    package_name = 'Load Balancer As A Service (LBaaS)'
    location = 'MEXICO'
    name = 'My-LBaaS-name'
    description = 'A description sample'

    # 'False' für privates Netz festlegen
    is_public = True

    protocols = [        
        {
            "backendPort": 80,
            "backendProtocol": "HTTP",
            "frontendPort": 8080,
            "frontendProtocol": "HTTP",
            "loadBalancingMethod": "ROUNDROBIN",    # ROUNDROBIN, LEASTCONNECTION, WEIGHTED_RR
            "maxConn": 1000
        }
    ]

    # verify=True entfernen, um Bestellung aufzugeben
    receipt = lbaas.order_lbaas(package_name, location, name, description,
                                protocols, public=is_public, verify=True)

    pprint(receipt)
```
{: codeblock}

## Details der Lastausgleichsfunktionen abrufen
### Alle Lastausgleichsfunktionen auflisten
```py
import SoftLayer
from prettytable import PrettyTable

class LBaasExample():
    def __init__(self):
        client = SoftLayer.Client()
        self.lbaas_service = client['Network_LBaaS_LoadBalancer']

    def get_list(self, dc=None):
        _filter = None
        lbaas_list = None

        # Filter verwenden, wenn Rechenzentrum festgelegt ist
        if dc:
            _filter = {"datacenter":{"name":{"operation": dc}}}

        try:
            # Lastausgleichsfunktionsobjekte abrufen
            lbaas_list = self.lbaas_service.getAllObjects(filter=_filter)
        except SoftLayer.SoftLayerAPIError as e:
            print("Unable to get the LBaaS list: %s, %s" % (e.faultCode, e.faultString))

        return lbaas_list


if __name__ == "__main__":
    table = PrettyTable(['ID','UUID','Name', 'Description',
                         'Address', 'Type', 'Location', 'Status'])

    # Um alle LBaas in Mexiko zu suchen
    datacenter = "mex01"

    lbaas = LBaasExample()
    # dc=datacenter entfernen, um alle Lastenausgleichsfunktionen im Konto abzurufen
    lbaas_list = lbaas.get_list(dc=datacenter)

    # LBaaS-Daten zur Tabelle hinzufügen
    for i in lbaas_list:
        isPublic = "Public" if i['isPublic'] == 1 else "Private"
        table.add_row([i['id'], i['uuid'], i['name'], i['description'], i['address'],
                       isPublic,i['datacenter']['longName'],i['operatingStatus']])

    print (table)
```
{: codeblock}

### Details einer bestimmten Lastausgleichsfunktion abrufen
```py
import SoftLayer
from pprint import pprint

# Ihre Lastausgleichsfunktions-UUID
uuid = 'set me'
# Maske zum Abrufen der Lastausgleichsfunktion-Listener und Statusüberwachungen
_mask = "mask[listeners, healthMonitors]"

# API-Client erstellen
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Ein bestimmtes Lastausgleichsfunktionsobjekt abrufen
    details = lbaas_service.getLoadBalancer(uuid, mask=_mask)
    pprint(details)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to retrieve LBaaS details: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Lastausgleichsfunktion aktualisieren
### Mitglied hinzufügen
```py
import SoftLayer
from pprint import pprint

# Ihre Lastausgleichsfunktions-UUID
uuid = 'set me'

# Mit korrekter IP-Adresse aktualisieren
serverInstances = [
    { "privateIpAddress": "10.131.11.46", "weight": 80 },
    { "privateIpAddress": "10.131.11.6" } # Default weight=50
]

# API-Client erstellen
client = SoftLayer.Client()
member_service = client['Network_LBaaS_Member']

_mask = "mask[members]"

try:
    response = member_service.addLoadBalancerMembers(uuid, serverInstances, mask=_mask)
    pprint(response)
except SoftLayer.SoftLayerAPIError as e:            
    print("Unable to add members: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

### Protokoll hinzufügen
```py
import SoftLayer
from pprint import pprint

# Ihre Lastausgleichsfunktions-UUID
uuid = 'set me'

# Neue hinzuzufügende Protokolle
protocolConfigurations = [
    {
        "backendPort": 1350,
        "backendProtocol": "TCP",
        "frontendPort": 1450,
        "frontendProtocol": "TCP",
        "loadBalancingMethod": "WEIGHTED_RR",    # ROUNDROBIN, LEASTCONNECTION, WEIGHTED_RR
        "maxConn": 500,
        "sessionType": "SOURCE_IP"
    },
    {
        "backendPort": 1200,
        "backendProtocol": "HTTP",
        "frontendPort": 1150,
        "frontendProtocol": "HTTP",
        "loadBalancingMethod": "ROUNDROBIN",    # ROUNDROBIN, LEASTCONNECTION, WEIGHTED_RR
        "maxConn": 1000,
        "sessionType": "SOURCE_IP"
    }
]

# API-Client erstellen
client = SoftLayer.Client()
listener_service = client['Network_LBaaS_Listener']

_mask = "mask[listeners]"

try:
    response = listener_service.updateLoadBalancerProtocols(uuid, protocolConfigurations, mask=mask)
    pprint(response)
except SoftLayer.SoftLayerAPIError as e:            
    print("Unable to add protocols: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Lastausgleichsfunktion abbrechen
```py
import SoftLayer

# Ihre Lastausgleichsfunktions-UUID
uuid = 'set me'

# API-Client erstellen
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    result = lbaas_service.cancelLoadBalancer(uuid)

    if result:
        print("The cancellation request is accepted")
except SoftLayer.SoftLayerAPIError as e:            
    print("Failed to cancel load balancer: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Überwachungsmetriken von Lastausgleichsfunktionen anzeigen
### Durchsatz des HTTP-Datenverkehrs abrufen
```py
import SoftLayer
from pprint import pprint

# Ihre Lastausgleichsfunktions-UUID
uuid = 'set me'

# Verfügbare Optionen: Throughput, ActiveConnections und ConnectionRate.
metric_name = 'Throughput'

# Optionen sind: 1hour, 6hours, 12hours, 24hour, 1week oder 2weeks
time_range = '1hour'

# UUID des Listener, dessen Durchsatz Sie anfordern
protocol_uuid = 'set me'

# API-Client erstellen
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Protokoll-UUID entfernen, um Datenverkehrsmetriken der gesamten Lastausgleichsfunktion abzurufen
    time_series = lbaas_service.getListenerTimeSeriesData(uuid, metric_name,
                                                          time_range, protocol_uuid)

    pprint(time_series)
except SoftLayer.SoftLayerAPIError as e:            
    print("Unable to retrieve the traffic: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Layer 7-APIs

### Mehrere L7-Richtlinien und L7-Regeln erstellen
```py
import SoftLayer
from pprint import pprint

# UUID des Listeners
listener_uuid = "set me"

# Regeln erstellen
l7RuleArray1 = [
    {
        "type": "HEADER",
        "comparisonType": "EQUAL_TO",
        "key": "headerkey",
        "value": "header_key3",
        "invert": 0
    },
    {
        "type": "PATH",
        "comparisonType": "STARTS_WITH",
        "value": "/secret_key",
        "invert": 0
    }
]

# Massenkonfiguration von Richtlinien und Regeln
policies_rules = [
    {
        "l7Policy": {
            "name": "traf_test1",
            "action": "REDIRECT_URL",
            "priority":101,
            "redirectUrl": "http://example.com"
        },
     "l7Rules": l7RuleArray1
    }
]

client = SoftLayer.Client()
networkLBaaSL7PolicyService = client['SoftLayer_Network_LBaaS_L7Policy']

try:
    result = networkLBaaSL7PolicyService.addL7Policies(listener_uuid, policies_rules)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to addL7Policies: %s, %s " % (e.faultCode, e.faultString))
```
{: codeblock}

### Layer 7-Richtlinie aktualisieren
```py
import SoftLayer
from pprint import pprint

# Die ID der Richtlinie, die aktualisiert werden soll
networkLBaaSL7PolicyId = 11111111

# Richtlinienkonfiguration durch Angabe des Namens und Werts der Variable aktualisieren, z. B. "<name>": "<value>"
policyConfiguration = {
    "name": "<value>"
}

client = SoftLayer.Client()
networkLBaaSL7PolicyService = client['SoftLayer_Network_LBaaS_L7Policy']

try:
    result = networkLBaaSL7PolicyService.editObject(policyConfiguration, id=networkLBaaSL7PolicyId)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to update the Layer 7 policy: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

### Regeln zu einer Layer-7-Richtlinie hinzufügen 
```py
import SoftLayer
from pprint import pprint

# UUID der Ebene 7-Richtlinie
policyUuid = "set me"

# Neue hinzuzufügende Regeln
rules = [
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

client = SoftLayer.Client()
networkLBaaSL7RuleService = client['SoftLayer_Network_LBaaS_L7Rule']

try:
    result = networkLBaaSL7RuleService.addL7Rules(policyUuid, rules)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to add rules to a Layer 7 policy: %s, %s " % (e.faultCode, e.faultString))
```
{: codeblock}

### Mehrere Layer 7-Regeln, die an dieselbe Layer 7-Richtlinie angehängt sind, aktualisieren 
```py
# Für eine gute Debugausgabe:
import SoftLayer
from pprint import pprint

# UUID der Ebene 7-Richtlinie
policyUuid = "set me"

# Neue hinzuzufügende Regeln
rules = [
    {
        'uuid': '<UUID of the L7 Rule being updated>',
        'type': 'FILE_TYPE',
        'comparisonType': 'CONTAINS',
        'value': 'some_newvalue',
        'invert': 1
    },
    {
        'uuid': '<UUID of the L7 Rule being updated>',
        'type': 'PATH',
        'comparisonType': 'EQUAL_TO',
        'value': 'some_newvalue2',
        'invert': 0
    }
]

client = SoftLayer.Client()
networkLBaaSL7RuleService = client['SoftLayer_Network_LBaaS_L7Rule']

try:
    result = networkLBaaSL7RuleService.updateL7Rules(policyUuid, rules)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:    
    print("Unable to update multiple Layer 7 Rules attached to the same Layer 7 policy: %s, %s"
          % (e.faultCode, e.faultString))
```
{: codeblock}

### Layer 7-Pool mit Servern, Statusüberwachung und Sitzungsaffinität erstellen
```py
import SoftLayer
from pprint import pprint

# UUID der zu aktualisierenden Lastausgleichsfunktion
loadBalancerUuid = "set me"

# Layer 7-Pool, der hinzugefügt werden soll
l7Pool = {
    'name': 'image_pool',
    'protocol': 'HTTP',  # unterstützt nur HTTP
    'loadBalancingAlgorithm': 'ROUNDROBIN'
}

# Layer 7-Back-End-Server, die hinzugefügt werden sollen
l7Members = [
    {
        'address': '10.131.11.46',
        'port': 80,
        'weight': 10
    },
    {
        'address': '10.130.188.130',
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

client = SoftLayer.Client()
networkLBaaSL7PoolService = client['SoftLayer_Network_LBaaS_L7Pool']

try:
    result = networkLBaaSL7PoolService.createL7Pool(loadBalancerUuid, l7Pool, l7Members,
                                                    l7HealthMonitor, l7SessionAffinity)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:    
    print("Unable to create a Layer 7 Pool with servers: %s, %s"
          % (e.faultCode, e.faultString))
```
{: codeblock}

### Layer 7-Pool zusammen mit Statusüberwachung und Sitzungsaffinität aktualisieren
```py
import SoftLayer
from pprint import pprint

# UUID des zu aktualisierenden L7-Pools
l7PoolUuid = 'set me'

# Neue Layer 7-Pool-Werte, die aktualisiert werden sollen
l7Pool = {'loadBalancingAlgorithm': 'LEASTCONNECTION'}

# Neue Layer 7-Statusüberwachungswerte, die aktualisiert werden sollen
l7HealthMonitor = {'urlPath': '/index'}

# Neue Layer 7-Sitzungsaffinitätswerte, die aktualisiert werden sollen
# Wenn nichts angegeben, wird die vorhandene Sitzungsaffinität gelöscht.
# Wenn angegeben und die Sitzungsaffinität ist nicht vorhanden, wird eine erstellt.
l7SessionAffinity = {'type': 'SOURCE_IP'}

client = SoftLayer.Client()
networkLBaaSL7PoolService = client['SoftLayer_Network_LBaaS_L7Pool']

try:
    result = networkLBaaSL7PoolService.updateL7Pool(l7PoolUuid, l7Pool,
                                                    l7HealthMonitor, l7SessionAffinity)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to update a Layer 7 pool along with health monitoring and session affinity: %s, %s"
          % (e.faultCode, e.faultString))
```
{: codeblock}

### Server zu einem Layer 7-Pool hinzufügen
```py
import SoftLayer
from pprint import pprint

# UUID des L7-Pools, dem Mitglieder hinzugefügt werden sollen
l7PoolUuid = 'set me'

# Back-End-Server, die hinzugefügt werden sollen
memberInstances = [
    {
        'address': '10.131.11.46',
        'port': 80,
        'weight': 10
    },
    {
        'address': '10.130.188.130',
        'port': 81,
        'weight': 11
    }
]

client = SoftLayer.Client()
networkLBaaSL7MemberService = client['SoftLayer_Network_LBaaS_L7Member']

try:
    result = networkLBaaSL7MemberService.addL7PoolMembers(l7PoolUuid, memberInstances)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to add servers to a Layer 7 Pool: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

### Server aktualisieren, die zu einem Layer 7-Pool gehören
```py
import SoftLayer
from pprint import pprint

# UUID des L7-Pools, dessen Mitglied aktualisiert werden soll
l7PoolUuid = 'set me'

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

client = SoftLayer.Client()
networkLBaaSL7MemberService = client['SoftLayer_Network_LBaaS_L7Member']

try:
    result = networkLBaaSL7MemberService.updateL7PoolMembers(l7PoolUuid, members)
    pprint(result)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to update severs belonging to a Layer 7 pool: %s, %s"
          % (e.faultCode, e.faultString))
```
