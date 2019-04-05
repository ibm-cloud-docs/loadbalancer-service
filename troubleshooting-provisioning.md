---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, provisioning, question, problem

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

# Load Balancer Provisioning Troubleshooting
{: #load-balancer-provisioning-troubleshooting}

This topic provides information on common issues you may encounter while creating a new instance of IBM© Cloud Load Balancer.

## Insufficient IP addresses in your subnet
{: #insufficient-ip-addresses-in-your-subnet}

IBM Cloud Load Balancer requires at least two free IP addresses from its private subnet. In addition, if the load balancer is a public load balancer and the **IBM system pool** option is not used, then at least two free IP addresses are needed from your public subnet as well.

Follow the steps below to check for free IPs in a subnet.

1. Go to the [Customer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com){:new_window}, and navigate to the subnets section by selecting **Network > IP Management > Subnets**.

2. Click on the subnet which you want to check for free IP's.

	<img src="images/subnet_list.png" alt="drawing" style="width: 600px;"/>

3. The details page for the selected subnet shows the status of all the IP's in that subnet.

## Issues with firewalls on public and private VLANs
{: #issues-with-firewalls-on-public-and-private-vlans}

Refer to the topic [IBM Cloud IP Range](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges) for information on allowing IP ranges through the firewall.

## Viewing load balancer error messages
{: #viewing-load-balancer-error-messages}

To view error messages for your load balancer, perform the following procedure:

1. Click on the load balancer from the list page to view its details.
2. Mouseover the error symbol next to the load balancer's status.

<img src="images/lbaas_error_message.png" alt="drawing" style="width: 500px;"/>

If the load balancer is in an `ERROR` state, it cannot be recovered and must be deleted.
