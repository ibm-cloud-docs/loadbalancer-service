---

copyright:
  years: 2017, 2020
lastupdated: "2021-09-14"

keywords: about, fqdn, http, https, tcp, features, logs, layer 7, monitoring, health checks

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
   * Variety of load-balancing methods, such as round robin, weighted round robin, and least connections
   * Load balancing among virtual server and bare metal compute instances residing locally within a data center
* Server health checks
   * Periodic monitoring of server health to ensure that traffic is forwarded to healthy servers only
   * Layer 4 health checks for TCP ports and Layer-7 health checks for HTTP port
* SSL offload: Termination of incoming SSL (HTTPS) traffic that uses plain-text HTTP communication with back-end servers
* Advanced traffic management
   * Client stickiness (session persistence)
   * Maximum connections per virtual port
* Easy management using an intuitive graphical interface and API
* Built-in reliability
* Usage-based pricing
* Monitoring: Monitors the throughput, active connections and connection rate metrics for HTTP, HTTPS, and TCP protocols over user-specified time intervals.
* Layer 7 support
   * HTTP/HTTPS traffic is routed to different back-end services based on the HTTP header, and is done by using policies and rules. Rules are used to classify the traffic and are based on the HTTP header fields. When the traffic matches all the rules, an action that is specified by the policy is taken.
* Multi-Zone Region (MZR) support: Load balancer nodes are instantiated in different data centers of an MZR. For more information, see [Multi-Zone Region overview](/docs/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).
* Data Logs: With data logs enabled, load balancer logs are forwarded to the [IBM Log Analysis](https://cloud.ibm.com/catalog/services/ibm-log-analysis-with-logdna){: external} where customers can view their data logs.
