---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: faq, questions, load balancer, dns, port, traffic, connection, health check, vmware, tls, ssl

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:faq: data-hd-content-type='faq'}
{:note: .note}
{:important: .important}

# FAQs for IBM Cloud Load Balancer
{: #faqs-for-ibm-cloud-load-balancer}

This section contains answers to some frequently asked questions about the {{site.data.keyword.loadbalancer_full}} Service.

## How many load balancing options are available in IBM Cloud?
{: faq}

For a detailed comparison of IBM's Load Balancer offerings, refer to [Explore Load Balancers](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-explore).

## Can I use a different DNS name for my load balancer?
{: faq}

While the auto-assigned DNS name for the load balancer is not customizable, you can add a CNAME (Canonical Name) record that points your preferred DNS name to the auto-assigned load balancer DNS name.

For example, if your account number is 123456, your load balancer is deployed in `dal09` datacenter and its name is `myapp`, the auto-assigned load balancer DNS name is `myapp-123456-dal09.lb.bluemix.net`. Your preferred DNS name is `www.myapp.com`. You may add a CNAME record (via the DNS provider that you use to manage myapp.com) pointing `www.myapp.com` to the load balancer DNS name myapp-12345-dal09.lb.bluemix.net`.

## What's the maximum number of virtual ports I can define with my load balancer service?
{: faq}

While trying to create a new load balancer service, you may define up to two virtual ports. You can define additional virtual ports after the service is created. The maximum number of virtual ports allowed is 10.

## What's the maximum number of compute instances I can associate with my load balancer?
{: faq}

While trying to create a new load balancer service, you may configure up to 10 compute instances as backend servers. You can define additional servers after the loadbalancer is created. The maximum number of backend members allowed is 50.

## Can my backend compute instances sit on a subnet different from the load balancer's subnet ?
{: faq}

Yes, the load balancer and the compute instances connected to the load balancer can be in different subnets, but **VLAN Spanning** needs to be enabled for the load balancer to communicate and forward requests to the compute instance. Refer to [VLAN Spanning](/docs/infrastructure/vlans?topic=vlans-vlan-spanning) for more information.

## What are the default settings and allowed values for various health check parameters?
{: faq}

The default settings and allowed values are listed below:

* **Health check interval:** Default is 5 seconds, range is 2 – 60 seconds
* **Health check response timeout:** Default is 2 seconds, range is 1 – 59 seconds
* **Max retry attempts:** Default is 2 retry attempts, and the range is 1 to 10 retries

The health check response timeout value must always be less than the health check interval value.
{: note}

## Can I use compute instances residing in remote data centers with this service?
{: faq}

We recommend that your load balancer service and your compute instances reside locally within the same data center. The load balancer service’s graphical interface (GUI) will not show compute instances from other remote data centers. However, the GUI will include compute instances from other data centers within the same city (for example, data centers whose names share the first three letters, such as DALxx). You may use the API interface to add compute instances from any remote data center.

## Which TLS version is supported with SSL offload?
{: faq}

The Cloud Load Balancer Service supports TLS 1.2 with SSL termination.

The following list details the supported ciphers (listed in order of precedence):  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## What is the maximum number of Load Balancer service instances I can create within my account?
{: faq}

Currently, you may create up to 50 service instances. If you need more instances, please contact IBM Support.

## Can the {{site.data.keyword.loadbalancer_full}} Service be used with VMWare?
{: faq}

VMWare virtual machines that are assigned IBM Cloud portable private addresses can be specified as backend servers to the load balancer. This feature is currently available only using the API, and not the web UI (GUI). Portable private IPs added using the API appear as "Unknown" in the GUI, as they are not assigned by IBM Cloud. Note that this kind of configuration can be used with other Hypervisors such as Xen and KVM as well.

VMWare virtual machines assigned non-IBM Cloud addresses (such as VMWare NSX networks) cannot be added directly as backend servers to the load balancer. However, depending on your configuration, it may be possible to configure an intermediary, such as an NSX gateway, that has a IBM Cloud private address as the backend server to the load balancer (with the actual servers being VMs attached to network(s) managed by VMware NSX).

## If I choose to use a public VLAN under my account to deploy my load balancer and I have a firewall deployed on my public VLAN, what configurations are required on my firewall to work with my load balancer service?
{: faq}

TCP port 56501 is used for management. Please ensure that traffic to this port, as well as your application's ports, are not blocked by your firewall, otherwise load balancer provisioning will fail.

## What if I cannot see the monitoring metrics of an existing Load Balancer after linking my Softlayer account to IBM Cloud?
{: faq}

Monitoring metrics will not be available for existing load balancers after linking the accounts. You must recreate the load balancers or contact support. Monitoring metrics for newly created load balancers will be available.

## Are the load balancer IP addresses fixed?
{: faq}

We cannot guarantee load balancer IP addresses to remain constant due to the elasticity that is built into the service. As it scales up or down, you will see changes in the available IPs associated with the FQDN of your instance.

You should use FQDN and not cached IP addresses.
{: note}

## If I have a firewall deployed on my private VLAN, what configurations are required for it to work with my load balancer service?
{: faq}

Please refer to the topic [IBM Cloud IP Ranges](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges) for information on allowing IP ranges through the firewall.

## What information do I need to file a support ticket?
{: faq}

To file a support ticket, please provide the product name ("{{site.data.keyword.loadbalancer_full}}"), the UUID of your load balancer (if possible) and your IBM Cloud account number. The UUID can be found in the URL after navigating to the overview page of the given load balancer.
