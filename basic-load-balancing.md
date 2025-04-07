---

copyright:
  years: 2017, 2025
lastupdated: "2025-04-07"

keywords: basics, load balancing

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Load balancer basics
{: #ibm-cloud-load-balancer-basics}

The {{site.data.keyword.loadbalancer_full}} service distributes traffic among multiple server instances (bare metal and virtual server) that reside locally, within the same data center.
{: shortdesc}

## Public-to-private load balancer
{: #public-private-load-balancer}

A publicly accessible, fully qualified domain name is assigned to your load balancer service instance. Use this domain name to access your applications hosted behind the load balancer service. This domain name can be registered with one or more public IP addresses. The public IP addresses and number of public IP addresses can change over time based on maintenance and scaling activities, which are transparent to users. Back-end compute instances hosting your application must be on an IBM Cloud Private network.

As a good practice, it is recommended that you provision your back-end servers as `private-only`, unless they require direct public connectivity. This practice helps achieve better security, and it preserves your public IP address. The applications that are hosted on these back-end servers are still accessible over public networks by using the load balancer.
{: note}  

There are two ways to allocate public IP addresses to the load balancer:

* **Allocate from IBM system pool:** The default method. This method allocates IP addresses from IBM system pool.

* **Allocate from a public subnet in this account:** This method allocates IP addresses from a public subnet from your account. By default, the subnet selection is automatic. If you are using API, you can select a particular subnet by passing the public subnet ID when placing the order.

## Private-to-private load balancer
{: #private-private-load-balancer}

The internal load balancer is only accessible within the IBM Cloud Private network.

Just like a public-to-private load balancer, your internal load balancer service instance is also assigned a fully qualified domain name. However, this domain name is registered with one or more private IP addresses.

Similar to a public load balancer, the private IP addresses and their numbers can change over time based on maintenance and scaling activities, which are transparent to users.

The back-end compute instances hosting your application must also be on the IBM Cloud private network.
{: note}

## Public-to-public load balancer
{: #public-public-load-balancer}

The public-to-public load balancer is publicly accessible.

Just like other load balancer types, your public-to-public load balancer service instance is assigned a fully qualified domain name. This domain name can be registered with one or more public IP addresses.

After the load balancer is provisioned, only the public IP addresses of the members in the server tables context are visible. This is applicable for both layer 4 and layer 7 load balancer members.

The public IP addresses and their numbers can change over time based on maintenance and scaling activities, which are transparent to users.

The back-end compute instances hosting your application must be on the IBM Cloud public network.
{: note}

## Front-end and back-end application ports/protocols
{: #front-end-and-back-end-application-ports-protocols}

You can define up to 10 front-end application ports (protocols) and map them to respective ports (protocols) on the back-end application servers. The fully qualified domain name that is assigned to your load balancer service instance and the front-end application ports are exposed to the external world. The incoming user requests are received on these ports.

The back-end ports are only known internally. These back-end ports might or might not be the same as the front-end ports. As an example, the load balancer can be configured to receive incoming web/HTTP traffic on front-end port 80, while the back-end servers are listening on custom port 81.

The supported front-end ports/protocols are HTTP, HTTPS, and TCP. The supported back-end ports/protocols are also HTTP, HTTPS, and TCP. Incoming HTTPS traffic must be terminated at the load balancer to allow for plain text HTTP communication with the back-end server. If the back-end protocol is HTTPS, the traffic is encrypted between load balancer and back-end servers.

### Considerations
{: #basic-considerations}

* During the initial configuration, you can define up to two front-end ports only. After a load balancer is created, you can edit the port configuration to define extra ports, up to the maximum of 10 ports.
* All 10 front-end ports must map to the same set of back-end server instances.
* The maximum number of server instances that can be placed behind a load balancer is 50.
* The port range of 56500 to 56520 is reserved for management purposes and cannot be used as front-end virtual ports.
* TCP port 56501 is used for management. If you choose to allocate load balancer public IP addresses from your public VLAN, ensure that traffic to this management port as well as your application's ports are not blocked by any firewalls you might have deployed on your public VLANs. This is not required if you choose the IBM system pool option to allocate load balancer public IP addresses.

## Load-balancing methods
{: #load-balancing-methods}

The following three load-balancing methods are available for distributing traffic among back-end application servers:

* **Round Robin** - Round Robin is the default load-balancing method. With this method, the load balancer forwards incoming client connections in round-robin fashion to the back-end servers. As a result, all back-end servers receive roughly an equal number of client connections.

* **Weighted Round Robin** - With this method, the load balancer forwards incoming client connections to the back-end servers in proportion to the weight assigned to these servers. Each server is assigned a default weight of 50, which you can customize to any value in the range 0 - 100.

	As an example, if there are three application servers A, B and C, and their weights are customized to 60, 60 and 30 respectively, then servers A and B receive an equal number of connections, while server C receives half that number of connections.

	Resetting a server weight to 0 means that no new connections are forwarded to that server, but any existing traffic continues to flow as long as it is active. Using a weight of 0 can help bring down a server gracefully and remove it from service rotation.
	{: note}

	The server weight values are applicable only with the weighted round robin method. Server weight values are ignored with round-robin and least connection load-balancing methods.
	{: note}

* **Least Connections** - With this method, the server instance serving the least number of connections at a given time receives the next client connection.

## Horizontal scaling
{: #horizontal-scaling}

The load balancer adjusts its capacity automatically according to the load. When this occurs, you might see a change in the number of IP addresses associated with the load balancer's DNS name.

## Multizone region requirements
{: #mzr-requirements}

A Multizone Region (MZR) ensures high availability by deploying your load balancer appliances in multiple data centers. When you create a load balancer, you select the subnet for deployment. If the data center is part of an MZR, one appliance is deployed in your selected data center, and the other is deployed in a different data center within the same region.

For example, `us-south` is an MZR, which contains the data centers `dal10`, `dal12`, `dal13`. You have a subnet A in `dal10`, subnets B and C in `dal12` and subnets D and E in `dal13`. If you create a load balancer in a data center `dal13`, the first appliance gets deployed in `dal13` while the second gets deployed in the subnet with the most available IPs between `dal10` or `dal12` data centers.

Currently, the **Cloud Load Balancer** service is available in the data centers listed in [Classic infrastructure](/docs/overview?topic=overview-services_region#iaas-service-infra). 

MZRs have the following requirements:

* The selected data center must be part of an MZR.  
* VLAN spanning or VRF must be enabled in your account.
* Private subnets must exist in your account in the data centers of the MZR. Creation of compute devices in data centers results in the instantiation of private subnets.

If the selected data center is not part of an MZR, or if VLAN spanning or VRF is not enabled in your account, the load balancer will be created with all nodes instantiated in the specified data center, following the original deployment behavior.
{: note}

For more information about multizone regions, see [IBM Cloud region and data center locations for resource deployment](/docs/overview?topic=overview-locations). For information about the mapping between regions and zones, see [Zone mapping per account](/docs/overview?topic=overview-locations#zone-mapping).
