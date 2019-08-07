---

copyright:
  years: 2017, 2018
lastupdated: "2019-02-19"

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

# {{site.data.keyword.loadbalancer_full}} 的最新更新
{: #recent-updates-for-ibm-cloud-load-balancer}

了解 {{site.data.keyword.loadbalancer_full}} 中的新增功能和更新功能。

## 2019 年 2 月
{: #february-2019}

### 数据日志
{: #data-logs}

{{site.data.keyword.loadbalancer_full}} 现在支持数据日志转发。启用数据日志后，负载均衡器日志数据将转发到 [IBM Cloud Log Analysis 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}。客户可以通过 [IBM Cloud Log Analysis 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/log-analysis){:new_window} 查看其数据日志。

## 2018 年 12 月
{: #december-2018}

### 后端加密和数据日志转发
{: #backend-encryption-and-data-log-forwarding}

{{site.data.keyword.loadbalancer_full}} 现在支持后端加密和转发数据日志的功能。后端加密允许端到端数据流量加密，包括负载均衡器与后端服务器之间的流量。通过数据日志转发，您可以将数据日志从负载均衡器发送到 IBM Bluemix Log Analysis 服务。

## 2018 年 8 月
{: #august-2018}

### 第 7 层支持
{: #layer-7-support-1}

{{site.data.keyword.loadbalancer_full}} 现在支持第 7 层负载均衡。通过第 7 层 (L7) 支持，流量可以重定向到 URL、拒绝流量或将流量分配给 L7 池成员，包括裸机和虚拟服务器实例。使用第 7 层策略和规则对入局数据流量进行分类。这些策略定义数据流量与关联的规则匹配时要执行的操作。

请参阅[第 7 层负载均衡](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing)获取更多详细信息。

## 2018 年 4 月 
{: #april-2018}

### 水平伸缩
{: #horizontal-scaling}

{{site.data.keyword.loadbalancer_full}} 现在将随着负载的增加自动扩展，并随着负载的减少而缩减。创建负载均衡器时，一开始有两个设备，但是当监视系统检测到负载增加时，设备数量可以增加到 16 个（截至本文执笔时）。每个活动设备的 IP 地址将作为 DNS A 记录添加到负载均衡器的标准域名 (FQDN) 。

### 内部负载均衡器
{: #internal-load-balancer-1}

现在，{{site.data.keyword.loadbalancer_full}} 的高要求“内部”版本已可用。此负载均衡器不向公众公开，但是仍可用于对其 IBM Cloud 专用网络中的应用程序进行负载均衡（例如，在多层部署中，如图所示）。

![内部负载均衡器](./images/InternalLB.png)

它不但安全，还与公共端先前版本的 {{site.data.keyword.loadbalancer_full}} 保持一致。

### 监视度量值
{: #monitoring-metrics-2}

您现在可以利用“IBM Cloud Monitoring”服务来监视与负载均衡器和应用程序关联的以下性能指标：

* 吞吐量
* 连接速率
* 活动连接数

![监视度量值](./images/Metrics.png)

负载均衡器 Web UI 收集并显示最多两周的样本。还可以在 IBM Cloud Monitoring 服务门户网站上查看这些数据。如果您需要两周之前的数据，根据您可能发送到 Cloud Monitoring 实例的其他云度量值的量，您可能需要升级监视套餐。请参阅[监视度量值](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer)获取更多详细信息。

此功能需要您的 IBM Cloud IaaS 和 PaaS 帐户链接在一起，链接帐户只需[简单几步](/docs/account?topic=account-unifyingaccounts)。

### 密码套件定制
{: #cipher-suite-custom-1}

现在，可以定制在负载均衡器配置为执行 SSL 终止时使用的密码套件。

在 {{site.data.keyword.loadbalancer_full}} 上启用 SSL 终止（通过选择 **HTTPS** 作为前端协议）时，将启用精心选择的符合最佳安全实践的一组缺省密码套件。IBM 将密切关注可能发现的任何新漏洞，并相应地更新列表。此列表以及软件和硬件组件的无缝安全更新将有助于时刻确保应用程序的安全。

请参阅[定制密码套件](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application)获取更多详细信息。
