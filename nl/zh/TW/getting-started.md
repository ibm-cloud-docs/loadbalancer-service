---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# 開始使用 IBM Cloud Load Balancer
{: #getting-started}

若要開始使用 IBM© Cloud Load Balancer，您將需要兩個主要項目：

* IBM 的帳戶：[IBM ID ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* IBM 伺服器，即[祼機](/docs/bare-metal?topic=bare-metal-about)或[虛擬伺服器實例 (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen)

如果您需要在取得 **IBM ID** 帳戶方面的協助，請與 [IBM 業務代表 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} 聯絡，以取得其他指引。

如果您具有現有的「IBM Cloud 基礎架構 (SoftLayer)」帳戶，則可以[鏈結您的帳戶](/docs/account?topic=account-unifyingaccounts)與您的 IBM ID。

## 訂購負載平衡器
{: #ordering-a-load-balancer}

若要訂購 IBM Cloud Load Balancer 服務，請從 [IBM Cloud 型錄  ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window} 選取 **IBM Cloud Load Balancer**。接著，按一下**建立**並執行下列程序：

1. 定義基本服務參數，例如名稱及說明。
2. 選取資料中心。
3. 選取**公用**負載平衡器類型。
4. 選取您要部署負載平衡器的子網路。

  在此子網路上，負載平衡器服務實例會有它的一個網路介面。請確定應用程式伺服器位在此子網路上或可透過此子網路連接。必要的話，請啟用 VLAN Spanning。
  {: note}

5. 建立前端和後端應用程式的通訊協定及埠。

  如需此配置的相關資訊，請參閱[配置 IBM Cloud Load Balancer 參數](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters)。
  {: note}

6. 若要啟用 SSL 卸載功能，請將前端通訊協定設為 HTTPS，並將後端通訊協定設為 HTTP。接著，從「憑證」下拉方框中選取「SSL 憑證」。

  所有現有的 SSL 憑證都是透過 [IBM Cloud 憑證庫 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/classic/security/sslcerts){:new_window} 進行管理。如果您沒有 SSL 憑證，可以在這裡新增一個憑證。

7. 視需要調整性能檢查參數，否則，請使用預設值。

  如需性能檢查參數的相關資訊，請參閱 [IBM Cloud Load Balancer 參數](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks)。
  {: note}

8. 按一下**連接伺服器**，使一個以上受負載平衡器保護的伺服器實例建立關聯。您只會看到資料中心的本端伺服器實例。
9. 檢閱該頁面，確認「服務合約」，然後按一下**建立**。

即會顯示 Load Balancer 清單，其中顯示所有的服務實例。

在此頁面上按一下服務名稱，會帶領您前往服務概觀頁面。您可以導覽至**通訊協定**、**性能檢查**及**伺服器實例**標籤，以進一步編輯配置。

新建立的負載平衡器可能不會立即顯示在此清單中。幾分鐘之後，新的負載平衡器將以灰色顯示，表示其狀態為 `Offline`。再過幾分鐘後，新的負載平衡器會顯示綠色，表示其為 `Online`。您可能需要重新整理畫面，才能看到這些變更。
{: note}

如需配置新 Cloud Load Balancer 的逐步指引，請參閱[如何使用 IBM Cloud Load Balancer 以進行彈性伺服器負載平衡](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing)。
