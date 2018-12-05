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


# 入门
要开始使用 IBM Cloud Load Balancer，您将需要两个主要项目：

* IBM 帐户：[IBM 标识 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/account/us-en/signup/register.html)
* IBM 服务器，可以是[裸机](/docs/bare-metal/about.html#getting-started-with-bare-metal-servers)，或者[虚拟服务器实例 (VSI)](/docs/vsi/vsi_index.html#getting-started-with-virtual-servers)

如果您在获取 **IBM 标识**帐户时需要帮助，请联系 [IBM 销售代表 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud-computing/bluemix/contact-us) 获取其他指导。

如果您已经拥有现有的 IBM Cloud Infrastructure (SoftLayer) 帐户，那么可以[链接帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/account/softlayerlink.html#link_user_account) 至 IBM 标识。

## 订购负载均衡器

要订购 IBM Cloud Load Balancer 服务，请从 [IBM Cloud 目录](https://console.bluemix.net/catalog/infrastructure/load-balancer-group)中选择**网络 > 负载均衡器 > IBM Cloud Load Balancer**。登录或创建新帐户，然后执行以下过程：

1. 选择数据中心并复查服务套餐。单击**下一步**。
2. 选择要将 Load Balancer 部署到的子网。您的 Load Balancer 服务实例将在此子网上具有其中一个网络接口：请确保应用程序服务器位于此子网上或可从此子网进行访问。如果必要，请启用 VLAN 生成。单击**下一步**。
3. 定义您的基本服务参数，如名称、描述、前端和后端应用程序协议和端口，以及负载均衡方法。 

	您可以在初始服务创建期间，最多定义两个协议。您可以在创建服务后，定义多达 10 个协议。您还必须使用唯一的前端端口。 
	
	完成后，单击**下一步**。
	
4. 根据需要调整运行状况检查参数，否则使用缺省设置。单击**下一步**。
5. 关联 Load Balancer 背后的一个或多个服务器实例。您将仅会看到属于数据中心本地的服务器实例。单击**下一步**。
6. 复查摘要页面，然后单击**创建**。

	摘要页面会显示您刚刚创建的 Load Balancer 服务实例。请注意**状态**字段。`Offline` 状态表示 Load Balancer 未在运行中。在状态更改为 `Online` 之前，不会进行任何新的配置，也不会提供任何负载均衡服务。您可能需要刷新屏幕，才能查看当前状态。

	单击此页面上的服务名称将带您进入服务概述页面。您可以浏览至**协议**、**运行状况检查**和**服务器实例**选项卡，以进一步编辑配置。

请参阅[如何创建 IBM Cloud Load Balancer 并将其用于弹性服务器负载均衡](reliability-guide.html)，获取分步配置指导。
