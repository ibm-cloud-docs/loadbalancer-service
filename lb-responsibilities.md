---

copyright:
  years: 2019
lastupdated: "2019-11-14"

keywords: load balancer, vpc, responsibilities

subcollection: vpc-on-classic

---

{:new_window: target="_blank_"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}
{:external: target="_blank_" .external}


# Your responsibilities by using IBM Cloud Load Balancer Service
{: #responsibilities-lb}

Learn about management responsibilities that you have when you use {{site.data.keyword.cloud}} Load Balancer Service. For overall terms of use, refer to the [IBM Cloud Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## IBM Responsibilities

* Deploy the Load Balancer in a secured, IBM-owned infrastructure account.
* Provision the Load Balancer and set up the necessary networking connections for management traffic and data path traffic.
* Fulfill requirements for additional capacity based on utilization.
* Automatically apply security updates to keep the Load Balancer service up to date.
* Monitor and automatically recover the service to prevent outage.

## Customer Responsibilities

* Use the provided API or UI to configure the Load Balancer to meet the needs of your workloads.
* Following the instructions in the [IBM Cloud Load Balancer user documentation](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started#getting-started) to make any necessary configurations (such as, setting up firewalls and VLAN spanning) based on the features used.
* Monitor service notifications for communications regarding maintenance operations.
