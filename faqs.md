---

copyright:
  years: 2017, 2021
lastupdated: "2021-03-10"

keywords:

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for IBM Cloud Load Balancer
{: #faqs-for-ibm-cloud-load-balancer}

This section contains answers to some frequently asked questions about the {{site.data.keyword.loadbalancer_full}} service.
{: shortdesc}

## How many load-balancing options are available in IBM Cloud?
{: #options}
{: faq}
{: support}

For a detailed comparison of IBM's load balancer offerings, refer to [Exploring IBM Cloud load balancers](/docs/loadbalancer-service?topic=loadbalancer-service-explore).

## Can I use a different DNS name for my load balancer?
{: #dns}
{: faq}
{: support}

While the auto-assigned DNS name for the load balancer is not customizable, you can add a Canonical Name (CNAME) record that points your preferred DNS name to the auto-assigned load balancer DNS name.

For example, if your account number is `123456`, your load balancer is deployed in `dal09` data center and its name is `myapp`, the auto-assigned load balancer DNS name is `myapp-123456-dal09.lb.bluemix.net`. Your preferred DNS name is `www.myapp.com`. You can add a CNAME record (through the DNS provider that you use to manage `myapp.com`) pointing `www.myapp.com` to the load balancer DNS name `myapp-12345-dal09.lb.bluemix.net`.

## What's the maximum number of virtual ports I can define with my load balancer service?
{: #max}
{: faq}
{: support}

While trying to create a load balancer service, you can define up to two virtual ports. You can define additional virtual ports after the service is created. The maximum number of virtual ports allowed is `10`.

## What's the maximum number of compute instances I can associate with my load balancer?
{: #faqs-max-instances}
{: faq}

While trying to create a load balancer service, you can configure up to 10 compute instances as back-end servers. You can define additional servers after the load balancer is created. The maximum number of back-end members allowed is 50.

## Can my back-end compute instances sit on a subnet different from the load balancer's subnet?
{: #faqs-back-end-instances}
{: faq}

Yes, the load balancer and the compute instances that are connected to the load balancer can be in different subnets, but **VLAN spanning** must be enabled for the load balancer to communicate and forward requests to the compute instance. For more information, see [VLAN spanning](/docs/vlans?topic=vlans-vlan-spanning).

## What are the default settings and allowed values for various health check options?
{: #healthcheck}
{: faq}
{: support}

The default settings and allowed values are as follows.

* **Health check interval** - Default is 5 seconds, range is 2 – 60 seconds
* **Health check response timeout** - Default is 2 seconds, range is 1 – 59 seconds
* **Max retry attempts** - Default is two retry attempts, and the range is 1 - 10 retries

The health check response timeout value must always be less than the health check interval value.
{: note}

## Can I use compute instances residing in remote data centers with this service?
{: #faqs-instances-remote-dc}
{: faq}

It is recommended that your load balancer service and your compute instances reside locally within the same data center. The load balancer service’s UI does not show compute instances from other remote data centers. However, the UI includes compute instances from other data centers within the same city (for example, data centers whose names share the first three letters, such as `DALxx`). You can use the API interface to add compute instances from any remote data center.

## Which TLS version is supported by SSL offload?
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

## What is the maximum number of load balancer service instances I can create within my account?
{: #faqs-max-lb-instances}
{: faq}

Currently, you can create up to 50 service instances. If you need more instances, contact IBM Support.

## Can the {{site.data.keyword.loadbalancer_full}} service be used with VMWare?
{: #vmware}
{: faq}
{: support}

VMWare virtual machines that are assigned IBM Cloud portable private addresses can be specified as back-end servers to the load balancer. This feature is available using the API only, and not the web UI. Portable private IPs added using the API appear as "Unknown" in the UI as they are not assigned by IBM Cloud. Note that this kind of configuration can be used with other hypervisors, such as Xen and KVM.

VMWare virtual machines assigned non-IBM Cloud addresses (such as VMWare NSX networks) cannot be added directly as back-end servers to the load balancer. However, depending on your configuration, it might be possible to configure an intermediary, such as an NSX gateway, that has a IBM Cloud private address as the back-end server to the load balancer (with the actual servers being VMs attached to networks managed by VMware NSX).

## If I choose to use a public VLAN under my account to deploy my load balancer and I have a firewall deployed on my public VLAN, what configurations are required on my firewall to work with my load balancer service?
{: #public}
{: faq}
{: support}

TCP port 56501 is used for management. Ensure that incoming traffic to this port is not blocked by your firewall, otherwise, load balancer provisioning fails. Some outbound traffic is also required to be open to make sure the load balancer functions properly.

In summary, this is the required firewall configuration:

| Inbound/Outbound |	Protocol |	Source IP |	Source Port |	Destination IP | Destination Port |
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

## What if I cannot see the monitoring metrics of an existing load balancer after linking my Softlayer account to IBM Cloud?
{: #faqs-cannot-see-metrics}
{: faq}

Monitoring metrics are not available for existing load balancers after linking the accounts. You must re-create the load balancers or contact IBM Support. Monitoring metrics for newly created load balancers is available.

## Are the load balancer IP addresses fixed?
{: #fixedip}
{: faq}
{: support}

IBM cannot guarantee load balancer IP addresses to remain constant due to the elasticity that is built into the service. As it scales up or down, you see changes in the available IPs associated with the FQDN of your instance.

You should use FQDN and not cached IP addresses.
{: note}

## If I have a firewall deployed in front of my backend servers, what configurations are required for it to work with my load balancer?
{: #faqs-firewall}
{: faq}
{: support}

The available range of possible IPs for `public to public` load balancers cannot be predicted. Because of this, you should open all back-end member ports that have been added to the load balancer and set the source IP to `any`.

`Public to private` and `private to private` type load balancers communicate with your back-end members from your own private subnets. Because of this, you can set the source IP with your subnet's CIDR. Note that if the data center where you created the load balancer is part of an MZR, one load balancer appliance deploys in the selected data center, while a second deploys in a different data center within the same region. This means they exist in two different subnets.

## Can the IBM Cloud Load Balancer service be used with Terraform?
{: #faqs-terraform}
{: faq}

Terraform can be used to create, update, and delete an IBM Cloud Load Balancer service resource. For more information, see [Using Terraform with Cloud Load Balancer service](/docs/terraform?topic=terraform-infrastructure-resources#lbaas).

## Is it possible to add members with secondary IP addresses?
{: #faqs-seconary-ip}
{: faq}

Members with secondary IP addresses can be added using the API.

## What happens when the load balancer is in `Maintenance Pending` state?
{: #faqs-maintenance-pending}
{: faq}

The load balancer can go into `Maintenance Pending` state due to following reasons:

* Horizontal scaling event takes place.
* The load balancer has a firewall that's blocking the management traffic.
* Security patches are being installed.

When the load balancer is in the `Maintenance Pending` state, the data path is not affected.

## What is a non-system pool?
{: #faqs-non-system-pool}
{: faq}

A non-system pool is applicable only with public to private load balancers. The public IP addresses of the load balancer appliances are allocated from your public subnet. Select the **Allocate from a public subnet in this account** option when provisioning a load balancer.

## Does IBM Cloud Load Balancer support UDP?
{: #faqs-udp}
{: faq}

The IBM Cloud Load Balancer service does not support UDP. It supports only TCP, HTTP, and HTTPS.

## Is autoscaling supported by IBM Cloud Load Balancer?
{: #faqs-autoscaling}
{: faq}

The IBM Cloud Load Balancer service does not support autoscaling at this time.

## How can I monitor my IBM Cloud Load Balancer metrics?
{: #faqs-monitor-metrics}
{: faq}

The IBM Cloud Load Balancer service supports monitoring with {{site.data.keyword.mon_full_notm}}. For more information, see [Monitoring metrics using {{site.data.keyword.mon_full_notm}}](/docs/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics#monitoring-metrics).

## What information do I need to file an IBM Support ticket?
{: #faqs-ticket}
{: faq}

To file an IBM Support ticket, provide the product name ("{{site.data.keyword.loadbalancer_full}}"), the UUID of your load balancer (if possible) and your IBM Cloud account number. The UUID can be found in the URL after navigating to the overview page of the given load balancer.

## Where can I find pricing information for IBM Cloud Load Balancer?
{: #faqs-pricing}
{: faq}

Pricing metrics for IBM Cloud Load Balancer are detailed in [this topic](/docs/loadbalancer-service?topic=loadbalancer-service-about-ibm-cloud-load-balancer#lb-pricing-metrics). You can estimate the cost of a service using the cost estimator on the provisioning pages for IBM Cloud Load Balancer. Select **{{site.data.keyword.loadbalancer_full}}** from the Load Balancer page of the [IBM Cloud catalog](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group), then click **Create**.

## Can I use my Classic Bandwidth Pool to cover bandwidth costs for my IBM Cloud Load Balancer?
{: #faqs-clb-costs}
{: faq}

No. Currently, IBM Cloud Load Balancer is not eligible to participate in Classic Bandwidth Pools.
