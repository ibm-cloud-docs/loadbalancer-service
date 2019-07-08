---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: health check, http, tcp, ports

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# 使用 IBM Cloud Load Balancer 執行性能檢查
{: #performing-health-checks-with-ibm-cloud-load-balancer}

每一個後端應用程式埠都必須要有性能檢查定義。性能檢查配置的埠及通訊協定必須符合已定義的後端埠及通訊協定，否則，會拒絕配置。

負載平衡器會進行定期性能檢查來監視後端埠的性能，並將用戶端資料流量相應地轉遞給它們。如果給定的後端伺服器埠性能不佳，則不會將任何新連線轉遞給它。負載平衡器會持續監視這些性能不佳埠的性能，並在透過成功傳遞兩個連續性能檢查嘗試而發現其性能良好之後繼續使用它們。

HTTP、HTTPS 及 TCP 埠的性能檢查進行方式如下：

* **HTTP：**會將針對預先指定 URL 的 `HTTP GET` 要求傳送至後端伺服器埠。收到 `200 OK` 回應時，會將伺服器埠標示為性能良好。預設 `GET` URL 是 "/"，可以透過 GUI 進行自訂。

* **HTTPS：**只有在啟用了後端加密且後端通訊協定設為 HTTPS 時才適用。此機制與 **HTTP** 相同，但所有性能檢查訊息都是 SSL 加密的。如需後端加密的相關資訊，請參閱 /docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-setting-backend-encryption

* **TCP：**「負載平衡器」試圖透過所指定的 TCP 埠開啟與後端伺服器的 TCP 連線。如果連線嘗試成功，則會將伺服器埠標示為性能良好，然後關閉此連線。

	預設性能檢查間隔是 5 秒、性能檢查要求的預設逾時是 2 秒，而預設重試次數是 2。
  {: note}
