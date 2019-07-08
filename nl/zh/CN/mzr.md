---

copyright:
  years: 2017, 2018
lastupdated: "2019-01-11"

keywords: mzr, overview, data centers

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

# 多专区区域 (MZR) 概述
{: #multi-zone-region-mzr-overview}

创建负载均衡器时，您将指定应在其中创建该负载均衡器的数据中心。如果该数据中心是多专区区域 (MZR) 的一部分，那么负载均衡器节点会在两个不同的数据中心内实例化。例如，`us-south` 是包含 `dal10`、`dal12` 和 `dal13` 的 MZR。如果客户在数据中心 `dal13` 中创建负载均衡器，那么节点会在 `dal13`、`dal10` 或 `dal12` 中实例化。通常情况下，流量不会出现任何显著变化。在与数据中心的通信中断时，MZR 支持非常有用。由于其他节点位于不同数据中心，因此负载均衡器将继续运作。

当前，以下数据中心是 MZR 的一部分：

| MZR 名称 | 数据中心 |
| ---------|--------------|
| us-south | dal10、dal12 和 dal13 |
| us-east | wdc04、wdc06 和 wdc07 |
| eu-gb | lon04、lon05 和 lon06 |
| eu-de | fra02、fra04 和 fra05 |
| jp-tok | tok02、tok04 和 tok05 |
| au-syd | syd01、syd04 和 syd05 |


## MZR 需求
{: #mzr-requirements}
多专区区域具有以下需求：
* 您选择的数据中心应为 MZR 的一部分。上表列出了区域以及每个区域中的数据中心。
* 您的帐户中必须启用 VLAN 生成或 VRF。
* 在 MZR 的数据中心内，您的帐户中必须存在专用子网。在数据中心内创建计算设备会使专用子网实例化。

如果选择的数据中心不是 MZR 的一部分，或者如果您的帐户中未启用 VLAN 生成或 VRF，那么创建负载均衡器将缺省为原始行为，即在您指定的数据中心内实例化所有负载均衡器节点。
