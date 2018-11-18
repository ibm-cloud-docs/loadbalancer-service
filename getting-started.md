---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Getting Started
To get started using the IBM Cloud Load Balancer, you’ll need two main items:

* An account with IBM: [IBMid ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/account/us-en/signup/register.html)
* A IBM server, either [Bare Metal](/docs/bare-metal/about.html#getting-started-with-bare-metal-servers) or [Virtual Server Instance (VSI)](/docs/vsi/vsi_index.html#getting-started-with-virtual-servers)

If you need assistance in obtaining an **IBMid** account, contact your [IBM sales representative ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/contact-us) for additional guidance.

If you have an existing IBM Cloud Infrastructure (SoftLayer) account, you can [link your account ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/account/softlayerlink.html#link_user_account) with your IBMid.

## Ordering a Load Balancer

To order an IBM Cloud Load Balancer service, select **Network > Load Balancers > IBM Cloud Load Balancer** from the [IBM Cloud catalog](https://console.bluemix.net/catalog/infrastructure/load-balancer-group). Log in or create a new account, then perform the following procedure:

1. Select your data center and review the service plan. Click **Next**.
2. Select the subnet where you'd like to deploy your load balancer. Your load balancer service instance will have one of its network interfaces on this subnet. Ensure that your application servers are either on this subnet or reachable from this subnet. If necessary, enable VLAN spanning. Click **Next**.
3. Define your basic service parameters, such as the name, description, front-end and back-end application protocols and ports, and load balancing method. 

	You may define a maximum of two protocols during the initial service creation. You may define up to ten protocols after the service is created. You must also use a unique front-end port. 
	
	Once you're done, click **Next**.
	
4. Adjust your health check parameters if desired, otherwise use the default settings. Click **Next**.
5. Associate one or more server instances behind your load balancer. You'll only see server instances local to your data center. Click **Next**.
6. Review the summary page then click **Create**.

	The summary page displays the load balancer service instance you just created. Note the **Status** field. A status of `Offline` implies the load balancer is not in service. No new configurations can be made and no load balancing service can be provided until its status changes to `Online`. You may need to refresh your screen to see the current status.

	Clicking on the service name on this page takes you to the service overview page. You can navigate to the **Protocols**, **Health Checks** and **Server Instances** tabs to further edit your configuration.

Refer to [How to create and use an IBM Cloud Load Balancer for elastic server load balancing](reliability-guide.html) for step-by-step configuration guidance.