---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-19"

keywords: log, logs, logging, las

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

# 資料記載
{: #data-logging}

資料日誌及性能檢查日誌對於除錯及維護用途非常重要。啟用資料記載特性後，IBM Load Balancer 會將這些日誌轉遞至您帳戶下的 [IBM Cloud Log Analysis 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://logging.ng.bluemix.net){:new_window}。

您可以透過以下方式啟用或停用此特性：

* 建立新的負載平衡器並將此特性設為開啟。
* 使用 API `enableOrDisableDataLogs`。

## 在 IBM Cloud Log Analysis 服務中檢視日誌
{: #viewing-logs-in-the-ibm-cloud-logging-analysis-service}

請使用客戶的 IBM Cloud 帳戶登入 [IBM Cloud Log Analysis 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://logging.ng.bluemix.net){:new_window}。您可以透過 Kibana 檢視日誌。如需相關資訊，請參閱[本主題](/docs/services/CloudLogAnalysis//kibana?topic=cloudloganalysis-analyzing_logs_Kibana)。

只有在 Softlayer 與 IBM Cloud 帳戶鏈結時，才能傳送資料日誌。請選取與 Softlayer 帳戶相關聯的 IBM Cloud 帳戶，然後登入 Kibana 儀表板。
{: tip}

## 日誌輸出範例
{: #log-output-examples}

下列輸出是 {{site.data.keyword.loadbalancer_full}} 資料日誌的範例：

```
Feb 19 05:50:34 loadbalancer-dal09-323698-643866-713576 load-balancer[2558]: Connect from xxx.xxx.xxx.xxx:29856 to 169.55.3.169:80 (a96406a3-12f6-4c1b-8e63-6901848d74ff/HTTP)
```

* `loadbalancer-dal09-323698-643866-713576` 是負載平衡器名稱，而 `dal09` 是資料中心。
* `323698` 是帳戶 ID。`643866` 是負載平衡器 ID。`713576` 是成員 ID。
* `xxx.xxx.xxx.xxx` 是針對 GDPR 標示的公用 IP。

下列輸出是 IBM Cloud Log Analysis 服務內性能檢查日誌的範例：

```
Jan 16 09:00:06 loadbalancer-dal09-323716-619551-682175 haproxy[5976]: Health check for server 673f0dc2-d8ee-4537-800d-eb1b96a360c4/6a876c35-3a6d-45f1-9e9f-db6cf09689bb-10.191.12.23 failed, reason: Layer4 connection problem, info: "Connection error during SSL handshake (Connection refused)", check duration: 1ms, status: 0/2 DOWN.
```

* `10.191.12.23` 是成員 IP 位址。
* `682175` 是成員 ID。
