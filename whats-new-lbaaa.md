---

copyright:
  years: 2017, 2018
lastupdated: "2019-09-11"

keywords: updates, additions, imporvements

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

# Recent Updates for IBM Cloud Load Balancer
{: #recent-updates-for-ibm-cloud-load-balancer}

Find out about new and updated features in {{site.data.keyword.loadbalancer_full}}.


## September 2019
{: #september-2019}

### HTTP Cookie Session Persistence
{: #http-cookie-session-persistence}
{{site.data.keyword.loadbalancer_full}} now supports a new session persistence type called 'HTTP Cookie'. With this type of session persistence, the load balancer adds a cookie to the first response from the back-end server. Subsequent HTTP(s) requests with the cookie arriving at the load balancer are now persistent on the same back-end server.

## June 2019
{: #june-2019}

### Public to Public Load Balancer
{: #public-to-public-load-balancer}
{{site.data.keyword.loadbalancer_full}} now supports a new load balancer type called Public to Public. With this type of load balancer, you can add backend server instances using their public IP's, and traffic will be forwarded to them through their public interface. This applies to both Layer-4 and Layer-7 backend members.

## April 2019
{: #april-2019}

### Layer 7 Support
{{site.data.keyword.loadbalancer_full}} now fully supports Layer 7 load balancing with APIs and the user portal. Through our Layer 7 (L7) support, you can now group VSI or Bare Metal server instances in server pools and handle incoming requests according to set rules and policies so that traffic can be redirected to a URL, rejected, or distributed to L7 pool members.


## February 2019
{: #february-2019}

### Data Logs
{: #data-logs}

{{site.data.keyword.loadbalancer_full}} now supports data logs forwarding. With data logs enabled, your load balancer log data will be forwarded to the [IBM Cloud Log Analysis Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}. Customers can view their data logs from the [IBM Cloud Log Analysis Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}.

## December 2018
{: #december-2018}

### Backend encryption and data log forwarding
{: #backend-encryption-and-data-log-forwarding}

{{site.data.keyword.loadbalancer_full}} now supports backend encryption and the ability to forward your data logs. Backend encryption allows end-to-end data traffic encryption, including the traffic between the load balancer and the backend servers. Data log forwarding lets you send data logs from your load balancers to the IBM Bluemix Log Analysis Service.

## August 2018
{: #august-2018}

### Layer 7 API Support
{: #layer-7-support-1}

{{site.data.keyword.loadbalancer_full}} now provides a set of APIs supporting Layer 7 load balancing. With Layer 7 (L7) support, traffic can be redirected to a URL, rejected, or distributed to L7 pool members, including bare-metal and virtual-server instances. Incoming data traffic is classified by using Layer 7 policies and rules. The policies define what action to take when the data traffic matches the rules associated with them.

Refer to [Layer 7 load balancing](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing) for additional details.

## April 2018
{: #april-2018}

### Horizontal Scaling
{: #horizontal-scaling}

{{site.data.keyword.loadbalancer_full}} now scales up automatically when its load increases, and scales down as it decreases. When you create a load balancer, it starts with two appliances, but the number of appliances can be increased to 16 (as of this writing) as the monitoring system detects an increase in the load. The IP addresses of each of the active appliances is added as DNS A-Records to the Fully Qualified Domain Name (FQDN) of the load balancer.

### Internal Load Balancer
{: #internal-load-balancer-1}

A highly demanded “internal” version of our {{site.data.keyword.loadbalancer_full}} is now available. This load balancer is not exposed publicly, but can still be used to balance applications within their IBM Cloud private networks (in a multi-tiered deployment, for instance, as shown in the figure).

![Internal Load Balancer](./images/InternalLB.png)

It is both secure and consistent with the previous versions of {{site.data.keyword.loadbalancer_full}} on the public side.

### Monitoring Metrics
{: #monitoring-metrics-2}

You can now leverage the “IBM Cloud Monitoring” service to monitor the following performance metrics associated with your load balancer and application:

* Throughput
* Connection rate
* Active connections

![Monitoring Metrics](./images/Metrics.png)

Up to two weeks of samples are collected and displayed by the load balancer web UI. The data can also be viewed on the IBM Cloud Monitoring service portal. If you require data for longer than two weeks, depending on the volume of other cloud metrics you may be sending to your Cloud Monitoring instance, you may need to upgrade your monitoring plan. Refer to [Monitoring-Metrics](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer) for additional details

This feature requires your IBM Cloud IaaS and PaaS accounts to be linked, with a few [simple steps](/docs/account?topic=account-unifyingaccounts).

### Cipher Suite Customization
{: #cipher-suite-custom-1}

You can now customize the cipher suites that are used when the load balancer is configured for SSL termination.

When you enable SSL termination on {{site.data.keyword.loadbalancer_full}} (by selecting **HTTPS** as the front-end protocol), a carefully selected default set of cipher suites is enabled that conform to security best practices. IBM keeps a close watch on any new vulnerabilities that may be discovered, and updates the list accordingly. This, along with the seamless security updates of software and hardware components, helps to keep your applications secure at all times.

Refer to [Custom Cipher Suite](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application) for additional details.
