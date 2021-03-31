---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-22"

keywords: data logs

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:term: .term}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:table: .aria-labeledby="caption"}
{:generic: data-hd-programlang="generic"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# Data logging
{: #data-logging}

Data and health check logs are valuable for debugging and maintenance purposes. With the data logging feature enabled, IBM Cloud Load Balancer forwards these logs to the [IBM Log Analysis](https://cloud.ibm.com/observe/logging){:external} under your account.
{:shortdesc}

You can enable or disable this feature by:

* Creating a load balancer and setting this feature to on.

![Data Logging](images/DataLogging.png "Data Logging")

* Using the API `enableOrDisableDataLogs`.

## Viewing logs in the IBM Cloud logging analysis service
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

Log in to the [IBM Log Analysis](https://cloud.ibm.com/observe/logging){:external} with your IBM Cloud account. Logs can be viewed from the Log Analysis instance. Refer to [Getting started with IBM Log Analysis](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-getting-started#getting-started) for more information.

Data logs are only sent if your Softlayer and IBM Cloud accounts are linked.
{: note}

To create a Log Analysis instance, follow these steps:

1. Select the IBM Cloud account associated with your Softlayer account, then select **Create a logging instance**. The logging instance creation dialog shows.

2. Choose the region from the dropdown list that corresponds to the data center where you provisioned the load balancer.

  For a load balancer in SYD01, you would choose the region of Sydney.
  {: tip}

  The following table shows the mapping between regions and data center:

| Region | Data center |
| ------ | ----------- |
| Sydney | SYD01, SYD05, SYD04, MEL01 |
| Tokyo | CHE01, HKG02, SNG01, TOK02, TOK04, TOK05, SEO01, OSA02 |
| Frankfurt | AMS01, AMS03, FRA02, FRA04, FRA05, MIL01, PAR01 |
| London | LON01, LON02, LON04, LON05, LON06, OSL01 |
| Dallas | DAL00, DAL01, DAL02, DAL05, DAL06, DAL07, DAL08, DAL09, DAL10, DAL12, DAL13, HOU01, HOU02, MEX01, SJC01, SJC03, SJC04, SEA01, SAO01 |
| Washington DC | MON01, TOR01, WDC01, WDC04, WDC06, WDC07 |
{: caption="Table 1. Mapping between region and datacenter" caption-side="top"}

  Load balancers whose logging was enabled before 22 April 2020, had their logs sent to **Dallas** by default. For these load balancers, you can now set the region based on the data center where the load balancer was provisioned. To do so, create a logging instance, then disable and re-enable the logging toggle for your load balancer.
  {: note}

After you choose your region, click **Create** to create the logging instance, then configure it by clicking **Configure the platform service logs**.

## Log output examples
{: #log-output-examples}

The following output is an example of an {{site.data.keyword.loadbalancer_full}} data log:

```
{"datetime":"2019-09-17T03:13:37.373247+00:00", "host":"loadbalancer-dal09-323716-880632-975820", "process":"Cloud Load Balancer", "message":" Connect from xxx.xxx.xxx.xxx:56771 to 169.55.233.136:80 (a9887082-02ff-440c-8e9e-f9026bdc209a\/HTTP)","logSourceCRN":"crn:v1:bluemix:public:logdna:us-south:a/5c59f412bc914beb390b080e07e5e6a2:ffff0000-ffff-0000-ffff-ffff0000ffff::"}
```
Note that:
* `datetime` is Coordinated Universal Time.
* `loadbalancer-dal09-323716-880632-975820` is the load balancer name, and `dal09` is the data center.
* `323716` is the account ID. `880632` is the load balancer ID. `975820` is the load balancer instance ID.
* `xxx.xxx.xxx.xxx` is a public IP, which is masked for GDPR compliance.

The following output is an example of a health check log seen in the IBM Log Analysis that uses the IBM Cloud Log Analysis service:

```
{"datetime":"2019-09-11T08:04:22.534063+00:00", "host":"loadbalancer-dal09-323716-879158-975712", "process":"Cloud Load Balancer", "message":" Health check for server 9a226696-64b7-4f42-a587-74addd178f0e\/81035d8f-5e50-4743-ab04-20987c4c51be-10.143.99.103 succeeded, reason: Layer7 check passed, code: 200, info: \"HTTP status check returned code <3C>200<3E>\", check duration: 2ms, status: 4\/4 UP.","logSourceCRN":"crn:v1:bluemix:public:logdna:us-south:a/5c59f412bc914beb390b080e07e5e6a2:ffff0000-ffff-0000-ffff-ffff0000ffff::"}
```

Note that `10.143.99.103` is the back-end server member IP address.
