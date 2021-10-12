---

copyright:
  years: 2017, 2020
lastupdated: "2020-10-15"

keywords: pod, vlan, subnet, location, selection, point of delivery

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

# Selecting Point of Delivery (PoD) based locations using the CLI and API
{: #selecting-pod}

Each physical data center location in {{site.data.keyword.cloud}} is divided into multiple, discrete networking LANs, otherwise known as PoDs. Each of these has its own separate network infrastructure, a limited number of VLANs, as well as public and private IP subnets. These VLANs and subnets are shared by all clients that have compute capacity that is provisioned within that PoD space.
{: shortdesc}

Currently, you can use the UI to select the deploying data center location at the specific zone, such as `tok02`. You can also select the deploying VLAN and subnet when you have the existing one. However, you cannot specify PoD-based locations except for a gateway appliance and VLAN in the UI.

Because you cannot specify PoD locations, and there is no VLAN or subnets, your provisioning can be distributed over multiple PoDs, which can be problematic. 

To prevent this issue, you can order a "Premium VLAN" in advance, then specify it as your network VLAN; however, this option incurs an additional cost. 

A better option is to use the CLI and API.

## Using the CLI and API to specify PoD

You can use the CLI and API to specify PoD using the following option:

```sh
--extras '{"virtualGuests": [{"hostname": "test", "domain": "softlayer.com", "primaryBackendNetworkComponent": {"router": {"id": 1673467}}}]}'
```
{: pre}

The `primaryBackendNetworkComponentId` can be obtained through the following API call:

```sh
slcli call-api SoftLayer_Network_Pod getAllObjects
```
{: pre}
