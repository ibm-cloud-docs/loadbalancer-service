---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: cipher, suite, https

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Choosing a Preferred Cipher Suite for your HTTPS Application
{: #choosing-a-preferred-cipher-suite-for-your-https-application}

Cipher algorithms help the IBM© Cloud Load Balancer form secure connections with its HTTP clients. IBM offers a suite of approved ciphers for you to choose from, so that you secure the communication between your load balancer and your clients.

To choose a preferred cipher suite for an existing load balancer:

1. Access the Cipher table from the **Protocols** tab. 

	There must be at least one existing HTTPS protocol. 
	{: note}

2. Click **Edit** to enable editing, and select (or unselect) the required ciphers. 

	<img src="images/CLB_ciphers_edit_PUP.png" alt="drawing" style="width: 800px;"/>
	
3. When you're dobne, click **Save** to save your changes.

	If you defined a HTTPS protocol when creating your load balancer, it will have all ciphers in the suite enabled. The selection of a particular set of ciphers can be done only after the load balancer is provisioned.
	{: note}

	For a list of supported ciphers, refer to [SSL Offload](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).
	{: note}
