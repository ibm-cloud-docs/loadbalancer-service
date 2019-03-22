---

copyright:
  years: 2017, 2018
lastupdated: "2019-01-11"

keywords: mzr, overview, data centers

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Multi-Zone Region (MZR) Overview
{: #multi-zone-region-mzr-overview}

When creating a load balancer you will specify the data center where it should be created. If that data center is part of a Multi-Zone Region (MZR) then the load balancer nodes are instantiated in two different data centers. For example, `us-south` is a MZR which contains `dal10`, `dal12`, `dal13`. If a customer creates a load balancer in data center `dal13`, the nodes are instantiated in `dal13`, `dal10` or `dal12`. Normally you will not see any obvious changes in traffic. MZR support is useful when communication to a data center is disrupted. The load balancer will continue to function, since the other node is located in a different data center.

Currently the following data centers are part of MZR:

| MZR Name | Data Centers |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |
| eu-gb | lon04, lon05, lon06 |
| eu-de | fra02, fra04, fra05 |
| jp-tok | tok02, tok04, tok05 |
| au-syd | syd01, syd04, syd05 |


## MZR Requirements
Multi-Zone Regions have the following requirements:
* The data center you select should be part of an MZR. The above table lists the regions and the data centers in each region.
* VLAN Spanning must be enabled in your account.
* Private subnets must exist in your account in the data centers of the MZR. Creation of compute devices in data centers results in the instantiation of private subnets.

If the data center you select is not part of an MZR or if VLAN spanning is not enabled in your account, the load balancer creation defaults to the original behavior of instantiating all load balancer nodes in the data center you specify.
