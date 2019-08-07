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

# 数据日志记录
{: #data-logging}

数据和运行状况检查日志对于调试和维护非常有用。启用数据日志记录功能后，IBM Load Balancer 会将这些日志转发到您帐户下的 [IBM Cloud Log Analysis 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://logging.ng.bluemix.net){:new_window}。

您可以通过以下方式启用或禁用此功能：

* 创建新的负载均衡器并将此功能设置为启用。
* 使用 API `enableOrDisableDataLogs`。

## 查看 IBM Cloud Log Analysis 服务中的日志
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

使用客户的 IBM Cloud 帐户登录到 [IBM Cloud Log Analysis 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://logging.ng.bluemix.net){:new_window}。可以通过 Kibana 查看日志。请参阅[本主题](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana)以获取更多信息。

只有当 Softlayer 和 IBM Cloud 帐户链接时才发送数据日志。选择与 Softlayer 帐户关联的 IBM Cloud 帐户，然后登录到 Kibana 仪表板。
{: tip}

## 日志输出示例
{: #log-output-examples}

以下输出是 {{site.data.keyword.loadbalancer_full}} 数据日志的示例：

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` 是负载均衡器名称，而 `dal09` 是数据中心。
* `323698` 是帐户标识。`643866` 是负载均衡器标识。`713576` 是成员标识。
* `xxx.xxx.xxx.xxx` 是根据 GDPR 屏蔽的公共 IP。

以下输出是 IBM Cloud Log Analysis 服务中运行状况检查日志的示例：

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` 是成员 IP 地址。
* `682175` 是成员标识。
