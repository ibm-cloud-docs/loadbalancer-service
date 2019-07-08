---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: l7, layer 7, monitor, manage, service

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}
{:important: .important}
{:tip: .tip}

# 監視及管理服務
{: #monitoring-and-managing-your-service}

您可以編輯配置或監視服務效能，方法是在負載平衡器摘要頁面按一下服務名稱 URL。

負載平衡器服務實例的**完整網域名稱 (FQDN) 位址**就在服務名稱下方。您的一般使用者可以透過此 FQDN 位址連接至您的應用程式。請注意，負載平衡器服務的公用及專用 IP 位址不會公開給外界；僅公開 FQDN 位址。

<img src="images/fqdn-address.png" alt="圖片" style="width: 300px;"/>

**概觀**標籤提供服務的高階狀態資訊。它會顯示應用程式伺服器及其埠的現行性能。它也提供系統效能的快速摘要 - 傳輸量、連線速率、並行連線等。

導覽至**監視**標籤，以檢視系統效能的即時圖表。可以依個別應用程式埠及各種期間檢視這些圖形。

<img src="images/monitor-lb.png" alt="圖片" style="width: 300px;"/>

您可以導覽至**通訊協定**、**伺服器實例**和**性能檢查**標籤，來編輯現有配置。例如，導覽至「通訊協定」標籤以定義其他應用程式埠，或自訂 SSL 密碼清單。

<img src="images/protocols-monitor.png" alt="圖片" style="width: 300px;"/>
