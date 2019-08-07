---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: about, load balancer, overview, features

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

# 關於 {{site.data.keyword.loadbalancer_full}}
{: #about-ibm-cloud-load-balancer}

{{site.data.keyword.loadbalancer_full}} 服務可協助客戶改善其企業關鍵應用程式的可用性，方法是將資料流量分散到多個應用程式伺服器實例，並且只將資料流量轉遞至性能良好的實例。

## 特性概觀
{: #overview-of-features}

{{site.data.keyword.loadbalancer_full}} 服務提供下列特性：

* 公用（面向網際網路）負載平衡器
	* 透過其完整網域名稱 (FQDN) 可公開存取服務
	* 專用子網路上的後端伺服器實例
* 內部負載平衡器
	* 透過其完整網域名稱 (FQDN) 可專用存取服務
	* 用戶端要求透過專用網路來遞送
	* 專用子網路上的後端伺服器實例
* 基本負載平衡
	* 根據第 4 層應用程式埠資訊的資料流量配送
	* HTTP、HTTPS 及 TCP 型應用程式的支援
	* 各種負載平衡方法，例如循環式 (RR)、加權循環式及最少連線
	* 位在資料中心本端的虛擬伺服器與裸機運算實例之間的負載平衡
* 伺服器性能檢查
	* 定期監視伺服器性能，以確保只將資料流量轉遞至性能良好的伺服器
	* TCP 埠是第 4 層性能檢查，而 HTTP 埠是第 7 層性能檢查
* SSL 卸載
	* 使用純文字 HTTP 通訊與後端伺服器搭配，來終止送入的 SSL (HTTPS) 資料流量
* 進階資料流量管理
	* 用戶端綁定（階段作業持續性）
	* 每個虛擬埠的連線上限
* 使用直覺式圖形介面及 API 輕鬆進行管理
* 內建可靠性
* 以用量為基礎的定價
* 監視
    * 在使用者指定的時間間隔，監視 HTTP、HTTPS 及 TCP 通訊協定的「傳輸量」、「作用中連線」及「連線速率」度量值。如需其他詳細資料，請參閱[監視度量值](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer)。
* 第 7 層支援
    * HTTP/HTTPS 資料流量會根據 HTTP 標頭遞送至不同的後端服務，並使用原則及規則來完成。規則用來分類資料流量，並且以 HTTP 標頭欄位為基礎。資料流量符合所有規則時，會採取原則所指定的動作。
* 多區域地區 (MZR) 支援
    * 負載平衡器節點會在 MZR 的不同資料中心中進行實例化。如需相關資訊，請參閱[多區域地區概觀](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview)。
* 資料日誌
    * 啟用資料日誌後，負載平衡器日誌將會轉遞至 [IBM Cloud Log Analysis 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}。客戶可以使用 [IBM Cloud Log Analysis 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/log-analysis){:new_window} 來檢視其資料日誌。
