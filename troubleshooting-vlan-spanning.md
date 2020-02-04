---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: vlan, troubleshooting, problems, questions

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
{:support: data-reuse='support'}

# Load Balancer VLAN Spanning Troubleshooting
{: #load-balancer-vlan-spanning-troubleshooting}
{: troubleshoot}
{: support}

This topic provides information on common issues you may encounter when the load balancer and the compute instances connected to the load balancer are in different subnets. VLAN Spanning must be enabled for the load balancer to communicate and forward requests to compute instances residing on a different subnet.

1. Go to the [Network VLANs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/classic/network/vlans){:new_window} page.

2. Toggle **VLAN Spanning** to **On**.

![VLAN Spanning](images/CLB_vlan_spanning_PUP.png "VLAN Spanning")

This opens communication between the load balancer and its compute instances.
