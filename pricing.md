---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: pricing, usage, month

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


# IBM Cloud Load Balancer pricing
{: #ibm-cloud-load-balancer-pricing}

{{site.data.keyword.loadbalancer_full}} pricing is based on the following three metrics, calculated monthly:
{: shortdesc}

* Service usage hours
* Data processed
* Outbound public bandwidth (egress)

All prices vary by geographic region. The outbound public bandwidth that is consumed by the {{site.data.keyword.loadbalancer_full}} service is billed per the standard data transfer charge of [USD 0.09 per GB ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/bandwidth).
{: note}

The following table details an example {{site.data.keyword.loadbalancer_full}} priced for a customer that uses 4500 GB per month for public load balancing:

| | Monthly | Rate | Cost |
| ------------- | ------------- | ------------- | ------------- |
| **Service Usage** | 720 hours | $0.025/hour | $18/month |
| **Data Processed** | 4500 GB | $0.008/GB | $36/month |

The total charge for this scenario is $54/month plus the standard data transfer charge [USD $0.09 per GB ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/bandwidth).

![Pricing](./images/pricing.png)

All prices vary by geographic region; pricing in the example and diagram is Dallas pricing in US dollars. Not displayed in the diagram is a service usage fee of $0.025/hour.
{: note}
