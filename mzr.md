---

copyright:
  years: 2017, 202
lastupdated: "2020-04-05"

keywords: mzr, overview, data centers

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Multi-Zone Region (MZR) overview
{: #multi-zone-region-mzr-overview}

A Multi-Zone Region (MZR) helps your load balancer appliances achieve high availability and redundancy. When provisioning a load balancer, you must specify the subnet where it should be created. If that data center is part of a MZR, one appliance is deployed in the selected data center while the second is deployed in different data center within the same region. For example, `us-south` is a MZR, which contains the data centers `dal10`, `dal12`, `dal13`. You have a subnet A in `dal10`, subnets B and C in `dal12` and subnets D and E in `dal13`. If you create a load balancer in data center `dal13`, the first appliance gets deployed in `dal13` while the second gets deployed in the subnet with the most available IPs between `dal10` or `dal12` data centers.

Currently the following data centers are part of MZR:

| MZR Name | Data Centers |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |
| eu-gb | lon04, lon05, lon06 |
| eu-de | fra02, fra04, fra05 |
| jp-tok | tok02, tok04, tok05 |
| au-syd | syd01, syd04, syd05 |

## MZR requirements
{: #mzr-requirements}
MZRs have the following requirements:
* The data center you select should be part of an MZR. The preceding table lists the regions and the data centers in each region.
* VLAN spanning or VRF must be enabled in your account.
* Private subnets must exist in your account in the data centers of the MZR. Creation of compute devices in data centers results in the instantiation of private subnets.

If the data center you select is not part of an MZR, or if VLAN spanning or VRF is not enabled in your account, the load balancer creation defaults to the original behavior of instantiating all load balancer nodes in the data center you specify.

For a detailed overview and list of data centers that are part of the MZR, see [Multi Zone Region](/docs/overview?topic=overview-locations#mzr-table).
