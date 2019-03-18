---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 開始使用 IBM Cloud Load Balancer
{: #getting-started-with-ibm-cloud-load-balancer}

若要開始使用 IBM© Cloud Load Balancer，您將需要兩個主要項目：

* IBM 的帳戶：[IBM ID ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* IBM 伺服器，即[祼機](/docs/bare-metal?topic=bare-metal-about)或[虛擬伺服器實例 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers#getting-started-with-virtual-servers)

如果您需要在取得 **IBM ID** 帳戶方面的協助，請與 [IBM 業務代表 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} 聯絡，以取得其他指引。

如果您具有現有的「IBM Cloud 基礎架構 (SoftLayer)」帳戶，則可以[鏈結您的帳戶](/docs/account?topic=account-unifyingaccounts)與您的 IBM ID。

## 訂購負載平衡器

若要訂購 IBM Cloud Load Balancer 服務，請從 [IBM Cloud 型錄  ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/infrastructure/load-balancer-group){:new_window}，選取**網路 > 負載平衡器 > IBM Cloud Load Balancer**。登入或建立新帳戶，然後執行下列程序：

1. 選取資料中心，並檢閱服務方案。按**下一步**。
2. 選取您要部署負載平衡器的子網路。在此子網路上，負載平衡器服務實例會有它的一個網路介面。請確定應用程式伺服器位在此子網路上或可透過此子網路連接。必要的話，請啟用 VLAN Spanning。按**下一步**。
3. 定義基本服務參數（例如名稱、說明、前端及後端應用程式通訊協定和埠）及負載平衡方法。 

	在起始服務建立期間，最多可以定義兩個通訊協定。建立服務之後，最多可以定義十個通訊協定。您也必須使用唯一前端埠。 
	
	完成之後，請按**下一步**。
	
4. 視需要調整性能檢查參數，否則，請使用預設值。按**下一步**。
5. 與一個以上受負載平衡器保護的伺服器實例建立關聯。您只會看到資料中心的本端伺服器實例。按**下一步**。
6. 檢閱摘要頁面，然後按一下**建立**。

	摘要頁面會顯示您剛剛建立的負載平衡器服務實例。請記下**狀態**欄位。`離線`狀態表示負載平衡器未作用。除非狀態變更為`線上`，否則無法進行任何新的配置，而且無法提供任何負載平衡服務。您可能需要重新整理畫面，才能看到現行狀態。

	在此頁面上按一下服務名稱，會帶領您前往服務概觀頁面。您可以導覽至**通訊協定**、**性能檢查**及**伺服器實例**標籤，以進一步編輯配置。

如需逐步配置指引，請參閱[如何建立及使用 IBM Cloud Load Balancer 以進行彈性伺服器負載平衡](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing)。
