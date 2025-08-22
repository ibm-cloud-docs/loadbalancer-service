---

copyright:
  years: 2017, 2025
lastupdated: "2025-08-22"

keywords: data logs

subcollection: loadbalancer-service

---

{{site.data.keyword.attribute-definition-list}}

# Logging for IBM Cloud Load Balancer
{: #ibm-cloud-logging}

Data and health check logs are valuable for debugging and maintenance purposes. With the data logging feature enabled, IBM Cloud Load Balancer forwards these logs to the [IBM Cloud Logs](https://cloud.ibm.com/observe/logging){: external} under your account.
{: shortdesc}

You can enable or disable this feature by:

* Creating a load balancer and setting this feature to on:

![Data Logging](images/DataLogging.png "Data Logging"){: caption="Data logging" caption-side="bottom"}

* Using the API: `enableOrDisableDataLogs`.

## Viewing logs in the IBM Cloud Logs service
{: #viewing-logs-in-the-ibm-cloud-logs-service}

Log in to the [IBM Cloud Logs](https://cloud.ibm.com/observe/logging){: external} with your IBM Cloud account. Logs can be viewed from the IBM Cloud Logs instance. Refer to [Getting started with IBM Cloud Logs](/docs/cloud-logs?topic=cloud-logs-getting-started) for more information.

Data logs are only sent if your Softlayer and IBM Cloud accounts are linked.
{: note}

To create a IBM Cloud Logs instance, perform the following procedure:

1. Select the IBM Cloud account associated with your Softlayer account, then select **Create a logging instance**. The logging instance creation dialog shows.

2. Choose the region from the dropdown list that corresponds to the data center where you provisioned the load balancer.

   For a load balancer in SYD01, you would choose the region of Sydney.
   {: tip}

   For information on the mapping between regions and data center, refer to [IBM Cloud global data centers](https://www.ibm.com/solutions/cloud-data-centers){: external}.

3. You can use {{site.data.keyword.logs_routing_full_notm}}, a platform service, to route platform logs in your account to a destination of your choice by configuring a tenant that defines where platform logs are sent. For more information, see [About Logs Routing](/docs/logs-router?topic=logs-router-about).

## Log output examples
{: #log-output-examples}

Sub-system name = `Cloud Load Balancer`
| Field             | Type       | Description             |
|-------------------|------------|-------------------------|
| `msgTimestamp`    | Required   | The timestamp that indicates when the log was generated.     |
| `logSourceCRN`    | Required   | The load balancer UUID can be obtained from `logSourceCRN`.    |
| `message`         | Required   | Datapath log message. |
{: caption="Log output examples" caption-side="top"}

The following output is an example of an {{site.data.keyword.loadbalancer_full}} data log:

```sh
{
datetime:2025-01-22T14:11:18.847230+00:00
msgTimestamp:2025-01-22T14:11:18.847230+00:00
host:loadbalancer-wdc04-323716-1137319-1367523
process:Cloud Load Balancer
message:Connect from 5.181.190.248:37328 to 52.116.108.53:80 (fabf4139-50b0-48ba-b399-277c09162832/HTTP)
logSourceCRN:crn:v1:bluemix:public:cloud-load-balancer:us-east:a/5c59f412bc914beb390b080e07e5e6a2:6239a1a7-6da4-4370-881c-2dec099b8623::
saveServiceCopy:false
platformSource:Cloud Load Balancer
}
```
{: screen}

Details of the datapath log fieds are:
* `msgTimestamp` is Coordinated Universal Time.
* `loadbalancer-wdc04-323716-1137319-1367523` is the load balancer name, and `wdc04` is the data center.
* `323716` is the account ID. `1137319` is the load balancer ID. `1367523` is the load balancer instance ID.

The following output is an example of a health check log seen in the IBM Cloud Logs service:

```sh
{
  datetime:2025-01-16T11:32:05.100888+00:00
  msgTimestamp:2025-01-16T11:32:05.100888+00:00
  host:loadbalancer-wdc04-323716-1137319-1367279
  process:Cloud Load Balancer
  message:Health check for server ea3b5aa1-cd85-4374-8387-cbf155d35643/c8d09bae-4d1c-4579-8af1-6e2fa75e81b5-10.171.112.26 failed, reason: Layer4 timeout, check duration: 5001ms, status: 0/2 DOWN.
  logSourceCRN:crn:v1:bluemix:public:cloud-load-balancer:us-east:a/5c59f412bc914beb390b080e07e5e6a2:6239a1a7-6da4-4370-881c-2dec099b8623::
  saveServiceCopy:false
  platformSource:Cloud Load Balancer
  }
```
{: screen}
