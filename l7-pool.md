---

copyright:
  years: 2017, 2019
lastupdated: "2019-07-01"

keywords: layer 7 pool

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


# Layer 7 pool
{: #layer-7-pool}

A Layer 7 (L7) pool is a logical grouping of the servers (members) for handling incoming requests.

The Layer 7 load balancing feature can direct the incoming traffic to different back-end pools based
on the policies and rules. This feature is supported by associating multiple L7 pools with a load balancer. Layer 7 pools are used with the Layer 7 policies whose action is `redirect to pool`.

   ![Layer 7 Add Pool](images/Layer7-AddPool.png "Layer 7 Add Pool")

L7 pools support both HTTP and HTTPS as the back-end protocol.

   ![Layer 7 Pool](images/Layer7-Pool.png "Layer 7 Pool")


## Session persistence
{: #session-persistence}

Session persistence can be configured for each Layer 7 pool. For more information, see 
[Advanced traffic management with IBM Cloud Load Balancer](/docs/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer).

## Layer 7 members
{: #layer-7-members}

Back-end servers that are associated with a Layer 7 pool are called Layer 7 members.

   ![Layer 7 Add Servers](images/Layer7-AddServers.png "Layer 7 Add Servers")

The same back-end server can be added multiple times to L7 pools, by specifying a different port number each time.

   ![Layer 7 Pool members](images/Layer7-PoolMembers.png "Layer 7 Pool members")


## Configure health checks
{: #configure-health-checks}

The health check definition is mandatory for each Layer 7 pool. The system pre-populates a default health check configuration for L7 pools.

   ![Layer 7 Add health check](images/Layer7-AddHealthCheck.png "Layer 7 Add health check")

You can customize these settings to suit your application needs:

* **Interval** - The interval in seconds between two consecutive health check attempts.
* **Timeout** -  The maximum amount of time the system waits for a response to the health check request.
* **MaxRetries** - The maximum number of additional health check attempts that the system makes before declaring the service unhealthy.
* **UrlPath** - The HTTP URL path for the Layer 7 health check.

   ![Layer 7 HealthCheck](images/Layer7-HealthCheck.png "Layer 7 HealthCheck")
