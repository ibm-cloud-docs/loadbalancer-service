---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: cipher, suite, https

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

# 为 HTTPS 应用程序选择首选密码套件
{: #choosing-a-preferred-cipher-suite-for-your-https-application}

密码算法可帮助 IBM© Cloud Load Balancer 建立与其 HTTP 客户机的安全连接。

IBM 提供了一套经核准的密码供您选择，以便保护 Load Balancer 与客户机之间的通信。

您可以为现有负载均衡器选择首选密码套件，也可以在创建新负载均衡器时指定密码套件。

## 为现有 Load Balancer 选择密码
{: #choosing-ciphers-for-an-existing-load-balancer}

要为现有 Load Balancer 选择密码套件配置，请在客户门户网站中浏览至 Load Balancer 屏幕，然后单击“协议”选项卡。如果未选择 HTTPS 作为前端协议，那么您不会看到密码套件列表。

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="图样" style="width: 700px;"/>

选择 HTTPS 作为前端协议，随后可用的密码套件会在“Load Balancer 详细信息”下显示。

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="图样" style="width: 600px;"/>

密码表是可编辑的，允许您选择所需的密码套件用于 SSL 握手。单击**编辑**，选择要实施的密码，然后单击**保存**。

要获取受支持密码的列表，请参阅 [SSL 卸载](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer)。
{: note}

## 创建新的 Load Balancer 时选择密码
{: #choosing-ciphers-when-creating-a-new-load-balancer}

要在创建新的 Load Balancer 时选择密码套件，请执行以下操作：

1. 遵循指示信息以[创建 Load Balancer](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-an-ibm-cloud-load-balancer#creating-an-ibm-cloud-load-balancer)。

2. 密码套件配置仅适用于 HTTPS 前端协议。执行到**添加协议**部分的配置步骤时，请选择 **HTTPS 协议**。

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="图样" style="width: 500px;"/>

3. 配置中已选择一组缺省密码，但仅当您完成配置 Load Balancer 后才能对其进行编辑。

	遵循主题中的指示信息完成 Load Balancer 配置。完成后，您可以在**协议**选项卡的 **Load Balancer 详细信息**下看到缺省密码列表。

	<img src="images/View-CustomCiphers.png" alt="图样" style="width: 600px;"/>

4. 密码表是可编辑的，允许您选择所需的密码套件用于 SSL 握手。单击**编辑**，选择要实施的密码，然后单击**保存**。

	要获取受支持密码的列表，请参阅 [SSL 卸载](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer)。
  {: note}
