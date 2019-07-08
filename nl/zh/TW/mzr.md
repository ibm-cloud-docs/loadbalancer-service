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

# 多區域地區 (MZR) 概觀
{: #multi-zone-region-mzr-overview}

建立負載平衡器時，將指定要建立在其中的資料中心。如果該資料中心是「多區域地區 (MZR)」的一部分，則會在兩個不同的資料中心中實例化負載平衡器節點。例如，`us-south` 是個 MZR，包含 `dal10`、`dal12`、`dal13`。如果客戶在資料中心 `dal13` 中建立負載平衡器，則會在 `dal13`、`dal10` 或 `dal12` 中實例化節點。一般而言，您不會在資料流量中看到任何明顯的變更。當與資料中心的通訊中斷時，MZR 支援非常好用。負載平衡器會繼續運作，因為另一個節點位於不同的資料中心。

目前，下列資料中心是 MZR 的一部分：

| MZR 名稱 | 資料中心 |
| ---------|--------------|
| us-south | dal10、dal12、dal13 |
| us-east | wdc04、wdc06、wdc07 |
| eu-gb | lon04、lon05、lon06 |
| eu-de | fra02、fra04、fra05 |
| jp-tok | tok02、tok04、tok05 |
| au-syd | syd01、syd04、syd05 |


## MZR 需求
{: #mzr-requirements}
多區域地區的需求如下：
* 您選取的資料中心應為 MZR 的一部分。上表列出地區以及每個地區中的資料中心。
* 您的帳戶必須啟用 VLAN Spanning 或 VRF。
* 在 MZR 的資料中心中，您的帳戶中必須有專用子網路。在資料中心中建立運算裝置會導致實例化專用子網路。

如果您選取的資料中心不是 MZR 的一部分，或者您的帳戶未啟用 VLAN Spanning 或 VRF，則負載平衡器的建立作業會預設回原始行為，即實例化您所指定資料中心中的所有負載平衡器節點。
