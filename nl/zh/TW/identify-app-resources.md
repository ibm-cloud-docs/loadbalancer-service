---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: resources, server, application, instance, configure

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

# 識別應用程式伺服器資源
{: #identifying-your-application-server-resources}

請從底端的表格中找出**伺服器實例**，然後按一下 **+** 以在負載平衡器後方新增它們。您可以從您帳戶的「IBM© Cloud 虛擬伺服器實例 (VSI)」及「裸機伺服器」中進行選取。

這些伺服器實例必須位於您部署負載平衡器服務之資料中心的本端。此外，也可以新增相同城市內鄰接資料中心的伺服器實例（例如，如果資料中心名稱的前三個字母相同）。

<img src="images/locate-server-instance.png" alt="圖片" style="width: 300px;"/>

按**下一步**。

只有在使用**加權循環式**負載平衡方法時，伺服器**權重**才有意義。預設權重是 50，而範圍是 0-100。使用其他負載平衡方法時，權重會呈現灰色。
{: note}

如需應用程式伺服器數目上限的相關資訊，請參閱[應用程式伺服器數目限制](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-faqs-for-ibm-cloud-load-balancer#what-s-the-maximum-number-of-compute-instances-i-can-associate-with-my-load-balancer-)。
{: tip}

## 下一步為何？
{: #what-s-next-3}
先[檢閱訂單的內容](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-review-and-place-your-order)，再下訂單。
