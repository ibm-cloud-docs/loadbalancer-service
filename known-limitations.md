---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: 

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Known issues and limitations with IBM Cloud Load Balancer
{: #known-issues-and-limitations-with-ibm-cloud-load-balancer}

Provides information on the currently known issues and limitations with the {{site.data.keyword.loadbalancer_full}} service.
{: shortdesc}

## Known issues
{: #known-issues}

The {{site.data.keyword.loadbalancer_full}} service currently has the following issues:

* The **Edit** button in the server instances and protocols tabs applies to all entries and is not restricted to rows selected by using a checkbox.
* During the initial creation of the load balancer service, your custom health check settings are lost if you go back and forth between various pages.
* You might experience some issues while using Internet Explorer 11, Edge, or Safari browsers for administering the load balancer service. As an alternative, use either the Firefox or Chrome browser.
* During the initial service creation, the list for the data centers might be skewed. Regardless, you can still select your data center.
* The pricing information on the review page is rounded off to two decimal digits. For correct pricing, refer to the pricing displayed on the plan page.

## Known limitations
{: #known-limits}

The {{site.data.keyword.loadbalancer_full}} service currently has the following limitations:

* Maximum number of virtual ports/protocols - 10
* Maximum number of servers behind load balancer - 50
