---

copyright:
  years: 2017, 2020
lastupdated: "2020-04-05"

keywords: mzr, data centers

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

# Multi-Zone Region (MZR) overview
{: #multi-zone-region-mzr-overview}

A Multi-Zone Region (MZR) helps your load balancer appliances achieve high availability and redundancy. When provisioning a load balancer, you must specify the subnet where you want it created. If that data center is part of an MZR, one appliance is deployed in the selected data center while a second is deployed in a different data center within the same region.
{:shortdesc}

For example, `us-south` is an MZR, which contains the data centers `dal10`, `dal12`, `dal13`. You have a subnet A in `dal10`, subnets B and C in `dal12` and subnets D and E in `dal13`. If you create a load balancer in data center `dal13`, the first appliance gets deployed in `dal13` while the second gets deployed in the subnet with the most available IPs between `dal10` or `dal12` data centers.

Currently, the following data centers are part of MZR:

| MZR Name | Data Centers |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |
| eu-gb | lon04, lon05, lon06 |
| eu-de | fra02, fra04, fra05 |
| jp-tok | tok02, tok04, tok05 |
| jp-osa | osa21, osa22, osa23 |
| au-syd | syd01, syd04, syd05 |
| ca-tor | tor01, tor04, tor05 |

## MZR requirements
{: #mzr-requirements}
MZRs have the following requirements:
* The data center that you select should be part of an MZR. The preceding table lists the regions and the data centers in each region.
* VLAN spanning or VRF must be enabled in your account.
* Private subnets must exist in your account in the data centers of the MZR. Creation of compute devices in data centers results in the instantiation of private subnets.

If the data center you select is not part of an MZR, or if VLAN spanning or VRF is not enabled in your account, the load balancer creation defaults to the original behavior of instantiating all load balancer nodes in the data center you specify.

For a detailed overview and list of data centers that are part of the MZR, see [Multi Zone Region](/docs/overview?topic=overview-locations#mzr-table).
