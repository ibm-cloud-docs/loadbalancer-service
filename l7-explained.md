---

copyright:
  years: 2017, 2019
lastupdated: "2019-07-01"

keywords: l7, layer 7

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Layer 7 load balancing
{: #layer-7-load-balancing}

The {{site.data.keyword.loadbalancer_full}} service distributes traffic among multiple server instances, including bare-metal and virtual-server instances, by using Layer 7 (application layer) data.
{: shortdesc}

* The data traffic to be distributed is classified by using policies and rules.
* Policies define what action to take when the data traffic matches all the rules that are associated with a policy.
* Layer 7 (L7) load balancing is supported for HTTP and HTTPS traffic only.

## Layer 7 policies and rules
{: #layer-7-policies-and-rules}

A Layer 7 policy is associated with a front-end application port. Multiple policies can be associated with a front-end port.

* These policies are evaluated in order, based on the priority assigned to each policy.
* An associated action is taken when the policy is matched.
* Each L7 rule is associated with a policy.
* If all the rules that are associated with the policy evaluate to `true`, the policy is matched, so the associated action is taken.

For more information, see [L7 Policy and Rules](/docs/loadbalancer-service?topic=loadbalancer-service-layer-7-policy).

## Layer 7 pools
{: #layer-7-pools}

Each Layer 7 load balancer pool contains one or more logical server instances.

* Each logical server instance is identified by an IP address and port number.
* Each pool has a health monitor associated with it, which monitors the health of all the servers in the pool.
* A pool can be configured for session persistence.
* Use the source IP address of the client or HTTP cookie to configure session persistence.

For more information, see [L7 Pools](/docs/loadbalancer-service?topic=loadbalancer-service-layer-7-pool).
