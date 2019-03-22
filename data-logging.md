---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

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

# Data Logging
{: #data-logging}

Data and health check logs are valuable for debugging and maintenance purposes. With the data logging feature enabled, IBM Load Balancer forwards these logs to the [IBM Cloud Log Analysis Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://logging.ng.bluemix.net){:new_window} under your account.

You can enable or disable this feature by:

* Creating a new load balancer and setting this feature to on.
* Using the API `enableOrDisableDataLogs`.

## Viewing Logs in the IBM Cloud Logging Analysis Service

Log into the [IBM Cloud Logging Analysis Service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://logging.ng.bluemix.net){:new_window} with customer's IBM Cloud account. Logs can be viewed from Kibana. Refer to [this topic](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana) for more information.

Data logs are only sent if Softlayer and IBM Cloud accounts are linked. Select the IBM Cloud account associated with your Softlayer account, and then login to the Kibana dashboard.
{: tip}

## Log Output Examples

The following output is an example of an IBM Cloud Load Balancer data log:

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` is the load balancer name, and `dal09` is the data center.
* `323698` is the account ID. `643866` is the load balancer ID. `713576` is the member ID.
* `xxx.xxx.xxx.xxx` is a public IP which has been masked for GDPR.

The following output is an example of a health check log within the IBM Cloud Logging Analysis Service:

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` is the member IP address.
* `682175` is the member ID.
