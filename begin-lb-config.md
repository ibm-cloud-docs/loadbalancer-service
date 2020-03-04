---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: parameters, load balancing, configure, protocol, health check

subcollection: loadbalancer-service


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Selecting the service and configuring basic parameters
{: #configuring-ibm-cloud-load-balancer-basic-parameters}

To begin creating your new {{site.data.keyword.loadbalancer_full}}, select **{{site.data.keyword.loadbalancer_full}}** from the Load Balancer page of the [IBM Cloud Catalog](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group), then click **Create**.

![CLB select service](images/CLB_Select_Service_PUP.png "CLB select service")

When the configuration screen appears, perform the following procedure:

1. Enter the name for the load balancer instance. The FQDN of the load balancer will be based on this name.

	![CLB Basic Parameters](images/CLB_Basic_Parameters_PUP.png "CLB Basic Parameters")

2. Enter a description for the load balancer (optional).

3. Select the datacenter where the load balancer instance will be created.

	For multi-zone availability, all requirements for [MZR](/docs/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview) must be satisfied.
	{: tip}

4. Select the type of load balancer you want to create from the options **Public to Private** , **Private to Private** or **Public to Public**. Refer to [{{site.data.keyword.loadbalancer_full}} Basics](/docs/loadbalancer-service?topic=loadbalancer-service-ibm-cloud-load-balancer-basics) for details on each type.

5. Select the subnet where you want to deploy your new load balancer.

	This option only applies to **Public to Private** and **Private to Private** load balancer types. Your load balancer service instance will have one of its network interfaces on this subnet. Ensure that your application servers are either on this subnet or reachable from this subnet. If necessary, enable VLAN spanning.
	{: note}

6. Select the allocation of Public IP's for the load balancer.

	This option only applies to **Public to Private** load balancer type. If you select the option **Allocate from a public subnet in this account** you must ensure that you have at least two public IP's available in a public subnet in the same datacenter. In addition, ensure that traffic to TCP management port 56501, as well as your application's own ports, are not blocked by firewalls deployed on your public VLANs.
	{: note}

## What's next
{: #what-s-next}

[Configure load balancing parameters and place your order](/docs/loadbalancer-service?topic=loadbalancer-service-configure-load-balancing-parameters-and-place-order).
