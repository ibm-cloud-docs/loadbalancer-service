---

copyright:
  years: 2017, 2018
lastupdated: "2019-02-19"

keywords: updates, additions, imporvements

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

# {{site.data.keyword.loadbalancer_full}} 的最近更新
{: #recent-updates-for-ibm-cloud-load-balancer}

瞭解 {{site.data.keyword.loadbalancer_full}} 中新增及更新的功能。

## 2019 年 2 月
{: #february-2019}

### 資料日誌
{: #data-logs}

{{site.data.keyword.loadbalancer_full}} 現在支援資料日誌轉遞。啟用資料日誌後，您的負載平衡器日誌資料將會轉遞至 [IBM Cloud Log Analysis 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}。客戶可以透過 [IBM Cloud Log Analysis 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/log-analysis){:new_window} 檢視其資料日誌。

## 2018 年 12 月
{: #december-2018}

### 後端加密及資料日誌轉遞
{: #backend-encryption-and-data-log-forwarding}

{{site.data.keyword.loadbalancer_full}} 現在支援後端加密以及轉遞資料日誌的功能。後端加密容許端對端資料流量加密，包括負載平衡器與後端伺服器之間的資料流量。資料日誌轉遞可讓您將資料日誌從負載平衡器傳送至「IBM Bluemix Log Analysis 服務」。

## 2018 年 8 月
{: #august-2018}

### 第 7 層支援
{: #layer-7-support-1}

{{site.data.keyword.loadbalancer_full}} 現在支援第 7 層負載平衡。使用第 7 層 (L7) 支援，可以將資料流量重新導向至 URL、拒絕資料流量，或將資料流量分佈到 L7 儲存區成員，包括裸機及虛擬伺服器實例。送入的資料流量是使用第 7 層原則及規則進行分類。這些原則定義在資料流量符合與其相關聯的規則時要採取的動作。

如需其他詳細資料，請參閱[第 7 層負載平衡](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-layer-7-load-balancing)。

## 2018 年 4 月
{: #april-2018}

### 水平調整
{: #horizontal-scaling}

現在，當 {{site.data.keyword.loadbalancer_full}} 的負載增加時它會自動擴增，而負載降低時則會縮減。建立負載平衡器時，會從兩個應用裝置開始，但監視系統偵測到負載增加時，應用裝置數目最多可以增加到 16（截至撰寫本文時）。每一個作用中應用裝置的 IP 位址會當作 DNS A-Records 新增至負載平衡器的「完整網域名稱 (FQDN)」。

### 內部負載平衡器
{: #internal-load-balancer-1}

現在提供高度需求的 {{site.data.keyword.loadbalancer_full}}「內部」版本。此負載平衡器不會公開給大眾使用，但仍可用來平衡其 IBM Cloud 專用網路內的應用程式（例如，在多層部署中，如圖所示）。

![內部負載平衡器](./images/InternalLB.png)

它既安全且與公用端上的舊版 {{site.data.keyword.loadbalancer_full}} 一致。

### 監視度量值
{: #monitoring-metrics-2}

您現在可以運用 IBM Cloud Monitoring 服務，來監視與負載平衡器及應用程式相關聯的效能度量值：

* 傳輸量
* 連線速率
* 作用中連線

![監視度量值](./images/Metrics.png)

負載平衡器 Web 使用者介面最多收集及顯示兩週的樣本。也可以在 IBM Cloud Monitoring 服務入口網站上檢視資料。如果您需要超過兩週的資料，則根據您可能傳送至「雲端監視」實例之其他雲端度量值的數量，可能需要升級您的監視方案。如需其他詳細資料，請參閱[監視度量值](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer)

此特性需要鏈結您的 IBM Cloud IaaS 及 PaaS 帳戶，只需幾個[簡單步驟](/docs/account?topic=account-unifyingaccounts)即可完成。

### 密碼組合自訂作業
{: #cipher-suite-custom-1}

您現在可以自訂在負載平衡器配置為進行 SSL 終止時所使用的密碼組合。

當您在 {{site.data.keyword.loadbalancer_full}} 啟用 SSL 終止（方法為選取 **HTTPS** 作為前端通訊協定）時，會啟用仔細選取的一組預設密碼組合，其符合安全最佳作法。IBM 會仔細監看任何可能探索到的新漏洞，並相應地更新清單。此功能連同軟體及硬體元件的無縫安全更新可協助保持您的應用程式始終安全無虞。

如需其他詳細資料，請參閱[自訂密碼組合](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application)。
