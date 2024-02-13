---

copyright:
  years: 2018
lastupdated: "2020-03-25"

keywords: troubleshooting, provisioning, question, problem

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Common issues when creating a new load balancer
{: #load-balancer-provisioning-troubleshooting}

This topic rovides information on common issues that you might encounter when creating a new instance of {{site.data.keyword.loadbalancer_full}}.
{: shortdesc}

## Insufficient IP addresses in your subnet
{: #insufficient-ip-addresses-in-your-subnet}
{: troubleshoot}
{: support}

{{site.data.keyword.loadbalancer_full}} requires at least two free IP addresses from its private subnet. In addition, if the load balancer is a public load balancer and the **IBM system pool** option is not used, then at least two free IP addresses are needed from your public subnet as well.

## Issues with firewalls on public and private VLANs
{: #issues-with-firewalls-on-public-and-private-vlans}
{: troubleshoot}
{: support}

For more information, see [IBM Cloud IP ranges](/docs/cloud-infrastructure?topic=cloud-infrastructure-ibm-cloud-ip-ranges).

## Viewing load balancer error messages
{: #viewing-load-balancer-error-messages}
{: troubleshoot}
{: support}

To view error messages for your load balancer, follow these steps:

1. Click the load balancer from the list page to view its details.
2. Mouseover the error symbol next to the load balancer's status.

If the load balancer is in an `ERROR` state, it cannot be recovered and must be deleted.
