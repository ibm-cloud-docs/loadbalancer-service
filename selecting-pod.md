---

copyright:
  years: 2017, 2025
lastupdated: "2025-05-08"

keywords: pod, vlan, subnet, location, selection, point of delivery

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Selecting Point of Delivery (PoD) based locations by using the CLI and API
{: #selecting-pod}

Each physical data center location in {{site.data.keyword.cloud}} is divided into multiple, discrete networking LANs, otherwise known as PoDs. Each of these has its own separate network infrastructure, a limited number of VLANs, as well as public and private IP subnets. These VLANs and subnets are shared by all clients that have compute capacity that is provisioned within that PoD space.
{: shortdesc}

Currently, you can use the UI to select the deploying data center location at the specific zone, such as `tok02`. You can also select the deploying VLAN and subnet when you have the existing one. However, you cannot specify PoD-based locations except for a gateway appliance and VLAN in the console.

Because you cannot specify PoD locations, and there is no VLAN or subnets, your provisioning can be distributed over multiple PoDs, which can be problematic.

To prevent this issue, you can order a "Premium VLAN" in advance, then specify it as your network VLAN; however, this option incurs an extra cost.

A better option is to use the CLI and API.

## Using the CLI and API to specify PoD
{: #pod-cli-api}

You can use the CLI and API to specify PoD using the following option:

```sh
--extras '{"virtualGuests": [{"hostname": "test", "domain": "softlayer.com", "primaryBackendNetworkComponent": {"router": {"id": 1673467}}}]}'
```
{: codeblock}

The `primaryBackendNetworkComponentId` can be obtained through the following API call:

```sh
slcli call-api SoftLayer_Network_Pod getAllObjects
```
{: codeblock}
