---

copyright:
  years: 2017, 2025
lastupdated: "2025-05-30"

keywords:

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for IBM Cloud Load Balancer
{: #faqs-for-ibm-cloud-load-balancer}

The following frequently asked questions relate to the {{site.data.keyword.loadbalancer_full}} service.
{: shortdesc}

## How many load-balancing options are available in IBM Cloud?
{: #options}
{: faq}
{: support}

For a detailed comparison of IBM's load balancer offerings, see [Exploring IBM Cloud load balancers](/docs/loadbalancer-service?topic=loadbalancer-service-explore).

## Does IBM Cloud {{site.data.keyword.loadbalancer_short}} support HTTP/2 protocol?
{: #http2}
{: faq}
{: support}

Yes. The load balancer supports HTTP/2 protocol for both HTTP requests and responses.

## Can I use a different DNS name for my load balancer?
{: #dns}
{: faq}
{: support}

While you can't customize the loads balancer's auto-assigned DNS name, you can add a Canonical Name (CNAME) record that points your preferred DNS name to the auto-assigned DNS name.

For example, if your account number is `123456`, your load balancer is deployed in the `dal09` data center, and its name is `myapp`, the system assigns it the DNS name `myapp-123456-dal09.lb.bluemix.net`.

If you want to use `www.myapp.com` as your preferred name instead, you can create a CNAME record with your DNS provider to point `www.myapp.com` to the load balancer DNS name `myapp-123456-dal09.lb.bluemix.net`.

## What's the maximum number of virtual ports that I can define with my load balancer service?
{: #max}
{: faq}
{: support}

While you try to create a load balancer service, you can define up to two virtual ports. After the service is created, you can define extra virtual ports, up to a maximum of `10` ports.

## What's the maximum number of compute instances that I can associate with my load balancer?
{: #faqs-max-instances}
{: faq}

When you create a load balancer service, you can configure up to 10 compute instances as back-end servers. After the load balancer is created, you can add more servers, up to a maximum of 50 back-end members.

## Can my back-end compute instances sit on a subnet different from the load balancer's subnet?
{: #faqs-back-end-instances}
{: faq}

Yes. The load balancer and the compute instances that are connected to the load balancer can be in different subnets. However, you must enable **VLAN spanning** for the load balancer to communicate and forward requests to the compute instance. For more information, see [VLAN spanning](/docs/vlans?topic=vlans-vlan-spanning).

## What are the default settings and allowed values for various health check options?
{: #healthcheck}
{: faq}
{: support}

The default settings and allowed values are as follows.

* **Health check interval** - The default is 5 seconds, and the range is 2 – 60 seconds
* **Health check response timeout** - The default is 2 seconds, and the range is 1 – 59 seconds
* **Max retry attempts** - The default is two retry attempts, and the range is 1 - 10 retries

The health check response timeout value must always be less than the health check interval value.
{: note}

## Can I use compute instances that reside in remote data centers with this service?
{: #faqs-instances-remote-dc}
{: faq}

It's best to keep your load balancer service and compute instances in the same data center. The console shows only compute instances from other data centers within the same city (for example, data centers whose names share the first three letters, such as `DALxx`). If you need to add instances that reside in remote data centers, you can do that through the API.

## Which TLS version does SSL offload support?
{: #faqs-ssl}
{: faq}

The IBM Cloud Load Balancer service supports TLS 1.2 with SSL termination.

The following list details the supported ciphers (listed in order of precedence):

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## What is the maximum number of load balancer service instances that I can create within my account?
{: #faqs-max-lb-instances}
{: faq}

Currently, you can create up to 50 service instances. If you need more instances, contact IBM Support.

## Can the {{site.data.keyword.loadbalancer}} service be used with VMWare?
{: #vmware}
{: faq}
{: support}

VMWare virtual machines that are assigned IBM Cloud portable private addresses can be specified as back-end servers to the load balancer. This feature is available only from the API, but not from the console. Portable private IPs added by using the API appear as "Unknown" in the console as they are not assigned by IBM Cloud. This configuration can be used with other hypervisors, such as Xen and KVM.

VMWare virtual machines with non-IBM Cloud addresses, such as those that are on VMWare NSX networks can't be added directly as back-end servers to the load balancer. But depending on your setup, you might use an intermediary, such as an NSX gateway. This gateway has an IBM Cloud private address and acts as the back-end server for the load balancer, while the actual servers are VMs on VMware NSX-managed networks.

## If I deploy a load balancer and a firewall on a public VLAN in my account, what configurations do I need on the firewall to make it work with the load balancer?
{: #public}
{: faq}
{: support}

The TCP port 56501 is used for management. Ensure that incoming traffic to this port is not blocked by your firewall. Otherwise, load balancer provisioning, customer operations, and service triggered operations, might fail. More specifically, ports 56501 (management), 443 (monitoring), 8834 and 10514 (security and compliance) must be always allowed for the load balancer to successfully manage customer workloads. Some outbound traffic is also required to be open to make sure the load balancer functions properly.

In summary, the following requirements are needed for the firewall configuration:

| Inbound and Outbound |	Protocol |	Source IP |	Source Port |	Destination IP | Destination Port |
| ---------------- | --------- | ---------- | ----------- | -------------- | ----------------- |
|     Inbound 	   |    TCP 	 |     AnyIP 	|    AnyPort  |    AnyIP       |    	 56501      |
|     Inbound 	   |    TCP 	 |     AnyIP 	|     443     |    AnyIP       |    	AnyPort     |
|     Inbound 	   |    TCP 	 |     AnyIP 	|    10514    |    AnyIP       |    	AnyPort     |
|     Inbound 	   |    TCP 	 |     AnyIP 	|     8834    |    AnyIP       |    	AnyPort     |
|     Outbound 	   |    TCP 	 |     AnyIP 	|     56501   |    AnyIP       |    	AnyPort     |
|     Outbound 	   |    TCP 	 |     AnyIP 	|    AnyPort  |    AnyIP       |    	  443       |
|     Outbound 	   |    TCP 	 |     AnyIP 	|    AnyPort  |    AnyIP       |    	 10514      |
|     Outbound 	   |    TCP 	 |     AnyIP 	|    AnyPort  |    AnyIP       |    	  8834      |
{: caption="Required firewall configuration" caption-side="bottom"}

Also, ensure your application's ports are open to accept traffic.

## What if I can't see the monitoring metrics of an existing load balancer after I link my Softlayer account to IBM Cloud?
{: #faqs-cannot-see-metrics}
{: faq}

Monitoring metrics aren't available for existing load balancers after you link the accounts. Re-create the load balancers or contact IBM Support. Monitoring metrics are available for all newly created load balancers.

## Are the load balancer IP addresses fixed?
{: #fixedip}
{: faq}
{: support}

No. The load balancer is built to adjust automatically as needed, which means its IP addresses might change over time. As the service scales up or down, the IPs linked to the FQDN of your instance might also change.

Use FQDN and not cached IP addresses.
{: note}

## If I deploy a firewall in front of my backend servers, what configurations do I need to make it work with my load balancer?
{: #faqs-firewall}
{: faq}
{: support}

The available range of possible IPs for `public to public` load balancers cannot be predicted. Because of this condition, you must open all back-end member ports that are added to the load balancer and set the source IP to `any`.

`Public to private` and `private to private` load balancers use your private subnets to communicate with your back-end members. Because of this setup, you can set the source IP with your subnet's CIDR.

If the data center where you created the load balancer is part of an MZR, one load balancer deploys in the selected data center, while a second deploys in a different data center within the same region. This means that they exist in two different subnets.

## Can the IBM Cloud Load Balancer service be used with Terraform?
{: #faqs-terraform}
{: faq}

Yes. You can use Terraform to create, update, and delete an IBM Cloud Load Balancer service resource.

## Is it possible to add members with secondary IP addresses?
{: #faqs-seconary-ip}
{: faq}

Yes. You can add members with secondary IP addresses by using the API.

## What happens when the load balancer is in `Maintenance Pending` state?
{: #faqs-maintenance-pending}
{: faq}

The load balancer can go into `Maintenance Pending` state due to the following reasons:

* A horizontal scaling event takes place.
* The load balancer has a firewall that's blocking the management traffic.
* Security patches are being installed.

When the load balancer is in the `Maintenance Pending` state, the data path is not affected.

## What is a nonsystem pool?
{: #faqs-non-system-pool}
{: faq}

A nonsystem pool is applicable only with public to private load balancers. The public IP addresses of the load balancer appliances are allocated from your public subnet. Select the **Allocate from a public subnet in this account** option when you provision a load balancer.

## Does IBM Cloud Load Balancer support UDP?
{: #faqs-udp}
{: faq}

No. The IBM Cloud Load Balancer service does not support UDP. It supports only TCP, HTTP, and HTTPS.

## Is autoscaling supported by IBM Cloud Load Balancer?
{: #faqs-autoscaling}
{: faq}

No. The IBM Cloud Load Balancer service currently doesn't support autoscaling.

## How can I monitor my IBM Cloud Load Balancer metrics?
{: #faqs-monitor-metrics}
{: faq}

The IBM Cloud Load Balancer service supports monitoring with {{site.data.keyword.mon_full_notm}}. For more information, see [Monitoring metrics that use {{site.data.keyword.mon_full_notm}}](/docs/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics#monitoring-metrics).

## What information do I need to file an IBM Support ticket?
{: #faqs-ticket}
{: faq}

To file an IBM Support ticket, provide the product name ("{{site.data.keyword.loadbalancer_full}}"), the UUID of your load balancer (if possible) and your IBM Cloud account number. You can find the UUID in the URL by going to the overview page of the specific load balancer.

## Where can I find pricing information for IBM Cloud Load Balancer?
{: #faqs-pricing}
{: faq}

Pricing metrics for IBM Cloud Load Balancer are detailed in the [pricing metrics page](/docs/loadbalancer-service?topic=loadbalancer-service-about-ibm-cloud-load-balancer#lb-pricing-metrics). You can estimate the cost of a service by using the cost estimator on the provisioning pages for IBM Cloud Load Balancer. Select **{{site.data.keyword.loadbalancer_full}}** from the Load Balancer page of the [IBM Cloud catalog](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group), then click **Create**.

## Can I use my Classic Bandwidth Pool to cover bandwidth costs for my IBM Cloud Load Balancer?
{: #faqs-clb-costs}
{: faq}

No. Currently, IBM Cloud Load Balancer bandwidth usage is not covered by Classic Bandwidth Pools.

## Do I need extra IPs in the subnet for IBM Cloud load balancer operations?
{: #faqs-extra-ips}
{: faq}

Yes. To support scaling and maintenance, it is best to allocate 8 extra IP addresses per subnet used by the load balancer. If your application load balancer uses only one subnet, allocate 16 extra IPs.
