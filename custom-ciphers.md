---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: cipher, suite, https

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
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Choosing a Preferred Cipher Suite for your HTTPS Application
{: #choosing-a-preferred-cipher-suite-for-your-https-application}
{: help}
{: support}

Cipher algorithms help the {{site.data.keyword.loadbalancer_full}} form secure connections with its HTTP clients. IBM offers a suite of approved ciphers for you to choose from, so that you secure the communication between your load balancer and your clients.

To choose a preferred cipher suite for an existing load balancer:

1. Access the Cipher table from the **Protocols** tab.

	There must be at least one existing HTTPS protocol.
	{: note}

2. Click **Edit** to enable editing, and select (or unselect) the required ciphers.

	![Edit CLB ciphers](images/CLB_ciphers_edit_PUP.png "Edit CLB ciphers")

3. When you're done, click **Save** to save your changes.

	If you defined a HTTPS protocol when creating your load balancer, it will have all ciphers in the suite enabled. The selection of a particular set of ciphers can be done only after the load balancer is provisioned.
	{: note}

	For a list of supported ciphers, refer to [SSL Offload](/docs/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).
	{: note}
