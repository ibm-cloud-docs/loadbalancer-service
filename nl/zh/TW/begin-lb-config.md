---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: parameters, load balancing, configure, protocol, health check

subcollection: loadbalancer-service


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# 配置 {{site.data.keyword.loadbalancer_full}} 參數
{: #configuring-ibm-cloud-load-balancer-parameters}

在您[建立負載平衡器](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-getting-started)之後，即可配置它，以進行彈性負載平衡。若要這樣做，請執行下列動作：

1. 命名負載平衡器，然後選擇性地新增說明。

	<img src="images/lb-config-basic.png" alt="圖片" style="width: 300px;"/>

2. 識別應用程式正在接聽的通訊協定及埠，以輸入應用程式設定檔的詳細資料。您可以對前端及後端使用相同的配置，或公開不同的前端埠（例如，基於安全緣故）。

3. 預設負載平衡方法是**循環式**。視您的應用程式需要而定，您可以從下拉清單將它變更為**加權循環式**或**最少連線**。

4. 您可以選擇啟用**階段作業綁定**。如果已啟用，則來自給定一般使用者（例如，具有相同來源 IP 的一般使用者）的所有要求都會送往相同的後端伺服器，時間長達系統所定義的「綁定」時間。

5. 您也可以對您的應用程式設定**最大連線限制**。

6. 按一下**新增通訊協定**，來指定應用程式可能在接聽的其他埠及通訊協定。請確定所有前端埠都是唯一的。您可以選擇 HTTP、HTTPS 或 TCP 作為前端通訊協定。

	<img src="images/lb-add-protocol.png" alt="圖片" style="width: 300px;"/>

	起始配置時，最多只能定義兩個埠。建立服務實例之後，稍後可能會新增其他埠。如需所容許埠數上限的相關資訊，請參閱[埠數限制](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-virtual-ports-i-can-define-with-my-load-balancer-service-)。
{:note:}

7. 如果選擇 HTTP 作為後端通訊協定，則 {{site.data.keyword.loadbalancer_full}} 會終止送入的 HTTPS（透過 SSL 的 HTTP）連線，並與後端應用程式伺服器進行純文字 HTTP 通訊，以及從伺服器卸載處理器密集的 SSL 作業。如果選取的後端通訊協定為 HTTPS，則會加密負載平衡器與後端伺服器之間的資料流量。您必須上傳「SSL 憑證」。請從下拉清單選取其中一個可用的憑證。  

	<img src="images/lb-ssl-cert.png" alt="圖片" style="width: 300px;"/>

	如果您沒有現有的憑證，請按一下**新增憑證**。這會將您帶往 IBM Cloud 憑證服務，您可以在其中購買新憑證或上傳現有憑證。

	新增憑證之後，請回到負載平衡器配置頁面，然後按一下「SSL 憑證」下拉清單下方的重新整理圖示，以檢視及新增新上傳的憑證。

	<img src="images/order-ssl-cert.png" alt="圖片" style="width: 300px;"/>

	<img src="images/refresh-cert.png" alt="圖片" style="width: 300px;"/>

	絕對不要刪除與 HTTPS 接聽器相關聯的任何憑證，因為這可能會導致功能發生問題。
  {: note}

8. 按**下一步**。

## 配置性能檢查
{: #configure-health-checks}

每個應用程式埠的性能檢查定義都是必要的。這些是前一個基本配置功能表中所識別的後端埠。

<img src="images/config-health-check.png" alt="圖片" style="width: 300px;"/>

系統會預先移入這些後端埠的預設性能檢查配置。您可以自訂下列設定，以符合應用程式需要。

* **間隔**：連續兩次性能檢查嘗試之間的間隔（以秒為單位）
* **逾時**：系統將等待性能檢查要求之回應的時間量上限
* **最大嘗試次數**：將埠宣告為性能不佳之前，系統將進行的額外性能檢查嘗試次數上限
* **路徑**：性能檢查的 HTTP URL 路徑     

按**下一步**，以啟用您的選擇。

## 下一步為何？
{: #what-s-next}

[識別應用程式的資源](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-identifying-your-application-server-resources)，例如原始儲存區及性能檢查機制。
