---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-28"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 設定後端加密
{: #setting-backend-encryption}

支援後端加密，以容許端對端資料流量加密。不僅負載平衡器與用戶端之間的資料流量會加密，負載平衡器與後端伺服器之間的資料流量也會加密。

若要啟用後端加密，請執行下列動作：

* 如果您是新增 HTTPS 通訊協定，請將前端及後端設為 **HTTPS**。
* 若為現有的 HTTPS 通訊協定，請將後端設為 **HTTPS**。
