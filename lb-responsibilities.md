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

**8/17 - WORK IN PROGRESS - OUT FOR REVIEW**

Learn about the management responsibilities and terms and conditions that you have when using the {{site.data.keyword.loadbalancer_full}} service. For a high-level view of the service types in {{site.data.keyword.Bluemix}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{:shortdesc}

Review the following sections for the specific responsibilities that apply to you and {{site.data.keyword.IBM_notm}} when using {{site.data.keyword.cloud_notm}} {{site.data.keyword.loadbalancer_short}}. For the overall terms of use, see [{{site.data.keyword.Bluemix}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## Incident and operations management
{: #incident-and-ops}

Incident and operations management includes tasks such as monitoring, event management, high availability, problem determination, recovery, and full state backup and recovery.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities |  Your Responsibilities |
|----------|-----------------------|-----------------------|
| ? | Deploy a fully managed, highly available, secured, IBM-owned infrastructure. | ? |  
| ? | Provision the load balancer and set up the necessary networking connections for management traffic and data path traffic. | ? |
| ? | Fulfill requirements for additional capacity based on utilization. | ? |
| ? |  ? | Use the provided API or UI to configure the load balancer to meet the needs of your workloads. |
| ? | ? | Follow the instructions in the [IBM Cloud Load Balancer user documentation](/docs/loadbalancer-service?topic=loadbalancer-service-getting-started#getting-started) to make any necessary configurations (such as, setting up VLAN spanning) based on the features used. |
| ? | ? | Monitor service notifications for communications regarding maintenance operations. |
{: caption="Table 1. Responsibilities for incidents and operations" caption-side="top"}

## Change management
{: #change-management}

Change management includes tasks such as deployment, configuration, upgrades, patching, configuration changes, and deletion.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|-----------------------|
| ? | ? | ? |
{: caption="Table 2. Responsibilities for change management" caption-side="top"}

## Identity and access management
{: #iam-responsibilities}

Identity and access management includes tasks such as authentication, authorization, access control policies, as well as  approving, granting, and revoking access.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|-----------------------|
| ? | ? | ? |
{: caption="Table 3. Responsibilities for identity and access management" caption-side="top"}

## Security and regulation compliance
{: #security-rich-environment}

Security and regulation compliance includes tasks such as security control implementation and compliance certification.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|-----------------------|
| ? | Automatically apply security updates to keep the Load Balancer service up to date. | ? |
| ? | ? | Following the instructions in the [IBM Cloud Load Balancer user documentation](/docs/loadbalancer-service?topic=loadbalancer-service-getting-started#getting-started) to make any necessary configurations (such as, setting up firewalls) based on the features used. |
{: caption="Table 4. Responsibilities for security and regulation compliance" caption-side="top"}

## Disaster recovery
{: #disaster-recovery}

Disaster recovery includes tasks such as providing dependencies on disaster recovery sites, provision disaster recovery environments, data and configuration backup, replicating data and configuration to the disaster recovery environment, and failover on disaster events.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|-----------------------|
| ? | Monitor and automatically recover the service to prevent outage. | ? |
{: caption="Table 5. Responsibilities for disaster recovery" caption-side="top"}
