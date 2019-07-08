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

# Référence d'API
{: #api-reference}

L'interface de programmation SoftLayer® permet aux développeurs et aux administrateurs système d'interagir directement avec le système back end de SoftLayer.

L'API SoftLayer (SLAPI) offre un grand nombre de fonctionnalités du portail client. Si une interaction est disponible dans le portail client, elle peut également être exécutée dans l'API. Ainsi, puisque vous pouvez interagir à l'aide d'un programme avec toutes les parties de l'environnement SoftLayer au sein de l'API, vous pouvez utiliser cette dernière pour automatiser des tâches.

L'API SoftLayer (SLAPI) est un système à appel de procédure distante. Chaque appel implique l'envoi de données vers un noeud final d'API et la réception de données structurées en retour. Le format utilisé pour l'envoi et la réception de données à l'aide de SLAPI dépend de l'implémentation que vous avez choisie. L'interface SLAPI utilise actuellement SOAP, XML-RPC ou REST pour la transmission de données.

Pour plus d'informations sur l'API SoftLayer et les API du service IBM© Cloud Load Balancer, voir les ressources suivantes dans le réseau de développement SoftLayer :
* [Getting Started with the SoftLayer API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/article/getting-started/){: new_window}
* [SoftLayer_Product_Package API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Product_Package/){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_LoadBalancer/){: new_window}
* [SoftLayer_Network_LBaaS_Listener API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Listener/){: new_window}
* [SoftLayer_Network_LBaaS_Member API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_Member/){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_HealthMonitor/){: new_window}
* [SoftLayer_Network_LBaaS_SSLCipher API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_SSLCipher/){: new_window}
* [SoftLayer_Network_LBaaS_L7Policy API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Policy/){: new_window}
* [SoftLayer_Network_LBaaS_L7Rule API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Rule/){: new_window}
* [SoftLayer_Network_LBaaS_L7Pool API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Pool/){: new_window}
* [SoftLayer_Network_LBaaS_L7Member API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://softlayer.github.io/reference/services/SoftLayer_Network_LBaaS_L7Member/){: new_window}

Les exemples suivants utilisent le client [softlayer-python ![Icône de lien extern](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/softlayer/softlayer-python){: new_window}.

Définissez un nom d'utilisateur d'API et une clé d'API comme suit pour chaque exemple si aucun fichier `~/.softlayer` n'est configuré dans votre environnement.

```py
client = SoftLayer.Client(username='set me', api_key='set me')
```

## Création d'un équilibreur de charge
{: #creating-a-load-balancer}

L'exemple suivant extrait l'ID de package, l'ID de sous-réseau et les prix d'un package "Equilibreur de charge en tant que service (LBaaS)", génère les données de commande et place/vérifie la commande.

```py
import SoftLayer
from pprint import pprint

class LBaaSExample():
    def __init__(self):
        self.client = SoftLayer.Client()

    def get_package_id(self, pkg_name):
        """Renvoie l'ID de package de LBaaS"""
        _filter = {"name":{"operation": pkg_name}}

        pkg_list = self.client['Product_Package'].getAllObjects(filter=_filter)

        return pkg_list[0]['id']


    def get_item_prices(self, pkg_id):
        """Renvoie les prix standard"""

        item_list = self.client['Product_Package'].getItems(id=pkg_id)
        prices = []

        for item in item_list:
            price_id = [p['id'] for p in item['prices']
                            if not p['locationGroupId']][0]
            prices.append(price_id)

        return prices

    def get_subnet_id(self, datacenter):
        """Trouve et renvoie le premier sous-réseau dans le centre de données"""

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
        """Autorise la commande d'un équilibreur de charge"""

        package_id = self.get_package_id(pkg_name)
        prices = self.get_item_prices(package_id)

        # Trouve et sélectionne un ID de sous-réseau si aucun n'a été indiqué.
        si subnet_id est None :
            subnet_id = self.get_subnet_id(datacenter)

        # Génère la configuration de la commande
        orderData = {
            'complexType': 'SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService',
            'name': name,
            'description': desc,
            'location': datacenter,
            'packageId': package_id,
            'useHourlyPricing': True,       # Requis car LBaaS est un service horaire
            'prices': [{'id': price_id} for price_id in prices],
            'protocolConfigurations': protocols,
            'subnets': [{'id': subnet_id}]
        }

        try:
            # Si verify=True vérification de votre commande à la recherche d'erreurs.
            # Si False lbaas n'est pas commandé.
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

    # Définir sur False pour le réseau privé
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

    # supprimer verify=True pour passer la commande
    receipt = lbaas.order_lbaas(package_name, location, name, description,
                                protocols, public=is_public, verify=True)

    pprint(receipt)
```
{: codeblock}

## Extraction des détails relatifs aux équilibreurs de charge
{: #retrieving-details-on-load-balancers}

### Recensement de tous les équilibreurs de charge
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

        # Utiliser des filtres si le centre de données est défini
        if dc:
            _filter = {"datacenter":{"name":{"operation": dc}}}

        try:
            # Extraire des objets d'équilibreur de charge
            lbaas_list = self.lbaas_service.getAllObjects(filter=_filter)
        except SoftLayer.SoftLayerAPIError as e:
            print("Unable to get the LBaaS list: %s, %s" % (e.faultCode, e.faultString))

        return lbaas_list


if __name__ == "__main__":
    table = PrettyTable(['ID','UUID','Name', 'Description',
                         'Address', 'Type', 'Location', 'Status'])

    # Pour trouver tous les lbaas du centre de données
    de Mexico = "mex01"

    lbaas = LBaasExample()
    # supprimer dc=datacenter pour extraire tous les équilibreurs de charge du compte
    lbaas_list = lbaas.get_list(dc=datacenter)

    # ajouter les données lbaas à la table
    pour i dans lbaas_list:
        isPublic = "Public" if i['isPublic'] == 1 else "Private"
        table.add_row([i['id'], i['uuid'], i['name'], i['description'], i['address'],
                       isPublic,i['datacenter']['longName'],i['operatingStatus']])

    print (table)
```
{: codeblock}

### Obtention des détails relatifs à un équilibreur de charge spécifique
{: #retrieve-details-of-a-specific-load-balancer}

```py
import SoftLayer
from pprint import pprint

# UUID de votre équilibreur de charge
uuid = 'set me'
# masquer pour extraire les programmes d'écoute et moniteurs d'état de l'équilibreur de charge
_mask = "mask[listeners, healthMonitors]"

# Créer le client d'API
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Extraction des détails d'un objet équilibreur de charge
    spécifique = lbaas_service.getLoadBalancer(uuid, mask=_mask)
    pprint(details)
except SoftLayer.SoftLayerAPIError as e:
    print("Unable to retrieve LBaaS details: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## Mise à jour d'un équilibreur de charge
{: #updating-a-load-balancer}

### Ajout d'un membre
{: #add-a-member}

```py
import SoftLayer
from pprint import pprint

# UUID de votre équilibreur de charge
uuid = 'set me'

# Mise à jour avec les adresses IP correctes
serverInstances = [
    { "privateIpAddress": "10.131.11.46", "weight": 80 },
    { "privateIpAddress": "10.131.11.6" } # Default weight=50
]

# Créer le client d'API
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

### Ajout d'un protocole
{: #add-a-protocol}

```py
import SoftLayer
from pprint import pprint

# UUID de votre équilibreur de charge
uuid = 'set me'

# Nouveaux protocoles à ajouter
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

# Créer le client d'API
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

## Annulation d'un équilibreur de charge
{: #cancelling-a-load-balancer}

```py
import SoftLayer

# UUID de votre équilibreur de charge
uuid = 'set me'

# Créer le client d'API
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

## Affichage des métriques de surveillance des équilibreurs de charge
{: #viewing-monitoring-metrics-of-load-balancers}

### Obtention du débit du trafic HTTP
{: #get-throughput-of-http-traffic}

```py
import SoftLayer
from pprint import pprint

# UUID de votre équilibreur de charge
uuid = 'set me'

# Options disponibles : Throughput, ActiveConnections et ConnectionRate.
metric_name = 'Throughput'

# Options : 1hour, 6hours, 12hours, 24hour, 1week ou 2weeks
time_range = '1hour'

# UUID du programme d'écoute dont vous demandez le débit
protocol_uuid = 'set me'

# Créer le client d'API
client = SoftLayer.Client()
lbaas_service = client['Network_LBaaS_LoadBalancer']

try:
    # Supprimer protocol_uuid pour extraire les mesures du trafic de l'intégralité de l'équilibreur de charge
    time_series = lbaas_service.getListenerTimeSeriesData(uuid, metric_name,
                                                          time_range, protocol_uuid)

    pprint(time_series)
except SoftLayer.SoftLayerAPIError as e:            
    print("Unable to retrieve the traffic: %s, %s" % (e.faultCode, e.faultString))
```
{: codeblock}

## API de couche 7
{: #layer-7-apis}

### Création de plusieurs politiques et règles L7
{: #create-multiple-l7-policies-and-l7-rules}

```py
import SoftLayer
from pprint import pprint

# UUID du programme d'écoute
listener_uuid = "set me"

# Génération des règles
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

# Configuration des politiques et règles groupées
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

### Mise à jour des politiques de couche 7
{: #update-layer-7-policy}

```py
import SoftLayer
from pprint import pprint

# ID de la politique à mettre à jour
networkLBaaSL7PolicyId = 11111111

# Mise à jour de la configuration de politique en spécifiant la valeur et le nom de la variable, par ex. "<name>": "<value>"
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

### Ajout de règles à une politique de couche 7
{: #add-rules-to-a-layer-7-policy-}

```py
import SoftLayer
from pprint import pprint

# UUID de la politique de couche 7
policyUuid = "set me"

# Nouvelles règles à ajouter
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

### Mise à jour de plusieurs règles de couche 7 associées à la même politique de couche 7
{: #update-multiple-layer-7-rules-attached-to-the-same-layer-7-policy-}

```py
# Pour une sortie de débogage parfaite :
import SoftLayer
from pprint import pprint

# UUID de la politique de couche 7
policyUuid = "set me"

# Nouvelles règles à ajouter
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

### Création d'un pool de couche 7 avec des serveurs, la surveillance de santé et l'affinité de session
{: #create-a-layer-7-pool-with-servers-health-monitoring-and-session-affinity}

```py
import SoftLayer
from pprint import pprint

# UUID de l'équilibreur de charge à mettre à jour
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

# Moniteur d'état de la couche 7 à ajouter
l7HealthMonitor = {
    'interval': 10,
    'timeout': 5,
    'maxRetries': 3,
    'urlPath': '/'
}

# Affinité de session de couche 7 à ajouter. Ne prend actuellement en charge que SOURCE_IP
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

### Mise à jour d'un pool de couche 7 avec la surveillance de santé et l'affinité de session
{: #update-a-layer-7-pool-along-with-health-monitoring-and-session-affinity}

```py
import SoftLayer
from pprint import pprint

# UUID du pool de couche 7 à mettre à jour
l7PoolUuid = 'set me'

# Nouvelles valeurs du pool de couche 7 à mettre à jour
l7Pool = {'loadBalancingAlgorithm': 'LEASTCONNECTION'}

# Nouvelles valeurs du moniteur d'état de couche 7 à mettre à jour
l7HealthMonitor = {'urlPath': '/index'}

# Nouvelles valeurs d'affinité de session de couche 7 à mettre à jour.
# Si elles ne sont pas indiquées, suppression de l'affinité de session existante
# Si elles sont indiquées et que l'affinité de session n'existe pas, cette dernière est créée.
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

### Ajout de serveurs à un pool de couche 7
{: #add-servers-to-a-layer-7-pool}

```py
import SoftLayer
from pprint import pprint

# UUID du pool de couche 7 pool auquel les membres doivent être ajoutés.
l7PoolUuid = 'set me'

# Backend servers to be added
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

### Mise à jour de serveurs appartenant à un pool de couche 7
{: #update-severs-belonging-to-a-layer-7-pool}

```py
import SoftLayer
from pprint import pprint

# UUID du pool de couche 7 dont un membre doit être mis à jour
l7PoolUuid = 'set me'

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

### Activation ou désactivation des journaux de données pour un équilibreur de charge particulier
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
