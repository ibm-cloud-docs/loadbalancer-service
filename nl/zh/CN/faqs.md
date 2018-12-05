---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:faq: data-hd-content-type='faq'}

# 常见问题及解答

本节包含有关 IBM Cloud Load Balancer 服务的一些常见问题的解答。

## {{site.data.keyword.BluSoftlayer_notm}} 中提供了多少负载均衡选项？
{:faq}

有关 IBM Load Balancer 产品的详细比较，请参阅[探索 Load Balancer](/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers)。

## 可以为 Load Balancer 使用不同的 DNS 名称吗？
{:faq}

由于为 Load Balancer 自动分配的 DNS 名称不可定制，您可以添加 CNAME（规范名称）记录来将首选 DNS 名称指向自动分配的 Load Balancer DNS 名称。 

例如，如果您的帐号为 123456，Load Balancer 部署于 `dal09` 数据中心且其名称为 `myapp`，那么自动分配的 Load Balancer DNS 名称为 `myapp-123456-dal09.lb.bluemix.net`。您的首选 DNS 名称为 `www.myapp.com`。您可以添加 CNAME 记录（通过用于管理 myapp.com 的 DNS 提供程序）将 `www.myapp.com` 指向 Load Balancer DNS 名称 `myapp-12345-dal09.lb.bluemix.net`。

## 使用 Load Balancer 服务可以定义的最大虚拟端口数是多少？
{:faq}

尝试创建新的 Load Balancer 服务时，您最多可以定义两个虚拟端口。在创建服务后，您可以定义附加虚拟端口。所允许的最大虚拟端口数目为 10。

## 可以与 Load Balancer 相关联的最大计算实例数是多少？
{:faq}

50.

## 后端计算实例位于的子网能否不同于 Load Balancer 的子网？
{:faq}

可以，Load Balancer 和连接到 Load Balancer 的计算实例可以位于不同的子网中，但需要启用 **VLAN 生成**，Load Balancer 才能与计算实例进行通信并向其转发请求。请参阅 [VLAN 生成故障诊断](troubleshooting-vlan-spanning.html)获取更多信息。

## 各种运行状况检查参数的缺省设置和允许值是什么？
{:faq}

缺省设置和允许值如下所示：

* **运行状况检查间隔：**缺省值为 5 秒，范围为 2 – 60 秒
* **运行状况检查响应超时：**缺省值为 2 秒，范围为 1 –59 秒
* **最大重试尝试次数：**缺省值为 2 次重试尝试，范围为 1 - 10 次重试

**注：**运行状况检查响应超时值必须始终小于运行状况检查时间间隔值。

## 可以将远程数据中心内的计算实例与此服务一起使用吗？
{:faq}

建议负载均衡器服务和计算实例位于相同数据中心本地。Load Balancer 服务的图形界面 (GUI) 不会显示来自其他远程数据中心的计算实例。但是，GUI 将包括同一城市其他数据中心的计算实例（例如，其名称的前三个字母相同的数据中心，如 DALxx）。您可以使用 API 接口添加来自任何远程数据中心的计算实例。

## SSL 卸载支持哪个 TLS 版本？
{:faq}

Cloud Load Balancer 服务支持具有 SSL 终止功能的 TLS 1.2。

下表详细说明受支持的密码（按优先顺序列出）：  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## 在帐户中可以创建的最大 Load Balancer 服务实例数是多少？
{:faq}

目前，最多可以创建 50 个服务实例。如果您需要更多实例，请联系 IBM 支持人员。 

## IBM Cloud Load Balancer 服务可与 VMWare 一起使用吗？
{:faq}

分配有 SoftLayer 可移植专用地址的 VMWare 虚拟机可以指定为负载均衡器的后端服务器。此功能当前仅在使用 API 时可用，在使用 Web UI (GUI) 时不可用。使用 API 添加的可移植专用 IP 在 GUI 中显示为“未知”，因为这些 IP 不是 SoftLayer 分配的。请注意，这种配置可用于其他管理程序，如 Xen 和 KVM。

分配有非 SoftLayer 地址（如 VMware NSX 网络）的 VMWare 虚拟机不可直接添加为负载均衡器的后端服务器。但是，根据您的配置，也许能够配置具有 SoftLayer 专用地址的中介（如 NSX 网关）作为负载均衡器的后端服务器（实际服务器为连接到由 VMware NSX 管理的网络的 VM）。

## 如果选择使用帐户下的公共 VLAN 来部署 Load Balancer，并且在公共 VLAN 上部署了防火墙，那么需要对防火墙执行哪些配置才能使用 Load Balancer 服务？
{:faq}

TCP 端口 56501 用于管理。请确保防火墙未阻止此端口以及应用程序端口的流量，否则负载均衡器供应将会失败。

## 如果将 Softlayer 帐户链接到 IBM Cloud 后看不到现有 Load Balancer 的监视度量值该怎么做？ 
{:faq}

链接帐户后，监视度量值将不可用于现有 Load Balancer。您必须重新创建 Load Balancer 或联系支持人员。新创建的 Load Balancer 的监视度量值将可用。

## Load Balancer IP 地址是固定的吗？
{:faq}

由于 Load Balancer 服务中内置的弹性，我们无法保证 Load Balancer 的 IP 地址保持不变。随着该服务向上或向下扩展，您将看到与实例的 FQDN 关联的可用 IP 发生变化。

**注：**您应该使用 FQDN 而不是高速缓存的 IP 地址。

## 如果在专用 VLAN 上部署了防火墙，那么需要对防火墙执行哪些配置才能使用 Load Balancer 服务？
{:faq}

请参阅 [IBM Cloud IP 范围](/docs/infrastructure/hardware-firewall-dedicated/ips.html#ibm-cloud-ip-ranges)主题，获取有关允许通过防火墙的 IP 范围的信息。

## 为什么在 UI 中看不到第 7 层配置？
{:faq}

目前，第 7 层支持仅通过公共 API 可用，但此功能将很快在 UI 中提供。请参阅 [API 文档](apis.html)的“第 7 层”部分获取更多信息。

## 我需要哪些信息来提交支持凭单？
{:faq}

要提交支持凭单，请提供产品名称（“IBM Cloud Load Balancer”）、Load Balancer 的 UUID（如果可能）和您的 Softlayer 帐号。浏览至给定 Load Balancer 的概述页面后，可以在 URL 中找到 UUID。
