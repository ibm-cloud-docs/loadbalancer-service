---

copyright:
  years: 2019
lastupdated: "2020-03-19"

---

{:new_window: target="_blank"}
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

# Understanding your responsibilities when using IBM Cloud Load Balancer
{: #responsibilities-lb}

Learn about management responsibilities that you have when you use {{site.data.keyword.cloud}} Load Balancer Service. For overall terms of use, refer to the [IBM Cloud Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.loadbalancer_full}}. For a high-level view of the service types in {{site.data.keyword.Bluemix}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyboard.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{:shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use IBM Cloud Load Balancer. For the overall terms of use, see [{{site.data.keyword.Bluemix}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## IBM Cloud infrastructure
{: #mgmt-infrastructure}

You and IBM have unique responsibilities for the set up and maintenance of IBM Cloud infrastructure and your workloads.

| Responsibilities |  Ownership |
|----------|-----------------------|
| Deploy a fully managed, highly available, secured, IBM-owned infrastructure. | IBM |  
| Provision the Load Balancer and set up the necessary networking connections for management traffic and data path traffic.  | IBM |
| Fulfill requirements for additional capacity based on utilization. | IBM |
| Use the provided API or UI to configure the Load Balancer to meet the needs of your workloads. | Customer |
| Following the instructions in the [IBM Cloud Load Balancer user documentation](/docs/loadbalancer-service?topic=loadbalancer-service-getting-started#getting-started) to make any necessary configurations (such as, setting up VLAN spanning) based on the features used. | Customer |
| Monitor service notifications for communications regarding maintenance operations. | Customer |

## Security and regulation compliance
{: #security-rich-environment}

You and IBM have unique responsibilities for security and compliance.

| Responsibilities |  Ownership |
|----------|-----------------------|
| Automatically apply security updates to keep the Load Balancer service up to date. | IBM |
| Following the instructions in the [IBM Cloud Load Balancer user documentation](/docs/loadbalancer-service?topic=loadbalancer-service-getting-started#getting-started) to make any necessary configurations (such as, setting up firewalls) based on the features used. | Customer |

## Disaster recovery
{: #disaster-recovery}

You and IBM have unique responsibilities for security and compliance.

| Responsibilities |  Ownership |
|----------|-----------------------|
| Monitor and automatically recover the service to prevent outage. | IBM |
