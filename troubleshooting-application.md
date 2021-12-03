---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, problem, server, application

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Why is my back-end server's health failing?
{: #the-back-end-server-is-unhealthy}
{: troubleshoot}
{: support}

Your back-end server's health is failing.
{: tsSymptoms}

To rectify this problem, check the following possible issues:
{: tsResolve}

* Does the port of the configured back-end protocol match the port that your application is listening on?
* Does the configured health-check have the correct protocol (TCP or HTTP), port, and URL (for HTTP) information? For HTTP, ensure that your application responds with `200 OK` for the configured health check URL.
* Is the back-end server on a different subnet than the load balancer? If not, ensure that VLAN spanning is enabled.
* Is the back-end server a virtual server with an enabled security group? If so, ensure that the security group rules allow traffic between the load balancer and the virtual server.
