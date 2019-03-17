---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, monitor, metrics, throughput, connection

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Monitoring Metrics with IBM Cloud Load Balancer
{: #monitoring-metrics-with-ibm-cloud-load-balancer}

The load balancer monitors the following metrics:

* Throughput
* Active Connections
* Connection Rate

These metrics are visualized as graphs that can be viewed by selecting the **Monitoring** tab,
and are available programmatically as time series data points by using the `getListenerTimeSeriesData` API.

Each data point contains a timestamp in UNIX epoch time, and the metric value for that time interval ending at that timestamp. The user can specify the protocols and the time interval over which the metrics are to be reported.

Supported protocols include:

* HTTP
* HTTPS
* TCP

Specifying a protocol filters the metric by that protocol.

For example, if no protocol is specified, and the metric is *Throughput*,
then the total throughput for all protocols is reported.

If the protocol is *HTTP*, then only the throughput for HTTP traffic is reported.

The user can also specify the time interval over which the metric is to be reported. The time intervals supported are:

* 1 hour
* 6 hours
* 12 hours
* 24 hours
* 1 week
* 2 weeks

The number of data points reported is roughly the same for each time interval.  
For example, if the interval is 1 hour, then each data point represents 5 minutes of data.

If the interval is 2 weeks, then each data point represents 24 hours of data.

The table below shows how the data points are derived from the time interval:

| Time Interval | Datapoint Precision | Number of Datapoints |                                                                                              
| ------------------------------------------ | --------------------------------------------------- | -------------------|
| 1 hour    | 5 minutes | 12   |
| 6 hours   | 30 minutes | 12  |
| 12 hours  | 1 hour | 12 |
| 24 hours  | 2 hours | 12 |
| 1 week    | 12 hours | 12 |
| 2 weeks  | 24 hours | 12 |

# How to enable Metrics Monitoring

In order to retrieve monitoring metrics you must link your SoftLayer account with your IBM© Cloud account. Refer to [this topic](/docs/account?topic=account-unifyingaccounts#link_accounts) for more information.
