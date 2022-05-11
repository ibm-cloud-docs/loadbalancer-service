---

copyright:
  years: 2017, 2022
lastupdated: "2022-05-05"

keywords: updates, additions, improvements

subcollection: loadbalancer-service

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for IBM Cloud Load Balancer
{: #loadbalancer-service-release-notes}

Find out about new and updated features in {{site.data.keyword.loadbalancer_full}}.
{: shortdesc}

## 15 April 2020
{: #loadbalancer-service-apr1520}
{: release-note}

Public subnet selection for public-to-private load balancers
:    You can now choose a public subnet while creating a public-to-private load balancer if non-system pool is also selected. This is supported for creation of load balancers by using APIs only.

:    For more information, see [public-private-load-balancer](/docs/loadbalancer-service?topic=loadbalancer-service-public-private-load-balancer).

{{site.data.keyword.mon_full_notm}} monitoring metrics

:    You can now access load balancer monitoring metrics (throughput, active connections, connection rate) through the use of [{{site.data.keyword.mon_full_notm}}](/docs/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics#monitoring-metrics).

## 11 March 2020
{: #loadbalancer-service-mar1120}
{: release-note}

Support redirection from HTTP to HTTPS
:    {{site.data.keyword.loadbalancer_full}} now allows you to configure a Level 7 policy by using the action `REDIRECT_HTTPS`. This action redirects HTTP traffic to the HTTPS listener port. You don't need a rule configuration for this action, and only one configuration is supported per listener. You can configure this action through API only.

:    For more information, see [Layer 7 policy](/docs/loadbalancer-service?topic=loadbalancer-service-layer-7-policy).

Allow customers to configure load-balancer timeout values
:    {{site.data.keyword.loadbalancer_full}} now allows you to configure or modify client and server timeout values by using the API. This feature is intended for applications that need customized timeout values.

## 22 September 2019
{: #loadbalancer-service-sep2219}
{: release-note}

Support for X-Forwarded-Proto Header
:    {{site.data.keyword.loadbalancer_full}} now inserts the X-Forwarded-Proto header for all requests when the front-end protocol is HTTP or HTTPS. This helps the back-end servers to know the protocol that is used by the client to connect to the load balancer.

HTTP cookie session persistence
:    {{site.data.keyword.loadbalancer_full}} now supports a new session persistence type called `HTTP Cookie`. With this type of session persistence, the load balancer adds a cookie to the first response from the back-end server. Subsequent HTTP requests with the cookie arriving at the load balancer are now persistent on the same back-end server.

## 3 June 2019
{: #loadbalancer-service-jun0319}
{: release-note}

Public-to-public load balancer
:    {{site.data.keyword.loadbalancer_full}} now supports a new load balancer type that is called a public-to-public load balancer. With this type of load balancer, you can add back-end server instances using their public IPs, and traffic is forwarded to them through their public interface. This applies to both layer 4 and layer 7 back-end members.

## 21 April 2019
{: #loadbalancer-service-apr2119}
{: release-note}

Layer 7 support
:    {{site.data.keyword.loadbalancer_full}} now fully supports layer 7 load balancing with APIs and the user portal. Through our layer 7 support, you can now group VSI or Bare Metal server instances in server pools and handle incoming requests according to set rules and policies so that traffic can be redirected to a URL, rejected, or distributed to layer 7 pool members.


## 20 February 2019
{: #loadbalancer-service-feb2019}
{: release-note}

Data logs
:    {{site.data.keyword.loadbalancer_full}} now supports data logs forwarding. With data logs enabled, your load balancer log data is forwarded to the IBM Cloud Log Analysis Service.

## 11 December 2018
{: #loadbalancer-service-dec1118}
{: release-note}

Back-end encryption and data log forwarding
: {{site.data.keyword.loadbalancer_full}} now supports back-end encryption and the ability to forward your data logs. Back-end encryption allows end-to-end data traffic encryption, including the traffic between the load balancer and the back-end servers. Data log forwarding lets you send data logs from your load balancers to the IBM Cloud Log Analysis Service.

## 04 August 2018
{: #loadbalancer-service-aug0418}
{: release-note}

Layer 7 API support
:    {{site.data.keyword.loadbalancer_full}} now provides a set of APIs supporting layer 7 load balancing. With layer 7 support, traffic can be redirected to a URL, rejected, or distributed to Level-7 pool members, including bare-metal and virtual-server instances. Incoming data traffic is classified by using Layer 7 policies and rules. The policies define what action to take when the data traffic matches the rules that are associated with them.

:    For more information, see [Layer 7 load balancing](/docs/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing).

## 04 April 2018
{: #loadbalancer-service-apr0418}
{: release-note}

Horizontal scaling
:    {{site.data.keyword.loadbalancer_full}} now scales up automatically when its load increases, and scales down as it decreases. When you create a load balancer, it starts with two appliances, but the number of appliances can be increased to 16 as the monitoring system detects an increase in the load. The IP addresses of each of the active appliances are added as DNS A-Records to the Fully Qualified Domain Name (FQDN) of the load balancer.

Internal load balancer
:    A highly demanded "internal" version of our {{site.data.keyword.loadbalancer_full}} is now available. This load balancer is not exposed publicly, but can still be used to balance applications within their IBM Cloud private networks (in a multi-tiered deployment, for instance, as shown in the figure).

:    ![Internal Load Balancer](./images/InternalLB.png){: caption="Internal load balancer" caption-side="bottom"}

:    It is both secure and consistent with the previous versions of {{site.data.keyword.loadbalancer_full}} on the public side.

Monitoring metrics
:    You can now use the "IBM Cloud Monitoring" service to monitor the following performance metrics that are associated with your load balancer and application:
    * Throughput
    * Connection rate
    * Active connections

:    ![Monitoring Metrics](./images/Metrics.png){: caption="Monitoring metrics" caption-side="bottom"}

:    Up to two weeks of samples are collected and displayed by the load balancer web UI. The data can also be viewed on the IBM Cloud Monitoring service portal. If you require data for longer than two weeks, depending on the volume of other cloud metrics you might be sending to your Cloud Monitoring instance, you might need to upgrade your monitoring plan. For more information, see [Monitoring metrics using {{site.data.keyword.mon_full_notm}}](/docs/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics).

Cipher suite customization
:    You can now customize the cipher suites that are used when the load balancer is configured for SSL termination.

:    When you enable SSL termination on {{site.data.keyword.loadbalancer_full}} (by selecting **HTTPS** as the front-end protocol), a carefully selected default set of cipher suites is enabled that conform to security best practices. IBM keeps a close watch on any new vulnerabilities that might be discovered, and updates the list . This, along with the seamless security updates of software and hardware components, helps to keep your applications secure at all times.

:    For more information, see [Custom cipher suite](/docs/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application).
