---

copyright:
  years: 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Application Server 疑難排解
{: #application-server-troubleshooting}

本主題提供您在使用負載平衡器時可能遇到的一般問題相關資訊。

## 後端伺服器性能不佳
如果您的後端伺服器性能失敗，請嘗試驗證下列清單來嘗試並進行修正：

* 已配置後端通訊協定的埠是否符合您應用程式正在接聽的埠？
* 已配置的性能檢查是否有正確的通訊協定（TCP 或 HTTP）、埠及 URL（適用於 HTTP）資訊？對於 HTTP，請確定應用程式以 `200 OK` 回應已配置的性能檢查 URL。
* 後端伺服器是否位於與負載平衡器不同的子網路上？如果不是，請確定已啟用 VLAN Spanning。
* 後端伺服器是否為具有已啟用安全群組的虛擬伺服器？如果是這樣，請確定安全群組規則容許負載平衡器與虛擬伺服器之間的資料流量。
