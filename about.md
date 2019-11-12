---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: about, load balancer, overview, features

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

# About IBM Cloud Load Balancer
{: #about-ibm-cloud-load-balancer}

The {{site.data.keyword.loadbalancer_full}} service helps customers improve availability of their business-critical applications by distributing traffic among multiple application server instances, and by forwarding traffic to healthy instances only.

## Overview of Features
{: #overview-of-features}

The {{site.data.keyword.loadbalancer_full}} Service offers the following features:

* Public (internet-facing) load balancer
	* Publicly-accessible service through its fully qualified domain name (FQDN)
	* Backend server instances on private subnets
* Internal load balancer
	* Privately-accessible service through its fully qualified domain name (FQDN)
	* Client requests are routed over the private network
	* Backend server instances on private subnets
* Basic load balancing
	* Traffic distribution based on Layer-4 application port information
	* Support for HTTP, HTTPS and TCP-based applications
	* Variety of load balancing methods such as round-robin (RR), weighted round-robin, and least connections
	* Load balancing among virtual server and bare metal compute instances residing locally within a data center
* Server health checks
	* Periodic monitoring of server health to ensure that traffic is forwarded to healthy servers only
	* Layer-4 health checks for TCP ports and Layer-7 health checks for HTTP port
* SSL offload
	* Termination of incoming SSL (HTTPS) traffic using plain-text HTTP communication with backend servers
* Advanced traffic management
	* Client stickiness (session persistence)
	* Maximum connections per virtual port
* Easy management using intuitive graphical interface and API
* Built-in reliability
* Usage-based pricing
* Monitoring
    * Monitors the Throughput, Active Connections and Connection Rate metrics for HTTP, HTTPS, and TCP protocols over user specified time intervals. Refer to [Monitoring Metrics](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer) for additional details.
* Layer 7 Support
    * HTTP/HTTPS traffic is routed to different backend services based on the HTTP header, and is done using policies and rules. Rules are used to classify the traffic and are based on the HTTP header fields. When the traffic matches all the rules, an action specified by the policy is taken.
* Multi-Zone Region (MZR) Support
    * Load balancer nodes are instantiated in different data centers of a MZR. Refer to [Multi-Zone Region Overview](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview) for more information.
* Data Logs
    * With data logs enabled, load balancer logs will be forwarded to the [IBM Cloud Log Analysis Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}. Customers can view their data logs using [IBM Cloud Log Analysis Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}.
