---

copyright:
  years: 2017, 2024
lastupdated: "2024-08-05"

keywords: options, load balancing, configure, protocol, health check

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Selecting the service and configuring basic options
{: #configuring-ibm-cloud-load-balancer-basic-parameters}

To begin creating your new {{site.data.keyword.loadbalancer_full}}, select **{{site.data.keyword.loadbalancer_full}}** from the Load Balancer page of the [IBM Cloud catalog](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group), then click **Create**.
{: shortdesc}

When the configuration page appears, follow these steps:

1. Enter the name for the load balancer instance. The fully qualified domain name (FQDN) of the load balancer is based on this name.

2. Enter a description for the load balancer (optional).

3. Select the data center where the load balancer instance is to be created.

	For multi-zone availability, all requirements for MZR must be satisfied.
	{: tip}

4. Select the type of load balancer that you want to create from the options **Public-to-Private, **Private-to-Private**, or **Public-to-Public**. Refer to [{{site.data.keyword.loadbalancer_full}} basics](/docs/loadbalancer-service?topic=loadbalancer-service-ibm-cloud-load-balancer-basics) for details on each type.

5. Select the subnet where you want to deploy your new load balancer.

	This option applies to only **Public-to-Private** and **Private-to-Private** load balancer types. Your load balancer service instance has one of its network interfaces on this subnet. Ensure that your application servers are either on this subnet or reachable from this subnet. If necessary, enable VLAN spanning.
	{: note}

6. Select the allocation of public IPs for the load balancer.

	This option applies to only the **Public-to-Private** load balancer type. If you select **Allocate from a public subnet in this account**, you must have at least two public IPs available in a public subnet in the same data center. Also, ensure that traffic to TCP management port 56501 and your application's own ports are not blocked by firewalls that are deployed on your public VLANs.
	{: note}

## What's next
{: #what-s-next}

[Configuring load-balancing options and placing your order](/docs/loadbalancer-service?topic=loadbalancer-service-configure-load-balancing-parameters-and-place-order).
