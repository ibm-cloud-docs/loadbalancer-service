---

copyright:
  years: 2017, 2025
lastupdated: "2025-04-03"

keywords: create, use, elastic

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Creating a load balancer service overview
{: #creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing}

The {{site.data.keyword.loadbalancer_full}} service helps improve scalability and availability of your business-critical applications. It monitors the health of your application servers, uses smart load-balancing methods to distribute traffic among multiple servers, and dynamically adjusts its system capacity to handle varying traffic load.
{: shortdesc}

In this step-by-step guide, learn how to create and configure a new load balancer service.

Task  | Description
------------- | -------------
[Selecting the service and configuring basic options](/docs/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-basic-parameters) | Configure basic options, such as the name, description, and type of your load balancer.
[Configuring load-balancing options and placing your order](/docs/loadbalancer-service?topic=loadbalancer-service-configure-load-balancing-parameters-and-place-order) | Configure protocols, health checks, and back-end servers.
[Monitoring and managing your service](/docs/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service) | Edit your configuration and monitor your load balancer performance.
{: caption="Configure a load balancer" caption-side="top"}

Mandatory management port 56501 must be allowlisted in order for load balancer provisioning (as well as customer and service triggered operations) to succeed. For more information, refer to this [FAQ](/docs/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#public).
{: important}
