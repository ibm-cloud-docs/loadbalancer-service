---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: troubleshooting, provisioning, question, problem

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

# Load Balancer 供应故障诊断
{: #load-balancer-provisioning-troubleshooting}

本主题提供有关在创建 IBM© Cloud Load Balancer 新实例时可能会遇到的常见问题的信息。

## 子网中的 IP 地址不足
{: #insufficient-ip-addresses-in-your-subnet}

IBM Cloud Load Balancer 至少需要其专用子网有两个可用 IP 地址。此外，如果 Load Balancer 是公共负载均衡器，并且未使用 **IBM 系统池**选项，那么还需要公用子网中至少有两个可用 IP 地址。

遵循以下步骤检查子网中是否有可用 IP。

1. 转至[客户门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://control.softlayer.com){:new_window}，并通过选择**网络 > IP 管理 > 子网**来导航至“子网”部分。

2. 单击要检查其中是否有可用 IP 的子网。

	<img src="images/subnet_list.png" alt="图样" style="width: 600px;"/>

3. 所选子网的详细信息页面会显示该子网中所有 IP 的状态。

## 公用和专用 VLAN 上的防火墙问题
{: #issues-with-firewalls-on-public-and-private-vlans}

请参阅 [IBM Cloud IP 范围](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges)主题，获取有关允许通过防火墙的 IP 范围的信息。

## 查看 Load Balancer 错误消息
{: #viewing-load-balancer-error-messages}

要查看 Load Balancer 的错误消息，请执行以下过程：

1. 单击列表页面中的 Load Balancer 以查看其详细信息。
2. 将鼠标悬停在 Load Balancer 状态旁边的错误符号上。

<img src="images/lbaas_error_message.png" alt="图样" style="width: 500px;"/>

如果 Load Balancer 处于 `ERROR` 状态，那么无法对其进行恢复，必须将其删除。
