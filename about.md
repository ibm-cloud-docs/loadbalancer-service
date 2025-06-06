---

copyright:
  years: 2017, 2025
lastupdated: "2025-04-23"

keywords: about, fqdn, http, https, tcp, features, logs, layer 7, monitoring, health checks

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# About IBM Cloud Load Balancer
{: #about-ibm-cloud-load-balancer}

The {{site.data.keyword.loadbalancer_full}} service offers the following features:
{: shortdesc}

* Public (internet-facing) load balancer
   * Publicly accessible service through its fully qualified domain name (FQDN)
   * Back-end server instances on private subnets
* Internal load balancer
   * Privately accessible service through its fully qualified domain name (FQDN)
   * Client requests are routed over the private network
   * Back-end server instances on private subnets
* Basic load balancing
   * Traffic distribution based on layer 4 application port information
   * Support for HTTP, HTTPS, and TCP-based applications
   * A variety of load-balancing methods, such as round robin, weighted round robin, and least connections
   * Load balancing among virtual server and bare metal compute instances that reside locally within a data center
* Server health checks
   * Periodic monitoring of server health to ensure that traffic is forwarded to healthy servers only
   * Layer 4 health checks for TCP ports and Layer-7 health checks for HTTP ports
* SSL offload: Termination of incoming SSL (HTTPS) traffic that uses plain-text HTTP communication with back-end servers
* Advanced traffic management
   * Client stickiness (session persistence)
   * Maximum connections per virtual port
* Easy management that uses an intuitive graphical interface and API
* Built-in reliability
* Usage-based pricing
* Monitoring: Monitors the throughput, active connections and connection rate metrics for HTTP, HTTPS, and TCP protocols over user-specified time intervals.
* Layer 7 support
   * HTTP/HTTPS traffic is routed to different back-end services based on the HTTP header, and is done by using policies and rules. Rules are used to classify the traffic and are based on the HTTP header fields. When the traffic matches all the rules, an action that is specified by the policy is taken.
* Multi-Zone Region (MZR) support: Load balancer nodes are instantiated in different data centers of an MZR. For more information, see [Multi-Zone Region overview](/docs/loadbalancer-service?topic=loadbalancer-service-ibm-cloud-load-balancer-basics#multi-zone-region-mzr-overview).

## Pricing metrics
{: #lb-pricing-metrics}

IBM Cloud Load Balancer determines its pricing based on the following metrics.

*Instance hour per month:* Measures the number of hours CLB is used per calendar month.

*Data Processed:* Measures how much data, in gigabytes (GB), that is processed per calendar month.

*Bandwidth Usage:* Measures the amount of bandwidth, in gigabytes (GB), used per calendar month.

This pricing metric has multiple pricing tiers that differ based on the amount of data used.
{: note}

You can estimate the cost of a service by using the cost estimator on the provisioning pages for IBM Cloud Load Balancer. Select **{{site.data.keyword.loadbalancer_full}}** from the Load Balancer page of the [IBM Cloud catalog](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group), then click **Create**.
{: tip}
