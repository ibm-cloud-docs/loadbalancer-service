---

copyright:
  years: 2017, 2026
lastupdated: "2026-04-28"

keywords:

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Setting back-end encryption
{: #setting-backend-encryption}
{: help}
{: support}

Back-end encryption is supported to allow end-to-end data traffic encryption. Not only is the traffic between the load balancer and the client encrypted, but so is the traffic between the load balancer and the backend server.
{: #shortdesc}

To enable back-end encryption:

* If you add a new HTTPS protocol, set the front end and back end to **HTTPS**.
* For existing HTTPS protocols, set the back end to **HTTPS**.
