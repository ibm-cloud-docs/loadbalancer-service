---

copyright:
  years: 2018
lastupdated: "2018-11-12"

keywords: vlan, troubleshooting, problems, questions

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

# 負載平衡器 VLAN Spanning 疑難排解
{: #load-balancer-vlan-spanning-troubleshooting}

本主題提供您在負載平衡器以及連接至負載平衡器的運算實例位在不同的子網路時可能遇到的一般問題相關資訊。必須針對負載平衡器啟用 VLAN Spanning，才能將要求傳遞及轉發至位在不同子網路的運算實例。

1. 登入[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://control.softlayer.com){:new_window}，導覽至**網路 > IP 管理**，然後按一下 **VLAN**。

2. 將 **VLAN Spanning** 切換為**開啟**。

<img src="images/vlan-spanning.png" alt="圖片" style="width: 500px;"/>

這會開啟負載平衡器與其運算實例之間的通訊。
