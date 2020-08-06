---

copyright:
  years: 2017, 2018
lastupdated: "2019-11-14"

keywords: migrate, update, load balancer, local, cloud

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

# Migrating a Local Load Balancer to IBM Cloud Load Balancer

You can migrate your Local Load Balancer to an IBM© Cloud Load Balancer by performing the following procedure.
{: shortdesc}

IBM Cloud Load Balancer offers a more enhanced customer experience, including:

* Load balancing support for public and private traffic
* Real-time support for horizontal scaling and health checks
* Usage-based pricing to reduce expenses
* No limitations on the number of connections you can have
* Layer 7 support

## Step 1: Order a Cloud Load Balancer
{: #step-1-order-a-cloud-load-balancer}

To order an IBM Cloud Load Balancer service, select **IBM Cloud Load Balancer** from the [IBM Cloud catalog  ![External link icon](../../icons/launch-glyph.svg "External link icon")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window}. Click **Create**, then perform the following procedure:

1. Define your basic service parameters, such as the name and description.
2. Select your data center.
3. Select a load balancer type of **Public**.
4. Select the subnet where you'd like to deploy your load balancer.

  Your load balancer service instance will have one of its network interfaces on this subnet. Ensure that your application servers are either on this subnet or reachable from this subnet. If necessary, enable VLAN spanning.
  {: note}

5. Create front-end and back-end application protocols and ports with the same configuration as the service groups you are currently using in your Local load Balancer. For more information on this configuration, refer to [Configuring IBM Cloud Load Balancer Parameters](/docs/loadbalancer-service?topic=loadbalancer-service-configure-load-balancing-parameters-and-place-order).
6. To enable SSL offload, set the front-end protocols to HTTPS, and the back-end protocols to HTTP. Then select the same SSL Certificate as your Local Load Balancer from the Certificate drop down box. The Certificate you use with your Local Load Balancer is in the drop down list because all existing SSL certificates are managed through the [IBM Cloud Certificate Store  ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}.
7. Adjust your health check parameters if desired, otherwise use the default settings. For more information on health check parameters, refer to [IBM Cloud Load Balancer Parameters](/docs/loadbalancer-service?topic=loadbalancer-service-configure-load-balancing-parameters-and-place-order#step-2-configuring-health-checks).
8. Click **Attach Server** to add any server instances you used for your Local Load Balancer service.
9. Review the page, confirm the Service Agreement, then click **Create**.

The Load Balancer list displays, showing all of your service instances.

Your newly created load balancer may not immediately display in this list. After a few minutes, the new load balancer will display in a gray color, indicating its status is `Offline`. After another few minutes, the new load balancer will display green, indicating it is `Online`. You may need to refresh your screen to see these changes.
{: note}

Clicking on the service name on this page takes you to the service overview page. You can navigate to the **Protocols**, **Health Checks** and **Server Instances** tabs to further edit your configuration.

## Step 2: Verify your Cloud Load Balancer is working as expected
{: #step-2-verify-your-cloud-load-balancer-is-working-as-expected}

Be aware, at this point, you now have two load balancers working at the same time: your old Local Load Balancer, and the new IBM Cloud Load Balancer.
{: important}

Test the new IBM Cloud Load Balancer using the domain listed in the status page above, ensuring that it functions in the same way as the VIP from your Local load Balancer.

Then, update any locations that use the Local Load Balancer VIP to use the new Cloud Load Balancer domain instead.

This configuration of the new new Cloud Load Balancer will be the only time you may experience downtime or traffic disruption in the migration process.
{: note}

## Step 3: Cancel your old Local Load Balancer
{: #step-3-cancel-your-local-load-balancer}

When you have replaced all Local load Balancer VIPs with the domain for your new IBM Cloud Load Balancer, and verified the functionality is working as expected, you can safely cancel your Local Load Balancer service. To do so, perform the following steps:

1. Go to the [Local Load Balancer list page](https://cloud.ibm.com/classic/network/loadbalancing/local).
2. Locate the Load Balancer you would like to delete and expand the arrow next to it.
3. Click the red **X** at the end of the row to cancel the Load Balancer.

