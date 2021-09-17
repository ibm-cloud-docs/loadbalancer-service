---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: slapi

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:term: .term}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:table: .aria-labeledby="caption"}
{:generic: data-hd-programlang="generic"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}


# IBM Cloud Load Balancer API reference
{: #api-reference}

The SoftLayer application programming interface (API) is the development interface that gives developers and system administrators direct interaction with the SoftLayer back-end system.
{: shortdesc}

The SoftLayer API (SLAPI) powers many of the features in the Customer Portal. Generally, if an interaction is possible in the Customer Portal, it can also be run in the API. Because you can programmatically interact with all portions of the SoftLayer environment within the API, you can use the API to automate tasks.

The SLAPI is a Remote Procedure Call system. Each call involves sending data towards an API endpoint and receiving structured data in return. The format used to send and receive data with the SLAPI depends on which implementation of the API you choose. The SLAPI currently uses SOAP, XML-RPC or REST for data transmission.

For more information about the SoftLayer API, {{site.data.keyword.loadbalancer_full}} Service APIs, see the following resources in the SoftLayer Development Network:
* [Getting Started with the SoftLayer API](https://softlayer.github.io/article/getting-started/){: external}
* [SoftLayer_Product_Package API](https://softlayer.github.io/reference/services/SoftLayer_Product_Package/){: external}
* [SoftLayer_Network_LBaaS_LoadBalancer API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_LoadBalancer/){: external}
* [SoftLayer_Network_LBaaS_Listener API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Listener/){: external}
* [SoftLayer_Network_LBaaS_Member API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Member/){: external}
* [SoftLayer_Network_LBaaS_HealthMonitor API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_HealthMonitor/){: external}
* [SoftLayer_Network_LBaaS_SSLCipher API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_SSLCipher/){: external}
* [SoftLayer_Network_LBaaS_L7Policy API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Policy/){: external}
* [SoftLayer_Network_LBaaS_L7Rule API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Rule/){: external}
* [SoftLayer_Network_LBaaS_L7Pool API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Pool/){: external}
* [SoftLayer_Network_LBaaS_L7Member API](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Member/){: external}

The following examples are using [softlayer-python](https://github.com/softlayer/softlayer-python){: external} client.

Set an api username and apikey as following for each example in case you don't have a `~/.softlayer` file that is configured in your environment.

```py
client = SoftLayer.Client(username='set me', api_key='set me')
```

## Creating a load balancer
{: #creating-a-load-balancer}

The following example retrieves the package ID, subnet ID, and prices for a "Load Balancer As A Service (LBaaS)" package, builds the order data and places the order.

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

        # Find and select a subnet id if it was not specified.
        if subnet_id is None:
            subnet_id = self.get_subnet_id(datacenter)

        # Build the configuration of the order
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
            # If verify=True it checks your order for errors.
            # It orders the lbaas if False.
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

    # Set False for private network
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

    # remove verify=True to place the order
    receipt = lbaas.order_lbaas(package_name, location, name, description,
                                protocols, public=is_public, verify=True)

    pprint(receipt)
```
{: codeblock}


## Order a public to private load balancer with specified public subnet
{: #Order-a-load-balancer-with-specified-public-subnet}

The following example focuses on the order data that is required to create a load balancer with a specified public subnet. It is only valid for public to private load balancer types, and `useSystemPublicIpPool` must be `false`.

```py
import SoftLayer
from prettytable import PrettyTable

class LBaasExample():
  ...
  def order_lbaas(self, pkg_name, datacenter, name, desc, protocols,
                  subnet_id=None, public_subnet_id=None, public=False, verify=False):
      """Allows to order a Load Balancer"""

      package_id = self.get_package_id(pkg_name)
      prices = self.get_item_prices(package_id)

      # Build the configuration of the order
      orderData = {
          'complexType': 'SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService',
          'name': name,
          'description': desc,
          'location': datacenter,
          'packageId': package_id,
          'useHourlyPricing': True,       # Required since LBaaS is an hourly service
          'prices': [{'id': price_id} for price_id in prices],
          'protocolConfigurations': protocols,
          'subnets': [{'id': subnet_id}],
          'useSystemPublicIpPool': False,
          'type': 1, # public to private load balancer
          'publicSubnets': [{'id': publicSubnet_id}]
      }

      try:
          # If verify=True it checks your order for errors.
          # It orders the lbaas if False.
          if verify:
              response = self.client['Product_Order'].verifyOrder(orderData)
          else:
              response = self.client['Product_Order'].placeOrder(orderData)

          return response
      except SoftLayer.SoftLayerAPIError as e:
          print("Unable to place the order: %s, %s" % (e.faultCode, e.faultString))
    ...
```
{: codeblock}

## Retrieving details on load balancers
{: #retrieving-details-on-load-balancers}

### List all load balancers
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

        # Use filters if datacenter is set
        if dc:
            _filter = {"datacenter":{"name":{"operation": dc}}}

        try:
            # Retrieve load balancer objects
            lbaas_list = self.lbaas_service.getAllObjects(filter=_filter)
        except SoftLayer.SoftLayerAPIError as e:            
            print("Unable to get the LBaaS list: %s, %s" % (e.faultCode, e.faultString))

        return lbaas_list


if __name__ == "__main__":
    table = PrettyTable(['ID','UUID','Name', 'Description',
                         'Address', 'Type', 'Location', 'Status'])

    # To find all lbaas in Mexico
    datacenter = "mex01"

    lbaas = LBaasExample()
    # remove dc=datacenter to retrieve all the load balancers in the account
    lbaas_list = lbaas.get_list(dc=datacenter)

    # add lbaas data to the table
    for i in lbaas_list:
        isPublic = "Public" if i['isPublic'] == 1 else "Private"
        table.add_row([i['id'], i['uuid'], i['name'], i['description'], i['address'],
                       isPublic,i['datacenter']['longName'],i['operatingStatus']])

    print (table)
```
{: codeblock}

### Retrieve details of a specific load balancer
{: #retrieve-details-of-a-specific-load-balancer}

```py
import SoftLayer
from pprint import pprint

# Your load balancer UUID
uuid = 'set me'
# mask to retrieve the load balancer's listeners and healthMonitors
_mask = "mask[listeners, healthMonitors]"

# Create the api client
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Retrieve a specific load balancer object
    details = lbaas_service.getLoadBalancer(uuid, mask=_mask)
    pprint(details)
except SoftLayer.SoftLayerAPIError as e:            
    print("Unable to retrieve LBaaS details: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Updating a load balancer
{: #updating-a-load-balancer}

### Add a member
{: #add-a-member}

```py
import SoftLayer
from pprint import pprint

# Your load balancer UUID
uuid = 'set me'

# Update with the correct IP addresses
serverInstances = [
    { "privateIpAddress": "10.131.11.46", "weight": 80 },
    { "privateIpAddress": "10.131.11.6" } # Default weight=50
]

# Create the api client
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

### Add a protocol
{: #add-a-protocol}

```py
import SoftLayer
from pprint import pprint

# Your load balancer UUID
uuid = 'set me'

# New protocols to add
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
        "sessionType": "SOURCE_IP",
        "serverTimeout": 70,
        "clientTimeout": 70
    }
]

# Create the api client
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

### Update a protocol
{: #update-a-protocol}

```py
import SoftLayer
from pprint import pprint

# Your load balancer UUID
uuid = 'set me'

# New protocols to add
protocolConfigurations = [
    {   
        "listenerUuid": "69fad83a-e850-4b72-a4d3-af94d5bf5437",
        "serverTimeout": 60,
        "clientTimeout": 60
    },
    {   
        "listenerUuid": "e4b8cfd0-1e27-4d3e-a8ed-595b198cd683",
        "frontendPort": 1450,
        "maxConn": 1002,
        "serverTimeout": 80,
        "clientTimeout": 80
    }
]

# Create the api client
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

## Canceling a load balancer
{: #cancelling-a-load-balancer}

```py
import SoftLayer

# Your load balancer UUID
uuid = 'set me'

# Create the api client
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

## Viewing monitoring metrics of load balancers
{: #viewing-monitoring-metrics-of-load-balancers}

### Get throughput of HTTP traffic
{: #get-throughput-of-http-traffic}

```py
import SoftLayer
from pprint import pprint

# UUID of load balancer
uuid = 'set me'

# Avaiable options: Throughput, ActiveConnections, and ConnectionRate.
metric_name = 'Throughput'

# Options are: 1hour, 6hours, 12hours, 24hour, 1week, or 2weeks
time_range = '1hour'

# UUID of the listener whose throughput your requesting
protocol_uuid = 'set me'

# Create the api client
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Remove protocol_uuid to retrieve the traffic metrics of the entire load balancer
    time_series = lbaas_service.getListenerTimeSeriesData(uuid, metric_name,
                                                          time_range, protocol_uuid)

    pprint(time_series)
except SoftLayer.SoftLayerAPIError as e:            
    print("Unable to retrieve the traffic: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Layer 7 APIs
{: #layer-7-apis}

### Create Multiple L7 policies and L7 rules
{: #create-multiple-l7-policies-and-l7-rules}

```py
import SoftLayer
from pprint import pprint

# UUID of the listener
listener_uuid = "set me"

# Build the rules
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

# Bulk policies and rules configuration
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

### Update Layer 7 policy
{: #update-layer-7-policy}

```py
import SoftLayer
from pprint import pprint

# The ID of policy you want to update
networkLBaaSL7PolicyId = 11111111

# Update policy configuration by specifying the variable name and value , e.g. "<name>": "<value>"
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

### Add rules to a Layer 7 policy 
{: #add-rules-to-a-layer-7-policy-}

```py
import SoftLayer
from pprint import pprint

# UUID of the Layer 7 policy
policyUuid = "set me"

# New rules to add
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

### Update multiple Layer 7 rules that are attached to the same Layer 7 policy
{: #update-multiple-layer-7-rules-attached-to-the-same-layer-7-policy-}

```py
# For nice debug output:
import SoftLayer
from pprint import pprint

# UUID of the Layer 7 policy
policyUuid = "set me"

# New rules to add
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

### Create a Layer 7 pool with servers, health monitoring, and session affinity
{: #create-a-layer-7-pool-with-servers-health-monitoring-and-session-affinity}

```py
import SoftLayer
from pprint import pprint

# UUID of load balancer to be updated
loadBalancerUuid = "set me"

# Layer 7 pool to be added
l7Pool = {
    'name': 'image_pool',
    'protocol': 'HTTP',  # only supports HTTP
    'loadBalancingAlgorithm': 'ROUNDROBIN'
}

# Layer 7 Backend servers to be added
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

### Update a Layer 7 pool along with health monitoring and session affinity
{: #update-a-layer-7-pool-along-with-health-monitoring-and-session-affinity}

```py
import SoftLayer
from pprint import pprint

# UUID of L7 pool to be updated
l7PoolUuid = 'set me'

# New Layer 7 pool values to be updated
l7Pool = {'loadBalancingAlgorithm': 'LEASTCONNECTION'}

# New Layer 7 Health monitor values to be updated
l7HealthMonitor = {'urlPath': '/index'}

# New Layer 7 session affinity values to be updated.
# If not given it deletes the existing session affinity
# If given and session affinity doesn't exist, it creates one.
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

### Add servers to a Layer 7 Pool
{: #add-servers-to-a-layer-7-pool}

```py
import SoftLayer
from pprint import pprint

# UUID of the L7 pool to which members should be added.
l7PoolUuid = 'set me'

# Back-end servers to be added
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

### Update severs belonging to a Layer 7 pool
{: #update-severs-belonging-to-a-layer-7-pool}

```py
import SoftLayer
from pprint import pprint

# UUID of the L7 pool who's member we need to update
l7PoolUuid = 'set me'

# Back-end servers to be added
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

### Enable or disable data logs for a specific load balancer
{: #enable-or-disable-data-logs-for-a-specific-load-balancer}

```py
from zeep import Client, xsd

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
