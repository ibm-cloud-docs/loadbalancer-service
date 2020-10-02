---

copyright:
  years: 2017, 2018
lastupdated: "2019-11-14"

keywords: migrate, update, local, cloud, faq, support, eom, auto scaling, vip, fqdn, service group, vsi, bare metal, migrating, disruption, scaling, protocol, TLS, version

subcollection: local-load-balancer

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:faq: data-hd-content-type='faq'}

# Local Load Balancer migration FAQs
{: #migration-faq}

Find answers to frequently asked questions about the IBM Local Load Balancer migration process.
{: shortdesc}

## What is the announcement and effective date for Local Load Balancer End of Marketing (EOM)?
{: faq}

The EOM announcement date is March 1, 2019 and the effective date is June 1, 2019. No new sales can happen after this date.

## Is support for Local Load Balancer available after EOM?
{: faq}

Yes, support is available for existing Local Load Balancer customers.

## How can I get started with IBM Cloud Load Balancer?
{: faq}

We recommend you get started by reading the [IBM Cloud Load Balancer documentation](/docs/loadbalancer-service?topic=loadbalancer-service-getting-started).

## Does a migration path exist from the Local Load Balancer service to an IBM Cloud Load Balancer?
{: faq}

No automated migration path exists. However, you can request your Local Load Balancer service to be turned off and order the Cloud Load Balancer service from the IBM Cloud Console.

## What is the difference between the Local Load Balancer and the Cloud Load Balancer?
{: faq}

The Local Load Balancer is a hardware-based local load-balancing service, while IBM Cloud Load Balancer is a cloud-native service that offers a cost-effective, auto-scaling, load-balancing solution with support for both public and private networks.

## Does Cloud Load Balancer use the same terminology as Local Load Balancer?
{: faq}

In some cases, it does not. The following table compares key terms in Local Load Balancer with their corresponding and differing terms in Cloud Load Balancer.

| Local Load Balancer Term  | Cloud Load Balancer Term |
| ------------- | ------------- |
| Service Groups | Protocols |
| Service | Server Instances |
| VIP | FQDN |

## Do I still have a single, fixed IP address for my load balancer when I migrate to Cloud Load Balancer?
{: faq}

IPs for IBM Cloud Load Balancer are not fixed. The IBM Cloud Load Balancer assigns load balancer instances from a pool, which requires a fully qualified domain name (FQDN) at all times. As a result, the individual IP address of a Cloud Load Balancer might change.

## Is IBM Cloud Load Balancer available for Public/Private VSI's and Bare metal solutions?
{: faq}

Yes, Cloud Load Balancer is available for public and private VSIs, as well as Bare metal.

## Is IBM Cloud Load Balancer GDPR compliant?
{: faq}

Yes, the Cloud Load Balancer offering is GDPR-compliant.

## After I begin the migration, how much downtime or traffic disruption can I expect with my system?

You won't experience downtime or traffic disruption as a result of the load balancer migration. The only downtime or traffic disruption you might encounter is when updating your Local Load Balancer configuration to the new IBM Cloud Load Balancer FQDN.

## Your instructions say to order the IBM Cloud Load Balancer before I cancel the Local Load Balancer. Is there any impact to my system or workload while I configure the two devices?

No, Cloud Load Balancer and the Local Load Balancer are two separate offerings that work independently.

## I used to choose a "connections per second" option with my Local Load Balancer. Do I also have to configure this with the Cloud Load Balancer?

No. IBM Cloud Load Balancer automatically adjusts its load capacity. You can read more about this in the topic [Cloud Load Balancer Horizontal Scaling](/docs/loadbalancer-service?topic=loadbalancer-service-ibm-cloud-load-balancer-basics#horizontal-scaling).

## What protocols can I choose when using the Cloud Load Balancer?

You can choose HTTP, HTTPS, and TCP protocols. IBM also offers Layer-7 support.

## I need a particular type of cipher. Does Cloud Load Balancer support that?

IBM Cloud Load Balancer supports TLS version 1.2 with SSL offload. You can find more information about the supported SSL ciphers in [Cloud Load Balancer SSL cipher suites](/docs/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer#ssl-cipher-suites)
