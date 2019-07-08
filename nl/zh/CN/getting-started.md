---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# IBM Cloud Load Balancer 入门
{: #getting-started}

要开始使用 IBM© Cloud Load Balancer，您将需要两个主要项目：

* IBM 帐户：[IBM 标识 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* IBM 服务器，可以是[裸机](/docs/bare-metal?topic=bare-metal-about)，或者[虚拟服务器实例 (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

如果您在获取 **IBM 标识**帐户时需要帮助，请联系 [IBM 销售代表 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} 获取其他指导。

如果您已经拥有现有的 IBM Cloud Infrastructure (SoftLayer) 帐户，那么可以[链接帐户](/docs/account?topic=account-unifyingaccounts)至 IBM 标识。

## 订购负载均衡器
{: #ordering-a-load-balancer}

要订购 IBM Cloud Load Balancer 服务，请从 [IBM Cloud 目录 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window} 选择 **IBM Cloud Load Balancer**。然后，单击**创建**并执行以下过程：

1. 定义基本服务参数，例如名称和描述。
2. 选择数据中心。
3. 将负载均衡器类型选择为**公共**。
4. 选择要将 Load Balancer 部署到的子网。

  您的 Load Balancer 服务实例将在此子网上具有其中一个网络接口：请确保应用程序服务器位于此子网上或可从此子网进行访问。如果必要，请启用 VLAN 生成。
  {: note}

5. 创建前端和后端应用程序协议和端口。

  有关此配置的更多信息，请参阅[配置 IBM Cloud Load Balancer 参数](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters)。
  {: note}

6. 要启用 SSL 卸载，请将前端协议设置为 HTTPS，将后端协议设置为 HTTP。然后从“证书”下拉框中选择您的 SSL 证书。

  所有现有 SSL 证书都通过 [IBM Cloud 证书库 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/classic/security/sslcerts){:new_window} 进行管理。如果您没有 SSL 证书，可以在此处进行创建。

7. 根据需要调整运行状况检查参数，否则使用缺省设置。

  有关运行状况检查参数的更多信息，请参阅 [IBM Cloud Load Balancer 参数](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks)。
  {: note}

8. 单击**连接服务器**，以关联负载均衡器后面的一个或多个服务器实例。您将仅会看到属于数据中心本地的服务器实例。
9. 复查此页面，确认“服务协议”，然后单击**创建**。

此时会显示负载均衡器列表，其中包含您的所有服务实例。

单击此页面上的服务名称将带您进入服务概述页面。您可以浏览至**协议**、**运行状况检查**和**服务器实例**选项卡，以进一步编辑配置。

新创建的负载均衡器可能不会立即在此列表中显示。几分钟之后，新的负载均衡器将显示为灰色，表示其状态为 `Offline`。再过几分钟之后，新的负载均衡器将显示为绿色，表示其状态为 `Online`。您可能需要刷新屏幕才能看到这些更改。
{: note}

请参阅[如何使用 IBM Cloud Load Balancer 实现弹性服务器负载均衡](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing)，以获取有关配置新 Cloud Load Balancer 的逐步指导信息。
