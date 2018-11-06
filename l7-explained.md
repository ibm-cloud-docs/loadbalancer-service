---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-30"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Layer-7 Load Balancing
The IBM Cloud Load Balancer Service distributes traffic among multiple server instances, including bare-metal and virtual-server instances, using Layer-7 (application layer) data. 

 * The data traffic to be distributed is classified using policies and rules. 
 * Policies define what action to take when the data traffic matches all the rules associated with a policy.
 * Layer-7 (L7) load balancing is supported for HTTP and HTTPS traffic only.

## Layer-7 Policies and Rules 
A Layer-7 policy is associated with a front-end application port. Multiple policies can be associated with a front-end port. 

 * These policies are evaluated in order, based on the priority assigned to each policy. 
 * An associated action is taken when the policy is matched.
 * Each L7 rule is associated with a policy. 
 * If all the rules associated with the policy evaluate to `true`, the policy is matched, so the associated action is taken.

Refer to [L7 Policy and Rules](l7-policy.html) for additional details.

## Layer-7 Pools
Each Layer-7 load balancer pool contains one or more logical server instances. 

 * Each logical server instance is identified by an IP address and port number. 
 * Each pool has a health monitor associated with it, which monitors the health of all the servers in the pool.
 * A pool can be configured for session persistence. 
 * Use the source IP address of the client to configure session persistence.

Refer to [L7 Pools](l7-pool.html) for additional details.