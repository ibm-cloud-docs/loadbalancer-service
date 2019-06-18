---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# Getting Started with IBM Cloud Load Balancer
{: #getting-started}

To get started using the IBM© Cloud Load Balancer, you’ll need two main items:

* An account with IBM: [IBMid ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* A IBM server, either [Bare Metal](/docs/bare-metal?topic=bare-metal-about) or [Virtual Server Instance (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

If you need assistance in obtaining an **IBMid** account, contact your [IBM sales representative ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} for additional guidance.

If you have an existing IBM Cloud Infrastructure (SoftLayer) account, you can [link your account](/docs/account?topic=account-unifyingaccounts) with your IBMid.

## Ordering a Load Balancer
{: #ordering-a-load-balancer}

To order an IBM Cloud Load Balancer service, select **IBM Cloud Load Balancer** from the [IBM Cloud catalog  ![External link icon](../../icons/launch-glyph.svg "External link icon")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window}. Then click **Create** and perform the following procedure:

1. Define your basic service parameters, such as the name and description.
2. Select your data center.
3. Select a load balancer type of **Public**.
4. Select the subnet where you'd like to deploy your load balancer.

  Your load balancer service instance will have one of its network interfaces on this subnet. Ensure that your application servers are either on this subnet or reachable from this subnet. If necessary, enable VLAN spanning.
  {: note}

5. Create front-end and back-end application protocols and ports.

  For more information on this configuration, refer to [Configuring IBM Cloud Load Balancer Parameters](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters).
  {: note}

6. To enable SSL offload, set the front-end protocols to HTTPS, and the back-end protocols to HTTP. Then select your SSL Certificate from the Certificate drop down box.

  All existing SSL certificates are managed through the [IBM Cloud Certificate Store  ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}. If you do not have an SSL certificate, you can create one here.

7. Adjust your health check parameters if desired, otherwise use the default settings.

  For more information on health check parameters, refer to [IBM Cloud Load Balancer Parameters](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks).
  {: note}

8. Click **Attach Server** to associate one or more server instances behind your load balancer. You'll only see server instances local to your data center.
9. Review the page, confirm the Service Agreement, then click **Create**.

The Load Balancer list displays, showing all of your service instances.

Clicking on the service name on this page takes you to the service overview page. You can navigate to the **Protocols**, **Health Checks** and **Server Instances** tabs to further edit your configuration.

Your newly created load balancer may not immediately display in this list. After a few minutes, the new load balancer will display in a gray color, indicating its status is `Offline`. After another few minutes, the new load balancer will display green, indicating it is `Online`. You may need to refresh your screen to see these changes.
{: note}

Refer to [How use an IBM Cloud Load Balancer for elastic server load balancing](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing) for step-by-step guidance on configuring your new Cloud Load Balancer.
