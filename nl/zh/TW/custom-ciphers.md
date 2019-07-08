---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: cipher, suite, https

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

# 選擇 HTTPS 應用程式的偏好密碼組合
{: #choosing-a-preferred-cipher-suite-for-your-https-application}

協助 IBM© Cloud Load Balancer 的密碼演算法會形成與其 HTTP 用戶端之間的安全連線。

IBM 提供一套核准的密碼供您選擇，讓您保護負載平衡器與用戶端之間的通訊安全。

您可以為現有負載平衡器選擇偏好的密碼組合，或在建立新的負載平衡器時指定它們。

## 選擇現有負載平衡器的密碼
{: #choosing-ciphers-for-an-existing-load-balancer}

若要選擇現有負載平衡器的密碼組合配置，請導覽至客戶入口網站中的負載平衡器畫面，然後按一下「通訊協定」標籤。如果未選取 HTTPS 作為前端通訊協定，您將看不到密碼組合清單。

  <img src="images/DetailsFlow-HTTPSUnselected.png" alt="圖片" style="width: 700px;"/>

選取 HTTPS 作為前端通訊協定，然後可用的「密碼組合」將會顯示在「負載平衡器詳細資料」下方。

  <img src="images/DetailsFlow-CustomCipherSelection.png" alt="圖片" style="width: 600px;"/>

「密碼」表格是可編輯的，容許您選取想要的密碼組合來進行 SSL 信號交換。按一下**編輯**、選取您想要實作的「密碼」，然後按一下**儲存**。

如需支援的密碼清單，請參閱 [SSL 卸載](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer)。
{: note}

## 在建立新的負載平衡器時選擇密碼
{: #choosing-ciphers-when-creating-a-new-load-balancer}

若要在建立新的負載平衡器時選擇密碼組合，請執行下列動作：

1. 遵循[建立負載平衡器](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-an-ibm-cloud-load-balancer#creating-an-ibm-cloud-load-balancer)的指示。

2. 「密碼組合」配置只適用於 HTTPS 前端通訊協定。當您到達**新增通訊協定**小節的配置步驟時，請選擇 **HTTPS 通訊協定**。

	<img src="images/ProvisioningFlow-CustomCiphers.png" alt="圖片" style="width: 500px;"/>

3. 配置中已選取一組預設密碼，但只有在完成配置負載平衡器之後，您才能編輯這組密碼。

	遵循主題中的指示，以完成負載平衡器配置。在完成之後，您可以在**負載平衡器詳細資料**下的**通訊協定**標籤中看到預設密碼清單。

	<img src="images/View-CustomCiphers.png" alt="圖片" style="width: 600px;"/>

4. 「密碼」表格是可編輯的，容許您選取想要的密碼組合來進行 SSL 信號交換。按一下**編輯**、選取您想要實作的「密碼」，然後按一下**儲存**。

	如需支援的密碼清單，請參閱 [SSL 卸載](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer)。
  {: note}
