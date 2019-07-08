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

# 負載平衡器佈建疑難排解
{: #load-balancer-provisioning-troubleshooting}

本主題提供您在建立新的 IBM© Cloud Load Balancer 實例時可能遇到的一般問題相關資訊。

## 子網路中的 IP 位址不足
{: #insufficient-ip-addresses-in-your-subnet}

IBM Cloud Load Balancer 需要至少兩個來自其專用子網路的可用 IP 位址。此外，如果負載平衡器是公用負載平衡器，而且未使用 **IBM 系統儲存區**選項，則還至少需要您公用子網路中的兩個可用 IP 位址。

請遵循下面的步驟，以檢查子網路中的可用 IP。

1. 移至[客戶入口網站![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://control.softlayer.com){:new_window}，然後選取**網路 > IP 管理 > 子網路**，來導覽至子網路區段。

2. 按一下您要檢查其可用 IP 的子網路。

	<img src="images/subnet_list.png" alt="圖片" style="width: 600px;"/>

3. 所選取子網路的詳細資料頁面，會顯示該子網路中所有 IP 的狀態。

## 公用及專用 VLAN 上的防火牆問題
{: #issues-with-firewalls-on-public-and-private-vlans}

如需容許透過防火牆之 IP 範圍的相關資訊，請參閱 [IBM Cloud IP 範圍](/docs/infrastructure/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges)主題。

## 檢視負載平衡器錯誤訊息
{: #viewing-load-balancer-error-messages}

若要檢視負載平衡器的錯誤訊息，請執行下列程序：

1. 按一下清單頁面中的負載平衡器，以檢視其詳細資料。
2. 將滑鼠指標移至負載平衡器狀態旁邊的錯誤符號。

<img src="images/lbaas_error_message.png" alt="圖片" style="width: 500px;"/>

如果負載平衡器處於 `ERROR` 狀態，則無法予以回復，因此必須予以刪除。
