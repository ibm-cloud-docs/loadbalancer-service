---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: pricing, usage, month

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


# {{site.data.keyword.loadbalancer_full}} 定價
{: #ibm-cloud-load-balancer-pricing}

{{site.data.keyword.loadbalancer_full}} 定價是根據下列三個度量值，每月計算：

* 服務使用小時數
* 處理的資料
* 出埠公用頻寬 (Egress)

所有價格會依地理區域而有所不同。{{site.data.keyword.loadbalancer_full}} 服務所耗用的「出埠」公用頻寬是根據標準資料傳送費用（即[每 GB 美金 0.09 元 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/bandwidth)）來計費。
{: note}

下圖詳述 {{site.data.keyword.loadbalancer_full}} 針對每個月使用 4500 GB 進行公用負載平衡之客戶定價的範例：

| | 每月 | 速率 | 成本 |
| ------------- | ------------- | ------------- | ------------- |
| **服務使用** | 720 小時 | $0.025/小時 | $18/月 |
| **處理的資料** | 4500GB | $0.008/GB | $36/月 |

上述情境的費用總計為 $54/月加上標準資料傳送費用[每 GB 美金 0.09 元 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/bandwidth)。

![定價](./images/pricing.png)


所有價格會依地理區域而有所不同；範例及圖表中的定價是以美金為單位的達拉斯定價；未在圖表中顯示的是服務使用費用，即 $0.025/小時。
{: note}

若要查看您地區的特定計價資訊，請逐步完成我們的簡單[註冊處理程序 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/infrastructure/load-balancer-group)。
