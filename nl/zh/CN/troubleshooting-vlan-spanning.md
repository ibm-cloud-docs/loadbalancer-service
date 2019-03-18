---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Load Balancer VLAN 生成故障诊断
{: #load-balancer-vlan-spanning-troubleshooting}

本主题提供有关 Load Balancer 和连接到 Load Balancer 的计算实例位于不同子网中时，可能会遇到的常见问题的信息。必须启用 VLAN 生成，Load Balancer 才能与位于不同子网中的计算实例进行通信并向其转发请求。

1. 登录到[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://control.softlayer.com){:new_window}，导航至**网络 > IP 管理**，然后单击 **VLAN**。

2. 将 **VLAN 生成**切换为**开启**。

<img src="images/vlan-spanning.png" alt="图样" style="width: 500px;"/>

这将打开 Load Balancer 与其计算实例之间的通信。
