---

copyright:
  years: 2017, 2019
lastupdated: "2019-07-01"

keywords: layer 7 pool

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Layer 7 pool
{: #layer-7-pool}

A Layer 7 (L7) pool is a logical grouping of the servers (members) for handling incoming requests.

The Layer 7 load balancing feature can direct the incoming traffic to different back-end pools based
on the policies and rules. This feature is supported by associating multiple L7 pools with a load balancer. Layer 7 pools are used with the Layer 7 policies whose action is `redirect to pool`.

L7 pools support both HTTP and HTTPS as the back-end protocol.

## Session persistence
{: #session-persistence}

Session persistence can be configured for each Layer 7 pool. For more information, see 
[Advanced traffic management with IBM Cloud Load Balancer](/docs/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer).

## Layer 7 members
{: #layer-7-members}

Back-end servers that are associated with a Layer 7 pool are called Layer 7 members.

The same back-end server can be added multiple times to L7 pools, by specifying a different port number each time.

## Configure health checks
{: #configure-health-checks}

The health check definition is mandatory for each Layer 7 pool. The system pre-populates a default health check configuration for L7 pools.

You can customize these settings to suit your application needs:

* **Interval** - The interval in seconds between two consecutive health check attempts.
* **Timeout** -  The maximum amount of time the system waits for a response to the health check request.
* **MaxRetries** - The maximum number of extra health check attempts that the system makes before declaring the service unhealthy.
* **UrlPath** - The HTTP URL path for the Layer 7 health check.
