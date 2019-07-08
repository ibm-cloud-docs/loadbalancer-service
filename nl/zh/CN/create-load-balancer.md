---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: create, new, load balancer

subcollection: loadbalancer-service


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}

# 创建 IBM Cloud Load Balancer
{: #creating-an-ibm-cloud-load-balancer}

要创建 IBM© Cloud Load Balancer 服务，请执行以下过程：

1. 从浏览器，打开[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://control.softlayer.com/){: new_window}，并登录您的帐户。

2. 单击**目录**，然后在“基础架构”部分中，浏览至**网络 > Load Balancer**。

	<img src="images/catalog-load-balancer.png" alt="图样" style="width: 600px;"/>

3. 选择 **IBM Cloud Load Balancer**（缺省选择），然后单击**创建**。

	如果您看到的是**升级**而不是**创建**，那么必须通过执行[这些步骤](/docs/account?topic=account-unifyingaccounts)来链接 IBM Cloud Infrastructure (SoftLayer) 帐户

	<img src="images/create-load-balancer.png" alt="图样" style="width: 600px;"/>

4. 从**数据中心**下拉列表中选择首选数据中心，复查信息，然后单击**下一步**。

	<img src="images/select-datacenter.png" alt="图样" style="width: 600px;"/>

5. 指定 Load Balancer 类型。

	对于需要访问公用因特网的面向因特网的应用程序，请选择**公共（面向因特网）**。

	<img src="images/select-lb-type.png" alt="图样" style="width: 600px;"/>

	缺省情况下，公共负载均衡器会接收来自 IBM 全局地址池的全局唯一公共 IP 地址。但是，如果您希望为其分配自己的地址池中的公共地址，或者希望将其部署在帐户中的防火墙服务后面，请检查公用子网是否有[足够的 IP 地址](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting)，然后选择**从帐户中的公用子网分配**。

	对于不需要访问公用因特网的仅限内部的应用程序，请选择**内部（专用）**类型。

	<img src="images/lb-type-private.png" alt="图样" style="width: 500px;"/>

	对于面向因特网的负载均衡器和内部负载均衡器类型，请选取要部署负载均衡器的帐户中的其中一个专用子网。应用程序服务器必须可从此子网进行访问。如果必要，请启用 VLAN 生成以确保相应的网络连接。

	如果看不到任何专用子网，请单击**上一步**，然后选择具有专用子网的其他数据中心。

6. 单击**下一步**以完成配置。

## 接下来做什么
{: #whats-next-2}
使用[基本参数](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters)配置 Load Balancer。
