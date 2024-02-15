---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-13"

keywords: cipher, suite, https

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Choosing a preferred cipher suite for your HTTPS application
{: #choosing-a-preferred-cipher-suite-for-your-https-application}
{: help}
{: support}

Cipher algorithms help the {{site.data.keyword.loadbalancer_full}} form secure connections with its HTTP clients. IBM offers a suite of approved ciphers for you to choose from so that you can secure the communication between your load balancer and your clients.
{: shortdesc}

To choose a preferred cipher suite for an existing load balancer:

1. Access the Cipher table from the **Protocols** tab.

	There must be at least one existing HTTPS protocol.
	{: note}

2. Click **Edit** to enable editing, and select (or clear) the required ciphers.

3. When you're done, click **Save** to save your changes.

	If you defined an HTTPS protocol when you create your load balancer, it has all ciphers in the suite enabled. The selection of a particular set of ciphers can be done only after the load balancer is provisioned.
	{: note}

	For a list of supported ciphers, refer to [SSL offload](/docs/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer).
	{: note}
