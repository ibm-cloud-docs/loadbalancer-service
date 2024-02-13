---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-22"

keywords: data logs

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Data logging
{: #data-logging}

Data and health check logs are valuable for debugging and maintenance purposes. With the data logging feature enabled, IBM Cloud Load Balancer forwards these logs to the [IBM Log Analysis](https://cloud.ibm.com/observe/logging){: external} under your account.
{: shortdesc}

You can enable or disable this feature by:

* Creating a load balancer and setting this feature to on.

![Data Logging](images/DataLogging.png "Data Logging"){: caption="Data logging" caption-side="bottom"}

* Using the API `enableOrDisableDataLogs`.

## Viewing logs in the IBM Cloud logging analysis service
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

Log in to the [IBM Log Analysis](https://cloud.ibm.com/observe/logging){: external} with your IBM Cloud account. Logs can be viewed from the Log Analysis instance. Refer to [Getting started with IBM Log Analysis](/docs/log-analysis?topic=log-analysis-getting-started) for more information.

Data logs are only sent if your Softlayer and IBM Cloud accounts are linked.
{: note}

To create a Log Analysis instance, follow these steps:

1. Select the IBM Cloud account associated with your Softlayer account, then select **Create a logging instance**. The logging instance creation dialog shows.

2. Choose the region from the dropdown list that corresponds to the data center where you provisioned the load balancer.

   For a load balancer in SYD01, you would choose the region of Sydney.
   {: tip}

   For information on the mapping between regions and data center, refer to [IBM Cloud global data centers](https://www.ibm.com/cloud/data-centers){: external}.

After you choose your region, click **Create** to create the logging instance, then configure it by clicking **Configure the platform service logs**.

## Log output examples
{: #log-output-examples}

The following output is an example of an {{site.data.keyword.loadbalancer_full}} data log:

```sh
{"datetime":"2019-09-17T03:13:37.373247+00:00", "host":"loadbalancer-dal09-323716-880632-975820", "process":"Cloud Load Balancer", "message":" Connect from xxx.xxx.xxx.xxx:56771 to 169.55.233.136:80 (a9887082-02ff-440c-8e9e-f9026bdc209a\/HTTP)","logSourceCRN":"crn:v1:bluemix:public:logdna:us-south:a/5c59f412bc914beb390b080e07e5e6a2:ffff0000-ffff-0000-ffff-ffff0000ffff::"}
```

Note that:
* `datetime` is Coordinated Universal Time.
* `loadbalancer-dal09-323716-880632-975820` is the load balancer name, and `dal09` is the data center.
* `323716` is the account ID. `880632` is the load balancer ID. `975820` is the load balancer instance ID.
* `xxx.xxx.xxx.xxx` is a public IP, which is masked for GDPR compliance.

The following output is an example of a health check log seen in the IBM Log Analysis that uses the IBM Cloud Log Analysis service:

```sh
{"datetime":"2019-09-11T08:04:22.534063+00:00", "host":"loadbalancer-dal09-323716-879158-975712", "process":"Cloud Load Balancer", "message":" Health check for server 9a226696-64b7-4f42-a587-74addd178f0e\/81035d8f-5e50-4743-ab04-20987c4c51be-10.143.99.103 succeeded, reason: Layer7 check passed, code: 200, info: \"HTTP status check returned code <3C>200<3E>\", check duration: 2ms, status: 4\/4 UP.","logSourceCRN":"crn:v1:bluemix:public:logdna:us-south:a/5c59f412bc914beb390b080e07e5e6a2:ffff0000-ffff-0000-ffff-ffff0000ffff::"}
```

Note that `10.143.99.103` is the back-end server member IP address.
