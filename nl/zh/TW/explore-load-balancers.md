---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 探索負載平衡器

IBM Cloud 提供數個負載平衡解決方案供您選擇。下表比較了這些負載平衡解決方案，以協助您選擇最適合的解決方案。若要進一步瞭解個別供應項目，請在表格中按一下其名稱。 

請捲動到右側以檢視表格的其餘部分！


|        |[IBM Cloud Load Balancer](../../infrastructure/loadbalancer-service/getting-started.html#getting-started)|[區域負載平衡器](../../infrastructure/local-load-balancer/getting-started.html#getting-started)（共用）|[區域負載平衡器](../../infrastructure/local-load-balancer/getting-started.html#getting-started)（專用）|[Citrix NetScaler](../../infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX (Standard)|[Citrix NetScaler](../../infrastructure/citrix-netscaler-vpx/getting-started.html#getting-started-with-citrix-netscaler) VPX/MPX (Platinum) |
|------- | :------: | :------: | :------: | :------: | :------: |
|**公用 VIP**|是|是|是|是|是|
|**專用 VIP**|是|否|是|是|是|
|**第 4 層 LB**|是|是|是|是|是|
|**第 7 層 LB**|是|Cookie 持續性|Cookie 持續性|是|是|
|**性能檢查**|是|是|是|是|是|
|**水平調整**|是|否|否|否|否|
|**SSL 卸載**|是|是|是|是|是|
|**管理**|透過 IBM 入口網站|透過 IBM 入口網站|透過 IBM 入口網站|自行管理（供應商 GUI）|自行管理（供應商 GUI）|
|**高可用性**|內建|內建|選用|選用|選用|
|**進階 LB（TCP 最佳化、壓縮、快取、WAF）**|否|否|否|有限|是|
|**廣域 LB (GLB)**|否|否|否|否|是|
|**定價**|用量型|月租型|月租型|月租型|月租型|
