---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: api, apis, reference, slapi

subcollection: loadbalancer-service

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
{: #api-reference}

La API de SoftLayer® es la interfaz de desarrollo que permite a los desarrolladores y administradores del sistema interactuar directamente con el sistema de fondo de SoftLayer.

La API de SoftLayer (SLAPI) ofrece muchas de las características del Portal de clientes. Por lo general, si una interacción es posible en el Portal de clientes, también lo es en la API. Por lo tanto, puesto que se puede interactuar mediante programación con todos los componentes del entorno de SoftLayer dentro de la API, es posible utilizar la API para automatizar tareas.

La API de SoftLayer (SLAPI) es un sistema de llamadas de procedimiento remoto. Cada llamada implica el envío de datos a un punto final de API y la recepción de datos estructurados. El formato utilizado para enviar y recibir datos con la SLAPI depende de qué implementación de la API utilice. Actualmente la SLAPI utiliza SOAP, XML-RPC o REST para la transmisión de datos.

Para obtener más información sobre la API SoftLayer, las API del servicio IBM© Cloud Load Balancer, consulte los siguientes recursos en la red de despliegue de SoftLayer:
* [Iniciación a la API de SoftLayer ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/article/getting-started/){: new_window}
* [SoftLayer_Product_Package API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Product_Package/){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_LoadBalancer/){: new_window}
* [SoftLayer_Network_LBaaS_Listener API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Listener/){: new_window}
* [SoftLayer_Network_LBaaS_Member API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Member/){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_HealthMonitor/){: new_window}
* [API SoftLayer_Network_LBaaS_SSLCipher ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_SSLCipher/){: new_window}
* [API SoftLayer_Network_LBaaS_L7Policy ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Policy/){: new_window}
* [API SoftLayer_Network_LBaaS_L7Rule ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Rule/){: new_window}
* [API SoftLayer_Network_LBaaS_L7Pool ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Pool/){: new_window}
* [API SoftLayer_Network_LBaaS_L7Member ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Member/){: new_window}

En los siguientes ejemplos se utiliza el cliente [softlayer-python ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/softlayer/softlayer-python){: new_window}.

Defina un nombre de usuario de api y una apikey del siguiente modo para cada ejemplo en el caso de que no tenga un archivo `~/.softlayer`
configurado en el entorno.

```py
client = SoftLayer.Client(username='set me', api_key='set me')
```

## Creación de un equilibrador de carga
{: #creating-a-load-balancer}

El ejemplo siguiente recupera el ID de paquete, el ID de subred y los precios de un paquete "Load Balancer As A Service (LBaaS)", crea los datos del pedido y realiza y verifica el pedido.

```py
import SoftLayer
from pprint import pprint

class LBaaSExample():
    def __init__(self):
        self.client = SoftLayer.Client()

    def get_package_id(self, pkg_name):
        """Returns the packageId for the LBaaS"""
        _filter = {"name":{"operation": pkg_name}}

        pkg_list = self.client['Product_Package'].getAllObjects(filter=_filter)

        return pkg_list[0]['id']


    def get_item_prices(self, pkg_id):
        """Returns the standard prices"""

        item_list = self.client['Product_Package'].getItems(id=pkg_id)
        prices = []

        for item in item_list:
            price_id = [p['id'] for p in item['prices']
                            if not p['locationGroupId']][0]
            prices.append(price_id)

        return prices

    def get_subnet_id(self, datacenter):
        """Find and returns the first subnet in the datacenter"""

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
        """Allows to order a Load Balancer"""

        package_id = self.get_package_id(pkg_name)
        prices = self.get_item_prices(package_id)

        # Buscar y seleccionar un id de subred si no se ha especificado.
        if subnet_id is None:
            subnet_id = self.get_subnet_id(datacenter)

        # Crear la configuración del pedido
        orderData = {
            'complexType': 'SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService',
            'name': name,
            'description': desc,
            'location': datacenter,
            'packageId': package_id,
            'useHourlyPricing': True,       # Required since LBaaS is an hourly service
            'prices': [{'id': price_id} for price_id in prices],
            'protocolConfigurations': protocols,
            'subnets': [{'id': subnet_id}]
        }

        try:
            # Si verify=True, se comprobará si el pedido contiene errores.
            # Se realizará el pedido de lbaas si el valor es False.
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

    # Establecer en False para red privada
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

    # eliminar verify=True para realizar el pedido
    receipt = lbaas.order_lbaas(package_name, location, name, description,
                                protocols, public=is_public, verify=True)

    pprint(receipt)
```
{: codeblock}

## Recuperación de detalles en equilibradores de carga
{: #retrieving-details-on-load-balancers}

### Lista de todos los equilibradores de carga
{: #list-all-load-balancers}

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

        # Utilizar filtros si el centro de datos está definido
        if dc:
            _filter = {"datacenter":{"name":{"operation": dc}}}

        try:
            # Recuperar objetos del equilibrador de carga
            lbaas_list = self.lbaas_service.getAllObjects(filter=_filter)
        except SoftLayer.SoftLayerAPIError as e:
            print("Unable to get the LBaaS list: %s, %s" % (e.faultCode, e.faultString))

        return lbaas_list


if __name__ == "__main__":
    table = PrettyTable(['ID','UUID','Name', 'Description',
                         'Address', 'Type', 'Location', 'Status'])

    # Para buscar todos los lbaas de México
    datacenter = "mex01"

    lbaas = LBaasExample()
    # eliminar dc=datacenter para recuperar todos los equilibradores de carga de la cuenta
    lbaas_list = lbaas.get_list(dc=datacenter)

    # añadir datos de lbaas a la tabla
    for i in lbaas_list:
        isPublic = "Public" if i['isPublic'] == 1 else "Private"
        table.add_row([i['id'], i['uuid'], i['name'], i['description'], i['address'],
                       isPublic,i['datacenter']['longName'],i['operatingStatus']])

    print (table)
```
{: codeblock}

### Recuperación de detalles de un equilibrador de carga específico
{: #retrieve-details-of-a-specific-load-balancer}

```py
import SoftLayer
from pprint import pprint

# El UUID de su equilibrador de carga
uuid = 'set me'
# máscara para recuperar los escuchas y healthMonitors del equilibrador de carga
_mask = "mask[listeners, healthMonitors]"

# Crear el cliente de api
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Recuperar un objeto de equilibrador de carga específico
    details = lbaas_service.getLoadBalancer(uuid, mask=_mask)
    pprint(details)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to retrieve LBaaS details: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Actualización de un equilibrador de carga
{: #updating-a-load-balancer}

### Adición de un miembro
{: #add-a-member}

```py
import SoftLayer
from pprint import pprint

# El UUID de su equilibrador de carga
uuid = 'set me'

# Actualizar con la dirección IP correcta
serverInstances = [
    { "privateIpAddress": "10.131.11.46", "weight": 80 },
    { "privateIpAddress": "10.131.11.6" } # Default weight=50
]

# Crear el cliente de api
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

### Adición de un protocolo
{: #add-a-protocol}

```py
import SoftLayer
from pprint import pprint

# El UUID de su equilibrador de carga
uuid = 'set me'

# Nuevos protocolos que añadir
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

# Crear el cliente de api
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

## Cancelación de un equilibrador de carga
{: #cancelling-a-load-balancer}

```py
import SoftLayer

# El UUID de su equilibrador de carga
uuid = 'set me'

# Crear el cliente de api
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

## Visualización de la supervisión de métricas de equilibradores de carga
{: #viewing-monitoring-metrics-of-load-balancers}

### Obtención del rendimiento del tráfico HTTP
{: #get-throughput-of-http-traffic}

```py
import SoftLayer
from pprint import pprint

# El UUID del equilibrador de carga
uuid = 'set me'

# Opciones disponibles: Throughput, ActiveConnections y ConnectionRate.
metric_name = 'Throughput'

# Las opciones son: 1hour, 6hours, 12hours, 24hour, 1week o 2weeks
time_range = '1hour'

# UUID del escucha cuyo rendimiento ha solicitado
protocol_uuid = 'set me'

# Crear el cliente de api
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Eliminar protocol_uuid para recuperar métricas de tráfico de todo el equilibrador de carga
    time_series = lbaas_service.getListenerTimeSeriesData(uuid, metric_name,
                                                          time_range, protocol_uuid)

    pprint(time_series)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to retrieve the traffic: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## API de capa 7
{: #layer-7-apis}

### Creación de varias políticas L7 y reglas L7
{: #create-multiple-l7-policies-and-l7-rules}

```py
import SoftLayer
from pprint import pprint

# UUID del escucha
listener_uuid = "set me"

# Crear las reglas
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

# Configuración masiva de políticas y reglas
policies_rules = [
    {
        "l7Policy": {
            "name": "traf_test1",
            "action": "REDIRECT_URL",
            "priority": 101,
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

### Actualización de la política de capa 7
{: #update-layer-7-policy}

```py
import SoftLayer
from pprint import pprint

# El ID de la política que desea actualizar
networkLBaaSL7PolicyId = 11111111

# Actualizar la configuración de la política especificando el nombre y el valor de la variable, por ejemplo "<name>": "<value>"
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

### Adición de reglas a la política de capa 7 
{: #add-rules-to-a-layer-7-policy-}

```py
import SoftLayer
from pprint import pprint

# UUID de la política de capa 7
policyUuid = "set me"

# Nuevas reglas que añadir
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

### Actualización de varias reglas de capa 7 adjuntas a la misma política de capa 7 
{: #update-multiple-layer-7-rules-attached-to-the-same-layer-7-policy-}

```py
# Para obtener salida depurada:
import SoftLayer
from pprint import pprint

# UUID de la política de capa 7
policyUuid = "set me"

# Nuevas reglas que añadir
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

### Creación de una agrupación de capa 7 con servidores, supervisión de estado y afinidad de sesiones
{: #create-a-layer-7-pool-with-servers-health-monitoring-and-session-affinity}

```py
import SoftLayer
from pprint import pprint

# UUID del equilibrador de carga que se va a actualizar
loadBalancerUuid = "set me"

# Agrupación de capa 7 que se va a añadir
l7Pool = {
    'name': 'image_pool',
    'protocol': 'HTTP',  # only supports HTTP
    'loadBalancingAlgorithm': 'ROUNDROBIN'
}

# Servidores de fondo de capa 7 que se van a añadir
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

# Supervisor de estado de capa 7 que se va a añadir
l7HealthMonitor = {
    'interval': 10,
    'timeout': 5,
    'maxRetries': 3,
    'urlPath': '/'
}

# Afinidad de sesión de capa 7 que se va a añadir. Actualmente solo se da soporte a SOURCE_IP
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

### Actualización de una agrupación de capa 7 con supervisión de estado y afinidad de sesiones
{: #update-a-layer-7-pool-along-with-health-monitoring-and-session-affinity}

```py
import SoftLayer
from pprint import pprint

# UUID de la agrupación L7 que se va a actualizar
l7PoolUuid = 'set me'

# Valores de la agrupación de capa 7 que se va a actualizar
l7Pool = {'loadBalancingAlgorithm': 'LEASTCONNECTION'}

# Nuevos del supervisor de estado de capa 7 que se va a actualizar
l7HealthMonitor = {'urlPath': '/index'}

# Nuevos valores de afinidad de sesión de capa 7 que se va a actualizar.
# Si no se especifican, se suprime la afinidad de sesión existente
# Si se especifican y la afinidad de sesión no existe, se crea una.
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

### Adición de servidores a una agrupación de capa 7
{: #add-servers-to-a-layer-7-pool}

```py
import SoftLayer
from pprint import pprint

# UUID de la agrupación L7 al que se deben añadir miembros.
l7PoolUuid = 'set me'

# Servidores de fondo que se van a añadir
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

### Actualización de los servidores que pertenecen a una agrupación de capa 7
{: #update-severs-belonging-to-a-layer-7-pool}

```py
import SoftLayer
from pprint import pprint

# UUID de la agrupación L7 cuyo miembro hay que actualizar
l7PoolUuid = 'set me'

# Servidores de fondo que se van a añadir
members = [
    {
        'uuid': '1e433123-ceae-4bbd-a4e3-2539ceb8b46f',  # UUID del miembro que se va a actualizar.
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
{: codeblock}

### Habilitar o inhabilitar registros de datos de un equilibrador de carga específico
{: #enable-or-disable-data-logs-for-a-specific-load-balancer}

```py
desde el cliente zeep import, xsd

# Username and apikey for SLAPI call
username = ''
apiKey = ''
# UUID of the load balancer
uuid = ''
# enabled = 1 when enable, enable = 0 when disable
enabled = 0

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

# Enable or disable data logs for a specific load balancer
loadbalancer = client.service.enableOrDisableDataLogs(_soapheaders=[userAuthValue], uuid=uuid, enabled=enabled)
#print loadbalancer
```
