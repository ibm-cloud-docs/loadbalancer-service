---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

keywords: 

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

# Setting back-end encryption
{: #setting-backend-encryption}
{: help}
{: support}

Back-end encryption is supported to allow end-to-end data traffic encryption. Not only is the traffic between the load balancer and the client encrypted, but so is the traffic between the load balancer and the back-end server.
{: #shortdesc}

To enable back-end encryption:

* If you are adding a new HTTPS protocol, set the front end and back end to **HTTPS**.
* For existing HTTPS protocols, set the back end to **HTTPS**.
