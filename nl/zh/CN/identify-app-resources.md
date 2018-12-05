---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 识别应用程序服务器资源
从底部的表中找到您的**服务器实例**，然后单击 **+** 以将其添加到负载均衡器后面。您可以从帐户中的 IBM Cloud 虚拟服务器实例 (VSI) 和裸机服务器中进行选择。

这些服务器实例必须是您部署 Load Balancer 服务的数据中心的本地实例。此外，还可以添加来自同一城市的相邻数据中心的服务器实例（例如，如果数据中心名称的前三个字母相同）。

<img src="images/locate-server-instance.png" alt="图样" style="width: 300px;"/>

单击**下一步**。

**注：** 

1. 仅当使用**加权循环法**负载均衡方法时，服务器**权重**才适用。缺省权重为 50，范围为 0-100。对于其他负载均衡方法，权重为灰显。
2. 请参阅[应用程序服务器数的限制](faqs.html#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-)，获取有关应用程序服务器数最大限制的更多信息。

## 接下来做什么
下订单之前[复查订单内容](order-lb.html)。
